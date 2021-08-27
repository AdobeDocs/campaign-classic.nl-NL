---
product: campaign
title: Een targetinglworkflow maken
description: Leer hoe u een A/B-test uitvoert met een speciale praktijkcase.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 10%

---

# Een targetingworkflow maken {#step-1--creating-a-targeting-workflow}

![](../../assets/common.svg)

U moet uw workflow maken op het tabblad **[!UICONTROL Targeting and Workflows]** van een campagne. Het bestaat uit een **[!UICONTROL Query]** activiteit, een **[!UICONTROL Split]** activiteit verbonden met twee **[!UICONTROL Email delivery]** activiteiten, een **[!UICONTROL Wait]** activiteit, een **[!UICONTROL JavaScript code]** activiteit, en een **[!UICONTROL Delivery]** activiteit.

1. Als u dit nog niet hebt gedaan, creeer een campagne (voor meer op dit, verwijs naar [deze sectie](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Ga naar het tabblad **[!UICONTROL Targeting and Workflows]**. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Wijzig het label van de bestaande workflow of klik op **[!UICONTROL Add]** om een nieuwe workflow te maken (zie [deze sectie](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population) voor meer informatie).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Gebruik de muis om activiteiten naar het werkstroomdiagram te slepen, inclusief een **[!UICONTROL Query]** (**[!UICONTROL Target]** tab), een **[!UICONTROL Split]** (**[!UICONTROL Target]** tab), twee **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** tab), een **[!UICONTROL Wait]** activiteit (**[!UICONTROL Flow Control]** tab), een **[!UICONTROL JavaScript code]** activiteit (**[!UICONTROL Actions]** tab) en een **[!UICONTROL Delivery]** activiteit (**[!UICONTROL Actions]** tabblad).

![](assets/use_case_abtesting_targetwkfl_004.png)

U kunt nu de bevolkingssteekproeven vormen. [Meer info](a-b-testing-uc-population-samples.md).
