---
product: campaign
title: Een targetingworkflow maken
description: Leer hoe u A/B-tests kunt uitvoeren met een speciale praktijkcase
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# AB-tests: een doelworkflow maken {#step-1--creating-a-targeting-workflow}

U moet uw workflow maken in het dialoogvenster **[!UICONTROL Targeting and Workflows]** tabblad van een campagne. Het bestaat uit een **[!UICONTROL Query]** activiteit **[!UICONTROL Split]** activiteiten in verband met twee **[!UICONTROL Email delivery]** activiteiten **[!UICONTROL Wait]** activiteit **[!UICONTROL JavaScript code]** en een **[!UICONTROL Delivery]** activiteit.

1. Als u dit nog niet hebt gedaan, maakt u een campagne (voor meer informatie hierover raadpleegt u [deze sectie](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Ga naar de **[!UICONTROL Targeting and Workflows]** tab.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Het label van de bestaande workflow wijzigen of op **[!UICONTROL Add]** om een nieuwe te maken (zie voor meer informatie hierover [deze sectie](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Gebruik de muis om activiteiten naar het werkstroomdiagram te slepen, inclusief een **[!UICONTROL Query]** (**[!UICONTROL Target]** tab), **[!UICONTROL Split]** (**[!UICONTROL Target]** tab), twee **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** tab), **[!UICONTROL Wait]** activiteit (**[!UICONTROL Flow Control]** tab), **[!UICONTROL JavaScript code]** activiteit (**[!UICONTROL Actions]** en een **[!UICONTROL Delivery]** activiteit (**[!UICONTROL Actions]** ).

![](assets/use_case_abtesting_targetwkfl_004.png)

U kunt nu de bevolkingssteekproeven vormen. [Meer informatie](a-b-testing-uc-population-samples.md).
