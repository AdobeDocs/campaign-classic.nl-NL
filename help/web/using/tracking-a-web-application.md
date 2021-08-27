---
product: campaign
title: Een webapplicatie opvolgen
description: Een webapplicatie opvolgen
audience: web
content-type: reference
topic-tags: web-applications
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 3%

---

# Bezoeken aan een webapplicatie bijhouden{#tracking-a-web-application}

![](../../assets/common.svg)

Met Adobe Campaign kunt u bezoeken op webtoepassingspagina&#39;s bijhouden en meten door trackingtags in te voegen. Deze functionaliteit kan voor alle toepassingstypes van het Web (vormen, Web-pagina&#39;s, enz.) worden gebruikt.

U kunt dus verschillende navigatiepaden definiëren en het succes ervan beoordelen. De teruggekregen gegevens zijn dan beschikbaar in de rapporten van elke toepassing.

De belangrijkste verbeteringen in deze versie zijn:

* De mogelijkheid om verschillende volgcodes op dezelfde pagina in te voegen om de definitie van navigatiepaden te vereenvoudigen (bijvoorbeeld aankoop, abonnement, retournering, enz.).
* Navigatiepaden en trackingcodes van de verschillende pagina&#39;s weergeven op het dashboard van de webtoepassing.

   ![](assets/trackers_1.png)

* Een volledig traceringsrapport genereren.

   ![](assets/trackers_5.png)

   De belangrijkste indicatoren zijn:

   * **Conversiesnelheid**: aantal personen dat alle stappen van een navigatiepad heeft weergegeven.
   * **Stuitsnelheid**: aantal personen dat alleen de eerste stap heeft getoond
   * **Conversietrechter**: verliespercentage tussen elke stap.

   Bovendien toont een **Sectordiagram** de populatie volgens zijn bron.

## Identificerend de verkeersbron {#identifying-the-traffic-source}

Twee verschillende wijzen kunnen worden gebruikt om te identificeren waar de bezoeker van komt wanneer het toegang tot van een toepassing van het Web:

1. Het verzenden van een specifieke levering om toegang tot de de toepassingspagina&#39;s van het Web te verlenen: in dit geval is de verkeersbron deze levering;
1. Het associëren van de toepassing van het Web aan een specifieke verkeersbron: in dit geval moet het een externe levering van het type &quot;verkeersbron&quot; zijn. Het kan van de de toepassingseigenschappen van het Web of van de doelafbeelding worden geselecteerd.

   ![](assets/trackers_6.png)

Om de verkeersbron in een toepassing van het Web te identificeren, zoekt Adobe Campaign achtereenvolgens de volgende informatie:

1. de bron-id, indien aanwezig (nlId cookie);
1. de id van de externe levering die is gedefinieerd in de webtoepassingseigenschappen, indien deze bestaan;
1. de identificatiecode van de externe levering die in de doeltoewijzing is gedefinieerd, indien deze bestaat.

>[!NOTE]
>
>Het anonieme volgen is slechts beschikbaar als de optie in de plaatsingstovenaar toen het installeren van Campagne is geactiveerd.

## Webtoepassingen die zijn ontworpen met Digital Content Editor (DCE) {#web-applications-designed-with-digital-content-editor--dce-}

Als een webtoepassing wordt gemaakt met de HTML-inhoudeditor - **Digital Content Editor (DCE)** - worden trackingtags ingevoegd op het tabblad **[!UICONTROL Properties]** van de editor. Raadpleeg [deze sectie](about-campaign-html-editor.md) voor meer informatie over de Digital Content Editor (DCE).

![](assets/trackers_2.png)

Wanneer het gebruiken van de interface van het Web, moet het volgen markeringen van de paginaeigenschappen worden opgenomen.

![](assets/trackers_3.png)

Met het pictogram **[!UICONTROL Display blocks]** kunt u het aantal trackinglabels weergeven dat voor de pagina is gedefinieerd.

![](assets/trackers_4.png)
