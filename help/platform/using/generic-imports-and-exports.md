---
solution: Campaign Classic
product: campaign
title: Algemene import- en exportbewerkingen
description: Algemene import- en exportbewerkingen
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 3%

---


# Algemene import- en exportbewerkingen{#generic-imports-and-exports}

Adobe Campaign biedt een gegevensexportmodule aan die het gemakkelijk maakt om een lijst van klanten of vooruitzichten (bijvoorbeeld, na een het richten verrichting) te halen die dan deel van een doelbevolking zullen worden.

Adobe Campaign beschikt ook over een importmodule waarmee u gegevens uit externe bestanden aan uw database kunt leveren.

>[!NOTE]
>
>De uitvoer en de invoer worden gevormd in specifieke malplaatjes die door werkschema&#39;s via **[!UICONTROL Import]** en **[!UICONTROL Export]** activiteiten worden uitgevoerd. Ze kunnen automatisch volgens een schema worden herhaald, bijvoorbeeld om de gegevensuitwisseling tussen verschillende informatiesystemen te automatiseren. Indien nodig, kunt u een occasionele invoer tot stand brengen of uitvoeren via de **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** knoop van de boom van Adobe Campaign.

U kunt:

* Maak een import- of exportsjabloon en configureer deze (zie hieronder).
* Een import- of exportbewerking maken: verwijst naar [Gegevens exporteren](../../platform/using/exporting-data.md) of [Gegevens importeren](../../platform/using/importing-data.md).
* Start het importeren of exporteren en controleer of het wordt uitgevoerd. Raadpleeg [Uitvoering bijhouden](#execution-tracking).

>[!CAUTION]
>
>Gegevensimport in campagne moet via workflows worden uitgevoerd om de consistentie van gegevens te waarborgen en de efficiëntie te verbeteren. Raadpleeg voor meer informatie de secties [Gegevens importeren](../../workflow/using/importing-data.md), [Beste werkwijzen importeren](../../workflow/using/importing-data.md#best-practices-when-importing-data) en [Sjabloon importeren](../../workflow/using/importing-data.md#setting-up-a-recurring-import).

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](../../platform/using/exporting-and-importing-profiles.md#import-profiles-video)

## Een taaksjabloon maken {#creating-a-job-template}

Importeren- en exportsjablonen worden opgeslagen in de map **[!UICONTROL Resources > Templates > Job templates]** van de Adobe Campaign-structuur.

Standaard staan er drie importsjablonen en één exportsjabloon in deze map. Ze mogen niet worden gewijzigd. U kunt ze dupliceren om uw eigen sjablonen te maken of een nieuwe sjabloon te maken via het menu **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]**.

![](assets/s_ncs_user_export_wizard_template_create.png)

De procedure voor het creëren van een procesmalplaatje wordt voorgesteld in [tovenaar van de Uitvoer](../../platform/using/exporting-data.md#export-wizard) en [tovenaar van de Invoer](../../platform/using/importing-data.md#import-wizard).

>[!NOTE]
>
>De native sjabloon **[!UICONTROL Import denylist]** is al geconfigureerd voor het importeren van een lijst met e-mailadressen die aan de lijst van afgewezen personen zijn toegevoegd.
> 
>Met de sjablonen **[!UICONTROL New text import]** en **[!UICONTROL New text export]** kunt u importeren of exporteren vanuit het niets.

## Nieuwe import/export {#creating-a-new-import-export} maken

Zodra het malplaatje is gevormd, kunnen de invoer en de uitvoerverrichtingen in verscheidene contexten in Adobe Campaign worden gelanceerd.

Met al deze opties opent u de wizard [import](../../platform/using/importing-data.md) of [export](../../platform/using/exporting-data.md#export-wizard).

* Klik in de sectie **[!UICONTROL Profiles and targets]** van de Adobe Campaign-werkruimte op de koppeling **[!UICONTROL Jobs]**: dit brengt u naar de lijst van bestaande in - en uitvoer .

   Klik op de knop **[!UICONTROL Create]** en selecteer het type taak dat u wilt uitvoeren.

   ![](assets/s_ncs_user_import_from_home.png)

* U kunt ook de import en export starten vanuit het gedeelte Toezicht van de werkruimte: met twee speciale koppelingen kunt u het importeren of exporteren rechtstreeks starten.

   ![](assets/s_ncs_user_import_from_production.png)

* Ook vanuit de Adobe Campaign-verkenner kunnen invoer en export plaatsvinden.

   Als u gegevens wilt exporteren/importeren, klikt u op het knooppunt **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]**, vervolgens op het pictogram **[!UICONTROL New]** en selecteert u **[!UICONTROL Export]** of **[!UICONTROL Import]**. Hiermee opent u de juiste wizard.

   ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)

## Reeksspatiëring {#execution-tracking}

U kunt het volgen van de uitvoering in de hogere sectie van deze redacteur bekijken. U kunt de wizard Exporteren sluiten en de uitvoering van de taak weergeven via de lijst met import-/exporttaken.

![](assets/s_ncs_user_export_list_and_details.png)

* Op het tabblad **[!UICONTROL Log]** kunt u logberichten over uitvoering bekijken.
* Het tabblad **[!UICONTROL Rejects]** bevat de geweigerde records. Zie [Gedrag in geval van een fout](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error).

>[!NOTE]
>
>De status van de import-/exporttaak wordt weergegeven in [Taakstatus](../../platform/using/importing-data.md#job-statuses).

