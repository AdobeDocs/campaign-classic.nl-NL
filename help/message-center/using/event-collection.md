---
solution: Campaign Classic
product: campaign
title: Gebeurtenisverzameling
description: Gebeurtenisverzameling
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 5%

---


# Gebeurtenisverzameling{#event-collection}

Gebeurtenissen die door het informatiesysteem worden gegenereerd, kunnen in twee modi worden verzameld:

* Met aanroepen van SOAP-methoden kunt u gebeurtenissen in Adobe Campaign duwen: Met de methode PushEvent kunt u één gebeurtenis tegelijk verzenden. Met de methode PushEvents kunt u verschillende gebeurtenissen tegelijk verzenden. Zie [Gebeurtenisbeschrijving](../../message-center/using/event-description.md).
* Door een workflow te maken kunt u gebeurtenissen herstellen door bestanden of via een SQL-gateway te importeren (met de optie **Federated Data Access**).

Zodra zij worden verzameld, worden de gebeurtenissen uitgesplitst - door technische werkschema&#39;s - tussen echt - tijd en partijrijen van de uitvoeringsinstanties, terwijl het wachten om aan een berichtmalplaatje worden verbonden.

![](assets/messagecenter_events_queues_001.png)
