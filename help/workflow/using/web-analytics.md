---
title: Webanalyse
seo-title: Webanalyse
description: Webanalyse
seo-description: null
page-status-flag: never-activated
uuid: 63742453-16d9-48c2-9a3d-d96f5b131fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: cc2d4741-2b26-4933-a28d-5dd7b5f436be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Webanalyse{#web-analytics}

De hieronder beschreven workflows worden standaard geïnstalleerd met de **module Web Analytics** . Raadpleeg deze [sectie](../../platform/using/adobe-analytics-data-connector.md)voor meer informatie over deze module.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Verzending van indicatoren en campagnerekenmerken</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span><br /> </td> 
   <td> Met deze workflow kunt u e-mailcampagneindicatoren vanuit Adobe Campaign naar Adobe Experience Cloud Suite verzenden via de Adobe® Genesis-connector. De betrokken indicatoren zijn als volgt: <strong>Verzonden</strong> (Verzonden), <strong>Totaal aantal van opent</strong> (iTotalRecipientOpen), <strong>Totaal aantal ontvangers die klikte</strong> (iTotalRecipientClick), <strong>Fouten</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identificatie van omgezette contactpersonen</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span><br /> </td> 
   <td> Deze workflow indexeert bezoekers van de site die hun aankoop hebben voltooid na een campagne voor het opnieuw op de markt brengen van producten. De gegevens die door deze workflow worden hersteld, zijn toegankelijk via het efficiëntierapport <span class="uicontrol">voor</span> opnieuw in de handel brengen (zie deze <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> pagina</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Gebeurtenis leegmaken</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span><br /> </td> 
   <td> Met deze workflow kunt u elke gebeurtenis uit het databaseveld verwijderen op basis van de periode die is geconfigureerd in het veld <span class="uicontrol">Lifespan</span> . <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Herstel van webgebeurtenissen</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span><br /> </td> 
   <td> Elk uur downloadt deze workflow segmenten op het gedrag van internetgebruikers op een bepaalde site, plaatst deze in de Adobe Campagne-database en start de workflow voor het opnieuw in de handel brengen. <br /> </td> 
  </tr> 
 </tbody> 
</table>

