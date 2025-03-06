---
product: campaign
title: Berichtcentrum (controle)
description: Berichtcentrum (controle)
hide: true
hidefromtoc: true
feature: Workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 1%

---


# Berichtcentrum (controle){#message-center-control}



De hieronder beschreven workflow wordt elk uur uitgevoerd. Het is geïnstalleerd met het **Centrum van het Bericht - de module van de Controle** door gebrek.


Raadpleeg de volgende secties voor meer informatie, afhankelijk van uw campagneversie:

![](assets/do-not-localize/v7.jpeg)[ de documentatie van de Campagne v7 ](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[ Campagne v8 documentatie ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong> Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Het Centrum van het bericht &lt;external_account_name&gt; <br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt; <br /> </td> 
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

