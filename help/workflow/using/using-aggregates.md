---
title: Werken met aggregaten
seo-title: Werken met aggregaten
description: Werken met aggregaten
seo-description: null
page-status-flag: never-activated
uuid: 70556745-56b2-4f22-bbc5-7f8106fb0d4a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 9ca649b4-2226-4cfe-bae1-4632c421975b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Werken met aggregaten{#using-aggregates}

In dit geval wordt beschreven hoe de laatste ontvangers die aan de database zijn toegevoegd, automatisch kunnen worden geïdentificeerd.

Met behulp van het volgende proces wordt de aanmaakdatum van ontvangers in de database vergeleken met de laatst bekende datum waarop een ontvanger is gemaakt met een aggregaat. Alle ontvangers die op dezelfde dag zijn gemaakt, worden ook geselecteerd.

Als u het filter **Aanmaakdatum = max. (Aanmaakdatum)** op de ontvangers wilt uitvoeren, moet u een workflow uitvoeren om de volgende stappen uit te voeren:

1. Haal de ontvangers van een database op met behulp van een standaardquery. Voor meer op deze stap, verwijs naar het [Creëren van een vraag](../../workflow/using/query.md#creating-a-query).
1. Bereken de laatst bekende datum dat een ontvanger is gemaakt met het resultaat dat is gegenereerd op basis van de samenvoegfunctie **max (aanmaakdatum)** .
1. Elke ontvanger aan de samenvoegingsfunctie verbinden resulteert in het zelfde schema.
1. Ontvangers filteren met het aggregaat via het bewerkte schema.

![](assets/datamanagement_usecase_1.png)

## Stap 1: Het totale resultaat berekenen {#step-1--calculating-the-aggregate-result}

1. Maak een query. Hier, is het doel om de laatste bekende aanmaakdatum uit alle ontvangers in het gegevensbestand te berekenen. De query bevat daarom geen filter.
1. Selecteer **[!UICONTROL Add data]**.
1. Selecteer **[!UICONTROL Data linked to the filtering dimension]** vervolgens in de geopende vensters **[!UICONTROL Filtering dimension data]**.
1. Voeg in het **[!UICONTROL Data to add]** venster een kolom toe die de maximumwaarde voor het veld **Aanmaakdatum** in de tabel met ontvangers berekent. U kunt de expressieeditor gebruiken of **max (@created)** rechtstreeks in een veld in de **[!UICONTROL Expression]** kolom invoeren. Klik vervolgens op de **[!UICONTROL Finish]** knop.

   ![](assets/datamanagement_usecase_2.png)

1. Klik **[!UICONTROL Edit additional data]** dan **[!UICONTROL Advanced parameters...]**. Schakel de **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]** optie in.

   Met deze optie zorgt u ervoor dat niet alle ontvangers als resultaat worden weergegeven en dat gegevens die expliciet worden toegevoegd, niet worden bewaard. In dit geval verwijst het naar de laatste datum waarop een ontvanger is gemaakt.

   Laat de **[!UICONTROL Remove duplicate rows (DISTINCT)]** optie ingeschakeld.

## Stap 2: De ontvangers koppelen en het resultaat van de aggregatiefunctie {#step-2--linking-the-recipients-and-the-aggregation-function-result}

Om de vraag te verbinden die ontvangers behandelt aan de vraag die de berekening van de samenvoegingsfunctie uitvoert, moet u schema gebruiken uitgeeft activiteit.

1. Definieer de query voor ontvangers als een hoofdset.
1. Voeg op het **[!UICONTROL Links]** tabblad een nieuwe koppeling toe en voer de informatie in het venster in dat als volgt wordt geopend:

   * Selecteer het tijdelijke schema voor het aggregaat. De gegevens voor dit schema worden toegevoegd aan de leden van de hoofdset.
   * Selecteer deze optie **[!UICONTROL Use a simple join]** om het geaggregeerde resultaat te koppelen aan elke ontvanger van de hoofdset.
   * Geef ten slotte op dat de koppeling een **[!UICONTROL Type 11 simple link]** koppeling is.
   ![](assets/datamanagement_usecase_3.png)

Het aggregatieresultaat is daarom gekoppeld aan elke ontvanger.

## Stap 3: Ontvangers filteren met het aggregaat. {#step-3--filtering-recipients-using-the-aggregate-}

Zodra de verbinding is gevestigd, maken het gezamenlijke resultaat en de ontvangers deel uit van het zelfde tijdelijke schema. Het is daarom mogelijk om een filter op het schema tot stand te brengen om de aanmaakdatum van ontvangers en de laatst bekende aanmaakdatum te vergelijken, die door de samenvoegingsfunctie wordt vertegenwoordigd. Dit filter wordt uitgevoerd met behulp van een splitsingsactiviteit.

1. In het **[!UICONTROL General]** lusje, uitgezochte **Ontvangers** als het richten dimensie en **geef schema** als het filtreren dimensie (om op de binnenkomende activiteit van het overgangsschema te filtreren) uit.
1. Selecteer op het **[!UICONTROL subsets]** tabblad de optie **[!UICONTROL Add a filtering condition on the inbound population]** en klik op **[!UICONTROL Edit...]**.
1. Voeg met behulp van de expressie-editor een gelijkheidscriterium toe tussen de aanmaakdatum van de ontvangers en de aanmaakdatum die wordt berekend door het aggregaat.

   De datumtekstvelden in de database worden over het algemeen tot op de milliseconde opgeslagen. Daarom moet u deze voor de hele dag verlengen om te voorkomen dat ontvangers worden opgehaald die slechts die milliseconde hebben gemaakt.

   Hiervoor gebruikt u de functie **ToDate** , beschikbaar in de expressieeditor, die datums en uren omzet in eenvoudige datums.

   De voor de criteria te gebruiken uitdrukkingen zijn derhalve:

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**: `toDate([datemax/expr####])`, waarbij expr#### betrekking heeft op het aggregaat dat is opgegeven in de query voor de aggregatiefunctie.
   ![](assets/datamanagement_usecase_4.png)

Het resultaat van de splitsingsactiviteit heeft dus betrekking op de ontvangers die op dezelfde dag zijn gemaakt als de laatst bekende aanmaakdatum.

Vervolgens kunt u andere activiteiten toevoegen, zoals een update van een lijst of een levering om de workflow te verrijken.
