---
product: campaign
title: Geavanceerde mogelijkheden
description: Meer informatie over geavanceerde mogelijkheden bij het werken met rapporten
feature: Reporting, Monitoring
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 4%

---

# Geavanceerde mogelijkheden{#advanced-functionalities}



Als technische gebruiker, naast [algemene eigenschappen](../../reporting/using/properties-of-the-report.md)kunt u geavanceerde mogelijkheden gebruiken om uw rapporten te configureren, zoals:

* Complexe query&#39;s maken om gegevens te verwerken in een **Script** activiteit. [Meer informatie](#script-activity)

* Voeg een extern script toe dat op de server of client moet worden uitgevoerd. [Meer informatie](#external-script)

* Een rapport bellen met een **Springen** activiteit. [Meer informatie](#calling-up-another-report)

* Voeg een parameter URL aan een rapport toe om het toegankelijker te maken. [Meer informatie](#calling-up-another-report)

* Voeg variabelen toe die in de context van het rapport moeten worden gebruikt. [Meer informatie](#adding-variables)

## Werken met scripts {#adding-a-script}

### Externe scripts {#external-script}

U kunt verwijzen naar JavaScript-codes die aan de client- en/of serverzijde worden uitgevoerd wanneer de rapportpagina wordt opgevraagd.

Dit doet u als volgt:

1. Bewerk de [rapporteigenschappen](../../reporting/using/properties-of-the-report.md) en klik op de knop **[!UICONTROL Scripts]**.
1. Klikken **[!UICONTROL Add]** en selecteert u het script waarnaar moet worden verwezen.
1. Selecteer vervolgens de uitvoeringsmodus.

   Als u meerdere scripts toevoegt, gebruikt u de pijlen van de werkbalk om de desbetreffende uitvoeringsvolgorde te definiëren.

   ![](assets/reporting_custom_js.png)

Voor een normale uitvoering op de client moeten de scripts waarnaar wordt verwezen, in JavaScript zijn geschreven en compatibel zijn met algemene browsers. Raadpleeg [deze sectie](../../web/using/web-forms-answers.md) voor meer informatie.

### Een scriptactiviteit toevoegen {#script-activity}

Wanneer [uw rapport ontwerpen](../../reporting/using/creating-a-new-report.md#modelizing-the-chart), gebruikt u de **[!UICONTROL Script]** activiteit om gegevens te verwerken en gemakkelijk complexe vragen tot stand te brengen die SQL taal niet toelaten. U kunt uw query rechtstreeks invoeren in het scriptvenster.

De **[!UICONTROL Texts]** kunt u tekstreeksen definiëren. Deze kunnen vervolgens met de volgende syntaxis worden gebruikt: **$(id)**. Voor meer informatie over het gebruik van teksten raadpleegt u [Een kop- en voettekst toevoegen](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>We raden u NIET aan JavaScript-code te gebruiken om aggregaten te maken.

Als u een geschiedenis van uw rapport wilt maken, voegt u de volgende regel toe aan uw JavaScript-query om uw gearchiveerde gegevens op te slaan:

```
if( ctx.@_historyId.toString().length == 0 )
```

Anders worden alleen de huidige gegevens weergegeven.

## Een URL-parameter toevoegen {#defining-additional-settings}

De **[!UICONTROL Parameters]** tabblad van het [rapporteigenschappen](../../reporting/using/properties-of-the-report.md) laat u extra montages voor het rapport bepalen: deze montages zullen in URL tijdens de vraag omhoog worden overgegaan.

>[!CAUTION]
>
>Om veiligheidsredenen moeten deze parameters met grote voorzichtigheid worden gebruikt.

Een nieuwe instelling maken:

1. Klik op de knop **[!UICONTROL Add]** en voert u de naam van de instelling in.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Geef indien nodig op of de instelling verplicht is.

1. Selecteer het type instelling dat u wilt maken: **[!UICONTROL Filter]** of **[!UICONTROL Variable]**.

   De **[!UICONTROL Filter entities]** kunt u een veld van de database als parameter gebruiken.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   De gegevens worden direct op entiteitniveau teruggevorderd: **ctx/ontvanger/@account**.

   De **[!UICONTROL Variable]** Met deze optie kunt u een variabele maken of selecteren die als parameter van de URL wordt doorgegeven en die in de filters kan worden gebruikt.

De **[!UICONTROL Response HTTP headers]** staat u toe om klikjacking te verhinderen wanneer het omvatten van de pagina van uw rapport in een HTML pagina gebruikend iframe. Als u wilt voorkomen dat er op de knop wordt geklikt, kunt u de optie **[!UICONTROL X-Frame-options header]** gedrag:

* **[!UICONTROL None]**: Het verslag bevat geen **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: Standaard ingesteld voor nieuwe rapporten en opnieuw gepubliceerde rapporten. De hostname zal het zelfde als URL van het rapport zijn.
* **[!UICONTROL Deny]**: Het rapport kan niet worden opgenomen in een HTML-pagina die iframe gebruikt.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Variabelen toevoegen {#adding-variables}

De **[!UICONTROL Variables]** bevat de lijst met variabelen die in het rapport zijn geconfigureerd. Deze variabelen worden in de context van het verslag weergegeven en kunnen in berekeningen worden gebruikt.

Klik op de knop **[!UICONTROL Add]** om een nieuwe variabele te maken.

Als u de definitie van een variabele wilt weergeven, selecteert u de variabele en klikt u op de knop **[!UICONTROL Detail...]** knop.

![](assets/s_ncs_advuser_report_properties_10.png)

## Hoofdlettergebruik: gebruik variabelen en parameters in een rapport

In het videovoorbeeld hieronder, zult u leren hoe te om een &quot;_type&quot;parameter toe te voegen om verschillende meningen van een rapport tot stand te brengen, die op de waarde van dit attribuut wordt gebaseerd.

<!--
![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&ref=helpx.adobe.com)-->


## Een ander rapport opvragen {#calling-up-another-report}

A **Springen** activiteit is als een overgang zonder een pijl: het laat u van één activiteit naar een andere gaan of tot een ander rapport toegang hebben.
