---
product: campaign
title: Voorbeelden van JavaScript-code in workflows
description: Deze voorbeelden laten zien hoe u JavaScript-code kunt gebruiken in een workflow
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1695'
ht-degree: 2%

---

# Voorbeelden van JavaScript-code in workflows{#javascript-in-workflows}



Deze voorbeelden laten zien hoe u JavaScript-code kunt gebruiken in een workflow:

* [Naar de database schrijven](#write-example)
* [De database opvragen](#read-example)
* [Een workflow activeren met een statische SOAP-methode](#trigger-example)
* [Communiceer met de database met een niet-statische SOAP-methode](#interact-example)

[ leer meer ](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=nl-NL) over statische en niet-statische methodes van SOAP.

In deze voorbeelden wordt de extensie ECMAScript for XML (E4X) gebruikt. Met deze extensie kunt u JavaScript-aanroepen en XML-primitieven combineren in hetzelfde script.

Voer de volgende stappen uit om deze voorbeelden uit te proberen:

1. Maak een workflow en voeg deze activiteiten toe aan de workflow:
   1. Startactiviteit
   1. JavaScript-codeactiviteit
   1. Eindactiviteit

   [ leer meer ](building-a-workflow.md) over het bouwen van werkschema&#39;s.

1. Voeg de JavaScript-code toe aan een activiteit. [Meer informatie](advanced-parameters.md).
1. Sla de workflow op.
1. Test de voorbeelden:
   1. Start de workflow. [Meer informatie](starting-a-workflow.md).
   1. Open het dagboek. [Meer informatie](monitoring-workflow-execution.md#displaying-logs).

## Voorbeeld 1: schrijven naar de database{#write-example}

Als u naar de database wilt schrijven, gebruikt u de statische methode `Write` in het `xtk:session` -schema:

1. Stel een schrijfverzoek in XML samen.

1. Schrijf de record:

   1. Roep de methode `Write` op in het `xtk:session` -schema.

      >[!IMPORTANT]
      > Als u Adobe Campaign v8 gebruikt, adviseren wij dat u het het opvoeren mechanisme met de **Opname** en **update/schrapt van Gegevens** APIs voor de `Write` methode in een lijst van Snowflake gebruikt. [Meer informatie](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=nl-NL){target="_blank"}.

   1. Geef de XML-code door als een argument voor de schrijfaanvraag.

### Stap 1: stel een schrijfverzoek samen

U kunt records toevoegen, bijwerken en verwijderen.

#### Een record invoegen

Omdat de bewerking `insert` de standaardbewerking is, hoeft u deze niet op te geven.

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

Gebruik de bewerking `_update` . [Meer informatie](../../configuration/using/data-oriented-apis.md).

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

Gebruik de methode `DeleteCollection` . [Meer informatie](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=nl-NL).

Geef deze informatie op:

* Het schema van de tabel die moet worden gewijzigd
* De `where` -component die vereist is om de record te identificeren die moet worden bijgewerkt, in de vorm van een XML-element

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

Roep de niet-statische `Write` methode op het `xtk:session` schema aan:

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

## Voorbeeld 2: de database opvragen{#read-example}

Als u een query op de database wilt uitvoeren, gebruikt u de niet-statische methode van de `xtk:queryDef` -instantie:

1. Stel een vraag in XML samen.
1. Maak een queryobject.
1. Voer de query uit.

### Stap 1: stel een query samen

Geef de XML-code op voor een entiteit `queryDef` .

Syntaxis:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Geef deze informatie op:

* Het schema van de te lezen tabel
* De bewerking
* De kolommen die moeten worden geretourneerd, in een `select` -component
* De voorwaarden, in een `where` -component
* De filtercriteria, in een `orderBy` -component

U kunt de volgende bewerkingen gebruiken:

| Bewerking | Resultaat |
| --- | --- |
| `select` | Nul of meer elementen worden geretourneerd als een verzameling. |
| `getIfExists` | Eén element wordt geretourneerd. Als er geen overeenkomend element bestaat, wordt een leeg element geretourneerd. |
| `get` | Eén element wordt geretourneerd. Als er geen overeenkomend element bestaat, wordt een fout geretourneerd. |
| `count` | Het aantal overeenkomende records wordt geretourneerd in de vorm van een element met een `count` -kenmerk. |

Schrijf de clausules `select`, `where` en `orderBy` als XML-elementen:

* `select` component

  Geef op welke kolommen moeten worden geretourneerd. Als u bijvoorbeeld de voornaam en achternaam van de persoon wilt selecteren, schrijft u de volgende code:

  ```xml
  <select>
      <node expr="@firstName"/>
      <node expr="@lastName"/>
  </select>
  ```

  Met het schema `nms:recipient` worden elementen in de volgende vorm geretourneerd:

  ```xml
  <recipient firstName="Bo" lastName="Didley"/>
  ```

* `where` component

  Gebruik een `where` -component om voorwaarden op te geven. Bijvoorbeeld, om de verslagen te selecteren die in de **omslag van de Opleiding** worden gevestigd, kunt u deze code schrijven:

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

* `orderBy` component

  Als u de resultaatset wilt sorteren, geeft u de component `orderBy` op als een XML-element met het kenmerk `sortDesc` . Als u bijvoorbeeld de achternamen in oplopende volgorde wilt sorteren, kunt u de volgende code schrijven:

  ```xml
  <orderBy>
      <node expr="@lastName> sortDesc="false"/>
  </orderBy>
  ```

### Stap 2: een queryobject maken

Als u een entiteit wilt maken op basis van de XML-code, gebruikt u de methode `create(`*`content`*`)` :

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Plaats de methode `create(`*`content`*`)` vooraf in het schema van de entiteit die u wilt maken.

Het argument *`content`* is een tekenreeksargument en is optioneel. Dit argument bevat de XML-code die de entiteit beschrijft.

### Stap 3: voer de query uit

Voer de volgende stappen uit:

1. Roep de methode `ExecuteQuery` op de entiteit `queryDef` aan:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. De resultaten verwerken:
   1. Doorloop de resultaten van de bewerking `select` met een lusconstructie.
   1. Test de resultaten met de bewerking `getIfExists` .
   1. Telt de resultaten met de bewerking `count` .

#### Resultaten van een `select` -bewerking

Alle overeenkomsten worden geretourneerd als een verzameling:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Als u de resultaten wilt doorlopen, gebruikt u de lus `for each` :

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

De lus bevat een variabele voor lokale ontvangers. Voor elke ontvanger die in de inzameling van ontvangers is teruggekeerd, wordt de e-mail van de ontvanger gedrukt. [ leer meer ](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=nl-NL) over de `logInfo` functie.

#### Resultaten van een `getIfExists` -bewerking

Elke overeenkomst wordt geretourneerd als een element:

```xml
<recipient id="52,378,079">
```

Als er geen gelijke is, dan is een leeg element teruggekeerd:

```xml
<recipient/>
```

U kunt verwijzen naar het knooppunt met de primaire sleutel, bijvoorbeeld het kenmerk `@id` :

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Resultaat van een `get` -bewerking

Eén overeenkomst wordt geretourneerd als een element:

```xml
<recipient id="52,378,079">
```

Als er geen overeenkomst is, wordt een fout geretourneerd.

>[!TIP]
>
>Als u weet dat er een overeenkomst is, gebruikt u de bewerking `get` . Anders gebruikt u de `getIfExists` -bewerking. Als u deze beste praktijken gebruikt, dan tonen de fouten onverwachte problemen. Gebruik de instructie `try…catch` niet wanneer u de bewerking `get` gebruikt. Het probleem wordt afgehandeld door het foutafhandelingsproces van de workflow.

#### Resultaat van een `count` -bewerking

Er wordt een element met het kenmerk `count` geretourneerd:

```xml
<recipient count="200">
```

Als u het resultaat wilt gebruiken, raadpleegt u het kenmerk `@count` :

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Voeg voor de bewerking `select` deze code toe aan een JavaScript-codeactiviteit in de workflow:

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

Omdat de bewerking `select` de standaardbewerking is, hoeft u deze niet op te geven.

In deze video wordt getoond hoe u van de database kunt lezen:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Een workflow activeren {#trigger-example}

U kunt werkstromen programmatically, bijvoorbeeld, in technische werkschema&#39;s of aan procesinformatie teweegbrengen die een gebruiker op een pagina van de Webtoepassing is ingegaan.

Workflowactivering werkt door het gebruik van gebeurtenissen. U kunt deze functies voor gebeurtenissen gebruiken:

* U kunt de statische methode `PostEvent` gebruiken om een gebeurtenis te posten. [Meer informatie](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=nl-NL).
* U kunt de **[!UICONTROL External signal]** -activiteit gebruiken om een gebeurtenis te ontvangen. [Meer informatie](external-signal.md).

U kunt workflows op verschillende manieren activeren:

* U kunt een workflow inline activeren, dat wil zeggen vanuit het hoofdscript van een **[!UICONTROL JavaScript code]** -activiteit.
* U kunt een workflow activeren als een andere bewerking is voltooid:
   * Voeg een initialisatiescript aan de **[!UICONTROL End]** activiteit van het aanvankelijke werkschema toe.
   * Voeg de **[!UICONTROL External signal]** -activiteit toe aan het begin van de doelworkflow.

     Na voltooiing van de initiële workflow wordt een gebeurtenis gepost. De uitgaande overgang wordt geactiveerd en de gebeurtenisvariabelen worden gevuld. De gebeurtenis wordt vervolgens ontvangen door de doelworkflow.

     >[!TIP]
     >
     >Als beste praktijk, wanneer u een manuscript aan een activiteit toevoegt, sluit de activiteitennaam in dubbele koppeltekens, bijvoorbeeld, `-- end --`. [ leer meer ](workflow-best-practices.md) over werkschemabeste praktijken.

Syntaxis van de methode `PostEvent` :

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

In dit voorbeeld, op voltooiing van het werkschema, wordt een korte tekst overgegaan tot de **signaal** activiteit van het **wkfExampleReceiver** werkschema:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Omdat de laatste parameter aan `false` wordt geplaatst, wordt het **wkfExampleReceiver** werkschema teweeggebracht telkens als het aanvankelijke werkschema wordt voltooid.

Houd rekening met de volgende beginselen wanneer u workflows activeert:

* De opdracht `PostEvent` wordt asynchroon uitgevoerd. Het bevel wordt geplaatst op de serverrij. De methode wordt geretourneerd nadat de gebeurtenis is gepost.
* De doelworkflow moet worden gestart. Anders wordt een fout naar het logbestand geschreven.
* Als de doelworkflow wordt onderbroken, wordt de opdracht `PostEvent` in de wachtrij geplaatst totdat de workflow wordt hervat.
* De getriggerde activiteit vereist niet dat een taak wordt uitgevoerd.

In deze video wordt getoond hoe u statische API-methoden kunt gebruiken:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

In deze video wordt getoond hoe workflows kunnen worden geactiveerd:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interactie met de database {#interact-example}

Deze voorbeelden laten zien hoe u deze handelingen uitvoert:

* Gebruik de methoden `get` en `create` voor schema&#39;s om niet-statische SOAP-methoden te gebruiken
* Methoden maken die SQL-query&#39;s uitvoeren
* Met de methode `write` kunt u records invoegen, bijwerken en verwijderen

Voer de volgende stappen uit:

1. Definieer de query:

   * Haal een entiteit op met de methode `create` in het corresponderende schema, bijvoorbeeld het schema `xtk:workflow` . [Meer informatie](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=nl-NL).
   * Gebruik de methode `queryDef` om een SQL-query uit te voeren.

1. Voer de query uit met de methode `ExecuteQuery` . [Meer informatie](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=nl-NL).

   Gebruik de lus `for each` om de resultaten op te halen.

### Syntaxis van de methode `queryDef` met een component `select`

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

### `Create` , methode

#### Voorbeeld 1: selecteer records en schrijf naar het journaal

De interne namen van de werkschema&#39;s die in de **wfExamples** omslag worden gevestigd worden geselecteerd. De resultaten worden gesorteerd op interne naam, in oplopende volgorde, en naar het dagboek geschreven.

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

De voornaam, de achternaam, het e-mailbericht en de id van alle ontvangers met de naam Chris Smith worden geselecteerd. De resultaten worden gesorteerd per e-mail, in oplopende volgorde, en geschreven aan het dagboek. Een `delete` -bewerking wordt gebruikt om de geselecteerde records te verwijderen.

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

#### Voorbeeld 3: selecteer records en schrijf naar het tijdschrift

In dit voorbeeld wordt een niet-statische methode gebruikt. Het e-mail en geboortejaar van alle ontvangers de waarvan informatie in **1234** omslag wordt opgeslagen en waarvan e-maildomeinnaam met &quot;adobe&quot;begint worden geselecteerd. De resultaten worden gesorteerd op geboortedatum in aflopende volgorde. De e-mail van de ontvangers wordt geschreven aan het dagboek.

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

### `Write` , methode

U kunt records invoegen, bijwerken en verwijderen. U kunt de methode `Write` op elk schema in Adobe Campaign gebruiken. Omdat deze methode statisch is, hoeft u geen object te maken. U kunt de volgende bewerkingen gebruiken:

* De bewerking `update`
* De bewerking `insertOrUpdate` , met het argument `_key` om de record te identificeren die moet worden bijgewerkt

  Als u niet de **Ontvangers** omslag specificeert, dan, als een gelijke bestaat, wordt het verslag bijgewerkt in om het even welke subfolder. Anders, wordt het verslag gecreeerd in de wortel **Ontvangers** omslag.

* De bewerking `delete`

>[!IMPORTANT]
> Als u Adobe Campaign v8 gebruikt, adviseren wij dat u het het opvoeren mechanisme met de **Opname** en **update/schrapt van Gegevens** APIs voor de `Write` methode in een lijst van Snowflake gebruikt. [Meer informatie](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=nl-NL){target="_blank"}.

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

* [ Steekproeven van SOAP roepen ](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=nl-NL)
* Methoden:
   * [ creeer ](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=nl-NL)
   * [ DeleteCollection ](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=nl-NL)
   * [ ExecuteQuery ](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=nl-NL)
   * [ PostEvent ](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=nl-NL)
   * [ schrijf ](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html?lang=nl-NL)
* [ logInfo functie ](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=nl-NL)
