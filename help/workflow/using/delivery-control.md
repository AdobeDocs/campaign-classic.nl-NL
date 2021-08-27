---
product: campaign
title: Leveringscontrole
description: Meer informatie over de activiteit van de workflow voor leveringsbeheer
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---

# Leveringscontrole{#delivery-control}

![](../../assets/common.svg)

Met een handeling van het type **Delivery control** kunt u een levering starten, pauzeren of stoppen.

Dit kan de levering zijn die in de overgang wordt gespecificeerd, uitdrukkelijk geselecteerde levering, of een levering die door een manuscript wordt berekend. Raadpleeg [Delivery](delivery.md) voor meer informatie hierover.

![](assets/edit_diffusion_act.png)

Als u **[!UICONTROL Start]** selecteert, voert de activiteit alle stappen uit die worden vereist om de levering te beginnen (doelberekening, inhoudsvoorbereiding, levering). Als sommige van deze stappen al zijn uitgevoerd door een eerdere workflowactiviteit, worden ze niet opnieuw uitgevoerd. Als de doelschatting bijvoorbeeld al is uitgevoerd door een **[!UICONTROL Delivery]** type activiteit (zie [Delivery](delivery.md)), start de **[!UICONTROL Act on the delivery]** activiteit de resterende stappen (voorbereiding en levering van inhoud).

De volgende opties zijn beschikbaar:

* **[!UICONTROL Generate an outbound transition]**

   Creeert een uitgaande overgang die aan het eind van uitvoering zal worden geactiveerd. U kunt kiezen al dan niet om het doel van de uitgaande levering terug te winnen.

* **[!UICONTROL Processing errors]**

   Zie [Fouten verwerken](monitoring-workflow-execution.md#processing-errors).

## Invoerparameters {#input-parameters}

* deliveryId

Leverings-id als de geselecteerde actie **[!UICONTROL Specified in the transition]** is.
