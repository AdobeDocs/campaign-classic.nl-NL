---
product: campaign
title: Belangrijke stappen bij het maken van een enquête
description: Uw eerste enquête maken met Campagne
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Surveys
exl-id: 22e14b24-59ba-4a92-8ffb-f5336793d64f
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 1%

---

# Belangrijke stappen bij het maken van een enquête{#getting-started-with-surveys}



Hier volgt een snel overzicht van de belangrijkste stappen om een eenvoudig onderzoek tot stand te brengen, gebruikend het volgende ingebouwde malplaatje:

![](assets/s_ncs_admin_survey_result.png)

Deze stappen zijn:

1. [ Stap 1 - creeer een onderzoek ](#step-1---creating-a-survey),
1. [ Stap 2 - selecteer het malplaatje ](#step-2---selecting-the-template),
1. [ Stap 3 - bouw het onderzoek ](#step-3---building-the-survey),
1. [ Stap 4 - creeer de paginainhoud ](#step-4---creating-the-page-content),
1. [ Stap 5 - sla de onderzoeksgegevens ](#step-5---storing-the-survey-data-) op,
1. [ Stap 6 - Publish de pagina&#39;s ](#step-6---publishing-the-pages),
1. [ Stap 7 - deel uw online onderzoek ](#step-7---sharing-your-online-survey).

## Stap 1 - Een enquête maken {#step-1---creating-a-survey}

Als u een nieuwe enquête wilt maken, gaat u naar de tab **[!UICONTROL Campaigns]** of **[!UICONTROL Profiles and targets]** en klikt u op het menu **[!UICONTROL Web Applications]** . Klik op de knop **[!UICONTROL Create]** boven de lijst met formulieren.

![](assets/s_ncs_admin_survey_create.png)

## Stap 2 - Selecteer de sjabloon {#step-2---selecting-the-template}

Selecteer een enquêtemalplaatje, dan geef het onderzoek een naam. Deze naam is niet zichtbaar voor de eindgebruikers, maar maakt het mogelijk de enquête te identificeren binnen Adobe Campaign. Klik op **[!UICONTROL Save]** om de enquête toe te voegen aan de lijst met webtoepassingen.

![](assets/s_ncs_admin_survey_wz_00.png)

## Stap 3 - Bouw het onderzoek {#step-3---building-the-survey}

Enquêtes zijn ingebouwd in een diagram met de volgende elementen: de pagina(&#39;s) waar de inhoud wordt gemaakt, de stappen voor het vooraf laden en opslaan van gegevens en de testfasen. Scripts en query&#39;s kunnen ook worden ingevoegd.

Klik op de **[!UICONTROL Edit]** -vorm van de enquête om het diagram te maken.

Een onderzoek moet **minstens** de volgende drie componenten bevatten: een pagina, een opslagdoos, en een eindpagina.

* Als u een pagina wilt maken, selecteert u het **[!UICONTROL Page]** -object in het linkergedeelte van de editor en plaatst u het object in het middelste gedeelte, zoals hieronder wordt getoond:

  ![](assets/s_ncs_admin_survey_new_page.png)

* Selecteer vervolgens het **[!UICONTROL Storage]** -object en plaats dit op de uitvoerovergang van de pagina.
* Selecteer ten slotte het **[!UICONTROL End]** -object en plaats dit aan het einde van de uitvoerovergang van het opslagvak om het volgende diagram te verkrijgen:

  ![](assets/s_ncs_admin_survey_end.png)

## Stap 4 - De pagina-inhoud maken {#step-4---creating-the-page-content}

In het volgende voorbeeld gebruiken we een **[!UICONTROL Page (v5 compatibility)]** tekstpagina. Dit type pagina is toegankelijk via het geavanceerde menu op de tab **[!UICONTROL Edit]** .

![](assets/s_ncs_admin_survey_pagev5.png)

* **voeg inputgebieden** toe

  Als u de inhoud van de pagina wilt maken, moet u deze bewerken. Dubbelklik hiertoe op het object **[!UICONTROL Page]** . Klik op het eerste pictogram op de werkbalk om de assistent voor het maken van velden te openen. Selecteer **[!UICONTROL Edit a recipient]** als u een invoerveld wilt maken waarin de gebruikersnaam wordt opgeslagen in het overeenkomende veld van het profiel van de ontvanger.

  ![](assets/s_ncs_admin_survey_add_field_menu.png)

  Klik op de knop **[!UICONTROL Next]** om het veld voor gegevensopslag in de database te selecteren. In dit geval het veld Achternaam.

  ![](assets/s_ncs_admin_survey_choose_field.png)

  Klik op **[!UICONTROL Finish]** om het maken van velden te bevestigen.

  Wanneer de informatie wordt opgeslagen in een veld dat al in de database bestaat, neemt het veld standaard de naam van het geselecteerde veld over, in dit voorbeeld &#39;Achternaam&#39;. U kunt dit label wijzigen zoals hieronder wordt getoond:

  ![](assets/s_ncs_admin_survey_change_label.png)

  Maak nu een invoerveld voor het gebruikersaccountnummer. Herhaal de bewerking en selecteer Account No. veld.

  Pas dezelfde procedure toe om een veld toe te voegen waarin de gebruiker een e-mailadres kan invoeren.

* **creeer een vraag**

  Als u een vraag wilt maken, klikt u met de rechtermuisknop op het laatste element in de structuur en selecteert u **[!UICONTROL Containers > Question]** . U kunt ook op het pictogram **[!UICONTROL Containers]** klikken en **[!UICONTROL Question]** selecteren.

  ![](assets/s_ncs_admin_survey_add_qu.png)

  Voer het label van de vraag in en voeg het (de) antwoordveld(en) in als een subvertakking van de vraag. Hiervoor moet het knooppunt dat aan de vraag is gekoppeld, worden geselecteerd wanneer u het antwoordveld maakt. Voeg een **[!UICONTROL drop-down listx]** toe met behulp van het pictogram **[!UICONTROL Selection controls]** of door met de rechtermuisknop te klikken, zoals hieronder wordt getoond:

  ![](assets/s_ncs_admin_survey_add_list.png)

  Selecteer een opslagruimte: selecteer een opsomveld om de waarden automatisch op te halen (in dit geval de e-mailindeling).

  ![](assets/s_ncs_admin_survey_add_itz_list.png)

  Klik op het tabblad **[!UICONTROL General]** op de koppeling **[!UICONTROL Initialize the list of values from the database]** : de waardetabel wordt automatisch ingevoerd.

  ![](assets/s_ncs_admin_survey_add_value.png)

  Klik op **[!UICONTROL OK]** om de editor te sluiten en op **[!UICONTROL Save]** om de wijzigingen op te slaan.

  >[!NOTE]
  >
  >Voor elk veld of elke vraag kunt u de paginalay-out aan uw wensen aanpassen, dankzij de opties op het tabblad **[!UICONTROL Advanced]** . De lay-out van de onderzoeksschermen wordt gedetailleerd in [ deze sectie ](../../web/using/about-web-forms.md).

  Klik in het detailscherm op het tabblad **[!UICONTROL Preview]** om de weergave weer te geven van de enquête die u zojuist hebt gemaakt.

  ![](assets/s_ncs_admin_survey_preview.png)

## Stap 5 - sla de enquêtegegevens op {#step-5---storing-the-survey-data-}

In het opslagvak kunt u de gebruikersreacties opslaan in de database. U moet een afstemmingssleutel selecteren om de profielen te identificeren die reeds in het gegevensbestand zijn.

Hiervoor bewerkt u het vak en selecteert u het veld dat wordt gebruikt als afstemmingssleutel wanneer de gegevens worden opgeslagen.

In het onderstaande voorbeeld wordt het profiel bijgewerkt wanneer het opslaan (bevestiging) plaatsvindt en een profiel wordt opgeslagen in de database met hetzelfde accountnummer als de ingevoerde gegevens in het formulier. Als het profiel niet bestaat, wordt het gemaakt.

![](assets/s_ncs_admin_survey_save_edit.png)

Klik op **[!UICONTROL OK]** om te bevestigen en klik vervolgens op **[!UICONTROL Save]** om de enquête op te slaan

## Stap 6 - Publish de pagina&#39;s {#step-6---publishing-the-pages}

Gebruikers kunnen pas toegang krijgen tot de HTML-pagina&#39;s als de toepassing beschikbaar is. Het moet zich niet meer in de bewerkingsfase bevinden, maar in productie. Als u een enquête in productie wilt plaatsen, moet u deze publiceren. Dit doet u als volgt:

* Klik op de knop **[!UICONTROL Publish]** boven het enquêtedashboard.
* Klik op **[!UICONTROL Start]** om de publicatie te starten en de assistent te sluiten.

  ![](assets/s_ncs_admin_survey_start_publ.png)

  De status van het onderzoek verandert in: **Online**.

  ![](assets/survey_published.png)

## Stap 7 - Deel uw online enquête {#step-7---sharing-your-online-survey}

Zodra het in productie is, is het onderzoek toegankelijk op de server en u kunt het leveren. De URL voor toegang tot de enquête wordt weergegeven op het dashboard.

![](assets/survey_url_from_dashboard.png)

Als u de enquête wilt afleveren, kunt u een bericht met een toegangskoppeling naar de doelpopulatie verzenden of de URL voor de toegang tot de enquête bijvoorbeeld op een webpagina plaatsen.

Vervolgens kunt u de antwoorden van gebruikers controleren via rapporten en logboeken. Zie [ het volgen van de Reactie ](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).

>[!CAUTION]
>
>De openbare URL bevat de interne naam van de enquête. Wanneer de interne naam wordt gewijzigd, wordt de URL automatisch bijgewerkt: alle koppelingen naar de enquête moeten ook worden bijgewerkt.
>
>Als er al leveringen met de koppeling naar het formulier zijn verzonden, werkt deze koppeling niet meer.
