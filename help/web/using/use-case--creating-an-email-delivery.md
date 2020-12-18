---
solution: Campaign Classic
product: campaign
title: Hoofdletters gebruiken - een e-maillevering maken
description: Gebruiksscenario voor e-maillevering maken
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 46aa896929c960abeb501642a5ffbbb56de4802e
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---


# Gebruiksscenario: een e-maillevering maken{#use-case-creating-an-email-delivery}

In dit geval leert u hoe u een e-maillevering ontwerpt met de Adobe Campaign Digital Content Editor (DCE).

Ons uiteindelijke doel is om een levering te maken met een gepersonaliseerde sjabloon die het volgende bevat:

* Een rechtstreeks adres voor een ontvanger (met de voornaam en de tweede naam)
* Twee typen koppelingen naar een externe URL
* Een spiegelpagina
* Een koppeling naar een webtoepassing

>[!NOTE]
>
>Voordat u begint, moet u minstens één **HTML-sjabloon** hebben geconfigureerd om de inhoud van toekomstige leveringen te hosten.
>
>Zorg er bij levering **[!UICONTROL Properties]** voor dat **[!UICONTROL Content editing mode]** (op het tabblad **[!UICONTROL Advanced]**) is ingesteld op **[!UICONTROL DCE]**. Om de optimale verrichting van de redacteur te verzekeren, verwijs naar [Inhoud het uitgeven beste praktijken](../../web/using/content-editing-best-practices.md).

## Stap 1 - het Creëren van een levering {#step-1---creating-a-delivery}

Als u een nieuwe levering wilt maken, plaatst u de cursor in het tabblad **Campagnes** en klikt u op **Leveringen**. Klik vervolgens op de knop **Maken** boven de lijst met bestaande leveringen. Raadpleeg [deze pagina](../../delivery/using/about-email-channel.md) voor meer informatie over het maken van leveringen.

![](assets/delivery_step_1.png)

## Stap 2 - Een sjabloon selecteren {#step-2---selecting-a-template}

Selecteer een leveringssjabloon en geef uw levering een naam. Deze naam is alleen zichtbaar voor gebruikers van de Adobe Campaign-console en niet voor uw ontvangers. Deze kop wordt echter wel weergegeven in uw lijst met leveringen. Klik op **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## Stap 3 - Inhoud selecteren {#step-3---selecting-a-content}

De Editor voor digitale inhoud wordt geleverd met verschillende out-of-the-box sjablonen met verschillende structuren (kolommen, tekstgebieden, enz.).

Selecteer het inhoudsmalplaatje dat u wilt gebruiken, dan klik **[!UICONTROL Start with the selected content]** knoop om het malplaatje in de gecreeerde levering te tonen.

![](assets/dce_select_model.png)

U kunt ook HTML-inhoud die buiten Adobe Campaign is gemaakt, importeren door **[!UICONTROL From a file]** te selecteren.

![](assets/dce_select_from_file_template.png)

U kunt deze inhoud opslaan als een sjabloon voor toekomstig gebruik. Nadat u een gepersonaliseerde inhoudssjabloon hebt gemaakt, kunt u deze voorvertonen in de lijst met sjablonen. Raadpleeg [Sjabloonbeheer](../../web/using/template-management.md) voor meer informatie hierover.

>[!CAUTION]
>
>Als u de **Adobe Campaign-webinterface** gebruikt, moet u een .zip-bestand importeren dat de HTML-inhoud en verwante afbeeldingen bevat.

## Stap 4 - Het ontwerpen van het bericht {#step-4---designing-the-message}

* De eerste en tweede naam van de ontvangers weergeven

   Als u de eerste en tweede naam van de ontvangers wilt invoegen in een tekstveld in de aflevering, klikt u op het gekozen tekstveld en plaatst u de cursor op de gewenste positie. Klik op het eerste pictogram op de pop-upwerkbalk en klik vervolgens op **[!UICONTROL Personalization block]**. Selecteer **[!UICONTROL Greetings]** en klik vervolgens op **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* Een koppeling invoegen in een afbeelding

   Als u ontvangers voor levering via een afbeelding naar een extern adres wilt sturen, klikt u op de desbetreffende afbeelding om de pop-upwerkbalk weer te geven. Plaats de cursor op het eerste pictogram en klik vervolgens op **[!UICONTROL Link to an external URL]**. Voor meer op dit, verwijs naar [Toevoegend een verbinding](../../web/using/editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   Voer de URL voor de koppeling in het veld **URL** in met de volgende notatie **https://www.myURL.com** en bevestig vervolgens de URL.

   U kunt de koppeling op elk gewenst moment wijzigen met de sectie rechts van het venster.

* Koppelingen in tekst invoegen

   Als u een externe koppeling wilt integreren in de tekst in uw bestelling, selecteert u een stuk tekst of een blok tekst en klikt u op het eerste pictogram in de pop-upwerkbalk. Klik **[!UICONTROL Link to an external URL]**, ga het verbindingsadres in **[!UICONTROL URL]** gebied in. Voor meer op dit, verwijs naar [Toevoegend een verbinding](../../web/using/editing-content.md#adding-a-link).

   U kunt de koppeling op elk gewenst moment wijzigen met de sectie rechts van het venster.

   >[!CAUTION]
   >
   >De oorspronkelijke tekst wordt vervangen door de tekst die u in het veld **[!UICONTROL Label]** hebt ingevoerd.

* Een spiegelpagina toevoegen

   Om uw ontvangers toe te staan om uw leveringsinhoud in browser van het Web te bekijken, kunt u een verbinding aan een spiegelpagina in uw levering integreren.

   Klik op het tekstveld waarin u de koppeling wilt plaatsen. Klik op het eerste pictogram op de pop-upwerkbalk, selecteer **[!UICONTROL Personalization block]** en **[!UICONTROL Link to Mirror Page (MirrorPage)]**. Klik **[!UICONTROL Save]** om te bevestigen.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >Het label van het verpersoonlijkingsblok vervangt automatisch de originele tekst in uw levering.

* Een koppeling naar een webtoepassing integreren

   Met de Digital Content Editor kunt u koppelingen naar webtoepassingen integreren vanuit uw Adobe Campaign-console, zoals een openingspagina of een formulierpagina. Voor meer op dit, verwijs naar [Verbinding aan een toepassing van het Web](../../web/using/editing-content.md#link-to-a-web-application).

   Selecteer een tekstveld voor de koppeling naar een webtoepassing en klik op het eerste pictogram. Kies **[!UICONTROL Link to a Web application]**, dan selecteer de gewenste toepassing door het pictogram aan het eind van **Web Application** te klikken gebied.

   ![](assets/dce_webapp.png)

   Klik **Opslaan** om te bevestigen.

   >[!NOTE]
   >
   >Voor deze stap moet u ten minste één webtoepassing opslaan. Deze vindt u op het tabblad **[!UICONTROL Campaigns > Web applications]** van uw console.

## Stap 5 - Besparing de levering {#step-5---saving-the-delivery}

Wanneer de inhoud is geïntegreerd, slaat u de levering op door op **Opslaan** te klikken. Het wordt nu weergegeven in de lijst met leveringen op het tabblad **[!UICONTROL Campaigns > Deliveries]**.
