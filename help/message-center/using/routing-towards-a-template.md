---
title: Routering naar een sjabloon
seo-title: Routering naar een sjabloon
description: Routering naar een sjabloon
seo-description: null
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 12%

---


# Routering naar een sjabloon{#routing-towards-a-template}

Nadat de berichtsjabloon op de uitvoeringsinstantie(s) is gepubliceerd, worden automatisch twee sjablonen gegenereerd die aan een realtime- of batchgebeurtenis moeten worden gekoppeld. De verpletterende stap bestaat uit het verbinden van een gebeurtenis aan het aangewezen berichtmalplaatje. Koppelen is gebaseerd op het gebeurtenistype dat is opgegeven in de eigenschappen van de gebeurtenis zelf en die van de sjabloon.

Definitie van het gebeurtenistype in de eigenschappen van de gebeurtenis:

![](assets/messagecenter_event_type_001.png)

Definitie van het gebeurtenistype in de eigenschappen van het berichtmalplaatje:

![](assets/messagecenter_event_type_002.png)

Door gebrek, is het verpletteren gebaseerd op de volgende informatie:

* het gebeurtenistype;
* het kanaal dat moet worden gebruikt (standaard: e-mail),
* de meest recente leveringstemplate, gebaseerd op de publicatiedatum.

