---
product: campaign
title: Sleutelbeheer in gegevensschema's
description: Belangrijk beheer in gegevensschema's begrijpen
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 1%

---

# Sleutelbeheer in schema&#39;s {#management-of-keys}

Elke tabel die aan een gegevensschema is gekoppeld, moet ten minste één sleutel bevatten voor het identificeren van een record in een tabel.

Een sleutel wordt verklaard van het belangrijkste element van het gegevensschema.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Een sleutel wordt een &#39;primaire sleutel&#39; genoemd wanneer deze de eerste sleutel in het schema is die moet worden ingevuld, of als deze het kenmerk `internal` bevat dat op &#39;true&#39; is ingesteld.

De volgende regels zijn van toepassing op sleutels:

* Een toets kan verwijzen naar een of meer velden in de tabel
* Een unieke index wordt impliciet gedeclareerd voor elke sleuteldefinitie. Het maken van een index op de toets kan worden voorkomen door het kenmerk `noDbIndex` in te stellen op &quot;true&quot;.

>[!NOTE]
>
>* Standaard zijn toetsen de elementen die worden gedeclareerd vanuit het hoofdelement van het schema nadat indexen zijn gedefinieerd.
>
>* Toetsen worden gemaakt tijdens het toewijzen van tabellen (standaard of FDA), Adobe Campaign zoekt naar unieke indexen.

**Voorbeeld**:

* Een sleutel toevoegen aan het e-mailadres en de plaats:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  Het gegenereerde schema:

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
     <dbindex name="email" unique="true">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
     </dbindex>    
  
     <key name="email">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="location/@city"/>    
     </key>    
  
     <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* Een primaire of interne sleutel toevoegen aan het naamveld &quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email" noDbIndex="true">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

  Het gegenereerde schema:

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
      <key name="email">      
        <keyfield xpath="@email"/>    
      </key>    
  
      <dbindex name="id" unique="true">      
        <keyfield xpath="@id"/>    
      </dbindex>    
  
      <key internal="true" name="id">      
       <keyfield xpath="@id"/>    
      </key>    
  
      <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
      <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

## Automatische incrementele toets {#auto-incremental-key}

De primaire sleutel van de meeste Adobe Campaign-tabellen is een 32-bits lang geheel getal dat automatisch wordt gegenereerd door de database-engine. De berekening van de zeer belangrijke waarde hangt van een opeenvolging (door gebrek, de **SQL functie 0} XtkNewId {af) die een aantal produceert dat in het volledige gegevensbestand uniek is.** De inhoud van de toets wordt automatisch ingevoerd bij het invoegen van de record.

Het voordeel van een stijgende sleutel is dat het een niet wijzigbare technische sleutel voor de verbindingen tussen lijsten verstrekt. Bovendien neemt deze sleutel niet veel geheugen in beslag omdat er een dubbel-byte geheel getal wordt gebruikt.

U kunt in het bronschema de naam van de opeenvolging specificeren die met het **pkSequence** attribuut moet worden gebruikt. Als dit attribuut niet in het bronschema wordt gegeven, zal de **XtkNewId** standaardopeenvolging worden gebruikt. De toepassing gebruikt specifieke opeenvolgingen voor **nms:wideLog** en **nms:trackingLog** schema&#39;s (**NmsBroadLogId** en **NmsTrackingLogId** respectievelijk) omdat dit de lijsten zijn die de meeste verslagen bevatten.

Van ACC 18.10, **XtkNewId** is niet meer de standaardwaarde voor de opeenvolging in uit-van-de-doosschema&#39;s. U kunt nu schema bouwen of bestaand schema met een specifieke opeenvolging uitbreiden.

>[!IMPORTANT]
>
>Wanneer het creëren van een nieuw schema of tijdens een schemauitbreiding, moet u de zelfde primaire zeer belangrijke opeenvolgingswaarde (@pkSequence) voor het volledige schema houden.

Een opeenvolging die in een schema van Adobe Campaign wordt van verwijzingen voorzien (**NmsTrackingLogId** bijvoorbeeld) moet met een SQL functie worden geassocieerd die het aantal IDs in de parameters terugkeert, die door komma&#39;s wordt gescheiden. Deze functie moet **worden geroepen GetNew** Ids **, waar** XXX **de naam van de opeenvolging is (** GetNewNmsTrackingLogIds **bijvoorbeeld).** Bekijk **postgres-nms.sql**, **mssql-nms.sql** of **oracle-nms.sql** dossiers die van de toepassing in **worden voorzien datakit/nms/eng/sql/** folder om het voorbeeld van een opeenvolging NmsTrackingLogId&quot;voor elk terug te krijgen database-engine.

Om een unieke sleutel te verklaren, bevolk het **automatische** attribuut (met waarde &quot;waar&quot;) op het belangrijkste element van het gegevensschema.

**Voorbeeld**:

Een incrementele sleutel in het bronschema declareren:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

Het gegenereerde schema:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

Naast de definitie van de sleutel en zijn index, is een numeriek gebied genoemd &quot;id&quot;toegevoegd aan het uitgebreide schema om de auto-geproduceerde primaire sleutel te bevatten.

>[!IMPORTANT]
>
>Bij het maken van de tabel wordt automatisch een record met de primaire sleutel ingesteld op 0 ingevoegd. Deze record wordt gebruikt om buitenste verbindingen te voorkomen, die niet effectief zijn op volumetabellen. Door gebrek, worden alle buitenlandse sleutels geïnitialiseerd met waarde 0 zodat een resultaat altijd kan zijn teruggekeerd op de verbinding wanneer het gegevenspunt niet bevolkt is.


## Meer informatie

Klik op de volgende koppelingen voor meer informatie:

* [Aan de slag met schema&#39;s](about-schema-reference.md)
* [Schemastructuur](schema-structure.md)
* [Databasetoewijzing](database-mapping.md)
* [Beheer van koppeling](database-links.md)
* [Campagne gegevensmodel](about-data-model.md)
