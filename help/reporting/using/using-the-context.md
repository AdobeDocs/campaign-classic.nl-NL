---
product: campaign
title: De context gebruiken
description: De context gebruiken
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: a19e2843-d3f9-48c3-af72-cc1bc54f6360
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 2%

---

# De context gebruiken{#using-the-context}

![](../../assets/common.svg)

Wanneer u gegevens in de vorm van **[!UICONTROL tables]** of **[!UICONTROL charts]** wilt vertegenwoordigen, kan het uit twee bronnen worden genomen: een nieuwe query (zie [Een direct filter definiëren op gegevens](#defining-a-direct-filter-on-data)) of de rapportcontext (zie [Contextgegevens gebruiken](#using-context-data)).

## Een rechtstreeks filter op gegevens definiëren {#defining-a-direct-filter-on-data}

### Gegevens filteren {#filtering-data}

Het gebruiken van **[!UICONTROL Query]** typeactiviteit is niet verplicht wanneer het bouwen van een rapport. De gegevens kunnen direct in de lijsten en grafieken worden gefiltreerd die omhoog het rapport maken.

Dit laat u toe om de gegevens aan vertoning in het rapport direct via de **[!UICONTROL Page]** activiteit van het rapport te selecteren.

Klik hiertoe op de koppeling **[!UICONTROL Filter data...]** op het tabblad **[!UICONTROL Data]**: met deze koppeling hebt u toegang tot de expressies-editor om een query te definiëren voor de gegevens die moeten worden geanalyseerd.

![](assets/reporting_filter_data_from_page.png)

### Voorbeeld: gebruik een filter in een grafiek {#example--use-a-filter-in-a-chart}

In het volgende voorbeeld willen we dat in het diagram alleen de ontvangende profielen worden weergegeven die in Frankrijk wonen en die in het jaar een aankoop hebben gedaan.

Als u dit filter wilt definiëren, plaatst u een pagina in het diagram en bewerkt u deze. Klik op de koppeling **[!UICONTROL Filter data]** en maak het filter dat overeenkomt met de gegevens die u wilt weergeven. Raadpleeg [deze sectie](../../platform/using/about-queries-in-campaign.md) voor meer informatie over het samenstellen van query&#39;s in Adobe Campaign.

![](assets/s_ncs_advuser_report_wizard_029.png)

Hier, willen wij de verdeling door stad van geselecteerde ontvangers tonen.

![](assets/reporting_graph_with_2vars.png)

De rendering ziet er als volgt uit:

![](assets/reporting_graph_with_2vars_preview.png)

### Voorbeeld: een filter in een draaientabel gebruiken {#example--use-a-filter-in-a-pivot-table}

In dit voorbeeld kunt u met het filter alleen niet-Parisiaanse klanten in de draaitabel weergeven, zonder dat u daarvoor een andere query hoeft te gebruiken.

Voer de volgende stappen uit:

1. Plaats een pagina in het diagram en bewerk deze.
1. Maak een draaitabel.
1. Ga naar het tabblad **[!UICONTROL Data]** en selecteer de kubus die u wilt gebruiken.
1. Klik op de koppeling **[!UICONTROL Filter data...]** en definieer de volgende query om Adobe uit de lijst met bedrijven te verwijderen.

   ![](assets/s_ncs_advuser_report_display_03.png)

Slechts zullen de ontvangers die de het filtreren criteria voldoen in het rapport verschijnen.

![](assets/s_ncs_advuser_report_display_04.png)

## Contextgegevens gebruiken {#using-context-data}

Om gegevens in de vorm van **[!UICONTROL table]** of **[!UICONTROL chart]** te vertegenwoordigen, kunnen de gegevens uit de rapportcontext komen.

Op de pagina die de tabel of het diagram bevat, kunt u met het tabblad **[!UICONTROL Data]** de gegevensbron selecteren.

![](assets/s_ncs_advuser_report_datasource_3.png)

* Met de optie **[!UICONTROL New query]** kunt u een query maken om gegevens te verzamelen. Raadpleeg [Een rechtstreeks filter op gegevens definiëren](#defining-a-direct-filter-on-data) voor meer informatie.
* Met de optie **[!UICONTROL Context data]** kunt u de invoergegevens gebruiken: de context van het rapport valt samen met de informatie in de binnenkomende overgang van de pagina die de grafiek of de tabel bevat. Deze context kan, bijvoorbeeld, gegevens bevatten die via een **[!UICONTROL Query]** activiteit worden verzameld die vóór **[!UICONTROL Page]** activiteit wordt geplaatst en waarvoor u de lijst en de gebieden moet specificeren die het rapport betrekking heeft.

Bijvoorbeeld, in een vraagvakje, bouw de volgende vraag voor de ontvangers:

![](assets/s_ncs_advuser_report_datasource_2.png)

Geef vervolgens de bron van de gegevens in uw rapport op, in dit geval: **[!UICONTROL Data from the context]**.

De gegevenslocatie wordt automatisch afgeleid. Indien nodig kunt u het gegevenspad forceren.

![](assets/s_ncs_advuser_report_datasource_4.png)

Wanneer u de gegevens selecteert waarop de statistieken betrekking hebben, komen de beschikbare velden overeen met de gegevens die in de query zijn opgegeven.

![](assets/s_ncs_advuser_report_datasource_1.png)
