---
title: Een nieuw rapport maken
seo-title: Een nieuw rapport maken
description: Een nieuw rapport maken
seo-description: null
page-status-flag: never-activated
uuid: dcea5c28-da09-4a31-a13c-c8995c6faa63
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 22c92ddf-fbea-49d3-afd4-1ba427be399d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Een nieuw rapport maken{#creating-a-new-report}

Voer de volgende stappen uit om een rapport te maken:

1. Open Adobe Campagne Explorer en selecteer de **[!UICONTROL Administration > Configuration]** map in het **[!UICONTROL Reports]** knooppunt.
1. Klik op de **[!UICONTROL New]** knop boven de lijst met rapporten.
1. Selecteer **[!UICONTROL Create a new report from a template]** en klik op **[!UICONTROL Next]**.

   ![](assets/s_ncs_advuser_report_wizard_new_01.png)

1. Selecteer het rapportmalplaatje in de drop-down lijst.

   * Met **[!UICONTROL Extended report]** deze optie kunt u een rapport maken dat is geconfigureerd met een grafiek.
   * Met het **[!UICONTROL Qualitative distribution]** rapport kunt u statistieken maken op basis van alle typen gegevens (bedrijfsnaam, e-maildomein, enzovoort).
   * Met het **[!UICONTROL Quantitative distribution]** rapport kunt u statistieken maken over gegevens die kunnen worden gemeten of geteld (factuurbedrag, leeftijd van de ontvanger, enz.).
   Voor meer informatie over deze rapportmalplaatjes, verwijs naar [deze sectie](../../reporting/using/about-descriptive-analysis.md).

1. Voer de rapportnaam en de beschrijving ervan in de desbetreffende velden in. Geef aan **[!UICONTROL schema]** op welke manier het rapport wordt toegepast.

   ![](assets/s_ncs_advuser_report_wizard_020.png)

1. Sla dit rapport op.

## Het diagram modelleren {#modelizing-the-chart}

Nadat u uw rapport hebt opgeslagen, moet dit worden weergegeven. U kunt nu het diagram van uw rapport maken.

![](assets/s_ncs_user_report_wizard_021.png)

Het overzicht voor de opstelling van het verslag bestaat uit een opeenvolging van activiteiten.

![](assets/s_ncs_advuser_report_wizard_031.png)

Activiteiten worden gekoppeld met behulp van overgangen, weergegeven door pijlen.

![](assets/s_ncs_advuser_report_wizard_032.png)

Om een rapport te bouwen, afhankelijk van zijn aard en context, moet u de nuttige elementen identificeren en hun logische opeenvolging verwissen.

1. Gebruik de activiteit van het &quot;Begin&quot;om het eerste proces tot stand te brengen dat moet worden uitgevoerd om het rapport te bouwen. U kunt slechts één van deze activiteiten per rapport gebruiken.

   Het is verplicht als het diagram een lus bevat.

1. Voeg één of meerdere &quot;Vraag&quot;activiteiten toe om gegevens te verzamelen die voor de bouw van het rapport nuttig zijn. Gegevens kunnen rechtstreeks worden verzameld via een query op een schema van de database, of via een geïmporteerde lijst of een bestaande kubus.

   Zie Gegevens [verzamelen voor analyse](../../reporting/using/collecting-data-to-analyze.md)voor meer informatie.

   Deze gegevens zullen (of niet) in het rapport afhankelijk van paginaconfiguratie worden getoond.

1. Plaats een of meer &#39;Pagina&#39;-activiteiten om de grafische weergave van de verzamelde gegevens te definiëren. U kunt tabellen, grafieken, invoervelden invoegen en de weergave van een of meer pagina&#39;s of elementen van de pagina bepalen. De weergegeven inhoud kan volledig worden geconfigureerd.

   Zie [Statische elementen](#static-elements)voor meer informatie.

1. Gebruik een &#39;Test&#39;-activiteit om de voorwaarden te definiëren voor het weergeven of openen van gegevens.

   Raadpleeg de weergave [van de pagina](../../reporting/using/defining-a-conditional-content.md#conditioning-page-display)Conditioning voor meer informatie.

1. Voeg, indien nodig, gepersonaliseerde scripts toe via de activiteit &#39;Script&#39;, bijvoorbeeld om de naam van een rapport te berekenen, om de weergave van het resultaat binnen een specifieke context te filteren, enz.

   Raadpleeg [Scriptactiviteit](../../reporting/using/advanced-functionalities.md#script-activity)voor meer informatie hierover.

1. Tot slot kunt u voor het gemakkelijker lezen van complexe rapporten één of meerdere &quot;sprong&quot;type activiteiten opnemen. Dit laat u van één activiteit aan een andere gaan zonder de overgang op het rapport te concretiseren. U kunt de functie Springen ook gebruiken om een ander rapport weer te geven.

   Zie [Snelactiviteit](../../reporting/using/advanced-functionalities.md#jump-activity)voor meer informatie hierover.

U kunt niet meerdere vertakkingen tegelijk uitvoeren. Dit betekent dat een dergelijk rapport niet werkt:

![](assets/reporting_graph_sample_ko.png)

U kunt echter verschillende vertakkingen plaatsen. Slechts één van hen zal worden uitgevoerd:

![](assets/reporting_graph_sample_ok.png)

## Een pagina maken {#creating-a-page}

De inhoud wordt gevormd via de activiteiten die in de grafiek worden geplaatst. Voor meer op dit, verwijs naar het [Modelleren van de grafiek](#modelizing-the-chart).

Om een activiteit te vormen, klik zijn pictogram tweemaal.

De weergegeven inhoud wordt gedefinieerd bij activiteiten van het type **Pagina** .

Een rapport kan een of meer pagina&#39;s bevatten. Pagina&#39;s worden gemaakt via een speciale editor waarmee u in een boomstructuur invoervelden, selectievelden, statische elementen, grafieken of tabellen kunt invoegen. Met behulp van containers kunt u de lay-out definiëren. Raadpleeg de lay-out [Element voor meer informatie hierover](../../reporting/using/element-layout.md).

Als u een component aan de pagina wilt toevoegen, gebruikt u de pictogrammen in de linkerbovensectie van de werkbalk.

![](assets/reporting_add_component_in_page.png)

U kunt ook met de rechtermuisknop op het knooppunt klikken waar u de component wilt toevoegen en dit selecteren in de lijst.

![](assets/s_ncs_advuser_report_wizard_09.png)

>[!CAUTION]
>
>Als het rapport bestemd is om in het formaat van Excel worden uitgevoerd, adviseren wij niet het gebruiken van complexe het formatteren van HTML. Voor meer op dit, verwijs naar het [Uitvoeren van een rapport](../../reporting/using/actions-on-reports.md#exporting-a-report).

Een **[!UICONTROL Page]** subformulier kan de volgende elementen bevatten:

* Staaf, taart, curvetype **[!UICONTROL charts]** enz.
* roteren; Lijst met groep of Onderverdeling **[!UICONTROL tables]**.
* Tekst- of getaltype **[!UICONTROL Input controls]**.
* Vervolgkeuzelijst, selectievakje, keuzerondje, meerkeuzevype, datum of type matrix **[!UICONTROL Selection controls]**.
* Koppelingseditor, Constante map, Type mapselectie **[!UICONTROL Advanced controls]**.
* Waarde, Koppeling, HTML, Afbeelding, enzovoort. **[!UICONTROL Static elements]**.
* **[!UICONTROL Containers]** waarmee u de indeling van componenten kunt bepalen.

De configuratiewijze van een pagina en zijn componenten is gedetailleerd in [deze sectie](../../web/using/about-web-forms.md).

Met de werkbalk kunt u besturingselementen toevoegen of verwijderen en de volgorde ervan in de rapportpagina(&#39;s) ordenen.

![](assets/s_ncs_advuser_report_wizard_08.png)

### Statische elementen {#static-elements}

De statische elementen laten u toe om informatie in het rapport, zoals grafische elementen of manuscripten te tonen, die de gebruiker niet met zal in wisselwerking staan. Zie [deze sectie](../../web/using/static-elements-in-a-web-form.md#inserting-html-content) voor meer informatie.

![](assets/s_advuser_report_page_activity_03.png)

### Gegevens in een rapport filteren {#filtering-information-in-a-report}

Met de besturingselementen voor invoer en selectie kunt u de informatie filteren die in het rapport wordt weergegeven. Voor meer bij het uitvoeren van dit type van het filtreren, verwijs naar het [Filtreren opties in de vragen](../../reporting/using/collecting-data-to-analyze.md#filtering-options-in-the-queries).

Raadpleeg [deze sectie](../../web/using/about-web-forms.md)voor meer informatie over het maken en configureren van invoervelden en selectievelden.

U kunt één of meerdere inputcontroles in uw rapporten integreren. Met dit type besturingselement kunt u informatie filteren die wordt weergegeven op basis van een ingevoerde waarde.

![](assets/reporting_control_text.png)

U kunt ook een of meer selectiemiddelen in uw rapporten integreren. Met dit type besturingselement kunt u de informatie in het rapport filteren op basis van de geselecteerde waarde(n), zoals:

* via keuzerondjes of selectievakjes:

   ![](assets/reporting_radio_buttons.png)

* via een vervolgkeuzelijst:

   ![](assets/reporting_control_list.png)

* via een kalender:

   ![](assets/reporting_control_date.png)

Tot slot kunt u één of meer geavanceerde controles in uw rapporten integreren. Met dit type besturingselement kunt u een koppeling, constante of een map invoegen.

Hier kunt u de gegevens in het rapport filtreren om slechts de informatie te tonen bevat in één van de omslagen van de boom:

![](assets/reporting_control_folder.png)

