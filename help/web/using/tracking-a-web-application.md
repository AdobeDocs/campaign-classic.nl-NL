---
product: campaign
title: Bezoeken aan een webapplicatie bijhouden
description: Bezoeken aan een webapplicatie bijhouden
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Web Apps, Reporting, Monitoring
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 4%

---

# Bezoeken aan een webapplicatie bijhouden{#tracking-a-web-application}



Met Adobe Campaign kunt u bezoeken op webtoepassingspagina&#39;s bijhouden en meten door trackingtags in te voegen. Deze functionaliteit kan voor alle toepassingstypes van het Web (vormen, Web-pagina&#39;s, enz.) worden gebruikt.

U kunt dus verschillende navigatiepaden definiëren en beoordelen of deze succesvol zijn. De teruggekregen gegevens zijn dan beschikbaar in de rapporten van elke toepassing.

De belangrijkste verbeteringen in deze versie zijn:

* De mogelijkheid om verschillende volgcodes op dezelfde pagina in te voegen om de definitie van navigatiepaden te vereenvoudigen (bijvoorbeeld aankoop, abonnement, retournering, enz.).
* Navigatiepaden en trackingcodes van de verschillende pagina&#39;s weergeven op het dashboard van de webtoepassing.

  ![](assets/trackers_1.png)

* Een volledig traceringsrapport genereren.

  ![](assets/trackers_5.png)

  De belangrijkste indicatoren zijn:

   * **het tarief van de Omzetting**: aantal personen die alle stappen van een navigatiepad getoond hebben.
   * **Stuiteren tarief**: aantal personen die de eerste slechts stap vertoonde
   * **Trechter van de Omzetting**: verliestarief tussen elke stap.

  Bovendien toont het het type van de a **Sector** grafiek de bevolking volgens zijn bron.

## Identificerend de verkeersbron {#identifying-the-traffic-source}

Twee verschillende wijzen kunnen worden gebruikt om te identificeren waar de bezoeker van komt wanneer het toegang tot van een toepassing van het Web:

1. Het verzenden van een specifieke levering om toegang tot de de toepassingspagina&#39;s van het Web te verlenen: in dit geval, is de verkeersbron deze levering,
1. Het associëren van de toepassing van het Web aan een specifieke verkeersbron: in dit geval, moet het een externe &quot;bron&quot;type levering zijn. Het kan van de de toepassingseigenschappen van het Web of van de doelafbeelding worden geselecteerd.

   ![](assets/trackers_6.png)

Om de verkeersbron in een toepassing van het Web te identificeren, zoekt Adobe Campaign achtereenvolgens de volgende informatie:

1. de bron-id, indien aanwezig (nlId cookie);
1. de id van de externe levering die is gedefinieerd in de webtoepassingseigenschappen, indien deze bestaan;
1. de identificatiecode van de externe levering die in de doeltoewijzing is gedefinieerd, indien deze bestaat.

>[!NOTE]
>
>Het anonieme volgen is slechts beschikbaar als de optie in de plaatsingstovenaar toen het installeren van Campagne is geactiveerd.

## Webtoepassingen die zijn ontworpen met Digital Content Editor (DCE) {#web-applications-designed-with-digital-content-editor--dce-}

Wanneer een toepassing van het Web gebruikend de de inhoudsredacteur van de HTML wordt gecreeerd - **de Digitale Redacteur van de Inhoud (DCE)** - volgende markeringen worden opgenomen van het **[!UICONTROL Properties]** lusje van de redacteur. Voor meer informatie over de Digitale Redacteur van de Inhoud (DCE), verwijs naar [ deze sectie ](about-campaign-html-editor.md).

![](assets/trackers_2.png)

Wanneer het gebruiken van de interface van het Web, moet het volgen markeringen van de paginaeigenschappen worden opgenomen.

![](assets/trackers_3.png)

Met het pictogram **[!UICONTROL Display blocks]** kunt u het aantal trackingtags weergeven dat voor de pagina is gedefinieerd.

![](assets/trackers_4.png)
