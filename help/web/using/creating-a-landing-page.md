---
product: campaign
title: Een landingspagina maken
description: Een landingspagina maken
feature: Landing Pages
exl-id: 71c737c2-b0d6-4ae8-a5df-28a08dff82d7
source-git-commit: 4ff86349d6b8966273585bf2a1ea0d785a7e87cb
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 3%

---

# Een landingspagina maken{#creating-a-landing-page}

![](../../assets/common.svg)

## Over het maken van bestemmingspagina&#39;s {#about-landing-pages-creation}

In dit geval kunt u het gebruik van de Digital Editor voor het maken van een bestemmingspagina op de Adobe Campaign-console bekijken.

Voordat u begint met het configureren van de bestemmingspagina in Adobe Campaign, moet u ervoor zorgen dat u **een of meer sjablonen** om de HTML pagina(&#39;s) te vertegenwoordigen.

Het hoofddoel van dit gebruiksgeval is om de formuliervelden van de landingspagina te laten overeenstemmen met de interne velden in Adobe Campaign met behulp van de functies in de DCE.

## De openingspagina maken {#creating-the-landing-page}

Als u een nieuwe webtoepassing van het type Landing Page wilt maken, gaat u als volgt te werk:

1. Ga naar de **[!UICONTROL Campaigns]** en klik op de knop **[!UICONTROL Web application]** klikt u op de koppeling **[!UICONTROL Create]** knop.
1. Selecteer **[!UICONTROL New landing page]** en voer een label in. Klik vervolgens op **[!UICONTROL Save]**.

   ![](assets/dce_uc1_newlandingpage.png)

1. Klik op de knop **[!UICONTROL Edit]** tab.
1. Verwijder de **Einde** activiteit.
1. Voeg een **[!UICONTROL Page]** activiteit na de **[!UICONTROL Storage]** activiteit.
1. Bewerk de **Pagina 2** activiteit dan uncheck **[!UICONTROL Activate outbound transitions]** in de **[!UICONTROL Properties]** tab.

   ![](assets/dce_uc1_transition.png)

1. Wijzigingen opslaan.

U krijgt dan de volgende opeenvolging:

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>Voor meer bij het creëren van een toepassing van het Web, verwijs naar [deze sectie](creating-a-new-web-application.md).

## Stap 1 - Sjablonen selecteren en laden {#step-1---selecting-and-loading-templates}

In deze sectie gaan we bekijken hoe **HTML-inhoud importeren** voor elke pagina van de toepassing van het Web.

Een sjabloon moet bevatten:

* een **HTML** bestand (verplicht)
* een of meer **CSS** bestanden (optioneel)
* een of meer **afbeeldingen** (optioneel)

Voer de volgende stappen uit om de sjabloon op de eerste pagina te laden:

1. Eerste openen **[!UICONTROL Page]** activiteit van de toepassing van het Web.
1. Selecteren **[!UICONTROL From a file]** om uw inhoudssjabloon op te halen.

   ![](assets/dce_uc1_selectmodel.png)

1. Selecteer het HTML-bestand dat u wilt gebruiken.
1. Klikken **Openen** om het importeren te starten.

   Tijdens het laden wordt de lijst met gedeelde bestanden weergegeven. Het importsysteem controleert of alle bestanden die aan de geselecteerde HTML zijn gekoppeld (CSS, afbeeldingen, enz.) aanwezig zijn.

   Klik op de knop **[!UICONTROL Close]** zodra het importeren is voltooid.

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >U moet wachten tot u het volgende bericht krijgt alvorens te sluiten: **[!UICONTROL The external resources have been successfully published]** .

1. Klik op de knop **[!UICONTROL Properties]** tab.
1. Voer een **label** voor elke pagina (bijvoorbeeld: Pagina 1= Verzamelen, pagina 2=Bedankt).

   ![](assets/dce_uc1_pagelabel.png)

Pas deze stappen voor elke pagina toe die in de toepassing van het Web wordt opgenomen.

>[!CAUTION]
>
>**De DCE voert de code JavaScript voor de geladen pagina van de HTML uit.** JavaScript-fouten in de HTML-sjabloon die kunnen voorkomen in de Adobe Campaign-interface. Deze fouten hebben geen betrekking op de editor. Als u wilt controleren of de geïmporteerde bestanden geen fouten bevatten, kunt u het beste deze testen in een webbrowser voordat u de bestanden importeert in de DCE.

## Stap 2 - De inhoud configureren {#step-2---configuring-the-content}

In deze sectie gaan we geïmporteerde inhoud aanpassen en de velden van de database koppelen aan de vorm van de webpagina. De eerder gemaakte webtoepassing is:

![](assets/dce_uc1_lp_enchainement.png)

### Inhoud wijzigen {#modifying-content}

Laten we beginnen met het wijzigen van de kleuren van de pagina. Dit doet u als volgt:

1. Open de **[!UICONTROL Collection]** pagina.
1. Klik op de achtergrond.
1. Klikken **Achtergrondkleur** aan de rechterkant.
1. Selecteer een nieuwe achtergrondkleur.
1. Klikken **OK** om de wijziging te bevestigen.

   ![](assets/dce_uc1_changecolor.png)

1. Dezelfde processen toepassen om de kleur van de knop te wijzigen

   ![](assets/dce_uc1_finalcolor.png)

### Formuliervelden koppelen {#linking-form-fields}

We gaan de velden op de pagina koppelen aan de velden in de database om de verstrekte informatie op te slaan.

1. Selecteer een formulierveld.
1. Bewerk de **[!UICONTROL Field]** aan de rechterkant van de editor.
1. Selecteer het databaseveld dat u wilt koppelen aan het geselecteerde veld.

   ![](assets/dce_uc1_mapping.png)

1. Herhaal dit proces voor elk veld op de pagina.

U kunt een veld verplicht maken: Klik bijvoorbeeld op de knop **[!UICONTROL Email]** veld en schakel vervolgens de **Verplicht** optie.

![](assets/dce_uc1_fieldmandatory.png)

### Koppelingen naar de volgende pagina maken {#creating-a-link-to-the-next-page}

Deze stap is verplicht omdat het de toepassing van het Web zal toestaan om de opeenvolging van de volgende stappen te bepalen: De verzamelde gegevens opslaan in de database en vervolgens de volgende pagina weergeven (**Bedankt** pagina).

1. Selecteer **[!UICONTROL Send it!]** van de **[!UICONTROL Collection]** pagina.
1. Klik op de knop **[!UICONTROL Action]** vervolgkeuzemenu.
1. Selecteer **[!UICONTROL Next page]** handeling.

   ![](assets/dce_uc1_actionbouton.png)

### Een personalisatieveld invoegen {#inserting-a-personalization-field}

Met deze stap kunt u de pagina Bedankt personaliseren. Dit doet u als volgt:

1. Open de **[!UICONTROL Thank you]** pagina.
1. Plaats de cursor in een tekstgebied waar u de voornaam van de ontvanger wilt invoegen.
1. Selecteren **[!UICONTROL Personalization field]** in de **[!UICONTROL Insert]** van de werkbalk.
1. Selecteer de voornaam.

   ![](assets/dce_uc1_persochamp.png)

Het verpersoonlijkingsgebied heeft een gele achtergrond in de redacteur.

![](assets/dce_uc1_edit_champperso.png)

## Stap 3 - Inhoud publiceren {#step-3---publishing-content}

De inhoud wordt gepubliceerd van het de toepassingsdashboard van het Web. Klik op de knop **[!UICONTROL Publish]** om het uit te voeren.

![](assets/dce_uc1_pub_dashboard.png)

Tijdens publicatie wordt een logboek weergegeven. Het publicatiesysteem analyseert alle inhoud die in de toepassing Web wordt gevonden

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>In het publicatielogboek worden waarschuwingen en fouten gesorteerd op activiteit.

Het formulier is nu beschikbaar: de URL ervan is toegankelijk in het toepassingsdashboard en kan naar ontvangers worden verzonden.
