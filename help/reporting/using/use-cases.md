---
product: campaign
title: Gebruiksscenario's voor rapportage van analyses
description: Gebruiksscenario's voor rapportage van analyses
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Reporting, Monitoring
exl-id: e326e32e-7bb0-46ff-9ba5-94ccd1169af2
source-git-commit: 5e062f9dbdf6c148e442ac10dbb12cf72ba0179b
workflow-type: tm+mt
source-wordcount: '1331'
ht-degree: 0%

---

# Gebruiksscenario&#39;s voor rapportage van analyses {#use-cases}

## Een populatie analyseren {#analyzing-a-population}

In het volgende voorbeeld kunt u de doelgroep van een reeks nieuwsbrieven verkennen met behulp van de beschrijvende analyseassistent.

De stappen van de implementatie worden hieronder beschreven, terwijl een uitvoerige lijst van opties en beschrijvingen in de andere secties van dit hoofdstuk beschikbaar is.

### Identificatie van de te analyseren populatie {#identifying-the-population-to-analyze}

In dit voorbeeld, willen wij de doelbevolking van de leveringen onderzoeken inbegrepen in de **omslag van Nieuwsbrieven**.

U doet dit door de desbetreffende leveringen te selecteren, vervolgens met de rechtermuisknop te klikken en **[!UICONTROL Action > Explore the target...]** te selecteren.

![](assets/reporting_quick_start_1.png)

### Een type analyse selecteren {#selecting-a-type-of-analysis}

In de eerste stap van de medewerker, kunt u het beschrijvende analysemalplaatje selecteren aan gebruik. Adobe Campaign biedt standaard twee sjablonen: **[!UICONTROL Qualitative distribution]** en **[!UICONTROL Quantitative distribution]** . Voor meer op dit verwijs naar [ het Vormen van de kwalitatieve verdelingsmalplaatje ](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-qualitative-distribution-template) sectie. De diverse teruggaven worden voorgesteld in [ Ongeveer beschrijvende analyse ](../../reporting/using/about-descriptive-analysis.md) sectie.

In dit voorbeeld selecteert u de sjabloon **[!UICONTROL Qualitative distribution]** en kiest u een weergave met een diagram en een tabel (array). Geef het rapport een naam (&quot;Beschrijvende analyse&quot;) en klik op **[!UICONTROL Next]** .

![](assets/reporting_descriptive_quickstart_step_1.png)

### Variabelen selecteren voor weergave {#selecting-the-variables-to-display}

In de volgende stap kunt u de gegevens selecteren die in de tabel moeten worden weergegeven.

Klik op de koppeling **[!UICONTROL Add...]** om de variabele te selecteren die de gegevens bevat die u wilt weergeven. Hier willen we de steden van onze ontvangers op één lijn weergeven:

![](assets/reporting_descriptive_quickstart_step_2.png)

In de kolommen wordt het aantal aankopen per bedrijf weergegeven. In dit voorbeeld, worden de bedragen samengevoegd op het **Aankopen van het Web** gebied.

Hier, willen wij resultaat binden bepalen om hun vertoning te verduidelijken. Selecteer hiertoe de bindingsoptie **[!UICONTROL Manual]** en stel de berekeningsklassen voor de segmenten in die u wilt weergeven:

![](assets/reporting_descriptive_quickstart_step_2a.png)

Klik vervolgens op **[!UICONTROL Ok]** om de configuratie goed te keuren.

Nadat de lijnen en kolommen zijn gedefinieerd, kunt u deze wijzigen, verplaatsen of verwijderen met de werkbalk.

![](assets/reporting_descriptive_quickstart_step_2b.png)

### De weergave-indeling definiëren {#defining-the-display-format}

De volgende stap van de medewerker laat u het type van grafiek selecteren u wilt produceren.

Kies in dit geval het histogram.

![](assets/reporting_descriptive_quickstart_step_3.png)

De mogelijke configuraties van de verschillende grafiek worden gedetailleerd in de [ sectie van de het rapportkaart van de Analyse opties ](../../reporting/using/processing-a-report.md#analysis-report-chart-options).

### De te berekenen statistiek configureren {#configuring-the-statistic-to-calculate}

Geef vervolgens de berekeningen op die op de verzamelde gegevens moeten worden toegepast. Door gebrek, voert de beschrijvende analysemedewerker een eenvoudige telling van de waarden uit.

In dit venster kunt u de lijst met te berekenen statistieken definiëren.

![](assets/reporting_descriptive_quickstart_step_4.png)

Klik op de knop **[!UICONTROL Add]** om een nieuwe statistiek te maken. Voor meer op dit, verwijs naar [ berekening van Statistieken ](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).

### Het bekijken van en het gebruiken van het rapport {#viewing-and-using-the-report}

De laatste stap van de medewerker toont de lijst en de grafiek.

U kunt gegevens opslaan, exporteren of afdrukken met de werkbalk boven de tabel. Voor meer op dit, verwijs naar [ Verwerking een rapport ](../../reporting/using/processing-a-report.md).

![](assets/reporting_descriptive_quickstart_step_5.png)

## Kwalitatieve gegevensanalyse {#qualitative-data-analysis}

### Voorbeeld van een diagramweergave {#example-of-a-chart-display}

**Doel**: produceer een analyserapport over de plaats van vooruitzichten of klanten.

1. Open de beschrijvende analyseassistent en selecteer **[!UICONTROL Chart]** only.

   ![](assets/s_ncs_user_report_wizard_05a.png)

   Klik op **[!UICONTROL Next]** om deze stap goed te keuren.

1. Selecteer vervolgens de optie **[!UICONTROL 2 variables]** en geef op dat **[!UICONTROL First variable (abscissa)]** naar de status van de ontvanger (perspectief/klanten) verwijst en dat de tweede variabele naar het land verwijst.
1. Selecteer **[!UICONTROL Cylinders]** als een type.

   ![](assets/s_ncs_user_report_wizard_05.png)

1. Klik op **[!UICONTROL Next]** en laat de standaardstatistiek **[!UICONTROL Simple count]** ongewijzigd.
1. Klik **[!UICONTROL Next]** om het rapport te tonen.

   ![](assets/s_ncs_user_report_wizard_04.png)

   Houd de muisaanwijzer boven een bar om het exacte aantal klanten of de vooruitzichten voor dit land te zien.

1. De weergave van een van de landen op basis van de legenda in- of uitschakelen.

   ![](assets/s_ncs_user_report_wizard_06png.png)

### Voorbeeld van een tabelweergave {#example-of-a-table-display}

**Doel**: analyseer bedrijf e-maildomeinen.

1. Open de beschrijvende analyseassistent en selecteer alleen de weergavemodus **[!UICONTROL Array]** .

   ![](assets/s_ncs_user_report_wizard_03a.png)

   Klik op **[!UICONTROL Next]** om deze stap goed te keuren.

1. Selecteer de variabele **[!UICONTROL Company]** als een kolom en de variabele **[!UICONTROL Email domain]** als een rij.
1. Houd de optie **[!UICONTROL By rows]** voor statistische oriëntatie: de statistische berekening wordt rechts van de variabele **[!UICONTROL Email domain]** weergegeven.

   ![](assets/s_ncs_user_report_wizard_03b.png)

   Klik op **[!UICONTROL Next]** om deze stap goed te keuren.

1. Dan ga de te berekenen statistieken in: houd het standaardaantal en creeer een nieuwe statistiek. Klik hiertoe op **[!UICONTROL Add]** en selecteer **[!UICONTROL Total percentage distribution]** als de operator.

   ![](assets/s_ncs_user_report_wizard_03.png)

1. Voer een label voor de statistiek in, zodat er geen leeg veld wordt weergegeven wanneer het rapport wordt weergegeven.

   ![](assets/s_ncs_user_report_wizard_014.png)

1. Klik **[!UICONTROL Next]** om het rapport te tonen.

   ![](assets/s_ncs_user_report_wizard_06.png)

1. Zodra het analyserapport is geproduceerd, kunt u de vertoning aanpassen om uw behoeften aan te passen zonder de configuratie te veranderen. U kunt bijvoorbeeld tussen de assen schakelen: klik met de rechtermuisknop op de domeinnamen en selecteer **[!UICONTROL Turn]** in het snelmenu.

   ![](assets/s_ncs_user_report_wizard_07.png)

   In de tabel worden de gegevens als volgt weergegeven:

   ![](assets/s_ncs_user_report_wizard_07a.png)

## Kwantitatieve gegevensanalyse {#quantitative-data-analysis}

**Doel**: om een kwantitatief analyserapport over ontvankelijke leeftijd te produceren

1. Open de beschrijvende analyseassistent en selecteer **[!UICONTROL Quantitative distribution]** in de vervolgkeuzelijst.

   ![](assets/s_ncs_user_report_wizard_011a.png)

   Klik op **[!UICONTROL Next]** om deze stap goed te keuren.

1. Selecteer de variabele **[!UICONTROL Age]** en voer het label ervan in. Geef op of het een geheel getal is en klik op **[!UICONTROL Next]** .

   ![](assets/s_ncs_user_report_wizard_011.png)

1. Verwijder de statistische gegevens **[!UICONTROL Deciles]** , **[!UICONTROL Distribution]** en **[!UICONTROL Sum]** : deze zijn hier niet nodig.

   ![](assets/s_ncs_user_report_wizard_012.png)

1. Klik **[!UICONTROL Next]** om het rapport te tonen.

   ![](assets/s_ncs_user_report_wizard_013.png)

## Een overgangsdoel analyseren in een workflow {#analyzing-a-transition-target-in-a-workflow}

**Doel**: om rapporten over de bevolking van een het richten werkschema te produceren

1. Open de gewenste doelworkflow.
1. Klik met de rechtermuisknop op een overgang die naar de tabel met ontvangers verwijst.
1. Selecteer **[!UICONTROL Analyze target]** in het keuzemenu om het beschrijvende analysevenster te openen.

   ![](assets/s_ncs_user_report_wizard_from_transision.png)

1. Op dit punt kunt u of de **[!UICONTROL Existing analyses and reports]** optie selecteren en rapporten gebruiken die eerder worden gecreeerd (verwijs naar [ het Hergebruiken van bestaande rapporten en analyses ](../../reporting/using/processing-a-report.md#re-using-existing-reports-and-analyses)), of tot een nieuwe beschrijvende analyse leiden. Hiervoor blijft de optie **[!UICONTROL New descriptive analysis from a template]** standaard geselecteerd.

   De rest van de configuratie is hetzelfde als voor alle beschrijvende analyses.

### Aanbevelingen voor doelanalyse {#target-analyze-recommendations}

De analyse van een populatie in een workflow vereist dat de populatie nog steeds aanwezig is in de overgang. Als de workflow wordt gestart, kan het resultaat met betrekking tot de bevolking uit de overgang worden verwijderd. Als u een analyse wilt uitvoeren, kunt u:

* Maak de overgang van zijn bestemmingsactiviteit los en begin het werkschema om het actief te maken. Zodra de overgang aan flits begint, lanceer de medewerker op de gebruikelijke manier.

  ![](assets/s_ncs_user_report_wizard_018.png)

* Wijzig de eigenschappen van de workflow door de optie **[!UICONTROL Keep the result of interim populations between two executions]** te selecteren. Hiermee kunt u een analyse van de overgang van uw keuze starten, zelfs als de workflow is voltooid.

  ![](assets/s_ncs_user_report_wizard_020.png)

  Als de bevolking uit de overgang werd leeggemaakt, vraagt een foutenmelding u om de betrokken optie te selecteren alvorens de beschrijvende analysemedewerker te lanceren.

  ![](assets/s_ncs_user_report_wizard_019.png)

>[!CAUTION]
>
>De optie **[!UICONTROL Keep the result of interim populations between two executions]** mag alleen worden gebruikt in ontwikkelingsfasen, maar nooit voor een productieomgeving.\
>De interimpopulaties worden automatisch leeggemaakt zodra de bewaartermijn is bereikt. Deze deadline wordt opgegeven op het tabblad met workfloweigenschappen **[!UICONTROL Execution]** .

## Logbestanden voor bijhouden ontvangers analyseren {#analyzing-recipient-tracking-logs}

De beschrijvende analysemedewerker kan rapporten over andere het werklijsten produceren. Dit betekent dat u leveringslogboeken kunt analyseren door een specifiek rapport te creëren.

In dit voorbeeld, willen wij het reactiviteitstarief van nieuwsbrieven ontvangers analyseren.

Hiervoor voert u de volgende stappen uit:

1. Open de beschrijvende analyseassistent via het menu **[!UICONTROL Tools > Descriptive analysis]** en wijzig de standaardwerktabel. Selecteer **[!UICONTROL Recipient tracking log]** en voeg een filter toe om Proofs uit te sluiten en nieuwsbrieven op te nemen.

   ![](assets/reporting_descriptive_sample_tracking_1.png)

   Selecteer een tabelweergave en klik op **[!UICONTROL Next]** .

1. Geef in het volgende venster op dat de analyse betrekking heeft op leveringen.

   ![](assets/reporting_descriptive_sample_tracking_2.png)

   Hier, zullen de leveringsetiketten in de eerste kolom worden getoond.

1. Schrap de standaardtelling en creeer drie statistieken om de statistieken te vormen die in de lijst moeten worden getoond.

   Hier wordt voor elke nieuwsbrief in de tabel het volgende weergegeven: het aantal keren dat wordt geopend, het aantal klikken, het percentage waarmee wordt gereactiveerd (als een percentage).

1. Voeg een statistiek toe voor het tellen van het aantal klikken: definieer het relevante filter op het tabblad **[!UICONTROL Filter]** .

   ![](assets/reporting_descriptive_sample_tracking_3.png)

1. Klik vervolgens op het tabblad **[!UICONTROL General]** om de naam van het label en de alias van de statistiek te wijzigen:

   ![](assets/reporting_descriptive_sample_tracking_4.png)

1. Voeg een tweede statistiek toe voor het tellen van het aantal openingen:

   ![](assets/reporting_descriptive_sample_tracking_5.png)

1. Klik vervolgens op het tabblad **[!UICONTROL General]** om de naam van het label voor statistieken en de alias ervan te wijzigen:

   ![](assets/reporting_descriptive_sample_tracking_6.png)

1. Voeg de derde statistiek toe en selecteer de operator **[!UICONTROL Calculated field]** om de reactiviteitssnelheid te meten.

   ![](assets/reporting_descriptive_sample_tracking_7.png)

   Ga naar het **[!UICONTROL User function]** gebied en ga de volgende formule in:

   ```
   @clic / @open * 100
   ```

   Pas het statistische label aan zoals hieronder aangegeven:

   ![](assets/reporting_descriptive_sample_tracking_8.png)

   Geef ten slotte op of de waarden worden weergegeven als een percentage: hiervoor schakelt u de optie **[!UICONTROL Default formatting]** op het tabblad **[!UICONTROL Advanced]** uit en selecteert u **[!UICONTROL Percentage]** zonder decimaalteken.

   ![](assets/reporting_descriptive_sample_tracking_10.png)

1. Klik **[!UICONTROL Next]** om het rapport te tonen.

   ![](assets/reporting_descriptive_sample_tracking_9.png)

## Logboeken voor leveringsuitsluitingen analyseren {#analyzing-delivery-exclusion-logs}

Als de analyse betrekking heeft op een levering, kunt u de uitgesloten populatie analyseren. Hiervoor selecteert u de te analyseren items en klikt u met de rechtermuisknop om het menu **[!UICONTROL Action > Explore exclusions]** te openen.

![](assets/reporting_descriptive_exclusion_menu.png)

Dit zal u aan de beschrijvende analysemedewerker nemen en de analyse zal de ontvankelijke uitsluitingslogboeken betreffen.

U kunt bijvoorbeeld de domeinen van alle uitgesloten adressen weergeven en deze sorteren op uitsluitingsdatum.

![](assets/reporting_descriptive_exclusion_sample.png)

Dit zou het volgende type van rapport produceren:

![](assets/reporting_descriptive_exclusion_result.png)
