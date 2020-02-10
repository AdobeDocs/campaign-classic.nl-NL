---
title: Berichtcentrum (controle)
seo-title: Berichtcentrum (controle)
description: Berichtcentrum (controle)
seo-description: null
page-status-flag: never-activated
uuid: bdb3610b-a893-4e60-a9f7-f21d90b66919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 69e3e99f-d392-4316-926c-3c3c675415ad
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Berichtcentrum (controle){#message-center-control}

De hieronder beschreven workflow wordt elk uur uitgevoerd. Het wordt geïnstalleerd met het Centrum van het **Bericht - de module van de Controle** door gebrek. Raadpleeg deze [sectie](../../message-center/using/about-transactional-messaging.md)voor meer informatie over deze module.

Meer over hoe te om technische werkschema&#39;s met betrekking tot de module van het Centrum van het Bericht te vormen, verwijs naar [deze pagina](../../message-center/using/technical-workflows.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Berichtencentrum &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> Deze workflow:<br /> 
    <ul> 
     <li> <p>Hiermee wordt de lijst met gebeurtenissen hersteld die door de bewerking(en) zijn verwerkt.</p> </li> 
     <li> <p>synchroniseert met de tabel NmsBroadLogMsg om de kwalificaties van de leveringsberichten te herstellen.</p> </li> 
     <li> <p>Hiermee worden de logbestanden voor gebeurtenislevering hersteld zodra de synchronisatie met de tabel NmsBroadLogMsg is voltooid.</p> </li> 
     <li> <p>synchroniseert met de tabel NmsTrackingUrl om de tracking voor bezorgings-URL's te herstellen.</p> </li> 
     <li> <p>Hiermee worden URL's voor het bijhouden van gebeurtenissen hersteld zodra de synchronisatie met de tabel NmsTrackingUrl is voltooid.</p> </li> 
     <li> <p>Hiermee kunt u alle e-mailadressen herstellen die elke drie uur nadat een levering is verzonden, in quarantaine zijn geplaatst.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

