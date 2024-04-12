---
product: campaign
title: Sleutelbeheer in gegevensschema's
description: Belangrijk beheer in gegevensschema's begrijpen
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '618'
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

Een sleutel wordt een &#39;primaire sleutel&#39; genoemd wanneer deze de eerste sleutel in het schema is die moet worden ingevuld, of als deze de `internal` kenmerk ingesteld op &quot;true&quot;.

De volgende regels zijn van toepassing op sleutels:

* Een toets kan verwijzen naar een of meer velden in de tabel
* Een unieke index wordt impliciet gedeclareerd voor elke sleuteldefinitie. Het maken van een index op de toets kan worden voorkomen door het instellen van de `noDbIndex` kenmerk naar &quot;true&quot;.

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

De primaire sleutel van de meeste Adobe Campaign-tabellen is een 32-bits lang geheel getal dat automatisch wordt gegenereerd door de database-engine. De berekening van de sleutelwaarde hangt van een opeenvolging (door gebrek, af **XtkNewId** SQL functie) die een aantal produceren dat in het volledige gegevensbestand uniek is. De inhoud van de toets wordt automatisch ingevoerd bij het invoegen van de record.

Het voordeel van een stijgende sleutel is dat het een niet wijzigbare technische sleutel voor de verbindingen tussen lijsten verstrekt. Bovendien neemt deze sleutel niet veel geheugen in beslag omdat er een dubbel-byte geheel getal wordt gebruikt.

U kunt in het bronschema de naam opgeven van de reeks die moet worden gebruikt voor de **pkSequence** kenmerk. Als dit kenmerk niet wordt opgegeven in het bronschema, wordt het **XtkNewId** de standaardreeks wordt gebruikt. De toepassing gebruikt specifieke reeksen voor de **nms:wideLog** en **nms:trackingLog** schema&#39;s (**NmsBroadLogId** en **NmsTrackingLogId** respectievelijk) omdat dit de lijsten zijn die de meeste verslagen bevatten.

Vanaf ACC 18.10 **XtkNewId** is niet meer de standaardwaarde voor de opeenvolging in uit-van-de-doosschema&#39;s. U kunt nu schema bouwen of bestaand schema met een specifieke opeenvolging uitbreiden.

>[!IMPORTANT]
>
>Wanneer het creëren van een nieuw schema of tijdens een schemauitbreiding, moet u de zelfde primaire zeer belangrijke opeenvolgingswaarde (@pkSequence) voor het volledige schema houden.

Een reeks waarnaar in een Adobe Campaign-schema wordt verwezen (**NmsTrackingLogId** moet bijvoorbeeld) worden gekoppeld aan een SQL-functie die het aantal id&#39;s in de parameters retourneert, gescheiden door komma&#39;s. Deze functie moet worden opgeroepen **GetNew** XXX **ID**, waarbij **XXX** is de naam van de reeks (**GetNewNmsTrackingLogIds** bijvoorbeeld). De weergave **postgres-nms.sql**, **mssql-nms.sql** of **oracle-nms.sql** bestanden die bij de toepassing worden geleverd in het dialoogvenster **datakit/nms/eng/sql/** directory om het voorbeeld van het maken van een &#39;NmsTrackingLogId&#39;-reeks voor elke database-engine te herstellen.

Als u een unieke sleutel wilt declareren, vult u de **automatische** kenmerk (met waarde &quot;true&quot;) op het hoofdelement van het gegevensschema.

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
* [Campaign datamodel](about-data-model.md)
