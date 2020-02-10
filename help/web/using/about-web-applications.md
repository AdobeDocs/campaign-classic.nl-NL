---
title: Webtoepassingen
seo-title: Webtoepassingen
description: Webtoepassingen
seo-description: null
page-status-flag: never-activated
uuid: acfa6e5e-b503-4a1a-871e-e70007874f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 3af763ad-6b0d-4f4c-aed1-c5e12efd4760
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Webtoepassingen{#about-web-applications}

Met Adobe Campaign kunt u dynamische en interactieve webtoepassingen maken en publiceren met gegevens uit de database en inhoud die zijn aangepast aan de rechten van de verbonden gebruiker. U kunt pagina&#39;s maken, zoals een bewerkingsformulier op een extranet, of meldingsformulieren, inclusief gegevens uit de database met tabellen, grafieken, invoerformulieren enzovoort. Met deze functionaliteit kunt u webpagina&#39;s ontwerpen en plaatsen waar gebruikers informatie kunnen opzoeken of invoeren.

Dit kan een abonnementsformulier zijn met gegevens die vooraf zijn geladen met informatie in de Adobe Campagne-database, zoals hieronder wordt weergegeven:

![](assets/webapp_form_sample.png)

Dit hoofdstuk verstrekt een overzicht van hoe te om de toepassingen van het Web te beheren.

>[!CAUTION]
>
>Om privacyredenen raden we aan HTTPS te gebruiken voor alle externe bronnen.

## Toepassingsbereik van webtoepassing {#web-application-scope}

Webtoepassingen in Adobe Campaign bieden toegang tot de volgende mogelijkheden:

* Formulier maken met meerdere pagina&#39;s,
* Meertalig beheer van enquêtes met een geïntegreerd vertaalhulpmiddel;
* Grafische paginabeheerinterface, paginalay-out met meerdere kolommen,
* Rendering van personalisatie en veldpositie,
* Voorwaardelijke weergave van enquêtevelden volgens antwoorden,
* Willekeurige weergave van vragen
* Voorwaardelijke paginaweergave,
* Informatiecontrole vóór validatie afhankelijk van het verwachte gegevenstype (nummer, e-mailadres, datum, enz.) en de verplichte velden,
* uitnodigingen of meldingen via e-mail;
* Personalisatie van fouten en eindberichten
* Gebruik van afbeeldingen, video&#39;s, hypertextkoppelingen, captcha, enzovoort.
* Monitoring van reacties in real time.

De optionele module voor het maken van **enquêtes** biedt de volgende aanvullende functies:

* Dynamische extensie van de database: het maken van reacties die niet in de oorspronkelijke gegevenssjabloon zijn opgenomen;
* Speciale rapporten genereren.

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
1. De webtoepassing publiceren om deze beschikbaar te maken op een extranet of in Adobe Campaign.

## Aanvankelijke configuratie webtoepassing {#web-application-initial-configuration}

De toepassing van het Web wordt gecreeerd via de **[!UICONTROL Web Applications]** verbinding in **[!UICONTROL Campaigns]** en **[!UICONTROL Profiles and targets]** lusjes.

Webtoepassingen worden opgeslagen in het **[!UICONTROL Resources > Online > Web Applications]** knooppunt van de Adobe Campaign-structuur. Configuraties worden uitgesplitst in de volgende mappen:

* **[!UICONTROL Administration > Configuration > Form renderings]**: bevat de renderingsjablonen voor de webformulierpresentatie (toepassingen en enquêtes). Met de sjabloon kunt u het formulier genereren. Er wordt ook een CSS-stijlpagina gebruikt. Deze stijlpagina kan op sjabloonniveau worden overgeladen. Raadpleeg [deze pagina](../../web/using/form-rendering.md#selecting-the-form-rendering-template)voor meer informatie.
* **[!UICONTROL Resources > Templates > Web application templates]**: bevat formuliersjablonen. Als u een formulier of een webtoepassing wilt maken, moet u beginnen met een sjabloon.

## Webtoepassingssjablonen {#web-application-templates}

Standaard biedt Adobe Campaign één sjabloon per beschikbare webtoepassing.

>[!NOTE]
>
>U kunt een bestaande toepassing van het Web in een malplaatje omzetten. Selecteer hiertoe het formulier en klik met de rechtermuisknop. Selecteer **[!UICONTROL Actions > Save as template...]**.

U kunt nieuwe sjablonen maken via het **[!UICONTROL Resources > Templates > Web Application templates]** knooppunt van de Adobe Campagne-structuur.

Met de wizard Maken kunt u de opties selecteren die u wilt inschakelen, zoals hieronder wordt weergegeven.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>De beschikbare toepassingen zijn afhankelijk van uw opties en modules. Controleer uw licentieovereenkomst.

