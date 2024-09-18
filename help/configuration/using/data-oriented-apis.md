---
product: campaign
title: Gegevensgerichte API’s
description: Gegevensgerichte API’s
feature: API
role: Data Engineer, Developer
exl-id: a392c55e-541a-40b1-a910-4a6dc79abd2d
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '1813'
ht-degree: 0%

---

# Gegevensgerichte API’s{#data-oriented-apis}

Met gegevensgeoriënteerde API&#39;s kunt u het gehele gegevensmodel gebruiken.

## Overzicht van het gegevensmodel {#overview-of-the-datamodel}

Adobe Campaign biedt geen specifieke lees-API per entiteit (geen functie getRecipient of getDelivery, enz.). Met de methoden QUERY &amp; WRITER-gegevens lezen en wijzigen hebt u toegang tot de gegevens van het model.

Met Adobe Campaign kunt u verzamelingen beheren: met query&#39;s kunt u een set gegevens herstellen die in de gehele basis zijn verzameld. In tegenstelling tot toegang in SQL-modus, retourneren Adobe Campaign API&#39;s een XML-structuur in plaats van gegevenskolommen. Adobe Campaign maakt dus samengestelde documenten met alle verzamelde gegevens.

Deze werkende wijze biedt geen één-op-één afbeelding tussen de attributen en de elementen van de documenten van XML en de kolommen van de lijsten in het gegevensbestand aan.

XML-documenten worden opgeslagen in MEMO-tekstvelden van de database.

## Beschrijving van het model {#description-of-the-model}

U moet bekend zijn met het Adobe Campaign-gegevensmodel om de velden van de database in uw scripts te kunnen verwerken.

Voor een presentatie van het gegevensmodel, verwijs naar de [ het modelbeschrijving van Gegevens van Adobe Campaign ](../../configuration/using/data-model-description.md).

## Query en schrijver {#query-and-writer}

In het volgende introductieschema worden uitwisselingen op laag niveau beschreven voor lezen (ExecuteQuery) en schrijven (Writer) tussen database en klant (webpagina&#39;s of Adobe Campaign-clientconsole).

![](assets/s_ncs_integration_webservices_schema_writer.png)

### ExecuteQuery {#executequery}

Voor kolommen en voorwaarden kunt u Query&#39;s gebruiken.

Hierdoor kunt u de onderliggende SQL isoleren. De querytaal is niet afhankelijk van de onderliggende engine: sommige functies worden opnieuw toegewezen, waardoor meerdere SELECT SQL-orders kunnen worden gegenereerd.

Voor meer op dit, verwijs naar [ Voorbeeld op de methode &quot;ExecuteQuery&quot;van schema &quot;xtk:queryDef&quot;](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-).

De **ExecuteQuery** methode wordt voorgesteld in [ ExecuteQuery (xtk:queryDef) ](#executequery--xtk-querydef-).

### Schrijven {#write}

Met schrijfopdrachten kunt u eenvoudige of complexe documenten schrijven met items in een of meer tabellen van de basis.

Transactionele APIs laat u aansluitingen via het **updateOrInsert** bevel beheren: één bevel laat u gegevens tot stand brengen of bijwerken. U kunt wijziging het samenvoegen (**ook vormen samenvoegt**): deze werkende wijze laat u gedeeltelijke updates machtigen.

De structuur van XML biedt een logische mening van de gegevens aan en laat u de fysieke structuur van de SQL lijst negeren.

De schrijfmethode wordt voorgesteld in [ Write/WriteCollection (xtk:zitting) ](#write---writecollection--xtk-session-).

## ExecuteQuery (xtk:queryDef) {#executequery--xtk-querydef-}

Deze methode laat u vragen van gegevens uitvoeren verbonden aan een schema. Het neemt een authentificatietekenreeks (moet worden het programma geopend) en een document van XML beschrijvend de vraag die als parameters moet worden voorgelegd. De retourparameter is een XML-document dat het resultaat bevat van de query in de indeling van het schema waarnaar de query verwijst.

Definitie van de methode &quot;ExecuteQuery&quot; in het schema &quot;xtk:queryDef&quot;:

```xml
<method name="ExecuteQuery" const="true">
  <parameters>
    <param desc="Output XML document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

>[!NOTE]
>
>Dit is een const-methode. De invoerparameters worden in een XML-document opgenomen in de indeling van het schema &quot;xtk:queryDef&quot;.

### Indeling van het XML-document van de invoerquery {#format-of-the-xml-document-of-the-input-query}

De structuur van het XML-document van de query wordt beschreven in het schema &quot;xtk:queryDef&quot;. In dit document worden de clausules van een SQL-query beschreven: &quot;select&quot;, &quot;where&quot;, &quot;order by&quot;, &quot;group by&quot;, &quot;have&quot;.

```xml
<queryDef schema="schema_key" operation="operation_type">
  <select>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </select>
  <where> 
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ... 
  </where>
  <orderBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </orderBy>
  <groupBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </groupBy>
  <having>
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ...
  </having>
</queryDef>
```

Een subquery ( `<subquery>` ) kan worden gedefinieerd in een `<condition> ` -element. De syntaxis voor een   `<subquery> `   element is gebaseerd op de syntaxis van een    `<querydef>` .

Voorbeeld van een `<subquery>  : </subquery>`

```xml
<condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
  <subQuery schema="xtk:operatorGroup">
     <select>
       <node expr="[@operator-id]" />
     </select>
     <where>
       <condition expr="[@group-id]=$long(../@owner-id)"/>
     </where>
   </subQuery>
</condition>  
  
```

Een vraag moet een beginschema van het **schema** attribuut van verwijzingen voorzien.

Het gewenste type van verrichting is ingegaan in het **verrichting** attribuut en bevat één van de volgende waarden:

* **krijgt**: wint een verslag van de lijst terug en keert een fout terug als het gegeven niet bestaat,
* **getIfExists**: wint een verslag van de lijst terug en keert een leeg document terug als het gegeven niet bestaat,
* **uitgezocht**: creeert een curseur om verscheidene verslagen terug te keren en een leeg document terug te keren als er geen gegevens zijn,
* **telling**: keert een gegevenstelling terug.

De **XPath** syntaxis wordt gebruikt om van gegevens de plaats te bepalen die op het inputschema worden gebaseerd. Voor verdere informatie over XPparagraphs, verwijs naar [ schema&#39;s van Gegevens ](../../configuration/using/data-schemas.md).

#### Voorbeeld met de bewerking get {#example-with-the--get--operation}

Haalt de achternaam en voornaam van een ontvanger (&quot;nms:ontvanger&quot;-schema) op met een filter in de e-mail.

```xml
<queryDef schema="nms:recipient" operation="get">
  <!-- fields to retrieve -->
  <select>
    <node expr="@firstName"/>
    <node expr="@lastName"/>
  </select> 

  <!-- condition on email -->
  <where>  
    <condition expr="@email= 'john.doe@aol.com'"/>
  </where>
</queryDef>
```

#### Voorbeeld met de bewerking &#39;select&#39; {#example-with-the--select--operation}

Retourneert de lijst met ontvangers die zijn gefilterd op een map en het e-maildomein met een sortering in aflopende volgorde op de geboortedatum.

```xml
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <!-- builds a string with the concatenation of the last name and first name separated by a dash -->      
    <node expr="@lastName+'-'+@firstName"/>
    <!-- get year of birth date -->
    <node expr="Year(@birthDate)"/>
  </select> 

  <where>  
     <condition expr="[@folder-id] = 1234 and @domain like 'Adobe%'"/>
  </where>

  <!-- order by birth date -->
  <orderBy>
    <node expr="@birthDate" sortDesc="true"/> <!-- by default sortDesc="false" -->
  </orderBy>
</queryDef>
```

Expressies kunnen eenvoudige velden of complexe expressies zijn, zoals rekenkundige bewerkingen of het samenvoegen van tekenreeksen.

Om het aantal terug te keren verslagen te beperken, voeg **lineCount** attributen aan het `<querydef>` element toe.

Om het aantal verslagen te beperken die door de vraag aan 100 zijn teruggekeerd:

```xml
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

Om volgende 100 verslagen terug te winnen, stel de zelfde vraag opnieuw in werking, toevoegend het **startLine** attribuut.

```xml
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### Voorbeeld met de bewerking &#39;count&#39; {#example-with-the--count--operation}

Om het aantal verslagen op een vraag te tellen:

```xml
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the email -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>Ook hier gebruiken we de voorwaarde uit het vorige voorbeeld. De clausules `<select>` en  worden niet gebruikt. `</select>`

#### Gegevensgroepering {#data-grouping}

U kunt als volgt e-mailadressen ophalen waarnaar meerdere keren wordt verwezen:

```xml
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <node expr="count(@email)"/>
  </select>

  <!-- email grouping clause -->
  <groupby>
    <node expr="@email"/>
  </groupby>

  <!-- grouping condition -->
  <having>
    <condition expr="count(@email) > 1"/>
  </having>

</queryDef>
```

De vraag kan worden vereenvoudigd door het **groupBy** attribuut aan het te groeperen gebied direct toe te voegen:

```xml
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>U hoeft het element `<groupby>` niet meer te vullen.

#### Bracketing in omstandigheden {#bracketing-in-conditions}

Hier volgen twee voorbeelden van haakjes op dezelfde voorwaarde.

* De eenvoudige versie in één expressie:

  ```xml
  <where>
    <condition expr="(@age > 15 or @age <= 45) and  (@city = 'Newton' or @city = 'Culver City') "/>
  </where>
  ```

* De gestructureerde versie met `<condition>` -elementen:

  ```xml
  <where>
    <condition bool-operator="AND">
      <condition expr="@age > 15" bool-operator="OR"/>
      <condition expr="@age <= 45"/>
    </condition>
    <condition>
      <condition expr="@city = 'Newton'" bool-operator="OR"/>
      <condition expr="@city = 'Culver City'"/>
    </condition>
  </where>
  ```

Het is mogelijk de operator &#39;OR&#39; te vervangen door de operator &#39;IN&#39; wanneer er verschillende voorwaarden gelden voor hetzelfde veld:

```xml
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

Deze syntaxis vereenvoudigt de query wanneer meer dan twee gegevens in de voorwaarde worden gebruikt.

#### Voorbeelden van koppelingen {#examples-on-links}

* Koppelingen 1-1 of N1: als de tabel de externe sleutel heeft (de koppeling begint in de tabel), kunnen de velden van de gekoppelde tabel worden gefilterd of rechtstreeks worden opgehaald.

  Voorbeeld van een filter op het maplabel:

  ```xml
  <where>
    <condition expr="[folder/@label] like 'Segment%'"/>
  </where>
  ```

  U kunt als volgt de velden van de map ophalen uit het schema &quot;nms:ontvanger&quot;:

  ```xml
  <select>
    <!-- label of recipient folder -->
    <node expr="[folder/@label]"/>
    <!-- displays the string count of the folder -->
    <node expr="partition"/>
  </select>
  ```

* De verbindingen van de inzameling (1N): Het filtreren op de gebieden van een inzamelingslijst moet via **worden uitgevoerd BESTAAT** of **** exploitant NIET BESTAAT.

  Om de ontvangers te filtreren die aan de de informatiedienst van de &quot;Krantenbrief&quot;zijn geabonneerd:

  ```xml
  <where>
    <condition expr="subscription" setOperator="EXISTS">
      <condition expr="@name = 'Newsletter'"/>
    </condition>
  </where>
  ```

  Directe herwinning van de gebieden van een inzamelingsverbinding van de `<select>` clausule wordt niet geadviseerd omdat de vraag een kardinaal product terugkeert. Deze wordt alleen gebruikt wanneer de gekoppelde tabel slechts één record bevat (bijvoorbeeld `<node expr="">` ).

  Voorbeeld op de verzamelingskoppeling &quot;Abonnement&quot;:

  ```xml
  <select>
    <node expr="subscription/@label"/>
  </select>
  ```

  Het is mogelijk om een sublijst op te halen met de elementen van een verzamelingskoppeling in de `<select>` -component. De XPath van de gebieden waarnaar wordt verwezen zijn contextueel van het inzamelingselement.

  De filterelementen ( `<orderby>` ) en de beperkingselementen ( `<where>` ) kunnen aan het inzamelingselement worden toegevoegd.

  In dit voorbeeld retourneert de query voor elke ontvanger de e-mail en de lijst met informatiediensten waarop de ontvanger zich abonneert:

  ```xml
  <queryDef schema="nms:recipient" operation="select">
    <select>
      <node expr="@email"/>
  
      <!-- collection table (unbound type) -->
      <node expr="subscription">  
        <node expr="[service/@label]"/>    
        <!-- sub-condition on the collection table -->
        <where>  
          <condition expr="@expirationDate >= GetDate()"/>
        </where>
        <orderBy>
          <node expr="@expirationDate"/> 
        </orderBy>
      </node>
    </select> 
  </queryDef>
  ```

#### De parameters van de component &#39;where&#39; en &#39;select&#39; binden {#binding-the-parameters-of-the--where--and--select--clause}

Door de binding van parameters kan de engine de waarden instellen van de parameters die in de query worden gebruikt. Dit is zeer nuttig, aangezien de motor voor het ontsnappen van waarden verantwoordelijk is, en er het extra voordeel van een geheime voorgeheugen voor de parameters is die moeten worden teruggewonnen.

Wanneer een vraag wordt geconstrueerd, worden de &quot;gebonden&quot;waarden vervangen door een karakter (? in ODBC, `#[index]#` in postgres...) in de tekst van de SQL-query.

```xml
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

Als u wilt voorkomen dat een parameter wordt gebonden, moet het kenmerk &quot;noSqlBind&quot; worden gevuld met de waarde &quot;true&quot;.

>[!IMPORTANT]
>
>Als de vraag &quot;orde-door&quot;of &quot;groep-door&quot;instructies omvat, zullen de gegevensbestandmotoren niet waarden kunnen &quot;binden&quot;. U moet het @noSqlBind= &quot;waar&quot;attribuut op &quot;selecteren&quot;en/of &quot;waar&quot;instructies van de vraag plaatsen.


### Documentindeling uitvoeren {#output-document-format}

De retourparameter is een XML-document in de indeling van het schema dat aan de query is gekoppeld.

Voorbeeld van een terugkeer van het &quot;nms:ontvanger&quot;schema op &quot;krijgt&quot;verrichting:

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

Bij een &quot;select&quot;-bewerking is het geretourneerde document een opsomming van elementen:

```xml
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

Voorbeeld van een document dat wordt geretourneerd voor bewerking van het type &quot;count&quot;:

```xml
<recipient count="3"/>
```

#### Alias {#alias}

Met een alias kunt u de locatie van gegevens in het uitvoerdocument wijzigen. Het **alias** attribuut moet een XPath op het overeenkomstige gebied specificeren.

```xml
<queryDef schema="nms:recipient" operation="get">
  <select>
    <node expr="@firstName" alias="@firstName"/>
    <node expr="@lastName"/>
    <node expr="[folder/@label]" alias="@My_folder"/>
  </select> 
</queryDef>
```

Retourneert:

```xml
<recipient My_folder="Recipients" First name ="John" lastName="Doe"/>
```

In plaats van:

```xml
<recipient firstName="John" lastName="Doe">
  <folder label="Recipients"/>
</recipient>
```

### Voorbeeld van SOAP berichten {#example-of-soap-messages}

* Query:

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <queryDef operation="get" schema="nms:recipient" xtkschema="xtk:queryDef">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@id = 3599"/>
            </where>
          </queryDef>
        </entity>
      </ExecuteQuery>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Reactie:

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
        </pdomOutput>
      </ExecuteQueryResponse>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

## Write/WriteCollection (xtk:session) {#write---writecollection--xtk-session-}

Deze services worden gebruikt om een entiteit (&quot;Write&quot;-methode) of een verzameling entiteiten (&quot;WriteCollection&quot;-methode) in te voegen, bij te werken of te verwijderen.

De bij te werken entiteiten zijn gekoppeld aan een gegevensschema. De invoerparameters zijn een verificatietekenreeks (moet worden aangemeld) en een XML-document met de gegevens die moeten worden bijgewerkt.

Dit document wordt aangevuld met instructies voor het configureren van de schrijfprocedures.

De aanroep retourneert geen gegevens, behalve fouten.

Definitie van de methoden &quot;Write&quot; en &quot;WriteCollection&quot; in het schema &quot;xtk:session&quot;:

```xml
<method name="Write" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference document"/>
  </parameters>
</method>
<method name="WriteCollection" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference collection document"/>
  </parameters>
</method>
```

>[!NOTE]
>
>Dit is een &quot;statische&quot; methode. De invoerparameters worden opgenomen in een XML-document in de indeling van het schema dat moet worden bijgewerkt.

### Overzicht {#overview}

De afstemming van gegevens werkt op basis van de definitie van de sleutels die zijn ingevoerd in het bijbehorende schema. De schrijfprocedure zoekt naar de eerste in aanmerking komende sleutel op basis van de gegevens die in het invoerdocument zijn ingevoerd. De entiteit wordt ingevoegd of bijgewerkt op basis van haar bestaan in de database.

De sleutel van het schema van de te bijwerken entiteit wordt voltooid gebaseerd op het **xtkschema** attribuut.

De verzoeningssleutel kan daarom met het **_key** attribuut worden gedwongen die de lijst van XPails bevatten die omhoog de sleutel (door komma&#39;s worden gescheiden) maken.

Het is mogelijk om het type van verrichting te dwingen door het **_operation** attribuut met de volgende waarden te bevolken:

* **tussenvoegsel**: krachten de toevoeging van het verslag (de verzoeningssleutel wordt niet gebruikt),
* **insertOrUpdate**: werkt of neemt het verslag afhankelijk van de verzoeningssleutel (standaardwijze) bij,
* **update**: werkt het verslag bij; doet niets als het gegeven niet bestaat,
* **schrapping**: schrapt de verslagen,
* **niets**: gebruikt slechts voor verbindingsverzoening, zonder update of toevoeging.

### Voorbeeld met de methode &#39;Write&#39; {#example-with-the--write--method}

Een ontvanger bijwerken of invoegen (impliciete bewerking &quot;insertOrUpdate&quot;) met e-mailadres, geboortedatum en plaats:

```xml
<recipient xtkschema="nms:recipient" email="john.doe@adobe.com" birthDate="1956/05/04" folder-id=1203 _key="@email, [@folder-id]">
  <location city="Newton"/>
</recipient>
```

Een ontvanger verwijderen:

```xml
<recipient xtkschema="nms:recipient" _operation="delete" email="rene.dupont@adobe.com" folder-id=1203 _key="@email, [@folder-id]"/>
```

>[!NOTE]
>
>Voor een verwijderingsbewerking moet het invoerdocument alleen de velden bevatten waaruit de afstemmingssleutel bestaat.

### Voorbeeld met de methode WriteCollection {#example-with-the--writecollection--method}

Bijwerken of invoegen voor verschillende ontvangers:

```xml
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### Voorbeeld van koppelingen {#example-on-links}

#### Voorbeeld 1 {#example-1}

De map koppelen aan een ontvanger op basis van de interne naam (@name).

```xml
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

De kenmerken &quot;_key&quot; en &quot;_operation&quot; kunnen worden ingevoerd op een gekoppeld element. Het gedrag op dit element is hetzelfde als op het hoofdelement van het invoerschema.

De definitie van de sleutel van de hoofdentiteit (&quot;nms:ontvanger&quot;) bestaat uit een veld van een gekoppelde tabel (element `<folder>` schema &quot;xtk:folder&quot;) en de e-mail.

>[!NOTE]
>
>De bewerking &quot;none&quot; die in het mappenelement is ingevoerd, definieert een afstemming in de map zonder update of invoeging.

#### Voorbeeld 2 {#example-2}

Het bijwerken van het bedrijf (verbonden lijst in &quot;cus:bedrijf&quot;schema) van een ontvanger:

```xml
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### Voorbeeld 3 {#example-3}

Een ontvanger aan een groep toevoegen met de groeprelatietabel (&quot;nms:rcpGrpRel&quot;):

```xml
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>De definitie van de sleutel wordt niet ingevoerd in het element `<rcpgroup>` omdat een impliciete sleutel die op de groepsnaam wordt gebaseerd, in het schema &quot;nms:group&quot; wordt gedefinieerd.

### XML-verzamelingselementen {#xml-collection-elements}

Door gebrek, moeten alle inzamelingselementen worden bevolkt om de de inzamelingselementen van XML bij te werken. Gegevens uit de database worden vervangen door gegevens uit het invoerdocument. Als het document alleen de elementen bevat die moeten worden bijgewerkt, moet u het kenmerk &quot;_operation&quot; invullen voor alle verzamelingselementen die moeten worden bijgewerkt om een samenvoeging met de XML-gegevens van de database te forceren.

### Voorbeeld van SOAP berichten {#example-of-soap-messages-1}

* Query:

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <Write xmlns='urn:xtk:persist' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <domDoc xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <recipient xtkschema="nms:recipient" email="rene.dupont@adobe.com" firstName="René" lastName="Dupont" _key="@email">
        </domDoc>
      </Write>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Reactie:

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <WriteResponse xmlns='urn:' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
      </WriteResponse>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

  Retourneren met fout:

  ```xml
  <?xml version='1.0'?>
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <SOAP-ENV:Fault>
        <faultcode>SOAP-ENV:Server</faultcode>
        <faultstring xsi:type="xsd:string">Error while executing the method 'Write' of service 'xtk:persist'.</faultstring>
        <detail xsi:type="xsd:string">PostgreSQL error: ERROR:  duplicate key violates unique constraint &quot;nmsrecipient_id&quot;Impossible to save document of type 'Recipients (nms:recipient)'</detail>
      </SOAP-ENV:Fault>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```
