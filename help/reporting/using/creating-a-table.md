---
solution: Campaign Classic
product: campaign
title: Een tabel maken
description: Een tabel maken
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2495'
ht-degree: 1%

---


# Een tabel maken{#creating-a-table}

U kunt een lijst aan een rapport toevoegen om gegevens te tonen. Dit kan een draaitabel zijn die is gemaakt op basis van kubutemetingen, een lijst met groepen of een tabel met een uitsplitsing van waarden.

![](assets/s_advuser_report_page_activity_05.png)

## Een lijst maken met groep {#creating-a-list-with-group}

Met een typetabel **[!UICONTROL List with group]** kunt u gegevens in de tabel groeperen en er statistieken over produceren. U kunt bijvoorbeeld totalen en subtotalen maken voor de gegevens. Elke groep heeft zijn eigen kop-, detail- en voettekstregel.

>[!CAUTION]
>
>De **[!UICONTROL Page]**-activiteit die de tabel bevat, moet worden voorafgegaan door een **[!UICONTROL Query]**- of **[!UICONTROL Script]**-activiteit om de gegevens te verzamelen die in het rapport moeten worden geanalyseerd. Raadpleeg [Gegevens verzamelen voor analyse](../../reporting/using/collecting-data-to-analyze.md) en [Scriptactiviteit](../../reporting/using/advanced-functionalities.md#script-activity) voor meer informatie over deze activiteiten.

### Werkwijze {#operating-principle}

Het kan gebeuren dat u verschillende gegevenscategorieën tegelijk moet analyseren. Met een lijst met groepen kunt u gegevens combineren en statistieken maken over verschillende groepen gegevens in dezelfde tabel. Hiertoe kunt u een groep in de tabel maken.

In het volgende voorbeeld toont de groep alle campagnes in het gegevensbestand, de leveringen, en het aantal berichten die per levering en per campagne worden verzonden.

Het laat u een lijst maken van de campagnes (**[!UICONTROL Label (Campaign)]**, de lijst van leveringen (**[!UICONTROL Label]**) verbonden aan de campagne, en laat u het aantal berichten tellen die per levering worden verzonden (**[!UICONTROL Processed)]**, alvorens hen voor elke campagne (**[!UICONTROL Sum(@processed)]**) toe te voegen.

![](assets/s_advuser_ergo_listgroup_005.png)

### Implementatiestappen {#implementation-steps}

Hier vindt u een volledig voorbeeld van implementatie: [Hoofdlettergebruik: Creeer een rapport met een groepslijst](#use-case--create-a-report-with-a-group-list).

Houd rekening met de volgende stappen om een tabel van het type &#39;Lijst met groep&#39; te maken:

1. Ga naar de rapportgrafiek en plaats een **[!UICONTROL Query]** activiteit. Zie [Gegevens verzamelen om te analyseren](../../reporting/using/collecting-data-to-analyze.md).
1. Vul de brontabel in en selecteer de velden van de tabel die de statistieken betreffen.
1. Plaats een **[!UICONTROL Page]** activiteit in de grafiek. Raadpleeg [Statische elementen](../../reporting/using/creating-a-new-report.md#static-elements) voor meer informatie.
1. Voeg een teksttabel **[!UICONTROL List with group]** in op de pagina.
1. Geef het gegevenspad op of de tabel die als gegevensbron in de query is geselecteerd.

   Deze stap is verplicht als u de velden in de brontabel later wilt herstellen en deze wilt invoegen in de cellen van de tabel.

1. De tabel en de inhoud ervan maken.
1. Geef het voltooide rapport weer op het tabblad **[!UICONTROL Preview]**. Vervolgens kunt u het rapport publiceren en het indien nodig exporteren naar een andere indeling. Voor meer op dit, verwijs naar [Exporting a report](../../reporting/using/actions-on-reports.md#exporting-a-report).

### Lijnen en kolommen {#adding-lines-and-columns} toevoegen

Standaard bevat een tabel van het type **[!UICONTROL List with group]** een koptekst, een detailregel en een voettekstregel.

De groep zelf bevat kop-, detail- en voettekstregel.

* **Koptekstregel**: op deze regel geeft u een titel aan de kolommen van de tabel.

   ![](assets/s_advuser_ergo_listgroup_003a.png)

* **Detaillijn**: deze regel bevat statistische waarden .

   ![](assets/s_advuser_ergo_listgroup_004.png)

* **Voettekstregel**: op deze regel kunt u de totale waarden weergeven.

   ![](assets/s_advuser_ergo_listgroup_003.png)

Lijnen en kolommen kunnen naar wens worden toegevoegd.

De groep kan op om het even welke lijn van de lijst worden geplaatst en omvat zijn eigen kopbal, detail en footer lijnen.

![](assets/s_advuser_ergo_listgroup_019.png)

**Regel en kolom**: als u een regel of kolom wilt toevoegen of verwijderen, gaat u naar een bestaande regel of kolom en gebruikt u het snelmenu.

![](assets/s_advuser_ergo_listgroup_006.png)

De aard van de lijn die u toevoegt, is afhankelijk van de locatie van de cursor. Als u bijvoorbeeld een koptekstregel wilt toevoegen, plaatst u de cursors op een koptekst en klikt u op **[!UICONTROL Add > A line above/below]**.

![](assets/s_advuser_ergo_listgroup_006a.png)

De breedte van de kolommen kan worden gewijzigd via het item **[!UICONTROL Column format]**.

**Groep**: om een groep toe te voegen, ga naar een lijn en selecteer het passende punt in het drop-down menu.

![](assets/s_advuser_ergo_listgroup_007.png)

### Celinhoud definiëren {#defining-cell-content}

Als u een cel van de tabel wilt bewerken en de inhoud en indeling ervan wilt definiëren, gaat u naar de cel en gebruikt u het snelmenu.

Gebruik de **[!UICONTROL Expression]** menuingang om de waarden te selecteren aan vertoning.

![](assets/s_advuser_ergo_listgroup_010.png)

* Als u de waarden wilt invoegen die rechtstreeks in de tabel moeten worden geanalyseerd, selecteert u deze in de beschikbare velden.

   De lijst van beschikbare gebieden valt met de inhoud van de vraag vóór de lijst in de grafiek van de rapportconstructie samen.

   ![](assets/s_advuser_ergo_listgroup_011.png)

* Voer een label in voor een cel, bijvoorbeeld de koptekst.

   Hiervoor gebruikt u hetzelfde proces als voor het invoegen van een veld in de database, maar selecteert u geen expressie. Typ het label in het veld **[!UICONTROL Label]**. Het zal worden getoond zoals is.

* Een aggregaat berekenen (gemiddelde waarde, som enz.) en in de cel weergeven.

   Hiervoor gebruikt u de menuvermelding **[!UICONTROL Aggregates]** en selecteert u de gewenste campagne.

   ![](assets/s_advuser_ergo_listgroup_008.png)

### Celindeling {#defining-cell-format} definiëren

![](assets/s_advuser_ergo_listgroup_017.png)

Als u de celindeling wilt definiëren, opent u met het menu **[!UICONTROL Cell format...]** alle opmaakopties die beschikbaar zijn voor de geselecteerde cel.

Met deze opties kunt u de uiteindelijke rendering van het rapport aanpassen en het lezen van informatie vereenvoudigen.

Gebruik het veld **[!UICONTROL Carriage return]** bij het exporteren van gegevens naar Excel: Selecteer de waarde **[!UICONTROL Yes]** om de harde return te forceren. Deze waarde blijft behouden bij het exporteren. Voor meer op dit, verwijs naar [Exporting a report](../../reporting/using/actions-on-reports.md#exporting-a-report).

In het venster **[!UICONTROL Cell format]** hebt u toegang tot het volgende tabblad:

* De tab **[!UICONTROL Value]**
* De tab **[!UICONTROL Borders]**
* De tab **[!UICONTROL Click]**
* De tab **[!UICONTROL Extra]**

Op het tabblad **[!UICONTROL Value]** kunt u het lettertype en de verschillende waardetekenmerken wijzigen of een opmaak definiëren op basis van de aard ervan.

![](assets/s_advuser_ergo_listgroup_009.png)

De indeling wijzigt de weergave van gegevens: Met de indelingen **[!UICONTROL Number]**, **[!UICONTROL Monetary]** en **[!UICONTROL Percentage]** kunt u bijvoorbeeld de cijfers rechts uitlijnen en decimalen weergeven.

Voorbeeld van het configureren van een valutaopmaak: u kunt opgeven in welke valuta de waarden worden uitgedrukt, kiezen of duizenden worden gescheiden en negatieve waarden in rood worden weergegeven. De positie van het valutasymbool hangt af van de taal van de operator die in zijn profiel is gedefinieerd.

![](assets/s_advuser_ergo_listgroup_012.png)

Voorbeeld van configuratie voor datums: U kunt kiezen of u de tijd wilt weergeven.

![](assets/s_advuser_ergo_listgroup_013.png)

Met het tabblad **Randen** kunt u randen toevoegen aan de lijnen en kolommen in de tabel. Als u randen toevoegt aan de cellen, kunnen er prestatieproblemen optreden wanneer u grote rapporten exporteert naar Excel.

![](assets/s_advuser_ergo_listgroup_014.png)

Indien nodig, kunt u grenzen in het lijstmalplaatje (**[!UICONTROL Administration > Configuration > Form rendering]**) bepalen.

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

Met het tabblad **[!UICONTROL Click]** kunt u een handeling definiëren wanneer de gebruiker op de inhoud van een cel of van de tabel klikt.

In het onderstaande voorbeeld kunt u de tweede pagina van het rapport weergeven door op de waarde in de cel te klikken: het zal informatie over de levering in de cel bevatten .

![](assets/s_advuser_ergo_listgroup_015.png)

Met het tabblad **Extra** kunt u een visuele koppeling maken naar uw gegevens, zoals een gekleurd teken of een waardebalk. Het gekleurde teken wordt gebruikt wanneer de tabel als een legenda in een diagram wordt weergegeven. Raadpleeg voor meer informatie het voorbeeld van de implementatie: [Stap 5 - Maak de tweede pagina](#step-5---create-the-second-page)

![](assets/s_advuser_ergo_listgroup_016.png)

## Hoofdlettergebruik: Een rapport maken met een groeplijst {#use-case--create-a-report-with-a-group-list}

In dit voorbeeld gaan we een rapport van twee pagina&#39;s maken: de eerste pagina bevat de lijst en het totale aantal leveringen per campagne , alsmede het aantal verzonden berichten . De namen van de levering zullen klikbare verbindingen zijn en zullen u toelaten om naar de tweede pagina van het rapport te gaan om de uitsplitsing van leveringen per e-maildomein voor de geselecteerde levering met een lijst en een grafiek te bekijken. Op de tweede pagina fungeert de tabel als een legenda voor het diagram.

![](assets/reporting_quick_start_report-final.png)

### Stap 1 - creeer een rapport {#step-1---create-a-report}

Creeer een nieuw rapport dat het campagneschema, **[!UICONTROL Campaigns (nms)]** behandelt.

![](assets/s_advuser_report_listgroup_001.png)

Klik **[!UICONTROL Save]** om het rapport tot stand te brengen.

Ga naar de grafiek en voeg de eerste componenten toe die voor het ontwerpen van de rapportinhoud moeten worden gebruikt: een eerste query en een eerste pagina.

![](assets/reporting_quick_start_diagram.png)

### Stap 2 - creeer de eerste vraag {#step-2---create-the-first-query}

Met de eerste query kunt u leveringen verzamelen die aan elke campagne zijn gekoppeld. Het doel is een rapport weer te geven over de verschillende leveringen van de Adobe Campaign-database die aan elke campagne zijn gekoppeld.

Dubbelklik op de eerste query om deze te bewerken en pas vervolgens de volgende stappen toe om deze te configureren:

1. Begin door het schema te veranderen waarop de bron van de vraag wordt toegepast: Selecteer het schema **[!UICONTROL Deliveries (nms)]**.
1. Klik op de koppeling **[!UICONTROL Edit query]** en geef de geavanceerde velden weer.

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
   * Verwerkt: **@processing**
   * Externe sleutel van de koppeling &#39;Campaign&#39; (&#39;id&#39;): **@operationId**
   * Foutfrequentie: **@errorRatio**


1. Klik tweemaal op de knop **[!UICONTROL Next]** om de stap **[!UICONTROL Data filtering]** te doorlopen.

   Voeg een filtervoorwaarde toe om slechts de leveringen te verzamelen verbonden aan een campagne.

   De syntaxis van dit filter is als volgt: &quot;De buitenlandse sleutel van de verbinding &quot;Campaigns&quot;groter dan 0&quot;.

   ![](assets/reporting_quick_start_query_filter.png)

1. Klik **[!UICONTROL Finish]** om deze voorwaarden te bewaren, dan klik **[!UICONTROL Ok]** om de vraagredacteur te sluiten.

### Stap 3: De eerste pagina {#step-3--create-the-first-page} maken

In deze stap, gaan wij de eerste pagina van het rapport vormen. Voer de volgende stappen uit om het te configureren:

1. Open de **[!UICONTROL Page]** activiteit en ga zijn titel in, bijvoorbeeld **Leveringen** in dit geval.

   ![](assets/s_advuser_report_listgroup_003.png)

1. Voeg een lijst met groepen in via de werkbalk en voer het label ervan in, bijvoorbeeld: Lijst van leveringen per campagne.

   ![](assets/s_advuser_report_listgroup_004.png)

1. Klik op de koppeling **[!UICONTROL Table data XPath...]** en selecteer de leveringskoppeling, dat wil zeggen: `[query/delivery]`.

   ![](assets/s_advuser_report_listgroup_005.png)

1. Klik op de tab **[!UICONTROL Data]** en wijzig de indeling van de tabel: Voeg drie kolommen aan de rechterkant toe.

   ![](assets/s_advuser_report_listgroup_006.png)

1. Voeg een groep toe.

   ![](assets/s_advuser_report_listgroup_008.png)

   Met deze groep kunt u campagnes en de bijbehorende leveringen groeperen.

1. Verwijs in het groepsvenster **Buitenlandse sleutel van de &quot;Campagne&quot;verbinding** en sluit het venster.

   ![](assets/s_advuser_report_listgroup_007.png)

1. Bewerk de eerste cel van de groepsheader en voeg het veld **[!UICONTROL Label]** van de campagnes in als een expressie.

   ![](assets/s_advuser_report_listgroup_009.png)

1. Bewerk de tweede cel van de detailregel en selecteer de leveringen **[!UICONTROL Label]**.

   ![](assets/s_advuser_report_listgroup_011.png)

1. Bewerk de opmaak van deze cel en open het tabblad **[!UICONTROL Click]**. Configureer de juiste opties zodat wanneer de gebruikers op de naam van een levering klikken, deze in hetzelfde venster wordt geopend.

   ![](assets/s_advuser_report_listgroup_0111.png)

   Om dit te doen, selecteer **[!UICONTROL Next page]** typeactie en selecteer **[!UICONTROL In the same window]** als open optie.

   ![](assets/s_advuser_report_listgroup_0112.png)

1. Klik in de onderste sectie van het venster op **[!UICONTROL Add]** en geef het pad **`/vars/selectedDelivery`** en de expressie **[!UICONTROL @deliveryId]** op die overeenkomen met de alias van de primaire sleutel van de levering, zoals gedefinieerd in de eerder gemaakte query. Met deze formule hebt u toegang tot de geselecteerde levering.

   ![](assets/s_advuser_report_listgroup_010.png)

1. Bewerk de tweede cel van de voettekstregel van de groep en typ **[!UICONTROL Total per campaign]** als label.

   ![](assets/s_advuser_report_listgroup_012.png)

1. Bewerk de derde cel van de koptekstregel van de groep en typ **[!UICONTROL Number of messages sent]** als label.

   ![](assets/s_advuser_report_listgroup_013.png)

   Deze informatie valt samen met de kolomtitel.

1. Bewerk de derde cel van de detailregel en selecteer de verwerkte berichtindicator als een expressie.

   ![](assets/s_advuser_report_listgroup_014.png)

1. Bewerk de derde cel van de voettekstregel van de groep, selecteer de verwerkte leveringsindicator en pas het **[!UICONTROL Sum]** aggregaat op het toe.

   ![](assets/s_advuser_report_listgroup_015.png)

1. Bewerk de vierde cel van de detailregel en selecteer de **error delivery error rate** als een expressie.

   ![](assets/s_advuser_report_listgroup_016.png)

1. Selecteer deze cel om een waardebalk weer te geven die de frequentie van de leveringsfout vertegenwoordigt.

   Hiervoor opent u de celindeling en gaat u naar het tabblad **[!UICONTROL More]**. Selecteer de **[!UICONTROL Value bar]** ingang in de drop-down lijst en selecteer **[!UICONTROL Hide the cell value]** optie.

   ![](assets/s_advuser_report_listgroup_023.png)

   U kunt nu een rendering van het rapport weergeven. Klik op de tab **[!UICONTROL Preview]** en selecteer de optie **[!UICONTROL Global]**: Hier ziet u een lijst met alle leveringen in de Adobe Campaign-database die aan een campagne zijn gekoppeld.

   ![](assets/s_advuser_report_listgroup_025.png)

   We raden u aan het tabblad **[!UICONTROL Preview]** te gebruiken om ervoor te zorgen dat de gegevens in uw tabel correct zijn geselecteerd en geconfigureerd. Zodra dit wordt gedaan, kunt u aan het formatteren van uw lijst verdergaan.

1. Pas de stijl **[!UICONTROL Bold]** toe op de cellen die het totaal per campagne en het totale aantal verwerkte berichten tonen.

   ![](assets/s_advuser_report_listgroup_024.png)

1. Klik op de eerste cel van de groepsheader lijn, die de campagnenaam toont, en selecteer **[!UICONTROL Edit > Merge to right]**.

   ![](assets/s_advuser_report_listgroup_026.png)

   Wanneer de eerste twee cellen van de groepsheader worden samengevoegd, worden de titel van de campagne en de lijst met hiermee verbonden leveringen opnieuw uitgelijnd.

   ![](assets/s_advuser_report_listgroup_027.png)

   >[!CAUTION]
   >
   >We raden u aan te wachten tot uw rapport is samengesteld voordat u cellen samenvoegt, aangezien samenvoegen onomkeerbaar is.

### Stap 4 - creeer de tweede vraag {#step-4---create-the-second-query}

Wij willen een tweede vraag en een tweede pagina toevoegen om de details van een levering te tonen wanneer de gebruiker van het rapport op het klikt. Alvorens de vraag toe te voegen, geef de pagina uit u hebt gecreeerd en laat de uitgaande overgang toe zodat het aan de vraag kan worden verbonden.

1. Voeg een nieuwe vraag na **[!UICONTROL Page]** activiteit toe en geef zijn schema uit: Selecteer het schema **[!UICONTROL Recipient delivery logs]**.

   ![](assets/reporting_quick_start_query-2.png)

1. Bewerk de query en definieer de uitvoerkolommen. Als u het aantal leveringen per e-maildomein wilt weergeven, moet u:

   * Bereken de som van de primaire sleutels om het aantal leveringslogboeken te tellen:

      ![](assets/reporting_quick_start_query-2_count.png)

   * e-maildomeinen van ontvangers en groepsgegevens in dit veld verzamelen: om dit te doen, selecteer **[!UICONTROL Group]** optie in de kolom van de domeinnaam.

   ![](assets/reporting_quick_start_query-2_filter.png)

   Koppel de volgende aliassen aan de velden:

   * count(primaire sleutel): **@count**
   * E-maildomein (ontvanger): **@domain**

      ![](assets/reporting_quick_start_query-2_alias.png)


1. Klik tweemaal op de knop **[!UICONTROL Next]**: Hiermee gaat u naar de stap **[!UICONTROL Data filtering]**.

   Voeg een filtervoorwaarde toe om slechts de informatie te verzamelen verbonden aan de geselecteerde levering.

   De syntaxis is als volgt: De buitenlandse sleutel van de verbinding van de &quot;Levering&quot;is de waarde van het plaatsen `$([vars/selectedDelivery])`

   ![](assets/s_advuser_report_listgroup_017.png)

1. Sluit het venster van de vraagconfiguratie en voeg een pagina aan de grafiek toe, enkel na de tweede vraag.

### Stap 5 - Maak de tweede pagina {#step-5---create-the-second-page}

1. Bewerk de pagina en voer het label ervan in: **E-maildomeinen**.
1. Schakel de optie **[!UICONTROL Enable output transitions]** uit: dit is de laatste bladzijde van het verslag en zal niet door een andere activiteit worden gevolgd .

   ![](assets/s_advuser_report_listgroup_028.png)

1. Voeg een nieuwe lijst met een groep toe gebruikend het met de rechtermuisknop-klik menu en roep het **E-maildomeinen per ontvanger**.
1. Klik op **[!UICONTROL Table data XPath...]** en selecteer de koppeling **[!UICONTROL Recipient delivery logs]**.

   ![](assets/s_advuser_report_listgroup_029.png)

1. Pas op het tabblad **[!UICONTROL Data]** de tabel als volgt aan:

   * Voeg twee kolommen aan de rechterkant toe.
   * Voeg in de eerste cel van de detailregel de expressie **[!UICONTROL rowNum()-1]** toe om het aantal regels te tellen. Wijzig vervolgens de indeling van de cel: Selecteer **[!UICONTROL Color tab]** op het tabblad **[!UICONTROL Extra]** en klik **[!UICONTROL Ok]**.

      ![](assets/s_advuser_report_listgroup_018.png)

      Deze configuratie zal u toelaten om de lijst als titel voor de grafiek te gebruiken.

   * Voeg in de tweede cel van de detailregel de expressie **[!UICONTROL Email domain(Recipient)]** toe.
   * Voeg in de derde cel van de detailregel de expressie **[!UICONTROL count(primary key)]** toe.

   ![](assets/s_advuser_report_listgroup_019.png)

1. Voeg een cirkeldiagram aan de pagina toe gebruikend het met de rechtermuisknop-klik menu en wijs **E-mail domeinen** etiket aan het toe. Voor meer informatie, verwijs naar [de types en de varianten van de Grafiek](../../reporting/using/creating-a-chart.md#chart-types-and-variants).
1. Klik op de koppeling **[!UICONTROL Variants]** en hef de selectie van de opties **[!UICONTROL Display label]** en **[!UICONTROL Display caption]** op.
1. Controleer of er geen waarde sortering is geconfigureerd. Raadpleeg [deze sectie](../../reporting/using/processing-a-report.md#configuring-the-layout-of-a-descriptive-analysis-report) voor meer informatie.

   ![](assets/s_advuser_report_listgroup_0191.png)

1. Wijzig op het tabblad **[!UICONTROL Data]** de gegevensbron: Selecteer **[!UICONTROL Context data]** in de vervolgkeuzelijst.

   ![](assets/s_advuser_report_listgroup_020.png)

1. Dan klik **[!UICONTROL Advanced settings]** en selecteer de verbinding aan de ontvankelijke leveringslogboeken.

   ![](assets/s_advuser_report_listgroup_0201.png)

1. Selecteer in de sectie **[!UICONTROL Chart type]** de variabele **[!UICONTROL Email domain]**.
1. Voeg vervolgens de uit te voeren berekening toe: selecteert de som als een operator.

   ![](assets/s_advuser_report_listgroup_0202.png)

1. Klik op de knop **[!UICONTROL Detail]** om het veld te selecteren waarop het aantal betrekking heeft en sluit vervolgens het configuratievenster.

   ![](assets/s_advuser_report_listgroup_030.png)

1. Sla het rapport op.

   Uw pagina is nu geconfigureerd.

### Stap 6 - het bekijken van het rapport {#step-6---viewing-the-report}

Als u het resultaat van deze configuratie wilt weergeven, klikt u op het tabblad **[!UICONTROL Preview]** en selecteert u de optie **[!UICONTROL Global]**.

De eerste pagina van uw rapport bevat de lijst met alle leveringen die in de database zijn opgenomen.

![](assets/s_advuser_report_listgroup_021.png)

Als u op de koppeling van een van deze leveringen klikt, wordt in het diagram de indeling van e-maildomeinen voor deze levering weergegeven. U bevindt zich nu op de tweede pagina van het rapport en kunt terugkeren naar de vorige pagina door op de desbetreffende knop te klikken.

![](assets/s_advuser_report_listgroup_022.png)

## Een splitsings- of draaitabel {#creating-a-breakdown-or-pivot-table} maken

Dit type van lijst laat u statistieken tonen die op de gegevens in het gegevensbestand worden berekend.

De configuratie van deze types van rapporten is gelijkaardig aan die gebruikt voor de beschrijvende analysetovenaar. Raadpleeg [deze pagina](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-quantitative-distribution-template) voor meer informatie.

Raadpleeg [deze sectie](../../reporting/using/using-cubes-to-explore-data.md) voor meer informatie over het maken van een draaitabel.
