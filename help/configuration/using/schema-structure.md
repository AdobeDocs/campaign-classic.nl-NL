---
product: campaign
title: Schemastructuur
description: Schemastructuur
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 2%

---

# Schemastructuur{#schema-structure}

De basisstructuur van een `<srcschema>` is als volgt:

```
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

Het XML-document van een gegevensschema moet het **`<srcschema>`** hoofdelement met de **name** en **namespace** attributen om de schemanaam en zijn namespace te bevolken.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Laten we de volgende XML-inhoud gebruiken om de structuur van een gegevensschema te illustreren:

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Met het bijbehorende gegevensschema:

```
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

Het punt van ingang van het schema is zijn belangrijkste element. Het is gemakkelijk te identificeren omdat het de zelfde naam zoals het schema heeft, en het zou het kind van het wortelelement moeten zijn. De beschrijving van de inhoud begint met dit element.

In ons voorbeeld wordt het hoofdelement vertegenwoordigd door de volgende regel:

```
<element name="recipient">
```

De elementen **`<attribute>`** en **`<element>`** die volgen op het hoofdelement, kunt u de locaties en namen van de gegevensitems in de XML-structuur definiëren.

In ons voorbeeldschema zijn de volgende:

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

De volgende regels moeten in acht worden genomen:

* Elk **`<element>`** en **`<attribute>`** moet met naam worden geïdentificeerd via de **name** kenmerk.

  >[!IMPORTANT]
  >
  >De naam van het element moet beknopt zijn, bij voorkeur in het Engels, en alleen geoorloofde tekens bevatten in overeenstemming met de XML-naamgevingsregels.

* Alleen **`<element>`** elementen kunnen bevatten **`<attribute>`** elementen en **`<element>`** elementen in de XML-structuur.
* An **`<attribute>`** element moet een unieke naam binnen een **`<element>`**.
* Het gebruik van **`<elements>`** in gegevensreeksen met meerdere regels wordt aanbevolen.

## Datatypen {#data-types}

Het gegevenstype is ingevoerd via het dialoogvenster **type** in het dialoogvenster **`<attribute>`** en **`<element>`** elementen.

Een gedetailleerde lijst is beschikbaar in de beschrijving van [`<attribute>` element](../../configuration/using/schema/attribute.md) en de [`<element>` element](../../configuration/using/schema/element.md)).

Wanneer dit kenmerk niet is gevuld, **string** is het standaardgegevenstype, tenzij het element onderliggende elementen bevat. Als dit het geval is, wordt het alleen gebruikt om de elementen hiërarchisch te structureren (**`<location>`** -element in ons voorbeeld).

De volgende gegevenstypen worden ondersteund in schema&#39;s:

* **string**: tekenreeks. Voorbeelden: een voornaam, een stad, enz.

  De grootte kan worden opgegeven via de **length** kenmerk (optioneel, standaardwaarde &quot;255&quot;).

* **boolean**: Booleaans veld. Voorbeeld van mogelijke waarden: true/false, 0/1, ja/nee enz.
* **byte**, **kort**, **lang**: gehele getallen (1 byte, 2 bytes, 4 bytes). Voorbeelden: leeftijd, rekeningnummer, aantal punten, enz.
* **double**: drijvende-kommagetal met dubbele precisie. Voorbeelden: een prijs, een tarief enz.
* **date**, **datetime**: datums en datums + tijden. Voorbeelden: geboortedatum, aankoopdatum enz.
* **datetimenotz**: datum + tijd zonder tijdzonegegevens.
* **timespan**: duur. Voorbeeld: anciënniteit.
* **memo**: lange tekstvelden (meerdere regels). Voorbeelden: een beschrijving, een opmerking enz.
* **uuid**: &quot;uniqueidentifier&quot;gebieden om een GUID (die in de Server van Microsoft SQL slechts wordt gesteund) te steunen.

  >[!NOTE]
  >
  >Een **uuid** in andere engines dan Microsoft SQL Server moet de functie &quot;newuid()&quot; worden toegevoegd en aangevuld met de standaardwaarde.

Hier is ons voorbeeldschema met de ingevoerde types:

```
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
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Tekenreeks<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 als unicode)<br /> </td> 
   <td> VARCHAR (NVARCHAR indien unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Boolean<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Kort<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(5)<br /> </td> 
   <td> SMALLINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Dubbel<br /> </td> 
   <td> DUBBELE PRECISIE<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Lang<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Datum<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> Tijd<br /> </td> 
   <td> TIJD<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Datumtijd<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> Timespan<br /> </td> 
   <td> DUBBELE PRECISIE<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Memo<br /> </td> 
   <td> TEXT<br /> </td> 
   <td> CLOB (NCLOB als Unicode)<br /> </td> 
   <td> TEXT (NTEXT als Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Klodder<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> AFBEELDING<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Properties {#properties}

De **`<elements>`** en **`<attributes>`** elementen van het gegevensschema kunnen met diverse eigenschappen worden verrijkt. U kunt een label vullen om het huidige element te beschrijven.

### Labels en beschrijvingen {#labels-and-descriptions}

* De **label** kunt u een korte beschrijving invoeren.

  >[!NOTE]
  >
  >Het label is gekoppeld aan de huidige taal van de instantie.

  **Voorbeeld**:

  ```
  <attribute name="email" type="string" length="80" label="Email"/>
  ```

  Het label kan worden weergegeven op het invoerformulier voor de Adobe Campaign-clientconsole:

  ![](assets/d_ncs_integration_schema_label.png)

* De **desc** kunt u een lange beschrijving invoeren.

  De beschrijving is te zien vanaf het invoerformulier in de statusbalk van het hoofdvenster van de Adobe Campaign-clientconsole.

  >[!NOTE]
  >
  >De beschrijving is gekoppeld aan de huidige taal van de instantie.

  **Voorbeeld**:

  ```
  <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
  ```

### Standaardwaarden {#default-values}

De **default** Met deze eigenschap kunt u een expressie definiëren die een standaardwaarde retourneert bij het maken van inhoud.

De waarde moet een expressie zijn die compatibel is met XPath-taal. Raadpleeg voor meer informatie hierover [Verwijzen naar XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Voorbeeld**:

* Huidige datum: **default=&quot;GetDate()&quot;**
* Teller: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

  In dit voorbeeld wordt de standaardwaarde geconstrueerd door de aaneenschakeling van een tekenreeks en het aanroepen van de **CounterValue** functie met een vrije tellernaam. Het geretourneerde getal wordt bij elke invoeging met één verhoogd.

  >[!NOTE]
  >
  >In de Adobe Campaign-clientconsole **[!UICONTROL Administration>Counters]** de knoop wordt gebruikt om tellers te beheren.

Als u een standaardwaarde aan een veld wilt koppelen, kunt u de opdracht `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` : hiermee kunt u het veld vooraf invullen met een standaardwaarde wanneer u entiteiten maakt. De waarde wordt geen standaard SQL-waarde.

`<sqldefault>` : hiermee kunt u een toegevoegde waarde krijgen wanneer u een veld maakt. Deze waarde wordt weergegeven als een SQL-resultaat. Tijdens een schema-update worden alleen de nieuwe records beïnvloed door deze waarde.

### Opsommingen {#enumerations}

#### Vrije opsomming {#free-enumeration}

De **userEnum** Met deze eigenschap kunt u een gratis opsomming definiëren voor het onthouden en weergeven van de waarden die via dit veld worden ingevoerd. De syntaxis is als volgt:

**userEnum=&quot;naam van opsomming&quot;**

De naam die aan de opsomming wordt gegeven kan vrij worden gekozen en met andere gebieden worden gedeeld.

Deze waarden worden weergegeven in een vervolgkeuzelijst van het invoerformulier:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>In de Adobe Campaign-clientconsole **[!UICONTROL Administration > Enumerations]** node wordt gebruikt om opsommingen te beheren.

#### Opsomming instellen {#set-enumeration}

De **enum** Met eigenschap kunt u een vaste opsomming definiëren die wordt gebruikt wanneer de lijst met mogelijke waarden vooraf bekend is.

De **enum** kenmerk verwijst naar de definitie van een opsommingsklasse die buiten het hoofdelement in het schema is geplaatst.

Met opsommingen kan de gebruiker een waarde in een vervolgkeuzelijst selecteren in plaats van de waarde in te voeren in een gewoon invoerveld:

![](assets/d_ncs_integration_schema_enum.png)

Voorbeeld van een opsommingsdeclaratie in het gegevensschema:

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Een opsomming wordt buiten het hoofdelement gedeclareerd via de **`<enumeration>`** element.

De opsommingseigenschappen zijn als volgt:

* **baseType**: type gegevens dat aan de waarden is gekoppeld,
* **label**: beschrijving van de opsomming,
* **name**: naam van de opsomming,
* **default**: standaardwaarde van de opsomming.

De opsommingswaarden worden gedeclareerd in de **`<value>`** element met de volgende kenmerken:

* **name**: naam van de waarde die intern is opgeslagen,
* **label**: label dat wordt weergegeven via de grafische interface.

#### dbenum-opsomming {#dbenum-enumeration}

* De **dbenum** Met eigenschap kunt u een opsomming definiëren waarvan de eigenschappen overeenkomen met die van de **enum** eigenschap.

  De **name** het attribuut slaat intern niet de waarde op, het slaat een code op die u de betrokken lijsten laat uitbreiden zonder hun schema te wijzigen.

  De waarden worden gedefinieerd via de **[!UICONTROL Administration>Enumerations]** knooppunt.

  Deze opsomming wordt bijvoorbeeld gebruikt om de aard van campagnes op te geven.

  ![](assets/d_ncs_configuration_schema_dbenum.png)

### Voorbeeld {#example}

Hier volgt ons voorbeeldschema met de eigenschappen die zijn ingevuld:

```
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

De **ongebonden** Met kenmerk met de waarde &quot;true&quot; kunt u een verzamelingselement vullen.

**Voorbeeld**: definitie van de **`<group>`** verzamelingselement in het schema.

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Met projectie van de XML-inhoud:

```
<group label="Group1"/>
<group label="Group2"/>
```

## Verwijzen naar XPath {#referencing-with-xpath}

De XPath-taal wordt in Adobe Campaign gebruikt om naar een element of kenmerk te verwijzen dat of dat tot een gegevensschema behoort.

XPath is een syntaxis waarmee u een knooppunt in de boomstructuur van een XML-document kunt zoeken.

Elementen worden aangeduid met hun naam en kenmerken worden aangeduid met de naam voorafgegaan door het teken &quot;@&quot;.

**Voorbeeld**:

* **@email**: hiermee selecteert u het e-mailbericht.
* **location/@city**: selecteert het kenmerk &quot;city&quot; onder het selectievakje **`<location>`** element
* **../@email**: selecteert het e-mailadres in het bovenliggende element van het huidige element
* **groep`[1]/@label`**: selecteert het kenmerk &quot;label&quot; dat het onderliggende element van het eerste object is **`<group>`** verzamelingselement
* **groep`[@label='test1']`**: selecteert het kenmerk &quot;label&quot; dat het onderliggende element is van het dialoogvenster **`<group>`** -element en bevat de waarde &quot;test1&quot;

>[!NOTE]
>
>Er wordt een extra beperking toegevoegd wanneer het pad een subelement kruist. In dit geval moet de volgende expressie tussen haakjes worden geplaatst:
>
>* **location/@city** is ongeldig; gebruik **`[location/@city]`**
>* **`[@email]`** en **@email** gelijkwaardig
>

Het is ook mogelijk complexe expressies te definiëren, zoals de volgende rekenkundige bewerkingen:

* **@gender+1**: voegt 1 toe aan de inhoud van de **sekse** kenmerk,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: maakt een tekenreeks door de waarde te nemen van het e-mailadres dat tussen haakjes aan de aanmaakdatum is toegevoegd (voor het type tekenreeks plaatst u de constante tussen aanhalingstekens).

Er zijn functies op hoog niveau toegevoegd aan de expressies om het potentieel van deze taal te verrijken.

U hebt toegang tot de lijst met beschikbare functies via een expressie-editor in de Adobe Campaign-clientconsole:

![](assets/d_ncs_integration_schema_function.png)

**Voorbeeld**:

* **GetDate()**: retourneert de huidige datum
* **Jaar (@gemaakt)**: retourneert het jaar van de datum in het kenmerk &quot;created&quot;.
* **GetEmailDomain(@email)**: retourneert het domein van het e-mailadres.

## Een tekenreeks samenstellen via de compute string {#building-a-string-via-the-compute-string}

A **Rekenreeks** is een XPath-expressie die wordt gebruikt om een tekenreeks samen te stellen die een record vertegenwoordigt in een tabel die aan het schema is gekoppeld. **Rekenreeks** wordt voornamelijk gebruikt in de grafische interface om het label van een geselecteerde record weer te geven.

De **Rekenreeks** wordt gedefinieerd via de **`<compute-string>`** element onder het belangrijkste element van het gegevensschema. An **expr** -kenmerk bevat een XPath-expressie waarmee de weergave wordt berekend.

**Voorbeeld**: compute string van de ontvangende tabel.

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

Resultaat van de berekende tekenreeks voor een ontvanger: **Doe John (john.doe@aol.com)**

>[!NOTE]
>
>Als het schema geen Compute koord bevat, wordt een Compute koord bevolkt door gebrek met de waarden van de primaire sleutel van het schema.
