---
title: Geavanceerde mogelijkheden
description: Geavanceerde mogelijkheden
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
translation-type: tm+mt
source-git-commit: 2a82493deada11cb22ef37d215b6eae8274ce890
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 3%

---


# Geavanceerde mogelijkheden{#advanced-functionalities}

Als technische gebruiker, naast [algemene eigenschappen](../../reporting/using/properties-of-the-report.md), kunt u hefboomwerking geavanceerde mogelijkheden gebruiken om uw rapporten te vormen, zoals:

* Maak complexe query&#39;s voor het verwerken van gegevens in een **scriptactiviteit** . [Meer informatie](#script-activity)

* Voeg een extern script toe dat op de server of client moet worden uitgevoerd. [Meer informatie](#external-script)

* Roep een rapport met een **sprongactiviteit** aan. [Meer informatie](#calling-up-another-report)

* Voeg een parameter URL aan een rapport toe om het toegankelijker te maken. [Meer informatie](#calling-up-another-report)

* Voeg variabelen toe die in de context van het rapport moeten worden gebruikt. [Meer informatie](#adding-variables)

## Werken met scripts {#adding-a-script}

### Externe scripts {#external-script}

U kunt verwijzen naar JavaScript-codes die aan de client- en/of serverzijde worden uitgevoerd wanneer de rapportpagina wordt opgevraagd.

Dit doet u als volgt:

1. Bewerk de [rapporteigenschappen](../../reporting/using/properties-of-the-report.md) en klik op **[!UICONTROL Scripts]**.
1. Klik **[!UICONTROL Add]** en selecteer het script waarnaar moet worden verwezen.
1. Selecteer vervolgens de uitvoeringsmodus.

   Als u meerdere scripts toevoegt, gebruikt u de pijlen van de werkbalk om de desbetreffende uitvoeringsvolgorde te definiëren.

   ![](assets/reporting_custom_js.png)

Voor een normale uitvoering op de client moeten de scripts waarnaar wordt verwezen, in JavaScript zijn geschreven en compatibel zijn met algemene browsers. Raadpleeg [deze sectie](../../web/using/web-forms-answers.md) voor meer informatie.

### Een scriptactiviteit toevoegen {#script-activity}

Wanneer het [ontwerpen van uw rapport](../../reporting/using/creating-a-new-report.md#modelizing-the-chart), gebruik de **[!UICONTROL Script]** activiteit om gegevens te verwerken en gemakkelijk complexe vragen tot stand te brengen die SQL taal niet toelaten. U kunt uw query rechtstreeks invoeren in het scriptvenster.

Op het **[!UICONTROL Texts]** tabblad kunt u tekstreeksen definiëren. Deze kunnen vervolgens met de volgende syntaxis worden gebruikt: **$(Id)**. Zie Koptekst en voettekst [toevoegen voor meer informatie over het gebruik van tekst](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>We raden u NIET aan JavaScript-code te gebruiken om aggregaten te maken.

Als u een geschiedenis van uw rapport wilt maken, voegt u de volgende regel toe aan uw JavaScript-query om uw gearchiveerde gegevens op te slaan:

```
if( ctx.@_historyId.toString().length == 0 )
```

Anders worden alleen de huidige gegevens weergegeven.

## Een URL-parameter toevoegen {#defining-additional-settings}

Het **[!UICONTROL Parameters]** lusje van de [rapporteigenschappen](../../reporting/using/properties-of-the-report.md) laat u extra montages voor het rapport bepalen: deze montages zullen in URL tijdens de vraag worden overgegaan.

>[!CAUTION]
>
>Om veiligheidsredenen moeten deze parameters met grote voorzichtigheid worden gebruikt.

Een nieuwe instelling maken:

1. Klik op de **[!UICONTROL Add]** knop en voer de naam van de instelling in.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Geef indien nodig op of de instelling verplicht is.

1. Select the type of setting you want to create: **[!UICONTROL Filter]** or **[!UICONTROL Variable]**.

   Met de **[!UICONTROL Filter entities]** optie kunt u een veld van de database als parameter gebruiken.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   De gegevens worden direct op het niveau van de entiteit teruggevorderd: **ctx/ontvanger/@account**.

   Met de **[!UICONTROL Variable]** optie kunt u een variabele maken of selecteren die als parameter van de URL wordt doorgegeven en die in de filters kan worden gebruikt.

Met **[!UICONTROL Response HTTP headers]** deze optie kunt u voorkomen dat wordt geklikt wanneer de rapportpagina wordt opgenomen in een HTML-pagina die iframe gebruikt. U kunt klikken vermijden door het **[!UICONTROL X-Frame-options header]** gedrag te kiezen:

* **[!UICONTROL None]**: Het verslag heeft niets **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: Standaard ingesteld voor nieuwe rapporten en opnieuw gepubliceerde rapporten. De hostname zal het zelfde als URL van het rapport zijn.
* **[!UICONTROL Deny]**: Het rapport kan niet worden opgenomen in een HTML-pagina die iframe gebruikt.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Variabelen toevoegen {#adding-variables}

Het **[!UICONTROL Variables]** lusje bevat de lijst van variabelen die in het rapport worden gevormd. Deze variabelen worden in de context van het verslag weergegeven en kunnen in berekeningen worden gebruikt.

Klik op de **[!UICONTROL Add]** knop om een nieuwe variabele te maken.

Als u de definitie van een variabele wilt weergeven, selecteert u de variabele en klikt u op de **[!UICONTROL Detail...]** knop.

![](assets/s_ncs_advuser_report_properties_10.png)

## Hoofdlettergebruik: gebruik variabelen en parameters in een rapport

In het videovoorbeeld hieronder, zult u leren hoe te om een &quot;_type&quot;parameter toe te voegen om verschillende meningen van een rapport tot stand te brengen, die op de waarde van dit attribuut wordt gebaseerd.

![](assets/do-not-localize/how-to-video.png) [Deze functie in video detecteren](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## Een ander rapport opvragen {#calling-up-another-report}

Een **sprongactiviteit** is als een overgang zonder een pijl: het laat u van één activiteit naar een andere gaan of tot een ander rapport toegang hebben.
