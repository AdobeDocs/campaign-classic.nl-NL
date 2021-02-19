---
solution: Campaign Classic
product: campaign
title: Voorbeelden van algemene importactiviteiten
description: Meer informatie over generieke importbewerkingen die u kunt uitvoeren met importtaken.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 37cc6cd8b71ec82cd4e6a910d6664a51ed5c091e
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 1%

---


# Voorbeelden van algemene importactiviteiten {#import-operations-samples}

## Importeren uit een lijst met ontvangers {#example--import-from-a-list-of-recipients}

Voer de volgende stappen uit om een lijst met ontvangers te maken en op te geven op basis van het overzicht van lijsten:

1. De lijst maken

   * Klik op de koppeling **[!UICONTROL Lists]** in het menu **[!UICONTROL Profiles and targets]** van de startpagina van Adobe Campaign.
   * Klik op **[!UICONTROL Create]** en vervolgens op de knop **[!UICONTROL Import a list]**.

1. Het te importeren bestand selecteren

   Klik op de map rechts van het veld **[!UICONTROL Local file]** en selecteer het bestand met de lijst die u wilt importeren.

   ![](assets/s_ncs_user_import_example00_01.png)

1. Lijstnaam en -opslag

   Voer de naam van de lijst in en selecteer de map waarin deze moet worden opgeslagen.

   ![](assets/s_ncs_user_import_example00_02.png)

1. Het importeren starten

   Klik op **[!UICONTROL Next]** en **[!UICONTROL Start]** om de lijst te importeren.

   ![](assets/s_ncs_user_import_example00_03.png)

## Nieuwe records importeren uit een tekstbestand {#example--import-new-records-from-a-text-file-}

Voer de volgende stappen uit om nieuwe, in een tekstbestand opgeslagen ontvangerprofielen te importeren in de Adobe Campaign-database:

1. Een sjabloon kiezen

   * Van de homepage van Adobe Campaign, klik **[!UICONTROL Profiles and targets]** verbinding, dan **[!UICONTROL Jobs]**. Klik boven de lijst met taken op **[!UICONTROL New import]**.
   * Laat de sjabloon **[!UICONTROL New text import]** standaard geselecteerd.
   * Wijzig het label en de beschrijving.
   * Selecteer **[!UICONTROL Simple import]**.
   * De standaardtaakmap behouden.
   * Klik **[!UICONTROL Advanced parameters]** en selecteer **[!UICONTROL Tracking mode]** optie om de details van uw invoer tijdens uitvoering te bekijken.

1. Het te importeren bestand selecteren

   Klik op de map rechts van het veld **[!UICONTROL Local file]** en selecteer het bestand dat u wilt importeren.

   ![](assets/s_ncs_user_import_example01_01.png)

1. Velden koppelen

   Klik op het pictogram **[!UICONTROL Guess the destination fields]** om de bron- en doelschema&#39;s automatisch toe te wijzen. Controleer de informatie in dit venster voordat u op **[!UICONTROL Next]** klikt.

   ![](assets/s_ncs_user_import_example03_01.png)

1. Afstemming

   * Ga naar **Ontvangers (nms:ontvanger)** lijst.
   * Selecteer de bewerking **[!UICONTROL Insertion]** en laat de standaardwaarden in de andere velden staan.

      ![](assets/s_ncs_user_import_example04_01.png)

1. Ontvangers importeren

   * Geef indien nodig een map op waarin de records moeten worden geïmporteerd.

      ![](assets/s_ncs_user_import_example05_01.png)

1. Het importeren starten

   * Klik op **[!UICONTROL Start]**.

      In het centrale gedeelte van de editor kunt u controleren of de importbewerking is voltooid en het aantal verwerkte records weergeven.

      ![](assets/s_ncs_user_import_example06_01.png)

      In de modus **[!UICONTROL Tracking]** kunt u de details van de import bijhouden voor elke record in het bronbestand. Om dit te doen, van de homepage klik **[!UICONTROL Profiles and Targets]** dan **[!UICONTROL Processes]**, selecteer de relevante invoer, en kijk omhoog **[!UICONTROL General]**, **[!UICONTROL Journal]** en **[!UICONTROL Rejects]** lusjes.

      * Voortgang van importeren controleren

         ![](assets/s_ncs_user_import_example07_01.png)

      * Procesweergave voor elke record

         ![](assets/s_ncs_user_import_example07_02.png)

## Ontvangers {#example--update-and-insert-recipients} bijwerken en invoegen

We willen bestaande records in de database bijwerken en nieuwe records maken vanuit een tekstbestand. Hier volgt een voorbeeld van de procedure:

1. Een sjabloon kiezen

   Herhaal de stappen die in voorbeeld 2 hierboven worden beschreven.

1. Te importeren bestand

   Selecteer het bestand dat u wilt importeren.

   In ons voorbeeld toont het overzicht van de eerste regels van het bestand aan dat het bestand updates bevat voor drie records en dat er een record wordt gemaakt.

   ![](assets/s_ncs_user_import_example02_02.png)

1. Velden koppelen

   Pas de procedure toe in voorbeeld 2 hierboven.

1. Afstemming

   * Laat **[!UICONTROL Update or insert]** standaard ingeschakeld.
   * Houd de optie **[!UICONTROL Management of duplicates]** in de modus **[!UICONTROL Update]**, zodat bestaande records in de database worden gewijzigd met gegevens uit het tekstbestand.
   * Selecteer de velden **[!UICONTROL Birth date]**, **[!UICONTROL Name]** en **[!UICONTROL Company]** en wijs er een afstemmingssleutel aan toe.

      ![](assets/s_ncs_user_import_example04_02.png)

1. Het importeren starten

   * Klik op **[!UICONTROL Start]**.

      In het venster Tekstspatiëring kunt u controleren of het importeren is gelukt en het aantal verwerkte records weergeven.

      ![](assets/s_ncs_user_import_example06_02.png)

   * Kijk in de ontvankelijke lijst om te controleren dat de verslagen door deze verrichting zijn gewijzigd.

      ![](assets/s_ncs_user_import_example06_03.png)

## Verrijk de waarden met die van een extern dossier {#example--enrich-the-values-with-those-of-an-external-file}

Wij willen bepaalde gebieden in een gegevensbestandlijst van een tekstdossier wijzigen, die aan de waarden in het gegevensbestand voorrang geven.

In dit voorbeeld ziet u dat bepaalde velden in het tekstbestand een waarde hebben, terwijl de bijbehorende velden in de database leeg zijn. Andere velden bevatten een andere waarde dan de waarde in de database.

* Inhoud van het tekstbestand dat moet worden geïmporteerd.

   ![](assets/s_ncs_user_import_example02_03.png)

* Databasestatus voor importeren

   ![](assets/s_ncs_user_import_example06_04.png)

Voer de volgende stappen uit:

1. Een sjabloon kiezen

   Pas de procedure toe in voorbeeld 2 hierboven.

1. Te importeren bestand

   Selecteer het bestand dat u wilt importeren.

1. Velden koppelen

   Pas de procedure toe in voorbeeld 2 hierboven.

   In de voorvertoning van de eerste regels van het bestand ziet u dat het bestand updates voor bepaalde records bevat.

1. Afstemming

   * Ga naar de lijst en selecteer **[!UICONTROL Update]** verrichting.
   * Selecteer de optie **[!UICONTROL Reject entity]** voor het **[!UICONTROL Management of doubles]** gebied.
   * Houd de optie **[!UICONTROL Management of duplicates]** in de modus **[!UICONTROL Update]**, zodat bestaande records in de database worden gewijzigd met gegevens uit het tekstbestand.
   * Plaats de cursor op het knooppunt **[!UICONTROL Last name (@lastName)]** en selecteer de optie **[!UICONTROL Update only if destination is empty]**.
   * Herhaal deze bewerking voor het knooppunt **[!UICONTROL Company (@company)]**.
   * Wijs een afstemmingssleutel aan de gebieden **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** en **[!UICONTROL First name]** toe.

      ![](assets/s_ncs_user_import_example04_03.png)

1. Het importeren starten

   Klik op **[!UICONTROL Start]**.

   Kijk in de lijst van ontvangers om te controleren dat de verslagen door de invoer zijn gewijzigd.

   ![](assets/s_ncs_user_import_example06_05.png)

   Alleen lege waarden zijn vervangen door waarden uit het tekstbestand, maar de bestaande waarde in de database is niet overschreven door de waarde uit het importbestand.

## De waarden in een extern bestand bijwerken en verrijken {#example--update-and-enrich-the-values-from-those-in-an-external-file}

We willen bepaalde velden in een databasetabel wijzigen vanuit een tekstbestand, waarbij prioriteit wordt gegeven aan de waarden in het tekstbestand.

In dit voorbeeld ziet u dat bepaalde velden in het tekstbestand een lege waarde hebben, terwijl de bijbehorende velden in de database niet leeg zijn. Andere velden bevatten een andere waarde dan de velden in de database.

* Inhoud van het tekstbestand dat moet worden geïmporteerd.

   ![](assets/s_ncs_user_import_example02_04.png)

* Databasestatus voor importeren

   ![](assets/s_ncs_user_import_example06_07.png)

1. Een sjabloon kiezen

   Pas de procedure toe in voorbeeld 2 hierboven.

1. Te importeren bestand

   Selecteer het bestand dat u wilt importeren.

   In de voorvertoning van de eerste regels van het bestand ziet u dat het bestand lege velden en updates voor bepaalde records bevat.

1. Velden koppelen

   Pas de procedure toe in voorbeeld 2 hierboven.

1. Afstemming

   * Ga naar de tabel en selecteer **[!UICONTROL Update]**.
   * Selecteer de optie **[!UICONTROL Reject entity]** voor het **[!UICONTROL Management of doubles]** gebied.
   * Laat de optie **[!UICONTROL Management of duplicates]** in de modus **[!UICONTROL Update]** staan, zodat bestaande records in de database kunnen worden gewijzigd met gegevens uit het tekstbestand.
   * Plaats de curseur op **[!UICONTROL Account number (@account)]** knoop en selecteer de optie **[!UICONTROL Take empty values into account]**.
   * Selecteer de velden **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** en **[!UICONTROL First name]** en wijs er een afstemmingssleutel aan toe.

      ![](assets/s_ncs_user_import_example04_04.png)

1. Het importeren starten

   * Klik op **[!UICONTROL Start]**.
   * Kijk in de ontvankelijke lijst om te controleren dat de verslagen door de verrichting zijn gewijzigd.

      ![](assets/s_ncs_user_import_example06_06.png)

      De waarden van het tekstbestand die leeg waren, hebben de waarden in de database overschreven. De bestaande waarden in de database zijn bijgewerkt met de waarden in het importbestand. Hierbij is de optie **[!UICONTROL Update]** geselecteerd voor duplicaten in stap 4.
