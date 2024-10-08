---
product: campaign
title: Een tabel maken
description: Een tabel maken
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Reporting, Monitoring
exl-id: 05f76bdf-6dcd-4360-9e72-0ba6a4dd0d5e
source-git-commit: f90df5a5e5b3a2317d86ff2919560ded38f44f44
workflow-type: tm+mt
source-wordcount: '2512'
ht-degree: 1%

---

# Een tabel maken{#creating-a-table}



U kunt een lijst aan een rapport toevoegen om gegevens te tonen. Dit kan een draaitabel zijn die is gemaakt op basis van kubutemetingen, een lijst met groepen of een tabel met een uitsplitsing van waarden.

![](assets/s_advuser_report_page_activity_05.png)

## Een lijst met groepen maken {#creating-a-list-with-group}

Met een **[!UICONTROL List with group]** -typetabel kunt u gegevens in de tabel groeperen en er statistieken over produceren. U kunt bijvoorbeeld totalen en subtotalen maken voor de gegevens. Elke groep heeft zijn eigen kop-, detail- en voettekstregel.

>[!CAUTION]
>
>De **[!UICONTROL Page]** -activiteit die de tabel bevat, moet worden voorafgegaan door een **[!UICONTROL Query]** - of **[!UICONTROL Script]** -activiteit om de gegevens te verzamelen die in het rapport moeten worden geanalyseerd. Voor meer op deze activiteiten, verwijs naar [ verzamelen gegevens om ](../../reporting/using/collecting-data-to-analyze.md) en [ activiteit van het Manuscript ](../../reporting/using/advanced-functionalities.md#script-activity) te analyseren.

### Werkwijze {#operating-principle}

Het kan gebeuren dat u verschillende gegevenscategorieën tegelijk moet analyseren. Met een lijst met groepen kunt u gegevens combineren en statistieken maken over verschillende groepen gegevens in dezelfde tabel. Hiertoe kunt u een groep in de tabel maken.

In het volgende voorbeeld toont de groep alle campagnes in het gegevensbestand, de leveringen, en het aantal berichten die per levering en per campagne worden verzonden.

Het laat u een lijst maken van de campagnes (**[!UICONTROL Label (Campaign)]**, de lijst van leveringen (**[!UICONTROL Label]**) verbonden aan de campagne, en laat u het aantal berichten tellen die per levering (**[!UICONTROL Processed)]** worden verzonden, alvorens hen voor elke campagne (**[!UICONTROL Sum(@processed)]**) op te tellen.

![](assets/s_advuser_ergo_listgroup_005.png)

### Implementatiestappen {#implementation-steps}

Een volledig implementatievoorbeeld wordt hier verstrekt: [ het geval van het Gebruik: Creeer een rapport met een groepslijst ](#use-case--create-a-report-with-a-group-list).

Houd rekening met de volgende stappen om een tabel van het type &#39;Lijst met groep&#39; te maken:

1. Ga naar het rapportdiagram en plaats een **[!UICONTROL Query]** activiteit. Verwijs naar [ verzamelen gegevens om ](../../reporting/using/collecting-data-to-analyze.md) te analyseren.
1. Vul de brontabel in en selecteer de velden van de tabel die de statistieken betreffen.
1. Plaats een **[!UICONTROL Page]** -activiteit in het diagram. Voor meer op dit, verwijs naar [ Statische elementen ](../../reporting/using/creating-a-new-report.md#static-elements).
1. Voeg een **[!UICONTROL List with group]** typetabel op de pagina in.
1. Geef het gegevenspad op of de tabel die als gegevensbron in de query is geselecteerd.

   Deze stap is verplicht als u de velden in de brontabel later wilt herstellen en deze wilt invoegen in de cellen van de tabel.

1. De tabel en de inhoud ervan maken.
1. Geef het voltooide rapport weer op het tabblad **[!UICONTROL Preview]** . Vervolgens kunt u het rapport publiceren en het indien nodig exporteren naar een andere indeling. Voor meer op dit, verwijs naar [ Uitvoer een rapport ](../../reporting/using/actions-on-reports.md#exporting-a-report).

### Lijnen en kolommen toevoegen {#adding-lines-and-columns}

Een **[!UICONTROL List with group]** -tabel bevat standaard een koptekst, een detailregel en een voettekstregel.

De groep zelf bevat kop-, detail- en voettekstregel.

* **lijn van de Kopbal**: deze lijn laat u een titel aan de kolommen van de lijst geven.

  ![](assets/s_advuser_ergo_listgroup_003a.png)

* **de lijn van het Detail**: deze lijn bevat statistische waarden.

  ![](assets/s_advuser_ergo_listgroup_004.png)

* **Voettekstregel**: deze lijn laat u de totale waarden tonen.

  ![](assets/s_advuser_ergo_listgroup_003.png)

Lijnen en kolommen kunnen naar wens worden toegevoegd.

De groep kan op om het even welke lijn van de lijst worden geplaatst en omvat zijn eigen kopbal, detail en footer lijnen.

![](assets/s_advuser_ergo_listgroup_019.png)

**Lijn en kolom**: om een lijn of een kolom toe te voegen of te schrappen, naar een bestaande lijn of een kolom te gaan en het met de rechtermuisknop aanklikken menu te gebruiken.

![](assets/s_advuser_ergo_listgroup_006.png)

De aard van de lijn die u toevoegt, is afhankelijk van de locatie van de cursor. Als u bijvoorbeeld een koptekstregel wilt toevoegen, plaatst u de cursors op een koptekst en klikt u op **[!UICONTROL Add > A line above/below]** .

![](assets/s_advuser_ergo_listgroup_006a.png)

De breedte van de kolommen kan worden gewijzigd via het item **[!UICONTROL Column format]** .

**Groep**: om een groep toe te voegen, ga naar een lijn en selecteer het passende punt in het drop-down menu.

![](assets/s_advuser_ergo_listgroup_007.png)

### Celinhoud definiëren {#defining-cell-content}

Als u een cel van de tabel wilt bewerken en de inhoud en indeling ervan wilt definiëren, gaat u naar de cel en gebruikt u het snelmenu.

Gebruik het menu-item **[!UICONTROL Expression]** om de waarden te selecteren die u wilt weergeven.

![](assets/s_advuser_ergo_listgroup_010.png)

* Als u de waarden wilt invoegen die rechtstreeks in de tabel moeten worden geanalyseerd, selecteert u deze in de beschikbare velden.

  De lijst van beschikbare gebieden valt met de inhoud van de vraag vóór de lijst in de grafiek van de rapportconstructie samen.

  ![](assets/s_advuser_ergo_listgroup_011.png)

* Voer een label in voor een cel, bijvoorbeeld de koptekst.

  Hiervoor gebruikt u hetzelfde proces als voor het invoegen van een veld in de database, maar selecteert u geen expressie. Voer het label in het veld **[!UICONTROL Label]** in. Het zal worden getoond zoals is.

* Een aggregaat berekenen (gemiddelde waarde, som enz.) en in de cel weergeven.

  Hiervoor gebruikt u de menuvermelding **[!UICONTROL Aggregates]** en selecteert u de gewenste campagne.

  ![](assets/s_advuser_ergo_listgroup_008.png)

### Celindeling definiëren {#defining-cell-format}

![](assets/s_advuser_ergo_listgroup_017.png)

Als u de celindeling wilt definiëren, opent u met het menu **[!UICONTROL Cell format...]** alle opmaakopties die beschikbaar zijn voor de geselecteerde cel.

Met deze opties kunt u de uiteindelijke rendering van het rapport aanpassen en het lezen van informatie vereenvoudigen.

Gebruik het veld **[!UICONTROL Carriage return]** wanneer u gegevens exporteert naar Excel: selecteer de waarde **[!UICONTROL Yes]** om de regelterugloop te forceren. Deze waarde blijft behouden bij het exporteren. Voor meer op dit, verwijs naar [ Uitvoer een rapport ](../../reporting/using/actions-on-reports.md#exporting-a-report).

In het venster **[!UICONTROL Cell format]** hebt u toegang tot het volgende tabblad:

* Het tabblad **[!UICONTROL Value]**
* Het tabblad **[!UICONTROL Borders]**
* Het tabblad **[!UICONTROL Click]**
* Het tabblad **[!UICONTROL Extra]**

Op het tabblad **[!UICONTROL Value]** kunt u het lettertype en de verschillende waardetekenmerken wijzigen of een opmaak definiëren op basis van de aard ervan.

![](assets/s_advuser_ergo_listgroup_009.png)

De indeling wijzigt de weergave van gegevens: met de indelingen **[!UICONTROL Number]** , **[!UICONTROL Monetary]** en **[!UICONTROL Percentage]** kunt u bijvoorbeeld de cijfers rechts uitlijnen en decimalen weergeven.

Voorbeeld van hoe u een valutanotatie configureert: u kunt de valuta opgeven waarin de waarden worden uitgedrukt, kiezen of u duizenden wilt scheiden en negatieve waarden in rood wilt weergeven. De positie van het valutasymbool hangt af van de taal van de operator die in zijn profiel is gedefinieerd.

![](assets/s_advuser_ergo_listgroup_012.png)

Voorbeeld van configuratie voor datums: u kunt kiezen of u de tijd wilt weergeven.

![](assets/s_advuser_ergo_listgroup_013.png)

Het **lusje van Grenzen** laat u grenzen aan de lijnen en de kolommen in de lijst toevoegen. Als u randen toevoegt aan de cellen, kunnen er prestatieproblemen optreden wanneer u grote rapporten exporteert naar Excel.

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

Met het tabblad **[!UICONTROL Click]** kunt u een actie definiëren wanneer de gebruiker op de inhoud van een cel of van de tabel klikt.

In het onderstaande voorbeeld kunt u de tweede pagina van het rapport weergeven door op de waarde in de cel te klikken. Deze pagina bevat informatie over de levering in de cel.

![](assets/s_advuser_ergo_listgroup_015.png)

Het **Extra** lusje laat u visueel met uw gegevens, zoals een gekleurd teken of een waardebar verbinden. Het gekleurde teken wordt gebruikt wanneer de tabel als een legenda in een diagram wordt weergegeven. Voor meer op dit, verwijs naar het implementatievoorbeeld: [ Stap 5 - creeer de tweede pagina ](#step-5---create-the-second-page)

![](assets/s_advuser_ergo_listgroup_016.png)

## Hoofdlettergebruik: een rapport maken met een groepslijst {#use-case--create-a-report-with-a-group-list}

In dit voorbeeld gaan we een rapport van twee pagina&#39;s maken: de eerste pagina bevat de lijst en de totale leveringen per campagne, plus het aantal verzonden berichten. De namen van de levering zullen klikbare verbindingen zijn en zullen u toelaten om naar de tweede pagina van het rapport te gaan om de uitsplitsing van leveringen per e-maildomein voor de geselecteerde levering met een lijst en een grafiek te bekijken. Op de tweede pagina fungeert de tabel als een legenda voor het diagram.

![](assets/reporting_quick_start_report-final.png)

### Stap 1 - Een rapport maken {#step-1---create-a-report}

Maak een nieuw rapport over het campagneschema **[!UICONTROL Campaigns (nms)]** .

![](assets/s_advuser_report_listgroup_001.png)

Klik op **[!UICONTROL Save]** om het rapport te maken.

Ga naar de grafiek en voeg de eerste componenten toe die voor het ontwerpen van de rapportinhoud moeten worden gebruikt: een eerste vraag en een eerste pagina.

![](assets/reporting_quick_start_diagram.png)

### Stap 2 - creeer de eerste vraag {#step-2---create-the-first-query}

Met de eerste query kunt u leveringen verzamelen die aan elke campagne zijn gekoppeld. Het doel is een rapport weer te geven over de verschillende leveringen van de Adobe Campaign-database die aan elke campagne zijn gekoppeld.

Dubbelklik op de eerste query om deze te bewerken en pas vervolgens de volgende stappen toe om deze te configureren:

1. Begin door het schema te veranderen waarop de bron van de vraag wordt toegepast: selecteer het **[!UICONTROL Deliveries (nms)]** schema.
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

   Koppel een alias aan elk veld: dit wordt aanbevolen om de selectie te vergemakkelijken van gegevens uit de tabel die aan de eerste pagina van het rapport worden toegevoegd.

   In dit voorbeeld gebruiken we de volgende aliassen:

   * Label: **@label**
   * Primaire sleutel: **@deliveryId**
   * Label (campagne): **@label1**
   * Verwerkt: **@processing**
   * Externe sleutel van de koppeling &#39;Campaign&#39; (&#39;id&#39;): **@operationId**
   * Foutfrequentie: **@errorRatio**

1. Klik tweemaal op de knop **[!UICONTROL Next]** om de stap **[!UICONTROL Data filtering]** te doorlopen.

   Voeg een filtervoorwaarde toe om slechts de leveringen te verzamelen verbonden aan een campagne.

   De syntaxis van dit filter is als volgt: &quot;Externe sleutel van de koppeling &#39;Campagnes&#39; groter dan 0&quot;.

   ![](assets/reporting_quick_start_query_filter.png)

1. Klik op **[!UICONTROL Finish]** om deze voorwaarden op te slaan en klik vervolgens op **[!UICONTROL Ok]** om de query-editor te sluiten.

### Stap 3: De eerste pagina maken {#step-3--create-the-first-page}

In deze stap, gaan wij de eerste pagina van het rapport vormen. Voer de volgende stappen uit om het te configureren:

1. Open de **[!UICONTROL Page]** activiteit en ga zijn titel, bijvoorbeeld **Leveringen** in dit geval in.

   ![](assets/s_advuser_report_listgroup_003.png)

1. Voeg een lijst met groepen in via de werkbalk en voer het label ervan in, bijvoorbeeld: Lijst met leveringen per campagne.

   ![](assets/s_advuser_report_listgroup_004.png)

1. Klik op de koppeling **[!UICONTROL Table data XPath...]** en selecteer de leveringskoppeling, d.w.z. `[query/delivery]` .

   ![](assets/s_advuser_report_listgroup_005.png)

1. Klik op de tab **[!UICONTROL Data]** en wijzig de indeling van de tabel: voeg drie kolommen aan de rechterkant toe.

   ![](assets/s_advuser_report_listgroup_006.png)

1. Voeg een groep toe.

   ![](assets/s_advuser_report_listgroup_008.png)

   Met deze groep kunt u campagnes en de bijbehorende leveringen groeperen.

1. In het groepsvenster, verwijs de **Buitenlandse sleutel van de verbinding van de &quot;Campagne&quot;** en sluit het venster.

   ![](assets/s_advuser_report_listgroup_007.png)

1. Bewerk de eerste cel van de groepsheader en voeg het veld **[!UICONTROL Label]** van de campagnes in als een expressie.

   ![](assets/s_advuser_report_listgroup_009.png)

1. Bewerk de tweede cel van de detailregel en selecteer de leveringen **[!UICONTROL Label]** .

   ![](assets/s_advuser_report_listgroup_011.png)

1. Bewerk de opmaak van deze cel en open het tabblad **[!UICONTROL Click]** . Configureer de juiste opties zodat wanneer de gebruikers op de naam van een levering klikken, deze in hetzelfde venster wordt geopend.

   ![](assets/s_advuser_report_listgroup_0111.png)

   Selecteer hiertoe een **[!UICONTROL Next page]** -tekstactie en selecteer **[!UICONTROL In the same window]** als een open optie.

   ![](assets/s_advuser_report_listgroup_0112.png)

1. Klik in de onderste sectie van het venster op **[!UICONTROL Add]** en geef het **`/vars/selectedDelivery`** path en de **[!UICONTROL @deliveryId]** -expressie op die overeenkomen met de alias van de primaire sleutel van de levering, zoals gedefinieerd in de eerder gemaakte query. Met deze formule hebt u toegang tot de geselecteerde levering.

   ![](assets/s_advuser_report_listgroup_010.png)

1. Bewerk de tweede cel van de voettekstregel van de groep en voer **[!UICONTROL Total per campaign]** in als een label.

   ![](assets/s_advuser_report_listgroup_012.png)

1. Bewerk de derde cel van de koptekstregel van de groep en voer **[!UICONTROL Number of messages sent]** in als een label.

   ![](assets/s_advuser_report_listgroup_013.png)

   Deze informatie valt samen met de kolomtitel.

1. Bewerk de derde cel van de detailregel en selecteer de verwerkte berichtindicator als een expressie.

   ![](assets/s_advuser_report_listgroup_014.png)

1. Bewerk de derde cel van de voettekstregel van de groep, selecteer de verwerkte leveringsindicator en pas het aggregaat **[!UICONTROL Sum]** erop toe.

   ![](assets/s_advuser_report_listgroup_015.png)

1. Bewerk de vierde cel van de detaillijn en selecteer het **foutentarief van de foutenlevering** als uitdrukking.

   ![](assets/s_advuser_report_listgroup_016.png)

1. Selecteer deze cel om een waardebalk weer te geven die de frequentie van de leveringsfout weergeeft.

   Hiervoor opent u de celindeling en gaat u naar het tabblad **[!UICONTROL More]** . Selecteer de vermelding **[!UICONTROL Value bar]** in de vervolgkeuzelijst en selecteer de optie **[!UICONTROL Hide the cell value]** .

   ![](assets/s_advuser_report_listgroup_023.png)

   U kunt nu een rendering van het rapport weergeven. Klik op het tabblad **[!UICONTROL Preview]** en selecteer de optie **[!UICONTROL Global]** : hier ziet u de lijst met alle leveringen in de Adobe Campaign-database die aan een campagne zijn gekoppeld.

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

### Stap 4 - Maak de tweede query {#step-4---create-the-second-query}

Wij willen een tweede vraag en een tweede pagina toevoegen om de details van een levering te tonen wanneer de gebruiker van het rapport op het klikt. Alvorens de vraag toe te voegen, geef de pagina uit u hebt gecreeerd en laat de uitgaande overgang toe zodat het aan de vraag kan worden verbonden.

1. Voeg een nieuwe query toe na de **[!UICONTROL Page]** -activiteit en bewerk het schema: selecteer het **[!UICONTROL Recipient delivery logs]** -schema.

   ![](assets/reporting_quick_start_query-2.png)

1. Bewerk de query en definieer de uitvoerkolommen. Als u het aantal leveringen per e-maildomein wilt weergeven, moet u:

   * Bereken de som van de primaire sleutels om het aantal leveringslogboeken te tellen:

     ![](assets/reporting_quick_start_query-2_count.png)

   * e-maildomeinen van ontvangers en groepsinformatie over dit veld verzamelen: hiervoor selecteert u de optie **[!UICONTROL Group]** in de kolom met domeinnamen.

   ![](assets/reporting_quick_start_query-2_filter.png)

   Koppel de volgende aliassen aan de velden:

   * count(primaire sleutel): **@count**
   * E-maildomein (ontvanger): **@domein**

     ![](assets/reporting_quick_start_query-2_alias.png)

1. Klik tweemaal op de knop **[!UICONTROL Next]** : hiermee gaat u naar de stap **[!UICONTROL Data filtering]** .

   Voeg een filtervoorwaarde toe om slechts de informatie te verzamelen verbonden aan de geselecteerde levering.

   De syntaxis is als volgt: de buitenlandse sleutel van de koppeling Aflevering is gelijk aan de waarde van de instelling `$([vars/selectedDelivery])`

   ![](assets/s_advuser_report_listgroup_017.png)

1. Sluit het venster van de vraagconfiguratie en voeg een pagina aan de grafiek toe, enkel na de tweede vraag.

### Stap 5 - Maak de tweede pagina {#step-5---create-the-second-page}

1. Bewerk de pagina en ga zijn etiket in: **E-maildomeinen**.
1. Schakel de optie **[!UICONTROL Enable output transitions]** uit: dit is de laatste pagina van het rapport en wordt niet gevolgd door een andere activiteit.

   ![](assets/s_advuser_report_listgroup_028.png)

1. Voeg een nieuwe lijst met een groep toe gebruikend het met de rechtermuisknop-klik menu en roep het **E-maildomeinen per ontvanger**.
1. Klik op **[!UICONTROL Table data XPath...]** en selecteer de koppeling **[!UICONTROL Recipient delivery logs]** .

   ![](assets/s_advuser_report_listgroup_029.png)

1. Pas de tabel op het tabblad **[!UICONTROL Data]** als volgt aan:

   * Voeg twee kolommen aan de rechterkant toe.
   * Voeg in de eerste cel van de detailregel de expressie **[!UICONTROL rowNum()-1]** toe om het aantal regels te tellen. Wijzig vervolgens de indeling van de cel: selecteer **[!UICONTROL Color tab]** op het tabblad **[!UICONTROL Extra]** en klik op **[!UICONTROL Ok]** .

     ![](assets/s_advuser_report_listgroup_018.png)

     Deze configuratie zal u toelaten om de lijst als titel voor de grafiek te gebruiken.

   * Voeg in de tweede cel van de detailregel de expressie **[!UICONTROL Email domain(Recipient)]** toe.
   * Voeg in de derde cel van de detailregel de expressie **[!UICONTROL count(primary key)]** toe.

   ![](assets/s_advuser_report_listgroup_019.png)

1. Voeg een cirkeldiagram aan de pagina toe gebruikend het met de rechtermuisknop-klik menu en wijs het **E-mail domeinen** etiket aan het toe. Voor meer informatie, verwijs naar [ types en varianten van de Grafiek ](../../reporting/using/creating-a-chart.md#chart-types-and-variants).
1. Klik op de koppeling **[!UICONTROL Variants]** en schakel de opties **[!UICONTROL Display label]** en **[!UICONTROL Display caption]** uit.
1. Controleer of er geen waarde sortering is geconfigureerd. Raadpleeg [deze sectie](../../reporting/using/processing-a-report.md#configuring-the-layout-of-a-descriptive-analysis-report) voor meer informatie.

   ![](assets/s_advuser_report_listgroup_0191.png)

1. Wijzig op het tabblad **[!UICONTROL Data]** de gegevensbron: selecteer **[!UICONTROL Context data]** in de vervolgkeuzelijst.

   ![](assets/s_advuser_report_listgroup_020.png)

1. Klik vervolgens op **[!UICONTROL Advanced settings]** en selecteer de koppeling naar de leveringslogboeken van de ontvanger.

   ![](assets/s_advuser_report_listgroup_0201.png)

1. Selecteer in de sectie **[!UICONTROL Chart type]** de variabele **[!UICONTROL Email domain]** .
1. Voeg vervolgens de uit te voeren berekening toe: selecteer de som als een operator.

   ![](assets/s_advuser_report_listgroup_0202.png)

1. Klik op de knop **[!UICONTROL Detail]** om het veld te selecteren waarop het aantal betrekking heeft en sluit vervolgens het configuratievenster.

   ![](assets/s_advuser_report_listgroup_030.png)

1. Sla het rapport op.

   Uw pagina is nu geconfigureerd.

### Stap 6 - Bekijk het rapport {#step-6---viewing-the-report}

Als u het resultaat van deze configuratie wilt weergeven, klikt u op de tab **[!UICONTROL Preview]** en selecteert u de optie **[!UICONTROL Global]** .

De eerste pagina van uw rapport bevat de lijst met alle leveringen die in de database zijn opgenomen.

![](assets/s_advuser_report_listgroup_021.png)

Als u op de koppeling van een van deze leveringen klikt, wordt in het diagram de indeling van e-maildomeinen voor deze levering weergegeven. U bevindt zich nu op de tweede pagina van het rapport en kunt terugkeren naar de vorige pagina door op de desbetreffende knop te klikken.

![](assets/s_advuser_report_listgroup_022.png)

## Een splitsings- of draaitabel maken {#creating-a-breakdown-or-pivot-table}

Dit type van lijst laat u statistieken tonen die op de gegevens in het gegevensbestand worden berekend.

De configuratie van deze types van rapporten is gelijkaardig aan die gebruikt voor de beschrijvende analysemedewerker. Raadpleeg [deze pagina](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-quantitative-distribution-template) voor meer informatie.

Voor meer bij het creëren van een spillijst, verwijs naar [ deze sectie ](../../reporting/using/ac-cubes.md).
