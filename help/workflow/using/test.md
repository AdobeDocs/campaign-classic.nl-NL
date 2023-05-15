---
product: campaign
title: Testen
description: Meer informatie over de activiteit van de testworkflow
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# Testen{#test}



A **Testen** type activity activeert de eerste overgang die voldoet aan de bijbehorende voorwaarde. Indien aan geen voorwaarde is voldaan en indien de **[!UICONTROL Use the default fork]** wordt geactiveerd, wordt de standaardovergang geactiveerd.

Een voorwaarde is een JavaScript-expressie die moet worden geëvalueerd op &#39;true&#39; of &#39;false&#39;. Als u de expressie wilt invoeren, klikt u op het pictogram rechts van de naam van de voorwaarde en selecteert u **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Raadpleeg voor meer informatie over alle extra JavaScript-functies en SOAP-methoden van de toepassingsserver die toegankelijk zijn via workflow JavaScript de volgende bronnen: [JSAPI-documentatie](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=nl).

U kunt variabelen ook rechtstreeks vanuit deze editor invoegen. Raadpleeg voor meer informatie over het werken met variabelen [deze sectie](javascript-scripts-and-templates.md#variables).

Voorwaarden kunnen worden toegevoegd, verwijderd of geordend in het bewerkingsvenster van de eigenschap activity, maar kunnen ook worden gewijzigd vanuit de overgang.

Als het resultaat van een berekening door verschillende voorwaarden moet worden hergebruikt, is het mogelijk om het in het initialisatiescript van de activiteit te berekenen. Het resultaat moet worden opgeslagen in een variabele van de taak die door de voorwaardenscripts (task.vars.xxx) moet worden betreden.
