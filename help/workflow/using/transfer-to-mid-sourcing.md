---
product: campaign
title: Overdracht naar midsourcing
description: Meer informatie over workflows voor overbrengen naar Midden-sourcing
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 7%

---


# Overdracht naar midsourcing{#transfer-to-mid-sourcing}

![](../../assets/common.svg)

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

