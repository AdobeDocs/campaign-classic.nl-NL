---
product: campaign
title: Anonieme interacties
description: Anonieme interacties
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---

# Anonieme interacties{#anonymous-interactions}

![](assets/do-not-localize/how-to-video.png) Bekijk deze  [](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) video voor een overzicht van hoe aanbiedingen worden geleverd aan geïdentificeerde en anonieme doelen.

## Een omgeving instellen en opslaan voor anonieme interacties {#targeting-and-storing-an-environment-for-anonymous-interactions}

Door gebrek, komt de Interactie met een vooraf gevormd milieu om de ontvankelijke lijst (geïdentificeerde aanbiedingen) te richten. Als u een andere lijst (bezoekerslijst voor anonieme aanbiedingen of een specifieke ontvankelijke lijst) wilt richten, moet u de tovenaar van de doelafbeelding gebruiken om het milieu tot stand te brengen. Zie [Een aanbiedingsomgeving maken](../../interaction/using/live-design-environments.md#creating-an-offer-environment) voor meer informatie.

Wanneer u via de wizard voor het maken van toewijzingen een anonieme omgeving maakt, wordt het selectievakje **[!UICONTROL Environment dedicated to incoming anonymous interactions]** automatisch ingeschakeld op het tabblad **[!UICONTROL General]** van de omgeving.

De **[!UICONTROL Targeting dimension]** wordt automatisch voltooid. Standaard is dit een koppeling naar de bezoekerstabel.

Het veld **[!UICONTROL Visitor folder]** wordt weergegeven. Het wordt automatisch voltooid om aan de **[!UICONTROL Visitors]** omslag te verbinden. In dit veld kunt u kiezen waar bezoekersprofielen worden opgeslagen.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Als u verschillende soorten bezoekers wilt filteren, bijvoorbeeld in het geval van anonieme aanbiedingen die voor een of meer merken worden aangeboden, moet u een omgeving voor elk merk en een **[!UICONTROL Visitors]** typemap voor elke omgeving maken.

## Catalogus aanbieden voor anonieme interacties {#offer-catalog-for-anonymous-interactions}

Net als uitgaande interacties worden inkomende interacties georganiseerd in een aanbiedingencatalogus die bestaat uit categorieën en aanbiedingen.

Als u categorieën en spaties wilt maken, past u hetzelfde proces toe als voor bepaalde bezoekers (zie [Aanbiedingscategorieën maken](../../interaction/using/creating-offer-categories.md) en [Een aanbiedingsomgeving maken](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Anonieme bezoekers {#anonymous-visitors}

Wanneer anonieme bezoekers verbinding maken, kunnen ze een cookie-identificatieproces ondergaan. Deze impliciete herkenning is gebaseerd op de browsergeschiedenis van de bezoeker.

Tijdens deze stap, wordt een vergelijking gemaakt tussen de gegevens die door de koekjes en die in uw gegevensbestand worden teruggekregen. In sommige gevallen wordt de bezoeker erkend (hij wordt dan impliciet geïdentificeerd), in andere gevallen wordt hij niet erkend (en blijft dus anoniem).

Om deze analyse, voor de aanbiedingsruimte in werking te stellen, controleer de **[!UICONTROL Implicitly identify the individual based on their browser history]** optie.

![](assets/identification_anonymous_visitors.png)

## Niet-geïdentificeerde anonieme bezoekers {#processing-unidentified-anonymous-visitors} verwerken

Als een anonieme bezoeker na analyse niet wordt geïdentificeerd, kunt u zijn gegevens opslaan in een bepaalde ruimte. Op deze manier kunt u voorstellen doen die specifiek op dit type bezoeker zijn gericht en die overeenkomen met de opgegeven typologische regels.

Als er geen element is dat u toestaat om een contact te identificeren, of als u geen geïdentificeerde aanbieding aan een contact wilt voorstellen dat impliciet kan worden geïdentificeerd, kunt u verkiezen om een reserve op een anonieme milieu uit te voeren.

Om dit te doen, controleer **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**, dan specificeer het milieu gewijd aan deze niet geïdentificeerde bezoekers in **[!UICONTROL Linked anonymous space]** wanneer het specificeren van een aanbiedingsruimte.

![](assets/anonymous_to_anonymous_environment.png)
