---
title: Gebeurtenisverzameling
seo-title: Gebeurtenisverzameling
description: Gebeurtenisverzameling
seo-description: null
page-status-flag: never-activated
uuid: 8c373962-40d4-4982-9bd1-ce1cf8261dd5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: cfff302a-6ac0-461a-a1e4-8e4b617fe134
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Gebeurtenisverzameling{#event-collection}

Gebeurtenissen die door het informatiesysteem worden gegenereerd, kunnen in twee modi worden verzameld:

* Met aanroepen van SOAP-methoden kunt u gebeurtenissen in Adobe Campaign uitvoeren: Met de methode PushEvent kunt u één gebeurtenis tegelijk verzenden. Met de methode PushEvents kunt u verschillende gebeurtenissen tegelijk verzenden. Zie de [gebeurtenisbeschrijving](../../message-center/using/event-description.md).
* Als u een workflow maakt, kunt u gebeurtenissen herstellen door bestanden of via een SQL-gateway te importeren (met de optie **Federated Data Access** ).

Zodra zij worden verzameld, worden de gebeurtenissen uitgesplitst - door technische werkschema&#39;s - tussen echt - tijd en partijrijen van de uitvoeringsinstanties, terwijl het wachten om aan een berichtmalplaatje worden verbonden.

![](assets/messagecenter_events_queues_001.png)

