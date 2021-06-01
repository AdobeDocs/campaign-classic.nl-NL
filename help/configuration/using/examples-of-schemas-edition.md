---
product: campaign
title: Voorbeelden van schemabewerking
description: Voorbeelden van schemabewerking
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: b7ee70e0-89c6-4cd3-8116-2f073d4a2f2f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 2%

---

# Voorbeelden van schemabewerking{#examples-of-schemas-edition}

## Een tabel {#extending-a-table} uitbreiden

Pas de volgende procedure toe om de **nms:receiving** schema ontvankelijke lijst uit te breiden:

1. Maak het extensieschema (**cus:extension**) met behulp van de volgende gegevens:

   ```
   <srcSchema mappingType="sql" name="extension" namespace="cus" xtkschema="xtk:srcSchema" extendedSchema="nms:recipient">  
     <enumeration basetype="string" default="area1" name="area">    
       <value label="Zone 1" name="area1"/>    
       <value label="Zone 2" name="area2"/>  
     </enumeration>  
   
     <element name="extension">    
       <dbindex name="area">      
         <keyfield xpath="location/@area"/>    
       </dbindex>      
   
       <attribute label="Loyalty code" name="fidelity" type="long"/>    
       <element name="location">      
         <attribute name="area" label="Purchasing zone" type="string" length="50" enum="area"/>    
       </element>  </element>  
   </srcSchema>
   ```

   In dit voorbeeld wordt een geïndexeerd veld (**fidelity**) toegevoegd en wordt het element **location** (dat al bestond in het schema **nms:receiving**) aangevuld met een opgesomd veld (**area**).

   >[!IMPORTANT]
   >
   >Vergeet niet het kenmerk **extendedSchema** toe te voegen om naar het extensieschema te verwijzen.

1. Controleer of het uitgebreide schema het schema **nms:receiving** is en of de aanvullende gegevens aanwezig zijn:

   ```
   <schema dependingSchemas="cus:extension" mappingType="sql" name="recipient" namespace="nms" xtkschema="xtk:schema">
     ...
     <enumeration basetype="string" default="area1" name="area">    
       <value label="Zone 1" name="area1"/>    
       <value label="Zone 2" name="area2"/>  
     </enumeration>
     ...
     <element autopk="true" name="recipient" sqltable="NmsRecipient"> 
       <dbindex name="area">      
         <keyfield xpath="location/@area"/>    
       </dbindex>
   
       ...
       <attribute belongsTo="cus:extension" label="Loyalty code" name="fidelity" sqlname="iFidelity" type="long"/>
       <element name="location">
         ...
         <attribute enum="area" label="Purchasing zone" length="50" name="area" sqlname="sArea" type="string"/>
       </element>
       ...
     </element>
   </schema>
   ```

   Het SQL-script dat is gegenereerd op basis van de wizard Database bijwerken ziet er als volgt uit:

   ```
   ALTER TABLE NmsRecipient ADD iFidelity INTEGER;
   UPDATE NmsRecipient SET iFidelity = 0;
   ALTER TABLE NmsRecipient ALTER COLUMN iFidelity SET NOT NULL;ALTER TABLE NmsRecipient ALTER COLUMN iFidelity SET Default 0;
   ALTER TABLE NmsRecipient ADD sArea VARCHAR(50); 
   CREATE INDEX NmsRecipient_area ON NmsRecipient(sArea);
   ```

## Gekoppelde verzamelingstabel {#linked-collection-table}

In deze sectie wordt beschreven hoe u een ordertabel maakt die is gekoppeld aan de tabel van de ontvanger met kardinaliteit 1-N.

Bronschema van tabel bestellen:

```
<srcSchema label="Order" name="order" namespace="cus" xtkschema="xtk:srcSchema">  
  <element autopk="true" name="order">    
    <compute-string expr="@number" + '(' + ToString(@date) + ')'/>    
    
    <attribute label="Number" length="128" name="number" type="string"/>    
    <attribute desc="Order date" label="Date" name="date" type="datetime" default="GetDate()"/>    
    <attribute desc="order total" label="Total" name="total" type="double"/>    
    <element label="Recipient" name="recipient" revDesc="Orders associated with this recipient" revIntegrity="own" revLabel="Orders" target="nms:recipient" type="link"/>  
  </element>
</srcSchema>
```

Het tabeltype is **automatische** om een automatisch gegenereerde primaire sleutel te maken die moet worden gebruikt door de samenvoeging van de koppeling naar de ontvangende tabel.

Gegenereerd schema:

```
<schema label="Order" mappingType="sql" name="order" namespace="cus" xtkschema="xtk:schema">  
  <element autopk="true" label="Order" name="order" sqltable="CusOrder">    
    <compute-string expr="ToString(@date) + ' - ' + @number"/>    

    <dbindex name="id" unique="true">      
      <keyfield xpath="@id"/>    
    </dbindex>    

    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>    

    <dbindex name="recipientId">      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iOrderId" type="long"/>    
    <attribute label="Number" length="128" name="number" sqlname="sNumber" type="string"/>    
    <attribute desc="Order date" label="Date" name="date" sqlname="tsDate" type="datetime"/>    
    <attribute desc="order total" label="Total" name="total" sqlname="Total" type="double"/>    
    <element label="Recipient" name="recipient" revLink="order" target="nms:recipient" type="link">      
      <join xpath-dst="@id" xpath-src="@recipient-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Recipient' link ('id' field)" name="recipient-id" sqlname="iRecipientId" type="long"/>  
   </element>
</schema>
```

Het SQL-script voor het maken van tabellen ziet er als volgt uit:

```
CREATE TABLE CusOrder(dTotal DOUBLE PRECISION NOT NULL Default 0, iOrderId INTEGER NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0, sNumber VARCHAR(128), tsDate TIMESTAMP Default NULL);
CREATE UNIQUE INDEX CusOrder_id ON CusOrder(iOrderId);
CREATE INDEX CusOrder_recipientId ON CusOrder(iRecipientId);  
INSERT INTO CusOrder (iOrderId) VALUES (0); 
```

>[!NOTE]
>
>Met de SQL-opdracht INSERT INTO aan het einde van het script kunt u een id-record invoegen die is ingesteld op 0 om buitenste verbindingen te simuleren.

## Extensietabel {#extension-table}

Met een extensietabel kunt u de inhoud van een bestaande tabel in een gekoppelde tabel met kardinaliteit 1-1 uitbreiden.

Het doel van een extensietabel is het voorkomen van beperkingen op het aantal velden dat in een tabel wordt ondersteund, of het optimaliseren van de ruimte die wordt ingenomen door de gegevens, die op verzoek worden gebruikt.

Het creëren van het schema van de uitbreidingslijst (**cus:feature**):

```
<srcSchema mappingType="sql" name="feature" namespace="cus" xtkschema="xtk:srcSchema">  
  <element autopk="true" name="feature">    
    <attribute label="Children" name="children" type="byte"/>    
    <attribute label="Single" name="single" type="boolean"/>    
    <attribute label="Spouse first name" length="100" name="spouseFirstName" type="string"/>  
  </element>
</srcSchema>
```

Een extensieschema maken voor de tabel met ontvangers om de koppeling tussen hoofdletters 1-1 toe te voegen:

```
<srcSchema extendedSchema="nms:recipient" label="Recipient" mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:srcSchema">  
  <element name="recipient">    
    <element desc="Features" integrity="own" label="Features" name="feature" revCardinality="single" revLink="recipient" target="cus:feature" type="link"/> 
  </element>
</srcSchema>
```

>[!NOTE]
>
>De definitie van de koppeling tussen de tabel met ontvangers en de tabel met extensies moet worden ingevuld in het schema dat de externe sleutel bevat.

Het SQL-script voor het maken van de extensietabel ziet er als volgt uit:

```
CREATE TABLE CusFeature(  iChildren NUMERIC(3) NOT NULL Default 0, iFeatureId INTEGER NOT NULL Default 0, iSingle NUMERIC(3) NOT NULL Default 0, sSpouseFirstName VARCHAR(100));
CREATE UNIQUE INDEX CusFeature_id ON CusFeature(iFeatureId);  
INSERT INTO CusFeature (iFeatureId) VALUES (0); 
```

Het SQL-updatescript voor de ontvangende tabel ziet er als volgt uit:

```
ALTER TABLE NmsRecipient ADD iFeatureId INTEGER;
UPDATE NmsRecipient SET iFeatureId = 0;
ALTER TABLE NmsRecipient ALTER COLUMN iFeatureId SET NOT NULL;
ALTER TABLE NmsRecipient ALTER COLUMN iFeatureId SET Default 0;
CREATE INDEX NmsRecipient_featureId ON NmsRecipient(iFeatureId);
```

## Overlopende tabel {#overflow-table}

Een overlooplijst is een uitbreidingslijst (kardinaliteit 1-1), maar de verklaring van de verbinding aan de uit te breiden lijst wordt bevolkt in het schema van de overlooplijst.

De overlooptabel bevat de vreemde sleutel voor de uit te breiden tabel. De uit te breiden tabel wordt derhalve niet gewijzigd. De relatie tussen de twee tabellen is de waarde van de primaire sleutel van de uit te breiden tabel.

Het creëren van het schema van de overlooplijst (**cus:overflow**):

```
<srcSchema label="Overflow" name="overflow" namespace="cus" xtkschema="xtk:srcSchema">  
  <element name="overflow">    
    <key internal="true" name="id">      
      <keyfield xlink="recipient"/>    
    </key>    

    <attribute label="Children" name="children" type="byte"/>    
    <attribute label="Single" name="single" type="boolean"/>    
    <attribute label="Spouse first name" length="100" name="spouseFirstName" type="string"/>  
    <element label="Customer" name="recipient" revCardinality="single" revIntegrity="own" revExternalJoin="true" target="nms:recipient" type="link"/>  
  </element>  
</srcSchema>
```

>[!NOTE]
>
>De primaire sleutel van de overlooplijst is de verbinding aan de uit te breiden lijst (&quot;nms:ontvangend&quot;schema in ons voorbeeld).

Het SQL-script voor het maken van tabellen ziet er als volgt uit:

```
CREATE TABLE CusOverflow(iChildren NUMERIC(3) NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0, iSingle NUMERIC(3) NOT NULL Default 0, sSpouseFirstName VARCHAR(100));
CREATE UNIQUE INDEX CusOverflow2_id ON CusOverflow2(iRecipientId);  
```

## Relatietabel {#relationship-table}

Met een relatietabel kunt u twee tabellen koppelen aan de kardinaliteit N-N. Deze tabel bevat alleen de externe sleutels van de tabellen die moeten worden gekoppeld.

Voorbeeld van een relatietabel tussen groepen (**nms:groep**) en ontvangers (**nms:ontvanger**).

Bronschema van de relatietabel:

```
<srcSchema name="rcpGrpRel" namespace="cus">
  <element name="rcpGrpRel">
    <key internal="true" name="id">      
      <keyfield xlink="rcpGroup"/>      
      <keyfield xlink="recipient"/>    
    </key>

    <element integrity="neutral" label="Recipient" name="recipient" revDesc="Groups to which this recipient belongs" revIntegrity="own" revLabel="Groups" target="nms:recipient" type="link"/>    
    <element integrity="neutral" label="Group" name="rcpGroup" revDesc="Recipients in the group" revIntegrity="own" revLabel="Recipients" revLink="rcpGrpRel" target="nms:group" type="link"/>
  </element>
</srcSchema>
```

Het gegenereerde schema ziet er als volgt uit:

```
<schema mappingType="sql" name="rcpGrpRel" namespace="cus" xtkschema="xtk:schema">  
  <element name="rcpGrpRel" sqltable="CusRcpGrpRel">    
    <compute-string expr="ToString([@rcpGroup-id]) + ',' + ToString([@recipient-id])"/>    
    <dbindex name="id" unique="true">      
      <keyfield xpath="@rcpGroup-id"/>      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <key internal="true" name="id">      
      <keyfield xpath="@rcpGroup-id"/>      
      <keyfield xpath="@recipient-id"/>    
    </key>    

    <dbindex name="rcpGroupId">      
      <keyfield xpath="@rcpGroup-id"/>    
    </dbindex>    
    <dbindex name="recipientId">      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <element integrity="neutral" label="Recipient" name="recipient" revLink="rcpGrpRel" target="nms:recipient" type="link">      
      <join xpath-dst="@id" xpath-src="@recipient-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Recipient' link ('id' field)" name="recipient-id" sqlname="iRecipientId" type="long"/>    

    <element integrity="neutral" label="Group" name="rcpGroup" revLink="rcpGrpRel" target="nms:group" type="link">      
      <join xpath-dst="@id" xpath-src="@rcpGroup-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Group' link ('id' field)" name="rcpGroup-id" sqlname="iRcpGroupId" type="long"/>  
  </element>
</schema>
```

Het SQL-script voor het maken van tabellen ziet er als volgt uit:

```
CREATE TABLE CusRcpGrpRel( iRcpGroupId INTEGER NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0);
CREATE UNIQUE INDEX CusRcpGrpRel_id ON CusRcpGrpRel(iRcpGroupId, iRecipientId);
CREATE INDEX CusRcpGrpRel_recipientId ON CusRcpGrpRel(iRecipientId);
```

## Hoofdlettergebruik: een veld koppelen aan een bestaande referentietabel {#uc-link}

Dit gebruiksgeval toont aan hoe u een bestaande verwijzingstabel als alternatief aan ingebouwde de opsingsmechanismen van Adobe Campaign (enum, userEnum, of dbEnum) kunt gebruiken.

U kunt een bestaande verwijzingstabel als opsomming in uw schema&#39;s ook gebruiken. Dit kan worden bereikt door een verbinding tussen een lijst en de verwijzingstabel te creëren, en door de attributen **displayAsField=&quot;waar&quot;** toe te voegen.

In dit voorbeeld bevat de referentietabel een lijst met namen en identificatiecodes van banken:

```
<srcSchema entitySchema="xtk:srcSchema" img="cus:bank16x16.png" label="Bank" mappingType="sql" name="bank" namespace="cus"
xtkschema="xtk:srcSchema">
    <element img="cus:bank16x16.png" label="Banks" name="bank">
        <compute-string expr="@name"/>
        <key name="id">
            <keyfield xpath="@id"/>
        </key>
        <attribute label="Bank Id" name="id" type="short"/>
        <attribute label="Name" length="64" name="name" type="string"/>
     </element> 
</srcSchema>
```

In om het even welke lijst die deze verwijzingstabel gebruikt, bepaal een verbinding en voeg **displayAsField=&quot;waar&quot;** toe attribuut.

```
<element displayAsField="true" label="Bank" name="bank" target="cus:bank" type="link" noDbIndex="true"/>
```

In de gebruikersinterface wordt geen koppeling maar een veld weergegeven. Wanneer de gebruiker dat veld kiest, kan hij een waarde in de referentietabel selecteren of de functie voor automatisch aanvullen gebruiken.

![](assets/schema-edition-ex.png)

* Als de instructie automatisch moet worden voltooid, moet u een compute-string definiëren in de referentietabel.

* Voeg het **noDbIndex=&quot;waar&quot;** attribuut in de verbindingsdefinitie toe om Adobe Campaign te verhinderen een index op de waarden te creëren die in de bronlijst van de verbinding worden opgeslagen.

## Verwante onderwerpen

* [Werken met opsommingen](../../platform/using/managing-enumerations.md)

* [Aan de slag met campagnereschema&#39;s](../../configuration/using/about-schema-edition.md)

* [De databasestructuur bijwerken](../../configuration/using/updating-the-database-structure.md)
