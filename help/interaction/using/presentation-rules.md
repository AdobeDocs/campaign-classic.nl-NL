---
product: campaign
title: Presentatieregels
description: Presentatieregels
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 1%

---

# Presentatieregels{#presentation-rules}



## Presentatieregel maken {#creating-a-presentation-rule}

In onze databank staan verschillende reisaanbiedingen voor Europa, Afrika, de Verenigde Staten en Canada. We willen voorstellen verzenden voor een reis naar Canada, maar als de ontvanger dit soort aanbiedingen weigert, willen we ze niet meer sturen

We gaan onze regels zodanig configureren dat de reis naar Canada slechts één keer per ontvanger wordt aangeboden en niet opnieuw wordt aangeboden als ze wordt afgewezen.

1. Ga in de Adobe Campaign-boom naar de **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** knooppunt.
1. Een nieuwe **[!UICONTROL Offer presentation]** typeregel.

   ![](assets/offer_typology_example_001.png)

1. Wijzig zo nodig het label en de beschrijving.

   ![](assets/offer_typology_example_002.png)

1. Kies de optie **[!UICONTROL All channels]** om de regel tot alle kanalen uit te breiden.

   ![](assets/offer_typology_example_003.png)

1. Klik op de knop **[!UICONTROL Edit expression]** en kies de **[!UICONTROL Category]** knooppunt als expressie.

   ![](assets/offer_typology_example_004.png)

1. Kies de categorie die overeenkomt met uw reisaanbod voor Canada en klik op **[!UICONTROL OK]** om het vraagvenster te sluiten.

   ![](assets/offer_typology_example_005.png)

1. In de **[!UICONTROL Offer presentation]** kiest u dezelfde afmetingen als de afmetingen die in de omgeving zijn geconfigureerd.

   ![](assets/offer_typology_example_006.png)

1. Geef de periode op waarin de regel van toepassing wordt.

   ![](assets/offer_typology_example_007.png)

1. Beperk het voorstel tot één voorstel, zodat ontvangers die al een reis naar Canada hebben afgewezen geen ander soortgelijk aanbod meer ontvangen.

   ![](assets/offer_typology_example_008.png)

1. Selecteer de **[!UICONTROL Offers for the same category]** filter om alle aanbiedingen uit te sluiten van de **Canada** categorie.

   ![](assets/offer_typology_example_020.png)

1. Selecteer de **[!UICONTROL Rejected propositions]** filter om alleen rekening te houden met door de ontvanger afgewezen voorstellen.

   ![](assets/offer_typology_example_021.png)

1. Kies de ontvangers waarop deze regel van toepassing is.

   In ons voorbeeld kiezen we de **Frequente reizigers** ontvangers.

   ![](assets/offer_typology_example_009.png)

1. Verwijs naar de regel in een aanbiedingstype.

   ![](assets/offer_typology_example_013.png)

1. Ga naar de aanbiedingsomgeving, (**Milieu - ontvanger** in dit geval) en verwijst u naar de nieuwe typologie die u zojuist hebt gemaakt met de vervolgkeuzelijst in het dialoogvenster **[!UICONTROL Eligibility]** tab.

   ![](assets/offer_typology_example_014.png)

## De presentatieregel toepassen {#applying-the-presentation-rule}

Hier volgt een voorbeeld van de eerder gemaakte typologieregel.

We willen een eerste voorstel verzenden dat tot de categorie Canada behoort. Indien het aanbod eenmaal door een van de ontvangers wordt afgewezen, wordt het niet opnieuw aan hen aangeboden.

1. In de **Frequente reizigers** de ontvankelijke omslag, kies één van de profielen om de aanbiedingen te controleren waarvoor zij verkiesbaar zijn: klik **[!UICONTROL Propositions]** en vervolgens de **[!UICONTROL Preview]** tab.

   In ons voorbeeld: **Tim Ramsey** komt in aanmerking voor een aanbod dat deel uitmaakt van het **Amerika** categorie.

   ![](assets/offer_typology_example_015.png)

1. Begin met het maken van een e-maillevering voor uw **Frequente reizigers** ontvangers met voorstellen.
1. Selecteer de vraagparameters van de aanbiedingsmotor.

   In ons voorbeeld **Reizen in Amerika** gekozen categorie, die de **Canada** en **Verenigde Staten** subcategorieën.

   ![](assets/offer_typology_example_016.png)

1. Voeg je voorstellen in in de tekst van het bericht en verzend de levering. Raadpleeg voor meer informatie hierover [Informatie over uitgaande kanalen](../../interaction/using/about-outbound-channels.md).

   De begunstigde heeft het aanbod ontvangen waarvoor hij in aanmerking komt.

1. De ontvanger heeft het aanbod van Canada afgewezen, zoals blijkt uit de geschiedenis van het voorstel.

   ![](assets/offer_typology_example_018.png)

1. Controleer de aanbiedingen waarvoor ze nu in aanmerking komen.

   We kunnen zien dat er geen aanbiedingen voor Canada worden gekozen.

   ![](assets/offer_typology_example_019.png)
