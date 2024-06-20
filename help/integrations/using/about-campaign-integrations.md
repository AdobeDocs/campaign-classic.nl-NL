---
product: campaign
title: Campaign-integraties
description: Gebruik andere Adobe-oplossingen en combineer hun verschillende mogelijkheden met Campaign
feature: Overview
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 597d24fa780a324507c56c55a5309b6ee1cf46eb
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 4%

---

# Aan de slag met Adobe Campaign-integratie {#about-campaign-integrations}

Adobe Experience Cloud is een uitgebreide reeks van best-in-klasse, geïntegreerde oplossingen die op een gemeenschappelijk gegevensplatform met een gemeenschappelijke reeks krachtige oplossingen en apps worden voortgebouwd.

Meer informatie over de beschikbare functionele integratie tussen Adobe Campaign- en Adobe Experience Cloud-oplossingen vindt u in [deze pagina](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/integrations){_blank}.

De volledige lijst met oplossingen en apps voor Adoben die met Adobe Campaign kunnen worden geïntegreerd, en de bijbehorende documentatie vindt u in [deze sectie](#experience-cloud-integrations).

>[!CAUTION]
>
>Deze integratie vereist om Adobe Identity Management System (IMS) uit te voeren, om zich via een Adobe ID aan te melden. [Meer informatie vindt u op deze pagina](../../integrations/using/about-adobe-id.md).
>

## Uw oplossingen koppelen {#working-with-experience-cloud-solutions}

U kunt meerdere oplossingen koppelen aan Adobe Experience Cloud. De **organisatie** is de klantenentiteit die een beheerder toelaat om groepen en gebruikers te vormen, en enige sign-on (SSO) in Adobe Experience Cloud te controleren. De organisatie handelt als een login bedrijf dat alle producten en oplossingen van de Experience Cloud overspant. Meestal is een organisatie uw bedrijfsnaam. Een bedrijf kan echter veel organisaties hebben.

Het beheer van organisaties en het koppelen van Adobe Experience Cloud-accounts worden nader beschreven in het [Adobe Experience Cloud Help-portal](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations){_blank}.

## Identiteitsbeheer en cookie {#id-and-cookies}

Wanneer u Adobe Campaign installeert of een bestaande installatie integreert met Adobe Experience Cloud, kunt u [Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/en/docs/id-service/using/home){_blank} is ingeschakeld. Deze service vervangt het permanente cookie dat in de eerste plaats door Adobe Campaign wordt gebruikt voor de trackingfuncties.

De Adobe Experience Cloud Identity Service (ID-service) biedt een universele, permanente id die uw bezoekers identificeert voor alle oplossingen in het Experience Cloud.

Aan ontvangers die trackinglogboeken genereren, wordt een unieke bezoeker-id toegewezen. Deze id wordt opgeslagen in de **[!UICONTROL Requester UUID (@sourceID)]** van het **[!UICONTROL nms:trackingLogRcp]** tabel. **De traceergegevens van ontvangers die bestonden voordat de dienst met de bezoekersidentiteitskaart werd geïmplementeerd, zullen daarom niet langer bruikbaar zijn**.

De id wordt dan herkend door de andere Adobe Experience Cloud-oplossingen met dezelfde CNAME. [Meer informatie](https://experienceleague.adobe.com/en/docs/id-service/using/reference/analytics-reference/cname){_blank}.

## Experience Cloud-integraties {#experience-cloud-integrations}

De volgende lijst verleent toegang tot beschikbare documentatie van de Experience Cloud integratie.

<table> 
 <thead> 
  <tr> 
   <th> Oplossingen en toepassingen<br /> </th> 
   <th> Gebruiksscenario’s<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform (RTCDP)</strong><br /> </td> 
   <td> Configureer de integratie tussen Adobe Campaign en Adobe Real-time Customer Data Platform (RTCDP) om segmentgegevens te delen en doelgroepen naar Adobe Campaign te importeren.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Meer informatie</a> over Campagne - Adobe Real-time Customer Data Platform-integratie.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> Configureer Adobe IMS om verbinding te maken met Adobe Campaign met dezelfde Adobe ID als voor de andere Adobe Experience Cloud-oplossingen.<br /> Een Adobe ID moet worden gebruikt om zich aan te melden om bepaalde functies te gebruiken die verband houden met de integratie van Adobe Experience Cloud.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Meer informatie</a> over de implementatie van Adobe ID met Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Configureer deze integratie om e-mailinhoud of formulieren te maken die rechtstreeks zijn toegewezen aan de Adobe Campaign-database in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Meer informatie</a> over de integratie tussen Adobe Campaign en Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Configureer deze integratie om afbeeldingen in te voegen die dynamisch zijn berekend door <strong>Adobe Target</strong> wanneer het e-mailbericht dat door Adobe Campaign is gemaakt en verzonden, wordt geopend.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Meer informatie</a> over de integratie tussen Adobe Campaign en Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Configureer deze integratie om gebruikers te laten delen tussen de Adobe Experience Cloud-oplossingen en -toepassingen die u gebruikt.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Meer informatie</a> over de integratie tussen Adobe Campaign en Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Activa</strong><br /> </td> 
   <td> Configureer deze integratie om elementen uit uw Adobe Experience Cloud-bibliotheek in te voegen in e-mails en bestemmingspagina's die in Adobe Campaign zijn gemaakt.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Meer informatie</a> over Adobe Campaign - Integratie van middelen</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Configureer deze integratie om elementen van uw <strong>AEM Assets</strong> bibliotheek naar e-mails en bestemmingspagina's die in Adobe Campaign zijn gemaakt.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Meer informatie</a> over de integratie tussen Adobe Campaign en AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud-triggers</strong><br /> </td> 
   <td> De integratie configureren tussen <strong>Adobe Experience Cloud Triggers</strong> en Adobe Campaign om persoonlijke e-mails naar uw klanten te sturen als reactie op specifieke gedragingen die door Adobe Analytics op uw website worden bijgehouden.<br /> <p><a href="about-triggers.md">Meer informatie</a> over Adobe Campaign - Experience Cloud leidt tot integratie.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics Connector</strong><br /> </td> 
   <td> Configureer deze integratie zodat Adobe Campaign en Adobe Analytics na een e-mailcampagne kunnen communiceren via segmenten met betrekking tot gebruikersgedrag. Omgekeerd verzendt het programma indicatoren en kenmerken van e-mailcampagnes die door Adobe Campaign aan Adobe Analytics worden geleverd.<br /> <p><a href="../../integrations/using/gs-aa.md">Meer informatie</a> over Campagne - integratie van Analytics Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
