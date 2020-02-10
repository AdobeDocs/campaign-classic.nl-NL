---
title: Uitsluiting
seo-title: Uitsluiting
description: Uitsluiting
seo-description: null
page-status-flag: never-activated
uuid: e4f54a0b-2fec-4415-986b-83c8928ed174
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: acab51f3-686b-4d2b-bb02-8fbfae36b1ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Uitsluiting{#exclusion}

Een **uitsluitingsactiviteit** leidt tot een doel dat op een hoofddoel wordt gebaseerd waarvan één of meerdere andere doelstellingen worden gehaald.

Om deze activiteit te vormen, ga zijn etiket in en selecteer de belangrijkste ontvankelijke reeks: de bevolking van de belangrijkste reeks laat u het resultaat construeren. Profielen die door de hoofdset en ten minste een van de entry-activiteiten worden gedeeld, worden uitgesloten.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>Voor meer bij het vormen van en het gebruiken van de uitsluitingsactiviteit, verwijs naar het [Uitsluiten van een bevolking (Uitsluiting)](../../workflow/using/targeting-data.md#excluding-a-population--exclusion-).

Controleer de **[!UICONTROL Generate complement]** optie als u de resterende populatie wilt uitbuiten. De aanvulling zal de belangrijkste inkomende bevolking min de uitgaande bevolking bevatten. Vervolgens wordt als volgt een extra uitvoerovergang aan de activiteit toegevoegd:

![](assets/s_user_segmentation_exclu_compl.png)

## Voorbeelden van uitsluitingen {#exclusion-examples}

In het volgende voorbeeld wordt getracht een lijst op te stellen van ontvangers tussen 18 en 30 jaar oud, met uitzondering van inwoners van Parijs.

1. Voeg een activiteit van het **[!UICONTROL Exclusion]** type -type in en open deze na twee vragen. De eerste vraag richt ontvangers die in Parijs wonen. De tweede vraag richt zich die van 18 tot 30 jaar oud.
1. Voer de hoofdset in. Hier is de belangrijkste reeks de **18-30 jaar oude** vraag. Elementen die betrekking hebben op de tweede set, worden uitgesloten van het eindresultaat.
1. Schakel de **[!UICONTROL Generate complement]** optie in als u de gegevens die na de uitsluiting overblijven, wilt gebruiken. In dit geval bestaat de aanvulling uit ontvangers in de leeftijd van 18 tot 30 jaar die in Parijs wonen.
1. Goedkeuren van de uitsluitingsconfiguratie en voegen vervolgens een activiteit uit de updatelijst in het resultaat. U kunt waar nodig ook een extra lijstupdate aan het complement toevoegen.
1. Voer de workflow uit. In dit voorbeeld bestaat het resultaat uit ontvangers tussen de 18 en 30 jaar, maar degenen die in Parijs wonen, worden uitgesloten en naar het complement gestuurd.

   ![](assets/exclusion_example.png)

In het voorbeeld van import op een zwarte lijst wordt een activiteit van het type **Uitsluiting** gebruikt die u kunt vinden in de [lijst](../../workflow/using/read-list.md)Lezen.

## Invoerparameters {#input-parameters}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert het doel dat uit de uitsluiting voortvloeit. **[!UICONTROL tableName]** is de naam van de lijst die de doelherkenningstekens registreert, **[!UICONTROL schema]** is het schema van de bevolking (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de lijst.

De overgang verbonden aan het complement heeft de zelfde parameters.
