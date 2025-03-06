---
product: campaign
title: Campaign
description: Campaign
feature: Workflows
hide: true
hidefromtoc: true
topic-tags: technical-workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---


# Campaign{#campaign}



De hieronder gedetailleerde werkschema&#39;s worden geïnstalleerd met de **Campagne** module door gebrek. Voor meer op deze module, verwijs naar deze [ sectie ](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>Deze workflows MOETEN worden gestart om de campagneprocessen op campagnereniveau te kunnen uitvoeren.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong> Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Berekening van Kosten </span> <br /> </td> 
   <td> <span class="uicontrol"> budgetMgt </span> <br /> </td> 
   <td> Dit werkschema begint de berekening van uitgave en kostenlijnen op de begrotingen, de plannen, de programma's, de campagnes, de leveringen en de taken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Voorraad: Orders en alarm </span> <br /> </td> 
   <td> <span class="uicontrol"> stockMgt </span> <br /> </td> 
   <td> Dit werkschema lanceert voorraadberekening op de ordelijnen en beheert waarschuwingsalarmdrempels.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Banen op leveringen in campagnes </span> <br /> </td> 
   <td> </span> <br /> 0} deliveryMgt<span class="uicontrol"> </td> 
   <td> Deze workflow activeert de goedgekeurde leveringen en start de naverwerking van de serviceprovider voor een externe levering. Het verzendt ook goedkeuringsberichten en herinneringen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> de banen van de Campagne </span> <br /> </td> 
   <td> <span class="uicontrol"> operationMgt </span> <br /> </td> 
   <td> In deze workflow worden de taken voor marketingcampagnes beheerd (starttaken, bestanden uitpakken, enz.). Het leidt ook tot werkschema's met betrekking tot terugkomende en periodieke campagnes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Banen op dienstverleners </span> <br /> </td> 
   <td> <span class="uicontrol"> providerMgt </span> <br /> </td> 
   <td> Dit werkschema begint de leverancier (e-mail aan de router en post-verwerking) te verwerken zodra de leveringen zijn goedgekeurd. <br /> </td> 
  </tr> 
 </tbody> 
</table>

