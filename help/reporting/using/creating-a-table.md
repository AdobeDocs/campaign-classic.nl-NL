---
product: campaign
title: Een tabel maken
description: Een tabel maken
exl-id: 05f76bdf-6dcd-4360-9e72-0ba6a4dd0d5e
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '2495'
ht-degree: 1%

---

# Een tabel maken{#creating-a-table}

![](../../assets/common.svg)

U kunt een lijst aan een rapport toevoegen om gegevens te tonen. Dit kan een draaitabel zijn die is gemaakt op basis van kubutemetingen, een lijst met groepen of een tabel met een uitsplitsing van waarden.

![](assets/s_advuser_report_page_activity_05.png)

## Een lijst met groepen maken {#creating-a-list-with-group}

A **[!UICONTROL List with group]** Met typetabel kunt u gegevens in de tabel groeperen en er statistieken over produceren. U kunt bijvoorbeeld totalen en subtotalen maken voor de gegevens. Elke groep heeft zijn eigen kop-, detail- en voettekstregel.

>[!CAUTION]
>
>De **[!UICONTROL Page]** activiteit die de tabel bevat, moet worden voorafgegaan door een **[!UICONTROL Query]** of **[!UICONTROL Script]** activiteit om de in het verslag te analyseren gegevens te verzamelen. Raadpleeg voor meer informatie over deze activiteiten [Gegevens verzamelen voor analyse](../../reporting/using/collecting-data-to-analyze.md) en [Scriptactiviteit](../../reporting/using/advanced-functionalities.md#script-activity).

### Werkwijze {#operating-principle}

Het kan gebeuren dat u verschillende gegevenscategorieën tegelijk moet analyseren. Met een lijst met groepen kunt u gegevens combineren en statistieken maken over verschillende groepen gegevens in dezelfde tabel. Hiertoe kunt u een groep in de tabel maken.

In het volgende voorbeeld toont de groep alle campagnes in het gegevensbestand, de leveringen, en het aantal berichten die per levering en per campagne worden verzonden.

Hiermee kunt u de campagnes weergeven (**[!UICONTROL Label (Campaign)]**, de lijst van leveringen (**[!UICONTROL Label]** ) gekoppeld aan de campagne en kunt u het aantal verzonden berichten per levering tellen (**[!UICONTROL Processed)]**, voordat u deze optelt voor elke campagne (**[!UICONTROL Sum(@processed)]** ).

![](assets/s_advuser_ergo_listgroup_005.png)

### Implementatiestappen {#implementation-steps}

Hier vindt u een volledig voorbeeld van implementatie: [Hoofdlettergebruik: Een rapport maken met een groepslijst](#use-case--create-a-report-with-a-group-list).

Houd rekening met de volgende stappen om een tabel van het type &#39;Lijst met groep&#39; te maken:

1. Ga naar het rapportdiagram en plaats een **[!UICONTROL Query]** activiteit. Zie [Gegevens verzamelen voor analyse](../../reporting/using/collecting-data-to-analyze.md).
1. Vul de brontabel in en selecteer de velden van de tabel die de statistieken betreffen.
1. Een **[!UICONTROL Page]** activiteit in de grafiek. Raadpleeg voor meer informatie hierover [Statische elementen](../../reporting/using/creating-a-new-report.md#static-elements).
1. Een **[!UICONTROL List with group]** typt u tabel in de pagina.
1. Geef het gegevenspad op of de tabel die als gegevensbron in de query is geselecteerd.

   Deze stap is verplicht als u de velden in de brontabel later wilt herstellen en deze wilt invoegen in de cellen van de tabel.

1. De tabel en de inhoud ervan maken.
1. Het voltooide rapport weergeven in het dialoogvenster **[!UICONTROL Preview]** tab. Vervolgens kunt u het rapport publiceren en het indien nodig exporteren naar een andere indeling. Raadpleeg voor meer informatie hierover [Een rapport exporteren](../../reporting/using/actions-on-reports.md#exporting-a-report).

### Lijnen en kolommen toevoegen {#adding-lines-and-columns}

Standaard wordt een **[!UICONTROL List with group]** teksttabel bevat een koptekst, een detailregel en een voettekstregel.

De groep zelf bevat kop-, detail- en voettekstregel.

* **Kopregel**: op deze regel geeft u een titel aan de kolommen van de tabel.

   ![](assets/s_advuser_ergo_listgroup_003a.png)

* **Detaillijn**: deze regel bevat statistische waarden .

   ![](assets/s_advuser_ergo_listgroup_004.png)

* **Voettekstregel**: op deze regel kunt u de totale waarden weergeven.

   ![](assets/s_advuser_ergo_listgroup_003.png)

Lijnen en kolommen kunnen naar wens worden toegevoegd.

De groep kan op om het even welke lijn van de lijst worden geplaatst en omvat zijn eigen kopbal, detail en footer lijnen.

![](assets/s_advuser_ergo_listgroup_019.png)

**Lijn en kolom**: als u een regel of kolom wilt toevoegen of verwijderen, gaat u naar een bestaande regel of kolom en gebruikt u het snelmenu.

![](assets/s_advuser_ergo_listgroup_006.png)

De aard van de lijn die u toevoegt, is afhankelijk van de locatie van de cursor. Als u bijvoorbeeld een koptekstregel wilt toevoegen, plaatst u de cursors op een koptekst en klikt u op **[!UICONTROL Add > A line above/below]**.

![](assets/s_advuser_ergo_listgroup_006a.png)

De breedte van de kolommen kan worden gewijzigd via de **[!UICONTROL Column format]** item.

**Groep**: om een groep toe te voegen, ga naar een lijn en selecteer het passende punt in het drop-down menu.

![](assets/s_advuser_ergo_listgroup_007.png)

### Celinhoud definiëren {#defining-cell-content}

Als u een cel van de tabel wilt bewerken en de inhoud en indeling ervan wilt definiëren, gaat u naar de cel en gebruikt u het snelmenu.

Gebruik de **[!UICONTROL Expression]** menu-item om de waarden te selecteren die moeten worden weergegeven.

![](assets/s_advuser_ergo_listgroup_010.png)

* Als u de waarden wilt invoegen die rechtstreeks in de tabel moeten worden geanalyseerd, selecteert u deze in de beschikbare velden.

   De lijst van beschikbare gebieden valt met de inhoud van de vraag vóór de lijst in de grafiek van de rapportconstructie samen.

   ![](assets/s_advuser_ergo_listgroup_011.png)

* Voer een label in voor een cel, bijvoorbeeld de koptekst.

   Hiervoor gebruikt u hetzelfde proces als voor het invoegen van een veld in de database, maar selecteert u geen expressie. Voer het label in het dialoogvenster **[!UICONTROL Label]** veld. Het zal worden getoond zoals is.

* Een aggregaat berekenen (gemiddelde waarde, som enz.) en in de cel weergeven.

   Om dit te doen, gebruik **[!UICONTROL Aggregates]** en selecteer de gewenste campagne.

   ![](assets/s_advuser_ergo_listgroup_008.png)

### Celindeling definiëren {#defining-cell-format}

![](assets/s_advuser_ergo_listgroup_017.png)

Als u de celindeling wilt definiëren, **[!UICONTROL Cell format...]** Hiermee hebt u toegang tot alle opmaakopties die beschikbaar zijn voor de geselecteerde cel.

Met deze opties kunt u de uiteindelijke rendering van het rapport aanpassen en het lezen van informatie vereenvoudigen.

Gebruik de **[!UICONTROL Carriage return]** veld bij het exporteren van gegevens naar Excel: Selecteer de **[!UICONTROL Yes]** waarde om de harde return te forceren. Deze waarde blijft behouden bij het exporteren. Raadpleeg voor meer informatie hierover [Een rapport exporteren](../../reporting/using/actions-on-reports.md#exporting-a-report).

De **[!UICONTROL Cell format]** kunt u het volgende tabblad openen:

* De **[!UICONTROL Value]** tab
* De **[!UICONTROL Borders]** tab
* De **[!UICONTROL Click]** tab
* De **[!UICONTROL Extra]** tab

De **[!UICONTROL Value]** kunt u het lettertype en de verschillende waardetekenmerken wijzigen of een opmaak definiëren op basis van de aard ervan.

![](assets/s_advuser_ergo_listgroup_009.png)

De indeling wijzigt de weergave van gegevens: bijvoorbeeld de **[!UICONTROL Number]**, **[!UICONTROL Monetary]** en **[!UICONTROL Percentage]** Met indelingen kunt u de cijfers rechts uitlijnen en decimalen weergeven.

Voorbeeld van het configureren van een valutaopmaak: u kunt opgeven in welke valuta de waarden worden uitgedrukt, kiezen of duizenden worden gescheiden en negatieve waarden in rood worden weergegeven. De positie van het valutasymbool hangt af van de taal van de operator die in zijn profiel is gedefinieerd.

![](assets/s_advuser_ergo_listgroup_012.png)

Voorbeeld van configuratie voor datums: U kunt kiezen of u de tijd wilt weergeven.

![](assets/s_advuser_ergo_listgroup_013.png)

De **Randen** kunt u randen toevoegen aan de lijnen en kolommen in de tabel. Als u randen toevoegt aan de cellen, kunnen er prestatieproblemen optreden wanneer u grote rapporten exporteert naar Excel.

![](assets/s_advuser_ergo_listgroup_014.png)

Indien nodig kunt u randen definiëren in de tabelsjabloon (**[!UICONTROL Administration > Configuration > Form rendering]** ).

In dit geval hebt u de volgende syntaxis:

Op het tabblad Web:

```
 .tabular td {
 border: solid 1px #000000;
 }
```

Op het tabblad Excel:

```
 <style name="odd" fillColor="#fdfdfd">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
 
 <style name="even" fillColor="#f7f8fa">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
```

De **[!UICONTROL Click]** kunt u een actie definiëren wanneer de gebruiker op de inhoud van een cel of van de tabel klikt.

In het onderstaande voorbeeld kunt u de tweede pagina van het rapport weergeven door op de waarde in de cel te klikken: het zal informatie over de levering in de cel bevatten .

![](assets/s_advuser_ergo_listgroup_015.png)

De **Extra** kunt u visueel koppelen aan uw gegevens, zoals een gekleurd teken of een waardebalk. Het gekleurde teken wordt gebruikt wanneer de tabel als een legenda in een diagram wordt weergegeven. Raadpleeg voor meer informatie het voorbeeld van de implementatie: [Stap 5 - Maak de tweede pagina](#step-5---create-the-second-page)

![](assets/s_advuser_ergo_listgroup_016.png)

## Hoofdlettergebruik: Een rapport maken met een groepslijst {#use-case--create-a-report-with-a-group-list}

In dit voorbeeld gaan we een rapport van twee pagina&#39;s maken: de eerste pagina bevat de lijst en het totale aantal leveringen per campagne , alsmede het aantal verzonden berichten . De namen van de levering zullen klikbare verbindingen zijn en zullen u toelaten om naar de tweede pagina van het rapport te gaan om de uitsplitsing van leveringen per e-maildomein voor de geselecteerde levering met een lijst en een grafiek te bekijken. Op de tweede pagina fungeert de tabel als een legenda voor het diagram.

![](assets/reporting_quick_start_report-final.png)

### Stap 1 - Een rapport maken {#step-1---create-a-report}

Een nieuw rapport maken dat betrekking heeft op het campagneschema, **[!UICONTROL Campaigns (nms)]**.

![](assets/s_advuser_report_listgroup_001.png)

Klikken **[!UICONTROL Save]** om het rapport te maken.

Ga naar de grafiek en voeg de eerste componenten toe die voor het ontwerpen van de rapportinhoud moeten worden gebruikt: een eerste query en een eerste pagina.

![](assets/reporting_quick_start_diagram.png)

### Stap 2 - creeer de eerste vraag {#step-2---create-the-first-query}

Met de eerste query kunt u leveringen verzamelen die aan elke campagne zijn gekoppeld. Het doel is een rapport weer te geven over de verschillende leveringen van de Adobe Campaign-database die aan elke campagne zijn gekoppeld.

Dubbelklik op de eerste query om deze te bewerken en pas vervolgens de volgende stappen toe om deze te configureren:

1. Begin door het schema te veranderen waarop de bron van de vraag wordt toegepast: Selecteer de **[!UICONTROL Deliveries (nms)]** schema.
1. Klik op de knop **[!UICONTROL Edit query]** De geavanceerde velden koppelen en weergeven.

   ![](assets/reporting_quick_start_query-1.png)

1. Selecteer de volgende velden:

   * het leveringsetiket,
   * de primaire sleutel voor de levering,
   * het campagneetiket,
   * de indicator van de verwerkte leveringen,
   * de buitenlandse sleutel van de Campagne-koppeling,
   * de indicator voor de foutenfrequentie.

   ![](assets/s_advuser_report_listgroup_002.png)

   Een alias koppelen aan elk veld: dit wordt aanbevolen om de gegevens in de tabel die aan de eerste pagina van het rapport worden toegevoegd, gemakkelijker te kunnen selecteren.

   In dit voorbeeld gebruiken we de volgende aliassen:

   * Label: **@label**
   * Primaire sleutel: **@deliveryId**
   * Label (campagne): **@label1**
   * Verwerkt: **@processed**
   * Externe sleutel van de koppeling &#39;Campaign&#39; (&#39;id&#39;): **@operationId**
   * Foutfrequentie: **@errorRatio**


1. Klik op de knop **[!UICONTROL Next]** tweemaal om naar de **[!UICONTROL Data filtering]** stap.

   Voeg een filtervoorwaarde toe om slechts de leveringen te verzamelen verbonden aan een campagne.

   De syntaxis van dit filter is als volgt: &quot;De buitenlandse sleutel van de verbinding &quot;Campaigns&quot;groter dan 0&quot;.

   ![](assets/reporting_quick_start_query_filter.png)

1. Klikken **[!UICONTROL Finish]** als u deze voorwaarden wilt opslaan, klikt u op **[!UICONTROL Ok]** om de vraagredacteur te sluiten.

### Stap 3: De eerste pagina maken {#step-3--create-the-first-page}

In deze stap, gaan wij de eerste pagina van het rapport vormen. Voer de volgende stappen uit om het te configureren:

1. Open de **[!UICONTROL Page]** activiteit en voer de titel ervan in, bijvoorbeeld **Leveringen** in dit geval.

   ![](assets/s_advuser_report_listgroup_003.png)

1. Voeg een lijst met groepen in via de werkbalk en voer het label ervan in, bijvoorbeeld: Lijst van leveringen per campagne.

   ![](assets/s_advuser_report_listgroup_004.png)

1. Klik op de knop **[!UICONTROL Table data XPath...]** en selecteer de leveringskoppeling, d.w.z. `[query/delivery]`.

   ![](assets/s_advuser_report_listgroup_005.png)

1. Klik op de knop **[!UICONTROL Data]** tabblad en layout van de tabel wijzigen: Voeg drie kolommen aan de rechterkant toe.

   ![](assets/s_advuser_report_listgroup_006.png)

1. Voeg een groep toe.

   ![](assets/s_advuser_report_listgroup_008.png)

   Met deze groep kunt u campagnes en de bijbehorende leveringen groeperen.

1. Verwijs in het groepsvenster naar de **Buitenlandse sleutel van de koppeling &#39;Campaign&#39;** en sluit het venster.

   ![](assets/s_advuser_report_listgroup_007.png)

1. Bewerk de eerste cel van de groepsheader en voeg de **[!UICONTROL Label]** veld van de campagnes als expressie.

   ![](assets/s_advuser_report_listgroup_009.png)

1. De tweede cel van de detailregel bewerken en de leveringen selecteren **[!UICONTROL Label]**.

   ![](assets/s_advuser_report_listgroup_011.png)

1. De opmaak van deze cel bewerken en het dialoogvenster **[!UICONTROL Click]** tab. Configureer de juiste opties zodat wanneer de gebruikers op de naam van een levering klikken, deze in hetzelfde venster wordt geopend.

   ![](assets/s_advuser_report_listgroup_0111.png)

   Selecteer een **[!UICONTROL Next page]** tekstactie en selecteer **[!UICONTROL In the same window]** als een open optie.

   ![](assets/s_advuser_report_listgroup_0112.png)

1. Klik in de onderste sectie van het venster op **[!UICONTROL Add]** en de **`/vars/selectedDelivery`** en **[!UICONTROL @deliveryId]** expressie die overeenkomt met de alias van de primaire sleutel van de levering, zoals gedefinieerd in de eerder gemaakte query. Met deze formule hebt u toegang tot de geselecteerde levering.

   ![](assets/s_advuser_report_listgroup_010.png)

1. De tweede cel van de voettekstregel van de groep bewerken en invoeren **[!UICONTROL Total per campaign]** als label.

   ![](assets/s_advuser_report_listgroup_012.png)

1. Bewerk de derde cel van de koptekstregel van de groep en typ **[!UICONTROL Number of messages sent]** als label.

   ![](assets/s_advuser_report_listgroup_013.png)

   Deze informatie valt samen met de kolomtitel.

1. Bewerk de derde cel van de detailregel en selecteer de verwerkte berichtindicator als een expressie.

   ![](assets/s_advuser_report_listgroup_014.png)

1. Bewerk de derde cel van de voettekstregel van de groep, selecteer de verwerkte leveringsindicator en pas de **[!UICONTROL Sum]** samenvoegen.

   ![](assets/s_advuser_report_listgroup_015.png)

1. Bewerk de vierde cel van de detailregel en selecteer de **foutfrequentie bij levering van fout** als een expressie.

   ![](assets/s_advuser_report_listgroup_016.png)

1. Selecteer deze cel om een waardebalk weer te geven die de frequentie van de leveringsfout vertegenwoordigt.

   Ga hiertoe naar de **[!UICONTROL More]** tab. Selecteer **[!UICONTROL Value bar]** in de vervolgkeuzelijst en selecteert u de **[!UICONTROL Hide the cell value]** optie.

   ![](assets/s_advuser_report_listgroup_023.png)

   U kunt nu een rendering van het rapport weergeven. Klik op de knop **[!UICONTROL Preview]** en selecteert u de **[!UICONTROL Global]** optie: Hier ziet u een lijst met alle leveringen in de Adobe Campaign-database die aan een campagne zijn gekoppeld.

   ![](assets/s_advuser_report_listgroup_025.png)

   We raden u aan de **[!UICONTROL Preview]** om ervoor te zorgen dat de gegevens in uw tabel correct zijn geselecteerd en geconfigureerd. Zodra dit wordt gedaan, kunt u aan het formatteren van uw lijst verdergaan.

1. Pas de **[!UICONTROL Bold]** stijl aan de cellen die het totaal per campagne en het totale aantal verwerkte berichten tonen.

   ![](assets/s_advuser_report_listgroup_024.png)

1. Klik op de eerste cel van de groepsheader, de cel die de naam van de campagne weergeeft, en selecteer **[!UICONTROL Edit > Merge to right]**.

   ![](assets/s_advuser_report_listgroup_026.png)

   Wanneer de eerste twee cellen van de groepsheader worden samengevoegd, worden de titel van de campagne en de lijst met hiermee verbonden leveringen opnieuw uitgelijnd.

   ![](assets/s_advuser_report_listgroup_027.png)

   >[!CAUTION]
   >
   >We raden u aan te wachten tot uw rapport is samengesteld voordat u cellen samenvoegt, aangezien samenvoegen onomkeerbaar is.

### Stap 4 - Maak de tweede query {#step-4---create-the-second-query}

Wij willen een tweede vraag en een tweede pagina toevoegen om de details van een levering te tonen wanneer de gebruiker van het rapport op het klikt. Alvorens de vraag toe te voegen, geef de pagina uit u hebt gecreeerd en laat de uitgaande overgang toe zodat het aan de vraag kan worden verbonden.

1. Een nieuwe query toevoegen na de opdracht **[!UICONTROL Page]** activiteit en geef zijn schema uit: Selecteer de **[!UICONTROL Recipient delivery logs]** schema.

   ![](assets/reporting_quick_start_query-2.png)

1. Bewerk de query en definieer de uitvoerkolommen. Als u het aantal leveringen per e-maildomein wilt weergeven, moet u:

   * Bereken de som van de primaire sleutels om het aantal leveringslogboeken te tellen:

      ![](assets/reporting_quick_start_query-2_count.png)

   * e-maildomeinen van ontvangers en groepsgegevens in dit veld verzamelen: om dit te doen, selecteer **[!UICONTROL Group]** in de kolom met domeinnamen.

   ![](assets/reporting_quick_start_query-2_filter.png)

   Koppel de volgende aliassen aan de velden:

   * count(primaire sleutel): **@count**
   * E-maildomein (ontvanger): **@domain**

      ![](assets/reporting_quick_start_query-2_alias.png)


1. Klik op de knop **[!UICONTROL Next]** knop tweemaal: dit brengt u naar **[!UICONTROL Data filtering]** stap.

   Voeg een filtervoorwaarde toe om slechts de informatie te verzamelen verbonden aan de geselecteerde levering.

   De syntaxis is als volgt: De buitenlandse sleutel van de verbinding van de &quot;Levering&quot;is de waarde van het plaatsen `$([vars/selectedDelivery])`

   ![](assets/s_advuser_report_listgroup_017.png)

1. Sluit het venster van de vraagconfiguratie en voeg een pagina aan de grafiek toe, enkel na de tweede vraag.

### Stap 5 - Maak de tweede pagina {#step-5---create-the-second-page}

1. Bewerk de pagina en voer het label ervan in: **E-maildomeinen**.
1. Schakel het selectievakje **[!UICONTROL Enable output transitions]** optie: dit is de laatste bladzijde van het verslag en zal niet door een andere activiteit worden gevolgd .

   ![](assets/s_advuser_report_listgroup_028.png)

1. Een nieuwe lijst met een groep toevoegen met behulp van het snelmenu en deze aanroepen **E-maildomeinen per ontvanger**.
1. Klik op de knop **[!UICONTROL Table data XPath...]** en selecteert u de **[!UICONTROL Recipient delivery logs]** koppeling.

   ![](assets/s_advuser_report_listgroup_029.png)

1. In de **[!UICONTROL Data]** kunt u de tabel als volgt aanpassen:

   * Voeg twee kolommen aan de rechterkant toe.
   * Voeg in de eerste cel van de detailregel de opdracht **[!UICONTROL rowNum()-1]** expressie om het aantal regels te tellen. Wijzig vervolgens de indeling van de cel: in de **[!UICONTROL Extra]** tab, selecteert u **[!UICONTROL Color tab]** en klik op **[!UICONTROL Ok]**.

      ![](assets/s_advuser_report_listgroup_018.png)

      Deze configuratie zal u toelaten om de lijst als titel voor de grafiek te gebruiken.

   * Voeg in de tweede cel van de detailregel de opdracht **[!UICONTROL Email domain(Recipient)]** expressie.
   * Voeg in de derde cel van de detailregel de knop **[!UICONTROL count(primary key)]** expressie.

   ![](assets/s_advuser_report_listgroup_019.png)

1. Voeg een cirkeldiagram aan de pagina toe gebruikend het met de rechtermuisknop aanklikken menu en wijs toe **E-maildomeinen** eraan te koppelen. Raadpleeg voor meer informatie [Grafiektypen en -varianten](../../reporting/using/creating-a-chart.md#chart-types-and-variants).
1. Klik op de knop **[!UICONTROL Variants]** en deselecteer de **[!UICONTROL Display label]** en de **[!UICONTROL Display caption]** opties.
1. Controleer of er geen waarde sortering is geconfigureerd. Raadpleeg [deze sectie](../../reporting/using/processing-a-report.md#configuring-the-layout-of-a-descriptive-analysis-report) voor meer informatie.

   ![](assets/s_advuser_report_listgroup_0191.png)

1. In de **[!UICONTROL Data]** wijzigen, wijzigt u de gegevensbron: selecteren **[!UICONTROL Context data]** in de vervolgkeuzelijst.

   ![](assets/s_advuser_report_listgroup_020.png)

1. Klik vervolgens op **[!UICONTROL Advanced settings]** en selecteer de koppeling naar de leveringslogboeken van de ontvanger.

   ![](assets/s_advuser_report_listgroup_0201.png)

1. In de **[!UICONTROL Chart type]** selecteert u de **[!UICONTROL Email domain]** variabele.
1. Voeg vervolgens de uit te voeren berekening toe: selecteert de som als een operator.

   ![](assets/s_advuser_report_listgroup_0202.png)

1. Klik op de knop **[!UICONTROL Detail]** om het gebied te selecteren dat de telling zal betreffen, dan sluit het configuratievenster.

   ![](assets/s_advuser_report_listgroup_030.png)

1. Sla het rapport op.

   Uw pagina is nu geconfigureerd.

### Stap 6 - Bekijk het rapport {#step-6---viewing-the-report}

Als u het resultaat van deze configuratie wilt weergeven, klikt u op de knop **[!UICONTROL Preview]** en selecteert u de **[!UICONTROL Global]** optie.

De eerste pagina van uw rapport bevat de lijst met alle leveringen die in de database zijn opgenomen.

![](assets/s_advuser_report_listgroup_021.png)

Als u op de koppeling van een van deze leveringen klikt, wordt in het diagram de indeling van e-maildomeinen voor deze levering weergegeven. U bevindt zich nu op de tweede pagina van het rapport en kunt terugkeren naar de vorige pagina door op de desbetreffende knop te klikken.

![](assets/s_advuser_report_listgroup_022.png)

## Een splitsings- of draaitabel maken {#creating-a-breakdown-or-pivot-table}

Dit type van lijst laat u statistieken tonen die op de gegevens in het gegevensbestand worden berekend.

De configuratie van deze types van rapporten is gelijkaardig aan die gebruikt voor de beschrijvende analysetovenaar. Raadpleeg [deze pagina](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-quantitative-distribution-template) voor meer informatie.

Raadpleeg voor meer informatie over het maken van een draaitabel [deze sectie](../../reporting/using/using-cubes-to-explore-data.md).
