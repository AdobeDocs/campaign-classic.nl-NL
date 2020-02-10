---
title: Anonieme interacties
seo-title: Anonieme interacties
description: Anonieme interacties
seo-description: null
page-status-flag: never-activated
uuid: 6e28e8a4-8d2f-4747-8dd0-680fbf02b25d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 3fd7a1ef-b0e2-4a7e-9e36-044d997db785
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8e37be4f764feadb49c70a9d598f8f3b8f864380

---


# Anonieme interacties{#anonymous-interactions}

Bekijk deze [video](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&ref=helpx.adobe.com) om een overzicht te krijgen van hoe aanbiedingen worden geleverd aan geïdentificeerde en anonieme doelen.

## Een omgeving instellen en opslaan voor anonieme interacties {#targeting-and-storing-an-environment-for-anonymous-interactions}

Door gebrek, komt de Interactie met een vooraf gevormd milieu om de ontvankelijke lijst (geïdentificeerde aanbiedingen) te richten. Als u een andere lijst (bezoekerslijst voor anonieme aanbiedingen of een specifieke ontvankelijke lijst) wilt richten, moet u de tovenaar van de doelafbeelding gebruiken om het milieu tot stand te brengen. Zie [Een aanbiedingsomgeving](../../interaction/using/live-design-environments.md#creating-an-offer-environment)maken voor meer informatie.

Wanneer u via de wizard voor het maken van toewijzingen een anonieme omgeving maakt, wordt het **[!UICONTROL Environment dedicated to incoming anonymous interactions]** vak automatisch ingecheckt op het **[!UICONTROL General]** tabblad van de omgeving.

De bewerking **[!UICONTROL Targeting dimension]** wordt automatisch voltooid. Standaard is dit een koppeling naar de bezoekerstabel.

Het **[!UICONTROL Visitor folder]** veld wordt weergegeven. De koppeling naar de **[!UICONTROL Visitors]** map wordt automatisch voltooid. In dit veld kunt u kiezen waar bezoekersprofielen worden opgeslagen.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Als u verschillende soorten bezoekers wilt filteren, bijvoorbeeld in het geval van anonieme aanbiedingen die voor een of meer merken worden aangeboden, moet u een omgeving voor elk merk en een **[!UICONTROL Visitors]** typemap voor elke omgeving maken.

## Catalogus aanbieden voor anonieme interacties {#offer-catalog-for-anonymous-interactions}

Net als uitgaande interacties worden inkomende interacties georganiseerd in een aanbiedingencatalogus die bestaat uit categorieën en aanbiedingen.

Om categorieën en ruimten tot stand te brengen, pas het zelfde proces toe zoals voor geïdentificeerde bezoekers (verwijs naar het [Creëren van aanbiedingscategorieën](../../interaction/using/creating-offer-categories.md) en het [Creëren van een aanbiedingsmilieu](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Anonieme bezoekers {#anonymous-visitors}

Wanneer anonieme bezoekers verbinding maken, kunnen ze een cookie-identificatieproces ondergaan. Deze impliciete herkenning is gebaseerd op de browsergeschiedenis van de bezoeker.

Tijdens deze stap, wordt een vergelijking gemaakt tussen de gegevens die door de koekjes en die in uw gegevensbestand worden teruggekregen. In sommige gevallen wordt de bezoeker erkend (hij wordt dan impliciet geïdentificeerd), in andere gevallen wordt hij niet erkend (en blijft dus anoniem).

Voor deze analyse, voor de aanbiedingsruimte, controleer de **[!UICONTROL Implicitly identify the individual based on their browser history]** optie.

![](assets/identification_anonymous_visitors.png)

## Niet-geïdentificeerde anonieme bezoekers verwerken {#processing-unidentified-anonymous-visitors}

Als een anonieme bezoeker na analyse niet wordt geïdentificeerd, kunt u zijn gegevens opslaan in een bepaalde ruimte. Op deze manier kunt u voorstellen doen die specifiek op dit type bezoeker zijn gericht en die overeenkomen met de opgegeven typologische regels.

Als er geen element is dat u toestaat om een contact te identificeren, of als u geen geïdentificeerde aanbieding aan een contact wilt voorstellen dat impliciet kan worden geïdentificeerd, kunt u verkiezen om een reserve op een anonieme milieu uit te voeren.

Om dit te doen, controleer het **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**, dan specificeer het milieu gewijd aan deze niet geïdentificeerde bezoekers in **[!UICONTROL Linked anonymous space]** wanneer het specificeren van een aanbiedingsruimte.

![](assets/anonymous_to_anonymous_environment.png)

