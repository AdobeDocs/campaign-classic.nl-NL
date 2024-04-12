---
product: campaign
title: Over responsbeheer
description: Over responsbeheer
feature: Campaigns
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 4%

---

# Aan de slag met Campagne Response Manager{#about-response-manager}



Adobe Campaign biedt een add-on voor responsbeheer waarmee u het succes en de winstgevendheid van marketingcampagnes kunt meten of voorstellen kunt bieden via communicatiekanalen: e-mail, mobiel, direct mail, enz.

## Hypothese {#hypothesis-concept}

De hypothesen kunnen over een bepaalde periode van de contactdatum worden gevormd om het gedrag van degenen te verminderen die na het ontvangen van een levering worden gericht. Deze hypothesen zijn gebaseerd op een **transactie** een tabel waarin de aankopen en de details van deze aankopen worden opgeslagen.

Hypothesen zijn beperkt in de tijd en kunnen worden toegepast op een controlegroep die moet worden vergeleken met de doelpopulatie. Hypothetische resultaten worden verstrekt door **indicatoren** die automatisch worden bijgewerkt wanneer de berekening is voltooid. In de campagnerapporten zal rekening worden gehouden met de ROI die aan de hypothesen is gekoppeld.

Ook de **rapporten** voorzien van de Manager van de Reactie laat u toe om de informatie samen te vatten met betrekking tot omzetverhoging, margeberekening, evenals het rendement van de levering of de aanbieding.

Bovendien kunt u dankzij de detailregels voor aankopen uw hypothesen zo instellen dat deze zich bijvoorbeeld op één bepaald product concentreren.

Zo willen we bijvoorbeeld na een levering die een post promoot de gegenereerde inkomsten evalueren. We gaan ervan uit dat iedere ontvanger die in de maand na de activering van de levering ten minste één artikel heeft aangeschaft, op deze actie heeft gereageerd. Op basis van deze hypothese zal het responsbeheer bepalen welke aankoopaanvraaglijnen er aan moeten worden toegewezen. Op basis daarvan zal het dan mogelijk zijn de daaruit voortvloeiende ontvangsten te bepalen als de som van deze begrotingslijnen.

>[!CAUTION]
>
>Responsbeheer is een **[!UICONTROL Campaign]** -optie. Controleer hiervoor uw licentieovereenkomst.

U kunt ook alle reacties berekenen voor het hele huishouden van de ontvanger die de levering of het aanbod heeft ontvangen.

Elke hypothese is gekoppeld aan een enkele transactietabel. Eén levering of aanbieding kan aan meerdere hypothesen worden gekoppeld.

## Implementatiestappen {#method}

Voordat u Reactiebeheer gaat gebruiken, raadpleegt u [Configuratie](configuration.md) en voert de nodige configuraties uit.

Om een hypothese over een levering of een aanbieding te lanceren, moet u zijn context in een malplaatje bepalen dat voor elke hypothese zal worden gebruikt u creeert.

U definieert en maakt meethypothesen door het volgende proces toe te passen:

1. Definieer een hypothesemodel. [Meer informatie](hypothesis-templates.md#creating-a-hypothesis-model)
1. Maak een of meer hypothesen van een bestaande levering. [Meer informatie](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   of

   Maak een of meer hypothesen voor aanbiedingen. [Meer informatie](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Controleer de resultaten van hypothesen. [Meer informatie](hypothesis-tracking.md)
1. Herstart indien nodig hypothesen. [Meer informatie](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
