---
solution: Campaign Classic
product: campaign
title: Berichtencentrum (controle)
description: Berichtencentrum (controle)
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 7%

---


# Berichtencentrum (controle){#message-center-control}

De hieronder beschreven workflow wordt elk uur uitgevoerd. Het wordt geïnstalleerd met **Centrum van het Bericht - Control** module door gebrek. Voor meer op deze module, verwijs naar dit [sectie](../../message-center/using/about-transactional-messaging.md).

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

