---
product: campaign
title: Query
description: Meer informatie over de activiteit van de Query-workflow
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 20d03627-cd56-46da-bc02-73b48a02a350
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1629'
ht-degree: 0%

---

# Query{#query}

![](../../assets/common.svg)

## Een query maken {#creating-a-query}

Met een query kunt u een doel selecteren op basis van criteria. U kunt een segmentcode aan het vraagresultaat associëren en extra gegevens opnemen in het.
Voor meer informatie over vraagsteekproeven, verwijs naar dit [deze sectie](querying-recipient-table.md).

>[!NOTE]
>
>De activiteiten van de vraag zijn niet compatibel met gebieden CLOB wanneer het gebruiken van Oracle.

![](assets/s_user_segmentation_wizard_9.png)

Raadpleeg [Gegevens toevoegen](#adding-data) voor meer informatie over het gebruik en het beheer van aanvullende gegevens.

Met de koppeling **[!UICONTROL Edit query...]** kunt u het doeltype, de beperkingen en de selectiecriteria voor de populatie als volgt definiëren:

1. Selecteer het richten en het filtreren dimensie. Standaard is het doel geselecteerd bij de ontvangers. De lijst met restrictiefilters is gelijk aan de lijst die wordt gebruikt voor het opgeven van doelen.

   De doelgerichte dimensie valt samen met het soort element waaraan wij zullen werken, bijvoorbeeld de bevolking die voor de operatie in aanmerking komt.

   De filterdimensie maakt het mogelijk deze elementen te verzamelen, bijvoorbeeld informatie over de doelpersoon (contracten, volledige en definitieve schikkingen, enz.).

   Voor meer op dit, verwijs naar [Het richten en het filtreren dimensies](building-a-workflow.md#targeting-and-filtering-dimensions).

   ![](assets/s_user_segmentation_query_edit.png)

   Een vraag kan op gegevens van de binnenkomende overgang worden gebaseerd, indien nodig, door **[!UICONTROL Temporary schema]** te selecteren wanneer het kiezen van het richten en het filtreren dimensies.

   ![](assets/query_temporary_table.png)

1. Definieer de populaties met de wizard. De velden die moeten worden ingevoerd, kunnen verschillen afhankelijk van het type doel. U kunt een voorvertoning van de doelpopulatie met uw huidige criteria weergeven via het tabblad **[!UICONTROL Preview]**.

   Raadpleeg deze [sectie](../../platform/using/filtering-options.md) voor meer informatie over het maken en gebruiken van filters of query&#39;s.

   ![](assets/s_user_segmentation_wizard.png)

1. Als u **[!UICONTROL Filtering conditions]** in stap 1 hebt geselecteerd of de optie **[!UICONTROL Filters]** > **[!UICONTROL Advanced filter...]** hebt gebruikt, moet u later handmatig filtercriteria toevoegen.

   U kunt ook voorwaarden voor gegevensgroepering toevoegen door het desbetreffende vak in te schakelen. Om dit te doen, moet de het filtreren afmeting aan de het richten van vraag afmeting verschillend zijn. Voor meer informatie bij groepering, verwijs naar dit [sectie](querying-using-grouping-management.md).

   U kunt meer criteria ook toevoegen door de bouwer van de Uitdrukking te gebruiken en het te combineren met de logische opties EN, OF, en BEHALVE. U kunt dan een voorbeeld van de combinatie **[!UICONTROL Corresponding SQL query...]** voor uw criteria bekijken. Voor meer op dit verwijs naar [sectie](../../platform/using/defining-filter-conditions.md#building-expressions).

   Sla het filter op als u het later opnieuw wilt gebruiken.

   ![](assets/s_user_segmentation_query_advanced.png)

## Gegevens toevoegen {#adding-data}

In de aanvullende kolommen kunt u aanvullende informatie over de doelpopulatie verzamelen, bijvoorbeeld contractnummers, abonnementen op nieuwsbrieven of oorsprong. Deze gegevens kunnen worden opgeslagen in de Adobe Campaign-database of in een externe database.

Met de koppeling **[!UICONTROL Add data...]** kunt u de aanvullende gegevens selecteren die u wilt verzamelen.

![](assets/wf_add_data_link.png)

Selecteer eerst het type gegevens dat u wilt toevoegen:

![](assets/wf_add_data_1st_option.png)

* Selecteer **[!UICONTROL Data linked to the filtering dimension]** om de gegevens in de Adobe Campaign-database te selecteren.
* Selecteer **[!UICONTROL External data]** om gegevens uit een externe database toe te voegen. Deze optie is alleen beschikbaar als u de optie **Federated Data Access** hebt aangeschaft. Raadpleeg [Toegang tot een externe database (FDA)](accessing-an-external-database--fda-.md) voor meer informatie hierover.
* Selecteer de optie **[!UICONTROL An offer proposition]** om een set kolommen toe te voegen waarmee u de beste propositie kunt opslaan die door de aanbiedingsengine wordt gegenereerd. Deze optie is alleen beschikbaar als u de module **Interaction** hebt aangeschaft.

Als er geen optionele module op het platform is geïnstalleerd, wordt dit werkgebied niet weergegeven. U wordt rechtstreeks naar de volgende fase geleid.

Gegevens toevoegen uit de Adobe Campaign-database:

1. Selecteer het type gegevens dat u wilt toevoegen. Dit kunnen gegevens zijn die tot de het filtreren afmeting of gegevens behoren die in verbonden lijsten worden opgeslagen.

   ![](assets/query_add_columns.png)

1. Als de gegevens tot de het filtreren dimensie van de vraag behoren, selecteer eenvoudig het in de lijst van beschikbare gebieden om het in de outputkolommen te tonen.

   ![](assets/wf_add_data_field_selection.png)

   U kunt toevoegen:

   * Een veld dat wordt berekend op basis van gegevens van de doelpopulatie of een geaggregeerd (aantal lopende aankopen in de laatste maand, gemiddeld bedrag van een ontvangstbewijs enz.). Bij een voorbeeld gaat u naar [Gegevens selecteren](targeting-data.md#selecting-data).
   * Een nieuw veld, gemaakt met de knop **[!UICONTROL Add]** rechts van de lijst met uitvoerkolommen.

      U kunt ook een verzameling gegevens toevoegen, zoals een lijst met contracten, de laatste vijf leveringen, enzovoort. Verzamelingen komen overeen met velden die meerdere waarden kunnen hebben voor hetzelfde profiel (1-N relatie). Raadpleeg [Extra gegevens bewerken](targeting-data.md#editing-additional-data) voor meer informatie.

Een verzameling gegevens toevoegen die verband houden met een doelgroep:

1. Selecteer bij de eerste stap van de wizard de optie **[!UICONTROL Data linked to the filtering dimension]**:
1. Selecteer de tabel die de gegevens bevat die u wilt verzamelen en klik op **[!UICONTROL Next]**.

   ![](assets/wf_add_data_linked_table.png)

1. Geef indien nodig het aantal elementen van de verzameling op dat u wilt behouden door een van de waarden in het veld **[!UICONTROL Data collected]** te selecteren. Standaard worden alle regels van de collectie hersteld en gefilterd volgens de voorwaarden die in de volgende stap zijn opgegeven.

   * Als één enkel element van de inzameling met de het filtreren voorwaarden voor deze inzameling samenvalt, selecteer **[!UICONTROL Single row]** in **[!UICONTROL Data collected]** gebied.

      >[!IMPORTANT]
      >
      >Deze wijze optimaliseert de SQL vraag die dankzij een directe verbinding op de inzamelingselementen wordt geproduceerd.
      >
      >Als niet aan de oorspronkelijke voorwaarde wordt voldaan, kan het resultaat onjuist zijn (ontbrekende of overlappende lijnen).

   * Als u meerdere regels (**[!UICONTROL Limit the line count]**) wilt herstellen, kunt u het aantal regels opgeven dat moet worden verzameld.
   * Indien de verzamelde kolommen aggregaten bevatten, bijvoorbeeld het aantal gedeclareerde fouten, de gemiddelde uitgaven op een locatie, enz. u kunt de waarde **[!UICONTROL Aggregates]** gebruiken.

   ![](assets/query_add_collection_param.png)

1. Geef de subselectie van de verzameling op. Bijvoorbeeld: alleen aankopen in de afgelopen 15 dagen.

   ![](assets/query_add_columns_collection_filter.png)

1. Als u de optie **[!UICONTROL Limit the line count]** hebt geselecteerd, definieert u de volgorde waarin de verzamelde gegevens moeten worden gefilterd. Zodra het aantal verzamelde lijnen meer dan het aantal lijnen is dat u specificeerde om te houden, staat de het filtreren orde u toe om te specificeren welke lijnen te houden.

## Voorbeeld: Afstemmen op eenvoudige attributen voor ontvangers {#example--targeting-on-simple-recipient-attributes}

In het volgende voorbeeld probeert de query mannen tussen 18 en 30 jaar te identificeren die in Frankrijk wonen. Deze query wordt gebruikt in een workflow die als doel heeft deze bijvoorbeeld tot een exclusieve aanbieding te maken.

>[!NOTE]
>
>Extra vraagsteekproeven worden voorgesteld in [deze sectie](querying-recipient-table.md).

1. Noem uw vraag dan selecteren **[!UICONTROL Edit query...]** verbinding.
1. Selecteer **[!UICONTROL Filtering conditions]** in de lijst van beschikbare types van filter.
1. Voer de verschillende criteria voor het voorgestelde doel in. De volgende criteria worden gecombineerd met de optie AND. Om in de selectie te worden opgenomen, moeten de ontvangers aan de volgende vier voorwaarden voldoen:

   * Ontvangers met de titel &quot;Mr.&quot; (kan ook worden gevonden met het veld **Gender** en door **Male** als waarde te selecteren).
   * Ontvangers jonger dan 30 jaar.
   * Ontvangers ouder dan 18 jaar.
   * Ontvangers die in Frankrijk wonen.

   ![](assets/query_example.png)

   U kunt de SQL bekijken die uw criteria combineert:

   ![](assets/query_example_sql.png)

1. U kunt controleren of uw criteria correct zijn door op het relevante tabblad een voorvertoning weer te geven van de ontvangers die overeenkomen met uw query:

   ![](assets/query_example_preview.png)

1. Sla de filters op zodat u ze later weer kunt gebruiken door op **[!UICONTROL Finish]** > **[!UICONTROL OK]** te klikken.
1. Ga door met het bewerken van uw workflow door er andere activiteiten aan toe te voegen. Zodra het is gelanceerd en de vorige vraagstap gebeëindigd, zal het aantal gevonden ontvangers worden getoond. U kunt meer details tonen gebruikend het muis pop-up menu (klik de overgang met de rechtermuisknop aan > **[!UICONTROL Display the target...]**).

   ![](assets/query_example_result.png)

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert de bevolking die door de vraag wordt gericht. **[!UICONTROL tableName]** is de naam van de lijst die de doelherkenningstekens registreert,  **[!UICONTROL schema]** is het schema van de bevolking (gewoonlijk nms:ontvanger) en  **[!UICONTROL recCount]** is het aantal elementen in de lijst.

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

   Zorg ervoor dat de `where` clausule het zelfde type als het gebied is.

   Een algemene fout is: `iBlacklist='3'` waarbij `iBlacklist` een numeriek veld is en `3` een tekstwaarde.

   Zorg ervoor u weet wat het uitvoeringsplan van uw vraag zal zijn. Vermijd volledig lijstaftasten, vooral voor vragen in real time of dichtbij vragen in real time die elke minuut lopen.

   Raadpleeg de volgende secties voor meer informatie, afhankelijk van uw campagneversie:

   ![](assets/do-not-localize/v7.jpeg)[  Documentatie voor Campaign v7](../../configuration/using/database-mapping.md)

   ![](assets/do-not-localize/v8.png)[  Documentatie voor Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/shemas-forms/database-mapping.html)

### Functies {#functions}

* Houd rekening met functies zoals `Lower(...)`. Wanneer de functie Lower wordt gebruikt, wordt de Index niet gebruikt.
* Controleer query&#39;s met de ‘soortgelijke’ instructie of de ‘bovenste’ of ‘onderste’ instructies zorgvuldig. Pas &quot;Upper&quot;op de gebruikersinput, niet op het gegevensbestandgebied toe.

   Zie [deze sectie](../../platform/using/defining-filter-conditions.md#list-of-functions) voor meer informatie over functies.

### Afmetingen filteren {#filtering-dimensions}

Gebruik de het filtreren dimensie van de vraag in plaats van het gebruiken van &quot;bestaat zoals&quot;exploitant.

![](assets/optimize-queries-filtering.png)

In query&#39;s zijn &#39;bestaat zoals&#39;-voorwaarden in filters niet efficiënt. Ze zijn het equivalent van een subquery in SQL:

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

De beste praktijken moeten in plaats daarvan de het filtreren afmeting van de vraag gebruiken:

![](assets/optimize-queries-filtering2.png)

Het equivalent van de het filtreren afmeting in SQL is de binnenpartij:

`select iRecipientId from nmsRecipient INNER JOIN nmsBroadLog ON (...)`

Raadpleeg [deze sectie](building-a-workflow.md#targeting-and-filtering-dimensions) voor meer informatie over filterafmetingen.

### Architectuur {#architecture}

* Bouw een ontwikkelingsplatform met gelijkaardige volumes, parameters, en architectuur als productieplatform.
* Gebruik dezelfde waarden voor de ontwikkelings- en productieomgeving. Gebruik zoveel mogelijk hetzelfde:

   * Besturingssysteem
   * Versie,
   * gegevens,
   * toepassing,
   * Volumes.

   >[!NOTE]
   >
   >Een functie die in een ontwikkelomgeving werkt, werkt mogelijk niet in een productieomgeving waarin de gegevens verschillend kunnen zijn. Probeer de belangrijkste verschillen vast te stellen om risico&#39;s te anticiperen en oplossingen voor te bereiden.

* Maak configuraties die overeenkomen met de doelvolumes. Voor grote volumes zijn specifieke configuraties vereist. Een configuratie die voor 100.000 ontvangers werkte kan niet voor 10.000.000 ontvangers werken.

   Bedenk hoe het systeem wordt geschaald wanneer het live gaat. Enkel omdat iets op kleine schaal werkt, betekent dat niet dat het geschikt zal zijn met grotere volumes. De tests moeten worden uitgevoerd met volumes die vergelijkbaar zijn met het productievolume. U zou ook het effect van veranderingen in volumes (aantal vraag, grootte van het gegevensbestand) bij piekuren, piekdagen, en over het leven van het project moeten evalueren.
