---
product: campaign
title: Aan de slag met webformulieren
description: Aan de slag met webformulieren in campagne
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 63602bed-ace6-4632-a735-5d268a7d72d0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 5%

---

# Aan de slag met webformulieren{#about-web-forms}

![](../../assets/common.svg)

Adobe Campaign integreert een grafische module voor het definiëren en publiceren van webformulieren om pagina&#39;s te maken die invoer- en selectievelden bevatten en die mogelijk gegevens in de database bevatten. Zo kunt u webpagina&#39;s ontwerpen en plaatsen die gebruikers kunnen openen om informatie weer te geven of in te voeren.

In dit hoofdstuk worden de creatie en het beheer van webformulieren beschreven, hoe u velden en pagina&#39;s beheert en hoe u de opslagmodi opslaat.

>[!CAUTION]
>
>Om privacyredenen raden we aan HTTPS te gebruiken voor alle externe bronnen.

## Stappen voor het maken van een webformulier {#steps-for-creating-a-web-form}

In dit hoofdstuk worden de stappen beschreven die zijn vereist voor het ontwerpen van een **webForm** typt u het formulier in Adobe Campaign en de beschikbare opties en configuraties. Met Adobe Campaign kunt u dit webformulier beschikbaar maken voor gebruikers en antwoorden in de database verzamelen en archiveren.

>[!CAUTION]
>
>Wanneer u webtoepassingen en webformulieren configureert, hebt u een minimale verticale resolutie van 900 pixels nodig (bijv. 1600x900).

Webformulieren zijn toegankelijk via het menu Webtoepassingen van het dialoogvenster **Campagnes** tab. In de Adobe Campaign-structuur worden ze gegroepeerd onder de **[!UICONTROL Resources > Online > Web Applications]** knooppunt.

Als u een webformulier wilt maken, klikt u op de knop **[!UICONTROL Create]** boven de lijst met webtoepassingen.

![](assets/webapp_create_new.png)

Selecteer de webformuliersjabloon ( **[!UICONTROL newWebForm]** standaard).

![](assets/s_ncs_admin_survey_select_template.png)

Hiermee gaat u naar het dashboard van het formulier.

![](assets/webapp_empty_dashboard.png)

De **[!UICONTROL Edit]** kunt u uw inhoud maken.

![](assets/webapp_edit_tab.png)

Om de configuratie en de inhoud van de vorm van het Web te bepalen, pas de volgende stappen toe:

* Begin door de vereiste pagina&#39;s en controles te creëren: invoervelden, vervolgkeuzelijsten, HTML-inhoud, enz.

   Deze stap wordt hieronder beschreven.

* Hiermee definieert u de volgorde van pagina&#39;s en bepaalt u de weergave.

   Deze stap wordt beschreven in [Opeenvolging van webformulierpagina&#39;s definiëren](defining-web-forms-page-sequencing.md).

* Vertaal indien nodig de inhoud.

   Deze stap wordt beschreven in [Een webformulier vertalen](translating-a-web-form.md).

## Webformulieren ontwerpen {#about-web-forms-designing}

De pagina&#39;s van het formulier worden gemaakt met een specifieke editor waarmee u invoerzones (tekst), selectievelden (lijsten, selectievakjes, enz.) kunt definiëren en configureren. en statische elementen (afbeeldingen, HTML-inhoud, enz.). U kunt ze groeperen in containers en de lay-out ervan wordt aangepast aan uw wensen (voor meer informatie hierover raadpleegt u [Containers maken](defining-web-forms-layout.md#creating-containers)).

In de volgende secties wordt beschreven hoe u inhoud en indeling voor formulierschermen definieert:

* [Velden toevoegen aan een webformulier](adding-fields-to-a-web-form.md),
* [HTML-inhoud invoegen](static-elements-in-a-web-form.md#inserting-html-content),
* [Statische elementen in een webformulier](static-elements-in-a-web-form.md),
* [De opmaak van webformulieren definiëren](defining-web-forms-layout.md).

>[!NOTE]
>
>* Tijdens het ontwerpen van een pagina kunt u de uiteindelijke rendering weergeven in het dialoogvenster **[!UICONTROL Preview]** tab. Sla het formulier eerst op om de wijzigingen weer te geven. Eventuele fouten worden weergegeven in het dialoogvenster **[!UICONTROL Log]** tab.
>* Om ervoor te zorgen dat de paginavertoning en de informatieopslag in de aangewezen opeenvolging voorkomen, laat zuiveringswijze in de vorm van het Web toe. Ga om dit te doen naar de **[!UICONTROL Preview]** subtab en controleer de **[!UICONTROL Enable debug mode]** vak: alle verzamelde informatie en mogelijke uitvoeringsfouten worden onder aan elke pagina weergegeven .

>


### De pictogrammen in de werkbalk gebruiken {#using-the-icons-in-the-toolbar}

U kunt ook de pictogrammen in de werkbalk gebruiken of met de rechtermuisknop klikken om een invoerzone in te voegen.

![](assets/s_ncs_admin_webform_add_selection.png)

In dit geval selecteert u eerst het type veld dat u wilt toevoegen en de opslagmodus voor antwoorden.

![](assets/s_ncs_admin_webform_select_storage.png)

Klikken **[!UICONTROL Ok]** om de selectie goed te keuren.

![](assets/s_ncs_admin_webform_confirm_storage.png)
