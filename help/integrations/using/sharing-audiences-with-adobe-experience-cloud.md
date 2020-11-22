---
solution: Campaign Classic
product: campaign
title: Soorten publiek delen met Adobe Experience Cloud
description: Soorten publiek delen met Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Sharing audiences with Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>Om het publiek met de oplossingen van Adobe Experience Cloud te delen, moet u het Systeem van Adobe Identity Management uitvoeren. [Meer informatie over IMS](../../integrations/using/about-adobe-id.md).

Met Adobe Campaign kunt u soorten publiek en segmenten delen met Adobe Experience Cloud-oplossingen en kernservices. Er zijn twee opties beschikbaar:

1. Verzend Adobe Experience Platform-segmentgegevens naar Adobe Campaign. Om deze integratie uit te voeren, moet u uw Platform van Gegevens van de Klant in real time met Campagne (RTCDP) verbinden. [Meer informatie vindt u in deze sectie](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integreer **Adobe Campaign** met de kernservice **** Mensen (ook wel de kernservice **** Profielen en Soorten publiek genoemd) of Adobe Audience Manager. Dan kunt u:

   * Importeer gedeelde soorten publiek/segmenten van verschillende Adobe Experience Cloud-oplossingen naar Adobe Campaign. Soorten publiek kan via lijsten in Adobe Campaign worden geïmporteerd.

   * Exportlijsten in de vorm van een gedeeld publiek in Adobe Experience Cloud. Deze doelgroepen kunnen worden gebruikt in de verschillende Adobe Experience Cloud-oplossingen die u gebruikt. Soorten publiek kunnen worden geëxporteerd nadat het doelpubliek zich in een workflow heeft gericht, met behulp van een speciale **[!UICONTROL Update shared audience]** activiteit.

Deze integratie ondersteunt twee typen Adobe Experience Cloud-id&#39;s:

* **Bezoeker-id**: dit type identificator maakt Adobe Experience Cloud-bezoekers in overeenstemming met Adobe Campaign-ontvangers.
* **Opgegeven ID**: dit type id vergelijkt alle soorten gegevens met elementen uit de Adobe Campaign-database. Het wordt in Adobe Campaign vertegenwoordigd als een vooraf gedefinieerde afstemmingssleutel.
