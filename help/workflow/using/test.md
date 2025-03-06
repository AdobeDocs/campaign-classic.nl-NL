---
product: campaign
title: Testen
description: Meer informatie over de activiteit van de testworkflow
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%

---

# Testen{#test}



A **het type van de Test** activiteit activeert de eerste overgang die aan de voorwaarde verbonden aan het voldoet. Als aan geen voorwaarde wordt voldaan en als de optie **[!UICONTROL Use the default fork]** wordt geactiveerd, wordt de standaardovergang geactiveerd.

Een voorwaarde is een JavaScript-expressie die moet worden geëvalueerd op &#39;true&#39; of &#39;false&#39;. Als u de expressie wilt invoeren, klikt u op het pictogram rechts van de naam van de voorwaarde en selecteert u **[!UICONTROL Edit...]** .

![](assets/edit_test.png)

Voor meer informatie over alle extra functies van JavaScript en de methodes van SOAP van de toepassingsserver die via werkschema JavaScript toegankelijk zijn, verwijs naar [ JSAPI documentatie ](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=nl).

U kunt variabelen ook rechtstreeks vanuit deze editor invoegen. Voor meer informatie over hoe te met variabelen te werken, verwijs naar [ deze sectie ](javascript-scripts-and-templates.md#variables).

Voorwaarden kunnen worden toegevoegd, verwijderd of geordend in het bewerkingsvenster van de eigenschap activity, maar kunnen ook worden gewijzigd vanuit de overgang.

Als het resultaat van een berekening door verschillende voorwaarden moet worden hergebruikt, is het mogelijk om het in het initialisatiescript van de activiteit te berekenen. Het resultaat moet worden opgeslagen in een variabele van de taak die door de voorwaardenscripts (task.vars.xxx) moet worden betreden.
