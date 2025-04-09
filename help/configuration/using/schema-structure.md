---
product: campaign
title: Schema-structuur begrijpen in Adobe Campaign
description: Schemastructuur
feature: Custom Resources
role: Data Engineer, Developer
audience: configuration
content-type: reference
level: Intermediate, Experienced
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '1511'
ht-degree: 1%

---

# Schema-structuur begrijpen {#schema-structure}

De basisstructuur van een schema wordt hieronder beschreven.

## Gegevensschema’s  {#data-schema}

Voor een `<srcschema>` is de structuur als volgt:

```sql
<srcSchema>
    <enumeration>
        ...          //definition of enumerations
    </enumeration>
   
    <element>         //definition of the root <element>    (mandatory)

        <compute-string/>  //definition of a compute-string
        <dbindex>
            ...        //definition of indexes
        </dbindex>
        <key>
            ...        //definition of keys
        </key>
        <sysFilter>
            ...           //definition of filters
        </sysFilter>
        <attribute>
            ...             //definition of fields
        </attribute>
    
            <element>           //definition of sub-<element> 
                  <attribute>           //(collection, links or XML)
                  ...                         //and additional fields
                  </attribute>
                ...
            </element>
      
    </element> 

        <methods>                 //definition of SOAP methods
            <method>
                ...
            </method>
            ...
    </methods>  
          
</srcSchema>
```

Het document van XML van een gegevensschema moet het **`<srcschema>`** wortelelement met de **naam** en **namespace** attributen bevatten om de schemanaam en zijn namespace te bevolken.

```sql
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Laten we de volgende XML-inhoud gebruiken om de structuur van een gegevensschema te illustreren:

```sql
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Met het bijbehorende gegevensschema:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email"/>
    <attribute name="created"/>
    <attribute name="gender"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

## Beschrijving {#description}

Het ingangspunt van het schema is zijn belangrijkste element. Het is gemakkelijk te identificeren omdat het de zelfde naam zoals het schema heeft, en het zou het kind van het wortelelement moeten zijn. De beschrijving van de inhoud begint met dit element.

In ons voorbeeld wordt het hoofdelement vertegenwoordigd door de volgende regel:

```
<element name="recipient">
```

De elementen **`<attribute>`** en **`<element>`** die volgen op het hoofdelement worden gebruikt om de locaties en namen van de gegevensitems in de XML-structuur te definiëren.

In ons voorbeeldschema zijn de volgende:

```sql
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

De volgende regels zijn van toepassing:

* Elk **`<element>`** en **`<attribute>`** moet op naam worden geïdentificeerd via het **name-attribuut** .

  >[!IMPORTANT]
  >
  >De naam van het element moet beknopt zijn, bij voorkeur in het Engels, en alleen tekens bevatten die zijn toegestaan in de XML-naamgevingsregels.

* Alleen **`<element>`** -elementen kunnen **`<attribute>`** -elementen en **`<element>`** -elementen in de XML-structuur bevatten.
* Een **`<attribute>`** -element moet een unieke naam binnen een **`<element>`** hebben.
* Het gebruik van **`<elements>`** in gegevensreeksen met meerdere regels wordt aanbevolen.

## Datatypen {#data-types}

Het gegevenstype is ingegaan via het **type** attribuut in **`<attribute>`** en **`<element>`** elementen.

Een gedetailleerde lijst is beschikbaar in de beschrijving van het [`<attribute>` element ](../../configuration/using/schema/attribute.md) en het [`<element>` element ](../../configuration/using/schema/element.md).

Wanneer dit attribuut niet bevolkt is, **koord** is het standaardgegevenstype tenzij het element kindelementen bevat. Als het, wordt het gebruikt slechts om de elementen hiërarchisch te structureren (**`<location>`** element in ons voorbeeld).

De volgende gegevenstypen worden ondersteund in schema&#39;s:

* **koord**: karakterkoord. Voorbeelden: een voornaam, een stad, enz.

  De grootte kan via het **lengte** attribuut (facultatieve, standaardwaarde &quot;255&quot;) worden gespecificeerd.

* **boolean**: Van Boole gebied. Voorbeeld van mogelijke waarden: true/false, 0/1, ja/nee enz.
* **byte**, **kort**, **lang**: gehelen (1 byte, 2 bytes, 4 bytes). Voorbeelden: leeftijd, rekeningnummer, aantal punten, enz.
* **Dubbel**: drijvende-kommagetal met dubbele precisie. Voorbeelden: een prijs, een tarief enz.
* **datum**, **datetime**: data en data + tijden. Voorbeelden: geboortedatum, aankoopdatum enz.
* **datetimenotz**: datum + tijd zonder gegevens van de tijdzone.
* **timespan**: duur. Voorbeeld: anciënniteit.
* **Memo**: Lange tekstvelden (meerdere regels). Voorbeelden: een beschrijving, een opmerking, enz.
* **uuid**: &quot;uniqueidentifier&quot;gebieden om een GUID (die in de Server van Microsoft SQL slechts wordt gesteund) te steunen.

  >[!NOTE]
  >
  >Om a **uuid** gebied in RDBMS buiten de Server van Microsoft SQL te bevatten, `the newuuid()` functie moet met zijn standaardwaarde worden toegevoegd en worden voltooid.

Hier is ons voorbeeldschema met de ingevoerde types:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email" type="string" length="80"/>
    <attribute name="created" type="datetime"/>
    <attribute name="gender" type="byte"/>
    <element name="location">
      <attribute name="city" type="string" length="50"/>
   </element>
  </element>
</srcSchema>
```

### Toewijzing van de typen Adobe Campaign/DBMS-gegevens {#mapping-the-types-of-adobe-campaign-dbms-data}

In de onderstaande tabel staan de toewijzingen voor de typen gegevens die door Adobe Campaign worden gegenereerd voor de verschillende databasebeheersystemen.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campagne</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Orakel</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Snaar<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 als unicode) <br /> </td> 
  </tr> 
  <tr> 
   <td> Boolean <br /> </td> 
   <td> SMALLINT <br /> </td> 
   <td> NUMBER(3) <br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> KLEIN<br /> </td> 
   <td> NUMBER(3) <br /> </td> 
  </tr> 
  <tr> 
   <td> Kort <br /> </td> 
   <td> SMALLINT <br /> </td> 
   <td> NUMBER(5) <br /> </td> 
  </tr> 
  <tr> 
   <td> Double<br /> </td> 
   <td> DUBBELE PRECISIE <br /> </td> 
   <td> FLOAT <br /> </td> 
  </tr> 
  <tr> 
   <td> Lang <br /> </td> 
   <td> INTEGER <br /> </td> 
   <td> AANTAL(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64 <br /> </td> 
   <td> BIGINT <br /> </td> 
   <td> NUMBER(20) <br /> </td> 
  </tr> 
  <tr> 
   <td> Datum <br /> </td> 
   <td> DATUM<br /> </td> 
   <td> DATUM<br /> </td> 
  </tr> 
  <tr> 
   <td> Tijd <br /> </td> 
   <td> TIME <br /> </td> 
   <td> FLOAT <br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime <br /> </td> 
   <td> TIMESTAMPZ <br /> </td> 
   <td> DATUM<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz <br /> </td> 
   <td> TIMESTAMPZ <br /> </td> 
   <td> DATUM<br /> </td> 
  </tr> 
  <tr> 
   <td> Timespan <br /> </td> 
   <td> DUBBELE PRECISIE <br /> </td> 
   <td> FLOAT <br /> </td> 
  </tr> 
  <tr> 
   <td> Memo <br /> </td> 
   <td> SMS<br /> </td> 
   <td> CLOB (NCLOB als Unicode) <br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Properties {#properties}

De elementen **`<elements>`** en **`<attributes>`** van het gegevensschema kunnen met diverse eigenschappen worden verrijkt. U kunt een label vullen om het huidige element te beschrijven.

### Labels en beschrijvingen {#labels-and-descriptions}

* Het **etiket** bezit laat u een korte beschrijving ingaan.

  >[!NOTE]
  >
  >Het label is gekoppeld aan de huidige taal van de instantie.

  **Voorbeeld**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email"/>
  ```

  Het label wordt weergegeven in het invoerformulier voor de Adobe Campaign-clientconsole:

  ![](assets/d_ncs_integration_schema_label.png)

* Het **desc** bezit laat u een lange beschrijving ingaan.

  De beschrijving wordt weergegeven in het invoerformulier in de statusbalk van het hoofdvenster van de Adobe Campaign-clientconsole.

  >[!NOTE]
  >
  >De beschrijving is gekoppeld aan de huidige taal van de instantie.

  **Voorbeeld**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
  ```

### Standaardwaarden {#default-values}

Gebruik het **gebrek** bezit om een uitdrukking te bepalen die een standaardwaarde op inhoudsverwezenlijking terugkeert.

De waarde moet een expressie zijn die compatibel is met XPath-taal. Voor meer op dit, verwijs naar [ Verwijzend met XPath ](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Voorbeeld**:

* Huidige datum: **default= &quot;GetDate ()&quot;**
* Teller: **default=&quot;&#39;FRM&#39;+CounterValue (&#39;myCounter&#39;)&quot;**

  In dit voorbeeld, wordt de standaardwaarde geconstrueerd gebruikend de aaneenschakeling van een koord en roepend de **functie CounterValue** met een vrije tellernaam. Het geretourneerde getal wordt bij elke invoeging met één verhoogd.

  >[!NOTE]
  >
  >Blader in de Adobe Campaign-clientconsole naar de map **[!UICONTROL Administration > Counters]** van de Verkenner om tellers te beheren.

Als u een standaardwaarde aan een veld wilt koppelen, kunt u het `<default>`  veld of  `<sqldefault>`   gebruiken.

`<default>` : hiermee kunt u het veld vooraf vullen met een standaardwaarde wanneer u entiteiten maakt. De waarde wordt geen standaard SQL-waarde.

`<sqldefault>` : hiermee kunt u een toegevoegde waarde krijgen wanneer u een veld maakt. Deze waarde wordt weergegeven als een SQL-resultaat. Tijdens een schema-update worden alleen de nieuwe records beïnvloed door deze waarde.

### Opsommingen {#enumerations}

#### Open opsomming {#free-enumeration}

Met de **eigenschap userEnum** kunt u een open opsomming definiëren om de waarden die via dit veld zijn ingevoerd, op te slaan en weer te geven.

De syntaxis is als volgt:

`userEnum="name of enumeration"`

Deze waarden worden weergegeven in een vervolgkeuzelijst van het invoerformulier:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>Blader in de Adobe Campaign-clientconsole naar de map **[!UICONTROL Administration > Enumerations]** van de Verkenner om opsommingen te beheren.

#### Opsomming instellen {#set-enumeration}

Het **enum** bezit laat u een vaste opsomming bepalen die wordt gebruikt wanneer de lijst van mogelijke waarden vooraf gekend is.

Het **enum** attribuut verwijst naar de definitie van een opsommingsklasse die in het schema buiten het belangrijkste element wordt bevolkt.

Met opsommingen kan de gebruiker een waarde selecteren in een vervolgkeuzelijst in plaats van de waarde in een regulier invoerveld in te voeren:

![](assets/d_ncs_integration_schema_enum.png)

Voorbeeld van een opsommingsdeclaratie in het gegevensschema:

```sql
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Een opsomming wordt via het element buiten het **`<enumeration>`** hoofdelement gedeclareerd.

De opsommingseigenschappen zijn als volgt:

* **baseType**: type van gegevens verbonden aan de waarden
* **etiket**: beschrijving van de opsomming
* **naam**: naam van de opsomming
* **gebrek**: standaardwaarde van de opsomming

De opsommingswaarden worden gedeclareerd in het element **`<value>`** met de volgende kenmerken:

* **naam**: naam van de waarde die intern wordt opgeslagen
* **etiket**: etiket getoond in de grafische interface

#### dbenum-opsomming {#dbenum-enumeration}

*Het **dbenum** bezit laat u een opsomming bepalen de waarvan eigenschappen aan die van het **gelijkaardig zijn enum** bezit.

Nochtans, slaat het **naam** attribuut intern niet de waarde op, het slaat een code op die u de betrokken lijsten zonder hun schema uit te breiden laat uitbreiden.

Deze opsomming wordt bijvoorbeeld gebruikt om de aard van campagnes te specificeren.

![](assets/d_ncs_configuration_schema_dbenum.png)

### Voorbeeld {#example}

Hier volgt ons voorbeeldschema met de eigenschappen die zijn ingevuld:

```sql
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="male" value="1"/>   
    <value name="female" label="female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
    <attribute name="created" type="datetime" label="Date of creation" default="GetDate()"/>
    <attribute name="gender" type="byte" label="gender" enum="gender"/>
    <element name="location" label="Location">
      <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
   </element>
  </element>
</srcSchema>
```

## Verzamelingen {#collections}

Een verzameling is een lijst met elementen met dezelfde naam en hetzelfde hiërarchische niveau.

Het **niet verbindende** attribuut met de waarde &quot;waar&quot;laat u een inzamelingselement bevolken.

**Voorbeeld**: definitie van het **`<group>`** inzamelingselement in het schema.

```sql
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Met projectie van de XML-inhoud:

```sql
<group label="Group1"/>
<group label="Group2"/>
```

## Verwijzen naar XPath {#referencing-with-xpath}

De XPath-taal wordt in Adobe Campaign gebruikt om naar een element of kenmerk te verwijzen dat of dat tot een gegevensschema behoort.

XPath is een syntaxis waarmee u een knooppunt in de boomstructuur van een XML-document kunt zoeken.

Elementen worden aangeduid met hun naam en kenmerken worden aangeduid met de naam voorafgegaan door het teken &quot;@&quot;.

**Voorbeeld**:

* **@email** : hiermee selecteert u het e-mailbericht,
* **plaats/@city**: selecteert de &quot;stad&quot;attributen onder het **`<location>`** element
* **../@email**: hiermee selecteert u het e-mailadres in het bovenliggende element van het huidige element
* **groep`[1]/@label`**: selecteert het &quot;etiket&quot;attribuut dat het kind van het eerste **`<group>`** inzamelingselement is
* **groep`[@label='test1']`**: selecteert het &quot;etiket&quot;attribuut dat het kind van het **`<group>`** element is en de waarde &quot;test1&quot;bevat

>[!NOTE]
>
>Er wordt een extra beperking toegevoegd wanneer het pad een subelement kruist. In dit geval moet de volgende expressie tussen haakjes worden geplaatst:
>
>* **plaats/@city** is ongeldig; gelieve te gebruiken **`[location/@city]`**
>* **`[@email]`** en **@email** zijn gelijk
>

Het is ook mogelijk complexe expressies te definiëren, zoals de volgende rekenkundige bewerkingen:

* **@gender+1**: voegt 1 aan de inhoud van het **gender** attribuut toe,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: hiermee maakt u een tekenreeks door de waarde te nemen van het e-mailadres dat tussen haakjes aan de aanmaakdatum is toegevoegd (voor het type tekenreeks plaatst u de constante tussen aanhalingstekens).

Er zijn functies op hoog niveau toegevoegd aan de expressies om het potentieel van deze taal te verrijken.

U hebt toegang tot de lijst met beschikbare functies via een expressie-editor in de Adobe Campaign-clientconsole:

![](assets/d_ncs_integration_schema_function.png)

**Voorbeeld**:

* **GetDate ()**: keert de huidige datum terug
* **Jaar (@created)**: keert het jaar van de datum in het &quot;gecreeerde&quot;attribuut terug
* **GetEmailDomain (@email)**: keert het domein van het e-mailadres terug

## Een tekenreeks samenstellen via de compute string {#building-a-string-via-the-compute-string}

A **verwerkt koord** is een uitdrukking van XPath die wordt gebruikt om een koord te construeren dat een verslag in een lijst vertegenwoordigt verbonden aan het schema. **verwerkt koord** wordt hoofdzakelijk gebruikt in de grafische interface om het etiket van een geselecteerd verslag te tonen.

De **Compute string** wordt gedefinieerd via het **`<compute-string>`** element onder het hoofdelement van het gegevensschema. Een **expr** attribuut bevat een uitdrukking van XPath om de vertoning te berekenen.

**Voorbeeld**: compute koord van de ontvankelijke lijst.

```sql
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

Resultaat van het gegevens verwerkte koord voor een ontvanger: **Doe John (john.doe@aol.com)**

>[!NOTE]
>
>Als het schema geen Compute koord bevat, wordt een Compute koord bevolkt door gebrek met de waarden van de primaire sleutel van het schema.


## Meer informatie

Blader door de volgende links voor meer informatie:

* [Aan de slag met schema&#39;s](about-schema-reference.md)
* [Databasetoewijzing](database-mapping.md)
* [Beheer van koppeling](database-links.md)
* [Sleutelbeheer](database-keys.md)
* [Campagne gegevensmodel](about-data-model.md)