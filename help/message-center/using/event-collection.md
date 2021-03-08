---
solution: Campaign Classic
product: campaign
title: Gebeurtenisverzameling
description: Gebeurtenisverzameling
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---


# Gebeurtenisverzameling{#event-collection}

Gebeurtenissen die door het informatiesysteem worden gegenereerd, kunnen in twee modi worden verzameld:

* Met aanroepen van SOAP-methoden kunt u gebeurtenissen in Adobe Campaign duwen: Met de methode PushEvent kunt u één gebeurtenis tegelijk verzenden. Met de methode PushEvents kunt u verschillende gebeurtenissen tegelijk verzenden. Zie [Gebeurtenisbeschrijving](../../message-center/using/event-description.md).
* Door een workflow te maken kunt u gebeurtenissen herstellen door bestanden of via een SQL-gateway te importeren (met de optie **Federated Data Access**).

Zodra zij worden verzameld, worden de gebeurtenissen uitgesplitst - door technische werkschema&#39;s - tussen echt - tijd en partijrijen van de uitvoeringsinstanties, terwijl het wachten om aan een berichtmalplaatje worden verbonden.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Bij de uitvoeringsinstanties moeten de mappen **[!UICONTROL Real time events]** of **[!UICONTROL Batch events]** niet worden ingesteld als weergaven, omdat dit tot problemen met toegangsrechten kan leiden. Raadpleeg [deze sectie](../../platform/using/access-management-folders.md) voor meer informatie over het instellen van een map als weergave.
