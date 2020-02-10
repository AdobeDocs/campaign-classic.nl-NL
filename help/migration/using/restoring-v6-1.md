---
title: v6.1 herstellen
seo-title: v6.1 herstellen
description: v6.1 herstellen
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# v6.1 herstellen{#restoring-v}

Hier volgt de procedure voor het herstellen van een versie 6.1 van een versie 7.

1. Herstel de back-up van de database en herstel deze.
1. Herstel de map **Adobe Campagne v6.back** (**nl6.back** in Linux), wijzig de naam in **Adobe Campagne v6** (**nl6** in Linux) en herstel de oorspronkelijke locatie.
1. Configureer IIS opnieuw door de listen-poorten opnieuw toe te wijzen om de integratie van Adobe Campaign v6.1 op het niveau van de IIS-website te herstellen.
1. Stop de Adobe Campagne v7 service.
1. Start IIS opnieuw.
1. Start de Adobe Campagne v6.1-service opnieuw.

