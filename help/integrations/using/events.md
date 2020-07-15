---
title: Integratie configureren
seo-title: Integratie configureren
description: Integratie configureren
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 0%

---


# Triggergebeurtenissen {#events}

## Gebeurtenissen verwerken in JavaScript {#events-javascript}

### JavaScript-bestand {#file-js}

Pipeline gebruikt een functie JavaScript om elk bericht te verwerken. Deze functie is door de gebruiker gedefinieerd.

Het wordt gevormd in de **[!UICONTROL NmsPipeline_Config]** optie onder het &quot;JSConnector&quot;attribuut. Deze javascript wordt geroepen telkens als een gebeurtenis wordt ontvangen. Het wordt door het [!DNL pipelined] proces geleid.

Het JS-voorbeeldbestand is cus:triggers.js.

### JavaScript, functie {#function-js}

Het [!DNL pipelined] Javascript moet met een specifieke functie beginnen.

Deze functie wordt één keer aangeroepen voor elke gebeurtenis:

```
function processPipelineMessage(xmlTrigger) {}
```

Het moet terugkeren zoals

```
<undefined/>
```

Start opnieuw [!DNL pipelined] nadat u de JS hebt bewerkt.

### Gegevensindeling activeren {#trigger-format}

De [!DNL trigger] gegevens worden doorgegeven aan de JS-functie. Het heeft XML-indeling.

* Het **[!UICONTROL @triggerId]** kenmerk bevat de naam van het [!DNL trigger]object.
* Het element **Verrijdingen** in JSON-indeling bevat de gegevens die door Analytics zijn gegenereerd en is gekoppeld aan de trigger.
* **[!UICONTROL @offset]** is de &quot;wijzer&quot;aan het bericht. Het wijst op de orde van het bericht binnen de rij.
* **[!UICONTROL @partitio]**n is een container van berichten binnen de rij. De verschuiving is relatief ten opzichte van een partitie. <br>De wachtrij bevat ongeveer 15 partities.

Voorbeeld:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Gegevensformaat verrijking {#enrichment-format}

>[!NOTE]
>
>Het is een specifiek voorbeeld van verschillende mogelijke implementaties.

De inhoud wordt gedefinieerd in Analytics voor elke trigger. Het heeft JSON-indeling.
Bijvoorbeeld in een trigger van LogoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** kan de Shopper-id bevatten die wordt gebruikt om te combineren met campagneontvangers. Het is in het formaat van het Koord. <br>U moet de Shopper-id vinden, de primaire sleutel.

* **[!UICONTROL timeGMT]** kan de tijd van de trigger aan de Analytics-zijde bevatten. De notatie is UTC Epoch (seconden sinds 01/01/1970 UTC).

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

### Volgorde van de verwerking van gebeurtenissen {#order-events}

De gebeurtenissen worden één voor één verwerkt, in volgorde van verschuiving. Elke draad van de [!DNL pipelined] processen een verschillende verdeling.

De &quot;verschuiving&quot; van de laatste opgehaalde gebeurtenis wordt opgeslagen in de database. Daarom als het proces wordt tegengehouden, begint het van het laatste bericht opnieuw. Dit gegeven wordt opgeslagen in het ingebouwde schema xtk:pipeOffset.

Deze aanwijzer is specifiek voor elk exemplaar en elke consument. Daarom wanneer vele instanties tot de zelfde pijpleiding met verschillende consumenten toegang hebben, krijgen zij elk alle berichten en in de zelfde orde.

De &quot;consument&quot;parameter van de pijpleidingsoptie identificeert de roepende instantie.

Er is momenteel geen manier om verschillende wachtrijen te hebben voor afzonderlijke omgevingen zoals &#39;staging&#39; of &#39;dev&#39;.

### Logboekregistratie en foutafhandeling {#logging-error-handling}

Logbestanden zoals logInfo() worden naar het [!DNL pipelined] logbestand gestuurd. Fouten zoals logError() worden naar het [!DNL pipelined] logbestand geschreven en zorgen ervoor dat de gebeurtenis in de wachtrij voor opnieuw proberen wordt geplaatst. Controleer het gepipetteerde log.
Foutberichten worden verschillende keren opnieuw geprobeerd in de duur die in de [!DNL pipelined] opties is ingesteld.

Voor foutopsporing en bewaking worden de volledige triggergegevens naar de triggertabel geschreven. Het bevindt zich in het veld &quot;data&quot; in XML-indeling. U kunt ook een logInfo() met de triggergegevens gebruiken voor hetzelfde doel.

### De gegevens parseren {#data-parsing}

Deze voorbeeld-JS-code parseert de eVar01 in de verrijkingen.

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
Aangezien deze code voor alle triggers wordt gebruikt, zijn de meeste gegevens niet vereist. Daarom kan het leeg worden gelaten wanneer niet aanwezig.

### De trigger opslaan {#storing-triggers-js}

>[!NOTE]
>
>Het is een specifiek voorbeeld van verschillende mogelijke implementaties.

Deze voorbeeld-JS-code slaat de trigger op in de database.

```
function processPipelineMessage(xmlTrigger)
 {```
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

De prestaties voor deze code moeten optimaal zijn omdat deze op hoge frequenties wordt uitgevoerd. Er zijn potentiële negatieve effecten voor andere marketingactiviteiten. Vooral als het verwerken van meer dan één miljoen triggergebeurtenissen per uur op de marketingserver. Of als het niet correct is ingesteld.

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
| triggerType | Tekenreeks 50 | TriggerType | De naam van de trigger. Identificeert het gedrag van de klant op de website. |
| shopper_id | String 32 | shopper_id | De interne id van de klant. Wordt ingesteld door de afstemmingsworkflow. Als nul, betekent het dat de klant in Campaign onbekend is. |
| shopper_key | Lang | shopper_key | De externe id van de klant zoals vastgelegd door Analytics. |
| gemaakt | Datumtijd | Gemaakt | De tijd waarop de gebeurtenis in Campagne werd gecreeerd. |
| lastModified | Datumtijd | Laatst gewijzigd | De laatste keer dat de gebeurtenis is gewijzigd in Adobe. |
| timeGMT | Datumtijd | Tijdstempel | Het tijdstip waarop de gebeurtenis in Analytics is gegenereerd. |

### Gebeurtenissen weergeven {#display-events}

De gebeurtenissen kunnen worden weergegeven met een eenvoudig formulier dat is gebaseerd op het gebeurtenissenschema.

>[!NOTE]
>
>Het knooppunt voor gebeurtenissen via de pijpleiding is niet ingebouwd en moet worden toegevoegd. Het gerelateerde formulier moet ook in Campagne worden gemaakt. Deze bewerkingen zijn alleen bestemd voor deskundige gebruikers. Raadpleeg de volgende secties voor meer informatie: [Navigatiehiërarchie](../../configuration/using/about-navigation-hierarchy.md) en formulieren [bewerken](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Gebeurtenissen verwerken {#processing-the-events}

### Verzoeningsworkflow {#reconciliation-workflow}

De verzoening is het proces om de klant van Analytics in het gegevensbestand van de Campagne aan te passen. De criteria voor overeenkomsten kunnen bijvoorbeeld de shopper_id zijn.

Om prestatieredenen moet de overeenkomst in batchmodus worden uitgevoerd door een workflow.
De frequentie moet op 15 minuten worden ingesteld om de werkbelasting te optimaliseren. Als gevolg hiervan is de periode tussen de ontvangst van een gebeurtenis in Adobe Campaign en de verwerking ervan via een marketingworkflow maximaal 15 minuten.

### Opties voor afstemming per eenheid in JavaScript {#options-unit-reconciliation}

In theorie, is het mogelijk om de verzoeningsvraag voor elke trekker in JavaScript in werking te stellen. Het heeft een hogere invloed op de prestaties en levert snellere resultaten op. Dit kan nodig zijn voor specifieke gevallen waarin reactiviteit nodig is.

Het kan moeilijk zijn om het te doen als geen index op shopper_id wordt geplaatst. Als de criteria op een afzonderlijke gegevensbestandserver dan de marketing server zijn, gebruikt het een gegevensbestandverbinding, die slechte prestaties heeft.

### Werkstroom leegmaken {#purge-workflow}

Triggers worden binnen het uur verwerkt, zodat er geen reden is om ze lang te houden. Het volume kan ongeveer 1 miljoen triggers per uur zijn. Er wordt uitgelegd waarom er een zuiveringsworkflow moet worden opgezet. Met de purge worden alle triggers verwijderd die ouder zijn dan drie dagen en eenmaal per dag worden uitgevoerd.

### Campagneworkflow {#campaign-workflow}

De workflow voor triggercampagnes lijkt vaak op andere terugkerende campagnes die zijn gebruikt.
Bijvoorbeeld, kan het met een vraag op de trekkers beginnen die specifieke gebeurtenissen tijdens de laatste dag zoeken. Dit doel wordt gebruikt om de e-mail te verzenden. Verrijkingen of gegevens kunnen afkomstig zijn van de trigger. Het kan veilig door Marketing worden gebruikt aangezien het geen configuratie vereist.
