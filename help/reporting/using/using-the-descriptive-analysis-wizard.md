---
title: De wizard voor beschrijvende analyse gebruiken
seo-title: De wizard voor beschrijvende analyse gebruiken
description: De wizard voor beschrijvende analyse gebruiken
seo-description: null
page-status-flag: never-activated
uuid: 30554909-4b91-46ff-bd8d-fa57ab6304f9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 18ba04d9-7bab-4eea-8dbb-6c2c138c5293
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# De wizard voor beschrijvende analyse gebruiken{#using-the-descriptive-analysis-wizard}

Als u een beschrijvend analyserapport wilt maken, gebruikt u de toegewezen wizard. De configuratie is afhankelijk van de te analyseren gegevens en van de gewenste rendering.

## Gegevens in de database analyseren {#analyzing-data-in-the-database}

De wizard voor beschrijvende analyse kan worden gestart via het **[!UICONTROL Tools > Descriptive analysis]** menu: in dit geval heeft de analyse standaard betrekking op ontvangers (**nms:ontvanger**) . Dit is van toepassing op alle gegevens in de Adobe Campagne-database.

![](assets/reporting_descriptive_wz_launch.png)

Als u een andere tabel dan de standaardontvangers wilt analyseren (**nms:ontvanger**), klikt u op de **[!UICONTROL Advanced settings...]** koppeling in de laatste fase van de wizard en selecteert u de tabel die overeenkomt met uw instellingen, in dit geval **met name:individu**:

![](assets/reporting_descriptive_other_schema.png)

Als u statistieken over een deel van de gegevens wilt produceren, kunt u een filter bepalen: Klik hiertoe op de **[!UICONTROL Advanced settings...]** koppeling en definieer het filter dat u wilt toepassen, zoals hieronder wordt weergegeven:

![](assets/reporting_descriptive_wz_filter.png)

De analyse zal alleen betrekking hebben op ontvangers van databanken van 16 jaar en ouder die in Londen wonen.

## Een set gegevens analyseren {#analyzing-a-set-of-data}

U kunt de beschrijvende analysewizard gebruiken via een andere context: een lijst, een workflowovergang, een of meer leveringen, een selectie van ontvangers, enz.

De toepassing is toegankelijk via verschillende knooppunten van de Adobe Campagne-structuur die naar de ontvangende tabel verwijzen.

Open de beschrijvende analysewizard door items te selecteren en met de rechtermuisknop te klikken. Alleen de geselecteerde gegevens worden geanalyseerd.

![](assets/reporting_descriptive_from_recipients.png)

* Voor een reeks **ontvangers** selecteert u de ontvangers die u wilt analyseren, klikt u met de rechtermuisknop en selecteert u **[!UICONTROL Actions > Explore...]**, zoals hierboven wordt weergegeven. Als een filter wordt toegepast op de lijst met ontvangers, wordt alleen de inhoud geanalyseerd.

   Als u alle ontvangers in de map of het huidige filter wilt selecteren, gebruikt u de sneltoets CTRL+A. Dit betekent dat zelfs ontvangers die niet worden weergegeven, worden geselecteerd.

   Een voorbeeld van de beschrijvende analyse van ontvangers vindt u in: [Kwalitatieve gegevensanalyse](../../reporting/using/use-cases.md#qualitative-data-analysis).

* In de context van een **werkschema**, plaats de curseur op een overgang die naar de lijst van ontvangers richt, klik met de rechtermuisknop aan en selecteer **[!UICONTROL Analyze target]**. Raadpleeg voor meer informatie het voorbeeld bij [Analyseren van een overgangsdoel in een workflow](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow).
* Voor **lijsten** selecteert u een of meer lijsten en past u hetzelfde proces toe als voor ontvangers.
* Selecteer in het kader van een **levering** de leveringen waarvan u het doel wilt analyseren, klik met de rechtermuisknop en selecteer **[!UICONTROL Actions > Explore the target]**, zoals hieronder wordt getoond:

   ![](assets/reporting_descriptive_from_deliveries.png)

   Hier worden voorbeelden gegeven van beschrijvende analyses voor leveringen: Een [populatie](../../reporting/using/use-cases.md#analyzing-a-population) analyseren en hier: Logboeken voor [bijhouden van ontvangers analyseren](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs).

## De kwalitatieve distributiesjabloon configureren {#configuring-the-qualitative-distribution-template}

Met de **[!UICONTROL Qualitative distribution]** sjabloon kunt u statistieken maken over alle typen gegevens (bijvoorbeeld de bedrijfsnaam, het e-maildomein).

De opties van de configuratie beschikbaar voor een rapport dat via het **[!UICONTROL Qualitative distribution]** malplaatje wordt gecreeerd zijn gedetailleerd in het [Weergeven van gegevens in de lijst](#displaying-data-in-the-table). Een volledig voorbeeld wordt in detail beschreven in het [Analyseren van een populatie](../../reporting/using/use-cases.md#analyzing-a-population).

Wanneer u de beschrijvende analysewizard gebruikt om uw gegevens te analyseren, zijn de beschikbare opties afhankelijk van de gekozen instellingen. Deze worden hieronder beschreven.

### Gegevensbinding {#data-binning}

Wanneer u de variabelen selecteert die u wilt weergeven, kunt u gegevensbinding definiëren, met andere woorden groepscriteria voor de geselecteerde gegevens configureren.

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>Wanneer het veld waarop de berekening betrekking heeft, wordt berekend aan de hand van een aggregaat, moet worden nagegaan of de prestaties **[!UICONTROL The data is already aggregated]** zijn verbeterd.

De opties zijn afhankelijk van de inhoud van het veld:

* **[!UICONTROL None]** : Met deze optie kunt u alle waarden weergeven die beschikbaar zijn voor de variabele, zonder dat u een binding hoeft te maken.

   >[!CAUTION]
   >
   >Deze optie dient met voorzichtigheid te worden gebruikt: het kan een grote invloed hebben op het rapport en op de prestaties van de machine .

* **[!UICONTROL Auto]** : met deze optie kunt u de meest gebruikte waarden weergeven. Ze worden automatisch berekend en elk vertegenwoordigen een percentage van de variabelen in verhouding tot het aantal vakken. Voor numerieke waarden genereert Adobe Campaign automatisch een klasse waarin de gegevens worden gesorteerd.
* **[!UICONTROL Manual]** : deze optie werkt net als de **[!UICONTROL Auto]** optie, maar u kunt deze waarden handmatig instellen. Klik hiertoe op de **[!UICONTROL Add]** knop rechts van de waardetabel.

   Waarden kunnen automatisch door Adobe Campaign worden geïnitialiseerd voordat u de afbeelding kunt aanpassen: Voer hiertoe het aantal vakken in dat u wilt genereren en klik op de **[!UICONTROL Initialize with]** koppeling, zoals hieronder wordt weergegeven:

   ![](assets/reporting_descriptive_initialize.png)

   Pas vervolgens de inhoud aan uw wensen aan:

   ![](assets/reporting_descriptive_initialize_perso.png)

   Afhankelijk van het gewenste precisieniveau kunnen velden met datums worden gegroepeerd op tijd, dag, maand, jaar, enzovoort.

   ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]** : Hiermee kunt u groepen waarden maken in het geval van numerieke waarden. Met een modulo met een waarde van 10 kunt u bijvoorbeeld een interval maken van waarden die tien voor tien veranderen.

   ![](assets/reporting_descriptive_initialize_modulo.png)

   In dit voorbeeld kunt u de uitsplitsing van ontvangers per leeftijdsgroep bekijken.

   ![](assets/reporting_descriptive_initialize_modulo_result.png)

### Gegevens in de tabel weergeven {#displaying-data-in-the-table}

Gebruik de werkbalk om de weergave van variabelen in de tabel aan te passen: Verwijder een kolom, geef gegevens in lijnen eerder dan kolommen weer, verplaats een kolom naar links of rechts, bekijk of wijzig de waardeberekening.

![](assets/s_ncs_user_report_wizard_toolbar.png)

In het bovenste gedeelte van het venster kunt u de weergave-instellingen selecteren.

U kunt de naam van de statistieken en de subtotalen weergeven of verbergen en de richting van de statistieken kiezen. Voor meer op dit, verwijs naar de montages [van de het rapportvertoning van de](../../reporting/using/processing-a-report.md#analysis-report-display-settings)Analyse.

### Gegevens in het diagram weergeven {#displaying-data-in-the-chart}

In de eerste stap van de beschrijvende analysewizard kunt u ervoor kiezen de gegevens alleen in diagramvorm weer te geven, zonder een tabel. In dit geval moet variabele selectie plaatsvinden tijdens het configureren van de afbeelding. U moet eerst het aantal variabelen selecteren dat u wilt weergeven en de velden in de desbetreffende database selecteren.

![](assets/s_ncs_user_report_wizard_023.png)

Selecteer vervolgens het gewenste diagramtype.

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>U kunt de variabelen in een grafiek en een lijst tezelfdertijd tonen. Voer hiertoe de variabelen in het **[!UICONTROL Table configuration]** venster in. Klik **[!UICONTROL Next]** en selecteer het type van grafiek in het venster van de grafiekconfiguratie. Als de subafmetingen in de lijst worden bepaald, worden zij niet getoond in de grafiek.

Klik op de **[!UICONTROL Variants]** koppeling om de eigenschappen van het diagram te wijzigen.

![](assets/reporting_descriptive_graphe_options.png)

Welke opties worden aangeboden, is afhankelijk van het geselecteerde diagramtype. Raadpleeg [deze pagina](../../reporting/using/creating-a-chart.md#chart-types-and-variants)voor meer informatie.

### Berekening van statistieken {#statistics-calculation}

De beschrijvende analysetovenaar laat u verscheidene types van statistieken over de gegevens berekenen. Door gebrek, slechts wordt één eenvoudige telling gevormd.

Klik **[!UICONTROL Add]** om een nieuwe statistiek te maken.

![](assets/reporting_descriptive_create_stat.png)

De volgende bewerkingen zijn mogelijk:

* **[!UICONTROL Count]** alle niet-null-waarden van het veld te tellen, met inbegrip van dubbele waarden (van het geaggregeerde veld);
* **[!UICONTROL Average]** het gemiddelde van de waarden in een numeriek veld te berekenen;
* **[!UICONTROL Minimum]** het minimum van de waarden in een numeriek veld te berekenen;
* **[!UICONTROL Maximum]** het maximum van de waarden in een numeriek veld te berekenen;
* **[!UICONTROL Sum]** de som van de waarden in een numeriek veld te berekenen;
* **[!UICONTROL Standard deviation]** om te berekenen hoe de geretourneerde waarden rond het gemiddelde zijn verspreid;
* **[!UICONTROL Row percentage distribution]** de verhouding tussen de waarde in een kolom en de waarde in een rij berekenen (alleen beschikbaar voor tabellen);
* **[!UICONTROL Column percentage distribution]** de verhouding tussen de waarde in een rij en de waarde in een kolom berekenen (alleen beschikbaar voor tabellen);
* **[!UICONTROL Total percentage distribution]** de verdeling van de begunstigden waarop de waarden betrekking hebben, te berekenen;

   ![](assets/s_ncs_user_report_wizard_026.png)

* **[!UICONTROL Calculated field]** om een gepersonaliseerde exploitant (beschikbaar voor lijsten slechts) tot stand te brengen. In het **[!UICONTROL User function]** veld kunt u de berekening invoeren die op de gegevens moet worden toegepast.

   Voorbeeld: Berekening van het gemiddelde aankoopbedrag per klant op basis van land en herkomst

   ![](assets/report_compute_data_sample1.png)

   Als u de bovenstaande gegevens in een tabel wilt weergeven, moet u een berekend veld maken voor het opslaan van het gemiddelde aankoopbedrag per klant.

   Dit doet u als volgt:

   1. Bereken het aankooptotaal.

      ![](assets/report_compute_data_sample2.png)

   1. Deze statistiek wordt niet weergegeven in de tabel. Schakel de **[!UICONTROL Display in the table]** optie van het **[!UICONTROL Advanced]** tabblad uit.

      ![](assets/report_compute_data_sample3.png)

   1. Maak een nieuwe **[!UICONTROL Calculated field]** typestatistiek en voer in het **[!UICONTROL User function]** veld de volgende formule in: **@aankopen/@aantal**.

      ![](assets/report_compute_data_sample4.png)

### Het rapport weergeven {#displaying-the-report}

De laatste stap van de tovenaar laat u het rapport, d.w.z. de lijst of de grafiek tonen aangezien zij zijn gevormd.

Als het rapport een tabel bevat, wordt de cel met het rekenresultaat gekleurd. Hoe hoger het resultaat, hoe sterker de kleur.

![](assets/report_compute_data_sample1.png)

Het is mogelijk om de indeling van de resultaten te wijzigen. Klik hiertoe met de rechtermuisknop op de betreffende variabele en selecteer de invoer in het snelmenu.

![](assets/s_ncs_user_report_wizard_029.png)

Wanneer het rapport een grafiek omvat, laten de etiketten van de legenda u de getoonde informatie filtreren: Klik op een label om de weergave in het diagram in of uit te schakelen.

![](assets/report_display_data_in_graph.png)

## De kwantitatieve distributiesjabloon configureren {#configuring-the-quantitative-distribution-template}

Als u zelf een beschrijvende analyse wilt genereren, selecteert u de optie **Nieuwe beschrijvende analyse in een sjabloon** als deze niet standaard is ingesteld.

De **[!UICONTROL Quantitative distribution]** sjabloon waarmee u statistieken kunt genereren over gegevens die kunnen worden gemeten of geteld (bijvoorbeeld factuurbedrag, leeftijd van ontvangers).

De configuratiewijze van een analyserapport dat via het **[!UICONTROL Quantitative distribution]** malplaatje wordt gecreeerd is gedetailleerd in een [Kwantitatieve gegevensanalyse](../../reporting/using/use-cases.md#quantitative-data-analysis)van het implementatievoorbeeld.

De opties die beschikbaar zijn wanneer u de wizard voor beschrijvende analyse gebruikt om een kwantitatief rapport te maken, worden hieronder beschreven.

Selecteer eerst de variabele waarop de berekeningen betrekking hebben:

![](assets/s_ncs_user_report_wizard_017.png)

Standaard biedt Adobe Campaign een aantal statistieken die voor de geselecteerde gegevens moeten worden berekend. U kunt deze lijst wijzigen, er statistieken aan toevoegen of verwijderen, afhankelijk van uw behoeften.

De volgende bewerkingen zijn mogelijk:

* **[!UICONTROL Count]** alle niet-null-waarden van het veld te tellen, met inbegrip van dubbele waarden (van het geaggregeerde veld);
* **[!UICONTROL Average]** het gemiddelde van de waarden in een numeriek veld te berekenen;
* **[!UICONTROL Minimum]** het minimum van de waarden in een numeriek veld te berekenen;
* **[!UICONTROL Maximum]** om het maximum van de waarden in een numeriek veld te berekenen.
* **[!UICONTROL Sum]** de som van de waarden in een numeriek veld te berekenen;
* **[!UICONTROL Standard deviation]** om te berekenen hoe de teruggekeerde waarden rond het gemiddelde worden verdeeld.
* **[!UICONTROL Number of missing values]** om het aantal numerieke velden zonder gedefinieerde waarden te berekenen.
* **[!UICONTROL Decile distribution]** om de geretourneerde waarden zo te verdelen dat elke waarde een tiende van de waarden in een numeriek veld vertegenwoordigt.
* **[!UICONTROL Custom distribution]** om de teruggekeerde waarden te verdelen die op user-defined drempels worden gebaseerd.

   Met de **[!UICONTROL Detail...]** knop kunt u een statistiek bewerken en, indien nodig, de berekening of weergave aanpassen:

   ![](assets/s_ncs_user_report_wizard_030.png)

   De laatste stap van de tovenaar toont het kwantitatieve analyserapport.

   ![](assets/reporting_descriptive_view_report.png)

   Om veranderingen in het rapport aan te brengen, verwijs naar het [Verwerken van een rapport](../../reporting/using/processing-a-report.md).

