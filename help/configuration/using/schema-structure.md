---
solution: Campaign Classic
product: campaign
title: Schemastructuur
description: Schemastructuur
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: a469d275fdd768fbd098a0027b5096872dbf6d89
workflow-type: tm+mt
source-wordcount: '1564'
ht-degree: 1%

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

Het document van XML van een gegevensschema moet **`<srcschema>`** wortelelement met **name** en **namespace** attributen bevatten om de schemanaam en zijn namespace te bevolken.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Gebruik de volgende XML-inhoud om de structuur van een gegevensschema te illustreren:

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

Met de elementen **`<attribute>`** en **`<element>`** die het hoofdelement volgen, kunt u de locaties en namen van de gegevensitems in de XML-structuur definiëren.

In ons voorbeeldschema zijn deze:

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

De volgende regels moeten in acht worden genomen:

* Elke **`<element>`** en **`<attribute>`** moeten door naam via het **name** attribuut worden geïdentificeerd.

   >[!IMPORTANT]
   >
   >De naam van het element moet beknopt zijn, bij voorkeur in het Engels, en alleen geoorloofde tekens bevatten in overeenstemming met de XML-naamgevingsregels.

* Alleen **`<element>`**-elementen kunnen **`<attribute>`**-elementen en **`<element>`**-elementen in de XML-structuur bevatten.
* Een **`<attribute>`** element moet een unieke naam binnen **`<element>`** hebben.
* Het gebruik van **`<elements>`** in gegevensreeksen met meerdere regels wordt aanbevolen.

## Datatypen {#data-types}

Het gegevenstype wordt ingevoerd via het **type**-kenmerk in de elementen **`<attribute>`** en **`<element>`**.

Een gedetailleerde lijst is beschikbaar in de beschrijving van [`<attribute>` element](../../configuration/using/schema/attribute.md) en [`<element>` element](../../configuration/using/schema/element.md)).

Wanneer dit kenmerk niet is gevuld, is **string** het standaardgegevenstype tenzij het element onderliggende elementen bevat. Als dit het geval is, wordt het alleen gebruikt om de elementen hiërarchisch te structureren (**`<location>`** element in ons voorbeeld).

De volgende gegevenstypen worden ondersteund in schema&#39;s:

* **tekenreeks**: tekenreeks. Voorbeelden: een voornaam, een stad, enz.

   De grootte kan worden opgegeven via het kenmerk **length** (optioneel, standaardwaarde &quot;255&quot;).

* **Booleaans**: Booleaans veld. Voorbeeld van mogelijke waarden: true/false, 0/1, ja/neen, enz.
* **byte**,  **kort**,  **lang**: gehele getallen (1 byte, 2 bytes, 4 bytes). Voorbeelden: leeftijd, rekeningnummer, aantal punten enz.
* **dubbel**: drijvende-kommagetal met dubbele precisie. Voorbeelden: een prijs, een tarief enz.
* **datum**,  **datetime**: datums en datums + tijden. Voorbeelden: een geboortedatum, een aankoopdatum enz.
* **datetimenotz**: datum en tijd zonder tijdzonegegevens.
* **tijdspan**: duur. Voorbeeld: anciënniteit.
* **memo** : lange tekstvelden (meerdere regels). Voorbeelden: een beschrijving, een opmerking enz.
* **uuuid**: &quot;uniqueidentifier&quot;gebieden om een GUID (die in de Server van Microsoft SQL slechts wordt gesteund) te steunen.

   >[!NOTE]
   >
   >Om een **uuid** gebied in motoren buiten de Server van Microsoft te bevatten SQL, moet de &quot;newuid ()&quot;functie met zijn standaardwaarde worden toegevoegd en worden voltooid.

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
   <td> <strong>Teradata</strong><br /> </td> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Tekenreeks<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 if unicode)<br /> </td> 
   <td> VARCHAR (VARCHAR TEKEN STELT UNICODE IN als Unicode)<br /> </td> 
   <td> VARCHAR<br /> </td> 
   <td> VARCHAR (NVARCHAR if unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Boolean<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Kort<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(5)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Double<br /> </td> 
   <td> DUBBELE PRECISIE<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DUBBEL<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Long<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
   <td> NUMERIC(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Datum<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> Tijd<br /> </td> 
   <td> TIME<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> TIME<br /> </td> 
   <td> TIME<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> Timespan<br /> </td> 
   <td> DUBBELE PRECISIE<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DUBBEL<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Memo<br /> </td> 
   <td> TEXT<br /> </td> 
   <td> CLOB (NCLOB als Unicode)<br /> </td> 
   <td> CLOB (CLOB-TEKEN STEL UNICODE IN ALS Unicode)<br /> </td> 
   <td> CLOB(6M)<br /> </td> 
   <td> TEXT (NTEXT als Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> IMAGE<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Properties {#properties}

De elementen **`<elements>`** en **`<attributes>`** van het gegevensschema kunnen met diverse eigenschappen worden verrijkt. U kunt een label vullen om het huidige element te beschrijven.

### Labels en beschrijvingen {#labels-and-descriptions}

* Met de eigenschap **label** kunt u een korte beschrijving invoeren.

   >[!NOTE]
   >
   >Het label is gekoppeld aan de huidige taal van de instantie.

   **Voorbeeld**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   Het label kan worden weergegeven op het invoerformulier voor de Adobe Campaign-clientconsole:

   ![](assets/d_ncs_integration_schema_label.png)

* Met de eigenschap **desc** kunt u een lange beschrijving invoeren.

   De beschrijving is te zien vanaf het invoerformulier in de statusbalk van het hoofdvenster van de Adobe Campaign-clientconsole.

   >[!NOTE]
   >
   >De beschrijving is gekoppeld aan de huidige taal van de instantie.

   **Voorbeeld**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### Standaardwaarden {#default-values}

Met de eigenschap **default** kunt u een expressie definiëren die een standaardwaarde retourneert bij het maken van inhoud.

De waarde moet een expressie zijn die compatibel is met XPath-taal. Voor meer op dit, verwijs naar [Verwijzen met XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Voorbeeld**:

* Huidige datum: **default=&quot;GetDate()&quot;**
* Teller: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   In dit voorbeeld wordt de standaardwaarde geconstrueerd door de samenvoeging van een tekenreeks en het aanroepen van de functie **CounterValue** met een vrije tellernaam. Het geretourneerde getal wordt bij elke invoeging met één verhoogd.

   >[!NOTE]
   >
   >In de Adobe Campaign clientconsole wordt het knooppunt **[!UICONTROL Administration>Counters]** gebruikt om tellers te beheren.

Als u een standaardwaarde aan een veld wilt koppelen, kunt u de `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` : Hiermee kunt u het veld vooraf vullen met een standaardwaarde wanneer u entiteiten maakt. De waarde wordt geen standaard SQL-waarde.

`<sqldefault>` : kunt u een toegevoegde waarde hebben bij het maken van een veld. Deze waarde wordt weergegeven als een SQL-resultaat. Tijdens een schema-update worden alleen de nieuwe records beïnvloed door deze waarde.

### Opsommingen {#enumerations}

#### Vrije opsomming {#free-enumeration}

Met de eigenschap **userEnum** kunt u een gratis opsomming definiëren voor het onthouden en weergeven van de waarden die via dit veld zijn ingevoerd. De syntaxis is als volgt:

**userEnum=&quot;naam van opsomming&quot;**

De naam die aan de opsomming wordt gegeven kan vrij worden gekozen en met andere gebieden worden gedeeld.

Deze waarden worden weergegeven in een vervolgkeuzelijst van het invoerformulier:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>In de Adobe Campaign-clientconsole wordt het knooppunt **[!UICONTROL Administration > Enumerations]** gebruikt om opsommingen te beheren.

#### Opsomming {#set-enumeration} instellen

Met de eigenschap **enum** kunt u een vaste opsomming definiëren die wordt gebruikt wanneer de lijst met mogelijke waarden van tevoren bekend is.

Het **enum** attribuut verwijst naar de definitie van een opsommingsklasse die in het schema buiten het belangrijkste element wordt bevolkt.

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

Een opsomming wordt gedeclareerd buiten het hoofdelement via het element **`<enumeration>`**.

De opsommingseigenschappen zijn als volgt:

* **baseType**: type gegevens dat aan de waarden is gekoppeld;
* **label**: beschrijving van de opsomming;
* **naam**: naam van de opsomming;
* **standaard**: standaardwaarde van de opsomming.

De opsommingswaarden worden gedeclareerd in het element **`<value>`** met de volgende kenmerken:

* **naam**: naam van de intern opgeslagen waarde;
* **label**: label dat via de grafische interface wordt weergegeven.

#### dbenumopsomming {#dbenum-enumeration}

* Met de eigenschap **dbenum** kunt u een opsomming definiëren waarvan de eigenschappen overeenkomen met die van de eigenschap **enum**.

   Nochtans, slaat het **name** attribuut niet intern de waarde op, het slaat een code op die u de betrokken lijsten zonder hun schema uit te breiden laat uitbreiden.

   De waarden worden gedefinieerd via het knooppunt **[!UICONTROL Administration>Enumerations]**.

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

Met het **unbound**-kenmerk met de waarde &quot;true&quot; kunt u een verzamelingselement vullen.

**Voorbeeld**: definitie van het  **`<group>`** inzamelingselement in het schema.

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

* **@email**: selecteert de e-mail;
* **location/@city**: selecteert het kenmerk &quot;city&quot; onder het  **`<location>`** element
* **../@email**: selecteert het e-mailadres in het bovenliggende element van het huidige element
* **groep`[1]/@label`**: selecteert het kenmerk &quot;label&quot; dat het onderliggende element is van het eerste  **`<group>`** verzamelingselement
* **groep`[@label='test1']`**: selecteert het kenmerk &quot;label&quot; dat het onderliggende element van het  **`<group>`** element is en de waarde &quot;test1&quot; bevat

>[!NOTE]
>
>Er wordt een extra beperking toegevoegd wanneer het pad een subelement kruist. In dit geval moet de volgende expressie tussen haakjes worden geplaatst:
>
>* **location/@** cityis not valid; gebruiken  **`[location/@city]`**
>* **`[@email]`** en  **@** e-mailequivalent

>



Het is ook mogelijk complexe expressies te definiëren, zoals de volgende rekenkundige bewerkingen:

* **@gender+1**: voegt 1 toe aan de inhoud van het  **** genderkenmerk;
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: construeert een koord door de waarde van het e-mailadres te nemen dat aan de aanmaakdatum tussen haakjes wordt toegevoegd (voor het koordtype, zet de constante in citaten).

Er zijn functies op hoog niveau toegevoegd aan de expressies om het potentieel van deze taal te verrijken.

U hebt toegang tot de lijst met beschikbare functies via een expressie-editor in de Adobe Campaign-clientconsole:

![](assets/d_ncs_integration_schema_function.png)

**Voorbeeld**:

* **GetDate()**: retourneert de huidige datum
* **Jaar (@gemaakt)**: retourneert het jaar van de datum in het kenmerk &quot;created&quot;.
* **GetEmailDomain(@email)**: retourneert het domein van het e-mailadres.

## Een tekenreeks maken via de compute tekenreeks {#building-a-string-via-the-compute-string}

Een **Berekende tekenreeks** is een XPath-expressie die wordt gebruikt om een tekenreeks samen te stellen die een record vertegenwoordigt in een tabel die is gekoppeld aan het schema. **Compute** stringt wordt vooral gebruikt in de grafische interface om het label van een geselecteerde record weer te geven.

De **Berekende tekenreeks** wordt gedefinieerd via het element **`<compute-string>`** onder het hoofdelement van het gegevensschema. Een **expr** attribuut bevat een uitdrukking van XPath om de vertoning te berekenen.

**Voorbeeld**: berekend koord van de ontvankelijke lijst.

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

