---
title: v5.11 herstellen
seo-title: v5.11 herstellen
description: v5.11 herstellen
seo-description: null
page-status-flag: never-activated
uuid: 4480c97c-5845-483c-a17b-644f05783b4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: ef778333-8e50-402b-9a69-78ac94497c67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# v5.11 herstellen{#restoring-v}

Hier volgt de procedure voor het herstellen van een versie 5.11 van een versie 7.

1. Herstel de back-up van de database en herstel deze.
1. Herstel de map **Neolane v5.back** (**nl5.back** in Linux), wijzig de naam in **Neolane v5** (**nl5** in Linux) en herstel de oorspronkelijke locatie.
1. Configureer IIS opnieuw door de listen-poorten opnieuw toe te wijzen om de integratie van Neolane v5 op IIS-websiteniveau te herstellen.
1. Stop de Adobe Campagne v7 service.
1. Start IIS opnieuw.
1. Start de Adobe Campagne v5-service opnieuw.

