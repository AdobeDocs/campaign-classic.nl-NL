---
title: Soorten publiek delen met Adobe Experience Cloud
seo-title: Soorten publiek delen met Adobe Experience Cloud
description: Soorten publiek delen met Adobe Experience Cloud
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---


# Sharing audiences with Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>Om deze integratie te kunnen gebruiken, moet IMS zijn geïmplementeerd. Raadpleeg de sectie over [IMS](../../integrations/using/about-adobe-id.md).

Met Adobe Campaign kunt u soorten publiek/segmenten uitwisselen en delen met Adobe Experience Cloud-oplossingen en kernservices. Hiervoor moet u **Adobe Campaign** integreren met de basisservice **** Mensen (ook wel de **kernservice** Profielen en Soorten publiek genoemd) of Adobe Audience Manager. Dan kunt u:

* Importeer gedeelde soorten publiek/segmenten van verschillende Adobe Experience Cloud-oplossingen naar Adobe Campaign. Soorten publiek kan via lijsten in Adobe Campaign worden geïmporteerd.
* Exportlijsten in de vorm van een gedeeld publiek in Adobe Experience Cloud. Deze doelgroepen kunnen worden gebruikt in de verschillende Adobe Experience Cloud-oplossingen die u gebruikt. Soorten publiek kunnen worden geëxporteerd nadat het doelpubliek zich in een workflow heeft gericht, met behulp van een speciale **[!UICONTROL Update shared audience]** activiteit.

>[!CAUTION]
>
>Afhankelijk van het type gegevens kunnen er wettelijke beperkingen gelden voor het importeren van soorten publiek in Adobe Campaign.

De integratie ondersteunt twee typen Adobe Experience Cloud-id&#39;s:

* **Bezoeker-id**: dit type identificator maakt Adobe Experience Cloud-bezoekers in overeenstemming met Adobe Campaign-ontvangers.
* **Opgegeven ID**: dit type id vergelijkt alle soorten gegevens met elementen uit de Adobe Campaign-database. Het wordt in Adobe Campaign vertegenwoordigd als een vooraf gedefinieerde afstemmingssleutel.
