---
product: campaign
title: De context in uw rapporten gebruiken
description: Meer informatie over het gebruik van de context in uw rapporten
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Reporting, Monitoring
exl-id: a19e2843-d3f9-48c3-af72-cc1bc54f6360
source-git-commit: 354fc8fd5d030ed88e2b279ba1dd3eaf2f314d53
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# De context in uw rapporten gebruiken{#using-the-context}



Wanneer u gegevens in de vorm van **[!UICONTROL tables]** of **[!UICONTROL charts]** wilt vertegenwoordigen, kan het uit twee bronnen worden genomen: een nieuwe vraag (verwijs naar [ een directe filter op gegevens ](#defining-a-direct-filter-on-data)) of de rapportcontext (verwijs naar [ de contextgegevens van het Gebruik ](#using-context-data)) bepalen.

## Een rechtstreeks filter op gegevens definiëren {#defining-a-direct-filter-on-data}

### Gegevens filteren {#filtering-data}

Het gebruik van een **[!UICONTROL Query]** type-activiteit is niet verplicht bij het maken van een rapport. De gegevens kunnen direct in de lijsten en grafieken worden gefiltreerd die omhoog het rapport maken.

Hierdoor kunt u de gegevens selecteren die in het rapport rechtstreeks via de **[!UICONTROL Page]** -activiteit van het rapport moeten worden weergegeven.

Klik hiertoe op de koppeling **[!UICONTROL Filter data...]** op het tabblad **[!UICONTROL Data]** : met deze koppeling hebt u toegang tot de editor voor expressies om een query op de te analyseren gegevens te definiëren.

![](assets/reporting_filter_data_from_page.png)

### Voorbeeld: gebruik een filter in een diagram {#example--use-a-filter-in-a-chart}

In het volgende voorbeeld willen we dat in het diagram alleen de ontvangende profielen worden weergegeven die in Frankrijk wonen en die in het jaar een aankoop hebben gedaan.

Als u dit filter wilt definiëren, plaatst u een pagina in het diagram en bewerkt u deze. Klik op de koppeling **[!UICONTROL Filter data]** en maak het filter dat overeenkomt met de gegevens die u wilt weergeven. Voor meer bij het bouwen van vragen in Adobe Campaign, verwijs naar [ deze sectie ](../../platform/using/adobe-campaign-workspace.md#about-queries-in-campaign).

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
1. Ga naar het tabblad **[!UICONTROL Data]** en selecteer de kubus die u wilt gebruiken.
1. Klik op de koppeling **[!UICONTROL Filter data...]** en definieer de volgende query om Adobe uit de lijst met bedrijven te verwijderen.

   ![](assets/s_ncs_advuser_report_display_03.png)

Slechts zullen de ontvangers die de het filtreren criteria voldoen in het rapport verschijnen.

![](assets/s_ncs_advuser_report_display_04.png)

## Contextgegevens gebruiken {#using-context-data}

Om gegevens in de vorm van a **[!UICONTROL table]** of a **[!UICONTROL chart]** te vertegenwoordigen, kunnen de gegevens uit de rapportcontext komen.

Op de pagina die de tabel of het diagram bevat, kunt u met het tabblad **[!UICONTROL Data]** de gegevensbron selecteren.

![](assets/s_ncs_advuser_report_datasource_3.png)

* Met de optie **[!UICONTROL New query]** kunt u een query voor het verzamelen van gegevens maken. Voor meer op dit, verwijs naar [ bepaal een directe filter op gegevens ](#defining-a-direct-filter-on-data).
* Met de optie **[!UICONTROL Context data]** kunt u de invoergegevens gebruiken: de context van het rapport valt samen met de informatie in de binnenkomende overgang van de pagina die de tabel of tabel bevat. Deze context kan bijvoorbeeld gegevens bevatten die zijn verzameld via een **[!UICONTROL Query]** -activiteit die vóór de **[!UICONTROL Page]** -activiteit is geplaatst en waarvoor u de tabel en de velden wilt opgeven waarop het rapport betrekking heeft.

Bijvoorbeeld, in een vraagvakje, bouw de volgende vraag voor de ontvangers:

![](assets/s_ncs_advuser_report_datasource_2.png)

Geef vervolgens de bron van de gegevens in het rapport op, in dit geval: **[!UICONTROL Data from the context]** .

De gegevenslocatie wordt automatisch afgeleid. Indien nodig kunt u het gegevenspad forceren.

![](assets/s_ncs_advuser_report_datasource_4.png)

Wanneer u de gegevens selecteert waarop de statistieken betrekking hebben, komen de beschikbare velden overeen met de gegevens die in de query zijn opgegeven.

![](assets/s_ncs_advuser_report_datasource_1.png)
