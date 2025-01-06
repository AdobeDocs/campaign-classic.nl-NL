---
product: campaign
title: Geavanceerde mogelijkheden
description: Meer informatie over geavanceerde mogelijkheden bij het werken met rapporten
feature: Reporting, Monitoring
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 4%

---

# Geavanceerde mogelijkheden{#advanced-functionalities}



Als technische gebruiker, naast [ algemene eigenschappen ](../../reporting/using/properties-of-the-report.md), kunt u hefboomwerking geavanceerde mogelijkheden gebruiken om uw rapporten, zoals te vormen:

* Creeer complexe vragen om gegevens in de activiteit van het a **Manuscript** te verwerken. [Meer informatie](#script-activity)

* Voeg een extern script toe dat op de server of client moet worden uitgevoerd. [Meer informatie](#external-script)

* Vraag een rapport met a **Jump** activiteit. [Meer informatie](#calling-up-another-report)

* Voeg een parameter URL aan een rapport toe om het toegankelijker te maken. [Meer informatie](#calling-up-another-report)

* Voeg variabelen toe die in de context van het rapport moeten worden gebruikt. [Meer informatie](#adding-variables)

## Werken met scripts {#adding-a-script}

### Externe scripts {#external-script}

U kunt verwijzen naar JavaScript-codes die aan de client- en/of serverzijde worden uitgevoerd wanneer de rapportpagina wordt opgevraagd.

Dit doet u als volgt:

1. Bewerk de [ rapporteigenschappen ](../../reporting/using/properties-of-the-report.md) en klik **[!UICONTROL Scripts]**.
1. Klik op **[!UICONTROL Add]** en selecteer het script waarnaar moet worden verwezen.
1. Selecteer vervolgens de uitvoeringsmodus.

   Als u meerdere scripts toevoegt, gebruikt u de pijlen van de werkbalk om de desbetreffende uitvoeringsvolgorde te definiëren.

   ![](assets/reporting_custom_js.png)

Voor een normale uitvoering op de client moeten de scripts waarnaar wordt verwezen, in JavaScript zijn geschreven en compatibel zijn met gewone browsers. Raadpleeg [deze sectie](../../web/using/web-forms-answers.md) voor meer informatie.

### Een scriptactiviteit toevoegen {#script-activity}

Wanneer [ het ontwerpen van uw rapport ](../../reporting/using/creating-a-new-report.md#modelizing-the-chart), gebruik de **[!UICONTROL Script]** activiteit om gegevens te verwerken en gemakkelijk complexe vragen tot stand te brengen die SQL taal niet toelaten. U kunt uw query rechtstreeks invoeren in het scriptvenster.

Op het tabblad **[!UICONTROL Texts]** kunt u tekstreeksen definiëren. Zij kunnen dan met de volgende syntaxis worden gebruikt: **$ (Herkenningsteken)**. Voor meer bij het gebruiken van teksten, verwijs naar [ Toevoegend een kopbal en footer ](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>We raden u NIET aan JavaScript-code te gebruiken om aggregaten te maken.

Als u een geschiedenis van uw rapport wilt maken, voegt u de volgende regel toe aan uw JavaScript-query om uw gearchiveerde gegevens op te slaan:

```
if( ctx.@_historyId.toString().length == 0 )
```

Anders worden alleen de huidige gegevens weergegeven.

## Een URL-parameter toevoegen {#defining-additional-settings}

Het **[!UICONTROL Parameters]** lusje van de [ rapporteigenschappen ](../../reporting/using/properties-of-the-report.md) laat u extra montages voor het rapport bepalen: deze montages zullen in URL tijdens de vraag omhoog worden overgegaan.

>[!CAUTION]
>
>Om veiligheidsredenen moeten deze parameters met grote voorzichtigheid worden gebruikt.

Een nieuwe instelling maken:

1. Klik op **[!UICONTROL Add]** en voer de naam van de instelling in.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Geef indien nodig op of de instelling verplicht is.

1. Selecteer het type instelling dat u wilt maken: **[!UICONTROL Filter]** of **[!UICONTROL Variable]** .

   Met de optie **[!UICONTROL Filter entities]** kunt u een veld van de database als parameter gebruiken.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   De gegevens worden teruggekregen direct op het entiteitniveau: **ctx/ontvanger/@rekening**.

   Met de optie **[!UICONTROL Variable]** kunt u een variabele maken of selecteren die wordt doorgegeven als een parameter van de URL en die kan worden gebruikt in de filters.

Met **[!UICONTROL Response HTTP headers]** kunt u voorkomen dat wordt geklikt wanneer de rapportpagina wordt opgenomen in een HTML-pagina met iframe. Als u wilt voorkomen dat er wordt geklikt, kunt u het gedrag **[!UICONTROL X-Frame-options header]** kiezen:

* **[!UICONTROL None]**: Het rapport heeft geen **[!UICONTROL X-Frame-options header]** .
* **[!UICONTROL Same as origin]**: standaard ingesteld voor nieuwe rapporten en opnieuw gepubliceerde rapporten. De hostname zal het zelfde als URL van het rapport zijn.
* **[!UICONTROL Deny]**: Het rapport kan niet worden opgenomen in een HTML-pagina die iframe gebruikt.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Variabelen toevoegen {#adding-variables}

Het tabblad **[!UICONTROL Variables]** bevat de lijst met variabelen die in het rapport zijn geconfigureerd. Deze variabelen worden in de context van het verslag weergegeven en kunnen in berekeningen worden gebruikt.

Klik op de knop **[!UICONTROL Add]** om een nieuwe variabele te maken.

Als u de definitie van een variabele wilt weergeven, selecteert u de variabele en klikt u op de knop **[!UICONTROL Detail...]** .

![](assets/s_ncs_advuser_report_properties_10.png)

## Hoofdlettergebruik: gebruik variabelen en parameters in een rapport

In het videovoorbeeld hieronder, zult u leren hoe te om een &quot;_type&quot;parameter toe te voegen om verschillende meningen van een rapport tot stand te brengen, die op de waarde van dit attribuut wordt gebaseerd.

<!--
![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&ref=helpx.adobe.com)-->


## Een ander rapport opvragen {#calling-up-another-report}

A **de activiteit van de Jump** is als een overgang zonder een pijl: het laat u van één activiteit naar een andere gaan of tot een ander rapport toegang hebben.
