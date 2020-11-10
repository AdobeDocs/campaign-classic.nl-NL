---
title: Leveringscontrole
description: Meer informatie over de activiteit van de workflow voor leveringsbeheer
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---


# Leveringscontrole{#delivery-control}

Met een **handeling van het type Delivery** kunt u een levering starten, pauzeren of stoppen.

Dit kan de levering zijn die in de overgang wordt gespecificeerd, uitdrukkelijk geselecteerde levering, of een levering die door een manuscript wordt berekend. For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

Als u **[!UICONTROL Start]** deze optie selecteert, voert de activiteit alle vereiste stappen uit om de levering te starten (doelberekening, inhoudsvoorbereiding, levering). Als sommige van deze stappen al zijn uitgevoerd door een eerdere workflowactiviteit, worden ze niet opnieuw uitgevoerd. Als de doelschatting bijvoorbeeld al door een **[!UICONTROL Delivery]** type activiteit is uitgevoerd (zie [Levering](../../workflow/using/delivery.md)), worden de resterende stappen (voorbereiding en levering van inhoud) door de **[!UICONTROL Act on the delivery]** activiteit gestart.

De volgende opties zijn beschikbaar:

* **[!UICONTROL Generate an outbound transition]**

   Creeert een uitgaande overgang die aan het eind van uitvoering zal worden geactiveerd. U kunt kiezen al dan niet om het doel van de uitgaande levering terug te winnen.

* **[!UICONTROL Processing errors]**

   Raadpleeg [Verwerkingsfouten](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Invoerparameters {#input-parameters}

* deliveryId

Leverings-id, als de geselecteerde actie **[!UICONTROL Specified in the transition]** is.
