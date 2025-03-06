---
product: campaign
title: Overschakelen naar middelmatige sourcing
description: Meer informatie over workflows voor overbrengen naar Midden-sourcing
hide: true
hidefromtoc: true
feature: Workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 1%

---


# Overschakelen naar middelmatige sourcing{#transfer-to-mid-sourcing}



De hieronder gedetailleerde werkschema&#39;s worden geïnstalleerd met de **Overdracht aan Midden-het bron** module door gebrek. Voor meer op deze module, verwijs naar [ de Gids van de Installatie van Campaign Classic v7 ](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong> Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Midden-sourcing (leveringstellers) </span> <br /> </td> 
   <td> <span class="uicontrol"> defaultMidSourcingDlv </span> <br /> </td> 
   <td> <p>Deze workflow verzamelt tellingsinformatie voor leveringen op de server voor midsourcing. De telgegevens omvatten algemene leveringsindicatoren zoals het aantal verzonden leveringen, enz.</p> <p>Trackinggegevens zoals die worden geopend, worden niet opgenomen.</p> <p>Deze wordt standaard om de tien minuten geactiveerd.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Midden-sourcing (leveringslogboeken) </span> <br /> </td> 
   <td> <span class="uicontrol"> defaultMidSourcingLog </span> <br /> </td> 
   <td> Deze workflow verzamelt leveringslogboeken op de server voor midsourcing. Het wordt teweeggebracht elk uur door gebrek.<br /> </td> 
  </tr> 
 </tbody> 
</table>

