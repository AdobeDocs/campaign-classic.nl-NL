---
product: campaign
title: Uitsluiting
description: Meer informatie over de activiteit van de uitsluitingsworkflow
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Uitsluiting{#exclusion}



Een **Uitsluiting** - type activiteit leidt tot een doel dat op een belangrijkste doel wordt gebaseerd waaruit één of meerdere andere doelstellingen worden gehaald.

Om deze activiteit te vormen, ga zijn etiket in en selecteer de belangrijkste ontvankelijke reeks: de bevolking van de belangrijkste reeks laat u het resultaat construeren. Profielen die door de hoofdset en ten minste een van de entry-activiteiten worden gedeeld, worden uitgesloten.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>Voor meer bij het vormen van en het gebruiken van de uitsluitingsactiviteit, verwijs naar [ exclusief een bevolking (Uitsluiting) ](targeting-data.md#excluding-a-population--exclusion-).

Schakel de optie **[!UICONTROL Generate complement]** in als u de resterende populatie wilt benutten. De aanvulling zal de belangrijkste inkomende bevolking min de uitgaande bevolking bevatten. Vervolgens wordt als volgt een extra uitvoerovergang aan de activiteit toegevoegd:

![](assets/s_user_segmentation_exclu_compl.png)

## Voorbeelden van uitsluitingen {#exclusion-examples}

In het volgende voorbeeld wordt getracht een lijst op te stellen van ontvangers tussen 18 en 30 jaar oud, met uitzondering van inwoners van Parijs.

1. Voeg een **[!UICONTROL Exclusion]** -type activiteit in en open deze na twee query&#39;s. De eerste vraag richt ontvangers die in Parijs wonen. De tweede vraag richt zich die van 18 tot 30 jaar oud.
1. Voer de hoofdset in. Hier is de belangrijkste reeks de **18-30 jaar oude** vraag. Elementen die betrekking hebben op de tweede set, worden uitgesloten van het eindresultaat.
1. Schakel de optie **[!UICONTROL Generate complement]** in als u de gegevens die na de uitsluiting overblijven, wilt gebruiken. In dit geval bestaat de aanvulling uit ontvangers in de leeftijd van 18 tot 30 jaar die in Parijs wonen.
1. Goedkeuren van de uitsluitingsconfiguratie en voegen vervolgens een activiteit uit de updatelijst in het resultaat. U kunt waar nodig ook een extra lijstupdate aan het complement toevoegen.
1. Voer de workflow uit. In dit voorbeeld bestaat het resultaat uit ontvangers tussen de 18 en 30 jaar, maar degenen die in Parijs wonen, worden uitgesloten en naar het complement gestuurd.

   ![](assets/exclusion_example.png)

## Invoerparameters {#input-parameters}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert het doel dat uit de uitsluiting voortvloeit. **[!UICONTROL tableName]** is de naam van de tabel waarin de doel-id&#39;s worden vastgelegd. **[!UICONTROL schema]** is het schema van de populatie (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de tabel.

De overgang verbonden aan het complement heeft de zelfde parameters.
