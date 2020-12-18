---
solution: Campaign Classic
product: campaign
title: Responsbeheer
description: Responsbeheer
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---


# Responsbeheer{#about-response-manager}

## Doelstellingen {#objectives}

Adobe Campaign biedt een toepassing voor responsbeheer (Response Manager) waarmee u het succes en de rentabiliteit van marketingcampagnes kunt meten of voorstellen kunt bieden voor alle communicatiekanalen (e-mail, mobiel, telefoon, direct mail, fax, agentschap, enz.).

## Hypotheconcept {#hypothesis-concept}

De hypothesen kunnen over een bepaalde periode van de contactdatum worden gevormd om het gedrag van degenen te verminderen die na het ontvangen van een levering worden gericht. Deze hypothesen zijn gebaseerd op een **transactie** tabel die aankopen en details van deze aankopen bewaart.

Hypothesen zijn beperkt in de tijd en kunnen worden toegepast op een controlegroep die moet worden vergeleken met de doelpopulatie. De resultaten van de hypothese worden verstrekt door **indicatoren** die automatisch worden bijgewerkt zodra de berekening volledig is. In de campagnerapporten zal rekening worden gehouden met de ROI die aan de hypothesen is gekoppeld.

Bovendien **reports** die van de Manager van de Reactie wordt voorzien laat u toe om de informatie samen te vatten verbonden aan omzetverhoging, margeberekening, evenals het rendement van de levering of de aanbieding.

Bovendien kunt u dankzij de detailregels voor aankopen uw hypothesen zo instellen dat deze zich bijvoorbeeld op één bepaald product concentreren.

Zo willen we bijvoorbeeld na een levering die een post promoot de gegenereerde inkomsten evalueren. We gaan ervan uit dat iedere ontvanger die in de maand na de activering van de levering ten minste één artikel heeft aangeschaft, op deze actie heeft gereageerd. Op basis van deze hypothese zal het responsbeheer bepalen welke aankoopaanvraaglijnen er aan moeten worden toegewezen. Op basis daarvan zal het dan mogelijk zijn de resulterende ontvangsten te bepalen als de som van deze begrotingslijnen.

>[!CAUTION]
>
>De Manager van de reactie is een **[!UICONTROL Campaign]** optie. Controleer hiervoor uw licentieovereenkomst.

U kunt ook alle reacties berekenen voor het hele huishouden van de ontvanger die de levering of het aanbod heeft ontvangen.

Elke hypothese is gekoppeld aan een enkele transactietabel. Eén levering of aanbieding kan aan meerdere hypothesen worden gekoppeld.

## Methode {#method}

Alvorens u begint de Manager van de Reactie te gebruiken, verwijs naar [Configuratie](../../campaign/using/configuration.md) en voer de noodzakelijke configuraties uit.

Om een hypothese over een levering of een aanbieding te lanceren, moet u zijn context in een malplaatje bepalen dat voor elke hypothese zal worden gebruikt u creeert.

U definieert en maakt meethypothesen door het volgende proces toe te passen:

1. Definieer een hypothesemodel. Zie [Een hypothesemodel maken](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Maak een of meer hypothesen van een bestaande levering. Zie [Verwijzen naar een hypothese in een campagnelevering](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery).

   of

   Maak een of meer hypothesen voor aanbiedingen. Zie [Een hypothese maken over een aanbieding](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer).

1. Controleer de resultaten van hypothesen. Zie [Hypothese bijhouden](../../campaign/using/hypothesis-tracking.md).
1. Herstart indien nodig hypothesen. Zie [Een hypothese maken tijdens een levering](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery).

