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
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---


# Pipetcontrole {#pipeline-monitoring}

De webservice voor gepipetteerde status geeft informatie over de status van het gepipetteerde proces.

U kunt deze functie handmatig openen in een browser of automatisch met een bewakingstoepassing.

Het heeft de REST-indeling, die hieronder wordt beschreven.

![](assets/triggers_8.png)

## Indicatoren {#indicators}

In deze sectie worden de indicatoren in de webservice voor status weergegeven.

Aanbevolen indicatoren voor de bewaking worden gemarkeerd.

* Consumenten: naam van de client die de triggers heeft opgehaald. Gevormd in de pijpleidingsoptie.
* http-request
   * laatst levende ms-geleden: tijd in ms sinds een verbindingscontrole is uitgevoerd.
   * last-failed-cnx-ms-ago: tijd in ms sinds de laatste keer dat de verbindingscontrole is mislukt.
   * pijpleiding-gastheer: naam van de gastheer waar de pijpleidingsgegevens van worden getrokken.
* aanwijzer
   * huidige verschuivingen: waarde van de wijzer in de pijpleiding, per kinddraad.
   * last-flush-ms-ago: tijd in ms sinds een batch triggers is opgehaald.
   * next-offsets-flush: tijd om tot de volgende partij te wachten, wanneer gebeëindigd.
   * verwerkt-sinds-laatste-flush: aantal triggers verwerkt in de laatste batch.
* verpletteren
   * triggers: lijst met opgehaalde triggers. Gevormd in de pijpleiding optie.
* stats
   * average-pointer-flush-time-ms: gemiddelde verwerkingstijd voor één partij triggers.
   * gemiddelde-trigger-processing-time-ms: gemiddelde tijd die wordt doorgebracht het ontleden van de trekkergegevens.
   * gelezen door bytes: Het aantal bytes dat uit de wachtrij is gelezen sinds het proces is gestart.
   * current-messages: Het huidige aantal berichten in behandeling die uit de wachtrij zijn gehaald en in afwachting zijn van verwerking. **Deze indicator moet dicht bij nul** zijn.
   * huidige-pogingen: Het huidige aantal berichten dat niet is verwerkt en dat nog moet worden geprobeerd.
   * piekberichten: maximumaantal berichten dat in behandeling is sinds het proces is gestart.
   * aanwijzer-flushes: aantal batches berichten die sinds het begin zijn verwerkt.
   * routing-JS-custom: aantal berichten die door douane JS werden verwerkt.
   * trigger-disczoals genegeerd: aantal berichten die na teveel pogingen wegens verwerkingsfouten werden verworpen.
   * triggerverwerking: aantal berichten die zonder een fout werden verwerkt.
   * ontvangen trigger: aantal berichten die van de rij worden ontvangen.

Deze stats worden weergegeven per verwerkingsthread.

* gemiddelde-trigger-processing-time-ms: gemiddelde tijd die wordt doorgebracht het ontleden van de trekkergegevens.
* is-JS-processor: waarde &quot;1&quot; als deze thread de aangepaste JS gebruikt.
* trigger-disczoals genegeerd: aantal berichten die na teveel pogingen wegens verwerkingsfouten werden verworpen. **Deze indicator moet nul** zijn.
* triggerfouten: aantal verwerkingsfouten in het JS. **Deze indicator moet nul** zijn.
* ontvangen trigger: aantal berichten die van de rij worden ontvangen.

* Instellingen: ze worden ingesteld in de configuratiebestanden.
   * flush-pointer-msg-count: aantal berichten in een batch.
   * punt-ms met flush-pointer: tijd tussen twee batches, in milliseconden.
   * processing-threads-JS: aantal verwerkingsdraden die de aangepaste JS uitvoeren.
   * heruitzetperiode-ms: tijd tussen twee pogingen wanneer een verwerkingsfout voorkomt.
   * hertry-validity-duration-ms: duur van de tijdverwerking wordt opnieuw geprobeerd tot het bericht wordt verworpen.
   * Rapport pijpleidingberichten

## Pijplijnberichten {#pipeline-report}

Dit rapport geeft het aantal berichten per uur in de afgelopen vijf dagen weer.

![](assets/triggers_9.png)
