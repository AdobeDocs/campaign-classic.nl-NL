---
product: campaign
title: Soorten publiek delen met Adobe Experience Cloud
description: Soorten publiek delen met Adobe Experience Cloud
feature: Audiences
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Soorten publiek delen met Adobe Experience Cloud {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>Om het publiek met de oplossingen van Adobe Experience Cloud te delen, moet u het Systeem van Adobe Identity Management uitvoeren. [Meer informatie over IMS](../../integrations/using/about-adobe-id.md).

Met Adobe Campaign kunt u soorten publiek en segmenten delen met Adobe Experience Cloud-services. Er zijn twee opties beschikbaar:

1. Verzend Adobe Experience Platform-segmentgegevens naar Adobe Campaign. Als u deze integratie wilt implementeren, moet u een verbinding tot stand brengen tussen uw Real-time Customer Data Platform en Campagne (RTCDP). [Meer informatie in deze sectie](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=nl-NL){target="_blank"}.

1. Integreren **Adobe Campaign** with  **Soorten publiek Experience Cloud** of **Adobe Audience Manager**. Dan kunt u:

   * Importeer gedeelde soorten publiek/segmenten van verschillende Adobe Experience Cloud-oplossingen naar Adobe Campaign. Soorten publiek kan via lijsten in Adobe Campaign worden geïmporteerd.

   * Exportlijsten in de vorm van een gedeeld publiek in Adobe Experience Cloud. Deze doelgroepen kunnen worden gebruikt in de verschillende Adobe Experience Cloud-oplossingen die u gebruikt. Soorten publiek kunnen worden geëxporteerd nadat het doelpubliek zich in een workflow heeft gericht, met behulp van een toegewezen publiek **[!UICONTROL Update shared audience]** activiteit.

Deze integratie ondersteunt twee typen Adobe Experience Cloud-id&#39;s:

* **Bezoeker-id**: dit type id zorgt ervoor dat Adobe Experience Cloud-bezoekers overeenkomen met Adobe Campaign-ontvangers.
* **Opgegeven id**: dit type id zorgt ervoor dat alle typen gegevens overeenkomen met elementen uit de Adobe Campaign-database. Het wordt in Adobe Campaign vertegenwoordigd als een vooraf gedefinieerde afstemmingssleutel.

  >[!NOTE]
  >
  > De opgegeven ID-gegevensbron kan nu ook worden gebruikt bij de integratie van Experience Cloud Assets.
  >
