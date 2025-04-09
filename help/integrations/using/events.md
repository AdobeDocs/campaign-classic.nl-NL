---
product: campaign
title: Gebeurtenissen configureren
description: Leer hoe u gebeurtenissen configureert voor een aangepaste implementatie
feature: Triggers
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 0%

---

# Gebeurtenissen configureren voor aangepaste implementatie {#events}



De delen van deze configuratie zijn een douaneontwikkeling en vereisen het volgende:

* Werken met JSON-, XML- en Javascript-parsering in Adobe Campaign.
* Werkkennis van de API&#39;s QueryDef en Writer.
* Werken met codering en verificatie met persoonlijke sleutels.

Aangezien voor het bewerken van de Javascript-code technische vaardigheden vereist zijn, probeert u dit niet zonder het juiste inzicht.

## Gebeurtenissen in JavaScript verwerken {#events-javascript}

### JavaScript-bestand {#file-js}

De pijpleiding gebruikt een functie van JavaScript om elk bericht te verwerken. Deze functie is door de gebruiker gedefinieerd.

Deze wordt geconfigureerd in de optie **[!UICONTROL NmsPipeline_Config]** onder het kenmerk &quot;JSConnector&quot;. Deze JavaScript wordt telkens opgeroepen wanneer een gebeurtenis wordt ontvangen. Het wordt uitgevoerd door het [!DNL pipelined] proces.

Het Javascript-voorbeeldbestand is cus:triggers.js.

### JavaScript, functie {#function-js}

[!DNL pipelined] JavaScript moet met een specifieke functie beginnen.

Deze functie wordt één keer aangeroepen voor elke gebeurtenis:

```
function processPipelineMessage(xmlTrigger) {}
```

Het moet terugkeren zoals

```
<undefined/>
```

Nadat u het JavaScript-bestand hebt bewerkt, moet u [!DNL pipelined] opnieuw starten.

### Gegevensindeling activeren {#trigger-format}

De [!DNL trigger] -gegevens worden doorgegeven aan de JS-functie in XML-indeling.

* Het attribuut **[!UICONTROL @triggerId]** bevat de naam van [!DNL trigger] .
* Het **verrijkt** element in formaat JSON bevat de gegevens die door Adobe Analytics worden geproduceerd en aan de trekker in bijlage zijn.
* **[!UICONTROL @offset]** is de &quot;wijzer&quot;aan het bericht. Het wijst op de orde van het bericht binnen de rij.
* **[!UICONTROL @partition]** is een container met berichten in de wachtrij. De verschuiving is relatief ten opzichte van een partitie. <br> er zijn ongeveer 15 verdelingen in de rij.

Voorbeeld:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Verrijking gegevensindeling {#enrichment-format}

>[!NOTE]
>
>Het is een specifiek voorbeeld van verschillende mogelijke implementaties.

De inhoud wordt gedefinieerd in JSON-indeling in Adobe Analytics voor elke trigger.
Bijvoorbeeld in een trigger van LogoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** kan de Shopper-id bevatten in tekenreeksindeling die wordt gebruikt om te combineren met Adobe Campaign-ontvangers. <br>Het moet worden afgestemd om de Shopper-ID te vinden, die de primaire sleutel is.

* **[!UICONTROL timeGMT]** kan de tijd van de trigger aan de Adobe Analytics-zijde in UTC Epoch-indeling bevatten (seconden sinds 01/01/1970 UTC).

Voorbeeld:

```
{
 "analyticsHitSummary": {
 "dimensions": {
 "eVar01": {
 "type": "string",
 "data": ["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],
 "name": " eVar01",
 "source": "session summary"
 },
 "timeGMT": {
 "type": "int",
 "data": [1469164186, 1469164195],
 "name": "timeGMT",
 "source": "session summary"
 }
 },
 "products": {}
 }
 }
```

### Volgorde voor verwerking van gebeurtenissen{#order-events}

De gebeurtenissen worden één voor één verwerkt, in volgorde van verschuiving. Elke thread van de [!DNL pipelined] verwerkt een andere partitie.

De &#39;offset&#39; van de laatste opgehaalde gebeurtenis wordt opgeslagen in de database. Daarom als het proces wordt tegengehouden, begint het van het laatste bericht opnieuw. Dit gegeven wordt opgeslagen in het ingebouwde schema xtk:pipeOffset.

Deze aanwijzer is specifiek voor elk exemplaar en elke consument. Daarom wanneer vele instanties tot de zelfde pijpleiding met verschillende consumenten toegang hebben, krijgen zij elk alle berichten en in de zelfde orde.

De **consument** parameter van de pijpleidingsoptie identificeert de roepende instantie.

Er is momenteel geen manier om verschillende wachtrijen te hebben voor afzonderlijke omgevingen zoals &#39;staging&#39; of &#39;dev&#39;.

### Logboekregistratie en foutafhandeling {#logging-error-handling}

Logbestanden zoals logInfo() worden naar het [!DNL pipelined] log geleid. Fouten zoals logError() worden naar het logbestand van [!DNL pipelined] geschreven en zorgen ervoor dat de gebeurtenis in de wachtrij voor opnieuw proberen wordt geplaatst. In dit geval dient u het gepipetteerde log te controleren.
Foutberichten worden verschillende keren opnieuw geprobeerd in de duur die is ingesteld bij de opties voor [!DNL pipelined] .

Voor foutopsporing en bewaking worden de volledige triggergegevens in XML-indeling naar de triggertabel in het veld &quot;data&quot; geschreven. U kunt ook een logInfo() met de triggergegevens gebruiken voor hetzelfde doel.

### De gegevens parseren {#data-parsing}

Dit voorbeeld van Javascript-code parseert de eVar01 in de verrijkingen.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var shopper_id = ""
 if (xmlTrigger.enrichments.length() > 0)
 {
 if (xmlTrigger.enrichments.toString().match(/eVar01/) != undefined)
 {
 var enrichments = JSON.parse(xmlTrigger.enrichments.toString())
 shopper_id = enrichments.analyticsHitSummary.dimensions. eVar01.data[0]
 }
 }
 (…)
 }
```

Wees voorzichtig bij het parseren om fouten te voorkomen.
Aangezien deze code voor alle triggers wordt gebruikt, zijn de meeste gegevens niet vereist. Daarom kan het leeg worden gelaten als het niet aanwezig is.

### De trigger opslaan {#storing-triggers-js}

>[!NOTE]
>
>Het is een specifiek voorbeeld van verschillende mogelijke implementaties.

Deze voorbeeld-JS-code slaat de trigger op in de database.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var event = 
 <pipelineEvent
 xtkschema = "cus:pipelineEvent"
 _operation = "insert"
 created = {timeNow}
 lastModified = {timeNow}
 triggerType = {triggerType}
 timeGMT = {timeGMT}
 shopper_id = {shopper_id}
 data = {xmlTrigger.toXMLString()}
 />
 xtk.session.Write(event)
 return <undef/>;
 }
```

### Restricties {#constraints}

De prestaties voor deze code moeten optimaal zijn, omdat deze op hoge frequenties wordt uitgevoerd en mogelijke negatieve effecten voor andere marketingactiviteiten kan hebben. Vooral als het verwerken van meer dan één miljoen triggergebeurtenissen per uur op de Marketing-server of als het niet correct is ingesteld.

De context van dit JavaScript is beperkt. Niet alle functies van de API zijn beschikbaar. getOption() of getCurrentdate() werkt bijvoorbeeld niet.

Om snellere verwerking toe te laten, worden verscheidene draden van dit manuscript uitgevoerd tezelfdertijd. De code moet thread safe zijn.

## Gebeurtenissen opslaan {#store-events}

>[!NOTE]
>
>Het is een specifiek voorbeeld van verschillende mogelijke implementaties.

### Gebeurtenisschema van Pipeline {#pipeline-event-schema}

Gebeurtenissen worden opgeslagen in een databasetabel. Het wordt gebruikt door marketing campagnes om klanten te richten en e-mails te verrijken gebruikend trekkers.
Hoewel elke trigger een afzonderlijke gegevensstructuur kan hebben, kunnen alle triggers in één tabel worden gehouden.
Het triggerType-veld identificeert waaruit de gegevens afkomstig zijn.

Hier volgt een voorbeeldschemacode voor deze tabel:

| Kenmerk | Type | Label | Beschrijving |
|:-:|:-:|:-:|:-:|
| pipeEventId | Lang | Primaire sleutel | De interne primaire sleutel van de trigger. |
| data | Memo | Gegevens activeren | De volledige inhoud van triggergegevens in XML-indeling. Voor foutopsporing en controle. |
| triggerType | Tekenreeks 50 | Trekker Type | De naam van de trigger. Identificeert het gedrag van de klant op de website. |
| shopper_id | String 32 | shopper_id | De interne id van de klant. Wordt ingesteld door de afstemmingsworkflow. Als nul, betekent het dat de klant in Campaign onbekend is. |
| shopper_key | Lang | shopper_key | De externe ID van de klant, zoals vastgelegd door Analytics. |
| gemaakt | Datumtijd | Gemaakt | De tijd waarop de gebeurtenis in Campagne werd gecreeerd. |
| lastModified | Datumtijd | Laatst gewijzigd | De laatste keer dat de gebeurtenis in Adobe is gewijzigd. |
| tijdGMT | Datumtijd | Tijdstempel | De tijd waarop de gebeurtenis in Analytics is gegenereerd. |

### Gebeurtenissen weergeven {#display-events}

De gebeurtenissen kunnen worden weergegeven met een eenvoudig formulier dat is gebaseerd op het gebeurtenissenschema.

>[!NOTE]
>
>Het knooppunt voor gebeurtenissen via de pijpleiding is niet ingebouwd en moet worden toegevoegd. Het gerelateerde formulier moet ook in Campagne worden gemaakt. Deze bewerkingen zijn alleen bestemd voor deskundige gebruikers. Voor meer op dit, verwijs naar deze secties: [ de hiërarchie van de Navigatie ](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy). en [Formulieren](../../configuration/using/editing-forms.md) bewerken.

![](assets/triggers_7.png)

## Verwerken van de gebeurtenissen {#processing-the-events}

### Afstemming werkstroom {#reconciliation-workflow}

Verzoening is het proces waarbij de klant van Adobe Analytics in de Adobe Campaign-database wordt opgenomen. De criteria voor overeenkomsten kunnen bijvoorbeeld de shopper_id zijn.

Om prestatieredenen moet de overeenkomst in batchmodus worden uitgevoerd door middel van een workflow.
De frequentie moet op 15 minuten worden ingesteld om de werkbelasting te optimaliseren. Als gevolg hiervan is de periode tussen de ontvangst van een gebeurtenis in Adobe Campaign en de verwerking ervan via een marketingworkflow maximaal 15 minuten.

### Opties voor afstemming per eenheid in JavaScript {#options-unit-reconciliation}

Het is mogelijk om de verzoeningsvraag voor elke trekker in JavaScript in werking te stellen. Het heeft een hogere invloed op de prestaties en levert snellere resultaten op. Dit kan nodig zijn voor specifieke gevallen waarin reactiviteit nodig is.

Het kan moeilijk zijn om uit te voeren als geen index op shopper_id wordt geplaatst. Als de criteria op een afzonderlijke gegevensbestandserver dan de marketing server zijn, gebruikt het een gegevensbestandverbinding, die slechte prestaties heeft.

### Werkstroom leegmaken {#purge-workflow}

Triggers worden binnen een uur verwerkt. Het volume kan ongeveer 1 miljoen triggers per uur zijn. Er wordt uitgelegd waarom er een zuiveringsworkflow moet worden opgezet. De purge wordt eenmaal per dag uitgevoerd en verwijdert alle triggers die ouder zijn dan drie dagen.

### Campagne-workflow {#campaign-workflow}

De workflow voor triggercampagnes lijkt vaak op andere terugkerende campagnes die zijn gebruikt.
Bijvoorbeeld, kan het met een vraag op de trekkers beginnen die specifieke gebeurtenissen tijdens de laatste dag zoeken. Dit doel wordt gebruikt om de e-mail te verzenden. Verrijkingen of gegevens kunnen afkomstig zijn van de trigger. Het kan veilig door Marketing worden gebruikt aangezien het geen configuratie vereist.
