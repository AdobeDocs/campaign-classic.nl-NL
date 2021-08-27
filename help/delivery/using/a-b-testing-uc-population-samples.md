---
product: campaign
title: Populatievoorbeelden configureren
description: Leer hoe u een A/B-test uitvoert met een speciale praktijkcase.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 7%

---

# Populatievoorbeelden configureren {#step-2--configuring-population-samples}

![](../../assets/common.svg)

## Vorm de activiteit van de Vraag {#configuring-the-query-activity}

* Dubbelklik op de activiteit **[!UICONTROL Query]**.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Klik op de koppeling **[!UICONTROL Edit query]** en selecteer de ontvangers die u als doel wilt instellen.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Koppel de **[!UICONTROL Query]** activiteit aan **[!UICONTROL Split]** activiteit.

   ![](assets/use_case_abtesting_createrecipients_003.png)

## De activiteit Splitsen configureren {#configuring-the-split-activity}

Met deze activiteit kunt u verschillende populaties maken: degene die levering A ontvangt, degene die levering B ontvangt, en de resterende populatie. Door willekeurige selectie te gebruiken, kunt u zich richten op slechts een deel van de populatie van elke levering.

1. Bezig met maken van populatie A:

   * Dubbelklik op de activiteit **[!UICONTROL Split]**.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * Wijzig in het bestaande tabblad het label in populatie A.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * Selecteer de optie **[!UICONTROL Limit the selected records]**.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * Klik op de koppeling **[!UICONTROL Edit]**, selecteer **[!UICONTROL Activate random sampling]** en klik op **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * Stel de drempel in op 10% en klik op **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. Bezig met maken van populatie B:

   * Klik **[!UICONTROL Add]** om een nieuw lusje voor populatie B tot stand te brengen.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * Beperk de bevolking tot 10% zoals eerder.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. Creëren van de resterende populatie:

   * Ga naar het tabblad **[!UICONTROL General]**. 

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * Selecteer **[!UICONTROL Generate complement]**.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * Wijzig het label om aan te geven dat deze populatie geen A of B bevat en klik op **[!UICONTROL OK]** om de activiteit te sluiten.

      ![](assets/use_case_abtesting_createrecipients_013.png)

U kunt nu de twee leveringssjablonen maken. [Meer informatie](a-b-testing-uc-delivery-templates.md)).
