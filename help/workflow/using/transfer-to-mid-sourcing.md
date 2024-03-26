---
product: campaign
title: Overschakelen naar middelmatige sourcing
description: Meer informatie over workflows voor overbrengen naar Midden-sourcing
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 7%

---


# Overschakelen naar middelmatige sourcing{#transfer-to-mid-sourcing}



De hieronder beschreven workflows worden geïnstalleerd met de **Overschakelen naar middelmatig bronnen** module standaard. Voor meer informatie over deze module raadpleegt u [Installatiehandleiding voor Campaign Classic v7](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Midden-sourcing (leveringstellers)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>Deze workflow verzamelt tellingsinformatie voor leveringen op de server voor midsourcing. De telgegevens omvatten algemene leveringsindicatoren zoals het aantal verzonden leveringen, enz.</p> <p>Trackinggegevens zoals die worden geopend, worden niet opgenomen.</p> <p>Deze wordt standaard om de tien minuten geactiveerd.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Midden-sourcing (leveringslogboeken)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> Deze workflow verzamelt leveringslogboeken op de server voor midsourcing. Deze wordt standaard elke uur geactiveerd.<br /> </td> 
  </tr> 
 </tbody> 
</table>

