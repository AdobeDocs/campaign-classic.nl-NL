---
solution: Campaign Classic
description: Interface van de content-editor
audience: web
content-type: reference
topic-tags: editing-html-content
dc-solution: Campaign Classic
product: campaign
title: </strong> en
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 3%

---


# Interface van de content-editor{#content-editor-interface}

## Venster bewerken {#editing-window}

Het DCE-bewerkingsvenster is onderverdeeld in drie verschillende secties. Hiermee kunt u de status van de inhoud weergeven, wijzigen en controleren.

![](assets/dce_decoupe_window_nb.png)

1. De **bovenste** sectie is een weergavegebied voor berichten aan de gebruiker. Deze berichten wijzen op het statuut van de de toepassingsstatus van het Web of de levering die evenals waarschuwingen en foutenmeldingen met betrekking tot de inhoud wordt gecreeerd. Raadpleeg de status van [HTML-inhoud voor meer informatie](../../web/using/content-editing-best-practices.md#html-content-statuses).
1. De sectie **links** van het venster is het gebied voor het bewerken van inhoud. Vanuit dit gebied kan de gebruiker rechtstreeks met de inhoud communiceren via de pop-upwerkbalk: voegt een koppeling in een afbeelding in, wijzigt het lettertype, verwijdert een veld, enzovoort. For more on this refer to [Editing forms](../../web/using/editing-content.md#editing-forms).
1. De sectie **rechts** van het venster is het gebied van het bedieningspaneel. In dit gebied worden de verschillende opties voor de editor gegroepeerd, met name de opties voor het configureren van de paginakop en de algemene opties voor een blok: Voeg een rand toe, verbind een gegevensbestandgebied met een inputstreek, toegang Web-pagina eigenschappen, enz. Raadpleeg de secties [Algemene opties](#global-options) en Inhoud [](../../web/using/editing-content.md) bewerken voor meer informatie.

## Algemene opties {#global-options}

In de rechterbovensectie van de editor hebt u toegang tot globale opties waarmee u de inhoud kunt beheren die momenteel wordt gemaakt.

![](assets/dce_global_options.png)

Het heeft vier pictogrammen:

![](assets/dce_icons_sidebar.png)

* Met het pictogram **Blokken** weergeven/verbergen kunt u blauwe kaders rond de inhoudsblokken (die overeenkomen met de `<div>` HTML-tag) weergeven.

* Met het pictogram **Een andere inhoud** kiezen kan de gebruiker nieuwe inhoud uit een sjabloon laden (bestaande sjabloon of een sjabloon buiten de doos).

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >De geselecteerde inhoud vervangt de huidige inhoud.

* Met het pictogram **Opslaan als sjabloon** kunt u de huidige inhoud opslaan als een sjabloon. U moet het label en de interne naam voor de sjabloon invoeren. Sjablonen worden opgeslagen in het **[!UICONTROL Resources > Templates > Content templates]** knooppunt.

   ![](assets/dce_popup_savetemplate.png)

   Nadat de sjabloon is opgeslagen, is deze beschikbaar en kan deze worden geselecteerd bij het maken van nieuwe inhoud.

   ![](assets/dce_create_fromtemplate.png)

* Met het pictogram **Pagina-eigenschappen** kunt u inhoudsgegevens boven aan de HTML-pagina selecteren.

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >Deze informatie komt overeen met de tags **`<title>`** en **`<meta>`** HTML op de pagina.
   >
   >De sleutelwoorden moeten door komma&#39;s worden gescheiden.

## Blokopties {#block-options}

In de sectie rechts van de editor worden de belangrijkste opties gegroepeerd waarmee u op de inhoud kunt reageren. Als u deze opties wilt weergeven, moet u een blok selecteren: de aard van deze opties is afhankelijk van het geselecteerde blok.

![](assets/dce_right_section.png)

U kunt:

* Bepaal de weergave voor een of meerdere blokken. Raadpleeg [Een zichtbaarheidsvoorwaarde](../../web/using/editing-content.md#defining-a-visibility-condition)definiëren.
* Definieer de randen en frames. Raadpleeg [Rand en achtergrond](../../web/using/editing-content.md#adding-a-border-and-background)toevoegen.
* Geef afbeeldingskenmerken (grootte, bijschrift) op, raadpleeg de eigenschappen [van de afbeelding](../../web/using/editing-content.md#editing-image-properties)bewerken.
* Koppel de database aan een formulierelement (invoerzone, selectievakje), raadpleeg [De gegevenseigenschappen voor een formulier](../../web/using/editing-content.md#changing-the-data-properties-for-a-form)wijzigen.
* Als u een deel van een formulier verplicht wilt maken, raadpleegt u [De gegevenseigenschappen van een formulier](../../web/using/editing-content.md#changing-the-data-properties-for-a-form)wijzigen.
* Definieer een handeling voor een knop. Zie [Een handeling aan een knop](../../web/using/editing-content.md#adding-an-action-to-a-button)toevoegen.

## Inhoud, werkbalk {#content-toolbar}

De werkbalk is een **pop-upelement** van de DCE-interface dat verschillende functies bevat volgens het geselecteerde blok.

>[!CAUTION]
>
>Met bepaalde werkbalkfuncties kunt u de HTML-content opmaken. However, if the page contains a CSS style sheet, the **instructions** from the style sheet may prove to take **priority** over the instructions specified with the toolbar.

