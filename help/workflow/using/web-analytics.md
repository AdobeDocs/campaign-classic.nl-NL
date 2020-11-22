---
solution: Campaign Classic
product: campaign
title: Web Analytics
description: Meer informatie over het pakket Webanalyse
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# Web Analytics{#web-analytics}

De hieronder beschreven workflows worden standaard geïnstalleerd met de **module Web Analytics** . For more on this module, refer to this [section](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Verzending van indicatoren en campagnerekenmerken</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> Met deze workflow kunt u e-mailcampagne-indicatoren verzenden van Adobe Campaign naar Adobe Experience Cloud Suite via de Adobe® Genesis-connector. De betrokken indicatoren zijn als volgt: <strong>Verzonden</strong> (Verzonden), <strong>Totaal aantal opent</strong> (iTotalRecipientOpen), <strong>Totaal aantal ontvangers die klikte</strong> (iTotalRecipientClick), <strong>Fouten</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identificatie van omgezette contactpersonen</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> Deze workflow indexeert bezoekers van de site die hun aankoop hebben voltooid na een campagne voor het opnieuw op de markt brengen van producten. De gegevens die door deze workflow worden hersteld, zijn toegankelijk in het efficiëntierapport <span class="uicontrol">voor</span> opnieuw in de handel brengen (zie deze <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> pagina</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Gebeurtenis leegmaken</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Met deze workflow kunt u elke gebeurtenis uit het databaseveld verwijderen op basis van de periode die is geconfigureerd in het veld <span class="uicontrol">Lifespan</span> . <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Herstel van webgebeurtenissen</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> Elk uur downloadt deze workflow segmenten op het gedrag van internetgebruikers op een bepaalde site, plaatst deze in de Adobe Campaign-database en start de workflow voor het opnieuw in de handel brengen. <br /> </td> 
  </tr> 
 </tbody> 
</table>

