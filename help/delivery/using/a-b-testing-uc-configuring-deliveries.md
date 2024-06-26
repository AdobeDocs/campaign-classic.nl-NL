---
product: campaign
title: Leveringen configureren
description: Leer hoe u A/B-tests kunt uitvoeren met een speciale praktijkcase
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# AB testen: De leveringen in de workflow configureren {#step-4--configuring-the-deliveries-in-the-workflow}

Eenmaal [populaties worden gecreëerd](a-b-testing-uc-population-samples.md), kunt u de leveringen configureren. In dit geval, laten de eerste twee leveringen u toe om verschillende inhoud naar populatie A en B te verzenden. De derde levering is de terugroeplevering: deze wordt verzonden naar de ontvangers die niet tot A of B behoren. De inhoud ervan wordt berekend met behulp van een script en is gelijk aan A of B, afhankelijk van welke score de hoogste open snelheid heeft behaald. We moeten een wachtperiode configureren voor de derde levering, om het resultaat van de leveringen A en B te achterhalen. Daarom omvat de derde levering een **[!UICONTROL Wait]** activiteit.

1. Ga naar de **[!UICONTROL Split]** activiteit en koppel de overgang voor populatie A aan één van de e-mailleveringen reeds in het werkschema.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Dubbelklik op de levering om deze te openen.
1. Selecteer de sjabloon voor levering A in de vervolgkeuzelijst.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Klikken **[!UICONTROL Continue]** om de levering te bekijken, dan sparen het.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. De overgang van de **[!UICONTROL Split]** activiteit bestemd voor populatie B tot de tweede e-maillevering.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Open de levering en selecteer het malplaatje in levering B, dan sparen de levering.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Koppel de overgang voor de resterende bevolking aan de **[!UICONTROL Wait]** activiteit.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Open de **[!UICONTROL Wait]** en configureer een wachttijd van 5 dagen.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Koppel de **[!UICONTROL Wait]** aan de **[!UICONTROL JavaScript code]** activiteit.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

U kunt nu het script maken. [Meer informatie](a-b-testing-uc-script.md).
