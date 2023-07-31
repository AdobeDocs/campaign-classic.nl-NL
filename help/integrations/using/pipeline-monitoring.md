---
product: campaign
title: Pijplijncontrole
description: Pijplijncontrole
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="Van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
exl-id: 84399496-33fd-4936-85e7-32de8503740f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 1%

---

# Pijplijncontrole {#pipeline-monitoring}



De [!DNL pipelined] status webservice geeft informatie over de status van de [!DNL pipelined] proces.

U kunt deze functie handmatig openen in een browser of automatisch met een bewakingstoepassing.

Het heeft de REST-indeling, die hieronder wordt beschreven.

![](assets/triggers_8.png)

## Indicatoren {#indicators}

In deze sectie worden de indicatoren in de webservice voor status weergegeven.

Aanbevolen indicatoren voor de bewaking worden gemarkeerd.

* Consumenten: naam van de cliënt die de trekkers trekt. Gevormd in de pijpleidingsoptie.
* http-request
   * laatst levend-ms-geleden: tijd in ms sinds een verbindingscontrole is uitgevoerd.
   * last-failed-cnx-ms-ago: tijd in ms sinds de laatste tijd de verbindingscontrole ontbrak.
   * pijpleiding-gastheer: naam van de gastheer waar de pijpleidingsgegevens van worden getrokken.
* aanwijzer
   * current-offsets: waarde van de wijzer in de pijpleiding, per kinddraad.
   * last-flush-ms-ago: tijd in ms sinds een partij triggers werd teruggewonnen.
   * next-offsets-flush: tijd om te wachten tot de volgende batch, als u klaar bent.
   * processing-since-last-flush: aantal triggers verwerkt in de laatste batch.
* verpletteren
   * triggers: lijst met opgehaalde triggers. Gevormd in [!DNL pipelined] -optie.
* stats
   * average-pointer-flush-time-ms: gemiddelde verwerkingstijd voor één batch triggers.
   * average-trigger-processing-time-ms: gemiddelde tijd besteed aan het ontleden van de triggergegevens.
   * bytes-gelezen: aantal bytes gelezen uit de wachtrij sinds het proces is gestart.
   * current-messages: huidige aantal berichten in behandeling die uit de wachtrij zijn opgehaald en in afwachting zijn van verwerking. **Deze indicator moet dicht bij nul liggen**.
   * current-retry: huidige aantal berichten die de verwerking hebben mislukt en die op een nieuwe poging wachten.
   * piekberichten: maximumaantal berichten dat in behandeling is sinds het proces is gestart.
   * pointer-flushes: aantal batches van berichten die zijn verwerkt sinds het begin.
   * routing-JS-custom: aantal berichten die zijn verwerkt door de aangepaste JS.
   * trigger-discted: aantal berichten dat is verwijderd na te veel pogingen vanwege verwerkingsfouten.
   * trigger-processing: aantal berichten dat zonder fout is verwerkt.
   * trigger-Ontvangen: aantal berichten dat van de wachtrij is ontvangen.

Deze stats worden weergegeven per verwerkingsthread.

* average-trigger-processing-time-ms: gemiddelde tijd besteed aan het ontleden van de triggergegevens.
* is-JS-processor: waarde &quot;1&quot; als deze thread de aangepaste JS gebruikt.
* trigger-discted: aantal berichten dat is verwijderd na te veel pogingen vanwege verwerkingsfouten. **Deze indicator moet nul zijn**.
* trigger-errors: aantal verwerkingsfouten in de JS. **Deze indicator moet nul zijn**.
* trigger-Ontvangen: aantal berichten dat van de wachtrij is ontvangen.

* Instellingen: deze worden ingesteld in de configuratiebestanden.
   * flush-pointer-msg-count: aantal berichten in een batch.
   * flush-pointer-period-ms: tijd tussen twee batches, in milliseconden.
   * processing-threads-JS: aantal verwerkingsthreads met de aangepaste JS.
   * punt-ms &#39;retry-period-ms&#39;: tijd tussen twee pogingen wanneer een verwerkingsfout optreedt.
   * hertry-validity-duration-ms: de duur vanaf de tijdverwerking wordt opnieuw geprobeerd tot het bericht wordt verworpen.
   * Rapport pijpleidingberichten

## Pijplijnberichten {#pipeline-report}

Dit rapport geeft het aantal berichten per uur in de afgelopen vijf dagen weer.

![](assets/triggers_9.png)
