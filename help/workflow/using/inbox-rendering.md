---
title: Technisch werkschema voor Inbox-rendering in Adobe Campaign Classic
description: In deze sectie wordt de technische workflow beschreven die met het Inbox-renderingspakket in Adobe Campaign Classic is geïnstalleerd.
page-status-flag: never-activated
uuid: f60a09f0-47a0-4fc0-b0ac-47178af6ad55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: da0779dc-b734-483b-81e9-ff4706a2b6de
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1bd878c45576932e085b579f91eb72f5d36d6fd

---


# Inbox rendering (IR){#inbox-rendering}

De hieronder beschreven workflow wordt standaard geïnstalleerd met de **Inbox Rendering (IR)** -module. Raadpleeg deze [sectie](../../delivery/using/inbox-rendering.md)voor meer informatie over het renderen van de Postvak IN.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Zaadnetwerk bijwerken voor renderen in Postvak</strong><br /> </td> 
   <td> <span class="uicontrol">updateRenderingSeeds</span><br /> </td> 
   <td> Deze workflow werkt e-mailadressen bij die worden gebruikt voor de weergave van Postvakken en werkt alleen als de HTTPS-poort open is voor <strong>leverability.neolane.net</strong>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

