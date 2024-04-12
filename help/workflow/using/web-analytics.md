---
product: campaign
title: Webanalyse
description: Meer informatie over het pakket Webanalyse
feature: Workflows, Analytics Integration
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 1%

---


# Webanalyse{#web-analytics}



De hieronder beschreven workflows worden geïnstalleerd met de **Webanalytische connectors** module standaard. Raadpleeg deze voor meer informatie over deze module [sectie](../../platform/using/gs-aa.md).

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
   <td> Met deze workflow kunt u e-mailcampagneindicatoren van Adobe Campaign naar Adobe Experience Cloud Suite verzenden via de connector voor Adobe® Analytics. De betrokken indicatoren zijn als volgt: <strong>Verzonden</strong> (Verzonden), <strong>Totaal aantal openingen</strong> (iTotalRecipientOpen), <strong>Totaal aantal ontvangers waarop is geklikt</strong> (iTotalRecipientClick), <strong>Fouten</strong> (iError), <strong>Uitschakelen</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identificatie van omgezette contactpersonen</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> Deze workflow indexeert bezoekers van de site die hun aankoop hebben voltooid na een campagne voor het opnieuw op de markt brengen van producten. De gegevens die door deze workflow worden hersteld, zijn toegankelijk in het dialoogvenster <span class="uicontrol">Verslag over de hermarketing van efficiëntie</span>. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Gebeurtenis leegmaken</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Met deze workflow kunt u elke gebeurtenis verwijderen uit het databaseveld, afhankelijk van de periode die in het dialoogvenster <span class="uicontrol">Lifespan</span> veld. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Herstel van webgebeurtenissen</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> Elk uur downloadt deze workflow segmenten op het gedrag van internetgebruikers op een bepaalde site, plaatst deze in de Adobe Campaign-database en start de workflow voor het opnieuw in de handel brengen. <br /> </td> 
  </tr> 
 </tbody> 
</table>

