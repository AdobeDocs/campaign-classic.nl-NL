---
title: Stappen om een query te maken
seo-title: Stappen om een query te maken
description: Stappen om een query te maken
seo-description: null
page-status-flag: never-activated
uuid: 9668f49c-2da7-42c8-8728-8d644c787935
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: d538f489-f1ae-4682-9c21-d0300bd42b26
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Stappen om een query te maken{#steps-to-create-a-query}

U kunt als volgt een query samenstellen in Adobe Campaign:

1. Selecteer de werktabel. Zie [Stap 1 - kies een lijst](#step-1---choose-a-table).
1. Selecteer de gegevens die u wilt extraheren. Zie [Stap 2 - kies gegevens om te extraheren](#step-2---choose-data-to-extract).
1. Definieer de gegevenssorteervolgorde. Zie [Stap 3 - Gegevens](#step-3---sort-data)sorteren.
1. Filter de gegevens. Zie [Stap 4 - Gegevens](#step-4---filter-data)filteren.
1. Maak de gegevens op. Verwijs naar [Stap 5 - de gegevens](#step-5---format-data)van het Formaat.
1. Geef het resultaat weer. Zie [Stap 6 - Gegevens](#step-6---preview-data)voorvertonen.

>[!NOTE]
>
>Al deze stappen zijn beschikbaar in de generische vraagredacteur. Wanneer een query in een andere context wordt gemaakt, kunnen sommige stappen worden weggelaten.\
>De activiteit van de Vraag wordt voorgesteld in [deze sectie](../../workflow/using/query.md).

## Stap 1 - Kies een tabel {#step-1---choose-a-table}

Selecteer in het **[!UICONTROL Document type]** venster de tabel met de gegevens waarop u een query wilt uitvoeren. Indien nodig, filtert u de gegevens met het filterveld of de **[!UICONTROL Filters]** knop.

![](assets/query_editor_nveau_21.png)

## Stap 2 - Kies de gegevens die u wilt extraheren {#step-2---choose-data-to-extract}

Selecteer in het **[!UICONTROL Data to extract]** venster de gegevens die u wilt weergeven: deze velden vormen de uitvoerkolommen .

Selecteer bijvoorbeeld **[!UICONTROL Age]**, **[!UICONTROL Primary key]****[!UICONTROL Email domain]** en **[!UICONTROL City]**. De resultaten worden op basis van deze selectie geordend. Gebruik de blauwe pijlen rechts van het venster om de kolomvolgorde te wijzigen.

![](assets/query_editor_nveau_01.png)

U kunt een expressie bewerken door er een formule in op te nemen of door een proces uit te voeren voor een statistische functie. Klik hiertoe op het **[!UICONTROL Expression]** kolomveld en selecteer **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

U kunt uitvoerkolomgegevens groeperen: Om dit te doen, controleer **[!UICONTROL Yes]** in de **[!UICONTROL Group]** kolom van het **[!UICONTROL Data to extract]** venster. Deze functie genereert een resultaat rond de geselecteerde groeperingsas. Een voorbeeld van een vraag met groepering is beschikbaar in [deze sectie](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* Met de **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** functie kunt u groeperen op en selecteren wat is gegroepeerd (&quot;hebben&quot;). Deze functie is van toepassing op alle velden in de uitvoerkolom. Met deze optie kunt u bijvoorbeeld alle keuzen van een uitvoerkolom groeperen en een bepaald type informatie herstellen, zoals ontvangers tussen 35 en 50.

   Zie [deze sectie](../../workflow/using/querying-using-grouping-management.md)voor meer informatie.

* Met de **[!UICONTROL Remove duplicate rows (DISTINCT)]** functie kunt u identieke resultaten dedupliceren die in de uitvoerkolom zijn verkregen. Als u bijvoorbeeld een telling uitvoert door de velden Achternaam, Voornaam en E-mail te selecteren in de uitvoerkolom, worden de velden met identieke gegevens verwijderd, omdat dit betekent dat dezelfde contactpersoon meerdere malen in de database is ingevoerd: slechts één resultaat zal in aanmerking worden genomen .

## Stap 3 - Gegevens sorteren {#step-3---sort-data}

In het **[!UICONTROL Sorting]** venster kunt u kolominhoud sorteren. Gebruik de pijlen om de kolomvolgorde te wijzigen:

* De **[!UICONTROL Sorting]** kolom maakt een eenvoudige sortering mogelijk en rangschikt de kolominhoud van A naar Z of in oplopende volgorde.
* De **[!UICONTROL Descending sort]** rangschikt de inhoud van Z naar A en in aflopende volgorde. Dit is bijvoorbeeld handig voor het weergeven van recordverkopen: boven aan de lijst staan de hoogste cijfers .

In dit voorbeeld worden de gegevens in oplopende volgorde gesorteerd op basis van de leeftijd van de ontvanger.

![](assets/query_editor_nveau_57.png)

## Stap 4 - Gegevens filteren {#step-4---filter-data}

Met de query-editor kunt u gegevens filteren om uw zoekopdracht te verfijnen.

De aangeboden filters zijn afhankelijk van de tabel waarop de query betrekking heeft.

![](assets/query_editor_nveau_09.png)

Zodra u selecteert zult **[!UICONTROL Filtering conditions]** u tot de **[!UICONTROL Target elements]** sectie toegang hebben: hiermee kunt u definiëren hoe de te verzamelen gegevens moeten worden gefilterd.

* Als u een nieuw filter wilt maken, selecteert u de velden, operatoren en waarden die nodig zijn voor het maken van de formule die moet worden gecontroleerd voordat de gegevens worden geselecteerd. Het is mogelijk verschillende voorwaarden te combineren (zie voor meer informatie de [filtervoorwaarden](../../platform/using/defining-filter-conditions.md)definiëren).
* Als u eerder opgeslagen filters wilt gebruiken, opent u de vervolgkeuzelijst door op de **[!UICONTROL Add]** knop te klikken, klikt u **[!UICONTROL Predefined filter]** en selecteert u de gewenste filters.

   ![](assets/query_editor_15.png)

* De filters die in het **[!UICONTROL Generic query editor]** worden gecreeerd zijn beschikbaar in andere vraagtoepassingen en vice versa. Klik op het **[!UICONTROL Save]** pictogram om een filter op te slaan.

   >[!NOTE]
   >
   >Raadpleeg de [filteropties](../../platform/using/filtering-options.md)voor meer informatie over het maken en gebruiken van filters.

Zoals aangetoond in het volgende voorbeeld, om alle Engelstalige ontvangers terug te krijgen, selecteer: &quot;taal van de ontvanger **gelijk aan** EN&quot;.

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>U hebt rechtstreeks toegang tot een optie door de volgende formule te typen in het veld **Waarde** : **$(opties:OPTION_NAME)**.

Klik op het **[!UICONTROL Preview]** tabblad om het resultaat van de filtervoorwaarde weer te geven. In dit geval worden alle Engelstalige ontvangers weergegeven met hun naam, voornaam en e-mailadres.

![](assets/query_editor_nveau_98.png)

Gebruikers die bekend zijn met SQL kunnen klikken **[!UICONTROL Generate SQL query]** om de query in SQL weer te geven.

![](assets/query_editor_nveau_99.png)

## Stap 5 - Gegevens opmaken {#step-5---format-data}

Zodra u de beperkingsfilters hebt gevormd, zult u tot het **[!UICONTROL Data formatting]** venster toegang hebben. In dit venster kunt u de uitvoerkolommen opnieuw rangschikken, gegevens transformeren en het hoofdlettergebruik van de kolomlabels wijzigen. Hiermee kunt u ook een formule op het uiteindelijke resultaat toepassen met een berekend veld.

>[!NOTE]
>
>Zie Berekende velden [maken voor meer informatie over de typen berekende velden](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

Niet-geselecteerde kolommen worden niet weergegeven in het venster met gegevensvoorvertoning.

![](assets/query_editor_nveau_10.png)

Met de **[!UICONTROL Transformation]** kolom kunt u een kolomlabel wijzigen in hoofdletters of kleine letters. Selecteer de kolom en klik in de **[!UICONTROL Transformation]** kolom. U kunt kiezen:

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## Stap 6 - Voorbeeldgegevens {#step-6---preview-data}

Het **[!UICONTROL Data preview]** venster is het laatste stadium. Klik **[!UICONTROL Start the preview of the data]** om uw vraagresultaat te krijgen. Deze optie is beschikbaar in kolommen of in XML-indeling. Klik op het **[!UICONTROL Generated SQL queries]** tabblad om de query in SQL-indeling weer te geven.

In dit voorbeeld worden gegevens in oplopende volgorde gesorteerd op basis van de leeftijd van de ontvanger.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>Standaard worden alleen de eerste 200 regels weergegeven in het **[!UICONTROL Data preview]** venster. Voer een getal in het **[!UICONTROL Lines to display]** vak in en klik op **[!UICONTROL Start the preview of the data]**.

