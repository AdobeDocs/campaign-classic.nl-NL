---
product: campaign
title: Databasetoewijzing
description: Databasetoewijzing
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 3%

---

# Databasetoewijzing{#database-mapping}

De SQL afbeelding van het steekproefschema dat [ in deze pagina ](schema-structure.md) wordt beschreven produceert het volgende document van XML:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient email address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

Het hoofdelement van het schema is veranderd in **`<srcschema>`** in **`<schema>`** .

Dit andere type van document wordt geproduceerd automatisch van het bronschema, en eenvoudig bedoeld als schema.

De SQL-namen worden automatisch bepaald op basis van de naam en het type van het element.

De SQL-naamgevingsregels zijn als volgt:

* **lijst**: aaneenschakeling van schema namespace en naam

  In ons voorbeeld, is de naam van de lijst ingegaan via het belangrijkste element van het schema in het **sqltable** attribuut:

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **gebied**: naam van het element dat door een prefix wordt voorafgegaan die volgens type wordt bepaald: &quot;i&quot;voor geheel, &quot;d&quot;voor dubbel, &quot;s&quot;voor koord, &quot;ts&quot;voor data, enz.

  De gebiedsnaam is ingegaan via het **sqlname** attribuut voor elk getypt **`<attribute>`** en **`<element>`**:

  ```sql
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>SQL-namen kunnen worden overgeladen uit het bronschema. Hiertoe vult u de kenmerken &quot;sqltable&quot; of &quot;sqlname&quot; op het desbetreffende element in.

Het SQL-script voor het maken van de tabel die wordt gegenereerd op basis van het uitgebreide schema ziet er als volgt uit:

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

De beperkingen voor het SQL-veld zijn als volgt:

* geen null-waarden in numerieke velden en datumvelden
* numerieke velden worden geïnitialiseerd naar 0

## XML-velden {#xml-fields}

Standaard worden alle elementen met het type **`<attribute>`** en **`<element>`** toegewezen aan een SQL-veld in de tabel met het gegevensschema. U kunt echter naar dit veld verwijzen in XML in plaats van naar SQL, wat betekent dat de gegevens worden opgeslagen in een geheugenveld (&quot;mData&quot;) van de tabel dat de waarden van alle XML-velden bevat. De opslag van deze gegevens is een XML-document dat de schemastructuur in acht neemt.

Om een gebied in XML te bevolken, moet u **xml** attributen met de waarde &quot;waar&quot;aan het betrokken element toevoegen.

**Voorbeeld**: hier zijn twee voorbeelden van het gebiedsgebruik van XML.

* Veld voor opmerkingen met meerdere regels:

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* Beschrijving van de gegevens in HTML-formaat:

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  Met het type &quot;html&quot; kunt u de HTML-inhoud opslaan in een CDATA-tag en een speciale controle voor het bewerken van HTML weergeven in de Adobe Campaign-clientinterface.

Gebruik XML-velden om nieuwe velden toe te voegen zonder de fysieke structuur van de database te wijzigen. Een ander voordeel is dat u minder bronnen gebruikt (grootte die is toegewezen aan SQL-velden, beperking van het aantal velden per tabel, enzovoort). U kunt een XML-veld echter niet indexeren of filteren.

## Geïndexeerde velden {#indexed-fields}

Met indexen kunt u de prestaties optimaliseren van de SQL-query&#39;s die in de toepassing worden gebruikt.

Een index wordt gedeclareerd vanuit het hoofdelement van het gegevensschema.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Indexen houden zich aan de volgende regels:

* Een index kan verwijzen naar een of meer velden in de tabel
* Een index kan (om duplicaten te vermijden) op alle gebieden uniek zijn als het **unieke** attribuut de waarde &quot;waar&quot;bevat
* De SQL-naam van de index wordt bepaald door de SQL-naam van de tabel en de naam van de index

>[!NOTE]
>
>* Standaard zijn indexen de eerste elementen die zijn gedeclareerd vanuit het hoofdelement van het schema.
>
>* De indexen worden automatisch gecreeerd tijdens lijstafbeelding (norm of FDA).

**Voorbeeld**:

* Een index toevoegen aan het e-mailadres en de plaats:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* Een unieke index toevoegen aan het naamveld &quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## Meer informatie

Klik op de volgende koppelingen voor meer informatie:

* [Aan de slag met schema&#39;s](about-schema-reference.md)
* [Schemastructuur](schema-structure.md)
* [Sleutelbeheer](database-keys.md)
* [Beheer van koppeling](database-links.md)
* [Campagne gegevensmodel](about-data-model.md)