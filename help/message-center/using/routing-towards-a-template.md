---
solution: Campaign Classic
product: campaign
title: Routering naar een sjabloon
description: Routering naar een sjabloon
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 9%

---


# Routering naar een sjabloon{#routing-towards-a-template}

Nadat de berichtsjabloon op de uitvoeringsinstantie(s) is gepubliceerd, worden automatisch twee sjablonen gegenereerd die aan een realtime- of batchgebeurtenis moeten worden gekoppeld. De verpletterende stap bestaat uit het verbinden van een gebeurtenis aan het aangewezen berichtmalplaatje. Koppelen is gebaseerd op het gebeurtenistype dat is opgegeven in de eigenschappen van de gebeurtenis zelf en die van de sjabloon.

Definitie van het gebeurtenistype in de eigenschappen van de gebeurtenis:

![](assets/messagecenter_event_type_001.png)

Definitie van het gebeurtenistype in de eigenschappen van het berichtmalplaatje:

![](assets/messagecenter_event_type_002.png)

Door gebrek, is het verpletteren gebaseerd op de volgende informatie:

* Het gebeurtenistype
* Het kanaal dat moet worden gebruikt (standaard: e-mail)
* De meest recente leveringstemplate, gebaseerd op de publicatiedatum
