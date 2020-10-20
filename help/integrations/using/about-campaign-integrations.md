---
title: Campaign-integraties
description: Gebruik andere Adobe-oplossingen en combineer hun verschillende mogelijkheden met Campagne.
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 10%

---


# Campaign-integraties {#about-campaign-integrations}

Adobe Experience Cloud is een uitgebreide reeks van best-in-klasse, geïntegreerde oplossingen die op een gemeenschappelijk gegevensplatform met een gemeenschappelijke reeks krachtige kerndiensten worden voortgebouwd.

Meer informatie over de beschikbare functionele integratie tussen Adobe Campaign- en [Adobe Experience Cloud-oplossingen](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) en [kernservices](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html). U kunt uw oplossingsimplementaties dan moderniseren en Experience Cloud uitvoeren zodat u eigenschappen zoals klantenattributen en publiek kunt gebruiken.

De volledige lijst van Adobe oplossingen en kerndiensten die met Adobe Campaign kunnen worden geïntegreerd, evenals bijbehorende documentatie, is beschikbaar in [deze sectie](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>Voor de meeste van deze integraties moet u zich aanmelden via een Adobe ID (IMS). For more on this implementation, refer to [this page](../../integrations/using/about-adobe-id.md).
>
>De IMS-implementatie is een complex proces, dat lang kan duren. Het is strikt voorbehouden aan de technische beheerders van de Adobe.

## Uw oplossingen koppelen {#working-with-experience-cloud-solutions}

Afhankelijk van uw omgeving kunnen verschillende oplossingen aan Adobe Experience Cloud worden gekoppeld. Ze zijn gekoppeld als organisaties. An **organization** is the entity that enables an administrator to configure groups and users, and to control single sign-on in the Experience Cloud. De organisatie functioneert als een aanmeldingsbedrijf dat alle producten en oplossingen van Experience Cloud omvat. Meestal is een organisatie uw bedrijfsnaam. Een bedrijf kan echter vele organisaties hebben.

Organisatiebeheer en het koppelen van Adobe Experience Cloud-accounts vindt u in het Help-portaal [van](https://docs.adobe.com/content/help/nl-NL/core-services/interface/manage-users-and-products/organizations.html)Adobe Experience Cloud.

>[!CAUTION]
>
>Wanneer u Adobe Campaign voor het eerst installeert of een bestaande installatie integreert met Adobe Experience Cloud, wordt de [Experience Cloud ID-service](https://docs.adobe.com/content/help/en/id-service/using/home.html) ingeschakeld. Deze service vervangt het permanente cookie dat in de eerste plaats door Adobe Campaign wordt gebruikt voor de trackingfuncties.
>
>Een unieke bezoeker-id wordt vervolgens toegewezen aan ontvangers die trackinglogboeken genereren. Deze id wordt opgeslagen in het **[!UICONTROL Requester UUID (@sourceID)]** veld van de **[!UICONTROL nms:trackingLogRcp]** tabel. De volggegevens van ontvangers die bestonden voordat de bezoekersidentiteitsdienst werd geïmplementeerd, zullen daarom niet langer bruikbaar zijn.
>
>De id wordt dan herkend door de andere Adobe Experience Cloud-oplossingen met dezelfde [CNAME](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html).

## Experience Cloud-integraties {#experience-cloud-integrations}

De volgende lijst verleent toegang tot beschikbare documentatie van de Experience Cloud integratie.

<table> 
 <thead> 
  <tr> 
   <th> Oplossing en kernservices<br /> </th> 
   <th> Gebruiksscenario’s<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform</strong><br /> </td> 
   <td> Dankzij de integratie tussen Adobe Campaign en Adobe Real-time Customer Data Platform kunt u segmentgegevens delen en publiek importeren naar Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Meer</a> informatie over Campagne - de Adobe integratie van het Platform van de Gegevens van de Klant in real time van de.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> Hiermee kunt u verbinding maken met Adobe Campaign met dezelfde Adobe ID als voor de andere Adobe Experience Cloud-oplossingen.<br /> Een Adobe ID moet worden gebruikt om zich aan te melden om bepaalde functies te gebruiken die verband houden met de integratie van Adobe Experience Cloud, met name Core Services.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Meer</a> weten over het implementeren van Adobe ID met Adobe Campaign?</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Allows you to create email contents or forms mapped to the Adobe Campaign database directly in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Meer</a> weten over de integratie tussen Adobe Campaign en Adobe Experience Manager?</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Allows you to insert images that are dynamically computed by <strong>Adobe Target</strong> when the email created and sent by Adobe Campaign is opened.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Meer</a> weten over de integratie tussen Adobe Campaign en Adobe Target?</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People core service</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Hiermee kunt u een publiek delen tussen de Adobe Experience Cloud-oplossingen en de kern die u gebruikt.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Meer</a> informatie over Adobe Campaign - People core service en Adobe Audience Manager integratie.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>De kerndienst van activa</strong><br /> </td> 
   <td> Hiermee kunt u assets uit uw Adobe Experience Cloud-bibliotheek invoegen in e-mails en landingspagina’s die in Adobe Campaign zijn gemaakt.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Meer</a> informatie over de integratie van Adobe Campaign - Assets core service</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Allows you to insert assets from your <strong>AEM Assets</strong> library into emails and landing pages created in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Meer</a> weten over de integratie tussen Adobe Campaign en AEM Assets?</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> Integration between <strong>Triggers core service</strong> and Adobe Campaign allows you to send personalized emails to your customers as a reaction to specific behaviors that are tracked on your website by Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/nl/campaign/kb/triggers-and-campaign.html">Meer</a> informatie over Adobe Campaign - Experience Cloud activeert integratie.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Gegevensconnectors</strong><br /> </td> 
   <td> <strong>Via gegevensconnectors</strong> (voorheen Adobe Genesis genoemd) kunnen Adobe Campaign en Adobe Analytics op verschillende gebieden communiceren over het gebruikersgedrag na een e-mailcampagne. Omgekeerd verzendt het programma indicatoren en kenmerken van e-mailcampagnes die door Adobe Campaign worden geleverd aan Adobe Analytics - Gegevensconnector.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Meer</a> informatie over campagne - integratie van gegevensconnectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

