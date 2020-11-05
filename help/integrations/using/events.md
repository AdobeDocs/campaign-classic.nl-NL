---
title: Gebeurtenissen configureren
description: Leer hoe u gebeurtenissen configureert voor een aangepaste implementatie
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 0%

---


# Gebeurtenissen configureren voor aangepaste implementatie {#events}

De delen van deze configuratie zijn een douaneontwikkeling en vereisen het volgende:

* Werken met kennis van JSON-, XML- en Javascript-parsering in Adobe Campaign.
* Werken met kennis van de API&#39;s QueryDef en Writer.
* Werken met codering en verificatie met persoonlijke sleutels.

Aangezien voor het bewerken van de Javascript-code technische vaardigheden vereist zijn, probeert u dit niet zonder het juiste inzicht.

## Gebeurtenissen verwerken in JavaScript {#events-javascript}

### JavaScript-bestand {#file-js}

Pipeline gebruikt een functie JavaScript om elk bericht te verwerken. Deze functie is door de gebruiker gedefinieerd.

Het wordt gevormd in de **[!UICONTROL NmsPipeline_Config]** optie onder het &quot;JSConnector&quot;attribuut. Deze javascript wordt geroepen telkens als een gebeurtenis wordt ontvangen. Het wordt door het [!DNL pipelined] proces geleid.

Het Javascript-voorbeeldbestand is cus:triggers.js.

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

Nadat u de JavaScript-code hebt bewerkt, moet u de toepassing opnieuw starten. [!DNL pipelined]

### Gegevensindeling activeren {#trigger-format}

De [!DNL trigger] gegevens worden doorgegeven aan de JS-functie in XML-indeling.

* Het **[!UICONTROL @triggerId]** kenmerk bevat de naam van het [!DNL trigger]object.
* Het element **Verrijdingen** in JSON-indeling bevat de gegevens die door Adobe Analytics zijn gegenereerd en is gekoppeld aan de trigger.
* **[!UICONTROL @offset]** is de &quot;wijzer&quot;aan het bericht. Het wijst op de orde van het bericht binnen de rij.
* **[!UICONTROL @partition]** is een container van berichten binnen de rij. De verschuiving is relatief ten opzichte van een partitie. <br>De wachtrij bevat ongeveer 15 partities.

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

* **[!UICONTROL eVar01]** Kan de Shopper-id bevatten in tekenreeksindeling die wordt gebruikt om te combineren met Adobe Campaign-ontvangers. <br>U moet de Shopper-id vinden, de primaire sleutel.

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

De gebeurtenissen worden één voor één verwerkt, in volgorde van verschuiving. Elke draad van de [!DNL pipelined] processen een verschillende verdeling.

De &quot;verschuiving&quot; van de laatste opgehaalde gebeurtenis wordt opgeslagen in de database. Daarom als het proces wordt tegengehouden, begint het van het laatste bericht opnieuw. Dit gegeven wordt opgeslagen in het ingebouwde schema xtk:pipeOffset.

Deze aanwijzer is specifiek voor elk exemplaar en elke consument. Daarom wanneer vele instanties tot de zelfde pijpleiding met verschillende consumenten toegang hebben, krijgen zij elk alle berichten en in de zelfde orde.

De **consument** parameter van de pijpleidingsoptie identificeert de roepende instantie.

Er is momenteel geen manier om verschillende wachtrijen te hebben voor afzonderlijke omgevingen zoals &#39;staging&#39; of &#39;dev&#39;.

### Logboekregistratie en foutafhandeling {#logging-error-handling}

Logbestanden zoals logInfo() worden naar het [!DNL pipelined] logbestand gestuurd. Fouten zoals logError() worden naar het [!DNL pipelined] logbestand geschreven en zorgen ervoor dat de gebeurtenis in de wachtrij voor opnieuw proberen wordt geplaatst. In dit geval dient u het gepipetteerde log te controleren.
Foutberichten worden verschillende keren opnieuw geprobeerd in de duur die in de [!DNL pipelined] opties is ingesteld.

Voor foutopsporing en bewaking worden de volledige triggergegevens in XML-indeling naar de triggertabel in het veld &quot;data&quot; geschreven. U kunt ook een logInfo() met de triggergegevens gebruiken voor hetzelfde doel.

### De gegevens parseren {#data-parsing}

Deze voorbeeldcode voor JavaScript parseert de eVar01 in de verrijkingen.

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

De prestaties voor deze code moeten optimaal zijn, omdat deze op hoge frequenties wordt uitgevoerd en mogelijke negatieve effecten voor andere marketingactiviteiten kan hebben. Vooral als het verwerken van meer dan één miljoen triggergebeurtenissen per uur op de marketingserver of als het niet correct wordt ingesteld.

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
| shopper_key | Lang | shopper_key | De externe id van de klant, zoals vastgelegd door Analytics. |
| gemaakt | Datumtijd | Gemaakt | De tijd waarop de gebeurtenis in Campagne werd gecreeerd. |
| lastModified | Datumtijd | Laatst gewijzigd | De laatste keer dat de gebeurtenis werd gewijzigd in Adobe. |
| timeGMT | Datumtijd | Tijdstempel | De tijd waarop de gebeurtenis in Analytics is gegenereerd. |

### Gebeurtenissen weergeven {#display-events}

De gebeurtenissen kunnen worden weergegeven met een eenvoudig formulier dat is gebaseerd op het gebeurtenissenschema.

>[!NOTE]
>
>Het knooppunt voor gebeurtenissen via de pijpleiding is niet ingebouwd en moet worden toegevoegd. Het gerelateerde formulier moet ook in Campagne worden gemaakt. Deze bewerkingen zijn alleen bestemd voor deskundige gebruikers. Raadpleeg de volgende secties voor meer informatie: [Navigatiehiërarchie](../../configuration/using/about-navigation-hierarchy.md) en formulieren [bewerken](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Gebeurtenissen verwerken {#processing-the-events}

### Verzoeningsworkflow {#reconciliation-workflow}

Verzoening is het proces waarbij de klant van Adobe Analytics in de Adobe Campaign-database wordt opgenomen. De criteria voor overeenkomsten kunnen bijvoorbeeld de shopper_id zijn.

Om prestatieredenen moet de overeenkomst in batchmodus worden uitgevoerd door een workflow.
De frequentie moet op 15 minuten worden ingesteld om de werkbelasting te optimaliseren. Als gevolg hiervan is de periode tussen de ontvangst van een gebeurtenis in Adobe Campaign en de verwerking ervan via een marketingworkflow maximaal 15 minuten.

### Opties voor afstemming per eenheid in JavaScript {#options-unit-reconciliation}

Het is mogelijk om de verzoeningsvraag voor elke trekker in JavaScript in werking te stellen. Het heeft een hogere invloed op de prestaties en levert snellere resultaten op. Dit kan nodig zijn voor specifieke gevallen waarin reactiviteit nodig is.

Het kan moeilijk zijn om uit te voeren als geen index op shopper_id wordt geplaatst. Als de criteria op een afzonderlijke gegevensbestandserver dan de marketing server zijn, gebruikt het een gegevensbestandverbinding, die slechte prestaties heeft.

### Werkstroom leegmaken {#purge-workflow}

Triggers worden binnen een uur verwerkt. Het volume kan ongeveer 1 miljoen triggers per uur zijn. Er wordt uitgelegd waarom er een zuiveringsworkflow moet worden opgezet. De purge wordt eenmaal per dag uitgevoerd en verwijdert alle triggers die ouder zijn dan drie dagen.

### Campagneworkflow {#campaign-workflow}

De workflow voor triggercampagnes lijkt vaak op andere terugkerende campagnes die zijn gebruikt.
Bijvoorbeeld, kan het met een vraag op de trekkers beginnen die specifieke gebeurtenissen tijdens de laatste dag zoeken. Dit doel wordt gebruikt om de e-mail te verzenden. Verrijkingen of gegevens kunnen afkomstig zijn van de trigger. Het kan veilig door Marketing worden gebruikt aangezien het geen configuratie vereist.
