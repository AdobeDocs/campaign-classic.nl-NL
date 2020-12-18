---
solution: Campaign Classic
product: campaign
title: Aanbiedingen per cel
description: Aanbiedingen per cel
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 8%

---


# Aanbiedingen per cel{#offers-by-cell}

De **[!UICONTROL Offers by cell]** activiteit laat u de binnenkomende bevolking (van een vraag bijvoorbeeld) in verscheidene segmenten verdelen en een aanbieding specificeren om voor elk van deze segmenten voor te stellen.

Deze activiteit kan slechts met **Interactie** worden gebruikt. Zie deze [sectie](../../interaction/using/about-outbound-channels.md) voor meer informatie.

Dit doet u als volgt:

1. Voeg de **[!UICONTROL Offers by cell]** activiteit toe zodra u de doelpopulatie hebt gespecificeerd, dan open het.
1. Selecteer op het tabblad **[!UICONTROL General]** de aanbiedingsruimte waarop u de aanbiedingen wilt weergeven.
1. Geef op het tabblad **[!UICONTROL Cells]** de verschillende subsets op met de knop **[!UICONTROL Add]**:

   * Geef de subsetpopulatie op met behulp van de beschikbare regels voor filteren en beperken.
   * Selecteer vervolgens het voorstel dat u aan de subset wilt presenteren. De beschikbare aanbiedingen zijn die welke in aanmerking komen op de aanbiedingsruimte die bij de vorige stap werd geselecteerd.

      ![](assets/int_offer_per_cell1.png)

1. Dan vorm een leveringsactiviteit die aan uw gekozen kanaal beantwoordt. Zie [Kanaaloverschrijvingen](../../workflow/using/cross-channel-deliveries.md).

