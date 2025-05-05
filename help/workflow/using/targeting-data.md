---
product: campaign
title: Doelgegevens
description: Meer informatie over doelgegevens in een workflow
feature: Query Editor, Data Management, Workflows
hide: true
hidefromtoc: true
exl-id: 74b82019-bdab-4442-84cf-5ad18d0db788
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1919'
ht-degree: 3%

---

# Targetgegevens{#targeting-data}



## Query&#39;s maken {#creating-queries}

### Gegevens selecteren {#selecting-data}

Met een **[!UICONTROL Query]** -activiteit kunt u basisgegevens selecteren om de doelpopulatie samen te stellen. Voor meer op dit, verwijs naar [ Creërend een vraag ](query.md#creating-a-query).

U kunt de volgende activiteiten ook gebruiken om gegevens van het gegevensbestand te vragen en te raffineren: [ Incrementele vraag ](incremental-query.md), [ leest lijst ](read-list.md).

Het is mogelijk aanvullende gegevens te verzamelen die gedurende de gehele levenscyclus van de werkstroom moeten worden doorgestuurd en verwerkt. Voor meer op dit, verwijs naar [ het Toevoegen van gegevens ](query.md#adding-data) en [ het Uitgeven van extra gegevens ](#editing-additional-data).

### Aanvullende gegevens bewerken {#editing-additional-data}

Zodra extra gegevens zijn toegevoegd, kunt u het uitgeven of het gebruiken om het doel te raffineren dat in de vraagactiviteit wordt bepaald.

Met de koppeling **[!UICONTROL Edit additional data...]** kunt u de toegevoegde gegevens weergeven en wijzigen of toevoegen.

![](assets/wf_add_data_edit_link.png)

Als u gegevens wilt toevoegen aan de eerder gedefinieerde uitvoerkolommen, selecteert u deze in de lijst met beschikbare velden. Als u een nieuwe uitvoerkolom wilt maken, klikt u op het pictogram **[!UICONTROL Add]** , selecteert u het veld en klikt u op **[!UICONTROL Edit expression]** .

![](assets/query_add_an_output_column.png)

Definieer een berekeningsmodus voor het veld dat moet worden toegevoegd, zoals bijvoorbeeld een aggregaat.

![](assets/query_add_an_output_column_formula.png)

Met de optie **[!UICONTROL Add a sub-item]** kunt u berekende gegevens aan de verzameling koppelen. Hiermee kunt u de aanvullende gegevens uit de verzameling selecteren of geaggregeerde berekeningen voor verzamelingselementen definiëren.

![](assets/query_add_columns_subscription_sub-element.png)

De subelementen worden weergegeven in de substructuur van de verzameling waaraan ze zijn toegewezen.

Verzamelingen worden weergegeven op het subtabblad **[!UICONTROL Collections]** . U kunt de verzamelde elementen filteren door op het pictogram **[!UICONTROL Detail]** van de geselecteerde verzameling te klikken. Met de filterassistent kunt u de verzamelde gegevens selecteren en de filtervoorwaarden opgeven die op de gegevens in de verzameling moeten worden toegepast.

![](assets/query_add_columns_collection.png)

### Het doel verfijnen met behulp van aanvullende gegevens {#refining-the-target-using-additional-data}

De extra verzamelde gegevens kunnen u toelaten om gegevens het filtreren in het gegevensbestand te verfijnen. Klik hiertoe op de koppeling **[!UICONTROL Refine the target using additional data...]** : hiermee kunt u de toegevoegde gegevens overschrijven.

![](assets/wf_add_data_use_additional_data.png)

### Gegevens homogeniseren {#homogenizing-data}

Bij **[!UICONTROL Union]** - of **[!UICONTROL Intersection]** -type-activiteiten kunt u ervoor kiezen alleen gedeelde aanvullende gegevens te behouden om de gegevens consistent te houden. In dit geval bevat de tijdelijke uitvoerwerktabel van deze activiteit alleen de aanvullende gegevens die in alle binnenkomende sets worden gevonden.

![](assets/option-common_additionnal_col_only.png)

### Afstemming met aanvullende gegevens {#reconciliation-with-additional-data}

Tijdens de afstemmingsfasen (**[!UICONTROL Union]**, **[!UICONTROL Intersection]**, enz.) activiteiten) selecteert u de kolommen die u wilt gebruiken voor het afstemmen van gegevens in de extra kolommen. Hiertoe configureert u een afstemming op een selectie van kolommen en geeft u de hoofdset op. Selecteer vervolgens de kolommen in de onderste kolom van het venster, zoals in het volgende voorbeeld wordt getoond:

![](assets/select-column-and-join.png)

### Subsets maken {#creating-subsets}

Met de **[!UICONTROL Split]** -activiteit kunt u subsets maken op basis van criteria die zijn gedefinieerd via extractiequery&#39;s. Voor elke ondergroep, wanneer u een filtervoorwaarde op de bevolking uitgeeft, zult u tot de standaardvraagactiviteit toegang hebben die u de voorwaarden van de doelsegmentatie laat bepalen.

U kunt een doel in verscheidene subsets verdelen gebruikend slechts extra gegevens als het filtreren voorwaarden, of naast doelgegevens. U kunt externe gegevens ook gebruiken als u de **Federated optie van de Toegang van Gegevens** hebt gekocht.

Voor meer op dit, verwijs naar [ Creërend ondergroepen gebruikend de Gesplitste activiteit ](#creating-subsets-using-the-split-activity).

## Segmentgegevens {#segmenting-data}

### Verschillende doelen combineren (Unie) {#combining-several-targets--union-}

Met de vakbondsactiviteit kunt u het resultaat van verschillende activiteiten in één overgang combineren. Stellen hoeven niet noodzakelijkerwijs homogeen te zijn.

![](assets/join_reconciliation_options.png)

De volgende afstemmingsopties voor gegevens zijn beschikbaar:

* **[!UICONTROL Keys only]**

  Deze optie kan worden gebruikt als de inputpopulaties homogeen zijn.

* **[!UICONTROL All columns in common]**

  Met deze optie kunt u gegevens afstemmen op basis van alle kolommen die de verschillende populaties van het doel gemeen hebben.

  Adobe Campaign geeft kolommen aan op basis van hun naam. Een tolerantiedrempel wordt geaccepteerd: een kolom &#39;E-mail&#39; kan bijvoorbeeld worden herkend als identiek aan een kolom &#39;@email&#39;.

* **[!UICONTROL A selection of columns]**

  Selecteer deze optie om de lijst met kolommen te definiëren waarop de afstemming van gegevens wordt toegepast.

  Begin door de belangrijkste reeks (die bevat de brongegevens) te selecteren, dan de kolommen die voor de verbinding moeten worden gebruikt.

  ![](assets/join_reconciliation_options_01.png)

  >[!CAUTION]
  >
  >Tijdens de afstemming van gegevens worden populaties niet gededupliceerd.

  U kunt de populatiegrootte tot een bepaald aantal verslagen beperken. Klik hiertoe op de gewenste optie en geef het aantal records op dat u wilt behouden.

  Geef ook de prioriteit van de binnenkomende populaties op: in de onderste sectie van het venster worden de binnenkomende overgangen van de samenvoegactiviteit weergegeven en kunt u deze sorteren met de blauwe pijlen rechts van het venster.

  De gegevens worden eerst overgenomen uit de populatie van de eerste binnenkomende overgang in de lijst. Als het maximum niet is bereikt, worden ze onttrokken aan de populatie van de tweede binnenkomende overgang, enz.

  ![](assets/join_limit_nb_priority.png)

### Verbindingsgegevens extraheren (doorsnede) {#extracting-joint-data--intersection-}

![](assets/traitements.png)

Met het snijpunt kunt u alleen de regels herstellen die worden gedeeld door de populaties van binnenkomende overgangen. Deze activiteit wordt als de vakbondsactiviteit gevormd.

Bovendien is het mogelijk om slechts een selectie van kolommen te houden, of slechts de kolommen die door de binnenkomende bevolking worden gedeeld.

De intersectieactiviteit is gedetailleerd in de [ sectie van de Intersectie ](intersection.md).

### Een populatie uitsluiten (Uitsluiting) {#excluding-a-population--exclusion-}

Met de uitsluitingsactiviteit kunt u de elementen van een doel uitsluiten van een andere doelpopulatie. De doeldimensie van deze activiteit is die van de hoofdset.

Indien nodig, is het mogelijk om binnenkomende lijsten te manipuleren. Om een doel van een andere dimensie uit te sluiten, moet dit doel worden teruggebracht naar dezelfde doeldimensie als het hoofddoel. Klik hiertoe op de knop **[!UICONTROL Add]** en geef de voorwaarden voor het wijzigen van de afmetingen op.

Afstemming van gegevens vindt plaats via een id, een veranderende as of een samenvoeging. Een voorbeeld is beschikbaar in [ Gebruikend gegevens van een lijst: Lees lijst ](../../platform/using/import-export-workflows.md#using-data-from-a-list--read-list).

![](assets/exclusion_edit_add_rule_01.png)

### Subsets maken met de splitsingsactiviteit {#creating-subsets-using-the-split-activity}

De **[!UICONTROL Split]** -activiteit is een standaardactiviteit waarmee u zoveel sets kunt maken als nodig via een of meerdere filterdimensies en waarbij u ook één uitvoerovergang per subset of een unieke overgang kunt genereren.

De extra gegevens die door de binnenkomende overgang worden overgebracht kunnen in de het filtreren criteria worden gebruikt.

Om het te vormen, moet u eerst criteria selecteren:

1. Sleep een **[!UICONTROL Split]** -activiteit in uw workflow en zet deze neer.
1. Selecteer op het tabblad **[!UICONTROL General]** de gewenste optie: **[!UICONTROL Use data from the target and additional data]** , **[!UICONTROL Use the additional data only]** of **[!UICONTROL Use external data]** .
1. Als de optie **[!UICONTROL Use data from the target and additional data]** is geselecteerd, kunt u met de doeldimensie alle gegevens gebruiken die door de binnenkomende overgang worden overgebracht.

   ![](assets/split-general-tab-options.png)

   Wanneer subsets worden gemaakt, worden de eerder vermelde filterparameters gebruikt.

   Als u filtervoorwaarden wilt definiëren, kiest u de optie **[!UICONTROL Add a filtering condition on the inbound population]** en klikt u op de koppeling **[!UICONTROL Edit...]** . Geef vervolgens de filtervoorwaarden op voor het maken van deze subset.

   ![](assets/split-subset-config-all-data.png)

   Een voorbeeld dat toont hoe te om het filtreren voorwaarden in de **[!UICONTROL Split]** activiteit te gebruiken om het doel in verschillende populaties te segmenteren wordt beschreven in [ deze sectie ](cross-channel-delivery-workflow.md).

   In het veld **[!UICONTROL Label]** kunt u de nieuwe subset een naam geven die overeenkomt met de uitgaande overgang.

   U kunt ook een segmentcode aan de subset toewijzen om deze te identificeren en te gebruiken om de populatie te bepalen.

   Indien nodig, kunt u de het richten en het filtreren dimensies individueel voor elke ondergroep veranderen u wilt tot stand brengen. Hiervoor bewerkt u de filtervoorwaarde van de subset en controleert u de optie **[!UICONTROL Use a specific filtering dimension]** .

   ![](assets/split-subset-config-specific-filtering.png)

1. Als de optie **[!UICONTROL Use the additional data only]** is geselecteerd, worden alleen aanvullende gegevens aangeboden voor filteren van subsets.

   ![](assets/split-subset-config-additional-data-only.png)

1. Als de **Verdeelde optie van de Toegang van Gegevens** wordt toegelaten, laat **[!UICONTROL Use external data]** u gegevens in een extern gegevensbestand verwerken dat reeds wordt gevormd, of een nieuwe verbinding tot stand brengen met een gegevensbestand.

   ![](assets/split-subset-config-add_external_data.png)

   Raadpleeg de volgende secties voor meer informatie, afhankelijk van uw campagneversie:

   ![](assets/do-not-localize/v7.jpeg) [ de documentatie van de Campagne v7 ](../../installation/using/about-fda.md)

   ![](assets/do-not-localize/v8.png) [ Campagne v8 documentatie ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html?lang=nl-NL)

Vervolgens moeten nieuwe subsets worden toegevoegd:

1. Klik op de knop **[!UICONTROL Add]** en definieer de filtervoorwaarden.

   ![](assets/wf_split_add_a_tab.png)

1. Definieer de filterdimensie op het tabblad **[!UICONTROL General]** van de activiteit (zie boven). Deze wordt standaard toegepast op alle subsets.

   ![](assets/wf_split_edit_filtering.png)

1. Indien nodig kunt u de filterdimensie voor elke subset afzonderlijk wijzigen. Hiermee kunt u een set maken voor alle houders van een Gold-kaart, één voor alle ontvangers die op de meest recente nieuwsbrief hebben geklikt en een derde voor personen van 18 tot en met 25 jaar die de laatste 30 dagen in de winkel een aankoop hebben gedaan, allemaal met dezelfde gesplitste activiteit. Selecteer hiertoe de optie **[!UICONTROL Use a specific filtering dimension]** en selecteer de context voor het filteren van gegevens.

   ![](assets/wf_split_change_dimension.png)

   >[!NOTE]
   >
   >Als u de **Verbond optie van de Toegang van Gegevens** hebt verworven, kunt u ondergroepen tot stand brengen die op de informatie in een externe basis worden gebaseerd. Selecteer hiertoe het schema van de externe tabel in het veld **[!UICONTROL Targeting dimension]** . Voor meer op dit, verwijs naar [ Toegang hebbend tot een extern gegevensbestand (FDA) ](accessing-an-external-database-fda.md).

Nadat subsets zijn gemaakt, toont de splitsingsactiviteit standaard evenveel uitvoerovergangen als er subsets zijn:

![](assets/wf_split_multi_outputs.png)

U kunt al deze subsets groeperen in één uitvoerovergang. In dit geval is de koppeling naar de desbetreffende subsets bijvoorbeeld zichtbaar in de segmentcode. Selecteer hiervoor de optie **[!UICONTROL Generate all subsets in the same table]** .

![](assets/wf_split_select_option_single_output.png)

Bijvoorbeeld, kunt u één enkele leveringsactiviteit plaatsen en de leveringsinhoud personaliseren die op de segmentcode van elke ontvankelijke reeks wordt gebaseerd:

![](assets/wf_split_single_output.png)

Subsets kunnen ook worden gemaakt met behulp van de **[!UICONTROL Cells]** -activiteit. Voor meer op dit, verwijs naar de [ sectie van Cellen ](cells.md).

### Doelgegevens gebruiken {#using-targeted-data}

Zodra de gegevens zijn geïdentificeerd en opgesteld, kunnen ze in de volgende context worden gebruikt:

* U kunt de gegevens in de database bijwerken na gegevensmanipulatie in de verschillende werkstroomfasen.

  Voor meer op dit, [ gegevens van de Update ](update-data.md).

* U kunt ook de inhoud van bestaande lijsten vernieuwen.

  Voor meer op dit, verwijs naar [ update van de Lijst ](list-update.md).

* U kunt leveringen rechtstreeks voorbereiden of starten in de workflow.

  Voor meer op dit, verwijs naar [ Levering ](delivery.md), [ de controle van de Levering ](delivery-control.md) en [ Ononderbroken levering ](continuous-delivery.md).

## Data management {#data-management}

In Adobe Campaign combineert het gegevensbeheer een reeks activiteiten om complexe doelgerichte problemen op te lossen door efficiëntere en flexibelere hulpmiddelen aan te bieden. Dit laat u verenigbaar beheer van alle communicatie met een contact uitvoeren gebruikend informatie met betrekking tot hun contracten, abonnementen, reactiviteit aan leveringen, enz. Met data management kunt u de levenscyclus van data bijhouden tijdens segmentatiebewerkingen, met name:

* Het vereenvoudigen en optimaliseren van targetingprocessen, door data op te nemen die niet in de datamart worden gemodelleerd (het maken van nieuwe tabellen: lokale extensie voor elke targetingworkflow afhankelijk van de configuratie).
* Het bijhouden en overbrengen van bufferberekeningen, vooral tijdens fasen voor de opbouw van doelen of voor databasebeheer.
* Het openen van externe databases (optioneel): heterogene databases waarmee tijdens het targetingproces rekening wordt gehouden.

Voor de uitvoering van deze transacties biedt Adobe Campaign:

* De activiteiten van de inzameling van gegevens: [ overdracht van het Dossier ](file-transfer.md), [ het laden van Gegevens (dossier) ](data-loading-file.md), [ het laden van Gegevens (RDBMS) ](data-loading-rdbms.md), [ gegevens van de Update ](update-data.md). In deze eerste stap voor het verzamelen van gegevens worden de gegevens voorbereid, zodat ze in andere activiteiten kunnen worden verwerkt. Verschillende parameters moeten worden gecontroleerd om ervoor te zorgen dat de workflow correct wordt uitgevoerd en de verwachte resultaten oplevert. Wanneer u bijvoorbeeld gegevens importeert, moet de primaire sleutel (sleutel) voor deze gegevens uniek zijn voor elke record.
* Het richten activiteiten die met de opties van het Beheer van Gegevens zijn verrijkt: [ Vraag ](query.md), [ Unie ](union.md), [ Intersectie ](intersection.md), [ Gesplitst ](split.md). Zo kunt u een samenvoeging of een doorsnede configureren tussen gegevens van verschillende doeldimensies, zolang de gegevens met elkaar in overeenstemming kunnen worden gebracht.
* De transformatieactiviteiten van gegevens: [ Verrijking ](enrichment.md), [ dimensie van de Verandering ](change-dimension.md).

>[!CAUTION]
>
>Wanneer twee workflows zijn gekoppeld, betekent het verwijderen van een brontabelelement niet dat alle gegevens die eraan zijn gekoppeld, worden verwijderd.
>  
>Als u bijvoorbeeld een ontvanger verwijdert via een workflow, wordt niet alle leveringsgeschiedenis van de ontvanger verwijderd. Als u echter een ontvanger rechtstreeks in de map &#39;Ontvangers&#39; verwijdert, worden alle gegevens die aan deze ontvanger zijn gekoppeld, ook verwijderd.

### Gegevens verrijken en wijzigen {#enriching-and-modifying-data}

Naast het richten afmeting, laat de het filtreren afmeting u de aard van de verzamelde gegevens specificeren. Verwijs naar [ het richten en het filtreren dimensies ](building-a-workflow.md#targeting-and-filtering-dimensions).

De geïdentificeerde en verzamelde gegevens kunnen worden verrijkt, geaggregeerd en gemanipuleerd om de doelconstructie te optimaliseren. Om dit te doen, naast de activiteiten van de gegevensmanipulatie die in de [ worden gedetailleerd het Segmenteren gegevens ](#segmenting-data) sectie, gebruik het volgende:

* Met de activiteit **[!UICONTROL Enrichment]** kunt u tijdelijk kolommen aan een schema toevoegen en informatie aan bepaalde elementen toevoegen. Het is gedetailleerd in de [ sectie van de Verrijking ](enrichment.md) van de bewaarplaats van activiteiten.
* Met de **[!UICONTROL Edit schema]** -activiteit kunt u de structuur van een schema wijzigen. Het wordt gedetailleerd in [ uitgeeft schema ](edit-schema.md) sectie van de bewaarplaats van activiteiten.
* Met de **[!UICONTROL Change dimension]** -activiteit kunt u de doeldimensie tijdens de constructiecyclus van het doel wijzigen. Het wordt gedetailleerd in de [ dimensie van de Verandering ](change-dimension.md) sectie.
