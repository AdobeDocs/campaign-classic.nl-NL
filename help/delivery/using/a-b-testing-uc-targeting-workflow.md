---
product: campaign
title: Een targetingworkflow maken
description: Leer hoe u A/B-tests kunt uitvoeren met een speciale praktijkcase
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 10%

---

# Een targetingworkflow maken {#step-1--creating-a-targeting-workflow}



U moet uw workflow maken in het dialoogvenster **[!UICONTROL Targeting and Workflows]** tabblad van een campagne. Het bestaat uit een **[!UICONTROL Query]** activiteit **[!UICONTROL Split]** activiteiten in verband met twee **[!UICONTROL Email delivery]** activiteiten **[!UICONTROL Wait]** activiteit **[!UICONTROL JavaScript code]** en een **[!UICONTROL Delivery]** activiteit.

1. Als u dit nog niet hebt gedaan, maakt u een campagne (voor meer informatie hierover raadpleegt u [deze sectie](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Ga naar het tabblad **[!UICONTROL Targeting and Workflows]**. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Wijzig het label van de bestaande workflow of klik op **[!UICONTROL Add]** om een nieuwe te maken (voor meer informatie hierover raadpleegt u [deze sectie](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Gebruik de muis om activiteiten naar het werkstroomdiagram te slepen, inclusief een **[!UICONTROL Query]** (**[!UICONTROL Target]** tab), a **[!UICONTROL Split]** (**[!UICONTROL Target]** tab), twee **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** tab), a **[!UICONTROL Wait]** activiteit (**[!UICONTROL Flow Control]** tab), a **[!UICONTROL JavaScript code]** activiteit (**[!UICONTROL Actions]** en een **[!UICONTROL Delivery]** activiteit (**[!UICONTROL Actions]** ).

![](assets/use_case_abtesting_targetwkfl_004.png)

U kunt nu de bevolkingssteekproeven vormen. [Meer informatie](a-b-testing-uc-population-samples.md).
