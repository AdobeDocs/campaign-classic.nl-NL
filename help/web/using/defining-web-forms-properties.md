---
solution: Campaign Classic
product: campaign
title: Eigenschappen voor webformulieren definiëren
description: Eigenschappen voor webformulieren definiëren
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 1%

---


# Eigenschappen voor webformulieren definiëren{#defining-web-forms-properties}

Webformulieren zijn volledig configureerbaar en aanpasbaar om aan uw vereisten te voldoen. De parameters moeten in het eigenschappenvenster worden ingevoerd.

Het eigenschappenvenster is toegankelijk via de knop **[!UICONTROL Properties]** op de werkbalk van het webformulier. In dit venster hebt u toegang tot een reeks instellingen die specifiek zijn voor het webformulier. Sommige instellingen zijn mogelijk afkomstig uit de sjabloonconfiguratie.

![](assets/s_ncs_admin_survey_properties_general.png)

## Algemene formuliereigenschappen {#overall-form-properties}

Op het tabblad **[!UICONTROL General]** van het eigenschappenvenster kunt u de **Label** van het formulier wijzigen. Het wordt sterk geadviseerd om **Interne naam** niet te veranderen.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

De formuliersjabloon wordt gekozen tijdens het maken van het formulier. Deze kan later niet worden gewijzigd. Raadpleeg [Een webformuliersjabloon gebruiken](../../web/using/using-a-web-form-template.md) voor meer informatie over het maken en beheren van formuliersjablonen.

## Opslag van formuliergegevens {#form-data-storage}

De gebieden van de vormen van het Web worden opgeslagen in de ontvangenlijst door gebrek. U kunt de tabel wijzigen door een nieuwe tabel te selecteren in het veld **[!UICONTROL Document type]**. Met het pictogram **[!UICONTROL Zoom]** kunt u de inhoud van de geselecteerde tabel weergeven.

Door gebrek, worden de antwoorden opgeslagen in **Antwoord aan een ontvankelijke vorm** lijst.

## Een foutpagina instellen {#setting-up-an-error-page}

U kunt een foutpagina configureren: deze pagina wordt weergegeven in het geval van fouten tijdens de uitvoering van het formulier.

De foutpagina wordt gedefinieerd op het bijbehorende tabblad van het venster met formuliereigenschappen.

Standaard wordt de volgende informatie weergegeven:

![](assets/s_ncs_admin_survey_default_error_page.png)

De inhoud van de weergegeven tekenreeksen wordt gedefinieerd op het tabblad **[!UICONTROL Error page]** van het eigenschappenvenster. Op het tabblad **[!UICONTROL HTML]** wordt de rendering weergegeven en op het tabblad **[!UICONTROL Texts]** kunt u de tekstreeksen wijzigen en zo nodig tekst toevoegen:

![](assets/s_ncs_admin_survey_error_page.png)

## Formulierlokalisatie {#form-localization}

Op het tabblad **[!UICONTROL Localization]** kunt u de ontwerp- en weergavetalen voor het webformulier selecteren.

Zie [Een webformulier vertalen](../../web/using/translating-a-web-form.md).

## Door formulieren bladeren en weergeven {#form-browsing-and-rendering}

Met het tabblad **[!UICONTROL Rendering]** kunt u het type bladeren tussen pagina&#39;s van het webformulier en de gebruikte renderingsjabloon definiëren.

U kunt navigeren via koppelingen of knoppen.

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

Knoppen zijn standaard de navigatie-elementen. Hiermee kunt u de volgende handelingen uitvoeren:

* Goedkeuren van de huidige pagina en de volgende pagina weergeven door op **[!UICONTROL Next]** te klikken. Deze knop wordt op alle pagina&#39;s weergegeven, behalve op de laatste.
* Geef de vorige pagina weer door op **[!UICONTROL Previous]** te klikken. Deze knop wordt op alle pagina&#39;s weergegeven, behalve op de eerste.
* Sla de formulierreacties op door op de knop **[!UICONTROL Approve]** te klikken. Deze knop wordt alleen op de laatste pagina weergegeven.

Deze elementen worden onder aan elke pagina weergegeven. Hun standpunten kunnen worden gewijzigd. Hiervoor moet u het stijlblad wijzigen.

>[!NOTE]
>
>Het is mogelijk om de **[!UICONTROL Previous]** knoop op sommige pagina&#39;s te verbergen. Ga hiertoe naar de desbetreffende pagina en controleer de optie **[!UICONTROL Disallow returning to the previous page]**. Deze optie is toegankelijk wanneer de hoofdmap van de paginastructuur is geselecteerd.

In het veld **[!UICONTROL Template]** van het tabblad **[!UICONTROL Rendering]** kunt u een thema selecteren uit de beschikbare thema&#39;s.

Thema&#39;s worden opgeslagen in het knooppunt **[!UICONTROL Administration>Configuration>Form rendering]** van de boomstructuur. Zie [De rendersjabloon van het formulier selecteren](../../web/using/form-rendering.md#selecting-the-form-rendering-template)

In het onderste gedeelte van het eigenschappenvenster wordt een voorbeeld van rendering weergegeven. Met het pictogram **[!UICONTROL Edit link]** kunt u de configuratie voor het geselecteerde thema weergeven.

![](assets/s_ncs_admin_survey_properties_render.png)

## Teksten in de vorm {#texts-in-the-form}

Op het tabblad **[!UICONTROL Page]** kunt u de inhoud van de kop- en voettekst van het formulier definiëren. Zie [Kop- en voetteksten definiëren](../../web/using/form-rendering.md#defining-headers-and-footers).

U kunt hiermee ook vertalingen beheren. Zie [Een webformulier vertalen](../../web/using/translating-a-web-form.md).

## Toegankelijkheid van het formulier {#accessibility-of-the-form}

Een webformulier is toegankelijk voor gebruikers als het **[!UICONTROL Online]** is en als de huidige datum binnen de geldigheidsperiode valt. De status van het formulier wordt gewijzigd tijdens de publicatiefase (zie [Een formulier publiceren](../../web/using/publishing-a-web-form.md#publishing-a-form)). De status wordt weergegeven in de sectie **Project** van het tabblad **[!UICONTROL General]** van het eigenschappenvenster.

De geldigheidsperiode loopt van **[!UICONTROL Start]** datum tot **[!UICONTROL End date]**. Als er in deze velden geen datums zijn opgegeven, is het formulier blijvend geldig.

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>Als het formulier wordt gesloten en de geldigheidsperiode ervan niet is bereikt of verlopen, of als het formulier is gesloten door de Adobe Campaign-operator, wordt een bericht weergegeven wanneer de gebruiker toegang probeert te krijgen tot het formulier. U kunt dit bericht personaliseren door **[!UICONTROL Personalize the message displayed if the form is closed...]** te klikken.

## Toegangsbeheer voor formulieren {#form-access-control}

Standaard wordt toegang tot webformulieren uitgevoerd in anonieme modus: aan alle operatoren die toegang krijgen tot het formulier, worden de rechten van de WebApp-operator toegewezen.

U kunt toegangsbeheer inschakelen voor de weergave van het formulier, bijvoorbeeld wanneer u een formulier op een intranetsite levert, om gebruikers te verifiëren. Hiervoor geeft u het venster **[!UICONTROL Properties]** van het betreffende formulier weer en klikt u op de optie **[!UICONTROL Enable access control]**, zoals hieronder wordt weergegeven:

![](assets/s_ncs_admin_survey_access_ctrl.png)

Als de pagina wordt geopend, wordt het volgende verificatieformulier weergegeven:

![](assets/s_ncs_admin_survey_access_login.png)

Aanmelding en wachtwoord zijn die welke door Adobe Campaign-operatoren worden gebruikt. Raadpleeg [deze sectie](../../platform/using/access-management.md) voor meer informatie.

Met de optie **[!UICONTROL Use a specific account]** kunt u de lees- of schrijfmachtigingen beperken van de operator die het formulier benadert. Gebruik de vervolgkeuzelijst om een operator of groep operatoren te selecteren die verantwoordelijk zijn voor het verlenen van deze machtigingen.

![](assets/s_ncs_admin_survey_access_op_select.png)

## URL-parameters van formulier {#form-url-parameters}

U kunt extra parameters in URL van een vorm toevoegen om zijn inhoud te personaliseren en een context (taal, gecodeerde ontvankelijke identiteitskaart, bedrijf, berekende formule te initialiseren die in een variabele wordt opgeslagen, etc.). Hiermee kunt u toegang geven tot één formulier via verschillende URL&#39;s en de pagina-inhoud aanpassen op basis van de waarde van de parameter(s) die in de URL is aangegeven.

Standaard biedt Adobe Campaign parameters voor het weergeven van een voorbeeld van het formulier en het controleren van fouten. U kunt nieuwe instellingen maken die zijn gekoppeld aan het formulier. Hierbij worden mogelijk de waarden van een veld in de database of van een lokale variabele gebruikt.

## Standaardparameters {#standard-parameters}

De volgende parameters zijn standaard beschikbaar:

* **Hiermee geeft u** de gecodeerde id aan.
* **om de** weergavetaal te wijzigen.
* **van** oorsprong de oorsprong van de geënquêteerde aangeven.
* **_** Hiermee wordt het weergeven van formulieren vóór publicatie en het bijhouden van fouten ondersteund. Deze parameter is bestemd voor intern gebruik (maken en fouten opsporen): wanneer u tot het formulier van het Web via dit URL toegang hebt, worden de gecreeerde verslagen niet in het volgen (rapporten) in aanmerking genomen. De oorsprong wordt afgedwongen tot de waarde **[!UICONTROL Adobe Campaign]**.

   Deze wordt gebruikt met de parameters **_preview** en/of **_debug**:

   **_** voorvertoning om de laatst opgeslagen versie weer te geven. Deze parameter mag alleen in de testfase worden gebruikt.

   **_** debuggen om het spoor van de gegevensinvoer of berekend in de pagina&#39;s van de vorm te tonen. Hiermee wordt meer informatie over fouten opgehaald, ook als het formulier eenmaal is gepubliceerd.

   >[!CAUTION]
   >
   >Wanneer het formulier via een URL wordt weergegeven met de parameter **_uuid**, wordt de waarde van de parameter **[!UICONTROL origin]** gedwongen naar **Adobe Campaign**.

## Parameters {#adding-parameters} toevoegen

Parameters kunnen worden toegevoegd via het tabblad **[!UICONTROL Parameters...]** in het venster Eigenschappen van het formulier. Zij kunnen verplicht worden gesteld, zoals hieronder wordt getoond:

![](assets/s_ncs_admin_survey_properties_param.png)

U moet een opslagplaats specificeren waarvan de waarde van de parameter zal worden teruggewonnen. Hiervoor selecteert u een van de opslagopties en klikt u op het tabblad **[!UICONTROL Storage]** om het betreffende veld of de betreffende variabele te selecteren. De opslagopties worden beschreven in [Opslagvelden van de Reactie](../../web/using/web-forms-answers.md#response-storage-fields).

De status van de geënquêteerde (0, 1 of een andere waarde) kan vervolgens aan de URL worden toegevoegd om het formulier te openen. Deze informatie kan opnieuw worden gebruikt op de pagina&#39;s van het formulier of in een testvak. De weergegeven pagina&#39;s kunnen worden geconditioneerd op basis van de waarde van de context, zoals hieronder wordt weergegeven:

1. Startpagina voor klanten (**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. Startpagina voor vooruitzichten (**status=0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. Startpagina voor andere profielen (bijvoorbeeld **status=12**):

   ![](assets/s_ncs_admin_survey_test_other.png)

Om deze vorm te vormen, creeer een testdoos en plaats het bij het begin van het diagram, zoals hieronder getoond:

![](assets/s_ncs_admin_survey_test.png)

Met het testvak kunt u de voorwaarden voor de volgorde van pagina&#39;s configureren:

![](assets/s_ncs_admin_survey_test_box.png)

