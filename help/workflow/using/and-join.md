---
solution: Campaign Classic
product: campaign
title: AND-join
description: AND-join
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 3eecc16442a11849c12819cf83392f60c5b82a13
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 5%

---


# AND-join{#and-join}

Verbinden teweegbrengt zijn uitgaande overgang slechts teweeg wanneer alle binnenkomende overgangen worden geactiveerd, d.w.z. wanneer alle vroegere activiteiten worden gebeëindigd. Op deze manier kunt u ervoor zorgen dat bepaalde activiteiten zijn voltooid voordat u doorgaat met het uitvoeren van de workflow.

U kunt bijvoorbeeld een AND-join-activiteit gebruiken in de context van het maken van inhoud en het verzenden van inhoud en automatisering, om ervoor te zorgen dat een levering pas wordt gestart wanneer de stappen voor het opvragen van doelen en het bijwerken van inhoud zijn voltooid. Er is een speciale gebruikscase beschikbaar in [deze sectie](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

>[!NOTE]
>
>Merk op dat de binnenkomende overgangen die met verschillende het richten dimensies worden gevormd niet samen kunnen worden gebracht gebruikend een **[!UICONTROL AND-join]** activiteit.

De uitgaande verzonden populatie van de activiteit wordt bepaald door een hoofdreeks onder de binnenkomende overgangen in de activiteit te kiezen.

De uitgaande overgang kan slechts één van de binnenkomende overgangspopulaties bevatten. Als de activiteit niet wordt gevormd, zal de uitgaande overgang willekeurig één van de binnenkomende populaties selecteren.

>[!CAUTION]
>
>In het geval van **AND-join** type activiteiten, worden de gebeurtenisvariabelen samengevoegd maar als één variabele tweemaal wordt bepaald, is er een conflict en de waarde blijft onbepaald. Raadpleeg [deze sectie](../../workflow/using/javascript-scripts-and-templates.md#event-variables) voor meer informatie.
