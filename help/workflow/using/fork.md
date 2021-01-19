---
solution: Campaign Classic
product: campaign
title: Vertakking
description: Meer informatie over de workflowactiviteit van Fork
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: e5f718908d0bb6893e54c51700865ecda09c80db
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 1%

---


# Vertakking{#fork}

Met de activiteit **[!UICONTROL Fork]** kunt u meerdere uitgaande overgangen maken, zodat u verschillende activiteiten onafhankelijk binnen dezelfde workflow kunt uitvoeren.

U kunt bijvoorbeeld de activiteit na een query gebruiken om twee acties parallel uit te voeren:

* Sla het resultaat van de query op in een publiek,
* Voer een segmentatie op het resultaat uit om veelvoudige leveringen te verzenden.

U kunt de activiteit ook gebruiken in de context van het creëren van inhoud en levering verzendend automatisering, om de doelberekening en de verwezenlijking van inhoud parallel te lanceren. Er is een speciaal geval voor gebruik beschikbaar in [deze sectie](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!IMPORTANT]
>
>Uitgaande overgangen die worden toegevoegd na een **[!UICONTROL Fork]** activiteit **zullen niet** gelijktijdig uitvoeren. Dit gedrag kan van invloed zijn op de prestaties van de workflow. Gebruik deze activiteit als u verscheidene activiteiten onafhankelijk moet uitvoeren, en uiteindelijk samen hen alvorens de rest van de werkstroom uit te voeren.

Om de **[!UICONTROL Fork]** activiteit te vormen, open het het aantal en het etiket van de uitgaande overgangen bepaalt.

![](assets/s_user_segmentation_fork.png)

U kunt elke uitgaande overgangen dan vormen, dan hen samenvoegen gebruikend een [AND-join](../../workflow/using/and-join.md) activiteit, indien nodig. Op deze manier wordt de rest van de workflow alleen uitgevoerd als de uitgaande overgangen van de activiteit **[!UICONTROL Fork]** zijn voltooid.
