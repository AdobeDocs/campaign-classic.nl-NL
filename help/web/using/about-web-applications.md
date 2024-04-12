---
product: campaign
title: Aan de slag met webapplicaties
description: Dynamische webtoepassingen, bestemmingspagina's en enquêtes maken en delen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Landing Pages, Web Apps
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 19%

---

# Aan de slag met webapplicaties{#about-web-applications}



Met Adobe Campaign kunt u dynamische en interactieve webtoepassingen maken en publiceren met gegevens uit de database en inhoud die zijn aangepast aan de rechten van de verbonden gebruiker.

U kunt pagina&#39;s maken, zoals een bewerkingsformulier op een extranet, of meldingsformulieren, inclusief gegevens uit de database met tabellen, grafieken, invoerformulieren enzovoort. Met deze functionaliteit kunt u webpagina&#39;s ontwerpen en plaatsen waar gebruikers informatie kunnen opzoeken of invoeren.

Dit kan een abonnementsformulier zijn dat gegevens bevat die vooraf zijn geladen met informatie in de Adobe Campaign-database, zoals hieronder wordt getoond:

![](assets/webapp_form_sample.png)

Dit hoofdstuk verstrekt een overzicht van hoe te om de toepassingen van het Web te beheren.

>[!NOTE]
>
>Zie de [Controlelijst voor beveiliging en privacy](https://helpx.adobe.com/nl/campaign/kb/acc-security.html) voor informatie over het optimaliseren van beveiliging voor webtoepassingen.

>[!CAUTION]
>
>Om privacyredenen raden we aan HTTPS te gebruiken voor alle externe bronnen.

## Toepassingsbereik van webtoepassing {#web-application-scope}

Webtoepassingen in Adobe Campaign bieden toegang tot de volgende mogelijkheden:

* Formulier maken met meerdere pagina&#39;s. Raadpleeg [deze pagina](about-web-forms.md) voor meer informatie.
* Meertalig enquêtebeheer met een geïntegreerd vertaalhulpmiddel. Raadpleeg [deze pagina](translating-a-web-application.md) voor meer informatie.
* Grafische paginabeheerinterface, paginalay-out met meerdere kolommen. Raadpleeg [deze pagina](designing-a-web-application.md) voor meer informatie.
* Renderen van personalisatie en veldpositie. Raadpleeg [deze pagina](editing-content.md#adding-personalization-content) voor meer informatie.
* Voorwaardelijke weergave van enquêtevelden volgens antwoorden. Raadpleeg [deze pagina](form-rendering.md#defining-fields-conditional-display) voor meer informatie.
* Willekeurige weergave van vragen. Raadpleeg [deze pagina](../../surveys/using/building-a-survey.md#adding-questions) voor meer informatie.
* Voorwaardelijke paginaweergave. Raadpleeg [deze pagina](defining-web-forms-page-sequencing.md#conditional-page-display) voor meer informatie.
* Informatiecontrole vóór validatie afhankelijk van het verwachte gegevenstype (nummer, e-mailadres, datum, enz.) en de verplichte velden. Raadpleeg [deze pagina](form-rendering.md#defining-control-settings) voor meer informatie.
* Uitnodigingen of meldingen via e-mail verzenden. Raadpleeg [deze pagina](publishing-a-web-form.md#delivering-a-form-via-email) voor meer informatie.
* Aanpassing van fout- en eindberichten. Raadpleeg [deze pagina](defining-web-forms-properties.md#setting-up-an-error-page) voor meer informatie.
* Gebruik van afbeeldingen, video&#39;s, hypertextkoppelingen, captcha, enzovoort. Raadpleeg [deze pagina](editing-content.md) voor meer informatie.
* Monitoring van reacties in real time. Raadpleeg [deze pagina](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking) voor meer informatie.

De optionele **Enquête** de aanmaakmodule biedt de volgende aanvullende functies:

* Dynamische extensie van de database: het maken van reacties die niet zijn opgenomen in de oorspronkelijke gegevenssjabloon. Raadpleeg [deze pagina](../../surveys/using/managing-answers.md#storing-collected-answers) voor meer informatie.
* Speciale rapporten genereren. Raadpleeg [deze pagina](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys) voor meer informatie.

Vergeleken met de toepassingen van het Web, hebben de onderzoeken een vereenvoudigde grafische interface met een verminderd aantal het uitgeven controles.

>[!NOTE]
>
>Enquêtes worden gedetailleerd weergegeven in [deze sectie](../../surveys/using/about-surveys.md).
>
>De algemene functies van webformulieren in Adobe Campaign worden beschreven in [deze sectie](about-web-forms.md).

## Implementatie van webtoepassingen {#web-application-implementation}

Als u een webtoepassing wilt maken en posten, moet u:

1. Maak de inhoud (velden, lijsten, tabellen, grafieken, enz.).

   U kunt ook de sectie weergeven waarin de beschikbare velden voor formulieren worden weergegeven: al deze velden zijn ook beschikbaar voor webtoepassingen. Deze informatie is beschikbaar in [deze pagina](adding-fields-to-a-web-form.md).

1. Zoals vereist, kunt u het vooraf laden toevoegen, testen, en besparingsstappen, en het toegangsbeheersysteem (hoofdzakelijk binnen het kader van een Extranetpublicatie) vormen.
1. Het publiceren van de toepassing van het Web om het op een Extranet of in Adobe Campaign ter beschikking te stellen.

## Aanvankelijke configuratie webtoepassing {#web-application-initial-configuration}

Webtoepassing wordt gemaakt via de **[!UICONTROL Web Applications]** in de **[!UICONTROL Campaigns]** en **[!UICONTROL Profiles and targets]** tabs.

De toepassingen van het Web worden opgeslagen in **[!UICONTROL Resources > Online > Web Applications]** knooppunt van de boomstructuur Adobe Campaign. Configuraties worden uitgesplitst in de volgende mappen:

* **[!UICONTROL Administration > Configuration > Form renderings]**: bevat de renderingsjablonen voor de webformulierpresentatie (toepassingen en enquêtes). Met de sjabloon kunt u het formulier genereren. Er wordt ook een CSS-stijlpagina gebruikt. Deze stijlpagina kan op sjabloonniveau worden overgeladen. Raadpleeg [deze pagina](form-rendering.md#selecting-the-form-rendering-template) voor meer informatie.
* **[!UICONTROL Resources > Templates > Web application templates]**: bevat formuliersjablonen. Als u een formulier of een webtoepassing wilt maken, moet u beginnen met een sjabloon.

## Webtoepassingssjablonen {#web-application-templates}

Adobe Campaign biedt standaard één sjabloon per beschikbare webtoepassing.

>[!NOTE]
>
>U kunt een bestaande toepassing van het Web in een malplaatje omzetten. Selecteer het formulier en klik met de rechtermuisknop om dit te doen. Selecteer **[!UICONTROL Actions > Save as template...]**.

U kunt nieuwe sjablonen maken via het dialoogvenster **[!UICONTROL Resources > Templates > Web Application templates]** knooppunt van de boomstructuur Adobe Campaign.

Met de wizard Maken kunt u de opties selecteren die u wilt inschakelen, zoals hieronder wordt weergegeven.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>De beschikbare toepassingen zijn afhankelijk van uw opties en modules. Controleer hiervoor uw licentieovereenkomst.
