---
title: v6.02 herstellen
seo-title: v6.02 herstellen
description: v6.02 herstellen
seo-description: null
page-status-flag: never-activated
uuid: df21209b-4825-42fa-a303-f383f872abb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 4f65ba19-e9f0-4425-b640-f27c61394859
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# v6.02 herstellen{#restoring-v}

Hier volgt de procedure voor het herstellen van een versie 6.02 van een versie 7.

1. Herstel de back-up van de database en herstel deze.
1. Herstel de map **Neolane v6.back** (**nl6.back** in Linux), wijzig de naam in **Neolane v6** (**nl6** in Linux) en herstel de oorspronkelijke locatie.
1. Configureer IIS opnieuw door de listen-poorten opnieuw toe te wijzen om de integratie van Adobe Campaign v6.02 op IIS-websiteniveau te herstellen.
1. Stop de Adobe Campagne v6.1-service.
1. Start IIS opnieuw.
1. Start de Adobe Campagne v6.02-service opnieuw.

