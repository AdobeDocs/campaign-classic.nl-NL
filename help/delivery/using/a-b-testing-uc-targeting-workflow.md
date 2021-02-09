---
solution: Campaign Classic
product: campaign
title: Een doelworkflow maken
description: Leer hoe u een A/B-test uitvoert met een speciale praktijkcase.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 9%

---


# Een doelworkflow maken {#step-1--creating-a-targeting-workflow}

U moet uw workflow maken op het tabblad **[!UICONTROL Targeting and Workflows]** van een campagne. Het bestaat uit een **[!UICONTROL Query]** activiteit, een **[!UICONTROL Split]** activiteit verbonden met twee **[!UICONTROL Email delivery]** activiteiten, een **[!UICONTROL Wait]** activiteit, een **[!UICONTROL JavaScript code]** activiteit, en een **[!UICONTROL Delivery]** activiteit.

1. Als u dit nog niet hebt gedaan, creeer een campagne (voor meer op dit, verwijs naar [sectie](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Ga naar het tabblad **[!UICONTROL Targeting and Workflows]**. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Wijzig het label van de bestaande workflow of klik op **[!UICONTROL Add]** om een nieuwe te maken (voor meer informatie hierover raadpleegt u deze [sectie](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Gebruik de muis om activiteiten naar het werkstroomdiagram te slepen, inclusief een **[!UICONTROL Query]** (**[!UICONTROL Target]** tab), een **[!UICONTROL Split]** (**[!UICONTROL Target]** tab), twee **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** tab), een **[!UICONTROL Wait]** activiteit (**[!UICONTROL Flow Control]** tab), een **[!UICONTROL JavaScript code]** activiteit (**[!UICONTROL Actions]** tab) en een **[!UICONTROL Delivery]** activiteit (**[!UICONTROL Actions]** tabblad).

![](assets/use_case_abtesting_targetwkfl_004.png)
