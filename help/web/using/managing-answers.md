---
title: Antwoorden beheren
seo-title: Antwoorden beheren
description: Antwoorden beheren
seo-description: null
page-status-flag: never-activated
uuid: 329e2f4a-c5bc-4654-bdef-71a0818fc2b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: affecd87-00a3-4d50-92d3-31ac6228948b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Antwoorden beheren{#managing-answers}

## Opgeslagen antwoorden opslaan {#storing-collected-answers}

Naast de standaard opslagmodi die alle webformulieren in Adobe Campagne gebruiken (databaseveld en lokale variabele), maken enquêtes het mogelijk het gegevensmodel dynamisch uit te breiden met behulp van gearchiveerde velden.

>[!CAUTION]
>
>Deze optie is beschikbaar voor de toepassingen van het **TypeWeb van Onderzoek** slechts. Het wordt niet aangeboden voor andere soorten de vormen van het Web.

### Opslaan in een gearchiveerd veld {#storing-in-an-archived-field}

Het is gemakkelijk om het gegevensmalplaatje uit te breiden door nieuwe opslagruimten toe te voegen om de reacties te bewaren die in onderzoeken worden verstrekt. U doet dit door de **[!UICONTROL Store answers to a question]** optie te selecteren wanneer u het invoerveld maakt. Klik op de **[!UICONTROL New field...]** koppeling en geef de eigenschappen ervan op:

![](assets/s_ncs_admin_survey_new_space.png)

Voer het label en de naam van het veld in en selecteer het veldtype: Tekst, Boolean, Geheel getal of decimaal getal, Datum, enzovoort.

Het geselecteerde veldtype bevat een besturingselement voor de gegevens wanneer de gebruikers de reacties invoeren. Voor **tekstvelden** kunt u een beperking (hoofdletters/kleine letters, opmaak) of een koppeling naar een bestaande opsomming toevoegen om selectie te forceren.

Als u een restrictie wilt toevoegen, selecteert u deze in de vervolgkeuzelijst. Er zijn twee soorten beperkingen:

1. Teken

   De ingevoerde informatie kan in de volgende notaties in het veld worden opgeslagen: in hoofdletters, in kleine letters of in hoofdletters. Deze beperking vereist niet dat de gebruiker de gegevens in de geselecteerde indeling invoert, maar de inhoud die in het veld wordt ingevoerd, wordt geconverteerd wanneer deze wordt opgeslagen.

1. Gegevensindeling

Als dit veld wordt gebruikt in een lijst, kunnen de waarden van de opsomming automatisch worden opgehaald in de waardetabel met behulp van de **[!UICONTROL Initialize the list of values from the database]** koppeling boven de lijst met waarden.

U kunt bijvoorbeeld een vervolgkeuzelijst maken waarin de gebruiker zijn of haar eigen taal kan selecteren. Het corresponderende gearchiveerde veld kan worden gekoppeld aan de opsomming van de **taal** die een lijst met talen bevat:

![](assets/s_ncs_admin_survey_database_values_2b.png)

Met het **[!UICONTROL Edit link]** pictogram rechts van het veld kunt u de inhoud van deze opsomming bewerken:

![](assets/s_ncs_admin_survey_database_values_2c.png)

Op het **[!UICONTROL General]** tabblad van het veld kunt u met de **[!UICONTROL Initialize the list of values from the database]** koppeling automatisch de lijst met aangeboden labels invoeren.

![](assets/s_ncs_admin_survey_database_values_2.png)

**Voorbeeld**: de contracten van een ontvanger in één veld opslaan

Als u verschillende typen contracten in één veld wilt opslaan, maakt u een **[!UICONTROL Text]** invoerveld en selecteert u de **[!UICONTROL Store answers to a question]** optie.

Klik op de **[!UICONTROL New field...]** koppeling en voer de veldeigenschappen in. Selecteer de **[!UICONTROL Multiple values]** optie om meerdere waarden op te slaan.

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

Maak invoervelden voor de andere contracten en sla de gegevens op in hetzelfde gearchiveerde veld.

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

Wanneer de gebruikers het onderzoek goedkeuren, zullen hun antwoorden op het **[!UICONTROL Contracts]** gebied worden opgeslagen.

In ons voorbeeld, voor de volgende antwoorden:

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

Het profiel van de respondent bevat de vier contracten die zijn aangegaan.

U kunt de desbetreffende kolommen weergeven op het **[!UICONTROL Answers]** tabblad van de enquête.

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

U kunt ontvangers ook filteren op basis van antwoorden om alleen de gebruikers weer te geven die u interesseren. Hiertoe maakt u een doelworkflow en gebruikt u het **[!UICONTROL Survey responses]** vak.

![](assets/s_ncs_admin_survey_read_responses_wf.png)

Maak uw query op basis van de profielen die u wilt herstellen. In het volgende voorbeeld kunt u met de query profielen selecteren met ten minste twee contracten, inclusief een A-typecontract.

![](assets/s_ncs_admin_survey_read_responses_edit.png)

Voor elk formulier kunnen de antwoorden worden gebruikt in velden of labels. Gebruik de volgende syntaxis voor inhoud die is opgeslagen in een gearchiveerd veld:

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>Voor andere typen velden wordt de syntaxis in [deze sectie](../../platform/using/about-queries-in-campaign.md)beschreven.

### Opslaginstellingen {#storage-settings}

Het is mogelijk om antwoorden op enquêtes in XML-indeling te archiveren. Hiermee kunt u een onbewerkte kopie van de verzamelde antwoorden opslaan. Dit kan handig zijn in geval van buitensporige standaardisering van de gegevens in een gespecificeerde lijst (zie voor meer informatie de [standaardiseringsgegevens](../../web/using/publish--track-and-use-collected-data.md#standardizing-data)).

>[!CAUTION]
>
>Door het archiveren van onbewerkte reacties neemt de vereiste opslagruimte aanzienlijk toe. Wees voorzichtig met deze optie.

Dit doet u als volgt:

* Bewerk de eigenschappen van de enquête via de **[!UICONTROL Properties]** knop op het **[!UICONTROL Edit]** tabblad.
* Klik op de **[!UICONTROL Advanced parameters]** koppeling en controleer de **[!UICONTROL Save a copy of raw answers]** optie.

![](assets/s_ncs_admin_survey_xml_archive_option.png)

U kunt deze optie standaard inschakelen voor alle enquêtes (deze optie wordt toegepast wanneer de enquête wordt gepubliceerd). Hiervoor maakt u de **[!UICONTROL NmsWebApp_XmlBackup]** optie en wijst u er een waarde **[!UICONTROL 1]** aan toe, zoals hieronder wordt weergegeven:

![](assets/s_ncs_admin_survey_xml_global_option.png)

## Score-beheer {#score-management}

U kunt een score toewijzen aan de opties op de pagina&#39;s van het formulier. Scores kunnen alleen worden gekoppeld aan gesloten vragen: selectievakje, waarde uit een vervolgkeuzelijst, abonnement, enz.

>[!CAUTION]
>
>Score-beheer is alleen beschikbaar voor **enquêtes** .

![](assets/s_ncs_admin_survey_score_create.png)

De scores worden verzameld en op de server opgeslagen wanneer de pagina wordt bevestigd, dat wil zeggen wanneer de gebruiker op de **[!UICONTROL Next]** knop of de **[!UICONTROL Finish]** knop klikt.

>[!NOTE]
>
>U kunt positieve of negatieve waarden, gehele getallen of niet-gehele getallen gebruiken.

Scores kunnen worden gebruikt in tests of scripts.

>[!CAUTION]
>
>Scores kunnen niet worden gebruikt in de zichtbaarheidsvoorwaarden voor velden die zich op dezelfde pagina bevinden. Ze kunnen echter wel op volgende pagina&#39;s worden gebruikt.

* Als u scores wilt gebruiken in tests, gebruikt u het **[!UICONTROL Score]** veld in de testberekeningsformule, zoals hieronder wordt getoond:

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* U kunt de score in een script gebruiken.

**Voorbeeld**: Bereken een score en gebruik deze als voorwaarde voor de weergave van de volgende pagina:

* In een enquête kunt u op de volgende pagina verschillende scores toewijzen aan gebruikers, afhankelijk van de waarde die is geselecteerd in de vervolgkeuzelijst:

   ![](assets/s_ncs_admin_survey_score_exa.png)

* U kunt deze score combineren met een tweede waarde, afhankelijk van de geselecteerde optie:

   ![](assets/s_ncs_admin_survey_score_exb.png)

* Wanneer de gebruiker op de **[!UICONTROL Next]** knop klikt, worden de twee waarden opgeteld.

   ![](assets/s_ncs_admin_survey_score_exe.png)

* De voorwaarden kunnen worden toegepast voor de pagina die volgens de score moet worden getoond. Dit is als volgt geconfigureerd:

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)

