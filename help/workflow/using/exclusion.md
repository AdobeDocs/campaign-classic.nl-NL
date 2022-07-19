---
product: campaign
title: Uitsluiting
description: Meer informatie over de activiteit van de uitsluitingsworkflow
feature: Workflows, Targeting Activity
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Uitsluiting{#exclusion}

![](../../assets/v7-only.svg)

An **Uitsluiting**-type activiteit leidt tot een doel dat op een hoofddoel wordt gebaseerd waaruit één of meerdere andere doelstellingen worden gehaald.

Om deze activiteit te vormen, ga zijn etiket in en selecteer de belangrijkste ontvankelijke reeks: de bevolking van de belangrijkste reeks laat u het resultaat construeren. Profielen die door de hoofdset en ten minste een van de entry-activiteiten worden gedeeld, worden uitgesloten.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>Voor meer bij het vormen van en het gebruiken van de uitsluitingsactiviteit, verwijs naar [Exclusief een populatie (Uitsluiting)](targeting-data.md#excluding-a-population--exclusion-).

Controleer de **[!UICONTROL Generate complement]** als u de overblijvende bevolking wilt uitbuiten. De aanvulling zal de belangrijkste inkomende bevolking min de uitgaande bevolking bevatten. Vervolgens wordt als volgt een extra uitvoerovergang aan de activiteit toegevoegd:

![](assets/s_user_segmentation_exclu_compl.png)

## Voorbeelden van uitsluitingen {#exclusion-examples}

In het volgende voorbeeld wordt getracht een lijst op te stellen van ontvangers tussen 18 en 30 jaar oud, met uitzondering van inwoners van Parijs.

1. Een **[!UICONTROL Exclusion]** -type activiteit na twee vragen. De eerste vraag richt ontvangers die in Parijs wonen. De tweede vraag richt zich die van 18 tot 30 jaar oud.
1. Voer de hoofdset in. Hier is de hoofdset **18-30 jaar oud** query. Elementen die betrekking hebben op de tweede set, worden uitgesloten van het eindresultaat.
1. Controleer de **[!UICONTROL Generate complement]** als u de gegevens wilt gebruiken die na de uitsluiting achterblijven. In dit geval bestaat de aanvulling uit ontvangers in de leeftijd van 18 tot 30 jaar die in Parijs wonen.
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

Deze reeks van drie waarden identificeert het doel dat uit de uitsluiting voortvloeit. **[!UICONTROL tableName]** is de naam van de lijst die de doelherkenningstekens registreert, **[!UICONTROL schema]** is het schema van de populatie (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de tabel.

De overgang verbonden aan het complement heeft de zelfde parameters.
