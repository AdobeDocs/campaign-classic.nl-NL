---
product: campaign
title: Terugdraaien naar de vorige versie
description: Leer hoe u terugkeert naar de vorige versie
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: migration
content-type: reference
topic-tags: rollback
hide: true
hidefromtoc: true
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Terugdraaien naar de vorige versie{#about-rollback}



Na een migratie, in het geval van kwesties, zou u aan de vorige versie van Campagne kunnen moeten terugdraaien.

De terugdraaiprocedure hangt van uw aanvankelijke versie van Campagne af.

Hier volgt de procedure voor het herstellen van een versie 6.1 van een versie 7.

1. Herstel de back-up van de database en herstel deze.
1. De **Adobe Campaign v6.back** map (**nl6.back** in Linux), hernoemen **Adobe Campaign v6** (**nl6** (in Linux) en herstel het op de oorspronkelijke locatie.
1. Configureer IIS opnieuw door de listen-poorten opnieuw toe te wijzen om de integratie van Adobe Campaign v6.1 op IIS-websiteniveau te herstellen.
1. Stop de Adobe Campaign v7 service.
1. Start IIS opnieuw.
1. Start de Adobe Campaign v6.1-service opnieuw.

<!--
	
## Restore to Campaign v6.02

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

## Restore to Campaign v5.11

Here is the procedure to restore a v5.11 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v5.back** folder (**nl5.back** in Linux), rename it to **Neolane v5** (**nl5** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Neolane v5 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Re-start the Adobe Campaign v5 service.

-->