---
product: campaign
title: De context in uw rapporten gebruiken
description: Meer informatie over het gebruik van de context in uw rapporten
badge-v7: label="v7" type="Informative" tooltip="Van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Reporting, Monitoring
exl-id: a19e2843-d3f9-48c3-af72-cc1bc54f6360
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# De context in uw rapporten gebruiken{#using-the-context}



Wanneer u gegevens wilt weergeven in de vorm van **[!UICONTROL tables]** of **[!UICONTROL charts]**, kan het uit twee bronnen worden gehaald: een nieuwe vraag (verwijs naar [Een rechtstreeks filter op gegevens definiëren](#defining-a-direct-filter-on-data)) of de context van het rapport (zie [Contextgegevens gebruiken](#using-context-data)).

## Een rechtstreeks filter op gegevens definiëren {#defining-a-direct-filter-on-data}

### Gegevens filteren {#filtering-data}

Een **[!UICONTROL Query]** type activiteit is niet verplicht wanneer het bouwen van een rapport. De gegevens kunnen direct in de lijsten en grafieken worden gefiltreerd die omhoog het rapport maken.

Dit laat u toe om de gegevens te selecteren in het rapport direct via te tonen **[!UICONTROL Page]** activiteit van het verslag.

Om dit te doen, klik **[!UICONTROL Filter data...]** in de **[!UICONTROL Data]** tab: met deze koppeling hebt u toegang tot de expressies-editor om een query te definiëren voor de gegevens die moeten worden geanalyseerd.

![](assets/reporting_filter_data_from_page.png)

### Voorbeeld: gebruik een filter in een diagram {#example--use-a-filter-in-a-chart}

In het volgende voorbeeld willen we dat in het diagram alleen de ontvangende profielen worden weergegeven die in Frankrijk wonen en die in het jaar een aankoop hebben gedaan.

Als u dit filter wilt definiëren, plaatst u een pagina in het diagram en bewerkt u deze. Klik op de knop **[!UICONTROL Filter data]** Maak een koppeling en maak het filter dat overeenkomt met de gegevens die u wilt weergeven. Raadpleeg voor meer informatie over het samenstellen van query&#39;s in Adobe Campaign [deze sectie](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

Hier, willen wij de verdeling door stad van geselecteerde ontvangers tonen.

![](assets/reporting_graph_with_2vars.png)

De rendering ziet er als volgt uit:

![](assets/reporting_graph_with_2vars_preview.png)

### Voorbeeld: een filter gebruiken in een draaientabel {#example--use-a-filter-in-a-pivot-table}

In dit voorbeeld kunt u met het filter alleen niet-Parisiaanse klanten in de draaitabel weergeven, zonder dat u daarvoor een andere query hoeft te gebruiken.

Voer de volgende stappen uit:

1. Plaats een pagina in het diagram en bewerk deze.
1. Maak een draaitabel.
1. Ga naar de **[!UICONTROL Data]** en selecteert u de kubus die u wilt gebruiken.
1. Klik op de knop **[!UICONTROL Filter data...]** koppeling en definieer de volgende query om Adobe uit de lijst met bedrijven te verwijderen.

   ![](assets/s_ncs_advuser_report_display_03.png)

Slechts zullen de ontvangers die de het filtreren criteria voldoen in het rapport verschijnen.

![](assets/s_ncs_advuser_report_display_04.png)

## Contextgegevens gebruiken {#using-context-data}

Gegevens weergeven in de vorm van een **[!UICONTROL table]** of **[!UICONTROL chart]** De gegevens kunnen afkomstig zijn uit de rapportcontext.

Op de pagina die de tabel of het diagram bevat, worden de **[!UICONTROL Data]** kunt u de gegevensbron selecteren.

![](assets/s_ncs_advuser_report_datasource_3.png)

* De **[!UICONTROL New query]** kunt u een query samenstellen voor het verzamelen van gegevens. Raadpleeg voor meer informatie hierover [Een rechtstreeks filter op gegevens definiëren](#defining-a-direct-filter-on-data).
* De **[!UICONTROL Context data]** kunt u de invoergegevens gebruiken: de context van het rapport valt samen met de informatie in de binnenkomende overgang van de pagina die de grafiek of de tabel bevat. Deze context kan bijvoorbeeld gegevens bevatten die via een **[!UICONTROL Query]** activiteit die vóór de **[!UICONTROL Page]** activiteit en waarvoor u de lijst en de gebieden moet specificeren die het rapport betrekking heeft.

Bijvoorbeeld, in een vraagvakje, bouw de volgende vraag voor de ontvangers:

![](assets/s_ncs_advuser_report_datasource_2.png)

Geef vervolgens de bron van de gegevens in uw rapport op, in dit geval: **[!UICONTROL Data from the context]**.

De gegevenslocatie wordt automatisch afgeleid. Indien nodig kunt u het gegevenspad forceren.

![](assets/s_ncs_advuser_report_datasource_4.png)

Wanneer u de gegevens selecteert waarop de statistieken betrekking hebben, komen de beschikbare velden overeen met de gegevens die in de query zijn opgegeven.

![](assets/s_ncs_advuser_report_datasource_1.png)
