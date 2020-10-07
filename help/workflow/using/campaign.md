---
title: Campaign
seo-title: Campaign
description: Campaign
seo-description: null
page-status-flag: never-activated
uuid: 9e5cf203-e5e9-4383-b628-aa6f131491e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: de892ec4-c378-4b22-875e-aa9345f82552
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 3%

---


# Campaign{#campaign}

De hieronder beschreven workflows worden standaard geïnstalleerd met de module **Campagne** . For more on this module, refer to this [section](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>Deze workflows MOETEN worden gestart om de campagneprocessen op campagnereniveau te kunnen uitvoeren.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kostprijsberekening</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> Deze workflow start de berekening van kosten en kostenposten voor de begrotingen, plannen, programma's, campagnes, leveringen en taken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Voorraad: Orders en waarschuwingen</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> Deze workflow start voorraadberekening op de orderregels en beheert drempelwaarden voor waarschuwingen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Banen op leveringen in campagnes</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> Deze workflow activeert de goedgekeurde leveringen en start de naverwerking van de serviceprovider voor een externe levering. Het verzendt ook goedkeuringsberichten en herinneringen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Campagnebanen</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> In deze workflow worden de taken voor marketingcampagnes beheerd (starttaken, bestanden uitpakken, enz.). Het leidt ook tot werkschema's met betrekking tot terugkomende en periodieke campagnes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Banen voor dienstverleners</span> <br /> </td> 
   <td> <span class="uicontrol">providerbeheer</span> <br /> </td> 
   <td> Dit werkschema begint de leverancier (e-mail aan de router en post-verwerking) te verwerken zodra de leveringen zijn goedgekeurd. <br /> </td> 
  </tr> 
 </tbody> 
</table>

