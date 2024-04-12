---
product: campaign
title: AND-join
description: AND-join
feature: Workflows
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 5%

---

# AND-join{#and-join}



Verbinden teweegbrengt zijn uitgaande overgang slechts teweeg wanneer alle binnenkomende overgangen worden geactiveerd, d.w.z. wanneer alle vroegere activiteiten worden gebeëindigd. Op deze manier kunt u ervoor zorgen dat bepaalde activiteiten zijn voltooid voordat u doorgaat met het uitvoeren van de workflow.

U kunt bijvoorbeeld een AND-join-activiteit gebruiken in de context van het maken van inhoud en het verzenden van inhoud en automatisering, om ervoor te zorgen dat een levering pas wordt gestart wanneer de stappen voor het opvragen van doelen en het bijwerken van inhoud zijn voltooid. Een speciale gebruiksmogelijkheid is beschikbaar in [deze sectie](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

>[!NOTE]
>
>Merk op dat de binnenkomende overgangen die met verschillende het richten dimensies worden gevormd niet samen kunnen aansluiten gebruikend een **[!UICONTROL AND-join]** activiteit.

De uitgaande verzonden populatie van de activiteit wordt bepaald door een hoofdreeks onder de binnenkomende overgangen in de activiteit te kiezen.

De uitgaande overgang kan slechts één van de binnenkomende overgangspopulaties bevatten. Als de activiteit niet wordt gevormd, zal de uitgaande overgang willekeurig één van de binnenkomende populaties selecteren.

>[!CAUTION]
>
>In het geval van **AND-join** type activiteiten, worden de gebeurtenisvariabelen samengevoegd maar als een zelfde variabele tweemaal wordt bepaald, is er een conflict en de waarde blijft onbepaald. Raadpleeg [deze sectie](javascript-scripts-and-templates.md#event-variables) voor meer informatie.
