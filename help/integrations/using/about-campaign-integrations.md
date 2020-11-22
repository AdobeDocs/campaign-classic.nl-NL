---
solution: Campaign Classic
product: campaign
title: Campaign-integraties
description: Gebruik andere Adobe-oplossingen en combineer hun verschillende mogelijkheden met Campagne.
audience: integrations
content-type: reference
topic-tags: campaign-integrations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 8%

---


# Get started with Adobe Campaign integrations {#about-campaign-integrations}

Adobe Experience Cloud is een uitgebreide reeks van best-in-klasse, geïntegreerde oplossingen die op een gemeenschappelijk gegevensplatform met een gemeenschappelijke reeks krachtige kerndiensten worden voortgebouwd.

Meer informatie over de beschikbare functionele integratie tussen Adobe Campaign- en [Adobe Experience Cloud-oplossingen](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) en [kernservices](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html). U kunt uw oplossingsimplementaties dan moderniseren en Experience Cloud uitvoeren zodat u eigenschappen zoals klantenattributen en publiek kunt gebruiken.

![](assets/ExCloud-solutions.png)

De volledige lijst van Adobe oplossingen en kerndiensten die met Adobe Campaign kunnen worden geïntegreerd, evenals bijbehorende documentatie, is beschikbaar in [deze sectie](#experience-cloud-integrations).

>[!CAUTION]
>
>De meeste van deze integraties vereisen om het Systeem van Adobe Identity Management (IMS) uit te voeren, aan login via een Adobe ID. [Meer weten op deze pagina](../../integrations/using/about-adobe-id.md)?


## Uw oplossingen koppelen {#working-with-experience-cloud-solutions}

U kunt meerdere oplossingen koppelen aan Adobe Experience Cloud. The **organization** is the customer entity that enables an administrator to configure groups and users, and to control single sign-on (SSO) in Adobe Experience Cloud. De organisatie handelt als een login bedrijf dat alle producten en oplossingen van de Experience Cloud overspant. Meestal is een organisatie uw bedrijfsnaam. Een bedrijf kan echter vele organisaties hebben.

Organisatiebeheer en het koppelen van Adobe Experience Cloud-accounts vindt u in het Help-portaal [van](https://docs.adobe.com/content/help/nl-NL/core-services/interface/manage-users-and-products/organizations.html)Adobe Experience Cloud.

## Identiteitsbeheer en cookie {#id-and-cookies}

Wanneer u Adobe Campaign installeert of een bestaande installatie integreert met Adobe Experience Cloud, wordt de [Adobe Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/id-service/using/home.html) ingeschakeld. Deze service vervangt het permanente cookie dat in de eerste plaats door Adobe Campaign wordt gebruikt voor de trackingfuncties.

De Adobe Experience Cloud Identity Service (ID-service) biedt een universele, permanente id die uw bezoekers identificeert voor alle oplossingen in de Experience Cloud.

Aan ontvangers die trackinglogboeken genereren, wordt een unieke bezoeker-id toegewezen. Deze id wordt opgeslagen in het **[!UICONTROL Requester UUID (@sourceID)]** veld van de **[!UICONTROL nms:trackingLogRcp]** tabel. **De volggegevens van ontvangers die bestonden voordat de bezoekersidentiteitsdienst werd geïmplementeerd, zijn daarom niet langer bruikbaar**.

De id wordt dan herkend door de andere Adobe Experience Cloud-oplossingen met dezelfde [CNAME](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html).

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
   <td> <strong>Adobe Real-time Customer Data Platform (RTCDP)</strong><br /> </td> 
   <td> Dankzij de integratie tussen Adobe Campaign en Adobe Real-time Customer Data Platform (RTCDP) kunt u gegevens over segmenten delen en een publiek importeren naar Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Meer</a> informatie over Campagne - de Adobe integratie van het Platform van de Gegevens van de Klant in real time van de.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
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

