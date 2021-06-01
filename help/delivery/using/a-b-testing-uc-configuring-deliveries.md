---
product: campaign
title: De verzendingen configureren
description: Leer hoe u een A/B-test uitvoert met een speciale praktijkcase.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 1%

---

# De leveringen in de workflow configureren {#step-4--configuring-the-deliveries-in-the-workflow}

De volgende stap is de leveringen te vormen. Zij zijn bestemd voor de drie populaties die in de vorige fase zijn ontstaan: [Stap 2: Bezig met configureren van populatiemonsters](#step-2--configuring-population-samples). Met de eerste twee leveringen kunt u verschillende inhoud naar populatie A en B sturen. De derde levering is bestemd voor de bevolking die noch A noch B heeft ontvangen. De inhoud ervan wordt berekend met behulp van een script en is gelijk aan A of B, afhankelijk van welke score de hoogste open snelheid heeft behaald. We moeten een wachtperiode configureren voor de derde levering, om het resultaat van de leveringen A en B te achterhalen. Dit is waarom de derde levering een **[!UICONTROL Wait]** activiteit omvat.

1. Ga naar **[!UICONTROL Split]** activiteit en verbind de overgang die voor populatie A aan één van de e-mailleveringen wordt bestemd reeds in het werkschema.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Dubbelklik op de levering om deze te openen.
1. Selecteer de sjabloon voor levering A in de vervolgkeuzelijst.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Klik **[!UICONTROL Continue]** om de levering te bekijken, dan sparen het.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Koppel de overgang van de **[!UICONTROL Split]** activiteit bestemd voor populatie B aan de tweede e-maillevering.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Open de levering en selecteer het malplaatje in levering B, dan sparen de levering.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Koppel de overgang bestemd voor de resterende populatie aan de **[!UICONTROL Wait]** activiteit.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Open de **[!UICONTROL Wait]** activiteit en vorm een wachttijd van 5 dagen.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Koppel de **[!UICONTROL Wait]** activiteit aan **[!UICONTROL JavaScript code]** activiteit.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

U kunt nu het script maken (zie [Stap 5: Maak het script (](../../delivery/using/a-b-testing-uc-script.md)).
