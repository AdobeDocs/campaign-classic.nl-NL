---
product: campaign
title: Databasetoewijzing
description: Databasetoewijzing
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: bd1007ffcfa58ee60fdafa424c7827e267845679
workflow-type: tm+mt
source-wordcount: '1984'
ht-degree: 0%

---

# Databasetoewijzing{#database-mapping}

De SQL-toewijzing van het voorbeeldschema dat wordt beschreven [op deze pagina](schema-structure.md) genereert het volgende XML-document:

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

## Beschrijving {#description}

Het hoofdelement van het schema is gewijzigd in **`<srcschema>`** tot **`<schema>`**.

Dit andere type van document wordt geproduceerd automatisch van het bronschema, en eenvoudig bedoeld als schema.

De SQL-namen worden automatisch bepaald op basis van de naam en het type van het element.

De SQL-naamgevingsregels zijn als volgt:

* **table**: samenvoeging van de naamruimte en naam van het schema

  In ons voorbeeld wordt de naam van de tabel ingevoerd via het hoofdelement van het schema in het dialoogvenster **sqltable** kenmerk:

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **field**: naam van het element, voorafgegaan door een voorvoegsel dat is gedefinieerd op basis van het type: &#39;i&#39; voor geheel getal, &#39;d&#39; voor dubbel, &#39;s&#39; voor tekenreeks, &#39;ts&#39; voor datums, enz.

  De veldnaam wordt ingevoerd via het dialoogvenster **sqlname** kenmerk voor elk type **`<attribute>`** en **`<element>`**:

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

Standaard worden alle  **`<attribute>`** en **`<element>`** -typed element wordt in kaart gebracht op een SQL gebied van de lijst van het gegevensschema. U kunt echter naar dit veld verwijzen in XML in plaats van naar SQL, wat betekent dat de gegevens worden opgeslagen in een geheugenveld (&quot;mData&quot;) van de tabel dat de waarden van alle XML-velden bevat. De opslag van deze gegevens is een XML-document dat de schemastructuur in acht neemt.

Als u een veld in XML wilt vullen, voegt u de opdracht **xml** kenmerk met de waarde &quot;true&quot; aan het betrokken element.

**Voorbeeld**: Hier volgen twee voorbeelden van het gebruik van XML-velden.

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
* Een index kan uniek zijn (om dubbele waarden te voorkomen) in alle velden als de **uniek** attribute contains the value &quot;true&quot;
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

## Sleutelbeheer {#management-of-keys}

Een tabel moet ten minste één sleutel bevatten voor het identificeren van een record in de tabel.

Een sleutel wordt verklaard van het belangrijkste element van het gegevensschema.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

De volgende regels zijn van toepassing op sleutels:

* Een toets kan verwijzen naar een of meer velden in de tabel
* Een sleutel wordt &#39;primair&#39; (of &#39;prioriteit&#39;) genoemd wanneer deze de eerste sleutel in het schema is die moet worden ingevuld of wanneer deze de **internal** kenmerk met de waarde &quot;true&quot;
* Een unieke index wordt impliciet gedeclareerd voor elke sleuteldefinitie. Het maken van een index op de toets kan worden voorkomen door het toevoegen van de **noDbIndex** kenmerk met de waarde &quot;true&quot;

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

### Automatische incrementele toets {#auto-incremental-key}

De primaire sleutel van de meeste Adobe Campaign-tabellen is een 32-bits lang geheel getal dat automatisch wordt gegenereerd door de database-engine. De berekening van de sleutelwaarde hangt van een opeenvolging (door gebrek, af **XtkNewId** SQL functie) die een aantal produceren dat in het volledige gegevensbestand uniek is. De inhoud van de toets wordt automatisch ingevoerd bij het invoegen van de record.

Het voordeel van een stijgende sleutel is dat het een niet wijzigbare technische sleutel voor de verbindingen tussen lijsten verstrekt. Bovendien neemt deze sleutel niet veel geheugen in beslag omdat er een dubbel-byte geheel getal wordt gebruikt.

U kunt in het bronschema de naam opgeven van de reeks die moet worden gebruikt voor de **pkSequence** kenmerk. Als dit kenmerk niet wordt opgegeven in het bronschema, wordt het **XtkNewId** de standaardreeks wordt gebruikt. De toepassing gebruikt specifieke reeksen voor de **nms:wideLog** en **nms:trackingLog** schema&#39;s (**NmsBroadLogId** en **NmsTrackingLogId** respectievelijk) omdat dit de lijsten zijn die de meeste verslagen bevatten.

Vanaf ACC 18.10 **XtkNewId** is niet meer de standaardwaarde voor de opeenvolging in uit-van-de-doosschema&#39;s. U kunt nu schema bouwen of bestaand schema met een specifieke opeenvolging uitbreiden.

>[!IMPORTANT]
>
>Wanneer het creëren van een nieuw schema of tijdens een schemauitbreiding, moet u de zelfde primaire zeer belangrijke opeenvolgingswaarde (@pkSequence) voor het volledige schema houden.

>[!NOTE]
>
>Een reeks waarnaar in een Adobe Campaign-schema wordt verwezen (**NmsTrackingLogId** moet bijvoorbeeld) worden gekoppeld aan een SQL-functie die het aantal id&#39;s in de parameters retourneert, gescheiden door komma&#39;s. Deze functie moet worden opgeroepen **GetNew** XXX **ID**, waarbij **XXX** is de naam van de reeks (**GetNewNmsTrackingLogIds** bijvoorbeeld). De weergave **postgres-nms.sql**, **mssql-nms.sql** of **oracle-nms.sql** bestanden die bij de toepassing worden geleverd in het dialoogvenster **datakit/nms/eng/sql/** directory om het voorbeeld van het maken van een &#39;NmsTrackingLogId&#39;-reeks voor elke database-engine te herstellen.

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

## Koppelingen: relatie tussen tabellen {#links--relation-between-tables}

Een koppeling beschrijft de koppeling tussen de ene tabel en de andere.

De verschillende soorten verenigingen (zogenaamde &quot;kardinaliteiten&quot;) zijn als volgt:

* Kardinaliteit 1-1: één instantie van de brontabel kan maximaal één overeenkomende instantie van de doeltabel hebben.
* Kardinaliteit 1-N: één voorkomen van de bronlijst kan verscheidene overeenkomstige voorkomen van de doellijst hebben, maar één voorkomen van de doellijst kan hoogstens één overeenkomstige voorkomen van de bronlijst hebben.
* Kardinaliteit N-N: één instantie van de brontabel kan meerdere corresponderende instanties van de doeltabel hebben, en omgekeerd.

In de interface kunt u de verschillende soorten relaties gemakkelijk onderscheiden dankzij hun pictogrammen.

Voor het samenvoegen van relaties met een tabel/database voor campagnes:

* ![](assets/join_with_campaign11.png) : Kardinaliteit 1-1. Bijvoorbeeld tussen een ontvanger en een huidige orde. Een ontvanger kan aan slechts één voorkomen van de huidige ordetabel tegelijkertijd worden verwant.
* ![](assets/externaljoin11.png) : Kardinaliteit 1-1, externe verbinding. Bijvoorbeeld tussen een ontvanger en hun land. Een ontvanger kan slechts aan één voorkomen van het lijstland worden verwant. De inhoud van de landentabel wordt niet opgeslagen.
* ![](assets/join_with_campaign1n.png) : Kardinaliteit 1-N. Bijvoorbeeld tussen een ontvanger en de abonnementstabel. Een ontvanger kan zijn verwant aan verscheidene voorkomen op de abonnementstabel.

Voor join-relaties met gebruik van Federated Database Access:

* ![](assets/join_fda_11.png) : Kardinaliteit 1-1
* ![](assets/join_fda_1m.png) : Kardinaliteit 1-N

Raadpleeg voor meer informatie over FDA-tabellen [Een externe database openen](../../installation/using/about-fda.md).

Een koppeling moet worden gedeclareerd in het schema met de externe sleutel van de tabel die is gekoppeld via het hoofdelement:

```sql
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Koppelingen voldoen aan de volgende regels:

* De definitie van een koppeling wordt ingevoerd op een **link**-type **`<element>`** met de volgende kenmerken:

   * **name**: naam van koppeling uit de brontabel,
   * **target**: naam van doelschema,
   * **label**: label van koppeling,
   * **revLink** (optioneel): naam van de reverse link van het doelschema (standaard automatisch afgetrokken);
   * **integriteit** (facultatief): referentiële integriteit van het voorkomen van de bronlijst aan het voorkomen van de doellijst. Mogelijke waarden zijn:

      * **definiëren**: het is mogelijk om de bron-instantie te verwijderen als er niet langer naar wordt verwezen door een doelinstantie,
      * **normaal**: als u de broninstantie verwijdert, worden de toetsen van de koppeling naar de doelinstantie (de standaardmodus) geïnitialiseerd. Bij dit type integriteit worden alle externe toetsen geïnitialiseerd.
      * **eigen**: het verwijderen van de broninstantie leidt tot het verwijderen van de doelinstantie,
      * **owncopy**: gelijk aan **eigen** (in geval van verwijdering) of dupliceert de voorvallen (in geval van duplicatie),
      * **neutraal**: doet niets.

   * **revIntegrity** (optioneel): integriteit in het doelschema (optioneel, standaard &quot;normaal&quot;);
   * **revCardinality** (optioneel): met de waarde &quot;single&quot; wordt de kardinaliteit gevuld met type 1-1 (standaard 1-N).
   * **externalJoin** (optioneel): forceert de buitenste verbinding
   * **revExternalJoin** (optioneel): hiermee wordt de buitenste verbinding op de omgekeerde koppeling gedwongen

* Een koppeling verwijst naar een of meer velden van de brontabel naar de doeltabel. De velden waaruit de verbinding bestaat ( `<join>`  -element) hoeft niet te worden gevuld omdat deze automatisch worden afgetrokken met de interne sleutel van het doelschema.
* Er wordt automatisch een index toegevoegd aan de externe sleutel van de koppeling in het uitgebreide schema.
* Een verbinding bestaat uit twee half-verbindingen, waar het eerste van het bronschema wordt verklaard en het tweede automatisch in het uitgebreide schema van het doelschema wordt gecreeerd.
* Een samenvoeging kan een buitenste samenvoeging zijn als **externalJoin** wordt toegevoegd, met de waarde &quot;true&quot; (wordt ondersteund in PostSQL).

>[!NOTE]
>
>Standaard zijn koppelingen de elementen die aan het einde van het schema worden gedeclareerd.

### Voorbeeld 1 {#example-1}

1-N met betrekking tot de &quot;cus:company&quot;schemalijst:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Het gegenereerde schema:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

De koppelingsdefinitie wordt aangevuld met de velden waaruit de verbinding bestaat, d.w.z. de primaire sleutel met zijn XPath (&quot;@id&quot;) in het doelschema en de buitenlandse sleutel met zijn XPath (&quot;@company-id&quot;) in het schema.

De buitenlandse sleutel wordt automatisch toegevoegd in een element dat de zelfde kenmerken zoals het bijbehorende gebied in de bestemmingslijst, met de volgende noemende overeenkomst gebruikt: naam van doelschema dat door naam van bijbehorend gebied (&quot;bedrijf-identiteitskaart&quot;in ons voorbeeld) wordt gevolgd.

Uitgebreid schema van het doel (&quot;cus:company&quot;):

```sql
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

Er is een omgekeerde koppeling naar de tabel &quot;cus:receiving&quot; toegevoegd met de volgende parameters:

* **name**: wordt automatisch afgetrokken van de naam van het bronschema (kan worden afgedwongen met het kenmerk &quot;revLink&quot; in de koppelingsdefinitie in het bronschema)
* **revLink**: naam van omgekeerde koppeling
* **target**: sleutel van gekoppeld schema (&quot;focus:ontvanger&quot;-schema)
* **ongebonden**: de koppeling wordt gedeclareerd als een verzamelingselement voor een kardinaliteit van 1 N (standaard)
* **integriteit**: &quot;define&quot;door gebrek (kan met het &quot;revIntegrity&quot;attribuut in de verbindingsdefinitie op het bronschema worden gedwongen).

### Voorbeeld 2 {#example-2}

In dit voorbeeld, zullen wij een verbinding naar de &quot;nms:adres&quot;schemalijst verklaren. De join is een outer join en wordt expliciet gevuld met het e-mailadres van de ontvanger en het veld &quot;@address&quot; van de gekoppelde tabel (&quot;nms:address&quot;).

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

### Voorbeeld 3 {#example-3}

1-1 met betrekking tot de tabel in het schema &quot;cus:extension&quot;:

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### Voorbeeld 4 {#example-4}

Koppeling naar een map (&quot;xtk:folder&quot;-schema):

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

De standaardwaarde retourneert de id van het eerste toepasselijke parametertype-bestand dat is ingevoerd in de functie &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;.

### Voorbeeld 5 {#example-5}

In dit voorbeeld willen we een sleutel maken op een koppeling (&quot;bedrijf&quot; naar het schema &quot;cus:bedrijf&quot;) met het **xlink** -kenmerk en een veld in de tabel (&quot;email&quot;):

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Het gegenereerde schema:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

De definitie van de naamsleutel &quot;companyEmail&quot; is uitgebreid met de buitenlandse sleutel van de koppeling &quot;bedrijf&quot;. Met deze sleutel wordt een unieke index voor beide velden gegenereerd.
