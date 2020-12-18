---
solution: Campaign Classic
product: campaign
title: Interaction
description: Interactie
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

De hieronder beschreven workflows worden geïnstalleerd met de **Aanbiedingsmotor (Interactie)** module door gebrek. Voor meer op deze module, verwijs naar dit [sectie](../../interaction/using/interaction-and-offer-management.md).

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
   <td> Deze workflow werkt het <strong>Volledige</strong> aggregaat bij voor de <strong>Propositie aanbieding</strong> kubus. Het wordt teweeggebracht elke dag om 6 uur door gebrek. In dit aggregaat worden de volgende afmetingen vastgelegd: Kanaal, levering, marketingaanbieding en datum.<br /> Het  <strong>voorstel van de </strong> Aanbieding wordt dan gebruikt om rapporten te produceren die op voorstellen worden gebaseerd. U kunt meer over kubussen in <a href="../../reporting/using/about-cubes.md">deze sectie</a> leren.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter volledige geaggregeerde berekening</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Deze workflow werkt het <strong>Volledige</strong> aggregaat voor de <strong>Berichtencentrum</strong> kubus bij. Deze wordt standaard elke dag om 3 uur geactiveerd. In dit aggregaat worden de volgende afmetingen vastgelegd: Het type Kanaal, Datum, Status en Gebeurtenis.<br /> Het  <strong>centrum van het Bericht </strong> wordt dan gebruikt om rapporten te produceren die op gebeurtenissen worden gebaseerd. U kunt meer over kubussen in <a href="../../reporting/using/about-cubes.md">deze sectie</a> leren.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

