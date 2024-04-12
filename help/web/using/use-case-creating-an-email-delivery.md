---
product: campaign
title: Kwestie gebruiken - een e-maillevering maken
description: Kwestie gebruiken - een e-maillevering maken
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

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
>Voordat u begint, moet u ten minste één **HTML-sjabloon** geconfigureerd om de inhoud van uw toekomstige leveringen te hosten.
>
>In de levering **[!UICONTROL Properties]**, zorgt u ervoor dat de **[!UICONTROL Content editing mode]** (in de **[!UICONTROL Advanced]** tab) is ingesteld op **[!UICONTROL DCE]**. Om de optimale werking van de redacteur te verzekeren, verwijs naar [Aanbevolen werkwijzen voor het bewerken van inhoud](content-editing-best-practices.md).

## Stap 1 - Een levering maken {#step-1---creating-a-delivery}

Als u een nieuwe levering wilt maken, plaatst u de cursor in de **Campagnes** en klik op **Leveringen**. Klik op de knop **Maken** boven de lijst met bestaande leveringen. Raadpleeg voor meer informatie over het maken van leveringen [deze pagina](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Stap 2 - Een sjabloon selecteren {#step-2---selecting-a-template}

Selecteer een leveringssjabloon en geef uw levering een naam. Deze naam is alleen zichtbaar voor gebruikers van de Adobe Campaign-console en niet voor uw ontvangers. Deze kop wordt echter wel weergegeven in uw lijst met leveringen. Klik op **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## Stap 3 - Inhoud selecteren {#step-3---selecting-a-content}

De Editor voor digitale inhoud wordt geleverd met verschillende out-of-box sjablonen met verschillende structuren (kolommen, tekstgebieden, enz.).

Selecteer de inhoudssjabloon die u wilt gebruiken en klik op de knop **[!UICONTROL Start with the selected content]** om de sjabloon weer te geven in de gemaakte levering.

![](assets/dce_select_model.png)

U kunt ook HTML-inhoud die buiten Adobe Campaign is gemaakt, importeren door **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

U kunt deze inhoud opslaan als een sjabloon voor toekomstig gebruik. Nadat u een gepersonaliseerde inhoudssjabloon hebt gemaakt, kunt u deze voorvertonen in de lijst met sjablonen. Raadpleeg voor meer informatie hierover [Sjabloonbeheer](template-management.md).

>[!CAUTION]
>
>Als u het **Adobe Campaign-webinterface**, moet u een .zip-bestand importeren dat de HTML-inhoud en verwante afbeeldingen bevat.

## Stap 4 - Het ontwerpen van het bericht {#step-4---designing-the-message}

* De eerste en tweede naam van de ontvangers weergeven

  Als u de eerste en tweede naam van de ontvangers wilt invoegen in een tekstveld in de aflevering, klikt u op het gekozen tekstveld en plaatst u de cursor op de gewenste positie. Klik op het eerste pictogram op de pop-upwerkbalk en klik vervolgens op **[!UICONTROL Personalization block]**. Selecteren **[!UICONTROL Greetings]** en klik vervolgens op **[!UICONTROL OK]**.

  ![](assets/dce_personalizationblock_greetings.png)

* Een koppeling invoegen in een afbeelding

  Als u ontvangers voor levering via een afbeelding naar een extern adres wilt sturen, klikt u op de desbetreffende afbeelding om de pop-upwerkbalk weer te geven. Plaats de cursor vervolgens op het eerste pictogram **[!UICONTROL Link to an external URL]**. Raadpleeg voor meer informatie hierover [Een koppeling toevoegen](editing-content.md#adding-a-link).

  ![](assets/dce_externalpage.png)

  Voer de URL voor de koppeling in het dialoogvenster **URL** veld met de volgende notatie **https://www.myURL.com**, bevestig vervolgens.

  U kunt de koppeling op elk gewenst moment wijzigen met de sectie rechts van het venster.

* Koppelingen in tekst invoegen

  Als u een externe koppeling wilt integreren in de tekst in uw bestelling, selecteert u een stuk tekst of een blok tekst en klikt u op het eerste pictogram in de pop-upwerkbalk. Klikken **[!UICONTROL Link to an external URL]**, voert u het koppelingsadres in de **[!UICONTROL URL]** veld. Raadpleeg voor meer informatie hierover [Een koppeling toevoegen](editing-content.md#adding-a-link).

  U kunt de koppeling op elk gewenst moment wijzigen met de sectie rechts van het venster.

  >[!CAUTION]
  >
  >De tekst die is ingevoerd in het **[!UICONTROL Label]** wordt de oorspronkelijke tekst vervangen.

* Een spiegelpagina toevoegen

  Om uw ontvangers toe te staan om uw leveringsinhoud in browser van het Web te bekijken, kunt u een verbinding aan een spiegelpagina in uw levering integreren.

  Klik op het tekstveld waarin u de koppeling wilt plaatsen. Klik op het eerste pictogram op de pop-upwerkbalk en selecteer **[!UICONTROL Personalization block]** vervolgens **[!UICONTROL Link to Mirror Page (MirrorPage)]**. Klik op **[!UICONTROL Save]** om te bevestigen.

  ![](assets/dce_mirrorpage.png)

  >[!CAUTION]
  >
  >Het label van het verpersoonlijkingsblok vervangt automatisch de originele tekst in uw levering.

* Een koppeling naar een webtoepassing integreren

  Met de Digital Content Editor kunt u koppelingen naar webtoepassingen integreren vanuit uw Adobe Campaign-console, zoals een openingspagina of een formulierpagina. Raadpleeg voor meer informatie hierover [Koppelen naar een webtoepassing](editing-content.md#link-to-a-web-application).

  Selecteer een tekstveld voor de koppeling naar een webtoepassing en klik op het eerste pictogram. Kies **[!UICONTROL Link to a Web application]** selecteert u vervolgens de gewenste toepassing door op het pictogram aan het einde van het dialoogvenster **Webtoepassing** veld.

  ![](assets/dce_webapp.png)

  Klikken **Opslaan** ter bevestiging.

  >[!NOTE]
  >
  >Voor deze stap moet u ten minste één webtoepassing opslaan. Deze vindt u in het dialoogvenster **[!UICONTROL Campaigns > Web applications]** tabblad van uw console.

## Stap 5 - de levering bewaren {#step-5---saving-the-delivery}

Nadat de inhoud is geïntegreerd, kunt u de levering opslaan door op **Opslaan**. Het wordt nu weergegeven in de lijst met leveringen die u kunt vinden in het dialoogvenster **[!UICONTROL Campaigns > Deliveries]** tab.
