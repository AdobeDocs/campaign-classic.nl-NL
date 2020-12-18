---
solution: Campaign Classic
product: campaign
title: Test
description: Meer informatie over de activiteit van de testworkflow
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 5%

---


# Test{#test}

Een **Test** type activiteit activeert de eerste overgang die aan de voorwaarde verbonden aan het voldoet. Als aan geen voorwaarde wordt voldaan en als de optie **[!UICONTROL Use the default fork]** wordt geactiveerd, zal de standaardovergang worden geactiveerd.

Een voorwaarde is een JavaScript-expressie die moet worden geëvalueerd op &#39;true&#39; of &#39;false&#39;. Als u de expressie wilt invoeren, klikt u op het pictogram rechts van de naam van de voorwaarde en selecteert u **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Raadpleeg [JSAPI-documentatie](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) voor meer informatie over alle extra JavaScript-functies en SOAP-methoden van de toepassingsserver die toegankelijk zijn via workflow JavaScript.

U kunt variabelen ook rechtstreeks vanuit deze editor invoegen. Raadpleeg [deze sectie](../../workflow/using/javascript-scripts-and-templates.md#variables) voor meer informatie over het werken met variabelen.

Voorwaarden kunnen worden toegevoegd, verwijderd of geordend in het bewerkingsvenster van de eigenschap activity, maar kunnen ook worden gewijzigd vanuit de overgang.

Als het resultaat van een berekening door verschillende voorwaarden moet worden hergebruikt, is het mogelijk om het in het initialisatiescript van de activiteit te berekenen. Het resultaat moet worden opgeslagen in een variabele van de taak die door de voorwaardenscripts (task.vars.xxx) moet worden betreden.
