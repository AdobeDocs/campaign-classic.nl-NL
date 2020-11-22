---
solution: Campaign Classic
product: campaign
title: Applicatieobjecten
description: Applicatieobjecten
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 4%

---


# Applicatieobjecten{#application-objects}

Ingebouwde objecten moeten worden gecontroleerd en voorkomen dat ze te veel groeien is belangrijk.

## Volgorde van id&#39;s {#sequence-of-ids}

Adobe Campaign gebruikt een id-reeks die dienovereenkomstig moet worden gebruikt: **xtkNewId**. Als de reeks zeer snel wordt verbruikt (d.w.z. van 100.000 per dag), moet u verifiëren dat het met uw bedrijfsvereisten, zoals het verzenden van miljoenen e-mails per dag verenigbaar is. Het is mogelijk om een specifieke opeenvolging voor bepaalde lijsten te bepalen. U kunt een workflow instellen om het gebruik van de id te controleren.

Wanneer de opeenvolging meer dan 2 miljard (2.147.483.648 is het nauwkeurige aantal) bereikt, gaat het terug naar nul. Het moet worden vermeden en er moeten problemen ontstaan, en daarom moet deze volgorde worden bewaakt.

Als u dit met grote tabellen wilt voorkomen, kunt u een specifieke reeks gebruiken. Dit kan met het **pkSequence** attribuut in het schema worden gedaan.

Workflows met hoge frequentie die veel logbestanden maken, verbruiken veel id&#39;s. Daarom wordt het ten zeerste aanbevolen te veel logbestanden en hoge frequenties in workflows te vermijden.

Als de reeks al heeft gefietst, is de beste oplossing om op negatieve IDs over te schakelen, die van -2.147.483.648 begint.

## Mappen {#folders}

Er moeten minder dan 1000 mappen zijn. Als er meer mappen zijn dan dit, kunnen er prestatieproblemen optreden met de Campagneclient. U kunt een controletaak instellen om het aantal mappen, workflows, enzovoort te tellen en deze taak op gezette tijden te rapporteren.

Deze methode markeert ook gebruikers die te veel objecten maken.

## Leveringen {#deliveries}

Op elk moment moeten er minder dan 1000 leveringen plaatsvinden. Veel leveringen verbruiken databaseruimte en veroorzaken problemen. Een geval dat tot meer dan 10 leveringen per dag leidt moet tegen bedrijfsvereisten worden gecontroleerd. Overweeg continue leveringen te gebruiken om minder leveringen te maken. Raadpleeg [deze sectie](../../workflow/using/continuous-delivery.md) voor meer informatie.

Leveringen ouder dan twee jaar moeten uit het geval worden verwijderd.

## Bestanden {#files}

Het aantal bestanden op de schijf van de toepassingsserver mag niet oneindig toenemen.

De werkschema&#39;s van de invoer leiden tot dossiers en veroorzaken daarom schijfuitbreiding. Dit kan worden voorkomen door de standaardactiviteit van de [inzamelaar](../../workflow/using/file-collector.md) van het Dossier te gebruiken. De bestandscollector verplaatst bestanden naar een tijdelijke map en schoont deze automatisch op.

Als een werkstroom bestanden importeert en geen gebruik maakt van de standaardfuncties, moet deze worden leeggemaakt om schijfruimte tot een minimum te beperken.

## Transactionele gegevens en logboeken {#transactional-data-and-logs}

Elke [werkstroom](../../workflow/using/data-life-cycle.md#work-table) die gegevens in Adobe Campaign invoert veroorzaakt de grootte van het gegevensbestand om te groeien.

Controleer of werkstromen voor opschonen of leegmaken worden uitgevoerd en of de records op effectieve wijze worden gewist. Alle transactiegegevens en logbestanden moeten worden gewist. Met de opschoningstaak worden alleen de standaardtabellen verwijderd: bijhouden en brede logboeken. Specifieke tabellen moeten worden leeggemaakt door specifieke workflows. Zie [deze sectie](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Controleer de oudste aanmaakdatum van de records om transactiegegevens te verouderen.
