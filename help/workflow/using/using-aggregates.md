---
product: campaign
title: Aggregaten gebruiken
description: Meer informatie over het gebruik van aggregaten
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Workflows
exl-id: 12b173e9-5068-4d45-9e1e-2aecc9866e9c
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 3%

---

# Aggregaten gebruiken{#using-aggregates}



In dit geval wordt beschreven hoe de laatste ontvangers die aan de database zijn toegevoegd, automatisch kunnen worden geïdentificeerd.

Met behulp van het volgende proces wordt de aanmaakdatum van ontvangers in de database vergeleken met de laatst bekende datum waarop een ontvanger is gemaakt met een aggregaat. Alle ontvangers die op dezelfde dag zijn gemaakt, worden ook geselecteerd.

Om een **Aanmaakdatum = max (aanmaakdatum)** Als u een filter op de ontvangers typt, moet u een workflow uitvoeren om de volgende stappen te volgen:

1. Haal de ontvangers van een database op met behulp van een standaardquery. Voor meer informatie over deze stap raadpleegt u [Een query maken](query.md#creating-a-query).
1. Bereken de laatst bekende datum een ontvanger werd gecreeerd gebruikend het resultaat dat van wordt geproduceerd **max (aanmaakdatum)** aggregatiefunctie.
1. Elke ontvanger aan de samenvoegingsfunctie verbinden resulteert in het zelfde schema.
1. Ontvangers filteren met het aggregaat via het bewerkte schema.

![](assets/datamanagement_usecase_1.png)

## Stap 1: Het totale resultaat berekenen {#step-1--calculating-the-aggregate-result}

1. Maak een query. Hier, is het doel om de laatste bekende aanmaakdatum uit alle ontvangers in het gegevensbestand te berekenen. De query bevat daarom geen filter.
1. Selecteer **[!UICONTROL Add data]**.
1. Selecteer in de geopende vensters de optie **[!UICONTROL Data linked to the filtering dimension]** dan **[!UICONTROL Filtering dimension data]**.
1. In de **[!UICONTROL Data to add]** venster, voegt u een kolom toe die de maximumwaarde voor de **Aanmaakdatum** in de tabel met ontvangers. U kunt de uitdrukkingsredacteur gebruiken of ingaan **max (@created)** rechtstreeks in een veld in **[!UICONTROL Expression]** kolom. Klik vervolgens op de knop **[!UICONTROL Finish]** knop.

   ![](assets/datamanagement_usecase_2.png)

1. Klikken **[!UICONTROL Edit additional data]** dan **[!UICONTROL Advanced parameters...]**. Schakel de optie **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]** in.

   Met deze optie zorgt u ervoor dat niet alle ontvangers als resultaat worden weergegeven en dat gegevens die expliciet worden toegevoegd, niet worden bewaard. In dit geval verwijst het naar de laatste datum waarop een ontvanger is gemaakt.

   Laat de optie **[!UICONTROL Remove duplicate rows (DISTINCT)]** ingeschakeld.

## Stap 2: De ontvangers en het resultaat van de aggregatiefunctie koppelen {#step-2--linking-the-recipients-and-the-aggregation-function-result}

Om de vraag te verbinden die ontvangers behandelt aan de vraag die de berekening van de samenvoegingsfunctie uitvoert, moet u schema gebruiken uitgeeft activiteit.

1. Definieer de query voor ontvangers als een hoofdset.
1. In de **[!UICONTROL Links]** voegt u een nieuwe koppeling toe en voert u de volgende informatie in het venster in:

   * Selecteer het tijdelijke schema voor het aggregaat. De gegevens voor dit schema worden toegevoegd aan de leden van de hoofdset.
   * Selecteren **[!UICONTROL Use a simple join]** om het geaggregeerde resultaat te koppelen aan elke ontvanger van de hoofdset.
   * Geef ten slotte op dat de koppeling een **[!UICONTROL Type 11 simple link]**.

   ![](assets/datamanagement_usecase_3.png)

Het aggregatieresultaat is daarom gekoppeld aan elke ontvanger.

## Stap 3: Ontvangers filteren met het aggregaat. {#step-3--filtering-recipients-using-the-aggregate-}

Zodra de verbinding is gevestigd, maken het gezamenlijke resultaat en de ontvangers deel uit van het zelfde tijdelijke schema. Het is daarom mogelijk om een filter op het schema tot stand te brengen om de aanmaakdatum van ontvangers en de laatst bekende aanmaakdatum te vergelijken, die door de samenvoegingsfunctie wordt vertegenwoordigd. Dit filter wordt uitgevoerd met behulp van een splitsingsactiviteit.

1. In de **[!UICONTROL General]** tab, selecteert u **Ontvangers** als doelgerichte dimensie en **Schema bewerken** als het filtreren afmeting (aan filter op de binnenkomende activiteit van het overgangsschema).
1. In de **[!UICONTROL subsets]** tab, selecteert u **[!UICONTROL Add a filtering condition on the inbound population]** klik vervolgens op **[!UICONTROL Edit...]**.
1. Voeg met behulp van de expressie-editor een gelijkheidscriterium toe tussen de aanmaakdatum van de ontvangers en de aanmaakdatum die wordt berekend door het aggregaat.

   De datumtekstvelden in de database worden over het algemeen tot op de milliseconde opgeslagen. Daarom moet u deze voor de hele dag verlengen om te voorkomen dat ontvangers worden opgehaald die slechts die milliseconde hebben gemaakt.

   Om dit te doen, gebruik **ToDate** functie, beschikbaar in de uitdrukkingsredacteur, die data en uren in eenvoudige data omzet.

   De voor de criteria te gebruiken uitdrukkingen zijn derhalve:

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**: `toDate([datemax/expr####])`, waarbij expr#### betrekking heeft op het aggregaat dat is opgegeven in de query voor de aggregatiefunctie.

   ![](assets/datamanagement_usecase_4.png)

Het resultaat van de splitsingsactiviteit heeft dus betrekking op de ontvangers die op dezelfde dag zijn gemaakt als de laatst bekende aanmaakdatum.

Vervolgens kunt u andere activiteiten toevoegen, zoals een update van een lijst of een levering om de workflow te verrijken.
