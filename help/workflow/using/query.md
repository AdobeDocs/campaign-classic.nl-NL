---
product: campaign
title: Query
description: Meer informatie over de activiteit van de Query-workflow
feature: Workflows, Targeting Activity, Query Editor
exl-id: 20d03627-cd56-46da-bc02-73b48a02a350
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1631'
ht-degree: 0%

---

# Query{#query}



## Een query maken {#creating-a-query}

Met een query kunt u een doel selecteren op basis van criteria. U kunt een segmentcode aan het vraagresultaat associëren en extra gegevens opnemen in het.
Raadpleeg dit voor meer informatie over queryvoorbeelden [deze sectie](querying-recipient-table.md).

>[!NOTE]
>
>De activiteiten van de vraag zijn niet compatibel met gebieden CLOB wanneer het gebruiken van Oracle.

![](assets/s_user_segmentation_wizard_9.png)

Raadpleeg voor meer informatie over het gebruik en het beheer van aanvullende gegevens [Gegevens toevoegen](#adding-data).

De **[!UICONTROL Edit query...]** Via de koppeling kunt u het doeltype, de beperkingen en de selectiecriteria voor de bevolking als volgt definiëren:

1. Selecteer het richten en het filtreren dimensie. Standaard is het doel geselecteerd bij de ontvangers. De lijst met restrictiefilters is gelijk aan de lijst die wordt gebruikt voor het opgeven van doelen voor levering.

   De doelgerichte dimensie valt samen met het soort element waaraan wij zullen werken, bijvoorbeeld de bevolking die voor de operatie in aanmerking komt.

   De filterdimensie maakt het mogelijk deze elementen te verzamelen, bijvoorbeeld informatie over de doelpersoon (contracten, volledige en definitieve schikkingen, enz.).

   Raadpleeg voor meer informatie hierover [Afmetingen gericht en filteren](building-a-workflow.md#targeting-and-filtering-dimensions).

   ![](assets/s_user_segmentation_query_edit.png)

   Een vraag kan op gegevens van de binnenkomende overgang, indien nodig worden gebaseerd, door te selecteren **[!UICONTROL Temporary schema]** wanneer het kiezen van het richten en het filtreren dimensies.

   ![](assets/query_temporary_table.png)

1. Definieer de populaties met de wizard. De velden die moeten worden ingevoerd, kunnen verschillen afhankelijk van het type doel. U kunt een voorvertoning van de doelpopulatie weergeven met de huidige criteria **[!UICONTROL Preview]** tab.

   Raadpleeg deze voor meer informatie over het maken en gebruiken van filters of query&#39;s [sectie](../../platform/using/filtering-options.md).

   ![](assets/s_user_segmentation_wizard.png)

1. Als u **[!UICONTROL Filtering conditions]** in stap 1 of met de **[!UICONTROL Filters]** > **[!UICONTROL Advanced filter...]** en moet u later handmatig filtercriteria toevoegen.

   U kunt ook voorwaarden voor gegevensgroepering toevoegen door het desbetreffende vak in te schakelen. Om dit te doen, moet de het filtreren dimensie aan de vraag richten afmeting verschillend zijn. Zie deze voor meer informatie over groeperen [sectie](querying-using-grouping-management.md).

   U kunt meer criteria ook toevoegen door de bouwer van de Uitdrukking te gebruiken en het te combineren met de logische opties EN, OF, en BEHALVE. U kunt vervolgens een voorvertoning weergeven van de **[!UICONTROL Corresponding SQL query...]** voor uw criteria. Zie voor meer informatie deze [sectie](../../platform/using/defining-filter-conditions.md#building-expressions).

   Sla het filter op als u het later opnieuw wilt gebruiken.

   ![](assets/s_user_segmentation_query_advanced.png)

## Gegevens toevoegen {#adding-data}

In de aanvullende kolommen kunt u aanvullende informatie over de doelpopulatie verzamelen, bijvoorbeeld contractnummers, abonnementen op nieuwsbrieven of oorsprong. Deze gegevens kunnen worden opgeslagen in de Adobe Campaign-database of in een externe database.

De **[!UICONTROL Add data...]** Met de koppeling kunt u de aanvullende gegevens selecteren die u wilt verzamelen.

![](assets/wf_add_data_link.png)

Selecteer eerst het type gegevens dat u wilt toevoegen:

![](assets/wf_add_data_1st_option.png)

* Selecteren **[!UICONTROL Data linked to the filtering dimension]** om de gegevens in de Adobe Campaign-database te selecteren.
* Selecteren **[!UICONTROL External data]** gegevens uit een externe database toevoegen. Deze optie is alleen beschikbaar als u de **Federale gegevenstoegang** -optie. Raadpleeg voor meer informatie hierover [Toegang tot een externe database (FDA)](accessing-an-external-database-fda.md).
* Selecteer de **[!UICONTROL An offer proposition]** om een reeks kolommen toe te voegen waarmee u de beste die propositie kunt opslaan door de aanbiedingsmotor wordt geproduceerd. Deze optie is alleen beschikbaar als u de **Interactie** -module.

Als er geen optionele module op het platform is geïnstalleerd, wordt dit werkgebied niet weergegeven. U wordt rechtstreeks naar de volgende fase geleid.

Gegevens toevoegen uit de Adobe Campaign-database:

1. Selecteer het type gegevens dat u wilt toevoegen. Dit kunnen gegevens zijn die tot de het filtreren afmeting of gegevens behoren die in verbonden lijsten worden opgeslagen.

   ![](assets/query_add_columns.png)

1. Als de gegevens tot de het filtreren dimensie van de vraag behoren, selecteer eenvoudig het in de lijst van beschikbare gebieden om het in de outputkolommen te tonen.

   ![](assets/wf_add_data_field_selection.png)

   U kunt toevoegen:

   * Een veld dat wordt berekend op basis van gegevens van de doelpopulatie of een geaggregeerd (aantal lopende aankopen in de laatste maand, gemiddeld bedrag van een ontvangstbewijs enz.). Ga bijvoorbeeld naar [Gegevens selecteren](targeting-data.md#selecting-data).
   * Een nieuw veld, gemaakt met de **[!UICONTROL Add]** rechts van de lijst met uitvoerkolommen.

     U kunt ook een verzameling gegevens toevoegen, bijvoorbeeld een lijst met contracten, de laatste vijf leveringen, enzovoort. Verzamelingen komen overeen met velden die meerdere waarden kunnen hebben voor hetzelfde profiel (1-N relatie). Raadpleeg voor meer informatie hierover [Aanvullende gegevens bewerken](targeting-data.md#editing-additional-data).

Een verzameling gegevens toevoegen die verband houden met een doelgroep:

1. Selecteer in de eerste stap van de wizard de optie **[!UICONTROL Data linked to the filtering dimension]** optie:
1. Selecteer de tabel met de gegevens die u wilt verzamelen en klik op **[!UICONTROL Next]**.

   ![](assets/wf_add_data_linked_table.png)

1. Geef indien nodig het aantal elementen van de verzameling op dat u wilt behouden door een van de waarden in het dialoogvenster **[!UICONTROL Data collected]** veld. Standaard worden alle regels van de collectie hersteld en gefilterd volgens de voorwaarden die in de volgende stap zijn opgegeven.

   * Als één element van de verzameling samenvalt met de filtervoorwaarden voor deze verzameling, selecteert u **[!UICONTROL Single row]** in de **[!UICONTROL Data collected]** veld.

     >[!IMPORTANT]
     >
     >Deze wijze optimaliseert de SQL vraag die dankzij een directe verbinding op de inzamelingselementen wordt geproduceerd.
     >
     >Als niet aan de oorspronkelijke voorwaarde wordt voldaan, kan het resultaat onjuist zijn (ontbrekende of overlappende lijnen).

   * Als u meerdere regels wilt herstellen (**[!UICONTROL Limit the line count]**) kunt u opgeven hoeveel regels moeten worden verzameld.
   * Indien de verzamelde kolommen aggregaten bevatten, bijvoorbeeld het aantal gedeclareerde fouten, de gemiddelde uitgaven op een locatie, enz. u kunt de **[!UICONTROL Aggregates]** waarde.

   ![](assets/query_add_collection_param.png)

1. Geef de subselectie van de verzameling op. Bijvoorbeeld: alleen aankopen in de afgelopen 15 dagen.

   ![](assets/query_add_columns_collection_filter.png)

1. Als u **[!UICONTROL Limit the line count]** , definieert u de volgorde waarin de verzamelde gegevens moeten worden gefilterd. Zodra het aantal verzamelde lijnen meer dan het aantal lijnen is dat u specificeerde om te houden, staat de het filtreren orde u toe om te specificeren welke lijnen te houden.

## Voorbeeld: gericht op eenvoudige attributen voor ontvangers {#example--targeting-on-simple-recipient-attributes}

In het volgende voorbeeld probeert de query mannen tussen 18 en 30 jaar te identificeren die in Frankrijk wonen. Deze query wordt gebruikt in een workflow die als doel heeft deze bijvoorbeeld tot een exclusieve aanbieding te maken.

>[!NOTE]
>
>Aanvullende queryvoorbeelden worden weergegeven in [deze sectie](querying-recipient-table.md).

1. Geef uw query een naam en selecteer vervolgens de opdracht **[!UICONTROL Edit query...]** koppeling.
1. Selecteren **[!UICONTROL Filtering conditions]** in de lijst met beschikbare typen filters.
1. Voer de verschillende criteria voor het voorgestelde doel in. De volgende criteria worden gecombineerd met de optie AND. Om in de selectie te worden opgenomen, moeten de ontvangers aan de volgende vier voorwaarden voldoen:

   * Ontvangers met de titel &quot;Mr.&quot; (kan ook worden gevonden met de **Geslacht** veld en selecteren **Mannelijk** als een waarde).
   * Ontvangers jonger dan 30 jaar.
   * Ontvangers ouder dan 18 jaar.
   * Ontvangers die in Frankrijk wonen.

   ![](assets/query_example.png)

   U kunt de SQL bekijken die uw criteria combineert:

   ![](assets/query_example_sql.png)

1. U kunt controleren of uw criteria correct zijn door op het relevante tabblad een voorvertoning weer te geven van de ontvangers die overeenkomen met uw query:

   ![](assets/query_example_preview.png)

1. Sla de filters op zodat u ze later weer kunt gebruiken door op **[!UICONTROL Finish]** > **[!UICONTROL OK]**.
1. Ga door met het bewerken van uw workflow door er andere activiteiten aan toe te voegen. Zodra het is gelanceerd en de vorige vraagstap gebeëindigd, zal het aantal gevonden ontvangers worden getoond. U kunt meer details weergeven met het pop-upmenu Muis (klik met de rechtermuisknop op de overgang > **[!UICONTROL Display the target...]**).

   ![](assets/query_example_result.png)

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert de bevolking die door de vraag wordt gericht. **[!UICONTROL tableName]** is de naam van de lijst die de doelherkenningstekens registreert, **[!UICONTROL schema]** is het schema van de populatie (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de tabel.

Deze waarde is het schema van de het werklijst. Deze parameter is geldig voor alle overgangen met **[!UICONTROL tableName]** en **[!UICONTROL schema]**.

## Uw query&#39;s optimaliseren {#optimizing-queries}

In de onderstaande sectie vindt u tips en trucs voor het optimaliseren van query&#39;s die op Adobe Campaign worden uitgevoerd om de werkbelasting van de database te beperken en de gebruikerservaring te verbeteren.

### Verbindingen en indexen {#joins-and-indexes}

* De efficiënte vragen baseren zich op indexen.
* Gebruik een index voor alle verbindingen.
* Het bepalen van verbindingen op het schema zal bepalen toetreedt voorwaarden. De gekoppelde tabel moet een unieke index hebben op de primaire sleutel en de samenvoeging moet zich in dit veld bevinden.
* Verbindingen uitvoeren door sleutels op numerieke gebieden in plaats van koordgebieden te bepalen.
* Vermijd het uitvoeren van buitenste verbindingen. Gebruik waar mogelijk de Nul-id-record om de functie voor buitenste verbindingen te bereiken.
* Gebruik het correcte gegevenstype voor verbindingen.

  Zorg ervoor dat de `where` is hetzelfde type als het veld.

  Een algemene fout is: `iBlacklist='3'` waar `iBlacklist` een numeriek veld is, en `3` Geeft een tekstwaarde aan.

  Zorg ervoor u weet wat het uitvoeringsplan van uw vraag zal zijn. Vermijd volledig lijstaftasten, vooral voor vragen in real time of dichtbij vragen in real time die elke minuut lopen.

  Raadpleeg de volgende secties voor meer informatie, afhankelijk van uw campagneversie:

  ![](assets/do-not-localize/v7.jpeg)[Campagne v7-documentatie](../../configuration/using/database-mapping.md)

  ![](assets/do-not-localize/v8.png)[Campagne v8-documentatie](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/shemas-forms/database-mapping.html)

### Functies {#functions}

* Functies zoals bewerken `Lower(...)`. Wanneer de functie Lower wordt gebruikt, wordt de Index niet gebruikt.
* Controleer query&#39;s met de ‘soortgelijke’ instructie of de ‘bovenste’ of ‘onderste’ instructies zorgvuldig. Pas &quot;Upper&quot;op de gebruikersinput, niet op het gegevensbestandgebied toe.

  Raadpleeg voor meer informatie over functies [deze sectie](../../platform/using/defining-filter-conditions.md#list-of-functions).

### Afmetingen filteren {#filtering-dimensions}

Gebruik de het filtreren dimensie van de vraag in plaats van het gebruiken van &quot;bestaat zoals&quot;exploitant.

![](assets/optimize-queries-filtering.png)

In query&#39;s zijn &#39;bestaat zoals&#39;-voorwaarden in filters niet efficiënt. Ze zijn het equivalent van een subquery in SQL:

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

De beste praktijken moeten in plaats daarvan de het filtreren afmeting van de vraag gebruiken:

![](assets/optimize-queries-filtering2.png)

Het equivalent van de het filtreren afmeting in SQL is de binnenvoeging:

`select iRecipientId from nmsRecipient INNER JOIN nmsBroadLog ON (...)`

Raadpleeg voor meer informatie over filterafmetingen [deze sectie](building-a-workflow.md#targeting-and-filtering-dimensions).

### Architectuur {#architecture}

* Bouw een ontwikkelingsplatform met gelijkaardige volumes, parameters, en architectuur als productieplatform.
* Gebruik dezelfde waarden voor de ontwikkelings- en productieomgeving. Gebruik zoveel mogelijk hetzelfde:

   * Besturingssysteem
   * Versie,
   * gegevens,
   * toepassing,
   * Volume.

  >[!NOTE]
  >
  >Een functie die in een ontwikkelomgeving werkt, werkt mogelijk niet in een productieomgeving waarin de gegevens verschillend kunnen zijn. Probeer de belangrijkste verschillen vast te stellen om risico&#39;s te anticiperen en oplossingen voor te bereiden.

* Maak configuraties die overeenkomen met de doelvolumes. Voor grote volumes zijn specifieke configuraties vereist. Een configuratie die voor 100.000 ontvangers werkte kan niet voor 10.000.000 ontvangers werken.

  Bedenk hoe het systeem wordt geschaald wanneer het live gaat. Enkel omdat iets op kleine schaal werkt, betekent dat niet dat het geschikt zal zijn met grotere volumes. De tests moeten worden uitgevoerd met volumes die vergelijkbaar zijn met het productievolume. U zou ook het effect van veranderingen in volumes (aantal vraag, grootte van het gegevensbestand) bij piekuren, piekdagen, en over het leven van het project moeten evalueren.
