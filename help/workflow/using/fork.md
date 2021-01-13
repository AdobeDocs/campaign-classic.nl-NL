---
solution: Campaign Classic
product: campaign
title: Vertakking
description: Meer informatie over de workflowactiviteit van Fork
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: d35b22386bd2681ba02e4379c627821b35a7d04e
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Vertakking{#fork}

Met de activiteit **[!UICONTROL Fork]** kunt u meerdere uitgaande overgangen maken, zodat u verschillende activiteiten onafhankelijk binnen dezelfde workflow kunt uitvoeren.

U kunt bijvoorbeeld de activiteit na een query gebruiken om twee acties parallel uit te voeren:

* Sla het resultaat van de query op in een publiek,
* Voer een segmentatie op het resultaat uit om veelvoudige leveringen te verzenden.

U kunt de activiteit ook gebruiken in de context van het creëren van inhoud en levering verzendend automatisering, om de doelberekening en de verwezenlijking van inhoud parallel te lanceren. Er is een speciaal geval voor gebruik beschikbaar in [deze sectie](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!IMPORTANT]
>
>Onthoud dat de uitgaande overgangen die na een vorkactiviteit worden toegevoegd, niet tegelijkertijd worden uitgevoerd.
>
>De activiteit moet daarom niet worden gebruikt om de prestaties van de werkstroom te verbeteren, maar om meerdere activiteiten onafhankelijk uit te voeren en uiteindelijk samen te voegen voordat de rest van de werkstroom wordt uitgevoerd.

Om de activiteit te vormen, open het dan het aantal en het etiket van de gewenste uitgaande overgangen bepaalt.

![](assets/s_user_segmentation_fork.png)

U kunt elke uitgaande overgangen dan vormen, dan hen samenvoegen gebruikend een [AND-join](../../workflow/using/and-join.md) activiteit, indien nodig. Op deze manier wordt de rest van de workflow alleen uitgevoerd wanneer de uitgaande overgangen van de activiteit **[!UICONTROL Fork]** zijn voltooid.
