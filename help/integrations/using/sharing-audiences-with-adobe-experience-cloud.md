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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 418a36cd51106dae2b4201c8b5abda9b05285a18

---


# Soorten publiek delen met Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>Om deze integratie te kunnen gebruiken, moet IMS zijn geïmplementeerd. Raadpleeg de sectie over [IMS](../../integrations/using/about-adobe-id.md).

Met Adobe Campaign kunt u soorten publiek en segmenten uitwisselen en delen met Adobe Experience Cloud-oplossingen en -kernservices. Hiervoor moet u **Adobe Campagne** integreren met de basisservice **** Personen (ook wel de kernservice **** Profielen en soorten publiek genoemd) of Adobe Audience Manager. Dan kunt u:

* Importeer gedeelde soorten publiek/segmenten van verschillende Adobe Experience Cloud-oplossingen naar Adobe Campagne. Soorten publiek kan worden geïmporteerd via lijsten in Adobe Campaign.
* Exportlijsten in de vorm van een gedeeld publiek voor Adobe Experience Cloud. Deze doelgroepen kunnen worden gebruikt in de verschillende Adobe Experience Cloud-oplossingen die u gebruikt. Soorten publiek kunnen worden geëxporteerd nadat het doelpubliek zich in een workflow heeft gericht, met behulp van een speciale **[!UICONTROL Update shared audience]** activiteit.

>[!CAUTION]
>
>Afhankelijk van het type gegevens kunnen er wettelijke beperkingen gelden voor het importeren van soorten publiek in Adobe Campaign.

De integratie ondersteunt twee typen Adobe Experience Cloud-id&#39;s:

* **Bezoeker-id**: dit type id zorgt ervoor dat bezoekers van Adobe Experience Cloud kunnen kiezen voor de ontvangers van Adobe Campagne.
* **Opgegeven ID**: dit type id zorgt ervoor dat alle typen gegevens worden vergeleken met elementen uit de Adobe Campagne-database. Het wordt in Adobe Campaign weergegeven als een vooraf gedefinieerde verzoeningssleutel.
