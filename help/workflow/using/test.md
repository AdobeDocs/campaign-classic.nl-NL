---
product: campaign
title: Testen
description: Meer informatie over de activiteit van de testworkflow
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
source-git-commit: 5d9e2f7d7cea9e6d1243b0e3a790f3990772e603
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# Testen{#test}

![](../../assets/common.svg)

A **Testen** type activity activeert de eerste overgang die voldoet aan de bijbehorende voorwaarde. Indien aan geen voorwaarde is voldaan en indien de **[!UICONTROL Use the default fork]** wordt geactiveerd, wordt de standaardovergang geactiveerd.

Een voorwaarde is een JavaScript-expressie die moet worden geëvalueerd op &#39;true&#39; of &#39;false&#39;. Als u de expressie wilt invoeren, klikt u op het pictogram rechts van de naam van de voorwaarde en selecteert u **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Raadpleeg voor meer informatie over alle extra JavaScript-functies en SOAP-methoden van de toepassingsserver die toegankelijk zijn via workflow JavaScript de volgende bronnen: [JSAPI-documentatie](https://experienceleague.adobe.com/developer/campaign-api/api/index.html).

U kunt variabelen ook rechtstreeks vanuit deze editor invoegen. Raadpleeg voor meer informatie over het werken met variabelen [deze sectie](javascript-scripts-and-templates.md#variables).

Voorwaarden kunnen worden toegevoegd, verwijderd of geordend in het bewerkingsvenster van de eigenschap activity, maar kunnen ook worden gewijzigd vanuit de overgang.

Als het resultaat van een berekening door verschillende voorwaarden moet worden hergebruikt, is het mogelijk om het in het initialisatiescript van de activiteit te berekenen. Het resultaat moet worden opgeslagen in een variabele van de taak die door de voorwaardenscripts (task.vars.xxx) moet worden betreden.
