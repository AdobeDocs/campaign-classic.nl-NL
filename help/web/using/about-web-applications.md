---
solution: Campaign Classic
product: campaign
title: Webapplicaties
description: Maak en deel dynamische webtoepassingen, landingspagina's en enquêtes.
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 20%

---


# Aan de slag met webapplicaties{#about-web-applications}

Met Adobe Campaign kunt u dynamische en interactieve webtoepassingen maken en publiceren met gegevens uit de database en inhoud die zijn aangepast aan de rechten van de verbonden gebruiker.

U kunt pagina&#39;s maken, zoals een bewerkingsformulier op een extranet, of meldingsformulieren, inclusief gegevens uit de database met tabellen, grafieken, invoerformulieren enzovoort. Met deze functionaliteit kunt u webpagina&#39;s ontwerpen en plaatsen waar gebruikers informatie kunnen opzoeken of invoeren.

Dit kan een abonnementsformulier zijn dat gegevens bevat die vooraf zijn geladen met informatie in de Adobe Campaign-database, zoals hieronder wordt getoond:

![](assets/webapp_form_sample.png)

Dit hoofdstuk verstrekt een overzicht van hoe te om de toepassingen van het Web te beheren.

>[!NOTE]
>
>Raadpleeg de checklist [voor](https://helpx.adobe.com/nl/campaign/kb/acc-security.html) beveiliging en privacy voor meer informatie over het optimaliseren van beveiliging voor webtoepassingen.

>[!CAUTION]
>
>Om privacyredenen raden we aan HTTPS te gebruiken voor alle externe bronnen.

## Toepassingsbereik van webtoepassing {#web-application-scope}

Webtoepassingen in Adobe Campaign bieden toegang tot de volgende mogelijkheden:

* Formulier maken met meerdere pagina&#39;s. Raadpleeg [deze pagina](../../web/using/about-web-forms.md) voor meer informatie.
* Meertalig enquêtebeheer met een geïntegreerd vertaalhulpmiddel. Raadpleeg [deze pagina](../../web/using/translating-a-web-application.md) voor meer informatie.
* Grafische paginabeheerinterface, paginalay-out met meerdere kolommen. Raadpleeg [deze pagina](../../web/using/designing-a-web-application.md) voor meer informatie.
* Renderen van personalisatie en veldpositie. Raadpleeg [deze pagina](../../web/using/editing-content.md#adding-personalization-content) voor meer informatie.
* Voorwaardelijke weergave van enquêtevelden volgens antwoorden. Raadpleeg [deze pagina](../../web/using/form-rendering.md#defining-fields-conditional-display) voor meer informatie.
* Willekeurige weergave van vragen. Raadpleeg [deze pagina](../../web/using/building-a-survey.md#adding-questions) voor meer informatie.
* Voorwaardelijke paginaweergave. Raadpleeg [deze pagina](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display) voor meer informatie.
* Informatiecontrole vóór validatie afhankelijk van het verwachte gegevenstype (nummer, e-mailadres, datum, enz.) en de verplichte velden. Raadpleeg [deze pagina](../../web/using/form-rendering.md#defining-control-settings) voor meer informatie.
* Uitnodigingen of meldingen via e-mail verzenden. Raadpleeg [deze pagina](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email) voor meer informatie.
* Aanpassing van fout- en eindberichten. Raadpleeg [deze pagina](../../web/using/defining-web-forms-properties.md#setting-up-an-error-page) voor meer informatie.
* Gebruik van afbeeldingen, video&#39;s, hypertextkoppelingen, captcha, enzovoort. Raadpleeg [deze pagina](../../web/using/editing-content.md) voor meer informatie.
* Monitoring van reacties in real time. Raadpleeg [deze pagina](../../web/using/publish--track-and-use-collected-data.md#response-tracking) voor meer informatie.

De optionele module voor het maken van **enquêtes** biedt de volgende aanvullende functies:

* Dynamische extensie van de database: het maken van reacties die niet in de oorspronkelijke gegevenssjabloon zijn opgenomen. Raadpleeg [deze pagina](../../web/using/managing-answers.md#storing-collected-answers) voor meer informatie.
* Speciale rapporten genereren. Raadpleeg [deze pagina](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys) voor meer informatie.

Vergeleken met de toepassingen van het Web, hebben de onderzoeken een vereenvoudigde grafische interface met een verminderd aantal het uitgeven controles.

>[!NOTE]
>
>Enquêtes worden in [deze sectie](../../web/using/about-surveys.md)beschreven.
>
>De algemene functies van webformulieren in Adobe Campaign worden in [deze sectie](../../web/using/about-web-forms.md)beschreven.

## Implementatie van webtoepassingen {#web-application-implementation}

Om een toepassing van het Web tot stand te brengen en te posten, moet u:

1. Maak de inhoud (velden, lijsten, tabellen, grafieken, enz.).

   U kunt ook de sectie weergeven waarin de beschikbare velden voor formulieren worden weergegeven: al deze gebieden zijn ook beschikbaar voor de toepassingen van het Web. Deze informatie is beschikbaar op [deze pagina](../../web/using/adding-fields-to-a-web-form.md).

1. Zoals vereist, kunt u het vooraf laden toevoegen, testen, en besparingsstappen, en het toegangsbeheersysteem (hoofdzakelijk binnen het kader van een Extranetpublicatie) vormen.
1. Het publiceren van de toepassing van het Web om het op een Extranet of in Adobe Campaign ter beschikking te stellen.

## Aanvankelijke configuratie webtoepassing {#web-application-initial-configuration}

De toepassing van het Web wordt gecreeerd via de **[!UICONTROL Web Applications]** verbinding in **[!UICONTROL Campaigns]** en **[!UICONTROL Profiles and targets]** lusjes.

Webtoepassingen worden opgeslagen in het **[!UICONTROL Resources > Online > Web Applications]** knooppunt van de Adobe Campaign-structuur. Configuraties worden uitgesplitst in de volgende mappen:

* **[!UICONTROL Administration > Configuration > Form renderings]**: bevat de renderingsjablonen voor de webformulierpresentatie (toepassingen en enquêtes). Met de sjabloon kunt u het formulier genereren. Er wordt ook een CSS-stijlpagina gebruikt. Deze stijlpagina kan op sjabloonniveau worden overgeladen. Raadpleeg [deze pagina](../../web/using/form-rendering.md#selecting-the-form-rendering-template) voor meer informatie.
* **[!UICONTROL Resources > Templates > Web application templates]**: bevat formuliersjablonen. Als u een formulier of een webtoepassing wilt maken, moet u beginnen met een sjabloon.

## Webtoepassingssjablonen {#web-application-templates}

Adobe Campaign biedt standaard één sjabloon per beschikbare webtoepassing.

>[!NOTE]
>
>U kunt een bestaande toepassing van het Web in een malplaatje omzetten. Selecteer hiertoe het formulier en klik met de rechtermuisknop. Selecteer **[!UICONTROL Actions > Save as template...]**.

U kunt nieuwe sjablonen maken via het **[!UICONTROL Resources > Templates > Web Application templates]** knooppunt van de Adobe Campaign-structuur.

Met de wizard Maken kunt u de opties selecteren die u wilt inschakelen, zoals hieronder wordt weergegeven.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>De beschikbare toepassingen zijn afhankelijk van uw opties en modules. Controleer hiervoor uw licentieovereenkomst.

