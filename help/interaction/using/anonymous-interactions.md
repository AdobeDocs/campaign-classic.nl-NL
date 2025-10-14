---
product: campaign
title: Anonieme interacties
description: Anonieme interacties
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 1%

---

# Anonieme interacties{#anonymous-interactions}



![](assets/do-not-localize/how-to-video.png) bekijk deze [&#x200B; video &#x200B;](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&ref=helpx.adobe.com) om een overzicht van te krijgen hoe de aanbiedingen aan geïdentificeerde en anonieme doelstellingen worden geleverd.

## Een omgeving instellen en opslaan voor anonieme interacties {#targeting-and-storing-an-environment-for-anonymous-interactions}

Door gebrek, komt de Interactie met een vooraf gevormd milieu om de ontvankelijke lijst (geïdentificeerde aanbiedingen) te richten. Als u een andere lijst (bezoekerslijst voor anonieme aanbiedingen of een specifieke ontvankelijke lijst) wenst te richten, moet u de medewerker van de doelafbeelding gebruiken om het milieu tot stand te brengen. Voor meer op dit, zie [&#x200B; Creërend een aanbiedingsmilieu &#x200B;](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

Wanneer u een anonieme omgeving maakt via de assistent voor het maken van toewijzingen, wordt het selectievakje **[!UICONTROL Environment dedicated to incoming anonymous interactions]** automatisch ingeschakeld op het tabblad **[!UICONTROL General]** van de omgeving.

**[!UICONTROL Targeting dimension]** wordt automatisch voltooid. Standaard is dit een koppeling naar de bezoekerstabel.

Het veld **[!UICONTROL Visitor folder]** wordt weergegeven. De koppeling naar de map **[!UICONTROL Visitors]** wordt automatisch voltooid. In dit veld kunt u kiezen waar bezoekersprofielen worden opgeslagen.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Als u verschillende soorten bezoekers wilt filteren, bijvoorbeeld in het geval van anonieme aanbiedingen die voor een of meer merken worden aangeboden, moet u een omgeving voor elk merk en een map van het type **[!UICONTROL Visitors]** voor elke omgeving maken.

## Catalogus aanbieden voor anonieme interacties {#offer-catalog-for-anonymous-interactions}

Net als uitgaande interacties worden inkomende interacties georganiseerd in een aanbiedingencatalogus die bestaat uit categorieën en aanbiedingen.

Om categorieën en ruimten tot stand te brengen, pas het zelfde proces zoals voor geïdentificeerde bezoekers toe (verwijs naar [&#x200B; Creërend aanbiedingscategorieën &#x200B;](../../interaction/using/creating-offer-categories.md) en [&#x200B; Creërend een aanbiedingsmilieu &#x200B;](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Anonieme bezoekers {#anonymous-visitors}

Wanneer anonieme bezoekers verbinding maken, kunnen ze een cookie-identificatieproces ondergaan. Deze impliciete herkenning is gebaseerd op de browsergeschiedenis van de bezoeker.

Tijdens deze stap, wordt een vergelijking gemaakt tussen de gegevens die door de koekjes en die in uw gegevensbestand worden teruggekregen. In sommige gevallen worden bezoekers erkend (ze worden dan impliciet geïdentificeerd), in andere gevallen worden ze niet herkend (en blijven dus anoniem).

Als u deze analyse wilt uitvoeren, schakelt u voor de aanbiedingsruimte de optie **[!UICONTROL Implicitly identify the individual based on their browser history]** in.

![](assets/identification_anonymous_visitors.png)

## Niet-geïdentificeerde anonieme bezoekers verwerken {#processing-unidentified-anonymous-visitors}

Als een anonieme bezoeker na analyse niet wordt geïdentificeerd, kunt u zijn gegevens opslaan in een bepaalde ruimte. Op deze manier kunt u voorstellen doen die specifiek op dit type bezoeker zijn gericht en die overeenkomen met de opgegeven typologische regels.

Als er geen element is dat u toestaat om een contact te identificeren, of als u geen geïdentificeerde aanbieding aan een contact wilt voorstellen dat impliciet kan worden geïdentificeerd, kunt u verkiezen om een reserve op een anonieme milieu uit te voeren.

Hiervoor controleert u **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** en geeft u vervolgens de omgeving op die is toegewezen aan deze niet-geïdentificeerde bezoekers in **[!UICONTROL Linked anonymous space]** wanneer u een aanbiedingsruimte opgeeft.

![](assets/anonymous_to_anonymous_environment.png)
