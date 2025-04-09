---
product: campaign
title: Pijplijncontrole
description: Pijplijncontrole
feature: Triggers
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 84399496-33fd-4936-85e7-32de8503740f
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---

# Pijplijncontrole {#pipeline-monitoring}



De [!DNL pipelined] status-webservice geeft informatie over de status van het [!DNL pipelined] -proces.

U kunt deze functie handmatig openen in een browser of automatisch met een bewakingstoepassing.

Het heeft de REST-indeling, die hieronder wordt beschreven.

![](assets/triggers_8.png)

## Indicatoren {#indicators}

In deze sectie worden de indicatoren in de webservice voor status weergegeven.

Aanbevolen indicatoren om te controleren zijn gemarkeerd.

* Consument: naam van de cliënt die de trekker overhaalt. Geconfigureerd in de pijplijnoptie.
* http-verzoek
   * last-alive-ms-ago: Tijd in MS sinds er een verbindingscontrole is uitgevoerd.
   * last-failed-cnx-ms-ago: tijd in ms sinds de laatste tijd de verbindingscontrole ontbrak.
   * pipeline-host: naam van de host waar de pijplijngegevens vandaan worden gehaald.
* aanwijzer
   * stroom-offsets: waarde van de aanwijzer in de pijplijn, per onderliggende thread.
   * last-flush-ms-ago: Tijd in MS sinds een batch triggers is opgehaald.
   * Next-Offsets-Flush: Tijd om te wachten tot de volgende batch, als deze klaar is.
   * processed-since-last-flush: aantal triggers dat in de laatste batch is verwerkt.
* verpletteren
   * triggers: lijst met opgehaalde triggers. Gevormd in de [!DNL pipelined] optie.
* Stats
   * average-pointer-flush-time-ms: gemiddelde verwerkingstijd voor één batch triggers.
   * average-trigger-processing-time-ms: gemiddelde tijd besteed aan het ontleden van de triggergegevens.
   * bytes-gelezen: aantal bytes gelezen uit de wachtrij sinds het proces is gestart.
   * current-messages: huidige aantal berichten in behandeling die uit de wachtrij zijn opgehaald en in afwachting zijn van verwerking. **Deze indicator zou dicht aan nul** moeten zijn.
   * current-retry: huidige aantal berichten die de verwerking hebben mislukt en die op een nieuwe poging wachten.
   * piekberichten: maximumaantal berichten dat in behandeling is sinds het proces is gestart.
   * pointer-flushes: aantal batches van berichten die zijn verwerkt sinds het begin.
   * routing-JS-custom: aantal berichten dat is verwerkt door de custom JS.
   * Trigger-Disclosed: aantal berichten dat is verwijderd na te veel nieuwe pogingen vanwege verwerkingsfouten.
   * Trigger-processed: aantal berichten dat foutloos is verwerkt.
   * Trigger-Received: aantal berichten ontvangen uit de wachtrij.

Deze stats worden weergegeven per verwerkingsthread.

* average-trigger-processing-time-ms: gemiddelde tijd besteed aan het ontleden van de triggersgegevens.
* is-JS-processor: waarde &quot;1&quot; als deze thread de aangepaste JS gebruikt.
* Trigger-Disclosed: aantal berichten dat is verwijderd na te veel nieuwe pogingen vanwege verwerkingsfouten. **Deze indicator moet nul** zijn.
* trigger-failures: aantal verwerkingsfouten in de JS. **Deze indicator moet nul** zijn.
* Trigger-Received: aantal berichten ontvangen uit de wachtrij.

* Instellingen: deze worden ingesteld in de configuratiebestanden.
   * flush-pointer-msg-count: aantal berichten in een batch.
   * flush-pointer-period-ms: tijd tussen twee batches, in milliseconden.
   * processing-threads-JS: aantal verwerkingsthreads met de aangepaste JS.
   * punt-ms &#39;retry-period-ms&#39;: tijd tussen twee pogingen wanneer een verwerkingsfout optreedt.
   * hertry-validity-duration-ms: de duur vanaf de tijdverwerking wordt opnieuw geprobeerd tot het bericht wordt verworpen.
   * Rapport over pijplijnberichten

## Rapport met pijplijnberichten {#pipeline-report}

In dit rapport wordt het aantal berichten per uur in de afgelopen vijf dagen weergegeven.

![](assets/triggers_9.png)
