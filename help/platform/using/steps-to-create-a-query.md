---
product: campaign
title: Stappen om een query te maken
description: Stappen om een query te maken
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: cf914366-8bac-4d68-a0cc-2a43d102eef2
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---

# Stappen om een query te maken{#steps-to-create-a-query}



De stappen voor het bouwen van een vraag in Adobe Campaign zijn als volgt:

1. Selecteer de werktabel. Zie [Stap 1 - Kies een tabel](#step-1---choose-a-table).
1. Selecteer de gegevens die u wilt extraheren. Zie [Stap 2 - Kies de gegevens die u wilt extraheren](#step-2---choose-data-to-extract).
1. Definieer de gegevenssorteervolgorde. Zie [Stap 3 - Gegevens sorteren](#step-3---sort-data).
1. Filter de gegevens. Zie [Stap 4 - Gegevens filteren](#step-4---filter-data).
1. Maak de gegevens op. Zie [Stap 5 - Gegevens opmaken](#step-5---format-data).
1. Geef het resultaat weer. Zie [Stap 6 - Voorbeeldgegevens](#step-6---preview-data).

>[!NOTE]
>
>Al deze stappen zijn beschikbaar in de generische vraagredacteur. Wanneer een query in een andere context wordt gemaakt, kunnen sommige stappen worden weggelaten.\
>De activiteit van de Vraag wordt voorgesteld in [deze sectie](../../workflow/using/query.md).

## Stap 1 - Kies een tabel {#step-1---choose-a-table}

Selecteer de tabel met de gegevens waarop u een query wilt uitvoeren in het dialoogvenster **[!UICONTROL Document type]** venster. Indien nodig, filtert u de gegevens met het filterveld of de **[!UICONTROL Filters]** knop.

![](assets/query_editor_nveau_21.png)

## Stap 2 - Kies de gegevens die u wilt extraheren {#step-2---choose-data-to-extract}

In de **[!UICONTROL Data to extract]** Selecteer de gegevens die u wilt weergeven: deze velden vormen de uitvoerkolommen .

Selecteer bijvoorbeeld **[!UICONTROL Age]**, **[!UICONTROL Primary key]**, **[!UICONTROL Email domain]** en **[!UICONTROL City]**. De resultaten worden op basis van deze selectie geordend. Gebruik de blauwe pijlen rechts van het venster om de kolomvolgorde te wijzigen.

![](assets/query_editor_nveau_01.png)

U kunt een expressie bewerken door er een formule in op te nemen of door een proces uit te voeren voor een statistische functie. Om dit te doen, klik **[!UICONTROL Expression]** kolomveld, selecteer vervolgens **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

U kunt uitvoerkolomgegevens groeperen: om dit te doen, controleer **[!UICONTROL Yes]** in de **[!UICONTROL Group]** kolom van de **[!UICONTROL Data to extract]** venster. Deze functie genereert een resultaat rond de geselecteerde groeperingsas. Een voorbeeld van een query met groepering is beschikbaar in [deze sectie](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* De **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** kunt u &quot;groeperen door&quot; en selecteren wat is gegroepeerd (&quot;hebben&quot;). Deze functie is van toepassing op alle velden in de uitvoerkolom. Met deze optie kunt u bijvoorbeeld alle keuzen van een uitvoerkolom groeperen en een bepaald type informatie herstellen, zoals ontvangers tussen 35 en 50.

   Raadpleeg [deze sectie](../../workflow/using/querying-using-grouping-management.md) voor meer informatie.

* De **[!UICONTROL Remove duplicate rows (DISTINCT)]** Met deze functie kunt u identieke resultaten dedupliceren die in de uitvoerkolom zijn verkregen. Als u bijvoorbeeld een telling uitvoert door de velden Achternaam, Voornaam en E-mail te selecteren in de uitvoerkolom, worden de velden met identieke gegevens verwijderd, omdat dit betekent dat dezelfde contactpersoon meerdere malen in de database is ingevoerd: slechts één resultaat zal in aanmerking worden genomen .

## Stap 3 - Gegevens sorteren {#step-3---sort-data}

De **[!UICONTROL Sorting]** kunt u kolominhoud sorteren. Gebruik de pijlen om de kolomvolgorde te wijzigen:

* De **[!UICONTROL Sorting]** de kolom maakt een eenvoudige sortering mogelijk en rangschikt de kolominhoud van A naar Z of in oplopende volgorde.
* De **[!UICONTROL Descending sort]** Hiermee rangschikt u de inhoud van Z naar A en in aflopende volgorde. Dit is bijvoorbeeld handig voor het weergeven van recordverkopen: boven aan de lijst staan de hoogste cijfers .

In dit voorbeeld worden de gegevens in oplopende volgorde gesorteerd op basis van de leeftijd van de ontvanger.

![](assets/query_editor_nveau_57.png)

## Stap 4 - Gegevens filteren {#step-4---filter-data}

Met de query-editor kunt u gegevens filteren om uw zoekopdracht te verfijnen.

De aangeboden filters zijn afhankelijk van de tabel waarop de query betrekking heeft.

![](assets/query_editor_nveau_09.png)

Wanneer u de **[!UICONTROL Filtering conditions]** u krijgt toegang tot de **[!UICONTROL Target elements]** sectie: hiermee kunt u definiëren hoe de te verzamelen gegevens moeten worden gefilterd.

* Als u een nieuw filter wilt maken, selecteert u de velden, operatoren en waarden die nodig zijn voor het maken van de formule die moet worden gecontroleerd voordat de gegevens worden geselecteerd. Het is mogelijk verschillende voorwaarden te combineren (voor meer informatie hierover raadpleegt u [Filtervoorwaarden definiëren](../../platform/using/defining-filter-conditions.md)).
* Als u eerder opgeslagen filters wilt gebruiken, opent u de vervolgkeuzelijst door op de knop **[!UICONTROL Add]** klikt u op **[!UICONTROL Predefined filter]** en selecteer de gewenste versie.

   ![](assets/query_editor_15.png)

* De filters die in de **[!UICONTROL Generic query editor]** zijn beschikbaar in andere vraagtoepassingen en vice versa. Als u een filter wilt opslaan, klikt u op de knop **[!UICONTROL Save]** pictogram.

   >[!NOTE]
   >
   >Raadpleeg voor meer informatie over het maken en gebruiken van filters [Filteropties](../../platform/using/filtering-options.md).

Zoals aangetoond in het volgende voorbeeld, om alle Engelstalige ontvangers terug te krijgen, selecteer: &quot;taal van de ontvanger **gelijk aan** NL&quot;.

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>U hebt rechtstreeks toegang tot een optie door de volgende formule te typen in het dialoogvenster **Waarde** veld: **$(opties:OPTION_NAME)**.

Klik op de knop **[!UICONTROL Preview]** om het resultaat van de filtervoorwaarde weer te geven. In dit geval worden alle Engelstalige ontvangers weergegeven met hun naam, voornaam en e-mailadres.

![](assets/query_editor_nveau_98.png)

Gebruikers die vertrouwd zijn met SQL kunnen klikken op **[!UICONTROL Generate SQL query]** om de query in SQL te bekijken.

![](assets/query_editor_nveau_99.png)

## Stap 5 - Gegevens opmaken {#step-5---format-data}

Zodra u de beperkingsfilters hebt gevormd, zult u tot **[!UICONTROL Data formatting]** venster. In dit venster kunt u de uitvoerkolommen opnieuw rangschikken, gegevens transformeren en het hoofdlettergebruik van de kolomlabels wijzigen. Hiermee kunt u ook een formule op het uiteindelijke resultaat toepassen met een berekend veld.

>[!NOTE]
>
>Raadpleeg voor meer informatie over de typen berekende velden [Berekende velden maken](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

Niet-geselecteerde kolommen worden niet weergegeven in het venster met gegevensvoorvertoning.

![](assets/query_editor_nveau_10.png)

De **[!UICONTROL Transformation]** kunt u een kolomlabel wijzigen in hoofdletters of kleine letters. Selecteer de kolom en klik in het dialoogvenster **[!UICONTROL Transformation]** kolom. U kunt kiezen:

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## Stap 6 - Voorbeeldgegevens {#step-6---preview-data}

De **[!UICONTROL Data preview]** venster is de laatste fase. Klikken **[!UICONTROL Start the preview of the data]** om uw vraagresultaat te krijgen. Deze optie is beschikbaar in kolommen of in XML-indeling. Klik op de knop **[!UICONTROL Generated SQL queries]** om de query in SQL-indeling weer te geven.

In dit voorbeeld worden gegevens in oplopende volgorde gesorteerd op basis van de leeftijd van de ontvanger.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>Standaard worden alleen de eerste 200 regels weergegeven in het dialoogvenster **[!UICONTROL Data preview]** venster. Als u dit wilt wijzigen, voert u een getal in het dialoogvenster **[!UICONTROL Lines to display]** en klik op **[!UICONTROL Start the preview of the data]**.
