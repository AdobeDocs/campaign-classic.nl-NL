---
title: Technische workflows
seo-title: Technische workflows
description: Technische workflows
seo-description: null
page-status-flag: never-activated
uuid: dfd1b180-86b5-4740-9bad-a0e210f433c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2e648e63-06d2-4e8f-9934-066a41d18eac
translation-type: tm+mt
source-git-commit: f7527a2d9b76e34fbaa2c9471c44a7a1e7e074d7
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 11%

---


# Technische workflows{#technical-workflows}

U moet ervoor zorgen dat de technische werkschema&#39;s op de controleinstantie en de verschillende uitvoeringsinstanties inderdaad zijn gecreeerd en begonnen alvorens om het even welke transactionele berichtmalplaatjes op te stellen.

De diverse technische werkschema&#39;s met betrekking tot transactioneel overseinen (het Centrum van het Bericht) worden verdeeld tussen de controleinstantie en de uitvoeringsinstantie(s).

## Workflows voor besturingsinstanties {#control-instance-workflows}

In de besturingsinstantie moet u voor elke **[!UICONTROL Message Center execution instance]** externe account één archiveringsworkflow maken, ongeacht of u een of meerdere uitvoeringsinstanties hebt geregistreerd. Klik op de **[!UICONTROL Create the archiving workflow]** knop om de workflow te maken en te starten.

![](assets/messagecenter_archiving_002.png)

Deze workflows zijn dan toegankelijk via de map **Beheer > Productie > Berichtencentrum** . Nadat de workflows voor archivering zijn gemaakt, worden deze automatisch gestart.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

## Workflows voor uitvoeringsinstanties {#execution-instance-workflows}

Op de uitvoeringsinstantie(s) zijn de technische workflows voor transactiemelding toegankelijk via de map **Beheer > Productie > Berichtencentrum** . Je moet ze gewoon starten. De workflows in de lijst zijn:

* **[!UICONTROL Processing batch events]** (interne naam: **[!UICONTROL batchEventsProcessing]** ): met deze workflow kunt u batchgebeurtenissen in een wachtrij onderverdelen voordat deze aan een berichtsjabloon zijn gekoppeld.
* **[!UICONTROL Processing real time events]** (interne naam: **[!UICONTROL rtEventsProcessing]** ): met deze workflow kunt u real-time gebeurtenissen in een wachtrij onderverdelen voordat deze aan een berichtsjabloon zijn gekoppeld.
* **[!UICONTROL Update event status]** (interne naam: **[!UICONTROL updateEventStatus]** ): in deze workflow kunt u een status aan de gebeurtenis toewijzen.

   De volgende gebeurtenisstatussen zijn beschikbaar:

   * **[!UICONTROL Pending]** : de gebeurtenis bevindt zich in de wachtrij. Er is nog geen berichtsjabloon aan toegewezen.
   * **[!UICONTROL Pending delivery]** : de gebeurtenis is in de rij, is een berichtmalplaatje toegewezen aan het en het wordt verwerkt door de levering.
   * **[!UICONTROL Sent]** : deze status wordt gekopieerd uit de leveringslogboeken. Dit betekent dat de levering is verzonden.
   * **[!UICONTROL Ignored by the delivery]** : deze status wordt gekopieerd uit de leveringslogboeken. Het betekent dat de levering is genegeerd.
   * **[!UICONTROL Delivery failed]** : deze status wordt gekopieerd uit de leveringslogboeken. Het betekent dat de levering is mislukt.
   * **[!UICONTROL Event not taken into account]** : de gebeurtenis kon niet aan een berichtmalplaatje worden verbonden. De gebeurtenis wordt niet verwerkt.

