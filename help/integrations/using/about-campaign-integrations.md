---
product: campaign
title: Campaign-integraties
description: Gebruik andere Adobe-oplossingen en combineer hun verschillende mogelijkheden met Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 12%

---

# Aan de slag met Adobe Campaign-integratie {#about-campaign-integrations}



Adobe Experience Cloud is een uitgebreide reeks van best-in-klasse, geïntegreerde oplossingen die op een gemeenschappelijk gegevensplatform met een gemeenschappelijke reeks krachtige kerndiensten worden voortgebouwd.

Meer informatie over functionele integratie tussen Adobe Campaign en [Adobe Experience Cloud-oplossingen](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html) en [kerndiensten](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html). U kunt uw oplossingsimplementaties dan moderniseren en Experience Cloud uitvoeren zodat u eigenschappen zoals klantenattributen en publiek kunt gebruiken.

![](assets/ExCloud-solutions.png)

De volledige lijst van Adobe oplossingen en kerndiensten die met Adobe Campaign kunnen worden geïntegreerd, en bijbehorende documentatie is beschikbaar in [deze sectie](#experience-cloud-integrations).

>[!CAUTION]
>
>De meeste van deze integraties vereisen om het Systeem van Adobe Identity Management (IMS) uit te voeren, aan login via een Adobe ID. [Meer informatie vindt u op deze pagina](../../integrations/using/about-adobe-id.md).

## Uw oplossingen koppelen {#working-with-experience-cloud-solutions}

U kunt meerdere oplossingen koppelen aan Adobe Experience Cloud. De **organisatie** is de klantenentiteit die een beheerder toelaat om groepen en gebruikers te vormen, en enige sign-on (SSO) in Adobe Experience Cloud te controleren. De organisatie handelt als een login bedrijf dat alle producten en oplossingen van de Experience Cloud overspant. Meestal is een organisatie uw bedrijfsnaam. Een bedrijf kan echter vele organisaties hebben.

Het beheer van organisaties en het koppelen van Adobe Experience Cloud-accounts worden nader beschreven in het [Adobe Experience Cloud Help Portal](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html).

## Identiteitsbeheer en cookie {#id-and-cookies}

Wanneer u Adobe Campaign installeert of een bestaande installatie integreert met Adobe Experience Cloud, wordt [Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html) is ingeschakeld. Deze service vervangt het permanente cookie dat in de eerste plaats door Adobe Campaign wordt gebruikt voor de trackingfuncties.

De Adobe Experience Cloud Identity Service (ID-service) biedt een universele, permanente id die uw bezoekers identificeert voor alle oplossingen in de Experience Cloud.

Aan ontvangers die trackinglogboeken genereren, wordt een unieke bezoeker-id toegewezen. Deze id wordt opgeslagen in de **[!UICONTROL Requester UUID (@sourceID)]** van het **[!UICONTROL nms:trackingLogRcp]** tabel. **De traceergegevens van ontvangers die bestonden voordat de dienst met de bezoekersidentiteitskaart werd geïmplementeerd, zullen daarom niet langer bruikbaar zijn**.

De id wordt dan herkend door de andere Adobe Experience Cloud-oplossingen met dezelfde CNAME. [Meer informatie](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/cname.html)

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
   <td> Dankzij de integratie tussen Adobe Campaign en Adobe Real-time Customer Data Platform (RTCDP) kunt u segmentgegevens delen en doelgroepen importeren naar Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Meer informatie</a> over Campagne - Adobe Real-time Customer Data Platform-integratie.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> Hiermee kunt u verbinding maken met Adobe Campaign met dezelfde Adobe ID als voor de andere Adobe Experience Cloud-oplossingen.<br /> Een Adobe ID moet worden gebruikt om zich aan te melden om bepaalde functies te gebruiken die verband houden met de integratie van Adobe Experience Cloud, met name Core Services.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Meer informatie</a> over de implementatie van Adobe ID met Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Hiermee kunt u e-mailinhoud of formulieren maken die rechtstreeks zijn toegewezen aan de Adobe Campaign-database in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Meer informatie</a> over de integratie tussen Adobe Campaign en Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Hiermee kunt u afbeeldingen invoegen die dynamisch zijn berekend door <strong>Adobe Target</strong> wanneer het e-mailbericht dat door Adobe Campaign is gemaakt en verzonden, wordt geopend.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Meer informatie</a> over de integratie tussen Adobe Campaign en Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Personenkern</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Hiermee kunt u een publiek delen tussen de Adobe Experience Cloud-oplossingen en de kern die u gebruikt.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Meer informatie</a> over Adobe Campaign - People core service en Adobe Audience Manager integratie.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>De kerndienst van activa</strong><br /> </td> 
   <td> Hiermee kunt u assets uit uw Adobe Experience Cloud-bibliotheek invoegen in e-mails en landingspagina’s die in Adobe Campaign zijn gemaakt.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Meer informatie</a> over Adobe Campaign - Integratie van de kernservice Middelen</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Hiermee kunt u elementen van uw <strong>AEM Assets</strong> bibliotheek naar e-mails en bestemmingspagina's die in Adobe Campaign zijn gemaakt.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Meer informatie</a> over de integratie tussen Adobe Campaign en AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> Integratie tussen <strong>Triggers Core-service</strong> en Adobe Campaign stelt u in staat persoonlijke e-mails naar uw klanten te sturen als reactie op specifieke gedragingen die door Adobe Analytics op uw website worden bijgehouden.<br /> <p><a href="https://helpx.adobe.com/nl/campaign/kb/triggers-and-campaign.html">Meer informatie</a> over Adobe Campaign - Experience Cloud zorgt voor integratie.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics-connector</strong><br /> </td> 
   <td> <strong>Adobe Analytics Connector</strong> Adobe Campaign en Adobe Analytics kunnen segmenten doorlopen die betrekking hebben op gebruikersgedrag na een e-mailcampagne. Omgekeerd verzendt het programma indicatoren en kenmerken van e-mailcampagnes die door Adobe Campaign aan Adobe Analytics worden geleverd.<br /> <p><a href="../../platform/using/adobe-analytics-connector.md">Meer informatie</a> over Campagne - integratie van Analytics Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
