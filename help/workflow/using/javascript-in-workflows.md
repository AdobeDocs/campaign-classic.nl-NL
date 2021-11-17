---
product: campaign
title: Voorbeelden van JavaScript-code in workflows
description: Deze voorbeelden laten zien hoe u JavaScript-code kunt gebruiken in een workflow
audience: workflow
content-type: reference
topic-tags: advanced-management
source-git-commit: fa3a3e1801738928876734aa42342f0a5b49e320
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 2%

---

# Voorbeelden van JavaScript-code in workflows{#javascript-in-workflows}

![](../../assets/common.svg)

Deze voorbeelden laten zien hoe u JavaScript-code in een workflow kunt gebruiken:

* [Naar de database schrijven](#write-example)
* [De database opvragen](#read-example)
* [Een workflow activeren met een statische SOAP-methode](#trigger-example)
* [Interactie met het gegevensbestand, gebruikend een niet statische methode van de ZEEP](#interact-example)

[Meer informatie](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html) over statische en niet-statische SOAP-methoden.

In deze voorbeelden wordt de extensie ECMAScript for XML (E4X) gebruikt. Met deze extensie kunt u JavaScript-aanroepen en XML-primitieven combineren in hetzelfde script.

Voer de volgende stappen uit om deze voorbeelden uit te proberen:

1. Maak een workflow en voeg deze activiteiten toe aan de workflow:
   1. Startactiviteit
   1. JavaScript-codeactiviteit
   1. Eindactiviteit

   [Meer informatie](building-a-workflow.md) over het bouwen van workflows.

1. Voeg de JavaScript-code toe aan een activiteit. [Meer info](advanced-parameters.md).
1. Sla de workflow op.
1. Test de voorbeelden:
   1. De workflow starten. [Meer info](starting-a-workflow.md).
   1. Open het dagboek. [Meer info](monitoring-workflow-execution.md#displaying-logs).

## Voorbeeld 1: schrijven naar de database{#write-example}

Als u naar de database wilt schrijven, kunt u de statische `Write` op de `xtk:session` schema:

1. Stel een schrijfverzoek in XML samen.

1. Schrijf de record:

   1. Roep de `Write` op de `xtk:session` schema.

      >[!IMPORTANT]
      > Als u Adobe Campaign v8 gebruikt, raden we u aan om het faseringsmechanisme te gebruiken met het **Inname** en **Gegevens bijwerken/verwijderen** API&#39;s voor de `Write` in een Snowflake-tabel. [Meer informatie](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

   1. Geef de XML-code door als een argument voor de schrijfaanvraag.

### Stap 1: een schrijfverzoek samenstellen

U kunt records toevoegen, bijwerken en verwijderen.

#### Een record invoegen

Omdat `insert` bewerking is de standaardbewerking, u hoeft deze niet op te geven.

Geef deze informatie op als XML-kenmerken:

* Het schema van de tabel die moet worden gewijzigd
* De tabelvelden die moeten worden ingevuld

Voorbeeld:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### Een record bijwerken

Gebruik de `_update` bewerking. [Meer info](../../configuration/using/data-oriented-apis.md).

Geef deze informatie op als XML-kenmerken:

* Het schema van de tabel die moet worden gewijzigd
* De tabelvelden die moeten worden bijgewerkt
* Het sleutelargument dat wordt vereist om het bij te werken record te identificeren

Voorbeeld:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    status="Client"
    email="isabel.garcia@mycompany.com"
    operation="_update"
    _key="@email"/>
```

#### Een record verwijderen

Gebruik de `DeleteCollection` methode. [Meer info](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html).

Geef deze informatie op:

* Het schema van de tabel die moet worden gewijzigd
* De `where` clausule die vereist is om de bij te werken record te identificeren, in de vorm van een XML-element

Voorbeeld:

```javascript
xtk.session.DeleteCollection(
    "nms:recipient",
    <where>
        <condition expr="[@email] = 'isabel.garcia@mycompany.com'"/>
    </where>,
    false
    )
```

### Stap 2: de record schrijven

Roep niet-statisch `Write` op de `xtk:session` schema:

```javascript
xtk.session.Write(myXML)
```

Er wordt geen waarde geretourneerd voor deze methode.

Voeg de volledige code toe aan een JavaScript-codeactiviteit in de workflow:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

In deze video wordt getoond hoe u naar de database kunt schrijven:
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## Voorbeeld 2: query uitvoeren op de database{#read-example}

Als u een query op de database wilt uitvoeren, kunt u de `xtk:queryDef` instantiemethode:

1. Stel een vraag in XML samen.
1. Maak een queryobject.
1. Voer de query uit.

### Stap 1: een query samenstellen

De XML-code voor een `queryDef` entiteit.

Syntaxis:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Geef deze informatie op:

* Het schema van de te lezen tabel
* De bewerking
* De kolommen die moeten worden geretourneerd, in een `select` clausule
* De voorwaarden, in `where` clausule
* De filtercriteria, in een `orderBy` clausule

U kunt de volgende bewerkingen gebruiken:

| Bewerking | Resultaat |
| --- | --- |
| `select` | Nul of meer elementen worden geretourneerd als een verzameling. |
| `getIfExists` | Eén element wordt geretourneerd. Als er geen overeenkomend element bestaat, wordt een leeg element geretourneerd. |
| `get` | Eén element wordt geretourneerd. Als er geen overeenkomend element bestaat, wordt een fout geretourneerd. |
| `count` | Het aantal overeenkomende records wordt geretourneerd in de vorm van een element met een `count` kenmerk. |

Schrijf de `select`, `where`, en `orderBy` clausules als XML-elementen:

* `select` clausule

   Geef op welke kolommen moeten worden geretourneerd. Als u bijvoorbeeld de voornaam en achternaam van de persoon wilt selecteren, schrijft u de volgende code:

   ```xml
   <select>
       <node expr="@firstName"/>
       <node expr="@lastName"/>
   </select>
   ```

   Met de `nms:recipient` schema, worden de elementen in de volgende vorm geretourneerd:

   ```xml
   <recipient firstName="Bo" lastName="Didley"/>
   ```

* `where` clausule

   Als u voorwaarden wilt opgeven, gebruikt u een `where` clausule. Als u bijvoorbeeld de records wilt selecteren die zich in het dialoogvenster **Training** map, kunt u deze code schrijven:

   ```xml
   <where>
       <condition expr="[folder/@label]='Training'"/>
   </where>
   ```

   Wanneer u meerdere expressies combineert, gebruikt u de Booleaanse operator in de eerste expressie. Als u bijvoorbeeld alle personen wilt selecteren met de naam Isabel Garcia, kunt u de volgende code schrijven:

   ```xml
   <condition boolOperator="AND" expr="@firstName='Isabel'"/>
   <condition expr="@lastName='Garcia'"/>
   ```

* `orderBy` clausule

   Als u de resultaatset wilt sorteren, geeft u de opdracht `orderBy` clausule als element van XML met `sortDesc` kenmerk. Als u bijvoorbeeld de achternamen in oplopende volgorde wilt sorteren, kunt u de volgende code schrijven:

   ```xml
   <orderBy>
       <node expr="@lastName> sortDesc="false"/>
   </orderBy>
   ```

### Stap 2: een queryobject maken

Als u een entiteit wilt maken op basis van de XML-code, gebruikt u de opdracht `create(`*`content`*`)` methode:

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Voorvoegsel `create(`*`content`*`)` methode met het schema van de te creëren entiteit.

De *`content`* argument is een string argument en is optioneel. Dit argument bevat de XML-code die de entiteit beschrijft.

### Stap 3: de query uitvoeren

Voer de volgende stappen uit:

1. Roep de `ExecuteQuery` op de `queryDef` entiteit:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. De resultaten verwerken:
   1. De resultaten van de `select` bewerking, met behulp van een lusconstructie.
   1. Test de resultaten met de `getIfExists` bewerking.
   1. Telling de resultaten met de opdracht `count` bewerking.

#### Resultaten van een `select` bewerking

Alle overeenkomsten worden geretourneerd als een verzameling:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Als u de resultaten wilt doorlopen, gebruikt u de opdracht `for each` lus:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

De lus bevat een variabele voor lokale ontvangers. Voor elke ontvanger die in de inzameling van ontvangers is teruggekeerd, wordt de e-mail van de ontvanger gedrukt. [Meer informatie](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) over de `logInfo` functie.

#### Resultaten van een `getIfExists` bewerking

Elke overeenkomst wordt geretourneerd als een element:

```xml
<recipient id="52,378,079">
```

Als er geen gelijke is, dan is een leeg element teruggekeerd:

```xml
<recipient/>
```

U kunt verwijzen naar de primaire-sleutelknoop-bijvoorbeeld, `@id` kenmerk:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Resultaat van een `get` bewerking

Eén overeenkomst wordt geretourneerd als een element:

```xml
<recipient id="52,378,079">
```

Als er geen overeenkomst is, wordt een fout geretourneerd.

>[!TIP]
>
>Als u weet dat er een overeenkomst is, gebruikt u de `get` bewerking. Gebruik anders de `getIfExists` bewerking. Als u deze beste praktijken gebruikt, dan tonen de fouten onverwachte problemen. Als u het `get` bewerking, gebruik de opdracht `try…catch` instructie. Het probleem wordt afgehandeld door het foutafhandelingsproces van de workflow.

#### Resultaat van een `count` bewerking

Een element met de `count` attribute is returned:

```xml
<recipient count="200">
```

Als u het resultaat wilt gebruiken, raadpleegt u de `@count` kenmerk:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Voor de `select` bewerking, voeg deze code toe aan een JavaScript-code-activiteit in de workflow:

```javascript
var myXML =
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@firstName"/>
        <node expr="@lastName"/>
    </select>
</queryDef>

var query = xtk.queryDef.create(myXML)

var res = query.ExecuteQuery()

for each (var rcp in res.recipient)
    logInfo(rcp.@firstName + " " + rcp.@lastName)
```

Omdat `select` bewerking is de standaardbewerking, u hoeft deze niet op te geven.

In deze video wordt getoond hoe u van de database kunt lezen:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Een workflow activeren {#trigger-example}

U kunt werkstromen programmatically, bijvoorbeeld, in technische werkschema&#39;s of aan procesinformatie teweegbrengen die een gebruiker op een pagina van de Webtoepassing is ingegaan.

Workflowactivering werkt door het gebruik van gebeurtenissen. U kunt deze functies voor gebeurtenissen gebruiken:

* Als u een gebeurtenis wilt posten, kunt u de statische `PostEvent` methode. [Meer info](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html).
* Als u een gebeurtenis wilt ontvangen, kunt u de opdracht **[!UICONTROL External signal]** activiteit. [Meer info](external-signal.md).

U kunt workflows op verschillende manieren activeren:

* U kunt een workflow inline activeren, dat wil zeggen vanuit het hoofdscript van een **[!UICONTROL JavaScript code]** activiteit.
* U kunt een workflow activeren als een andere bewerking is voltooid:
   * Voeg een initialisatiescript aan toe **[!UICONTROL End]** activiteit van de initiële workflow.
   * Voeg de **[!UICONTROL External signal]** activiteit aan het begin van de doelworkflow.

      Na voltooiing van de initiële workflow wordt een gebeurtenis gepost. De uitgaande overgang wordt geactiveerd en de gebeurtenisvariabelen worden gevuld. De gebeurtenis wordt vervolgens ontvangen door de doelworkflow.

      >[!TIP]
      >
      >Als beste praktijk, wanneer u een manuscript aan een activiteit toevoegt, neem de activiteitennaam in dubbele koppeltekens op, bijvoorbeeld `-- end --`. [Meer informatie](workflow-best-practices.md) over best practices voor workflows.

Syntaxis van de `PostEvent` methode:

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

In dit voorbeeld wordt na voltooiing van de workflow een korte tekst doorgegeven aan de **signaal** van de **wkfExampleReceiver** workflow:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Omdat de laatste parameter is ingesteld op `false`de **wkfExampleReceiver** elke keer dat de initiële workflow wordt voltooid, wordt een workflow gestart.

Houd rekening met de volgende beginselen wanneer u workflows activeert:

* De `PostEvent` wordt asynchroon uitgevoerd. Het bevel wordt geplaatst op de serverrij. De methode wordt geretourneerd nadat de gebeurtenis is gepost.
* De doelworkflow moet worden gestart. Anders wordt een fout naar het logbestand geschreven.
* Als de doelworkflow wordt onderbroken, wordt de `PostEvent` wordt in een wachtrij geplaatst totdat de workflow wordt hervat.
* De getriggerde activiteit vereist niet dat een taak wordt uitgevoerd.

In deze video wordt getoond hoe u statische API-methoden kunt gebruiken:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

In deze video wordt getoond hoe workflows kunnen worden geactiveerd:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interactie met de database {#interact-example}

Deze voorbeelden laten zien hoe u deze handelingen uitvoert:

* Gebruik de `get` en `create` methoden op schema&#39;s voor het gebruik van niet-statische SOAP-methoden
* Methoden maken die SQL-query&#39;s uitvoeren
* Gebruik de `write` methode voor het invoegen, bijwerken en verwijderen van records

Voer de volgende stappen uit:

1. Definieer de query:

   * Een entiteit ophalen met de opdracht `create` methode op het overeenkomstige schema, bijvoorbeeld `xtk:workflow` schema. [Meer info](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html).
   * Gebruik de `queryDef` om een SQL-query uit te geven.

1. Voer de query uit met de `ExecuteQuery` methode. [Meer info](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html).

   Gebruik de `for each` om de resultaten op te halen.

### Syntaxis van de `queryDef` methode met een `select` clausule

```xml
<queryDef schema="schema_key" operation="operation_type">
    <select>
        <node expr="expression1">
        <node sql="expression2">
    </select>
    <where> 
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </where>
    <orderBy>
        <node expr="expression1">
        <node sql="expression2">
    </orderBy>
    <groupBy>
        <node expr="expression1">
        <node sql="expression2">
    </groupBy>
    <having>
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </having>
</queryDef>
```

### `Create` methode

#### Voorbeeld 1: records selecteren en naar het journaal schrijven

De interne namen van de workflows die zich in de **wfExamples** is geselecteerd. De resultaten worden gesorteerd op interne naam, in oplopende volgorde, en naar het dagboek geschreven.

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="xtk:workflow" operation="select">
        <select>
            <node expr="@internalName"/>
        </select>
        <where>
            <condition expr="[folder/@name]='wfExamples'"/>
        </where>
        <orderBy>
            <node expr="@internalName" sortDesc="false"/>
        </orderBy>
    </queryDef>
    )

var res = query.ExecuteQuery()
for each (var w in res.workflow)
    logInfo(w.@internalName)
```

#### Voorbeeld 2: records verwijderen

De voornaam, de achternaam, het e-mailbericht en de id van alle ontvangers met de naam Chris Smith worden geselecteerd. De resultaten worden gesorteerd per e-mail, in oplopende volgorde, en geschreven aan het dagboek. A `delete` wordt gebruikt om de geselecteerde records te verwijderen.

```javascript
// Build the query, create a query object and hold the object in a variable
var query = xtk.queryDef.create(
        <queryDef schema="nms:recipient" operation="select">
            <select>
                <node expr="@firstName"/>
                <node expr="@lastName"/>
                <node expr="@email"/>
                <node expr="@id"/>
            </select>
            <where>
                <condition expr="[folder/@label]='Recipients'"/>
                <condition expr="[@lastName]='Smith'"/>
                <condition expr="[@firstName]='Chris'"/>
            </where>
            <orderBy>
                <node expr="@email" sortDesc="false"/>
            </orderBy>
        </queryDef>
)

//Run the query using the ExecuteQuery method against the created object
var res = query.ExecuteQuery()

//Loop through the results, print out the person's name and email, then delete the records
for each (var rec in res.recipient)
    {
     logInfo("Delete record = Email: " + rec.@email + ', ' + rec.@firstName + ' ' + rec.@lastName)
     xtk.session.Write(<recipient xtkschema="nms:recipient" _operation="delete" id={rec.@id}/>)
    }
```

#### Voorbeeld 3: records selecteren en naar het journaal schrijven

In dit voorbeeld wordt een niet-statische methode gebruikt. Het e-mail- en geboortejaar van alle ontvangers waarvan de gegevens in het **1234** en de map waarin de naam van het e-maildomein begint met &quot;adobe&quot; zijn geselecteerd. De resultaten worden gesorteerd op geboortedatum in aflopende volgorde. De e-mail van de ontvangers wordt geschreven aan het dagboek.

```javascript
var query = xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@email"/>
        <node sql="sEmail"/>
        <node expr="Year(@birthDate)"/>
    </select>
    <where>
        <condition expr="[@folder-id] = 1234 and @domain like 'adobe%'"/>
        <condition sql="iFolderId = 1234 and sDomain like 'adobe%'"/>
    </where>
    <orderBy>
        <node expr="@birthDate" sortDesc="true"/>
    </orderBy>
</queryDef>
)

var res = query.ExecuteQuery()
for each (var w in res.recipient)
    logInfo(w.@email)
```

### `Write` methode

U kunt records invoegen, bijwerken en verwijderen. U kunt de `Write` in Adobe Campaign. Omdat deze methode statisch is, hoeft u geen object te maken. U kunt de volgende bewerkingen gebruiken:

* De `update` bewerking
* De `insertOrUpdate` met de `_key` argument om de bij te werken record te identificeren

   Als u geen **Ontvangers** als er een overeenkomst bestaat, wordt de record in elke submap bijgewerkt. Anders wordt de record in de hoofdmap gemaakt **Ontvangers** map.

* De `delete` bewerking

>[!IMPORTANT]
> Als u Adobe Campaign v8 gebruikt, raden we u aan om het faseringsmechanisme te gebruiken met het **Inname** en **Gegevens bijwerken/verwijderen** API&#39;s voor de `Write` in een Snowflake-tabel. [Meer informatie](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

#### Voorbeeld 1: een record invoegen of bijwerken

```javascript
xtk.session.Write(
<recipient
    xtkschema="nms:recipient"
    _operation="insertOrUpdate" _key="@email"
    lastName="Lennon"
    firstName="John"
    email="johnlennon@thebeatles.com"
/>
)
```

#### Voorbeeld 2: records verwijderen

In dit voorbeeld worden een statische methode en een niet-statische methode gecombineerd.

```javascript
var query=xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@Id"/>
    </select>
    <where>
        <condition expr="[@email]='johnlennon@thebeatles.com'"/>
    </where>
</queryDef>
);

var res = query.ExecuteQuery()
for each (var w in res.recipient) {
xtk.session.Write(
    <recipient xtkschema="nms:recipient" _operation="delete" id={w.@id}/>
);
}
```

In deze video wordt getoond hoe u niet-statische API-methoden kunt gebruiken:
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

In deze video ziet u een voorbeeld van het gebruik van een niet-statische API-methode in een workflow:
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## Verwante onderwerpen

* [Gegevensgeoriënteerde API&#39;s](../../configuration/using/data-oriented-apis.md)
* [JavaScript-scripts en -sjablonen](javascript-scripts-and-templates.md)
* [SOAP-methoden in JavaScript](../../configuration/using/soap-methods-in-javascript.md)

### API-documentatie

* [Voorbeelden van SOAP-aanroepen](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)
* Methoden:
   * [Maken](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [Schrijven](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [logInfo, functie](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)