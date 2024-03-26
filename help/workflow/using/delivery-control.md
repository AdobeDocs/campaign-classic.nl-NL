---
product: campaign
title: Leveringscontrole
description: Meer informatie over de activiteit van de workflow voor leveringsbeheer
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Workflows
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 6%

---

# Leveringscontrole{#delivery-control}



A **Afleveringscontrole** Met een handeling van het type -kunt u een levering starten, pauzeren of stoppen.

Dit kan de levering zijn die in de overgang wordt gespecificeerd, uitdrukkelijk geselecteerde levering, of een levering die door een manuscript wordt berekend. Raadpleeg voor meer informatie hierover [Aflevering](delivery.md).

![](assets/edit_diffusion_act.png)

Als u **[!UICONTROL Start]**, voert de activiteit alle vereiste stappen uit om de levering te starten (doelberekening, inhoudsvoorbereiding, levering). Als sommige van deze stappen al zijn uitgevoerd door een eerdere workflowactiviteit, worden ze niet opnieuw uitgevoerd. Als de doelschatting bijvoorbeeld al is uitgevoerd door een **[!UICONTROL Delivery]** tekstactiviteit (zie [Aflevering](delivery.md)), **[!UICONTROL Act on the delivery]** de resterende stappen ( voorbereiding en levering van inhoud ) zullen worden opgestart .

De volgende opties zijn beschikbaar:

* **[!UICONTROL Generate an outbound transition]**

  Creeert een uitgaande overgang die aan het eind van uitvoering zal worden geactiveerd. U kunt kiezen al dan niet om het doel van de uitgaande levering terug te winnen.

* **[!UICONTROL Processing errors]**

  Zie [Verwerkingsfouten](monitoring-workflow-execution.md#processing-errors).

## Invoerparameters {#input-parameters}

* deliveryId

Leverings-id als de geselecteerde actie **[!UICONTROL Specified in the transition]**.
