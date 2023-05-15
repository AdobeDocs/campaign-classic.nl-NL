---
product: campaign
title: Berichtencentrum (controle)
description: Berichtencentrum (controle)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 10%

---


# Berichtencentrum (controle){#message-center-control}



De hieronder beschreven workflow wordt elk uur uitgevoerd. Het wordt geïnstalleerd met de **Berichtencentrum - Besturing** module standaard.


Raadpleeg de volgende secties voor meer informatie, afhankelijk van uw campagneversie:

![](assets/do-not-localize/v7.jpeg)[  Documentatie voor Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[  Documentatie voor Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)


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

