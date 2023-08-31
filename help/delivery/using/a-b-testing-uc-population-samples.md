---
product: campaign
title: Populatievoorbeelden configureren
description: Leer hoe u A/B-tests kunt uitvoeren met een speciale praktijkcase
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 6%

---

# AB-tests: bevolkingsmonsters configureren {#step-2--configuring-population-samples}

## Vorm de activiteit van de Vraag {#configuring-the-query-activity}

* Dubbelklik op de knop **[!UICONTROL Query]** activiteit.

  ![](assets/use_case_abtesting_createrecipients_001.png)

* Klik op de knop **[!UICONTROL Edit query]** en selecteer de ontvangers u wilt richten.

  ![](assets/use_case_abtesting_createrecipients_002.png)

* Koppel de **[!UICONTROL Query]** aan de **[!UICONTROL Split]** activiteit.

  ![](assets/use_case_abtesting_createrecipients_003.png)

## De activiteit Splitsen configureren {#configuring-the-split-activity}

Deze activiteit laat u verscheidene populaties tot stand brengen: die die levering A, ontvangt die levering B ontvangt, en de resterende bevolking. Door willekeurige selectie te gebruiken, kunt u zich richten op slechts een deel van de populatie van elke levering.

1. Bezig met maken van populatie A:

   * Dubbelklik op de knop **[!UICONTROL Split]** activiteit.

     ![](assets/use_case_abtesting_createrecipients_004.png)

   * Wijzig in het bestaande tabblad het label in populatie A.

     ![](assets/use_case_abtesting_createrecipients_005.png)

   * Selecteer de **[!UICONTROL Limit the selected records]** -optie.

     ![](assets/use_case_abtesting_createrecipients_006.png)

   * Klik op de knop **[!UICONTROL Edit]** koppeling, selecteren **[!UICONTROL Activate random sampling]** en klik op **[!UICONTROL Next]**.

     ![](assets/use_case_abtesting_createrecipients_007.png)

   * Stel de drempel in op 10% en klik vervolgens op **[!UICONTROL Finish]**.

     ![](assets/use_case_abtesting_createrecipients_008.png)

1. Bezig met maken van populatie B:

   * Klikken **[!UICONTROL Add]** om een nieuw tabblad voor populatie B te maken.

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
