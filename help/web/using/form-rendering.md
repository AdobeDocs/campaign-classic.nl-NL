---
product: campaign
title: Formulierweergave
description: Formulierweergave
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Forms
exl-id: 723a6c47-5323-4914-a014-58be493852cc
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 2%

---

# Formulierweergave{#form-rendering}



## De renderingsjabloon van het formulier selecteren {#selecting-the-form-rendering-template}

Met de formulierinstellingen kunt u de sjabloon selecteren waarmee de pagina&#39;s worden gegenereerd. Klik op de knop **[!UICONTROL Properties]** op de werkbalk met formulierdetails en selecteer de knop **[!UICONTROL Rendering]** tab. Er is standaard een aantal sjablonen (stijlpagina&#39;s) beschikbaar.

![](assets/s_ncs_admin_survey_rendering_select.png)

In het onderste gedeelte van de editor kunt u een rendering van de geselecteerde sjabloon weergeven.

Met de functie Zoomen kunt u de geselecteerde sjabloon bewerken.

![](assets/s_ncs_admin_survey_render_edit.png)

U kunt deze sjablonen wijzigen of overschrijven. Om dit te doen, klik **[!UICONTROL Page layout...]** de informatie koppelen en aanpassen.

![](assets/s_ncs_admin_survey_render_edit_param.png)

U kunt:

* Wijzig de afbeelding die als logo wordt gebruikt en pas de grootte ervan aan.
* Geef ook het pad op voor toegang tot de voorvertoning wanneer gebruikers deze renderingsjabloon selecteren.

De **[!UICONTROL Headers/Footers]** kunt u met deze sjabloon de informatie wijzigen die wordt weergegeven in de kop- en voetteksten van elke formulierpagina.

![](assets/s_ncs_admin_survey_render_edit_header.png)

Elke regel van de **[!UICONTROL Page headers]** en **[!UICONTROL Page footers]** komt overeen met een regel op de pagina HTML. Klikken **[!UICONTROL Add]** om een nieuwe regel te maken.

Selecteer een bestaande regel en klik op de knop **[!UICONTROL Detail]** om het aan te passen.

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

U kunt de inhoud van de regel wijzigen, randen toevoegen en de lettertypekenmerken wijzigen via de desbetreffende tabbladen. Klikken **[!UICONTROL OK]** deze wijzigingen te bevestigen.

De **[!UICONTROL Position]** in velden kunt u de positie van elementen in de kop- en voettekst van de pagina definiëren.

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>Rendersjablonen worden opgeslagen in het dialoogvenster **[!UICONTROL Administration > Configuration > Form rendering]** knooppunt.\
>Raadpleeg voor meer informatie hierover [Rendering van formulieren aanpassen](#customizing-form-rendering)

## Rendering van formulieren aanpassen {#customizing-form-rendering}

### De lay-out van elementen wijzigen {#changing-the-layout-of-elements}

U kunt de stijlpagina voor elk element van het formulier (invoervelden, afbeeldingen, keuzerondjes, enz.) overladen.

Om dit te doen, gebruik **[!UICONTROL Advanced]** tab.

![](assets/s_ncs_admin_survey_advanced_tab.png)

Hiermee kunt u de volgende eigenschappen definiëren:

* **[!UICONTROL Label position]**: zie [De positie van labels definiëren](defining-web-forms-layout.md#defining-the-position-of-labels),
* **[!UICONTROL Label format]**: Tekstomloop of Geen tekstomloop
* **[!UICONTROL Number of cells]** : zie [De velden op de pagina plaatsen](defining-web-forms-layout.md#positioning-the-fields-on-the-page),
* **[!UICONTROL Horizontal alignment]** (Links, Rechts, Gecentreerd) en **[!UICONTROL Vertical alignment]** (Hoog, Laag, Midden),
* **[!UICONTROL Width]** van het gebied: dit kan worden uitgedrukt als een percentage of in ems, punten of pixels (standaardwaarde);
* Maximum **[!UICONTROL Length]**: Maximum aantal tekens toegestaan (voor besturingselementen voor tekst, aantal en wachtwoordtype),
* **[!UICONTROL Lines]**: aantal regels voor een **[!UICONTROL Multi-line text]** typezone,
* **[!UICONTROL Style inline]**: kunt u de CSS-stijlpagina overladen met extra instellingen. Deze worden gescheiden met **;** tekens zoals in het onderstaande voorbeeld wordt getoond:

   ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### Kop- en voetteksten definiëren {#defining-headers-and-footers}

Velden worden gerangschikt in een boomstructuur waarvan het basisniveau dezelfde naam heeft als de pagina. Selecteer het om de naam te wijzigen.

De titel van het venster moet worden ingevoerd in het **[!UICONTROL Page]** tabblad van het venster met formuliereigenschappen. U kunt ook een setinhoud toevoegen aan de kop- en voettekst van de pagina (deze informatie wordt op elke pagina weergegeven). Deze inhoud wordt ingevoerd in de overeenkomende gedeelten van het dialoogvenster **[!UICONTROL Texts]** tab, zoals hieronder wordt getoond:

![](assets/s_ncs_admin_survey_titles_config.png)

### Elementen toevoegen aan HTML header {#adding-elements-to-html-header}

U kunt aanvullende elementen invoeren die moeten worden ingevoegd in de koptekst HTML van een formulierpagina. Om dit te doen, ga de elementen in in **[!UICONTROL Header]** tabblad van de desbetreffende pagina.

Zo kunt u verwijzen naar een pictogram dat bijvoorbeeld op de titelbalk van de pagina wordt weergegeven.

![](assets/webform_header_page_tab.png)

## Besturingsinstellingen definiëren {#defining-control-settings}

Wanneer de gebruiker het formulier invult, wordt automatisch een controle uitgevoerd op bepaalde velden, afhankelijk van de indeling of configuratie. Hiermee kunt u bepaalde velden verplicht maken (zie [Verplichte velden definiëren](#defining-mandatory-fields)) of de indeling van de ingevoerde gegevens controleren (zie [Gegevensindeling controleren](#checking-data-format)). Controles worden uitgevoerd tijdens paginaconclusie (door een verbinding of een knoop te klikken die een outputovergang toelaat).

### Verplichte velden definiëren {#defining-mandatory-fields}

Als u bepaalde velden verplicht wilt maken, selecteert u deze optie bij het maken van het veld.

![](assets/s_ncs_admin_survey_required_field.png)

Als de gebruiker deze pagina goedkeurt zonder het veld in te voeren, wordt het volgende bericht weergegeven:

![](assets/s_ncs_admin_survey_required_default_msg.png)

U kunt dit bericht aanpassen door op het pictogram **[!UICONTROL Personalize this message]** koppeling.

![](assets/s_ncs_admin_survey_required_custom_msg.png)

Als de gebruiker deze pagina goedkeurt zonder het veld in te voeren, wordt het volgende bericht weergegeven:

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### Gegevensindeling controleren {#checking-data-format}

Voor formuliercontroles waarvan de waarden zijn opgeslagen in een bestaand veld van de database, worden de regels voor het opslagveld toegepast.

Voor formuliercontroles waarvan de waarden in een variabele worden opgeslagen, zijn de goedkeuringsregels afhankelijk van de indeling van de variabele.

Als u bijvoorbeeld een **[!UICONTROL Number]** controle om het cliëntaantal op te slaan, zoals hieronder getoond:

![](assets/s_ncs_admin_survey_choose_format.png)

De gebruiker moet een geheel getal in het formulierveld invoeren.

## Voorwaardelijke weergave van velden definiëren {#defining-fields-conditional-display}

U kunt de weergave van velden op de pagina configureren die moeten worden weergegeven op basis van de waarden die de gebruiker heeft gekozen. Dit kan op één gebied of een groep gebieden van toepassing zijn (wanneer zij in een container worden gegroepeerd).

Voor elk element van de pagina geldt het **[!UICONTROL Visibility]** kunt u de weergavevoorwaarden definiëren.

![](assets/s_ncs_admin_survey_condition_edit.png)

Voorwaarden kunnen betrekking hebben op de waarde van databasevelden of -variabelen.

In het venster van de gebiedsselectie, kunt u van de volgende gegevens kiezen:

![](assets/s_ncs_admin_survey_condition_select.png)

* De hoofdstructuur bevat de parameters van de formuliercontext. De standaardparameters zijn de id (die overeenkomt met de gecodeerde id van de ontvanger), de taal en de oorsprong.

   Raadpleeg [deze pagina](defining-web-forms-properties.md#form-url-parameters) voor meer informatie.

* De **[!UICONTROL Recipients]** De substructuur bevat de invoervelden die in het formulier zijn ingevoegd en in de database zijn opgeslagen.

   Raadpleeg voor meer informatie hierover [Gegevens opslaan in de database](web-forms-answers.md#storing-data-in-the-database).

* De **[!UICONTROL Variables]** De substructuur bevat de beschikbare variabelen voor dit formulier. Raadpleeg voor meer informatie hierover [Gegevens opslaan in een lokale variabele](web-forms-answers.md#storing-data-in-a-local-variable).

Raadpleeg de volgende gebruiksscenario&#39;s voor meer informatie: [Verschillende opties weergeven, afhankelijk van de geselecteerde waarden](use-cases--web-forms.md#displaying-different-options-depending-on-the-selected-values).

U kunt ook de weergave van formulierpagina&#39;s bepalen met de opdracht **[!UICONTROL Test]** object. Raadpleeg [deze pagina](defining-web-forms-page-sequencing.md#conditional-page-display) voor meer informatie.

## Elementen uit een bestaand formulier importeren {#importing-elements-from-an-existing-form}

Het is mogelijk om gebieden of containers van andere vormen van het Web in te voeren. Hiermee kunt u een bibliotheek maken met herbruikbare blokken die in formulieren worden ingevoegd, zoals het adresblok, het abonnementsgebied voor nieuwsbrieven, enzovoort.

Als u een element in een formulier wilt importeren, voert u de volgende stappen uit:

1. Bewerk de pagina waarin u een of meer elementen wilt invoegen en klik vervolgens op **[!UICONTROL Import an existing block]** in de werkbalk.

   ![](assets/s_ncs_admin_survey_import_block.png)

1. Selecteer het webformulier met de velden die u wilt importeren en kies de containers en velden die u wilt importeren.

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >De **[!UICONTROL Edit link]** rechts van de naam van het bronformulier kunt u het geselecteerde webformulier weergeven.

1. Klikken **[!UICONTROL Ok]** om de invoeging te bevestigen.

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)
