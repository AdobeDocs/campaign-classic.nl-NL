---
product: campaign
title: Lay-out van element
description: Lay-out van element
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Reporting, Monitoring
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# Lay-out van element{#element-layout}



Naast de verschillende gedetailleerde grafieken [hier](../../reporting/using/creating-a-chart.md#chart-types-and-variants)kunt u de weergave aanpassen en elementen toevoegen aan de rapportpagina(&#39;s).

U kunt containers gebruiken: hiermee kunt u verschillende elementen van een pagina koppelen en de lay-out ervan in kolommen en/of cellen configureren. Hoe deze te gebruiken is gedetailleerd in [deze sectie](../../web/using/defining-web-forms-layout.md#creating-containers).

U kunt de rapportlay-out bij de wortel van de boom vormen en het voor elke container overladen. Pagina&#39;s worden in kolommen gesorteerd. Containers worden ook in kolommen gesorteerd. Alleen de statische en grafische items worden in cellen gesorteerd.

## Definieer de opties voor elke pagina {#defining-the-options-for-each-page}

U kunt de opties op elke pagina van het rapport gebruiken.

De **[!UICONTROL General]** kunt u de titel van de pagina veranderen, evenals legendeposities vormen en tussen de rapportpagina&#39;s doorbladeren.

![](assets/s_ncs_advuser_report_wizard_022.png)

De **[!UICONTROL Title]** In dit veld kunt u het label aanpassen in de koptekst van de rapportpagina. De titel van het venster kan via **[!UICONTROL Properties]** venster van het rapport. Raadpleeg voor meer informatie hierover [Een kop- en voettekst toevoegen](#adding-a-header-and-a-footer).

De **[!UICONTROL Display settings]** Met opties kunt u de positie van het bijschrift van het besturingselement in een rapportpagina selecteren en het aantal kolommen op de pagina definiëren. Raadpleeg voor meer informatie over de paginalay-out de **Itemlay-out** deel van [deze sectie](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Selecteer de verschillende opties in het dialoogvenster **[!UICONTROL Browse]** sectie gebruiken om het bladeren van de ene rapportpagina naar een andere toe te staan. Als de **[!UICONTROL Disable next page]** of de **[!UICONTROL Disable previous page]** is geselecteerd, wordt de **[!UICONTROL Next]** en **[!UICONTROL Previous]** de knoppen verdwijnen uit de rapportpagina.

## Een kop- en voettekst toevoegen {#adding-a-header-and-a-footer}

In het venster met rapporteigenschappen kunt u ook de lay-outelementen definiëren, zoals: de titel van het venster, de HTML-inhoud van de kop- en voetteksten.

Als u het venster met eigenschappen wilt openen, klikt u op de knop **[!UICONTROL Properties]** knop van het rapport.

![](assets/reporting_properties.png)

De **[!UICONTROL Page]** kunt u de weergave aanpassen.

![](assets/s_ncs_advuser_report_properties_04.png)

De inhoud die op dit lusje wordt gevormd zal op alle rapportpagina&#39;s zichtbaar zijn.

De **[!UICONTROL Texts]** Met subtab kunt u variabele inhoud definiëren. Tijdens de vertaalcyclus wordt hiermee rekening gehouden als het rapport is ontworpen voor gebruik in verschillende talen.

Hiermee kunt u een lijst met tekstfragmenten maken en deze koppelen aan id&#39;s:

![](assets/s_ncs_advuser_report_properties_04a.png)

Dan neem deze herkenningstekens in de inhoud van HTML van het rapport op:

![](assets/s_ncs_advuser_report_properties_04b.png)

Wanneer het rapport wordt weergegeven, worden deze automatisch vervangen door de juiste inhoud.

Net als bij HTML-teksten kunt u met deze modus de teksten in het rapport centraliseren en de vertaling ervan beheren. De op dit tabblad gemaakte tekst wordt automatisch verzameld door het geïntegreerde vertaalgereedschap van Adobe Campaign.
