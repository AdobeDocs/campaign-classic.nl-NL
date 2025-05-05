---
product: campaign
title: Campaign-integraties
description: Gebruik andere Adobe-oplossingen en combineer hun verschillende mogelijkheden met Campaign
feature: Overview
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 4%

---

# Aan de slag met Adobe Campaign-integratie {#about-campaign-integrations}

Adobe Experience Cloud is een uitgebreide reeks van best-in-klasse, geïntegreerde oplossingen die op een gemeenschappelijk gegevensplatform met een gemeenschappelijke reeks krachtige oplossingen en apps worden voortgebouwd.

Leer meer over functionele integratie beschikbaar tussen de oplossingen van Adobe Campaign en van Adobe Experience Cloud in [ deze pagina ](https://experienceleague.adobe.com/nl/docs/core-services/interface/administration/integrations){_blank}.

De volledige lijst van de oplossingen en de apps van Adobe diensten die met Adobe Campaign, evenals bijbehorende documentatie kunnen worden geïntegreerd, is beschikbaar in [ deze sectie ](#experience-cloud-integrations).

>[!CAUTION]
>
>Voor deze integratie is de implementatie van Adobe Identity Management System (IMS) vereist, zodat u zich kunt aanmelden via een Adobe ID. [Meer informatie vindt u op deze pagina](../../integrations/using/about-adobe-id.md).
>

## Uw oplossingen koppelen {#working-with-experience-cloud-solutions}

U kunt meerdere oplossingen koppelen aan Adobe Experience Cloud. De **organisatie** is de klantenentiteit die een beheerder toelaat om groepen en gebruikers te vormen, en enig teken-binnen (SSO) in Adobe Experience Cloud te controleren. De organisatie handelt als een login bedrijf dat alle producten en oplossingen van Experience Cloud overspant. Meestal is een organisatie uw bedrijfsnaam. Een bedrijf kan echter veel organisaties hebben.

Het beheer van de organisatie en het verbinden van de rekeningen van Adobe Experience Cloud zijn gedetailleerd in het [ de hulpportaal van Adobe Experience Cloud ](https://experienceleague.adobe.com/nl/docs/core-services/interface/administration/organizations){_blank}.

## Identiteitsbeheer en cookie {#id-and-cookies}

Wanneer het installeren van Adobe Campaign of het integreren van een bestaande installatie met Adobe Experience Cloud, wordt de [ Dienst van de Identiteit van Adobe Experience Cloud ](https://experienceleague.adobe.com/nl/docs/id-service/using/home){_blank} toegelaten. Deze service vervangt het permanente cookie dat in de eerste plaats door Adobe Campaign wordt gebruikt voor de trackingfuncties.

De Adobe Experience Cloud Identity Service (ID-service) biedt een universele, permanente id die uw bezoekers identificeert voor alle oplossingen in de Experience Cloud.

Aan ontvangers die trackinglogboeken genereren, wordt een unieke bezoeker-id toegewezen. Deze id wordt opgeslagen in het veld **[!UICONTROL Requester UUID (@sourceID)]** van de tabel **[!UICONTROL nms:trackingLogRcp]** . **de volgende gegevens van ontvangers die vóór de dienst van bezoekersidentiteitskaart werden uitgevoerd zullen daarom niet meer bruikbaar** zijn.

De id wordt dan herkend door de andere Adobe Experience Cloud-oplossingen met dezelfde CNAME. [Meer informatie](https://experienceleague.adobe.com/nl/docs/id-service/using/reference/analytics-reference/cname){_blank}.

## Experience Cloud-integraties {#experience-cloud-integrations}

In de volgende tabel vindt u toegang tot de beschikbare documentatie over Experience Cloud-integratie.

<table> 
 <thead> 
  <tr> 
   <th> Oplossingen en toepassingen <br /> </th> 
   <th> Gebruiksscenario’s<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong> Adobe Real-time het Platform van de Gegevens van de Klant (RTCDP) </strong><br /> </td> 
   <td> Configureer de integratie tussen Adobe Campaign en Adobe Real-time Customer Data Platform (RTCDP) voor het delen van segmentgegevens en het importeren van soorten publiek naar Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md"> Leer meer </a> over Campagne - de integratie van het Platform van Gegevens van de Klant in real time van Adobe.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong> het Systeem van Identity Management van Adobe (IMS) - Adobe ID </strong><br /> </td> 
   <td> Configureer Adobe IMS om verbinding te maken met Adobe Campaign met dezelfde Adobe ID als voor de andere Adobe Experience Cloud-oplossingen.<br /> Een Adobe ID moet worden gebruikt om u aan te melden om bepaalde functies te kunnen gebruiken die aan de integratie van Adobe Experience Cloud zijn gekoppeld. <br /> <p><a href="../../integrations/using/about-adobe-id.md"> leer meer </a> over het uitvoeren van Adobe ID met Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong> Adobe Experience Manager </strong><br /> </td> 
   <td> Vorm deze integratie om e-mailinhoud of vormen tot stand te brengen die aan het gegevensbestand van Adobe Campaign direct in <strong> Adobe Experience Manager </strong> worden in kaart gebracht.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md"> leer meer </a> over integratie Adobe Campaign - Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong> Adobe Target </strong><br /> </td> 
   <td> Vorm deze integratie om beelden op te nemen die dynamisch door <strong> Adobe Target </strong> worden gegevens verwerkt wanneer e-mail die door Adobe Campaign wordt gecreeerd en wordt verzonden wordt geopend.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md"> leer meer </a> over integratie Adobe Campaign - Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong> Adobe Audience Manager </strong><br /> </td> 
   <td> Vorm deze integratie om publiek tussen de oplossingen en de apps van Adobe Experience Cloud te delen die u gebruikt.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md"> leer meer </a> over Adobe Campaign - de integratie van Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong> Assets </strong><br /> </td> 
   <td> Configureer deze integratie om elementen uit uw Adobe Experience Cloud-bibliotheek in te voegen in e-mails en bestemmingspagina's die in Adobe Campaign zijn gemaakt.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets"> Leer meer </a> over integratie Adobe Campaign - Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong> AEM Assets </strong><br /> </td> 
   <td> Vorm deze integratie om activa van uw <strong> AEM Assets </strong> bibliotheek in e-mail op te nemen en pagina's te landen die in Adobe Campaign worden gecreeerd.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets"> leer meer </a> over integratie Adobe Campaign - AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong> Triggers van Experience Cloud </strong><br /> </td> 
   <td> Vorm de integratie tussen <strong> Triggers van de Wolk van de Ervaring van Adobe </strong> en Adobe Campaign om gepersonaliseerde e-mails naar uw klanten als reactie op specifiek gedrag te verzenden dat op uw website door Adobe Analytics wordt gevolgd.<br /> <p><a href="about-triggers.md"> Leer meer </a> over Adobe Campaign - Experience Cloud brengt integratie teweeg.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong> Verbinding van Adobe Analytics </strong><br /> </td> 
   <td> Configureer deze integratie zodat Adobe Campaign en Adobe Analytics na een e-mailcampagne kunnen communiceren via segmenten met betrekking tot gebruikersgedrag. Omgekeerd, verzendt het indicatoren en attributen van e-mailcampagnes die door Adobe Campaign aan Adobe Analytics worden geleverd.<br /> <p><a href="../../integrations/using/gs-aa.md"> leer meer </a> over Campagne - de integratie van Verbindingen van de Analyse.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
