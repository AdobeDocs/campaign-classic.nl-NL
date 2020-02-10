---
title: Gebruik hoofdletters
seo-title: Gebruik hoofdletters
description: Gebruik hoofdletters
seo-description: null
page-status-flag: never-activated
uuid: 86762d94-2a7d-4053-980b-c699a58a021d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 691eea2c-bffc-4520-91c8-43798eece916
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# Gebruik hoofdletters{#use-cases}

## Een populatie analyseren {#analyzing-a-population}

In het volgende voorbeeld kunt u de doelgroep van een reeks nieuwsbrieven verkennen met behulp van de beschrijvende analysewizard.

De stappen van de implementatie worden hieronder beschreven, terwijl een uitvoerige lijst van opties en beschrijvingen in de andere secties van dit hoofdstuk beschikbaar is.

### Identificatie van de te analyseren populatie {#identifying-the-population-to-analyze}

In dit voorbeeld willen we de doelpopulatie van de leveringen in de map **Newsletters** verkennen.

U doet dit door de desbetreffende leveringen te selecteren, vervolgens met de rechtermuisknop te klikken en te selecteren **[!UICONTROL Action > Explore the target...]**.

![](assets/reporting_quick_start_1.png)

### Een type analyse selecteren {#selecting-a-type-of-analysis}

In de eerste stap van de medewerker, kunt u het beschrijvende analysemalplaatje selecteren aan gebruik. Standaard bevat Adobe Campaign twee sjablonen: **[!UICONTROL Qualitative distribution]** en **[!UICONTROL Quantitative distribution]**. Voor meer op dit verwijs naar het [Vormen van de kwalitatieve sectie van het distributiemalplaatje](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-qualitative-distribution-template) . De verschillende weergaven worden weergegeven in het gedeelte [Info beschrijvende analyse](../../reporting/using/about-descriptive-analysis.md) .

In dit voorbeeld selecteert u de **[!UICONTROL Qualitative distribution]** sjabloon en kiest u een weergave met een grafiek en tabel (array). Geef het rapport een naam (&quot;Omschrijvende analyse&quot;) en klik op **[!UICONTROL Next]**.

![](assets/reporting_descriptive_quickstart_step_1.png)

### Variabelen selecteren voor weergave {#selecting-the-variables-to-display}

In de volgende stap kunt u de gegevens selecteren die in de tabel moeten worden weergegeven.

Klik op de **[!UICONTROL Add...]** koppeling om de variabele te selecteren die de gegevens bevat die u wilt weergeven. Hier willen we de steden van onze ontvangers op één lijn weergeven:

![](assets/reporting_descriptive_quickstart_step_2.png)

In de kolommen wordt het aantal aankopen per bedrijf weergegeven. In dit voorbeeld worden bedragen geaggregeerd in het veld **Webaankopen** .

Hier, willen wij resultaat binden bepalen om hun vertoning te verduidelijken. Selecteer hiertoe de **[!UICONTROL Manual]** bindingsoptie en stel de berekeningsklassen voor de segmenten in die u wilt weergeven:

![](assets/reporting_descriptive_quickstart_step_2a.png)

Klik vervolgens **[!UICONTROL Ok]** om de configuratie goed te keuren.

Nadat de lijnen en kolommen zijn gedefinieerd, kunt u deze wijzigen, verplaatsen of verwijderen met de werkbalk.

![](assets/reporting_descriptive_quickstart_step_2b.png)

### De weergave-indeling definiëren {#defining-the-display-format}

In de volgende stap van de wizard kunt u het type diagram selecteren dat u wilt genereren.

Kies in dit geval het histogram.

![](assets/reporting_descriptive_quickstart_step_3.png)

Mogelijke configuraties van de verschillende grafiek worden gedetailleerd in de de opties [van het het rapportdiagram van de](../../reporting/using/processing-a-report.md#analysis-report-chart-options) Analyse.

### De te berekenen statistiek configureren {#configuring-the-statistic-to-calculate}

Geef vervolgens de berekeningen op die op de verzamelde gegevens moeten worden toegepast. Standaard worden de waarden door de wizard Omschrijvende analyse een eenvoudige telling uitgevoerd.

In dit venster kunt u de lijst met statistieken definiëren die moeten worden berekend.

![](assets/reporting_descriptive_quickstart_step_4.png)

Klik op de **[!UICONTROL Add]** knop om een nieuwe statistiek te maken. Raadpleeg voor meer informatie de berekening [Statistieken](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).

### Het bekijken van en het gebruiken van het rapport {#viewing-and-using-the-report}

De laatste stap van de tovenaar toont de lijst en de grafiek.

U kunt gegevens opslaan, exporteren of afdrukken met de werkbalk boven de tabel. Raadpleeg [Een rapport](../../reporting/using/processing-a-report.md)verwerken voor meer informatie.

![](assets/reporting_descriptive_quickstart_step_5.png)

## Kwalitatieve gegevensanalyse {#qualitative-data-analysis}

### Voorbeeld van een diagramweergave {#example-of-a-chart-display}

**Doel**: een analyseverslag opstellen over de locatie van de vooruitzichten of afnemers.

1. Open de beschrijvende wizard voor analyse en selecteer **[!UICONTROL Chart]** alleen.

   ![](assets/s_ncs_user_report_wizard_05a.png)

   Klik **[!UICONTROL Next]** om deze stap goed te keuren.

1. Vervolgens selecteert u de **[!UICONTROL 2 variables]** **[!UICONTROL First variable (abscissa)]** optie en geeft u op dat de variabele naar de status van de ontvanger (vooruitzichten/klanten) verwijst en de tweede variabele naar het land.
1. Selecteren **[!UICONTROL Cylinders]** als type.

   ![](assets/s_ncs_user_report_wizard_05.png)

1. Klik **[!UICONTROL Next]** en verlaat de standaardstatistiek **[!UICONTROL Simple count]** .
1. Klik **[!UICONTROL Next]** om het rapport weer te geven.

   ![](assets/s_ncs_user_report_wizard_04.png)

   Houd de muisaanwijzer boven een bar om het exacte aantal klanten of de vooruitzichten voor dit land te zien.

1. De weergave van een van de landen op basis van de legenda in- of uitschakelen.

   ![](assets/s_ncs_user_report_wizard_06png.png)

### Voorbeeld van een tabelweergave {#example-of-a-table-display}

**Doel**: analyse van de e-maildomeinen van het bedrijf.

1. Open de beschrijvende analysewizard en selecteer alleen de **[!UICONTROL Array]** weergavemodus.

   ![](assets/s_ncs_user_report_wizard_03a.png)

   Klik op de **[!UICONTROL Next]** knop om deze stap goed te keuren.

1. Selecteer de **[!UICONTROL Company]** variabele als een kolom en de **[!UICONTROL Email domain]** variabele als een rij.
1. Houd de **[!UICONTROL By rows]** optie voor statistische oriëntatie: de statistische berekening wordt rechts van de **[!UICONTROL Email domain]** variabele weergegeven.

   ![](assets/s_ncs_user_report_wizard_03b.png)

   Klik **[!UICONTROL Next]** om deze stap goed te keuren.

1. Voer vervolgens de te berekenen statistieken in: de standaardtelling houden en een nieuwe statistiek creëren. Om dit te doen, klik **[!UICONTROL Add]** en selecteer **[!UICONTROL Total percentage distribution]** als exploitant.

   ![](assets/s_ncs_user_report_wizard_03.png)

1. Voer een label voor de statistiek in, zodat er geen leeg veld wordt weergegeven wanneer het rapport wordt weergegeven.

   ![](assets/s_ncs_user_report_wizard_014.png)

1. Klik **[!UICONTROL Next]** om het rapport weer te geven.

   ![](assets/s_ncs_user_report_wizard_06.png)

1. Zodra het analyserapport is geproduceerd, kunt u de vertoning aanpassen om uw behoeften aan te passen zonder de configuratie te veranderen. U kunt bijvoorbeeld tussen de assen schakelen: Klik met de rechtermuisknop op de domeinnamen en selecteer **[!UICONTROL Turn]** in het snelmenu.

   ![](assets/s_ncs_user_report_wizard_07.png)

   In de tabel worden de gegevens als volgt weergegeven:

   ![](assets/s_ncs_user_report_wizard_07a.png)

## Kwantitatieve gegevensanalyse {#quantitative-data-analysis}

**Doel**: het opstellen van een kwantitatief analyseverslag over de pensioengerechtigde leeftijd

1. Open de beschrijvende analysewizard en selecteer een optie in de **[!UICONTROL Quantitative distribution]** vervolgkeuzelijst.

   ![](assets/s_ncs_user_report_wizard_011a.png)

   Klik op de **[!UICONTROL Next]** knop om deze stap goed te keuren.

1. Selecteer de **[!UICONTROL Age]** variabele en voer het label ervan in. Geef op of het een geheel getal is en klik op **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_report_wizard_011.png)

1. Verwijder de **[!UICONTROL Deciles]**, **[!UICONTROL Distribution]** en de **[!UICONTROL Sum]** statistieken: ze zijn hier niet nodig .

   ![](assets/s_ncs_user_report_wizard_012.png)

1. Klik **[!UICONTROL Next]** om het rapport weer te geven.

   ![](assets/s_ncs_user_report_wizard_013.png)

## Een overgangsdoel analyseren in een workflow {#analyzing-a-transition-target-in-a-workflow}

**Doel**: rapporten te genereren over de populatie van een doelworkflow

1. Open de gewenste doelworkflow.
1. Klik met de rechtermuisknop op een overgang die naar de tabel met ontvangers verwijst.
1. Selecteer **[!UICONTROL Analyze target]** in het keuzemenu om het beschrijvende analysevenster te openen.

   ![](assets/s_ncs_user_report_wizard_from_transision.png)

1. Op dit punt kunt u de **[!UICONTROL Existing analyses and reports]** optie selecteren en rapporten gebruiken die eerder zijn gemaakt (zie [Bestaande rapporten en analyses](../../reporting/using/processing-a-report.md#re-using-existing-reports-and-analyses)opnieuw gebruiken), of een nieuwe beschrijvende analyse maken. Laat de **[!UICONTROL New descriptive analysis from a template]** optie standaard geselecteerd om dit te doen.

   De rest van de configuratie is hetzelfde als voor alle beschrijvende analyses.

### Aanbevelingen voor doelanalyse {#target-analyze-recommendations}

De analyse van een populatie in een workflow vereist dat de populatie nog steeds aanwezig is in de overgang. Als de workflow wordt gestart, kan het resultaat met betrekking tot de bevolking uit de overgang worden verwijderd. Als u een analyse wilt uitvoeren, kunt u:

* Maak de overgang van zijn bestemmingsactiviteit los en begin het werkschema om het actief te maken. Start de wizard op de gebruikelijke manier wanneer de overgang begint te knipperen.

   ![](assets/s_ncs_user_report_wizard_018.png)

* Wijzig de eigenschappen van de workflow door de **[!UICONTROL Keep the result of interim populations between two executions]** optie te selecteren. Hiermee kunt u een analyse van de overgang van uw keuze starten, zelfs als de workflow is voltooid.

   ![](assets/s_ncs_user_report_wizard_020.png)

   Als de populatie uit de overgang is gewist, wordt u in een foutbericht gevraagd de desbetreffende optie te selecteren voordat u de wizard voor beschrijvende analyse start.

   ![](assets/s_ncs_user_report_wizard_019.png)

>[!CAUTION]
>
>De **[!UICONTROL Keep the result of interim populations between two executions]** optie mag alleen in de ontwikkelingsfase worden gebruikt, maar nooit voor een productieomgeving.\
>De tussentijdse populaties worden automatisch leeggemaakt zodra de bewaartermijn is bereikt. Deze deadline is opgegeven op het **[!UICONTROL Execution]** tabblad met workfloweigenschappen.

## Logbestanden voor bijhouden ontvangers analyseren {#analyzing-recipient-tracking-logs}

De beschrijvende analysetovenaar kan rapporten over andere het werklijsten produceren. Dit betekent dat u leveringslogboeken kunt analyseren door een specifiek rapport te creëren.

In dit voorbeeld, willen wij het reactiviteitstarief van nieuwsbrieven ontvangers analyseren.

Hiervoor voert u de volgende stappen uit:

1. Open de beschrijvende wizard voor analyse via het **[!UICONTROL Tools > Descriptive analysis]** menu en wijzig de standaardtabel voor werken. Selecteer Proefdrukken **[!UICONTROL Recipient tracking log]** en voeg een filter toe om deze uit te sluiten en nieuwsbrieven op te nemen.

   ![](assets/reporting_descriptive_sample_tracking_1.png)

   Selecteer een tabelweergave en klik op **[!UICONTROL Next]**.

1. Geef in het volgende venster op dat de analyse betrekking heeft op leveringen.

   ![](assets/reporting_descriptive_sample_tracking_2.png)

   Hier, zullen de leveringsetiketten in de eerste kolom worden getoond.

1. Schrap de standaardtelling en creeer drie statistieken om de statistieken te vormen die in de lijst moeten worden getoond.

   In de tabel ziet u voor elke nieuwsbrief het volgende: het aantal wordt geopend, het aantal klikken, het reactiviteitspercentage (als percentage).

1. Voeg een statistiek toe voor het tellen van het aantal klikken: het relevante filter op het **[!UICONTROL Filter]** tabblad definiëren.

   ![](assets/reporting_descriptive_sample_tracking_3.png)

1. Klik vervolgens op het **[!UICONTROL General]** tabblad om de naam van het label en de alias van de statistiek te wijzigen:

   ![](assets/reporting_descriptive_sample_tracking_4.png)

1. Voeg een tweede statistiek toe voor het tellen van het aantal openingen:

   ![](assets/reporting_descriptive_sample_tracking_5.png)

1. Klik vervolgens op het **[!UICONTROL General]** tabblad om de naam van het label voor statistieken en de bijbehorende alias te wijzigen:

   ![](assets/reporting_descriptive_sample_tracking_6.png)

1. Voeg de derde statistiek toe en selecteer de **[!UICONTROL Calculated field]** operator om de reactiviteitsgraad te meten.

   ![](assets/reporting_descriptive_sample_tracking_7.png)

   Ga naar het **[!UICONTROL User function]** gebied en ga de volgende formule in:

   ```
   @clic / @open * 100
   ```

   Pas het statistische label aan zoals hieronder aangegeven:

   ![](assets/reporting_descriptive_sample_tracking_8.png)

   Geef ten slotte op of de waarden als een percentage worden weergegeven: Als u dit wilt doen, schakelt u de **[!UICONTROL Default formatting]** optie op het **[!UICONTROL Advanced]** tabblad uit en selecteert u **[!UICONTROL Percentage]** zonder decimaalteken.

   ![](assets/reporting_descriptive_sample_tracking_10.png)

1. Klik **[!UICONTROL Next]** om het rapport weer te geven.

   ![](assets/reporting_descriptive_sample_tracking_9.png)

## Logboeken voor leveringsuitsluitingen analyseren {#analyzing-delivery-exclusion-logs}

Als de analyse betrekking heeft op een levering, kunt u de uitgesloten populatie analyseren. Hiervoor selecteert u de te analyseren items en klikt u met de rechtermuisknop om het **[!UICONTROL Action > Explore exclusions]** menu te openen.

![](assets/reporting_descriptive_exclusion_menu.png)

Dit zal u aan de beschrijvende analysetovenaar nemen en de analyse zal de ontvankelijke uitsluitingslogboeken betreffen.

U kunt bijvoorbeeld de domeinen van alle uitgesloten adressen weergeven en deze sorteren op uitsluitingsdatum.

![](assets/reporting_descriptive_exclusion_sample.png)

Dit zou het volgende type van rapport produceren:

![](assets/reporting_descriptive_exclusion_result.png)

