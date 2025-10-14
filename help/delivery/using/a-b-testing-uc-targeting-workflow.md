---
product: campaign
title: Een targetingworkflow maken
description: Leer hoe u A/B-tests kunt uitvoeren met een speciale praktijkcase
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# AB-tests: een doelworkflow maken {#step-1--creating-a-targeting-workflow}

U moet uw workflow maken op het tabblad **[!UICONTROL Targeting and Workflows]** van een campagne. Deze bestaat uit een **[!UICONTROL Query]** -activiteit, een **[!UICONTROL Split]** -activiteit die gekoppeld is aan twee **[!UICONTROL Email delivery]** -activiteiten, een **[!UICONTROL Wait]** -activiteit, een **[!UICONTROL JavaScript code]** -activiteit en een **[!UICONTROL Delivery]** -activiteit.

1. Maak een campagne als u dat nog niet hebt gedaan. Voor meer op dit, verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=nl-NL){target=_blank}.

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Ga naar de tab **[!UICONTROL Targeting and Workflows]** .

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Verander het etiket van het bestaande werkschema of klik **[!UICONTROL Add]** om nieuwe tot stand te brengen (voor meer op dit, verwijs naar de [&#x200B; Campagne v8 documentatie &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=nl-NL){target="_blank"}.

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Gebruik de muis om activiteiten naar het werkstroomdiagram te slepen, zoals een **[!UICONTROL Query]** (**[!UICONTROL Target]** tab), een **[!UICONTROL Split]** (**[!UICONTROL Target]** tab), twee **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** tab), een **[!UICONTROL Wait]** activiteit (**[!UICONTROL Flow Control]** tab), een **[!UICONTROL JavaScript code]** activiteit (**[!UICONTROL Actions]** tab) en een **[!UICONTROL Delivery]** activiteit (**[!UICONTROL Actions]** tab).

![](assets/use_case_abtesting_targetwkfl_004.png)

U kunt nu de bevolkingssteekproeven vormen. [Meer informatie](a-b-testing-uc-population-samples.md).
