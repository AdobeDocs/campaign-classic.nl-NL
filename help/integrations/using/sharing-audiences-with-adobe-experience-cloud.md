---
product: campaign
title: Soorten publiek delen met Adobe Experience Cloud
description: Soorten publiek delen met Adobe Experience Cloud
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 6%

---

# Soorten publiek delen met Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}



>[!CAUTION]
>
>Om het publiek met de oplossingen van Adobe Experience Cloud te delen, moet u het Systeem van Adobe Identity Management uitvoeren. [Meer informatie over IMS](../../integrations/using/about-adobe-id.md).

Met Adobe Campaign kunt u soorten publiek en segmenten delen met Adobe Experience Cloud-oplossingen en kernservices. Er zijn twee opties beschikbaar:

1. Verzend Adobe Experience Platform-segmentgegevens naar Adobe Campaign. Als u deze integratie wilt implementeren, moet u een verbinding tot stand brengen tussen uw Real-time Customer Data Platform en Campagne (RTCDP). [Meer informatie in dit gedeelte](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

1. Integreren **Adobe Campaign** with **Personenkern** (ook bekend als **Profielen en publiek kernservice**) of Adobe Audience Manager. Dan kunt u:

   * Importeer gedeelde soorten publiek/segmenten van verschillende Adobe Experience Cloud-oplossingen naar Adobe Campaign. Soorten publiek kan via lijsten in Adobe Campaign worden geïmporteerd.

   * Exportlijsten in de vorm van een gedeeld publiek in Adobe Experience Cloud. Deze doelgroepen kunnen worden gebruikt in de verschillende Adobe Experience Cloud-oplossingen die u gebruikt. Soorten publiek kunnen worden geëxporteerd nadat het doelpubliek zich in een workflow heeft gericht, met behulp van een toegewezen publiek **[!UICONTROL Update shared audience]** activiteit.

Deze integratie ondersteunt twee typen Adobe Experience Cloud-id&#39;s:

* **Bezoeker-id**: dit type id zorgt ervoor dat Adobe Experience Cloud-bezoekers zich kunnen verzoenen met Adobe Campaign-ontvangers.
* **Opgegeven id**: dit type id zorgt ervoor dat alle typen gegevens overeenkomen met elementen uit de Adobe Campaign-database. Het wordt in Adobe Campaign vertegenwoordigd als een vooraf gedefinieerde afstemmingssleutel.

   >[!NOTE]
   >
   > De gegevensbron Declared ID kan nu ook worden gebruikt met de integratie van de People-kernservice.
   >
   >Als u de de dienstintegratie van de Kern van Mensen gebruikt en de integratie van de Audience Manager wilt toevoegen, zult u de hulp van een consultant van Adobe Audience Manager nodig hebben om te vermijden verlies van alle verzamelde syncs van identiteitskaart wanneer het overgaan aan het gebruiken van deze Gedeclareerde gegevensbron van identiteitskaart in een context van Adobe Audience Manager.
