---
solution: Campaign Classic
product: campaign
title: Indeling van element
description: Indeling van element
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 1%

---


# Indeling van element{#element-layout}

Naast de verschillende hier beschreven grafieken: [Grafiektypen en -varianten](../../reporting/using/creating-a-chart.md#chart-types-and-variants), kunt u de weergave aanpassen en elementen toevoegen aan de rapportpagina(&#39;s).

U kunt containers gebruiken: Hiermee kunt u verschillende elementen van een pagina aan elkaar koppelen en de lay-out ervan in kolommen en/of cellen configureren. Hoe deze te gebruiken is gedetailleerd in [deze sectie](../../web/using/defining-web-forms-layout.md#creating-containers).

U kunt de rapportlay-out bij de wortel van de boom vormen en het voor elke container overladen. Pagina&#39;s worden in kolommen gesorteerd. Containers worden ook in kolommen gesorteerd. Alleen de statische en grafische items worden in cellen gesorteerd.

## Opties definiëren voor elke pagina {#defining-the-options-for-each-page}

U kunt de opties op elke pagina van het rapport gebruiken.

Met het tabblad **[!UICONTROL General]** kunt u de titel van de pagina wijzigen en legendeposities configureren en bladeren tussen de rapportpagina&#39;s.

![](assets/s_ncs_advuser_report_wizard_022.png)

Met het veld **[!UICONTROL Title]** kunt u het label in de koptekst van de rapportpagina aanpassen. De titel van het venster kan via het **[!UICONTROL Properties]** venster van het rapport worden gevormd. Raadpleeg [Koptekst en voettekst toevoegen](#adding-a-header-and-a-footer) voor meer informatie.

Met de opties **[!UICONTROL Display settings]** kunt u de positie van het bijschrift van het besturingselement binnen een rapportpagina selecteren en het aantal kolommen op de pagina definiëren. Raadpleeg de sectie **Itemlayout** van [deze sectie](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page) voor meer informatie over paginalay-out.

Selecteer de verschillende opties in de **[!UICONTROL Browse]** sectie om het doorbladeren van één rapportpagina aan een andere toe te staan. Als de optie **[!UICONTROL Disable next page]** of **[!UICONTROL Disable previous page]** is geselecteerd, verdwijnen de knoppen **[!UICONTROL Next]** en **[!UICONTROL Previous]** uit de rapportpagina.

## Een kop- en voettekst {#adding-a-header-and-a-footer} toevoegen

In het venster met rapporteigenschappen kunt u ook de lay-outelementen definiëren, zoals: de titel van het venster, de HTML-inhoud van de kop- en voetteksten.

Klik op de knop **[!UICONTROL Properties]** van het rapport om het eigenschappenvenster te openen.

![](assets/reporting_properties.png)

Met de tab **[!UICONTROL Page]** kunt u de weergave aanpassen.

![](assets/s_ncs_advuser_report_properties_04.png)

De inhoud die op dit lusje wordt gevormd zal op alle rapportpagina&#39;s zichtbaar zijn.

Met het subtabblad **[!UICONTROL Texts]** kunt u variabele inhoud definiëren: tijdens de vertaalcyclus zal hiermee rekening worden gehouden indien het verslag is opgesteld voor gebruik in verschillende talen .

Hiermee kunt u een lijst met tekstfragmenten maken en deze koppelen aan id&#39;s:

![](assets/s_ncs_advuser_report_properties_04a.png)

Dan neem deze herkenningstekens in de inhoud van HTML van het rapport op:

![](assets/s_ncs_advuser_report_properties_04b.png)

Wanneer het rapport wordt weergegeven, worden deze automatisch vervangen door de juiste inhoud.

Net als bij HTML-teksten kunt u met deze modus de teksten in het rapport centraliseren en de vertaling ervan beheren. De op dit tabblad gemaakte tekst wordt automatisch verzameld door het geïntegreerde vertaalgereedschap van Adobe Campaign.
