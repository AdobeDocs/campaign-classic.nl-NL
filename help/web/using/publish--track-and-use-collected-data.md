---
title: Gezamelde gegevens publiceren, bijhouden en gebruiken
seo-title: Gezamelde gegevens publiceren, bijhouden en gebruiken
description: Gezamelde gegevens publiceren, bijhouden en gebruiken
seo-description: null
page-status-flag: never-activated
uuid: eac16f2c-0423-4727-a2da-3af1d6c616ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 434a4bda-0907-42a7-8a75-2db658bba046
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Gezamelde gegevens publiceren, bijhouden en gebruiken{#publish-track-and-use-collected-data}

Nadat het formulier is gemaakt, geconfigureerd en gepubliceerd, kunt u de koppeling delen met uw publiek en de reacties volgen.

>[!NOTE]
>
>De levenscyclus van een onderzoek in de Campagne van Adobe evenals zijn het publiceren en leveringswijzen zijn gelijkaardig aan die van Web: deze worden in [dit gedeelte](../../web/using/about-web-forms.md)nader toegelicht.

## Beoordelingsdashboard {#survey-dashboard}

Elk onderzoek heeft zijn eigen dashboard dat u zijn status, beschrijving, openbare URL en beschikbaarheidsprogramma laat bekijken. U kunt ook de beschikbare rapporten weergeven. Zie [Rapporten over enquêtes](#reports-on-surveys)voor meer informatie hierover.

De openbare URL van de enquête wordt weergegeven op het dashboard:

![](assets/survey_public_url.png)

## Respons bijhouden {#response-tracking}

U kunt de antwoorden op de enquête bijhouden in logboeken en rapporten.

### Beoordelingslogboeken {#survey-logs}

Voor elke geleverde enquête kunt u de antwoorden op het **[!UICONTROL Logs]** tabblad bijhouden. Op dit tabblad ziet u de lijst met gebruikers die de enquête hebben voltooid en de oorsprong van de enquête:

![](assets/s_ncs_admin_survey_logs.png)

Dubbelklik op een regel om het enquêteformulier weer te geven zoals het door de geënquêteerde is ingevuld. U kunt de enquête volledig doorbladeren en de antwoorden volledig openen. Deze bestanden kunnen in een extern bestand worden geëxporteerd. Raadpleeg Antwoorden [exporteren voor meer informatie](#exporting-answers).

De oorsprong wordt aangegeven in de URL van de enquête door de volgende tekens toe te voegen:

```
?origin=xxx
```

terwijl het onderzoek wordt uitgegeven, bevat zijn URL de parameter **[!UICONTROL __uuid]**, die erop wijst dat het in een testfase en nog niet online is. Wanneer u de enquête opent via deze URL, wordt er geen rekening gehouden met de gemaakte records in de tracering (rapporten). De oorsprong wordt gedwongen tot de waarde **[!UICONTROL Adobe Campaign]**.

Raadpleeg [deze pagina](../../web/using/defining-web-forms-properties.md#form-url-parameters)voor meer informatie over URL-parameters.

### Verslagen over enquêtes {#reports-on-surveys}

Op het tabblad dashboard hebt u toegang tot enquêterapporten. Klik op een rapportnaam om deze weer te geven.

![](assets/s_ncs_admin_survey_report_doc.png)

De structuur van de enquête wordt in het **[!UICONTROL Documentation]** rapport weergegeven.

Op het **[!UICONTROL Reports]** tabblad van de enquêtes zijn nog twee andere rapporten over de webinspecties beschikbaar: **[!UICONTROL General]** en **[!UICONTROL Breakdown of responses]**.

* Algemeen

   Dit verslag bevat algemene informatie over de enquête: hoe het aantal reacties in de loop der tijd verandert en hoe de verdeling per oorsprong en taal is.

   Voorbeeld van een algemeen rapport:

   ![](assets/s_ncs_admin_survey_report_0.png)

* Uitsplitsing van reacties

   In dit verslag worden de antwoorden voor elke vraag uitgesplitst. Deze indeling is alleen beschikbaar voor antwoorden op velden die zijn opgeslagen in **[!UICONTROL Question]** tekstcontainers. Deze is alleen geldig voor selectiecontroles (bijvoorbeeld geen uitsplitsing op tekstvelden).

   ![](assets/s_ncs_admin_survey_report_2.png)

## Antwoorden exporteren {#exporting-answers}

Antwoorden op een enquête kunnen worden geëxporteerd in een extern bestand dat later wordt verwerkt. Er zijn twee manieren om dit te doen:

1. Rapportgegevens exporteren

   Als u rapportgegevens wilt exporteren, klikt u op de **[!UICONTROL Export]** knop en kiest u de exportindeling.

   Raadpleeg [deze sectie](../../reporting/using/about-reports-creation-in-campaign.md)voor meer informatie over het exporteren van rapportgegevens.

1. Antwoorden exporteren

   Als u antwoorden wilt exporteren, klikt u op het **[!UICONTROL Responses]** tabblad van de enquête en klikt u met de rechtermuisknop. Selecteer **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Voer vervolgens de gegevens in die u wilt exporteren en het opslagbestand.

   U kunt de inhoud en indeling van het uitvoerbestand configureren in de wizard Exporteren.

   Hiermee kunt u:

   * kolommen toevoegen aan het uitvoerbestand en de informatie over de ontvanger (die in de database is opgeslagen) herstellen;
   * de indeling van de geëxporteerde gegevens;
   * Selecteer de coderingsindeling voor de gegevens in het bestand.
   Als het onderzoek u wilt uitvoeren verscheidene **[!UICONTROL Multi-line text]** of **[!UICONTROL HTML text]** gebieden bevat, moet het in **[!UICONTROL XML]** formaat worden uitgevoerd. U doet dit door deze indeling te selecteren in de vervolgkeuzelijst van het **[!UICONTROL Output format]** veld, zoals hieronder wordt weergegeven:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Klik **[!UICONTROL Start]** om het exporteren uit te voeren.

   >[!NOTE]
   >
   >De uitvoer van gegevens en de stadia van hun configuratie zijn gedetailleerd in [deze sectie](../../platform/using/generic-imports-and-exports.md).

## De verzamelde gegevens gebruiken {#using-the-collected-data}

De informatie die via online enquêtes wordt verzameld, kan worden teruggevonden in het kader van een gerichte workflow. Gebruik hiervoor het **[!UICONTROL Survey responses]** vak.

In het volgende voorbeeld, willen wij een aanbieding van het Web speciaal voor de vijf ontvangers met minstens twee kinderen en met de hoogste scores bij een online onderzoek maken. De antwoorden op deze enquête zijn:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

In de het richten werkschema, **[!UICONTROL Survey responses]** zal als volgt worden gevormd:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Selecteer eerst de desbetreffende enquête en vervolgens de gegevens die u wilt extraheren in het centrale gedeelte van het venster. In dit geval moeten we ten minste de kolom met de score extraheren, aangezien deze in het gesplitste vak wordt gebruikt om de vijf hoogste scores te herstellen.

Wijs op de het filtreren voorwaarden voor antwoorden door de **[!UICONTROL Edit query...]** verbinding te klikken.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Start de doelworkflow. De query herstelt 8 ontvangers.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Klik met de rechtermuisknop op de uitvoerovergang van het verzamelingsvak om deze te bekijken.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Plaats vervolgens een gesplitst vak in de workflow om de 5 ontvangers met de hoogste score te herstellen.

Bewerk het gesplitste vak om het te configureren:

* Begin door het adequate schema op het **[!UICONTROL General]** lusje te selecteren, dan vorm de ondergroep:

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Ga naar het **[!UICONTROL Sub-sets]** tabblad en selecteer de **[!UICONTROL Limit the selected records]** optie en klik vervolgens op de **[!UICONTROL Edit...]** koppeling.

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Selecteer de **[!UICONTROL Keep only the first records after sorting]** optie en selecteer de sorteerkolom. Schakel de **[!UICONTROL Descending sort]** optie in.

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Klik op de **[!UICONTROL Next]** knop en beperkt het aantal records tot 5.

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Klik **[!UICONTROL Finish]** dan opnieuw begin de werkschema om het richten goed te keuren.

## Gegevens standaardiseren {#standardizing-data}

Het is mogelijk om normalisatieprocessen in de Campagne van Adobe op te zetten voor gegevens die gebruikend aliassen worden verzameld. Zo kunt u de gegevens standaardiseren die in de database zijn opgeslagen: Hiertoe definieert u aliassen in de gespecificeerde lijsten die de relevante informatie bevatten.

Raadpleeg [deze pagina](../../platform/using/managing-enumerations.md#about-enumerations)voor meer informatie.
