---
title: Over de integratie van campagnes
description: Meer informatie over de beschikbare functionele integratie tussen de huidige versie van Adobe Campaign en [Adobe Experience Cloud-oplossingen]
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e488e1771fe4d07132844900f41f5f4f09fa9438
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 1%

---


# Over de integratie van campagnes {#about-campaign-integrations}

Adobe Experience Cloud is een uitgebreide reeks van best-in-class, geïntegreerde oplossingen die zijn gebaseerd op een gemeenschappelijk gegevensplatform met een gemeenschappelijke reeks krachtige kernservices.

Meer informatie over de beschikbare functionele integratie tussen Adobe Campaign en [Adobe Experience Cloud-oplossingen](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) en [kernservices](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html). Vervolgens kunt u de implementatie van uw oplossing moderniseren en de Experience Cloud implementeren zodat u functies zoals klantkenmerken en doelgroepen kunt gebruiken.

De volledige lijst met Adobe-oplossingen en -kernservices die kunnen worden geïntegreerd in Adobe Campaign, en de bijbehorende documentatie, vindt u in [deze sectie](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>Voor de meeste van deze integraties moet u zich aanmelden met een Adobe-id (IMS). Raadpleeg [deze pagina](../../integrations/using/about-adobe-id.md)voor meer informatie over deze implementatie.
>
>De IMS-implementatie is een complex proces, dat lang kan duren. Het is uitsluitend bestemd voor technische beheerders van Adobe.

## Uw oplossingen koppelen {#working-with-experience-cloud-solutions}

Afhankelijk van uw omgeving kunnen verschillende oplossingen worden gekoppeld aan Adobe Experience Cloud. Ze zijn gekoppeld als organisaties. Een **organisatie** is de entiteit die een beheerder toelaat om groepen en gebruikers te vormen, en enige aanmelding in de Cloud van de Ervaring te controleren. De organisatie werkt als een aanmeldingsbedrijf dat alle producten en oplossingen van de Experience Cloud overspant. Meestal is een organisatie uw bedrijfsnaam. Een bedrijf kan echter veel organisaties hebben.

Organisatiebeheer en het koppelen van Adobe Experience Cloud-accounts vindt u in detail in de Help-portal [van](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html)Adobe Experience Cloud.

>[!CAUTION]
>
>Wanneer u Adobe Campaign opnieuw installeert of een bestaande installatie integreert met Adobe Experience Cloud, wordt de [Experience Cloud ID Service](https://marketing.adobe.com/resources/help/en_US/mcvid/) ingeschakeld. Deze service vervangt het permanente cookie dat in de eerste plaats door Adobe Campaign wordt gebruikt voor de trackingfuncties.
>
>Een unieke bezoeker-id wordt vervolgens toegewezen aan ontvangers die trackinglogboeken genereren. Deze id wordt opgeslagen in het **[!UICONTROL Requester UUID (@sourceID)]** veld van de **[!UICONTROL nms:trackingLogRcp]** tabel. De volggegevens van ontvangers die bestonden voordat de bezoekersidentiteitsdienst werd geïmplementeerd, zullen daarom niet langer bruikbaar zijn.
>
>De id wordt dan herkend door de andere Adobe Experience Cloud-oplossingen met dezelfde [CNAME](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_cname.html).

## Experience Cloud-integraties {#experience-cloud-integrations}

In de volgende tabel vindt u toegang tot de beschikbare documentatie over de integratie van Experience Cloud.

<table> 
 <thead> 
  <tr> 
   <th> Oplossing en kernservices<br /> </th> 
   <th> Gebruik hoofdletters<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time klantgegevensplatform</strong><br /> </td> 
   <td> Dankzij de integratie tussen Adobe Campaign en Adobe Real-time Customer Data Platform kunt u gegevens over segmenten delen en doelgroepen importeren naar Adobe Campagne.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Meer</a> informatie over campagne - integratie van het Adobe Real-time klantgegevensplatform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe-id</strong><br /> </td> 
   <td> Hiermee kunt u verbinding maken met Adobe Campaign met dezelfde Adobe-id als voor de andere Adobe Experience Cloud-oplossingen.<br /> Een Adobe-id moet worden gebruikt om u aan te melden voor het gebruik van bepaalde functies die gekoppeld zijn aan de integratie met de Adobe Experience Cloud, met name Core Services.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Meer</a> informatie over het implementeren van Adobe-id met Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Hiermee kunt u rechtstreeks in <strong>Adobe Experience Manager</strong>e-mailinhoud of formulieren maken die zijn toegewezen aan de Adobe Campagne-database.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Meer</a> informatie over de integratie van Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe-doel</strong><br /> </td> 
   <td> Hiermee kunt u afbeeldingen invoegen die dynamisch door <strong>Adobe Target</strong> zijn berekend wanneer het e-mailbericht dat door Adobe Campaign is gemaakt en verzonden, wordt geopend.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Meer</a> informatie over de integratie van Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People core service</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Hiermee kunt u soorten publiek delen tussen de Adobe Experience Cloud-oplossingen en de kern die u gebruikt.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Meer</a> informatie over de integratie van Adobe Campaign - People core service en Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>De kerndienst van activa</strong><br /> </td> 
   <td> Hiermee kunt u elementen uit uw Adobe Experience Cloud-bibliotheek invoegen in e-mails en bestemmingspagina's die zijn gemaakt in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Meer</a> informatie over Adobe Campagne - De integratie van de elementenkern van de service</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM-middelen</strong><br /> </td> 
   <td> Hiermee kunt u elementen uit uw <strong>AEM Assets</strong> -bibliotheek invoegen in e-mails en bestemmingspagina's die zijn gemaakt in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Meer</a> informatie over de integratie van Adobe Campaign - AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> Dankzij de integratie tussen de <strong>Triggers Core-service</strong> en de Adobe-campagne kunt u persoonlijke e-mails naar uw klanten sturen als reactie op specifieke gedragingen die door Adobe Analytics op uw website worden bijgehouden.<br /> <p><a href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html">Meer</a> informatie over Adobe Campaign - Experience Cloud activeert integratie.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Data Connectors</strong><br /> </td> 
   <td> <strong>Met gegevensconnectors</strong> (voorheen Adobe Genesis genoemd) kunnen Adobe Campaign en Adobe Analytics via segmenten communiceren over het gebruikersgedrag na een e-mailcampagne. Omgekeerd verzendt het programma indicatoren en kenmerken van e-mailcampagnes die door Adobe Campaign worden geleverd naar Adobe Analytics - Data connector.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Meer</a> informatie over campagne - integratie van gegevensconnectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

