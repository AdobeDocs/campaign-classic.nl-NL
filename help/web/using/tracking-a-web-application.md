---
product: campaign
title: Bezoeken aan een webapplicatie bijhouden
description: Bezoeken aan een webapplicatie bijhouden
badge-v7: label="v7" type="Informative" tooltip="Van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Web Apps, Reporting, Monitoring
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '413'
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

   * **Omrekeningskoers**: aantal personen dat alle stappen van een navigatiepad heeft weergegeven.
   * **Stuitpercentage**: aantal personen dat alleen de eerste stap heeft getoond
   * **Conversietrechter**: verliespercentage tussen elke stap.

  Bovendien **Sector** de typegrafiek geeft de populatie weer volgens de bron .

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

Wanneer een toepassing van het Web gebruikend de inhoudsredacteur van HTML wordt gecreeerd - **Digital Content Editor (DCE)** - tags voor bijhouden worden ingevoegd vanuit het **[!UICONTROL Properties]** tabblad van de editor. Raadpleeg voor meer informatie over de Digital Content Editor (DCE) [deze sectie](about-campaign-html-editor.md).

![](assets/trackers_2.png)

Wanneer het gebruiken van de interface van het Web, moet het volgen markeringen van de paginaeigenschappen worden opgenomen.

![](assets/trackers_3.png)

De **[!UICONTROL Display blocks]** Met dit pictogram kunt u het aantal trackinglabels weergeven dat voor de pagina is gedefinieerd.

![](assets/trackers_4.png)
