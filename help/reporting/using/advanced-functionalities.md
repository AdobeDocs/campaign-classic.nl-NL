---
solution: Campaign Classic
product: campaign
title: Geavanceerde mogelijkheden
description: Geavanceerde mogelijkheden
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 4%

---


# Geavanceerde mogelijkheden{#advanced-functionalities}

Als technische gebruiker, naast [algemene eigenschappen](../../reporting/using/properties-of-the-report.md), kunt u geavanceerde mogelijkheden gebruiken om uw rapporten te vormen, zoals:

* Maak complexe query&#39;s voor het verwerken van gegevens in een **Script**-activiteit. [Meer informatie](#script-activity)

* Voeg een extern script toe dat op de server of client moet worden uitgevoerd. [Meer informatie](#external-script)

* Roep een rapport aan met een **Jump** activiteit. [Meer informatie](#calling-up-another-report)

* Voeg een parameter URL aan een rapport toe om het toegankelijker te maken. [Meer informatie](#calling-up-another-report)

* Voeg variabelen toe die in de context van het rapport moeten worden gebruikt. [Meer informatie](#adding-variables)

## Werken met scripts {#adding-a-script}

### Verwijzing naar externe scripts {#external-script}

U kunt verwijzen naar JavaScript-codes die aan de client- en/of serverzijde worden uitgevoerd wanneer de rapportpagina wordt opgevraagd.

Dit doet u als volgt:

1. Bewerk de [rapporteigenschappen](../../reporting/using/properties-of-the-report.md) en klik op **[!UICONTROL Scripts]**.
1. Klik op **[!UICONTROL Add]** en selecteer het script waarnaar moet worden verwezen.
1. Selecteer vervolgens de uitvoeringsmodus.

   Als u meerdere scripts toevoegt, gebruikt u de pijlen van de werkbalk om de desbetreffende uitvoeringsvolgorde te definiëren.

   ![](assets/reporting_custom_js.png)

Voor een normale uitvoering op de client moeten de scripts waarnaar wordt verwezen, in JavaScript zijn geschreven en compatibel zijn met algemene browsers. Raadpleeg [deze sectie](../../web/using/web-forms-answers.md) voor meer informatie.

### Een scriptactiviteit {#script-activity} toevoegen

Wanneer [het ontwerpen van uw rapport](../../reporting/using/creating-a-new-report.md#modelizing-the-chart), gebruik **[!UICONTROL Script]** activiteit om gegevens te verwerken en gemakkelijk complexe vragen tot stand te brengen die SQL taal niet toelaten. U kunt uw query rechtstreeks invoeren in het scriptvenster.

Met de tab **[!UICONTROL Texts]** kunt u tekstreeksen definiëren. Deze kunnen vervolgens met de volgende syntaxis worden gebruikt: **$(Identifier)**. Raadpleeg [Koptekst en voettekst toevoegen](../../reporting/using/element-layout.md#adding-a-header-and-a-footer) voor meer informatie over het gebruik van tekst.

>[!CAUTION]
>
>We raden u NIET aan JavaScript-code te gebruiken om aggregaten te maken.

Als u een geschiedenis van uw rapport wilt maken, voegt u de volgende regel toe aan uw JavaScript-query om uw gearchiveerde gegevens op te slaan:

```
if( ctx.@_historyId.toString().length == 0 )
```

Anders worden alleen de huidige gegevens weergegeven.

## Een URL-parameter {#defining-additional-settings} toevoegen

Met het tabblad **[!UICONTROL Parameters]** van de [rapporteigenschappen](../../reporting/using/properties-of-the-report.md) kunt u aanvullende instellingen voor het rapport definiëren: deze montages zullen in URL tijdens de vraag worden overgegaan.

>[!CAUTION]
>
>Om veiligheidsredenen moeten deze parameters met grote voorzichtigheid worden gebruikt.

Een nieuwe instelling maken:

1. Klik op de knop **[!UICONTROL Add]** en voer de naam van de instelling in.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Geef indien nodig op of de instelling verplicht is.

1. Selecteer het type instelling dat u wilt maken: **[!UICONTROL Filter]** of **[!UICONTROL Variable]**.

   Met de optie **[!UICONTROL Filter entities]** kunt u een veld van de database als parameter gebruiken.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   De gegevens worden direct op het niveau van de entiteit teruggevorderd: **ctx/receiver/@account**.

   Met de optie **[!UICONTROL Variable]** kunt u een variabele maken of selecteren die wordt doorgegeven als een parameter van de URL en die kan worden gebruikt in de filters.

Met **[!UICONTROL Response HTTP headers]** kunt u klikaanvallen voorkomen wanneer u de pagina van uw rapport opneemt in een HTML-pagina die iframe gebruikt. Als u wilt voorkomen dat wordt geklikt, kunt u het gedrag **[!UICONTROL X-Frame-options header]** kiezen:

* **[!UICONTROL None]**: Het verslag heeft niets  **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: Standaard ingesteld voor nieuwe rapporten en opnieuw gepubliceerde rapporten. De hostname zal het zelfde als URL van het rapport zijn.
* **[!UICONTROL Deny]**: Het rapport kan niet worden opgenomen in een HTML-pagina die iframe gebruikt.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Variabelen {#adding-variables} toevoegen

Het **[!UICONTROL Variables]** lusje bevat de lijst van variabelen die in het rapport worden gevormd. Deze variabelen worden in de context van het verslag weergegeven en kunnen in berekeningen worden gebruikt.

Klik op de knop **[!UICONTROL Add]** om een nieuwe variabele te maken.

Als u de definitie van een variabele wilt weergeven, selecteert u de variabele en klikt u op de knop **[!UICONTROL Detail...]**.

![](assets/s_ncs_advuser_report_properties_10.png)

## Hoofdlettergebruik: gebruik variabelen en parameters in een rapport

In het videovoorbeeld hieronder, zult u leren hoe te om een &quot;_type&quot;parameter toe te voegen om verschillende meningen van een rapport tot stand te brengen, die op de waarde van dit attribuut wordt gebaseerd.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## Een ander rapport opvragen {#calling-up-another-report}

Een **Jump** activiteit is als een overgang zonder een pijl: het laat u van één activiteit naar een andere gaan of tot een ander rapport toegang hebben.
