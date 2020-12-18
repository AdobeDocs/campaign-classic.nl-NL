---
solution: Campaign Classic
product: campaign
title: Antwoorden beheren
description: Antwoorden beheren
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 1%

---


# Antwoorden beheren{#managing-answers}

## Opgeslagen antwoorden opslaan {#storing-collected-answers}

Naast de standaard opslagwijzen die voor alle vormen van het Web in Adobe Campaign (gegevensbestandgebied en lokale variabele) gemeenschappelijk zijn, laten de onderzoeken de dynamische uitbreiding van het gegevensmodel toe gebruikend gearchiveerde gebieden.

>[!CAUTION]
>
>Deze optie is beschikbaar voor **Enquête** type slechts de toepassingen van het Web. Het wordt niet aangeboden voor andere soorten de vormen van het Web.

### Opslaan in een gearchiveerd veld {#storing-in-an-archived-field}

Het is gemakkelijk om het gegevensmalplaatje uit te breiden door nieuwe opslagruimten toe te voegen om de reacties te bewaren die in onderzoeken worden verstrekt. Om dit te doen, selecteer **[!UICONTROL Store answers to a question]** optie wanneer het creëren van het inputgebied. Klik op de koppeling **[!UICONTROL New field...]** en geef de eigenschappen ervan op:

![](assets/s_ncs_admin_survey_new_space.png)

Voer het label en de naam van het veld in en selecteer het veldtype: Tekst, Boolean, Geheel getal of decimaal getal, Datum, enzovoort.

Het geselecteerde veldtype bevat een besturingselement voor de gegevens wanneer de gebruikers de reacties invoeren. Voor **text** gebieden, kunt u een beperking (geval, formaat) of verbinding aan een bestaande opsomming toevoegen om selectie te dwingen.

Als u een restrictie wilt toevoegen, selecteert u deze in de vervolgkeuzelijst. Er zijn twee soorten beperkingen:

1. Teken

   De ingevoerde informatie kan in de volgende notaties in het veld worden opgeslagen: in hoofdletters, in kleine letters of in hoofdletters. Deze beperking vereist niet dat de gebruiker de gegevens in de geselecteerde indeling invoert, maar de inhoud die in het veld wordt ingevoerd, wordt geconverteerd wanneer deze wordt opgeslagen.

1. Gegevensindeling

Als dit veld wordt gebruikt in een lijst, kunnen de waarden van de opsomming automatisch worden opgehaald in de waardetabel met behulp van de koppeling **[!UICONTROL Initialize the list of values from the database]** boven de lijst met waarden.

U kunt bijvoorbeeld een vervolgkeuzelijst maken waarin de gebruiker zijn of haar eigen taal kan selecteren. Het overeenkomstige gearchiveerde gebied kan met de **language** opsomming worden geassocieerd die een lijst van talen bevat:

![](assets/s_ncs_admin_survey_database_values_2b.png)

Met het pictogram **[!UICONTROL Edit link]** rechts van het veld kunt u de inhoud van deze opsomming bewerken:

![](assets/s_ncs_admin_survey_database_values_2c.png)

Op het **[!UICONTROL General]** lusje van het gebied, laat **[!UICONTROL Initialize the list of values from the database]** u automatisch de lijst van aangeboden etiketten ingaan.

![](assets/s_ncs_admin_survey_database_values_2.png)

**Voorbeeld**: de contracten van een ontvanger in één veld opslaan

Als u verschillende typen contracten in één veld wilt opslaan, maakt u een invoerveld **[!UICONTROL Text]** en selecteert u de optie **[!UICONTROL Store answers to a question]**.

Klik op de koppeling **[!UICONTROL New field...]** en voer de veldeigenschappen in. Selecteer de optie **[!UICONTROL Multiple values]** als u meerdere waarden wilt opslaan.

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

Maak invoervelden voor de andere contracten en sla de gegevens op in hetzelfde gearchiveerde veld.

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

Wanneer gebruikers de enquête goedkeuren, worden hun antwoorden opgeslagen in het veld **[!UICONTROL Contracts]**.

In ons voorbeeld, voor de volgende antwoorden:

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

Het profiel van de respondent bevat de vier contracten die zijn aangegaan.

U kunt deze weergeven op het tabblad **[!UICONTROL Answers]** van de enquête door de desbetreffende kolommen weer te geven.

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

U kunt ontvangers ook filteren op basis van antwoorden om alleen de gebruikers weer te geven die u interesseren. Hiertoe maakt u een doelworkflow en gebruikt u het vak **[!UICONTROL Survey responses]**.

![](assets/s_ncs_admin_survey_read_responses_wf.png)

Maak uw query op basis van de profielen die u wilt herstellen. In het volgende voorbeeld kunt u met de query profielen selecteren met ten minste twee contracten, inclusief een A-typecontract.

![](assets/s_ncs_admin_survey_read_responses_edit.png)

Voor elk formulier kunnen de antwoorden worden gebruikt in velden of labels. Gebruik de volgende syntaxis voor inhoud die is opgeslagen in een gearchiveerd veld:

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>Voor andere typen velden wordt de syntaxis beschreven in [deze sectie](../../platform/using/about-queries-in-campaign.md).

### Opslaginstellingen {#storage-settings}

Het is mogelijk om antwoorden op enquêtes in XML-indeling te archiveren. Hiermee kunt u een onbewerkte kopie van de verzamelde antwoorden opslaan. Dit kan handig zijn in geval van buitensporige standaardisering van de gegevens in een gespecificeerde lijst (zie [Gegevens standaardiseren](../../web/using/publish--track-and-use-collected-data.md#standardizing-data) voor meer informatie).

>[!CAUTION]
>
>Door het archiveren van onbewerkte reacties neemt de vereiste opslagruimte aanzienlijk toe. Wees voorzichtig met deze optie.

Dit doet u als volgt:

* Bewerk de eigenschappen van de enquête via de knop **[!UICONTROL Properties]** op het tabblad **[!UICONTROL Edit]**.
* Klik op de koppeling **[!UICONTROL Advanced parameters]** en controleer de optie **[!UICONTROL Save a copy of raw answers]**.

![](assets/s_ncs_admin_survey_xml_archive_option.png)

U kunt deze optie standaard inschakelen voor alle enquêtes (deze optie wordt toegepast wanneer de enquête wordt gepubliceerd). Hiervoor maakt u de optie **[!UICONTROL NmsWebApp_XmlBackup]** en wijst u er waarde **[!UICONTROL 1]** aan toe, zoals hieronder wordt weergegeven:

![](assets/s_ncs_admin_survey_xml_global_option.png)

## Score-beheer {#score-management}

U kunt een score toewijzen aan de opties op de pagina&#39;s van het formulier. Scores kunnen alleen worden gekoppeld aan gesloten vragen: selectievakje, waarde uit een vervolgkeuzelijst, abonnement, enz.

>[!CAUTION]
>
>Score management is alleen beschikbaar voor **Enquêtes**.

![](assets/s_ncs_admin_survey_score_create.png)

De scores worden verzameld en op de server opgeslagen wanneer de pagina wordt bevestigd, dat wil zeggen wanneer de gebruiker op de knop **[!UICONTROL Next]** of **[!UICONTROL Finish]** klikt.

>[!NOTE]
>
>U kunt positieve of negatieve waarden, gehele getallen of niet-gehele getallen gebruiken.

Scores kunnen worden gebruikt in tests of scripts.

>[!CAUTION]
>
>Scores kunnen niet worden gebruikt in de zichtbaarheidsvoorwaarden voor velden die zich op dezelfde pagina bevinden. Ze kunnen echter wel op volgende pagina&#39;s worden gebruikt.

* Als u scores wilt gebruiken in tests, gebruikt u het veld **[!UICONTROL Score]** in de formule voor de testberekening, zoals hieronder wordt getoond:

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* U kunt de score in een script gebruiken.

**Voorbeeld**: Bereken een score en gebruik deze als voorwaarde voor de weergave van de volgende pagina:

* In een enquête kunt u op de volgende pagina verschillende scores toewijzen aan gebruikers, afhankelijk van de waarde die is geselecteerd in de vervolgkeuzelijst:

   ![](assets/s_ncs_admin_survey_score_exa.png)

* U kunt deze score combineren met een tweede waarde, afhankelijk van de geselecteerde optie:

   ![](assets/s_ncs_admin_survey_score_exb.png)

* Wanneer de gebruiker op de knop **[!UICONTROL Next]** klikt, worden de twee waarden opgeteld.

   ![](assets/s_ncs_admin_survey_score_exe.png)

* De voorwaarden kunnen worden toegepast voor de pagina die volgens de score moet worden getoond. Dit is als volgt geconfigureerd:

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)

