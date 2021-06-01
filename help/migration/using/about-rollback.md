---
product: campaign
title: Terugdraaien naar de vorige versie
description: Leer hoe u terugkeert naar de vorige versie
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Terugdraaien naar vorige versie{#about-rollback}

Na een migratie, in het geval van kwesties, zou u aan de vorige versie van Campagne kunnen moeten terugdraaien.

De terugdraaiprocedure hangt van uw aanvankelijke versie van Campagne af.

## v6.1 herstellen

Hier volgt de procedure voor het herstellen van een versie 6.1 van een versie 7.

1. Herstel de back-up van de database en herstel deze.
1. Herstel de map **Adobe Campaign v6.back** (**nl6.back** in Linux), wijzig de naam in **Adobe Campaign v6** (**nl6** in Linux) en herstel de oorspronkelijke locatie.
1. Configureer IIS opnieuw door de listen-poorten opnieuw toe te wijzen om de integratie van Adobe Campaign v6.1 op IIS-websiteniveau te herstellen.
1. Stop de Adobe Campaign v7 service.
1. Start IIS opnieuw.
1. Start de Adobe Campaign v6.1-service opnieuw.

## Herstellen naar campagne v6.02

Hier volgt de procedure voor het herstellen van een versie 6.02 van een versie 7.

1. Herstel de back-up van de database en herstel deze.
1. Herstel de map **Neolane v6.back** (**nl6.back** in Linux), wijzig de naam in **Neolane v6** (**nl6** in Linux) en herstel deze op de oorspronkelijke locatie.
1. Configureer IIS opnieuw door de listen-poorten opnieuw toe te wijzen om de integratie van Adobe Campaign v6.02 op IIS-websiteniveau te herstellen.
1. Stop de service Adobe Campaign v6.1.
1. Start IIS opnieuw.
1. Start de Adobe Campaign v6.02-service opnieuw.

## Herstellen naar campagne v5.11

Hier volgt de procedure voor het herstellen van een versie 5.11 van een versie 7.

1. Herstel de back-up van de database en herstel deze.
1. Herstel de **Neolane v5.back**-map (**nl5.back** in Linux), wijzig de naam in **Neolane v5** (**nl5** in Linux) en herstel de oorspronkelijke locatie.
1. Configureer IIS opnieuw door de listen-poorten opnieuw toe te wijzen om de integratie van Neolane v5 op IIS-websiteniveau te herstellen.
1. Stop de Adobe Campaign v7 service.
1. Start IIS opnieuw.
1. Start de Adobe Campaign v5-service opnieuw.
