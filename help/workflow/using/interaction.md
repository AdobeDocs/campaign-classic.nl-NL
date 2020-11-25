---
solution: Campaign Classic
product: campaign
title: Interaction
description: Interaction
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: affc541c480ad7e618120fe90270841add06b711
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---


# Interaction{#interaction}

De hieronder beschreven workflows worden standaard geïnstalleerd met de module **Aanbieding (Interactie)** . For more on this module, refer to this [section](../../interaction/using/interaction-and-offer-management.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Volledige geaggregeerde berekening (voorzettingskubus)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> Deze workflow werkt het <strong>volledige</strong> aggregaat voor de <strong>aanbiedingskubus</strong> bij. Het wordt teweeggebracht elke dag om 6 uur door gebrek. In dit aggregaat worden de volgende afmetingen vastgelegd: Kanaal, levering, marketingaanbieding en datum.<br /> De <strong>blokje van het Voorstel</strong> van de Aanbieding wordt dan gebruikt om rapporten te produceren die op aanbiedingen worden gebaseerd. Meer informatie over kubussen vindt u in <a href="../../reporting/using/about-cubes.md">deze sectie</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter volledige geaggregeerde berekening</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Deze werkstroom werkt het <strong>Volledige</strong> aggregaat voor de kubus van het <strong>Centrum</strong> van het Bericht bij. Deze wordt standaard elke dag om 3 uur geactiveerd. In dit aggregaat worden de volgende afmetingen vastgelegd: Het type Kanaal, Datum, Status en Gebeurtenis.<br /> De kubus van het centrum <strong>van het</strong> Bericht wordt dan gebruikt om rapporten te produceren die op gebeurtenissen worden gebaseerd. Meer informatie over kubussen vindt u in <a href="../../reporting/using/about-cubes.md">deze sectie</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

