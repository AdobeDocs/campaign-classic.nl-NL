---
product: campaign
title: Terugdraaien naar de vorige versie
description: Leer hoe u terugkeert naar de vorige versie
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Terugdraaien naar de vorige versie{#about-rollback}

![](../../assets/v7-only.svg)

Na een migratie, in het geval van kwesties, zou u aan de vorige versie van Campagne kunnen moeten terugdraaien.

De terugdraaiprocedure hangt van uw aanvankelijke versie van Campagne af.

## Terugzetten naar campagne v6.1

Hier volgt de procedure voor het herstellen van een versie 6.1 van een versie 7.

1. Herstel de back-up van de database en herstel deze.
1. De **Adobe Campaign v6.back** map (**nl6.back** in Linux), hernoemen **Adobe Campaign v6** (**nl6** (in Linux) en herstel het op de oorspronkelijke locatie.
1. Configureer IIS opnieuw door de listen-poorten opnieuw toe te wijzen om de integratie van Adobe Campaign v6.1 op IIS-websiteniveau te herstellen.
1. Stop de Adobe Campaign v7 service.
1. Start IIS opnieuw.
1. Start de Adobe Campaign v6.1-service opnieuw.

## Terugzetten naar campagne v6.02

Hier volgt de procedure voor het herstellen van een versie 6.02 van een versie 7.

1. Herstel de back-up van de database en herstel deze.
1. De **Neolane v6.back** map (**nl6.back** in Linux), hernoemen **Neolane v6** (**nl6** (in Linux) en herstel het op de oorspronkelijke locatie.
1. Configureer IIS opnieuw door de listen-poorten opnieuw toe te wijzen om de integratie van Adobe Campaign v6.02 op IIS-websiteniveau te herstellen.
1. Stop de service Adobe Campaign v6.1.
1. Start IIS opnieuw.
1. Start de Adobe Campaign v6.02-service opnieuw.

## Terugzetten naar campagne v5.11

Hier volgt de procedure voor het herstellen van een versie 5.11 van een versie 7.

1. Herstel de back-up van de database en herstel deze.
1. De **Neolane v5.back** map (**nl5.back** in Linux), hernoemen **Neolane v5** (**nl5** (in Linux) en herstel het op de oorspronkelijke locatie.
1. Configureer IIS opnieuw door de listen-poorten opnieuw toe te wijzen om de integratie van Neolane v5 op IIS-websiteniveau te herstellen.
1. Stop de Adobe Campaign v7 service.
1. Start IIS opnieuw.
1. Start de Adobe Campaign v5-service opnieuw.
