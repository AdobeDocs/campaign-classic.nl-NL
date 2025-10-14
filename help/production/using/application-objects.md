---
product: campaign
title: Applicatieobjecten
description: Applicatieobjecten
feature: Monitoring
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 1%

---

# Applicatieobjecten{#application-objects}



Ingebouwde objecten moeten worden gecontroleerd en voorkomen dat ze te veel groeien is belangrijk.

## Volgorde van id&#39;s {#sequence-of-ids}

Adobe Campaign gebruikt een opeenvolging van identiteitskaart die dienovereenkomstig moet worden verbruikt: **xtkNewId**. Als de reeks zeer snel wordt verbruikt (d.w.z. van 100.000 per dag), moet u verifiëren dat het met uw bedrijfsvereisten, zoals het verzenden van miljoenen e-mails per dag verenigbaar is. Het is mogelijk om een specifieke opeenvolging voor bepaalde lijsten te bepalen. U kunt een workflow instellen om het gebruik van de id te controleren.

Wanneer de opeenvolging meer dan 2 miljard (2.147.483.648 is het nauwkeurige aantal) bereikt, gaat het terug naar nul. Het moet worden vermeden en er moeten problemen ontstaan, en daarom moet deze volgorde worden bewaakt.

Als u dit met grote tabellen wilt voorkomen, kunt u een specifieke reeks gebruiken. Dit kan met het **pkSequence** attribuut in het schema worden gedaan.

Workflows met hoge frequentie die veel logbestanden maken, verbruiken veel id&#39;s. Daarom wordt het ten zeerste aanbevolen te veel logbestanden en hoge frequenties in workflows te vermijden.

Als de reeks al heeft gefietst, is de beste oplossing om op negatieve IDs over te schakelen, die van -2.147.483.648 begint.

## Mappen {#folders}

Er moeten minder dan 1000 mappen zijn. Als er meer mappen zijn dan dit, kunnen er prestatieproblemen optreden met de Campagneclient. U kunt een controletaak instellen om het aantal mappen, workflows, enzovoort te tellen en deze taak op gezette tijden te rapporteren.

Deze methode markeert ook gebruikers die te veel objecten maken.

## Leveringen {#deliveries}

Op elk moment moeten er minder dan 1000 leveringen plaatsvinden. Veel leveringen verbruiken databaseruimte en veroorzaken problemen. Een geval dat tot meer dan 10 leveringen per dag leidt moet tegen bedrijfsvereisten worden gecontroleerd. Overweeg continue leveringen te gebruiken om minder leveringen te maken. Voor meer op dit, verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/continuous-delivery.html?lang=nl-NL){target="_blank"}.

Leveringen ouder dan twee jaar moeten uit het geval worden verwijderd.

## Bestanden {#files}

Het aantal bestanden op de schijf van de toepassingsserver mag niet oneindig toenemen.

De werkschema&#39;s van de invoer leiden tot dossiers en veroorzaken daarom schijfuitbreiding. Dit kan worden verhinderd door de standaard [&#x200B; activiteit te gebruiken van de inzamelaar van het 0&rbrace; Dossier. &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-collector.html?lang=nl-NL){target="_blank"} De bestandscollector verplaatst bestanden naar een tijdelijke map en schoont deze automatisch op.

Als een werkstroom bestanden importeert en geen gebruik maakt van de standaardfuncties, moet deze worden leeggemaakt om schijfruimte tot een minimum te beperken.

## Transactionele gegevens en logboeken {#transactional-data-and-logs}

Elke werkstroom die gegevens in Adobe Campaign invoert veroorzaakt de grootte van het gegevensbestand om te groeien. Verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/use-workflow-data.html?lang=nl-NL){target="_blank"}.

Controleer of werkstromen voor opschonen of leegmaken worden uitgevoerd en of de records op effectieve wijze worden gewist. Alle transactiegegevens en logbestanden moeten worden gewist. Met de opschoningstaak worden alleen de standaardtabellen verwijderd: bijhouden en brede logboeken. Specifieke tabellen moeten worden leeggemaakt door specifieke workflows. verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=nl-NL){target="_blank"}.

Controleer de oudste aanmaakdatum van de records om transactiegegevens te verouderen.
