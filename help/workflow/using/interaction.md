---
product: campaign
title: Interaction
description: Interactie
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 6%

---


# Interactie{#interaction}

![](../../assets/common.svg)

De hieronder beschreven workflows worden geïnstalleerd met de **Aanbiedingsengine (interactie)** standaard invoegtoepassing.

Raadpleeg de volgende secties voor meer informatie, afhankelijk van uw campagneversie:

![](assets/do-not-localize/v7.jpeg)[  Documentatie voor Campaign v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[  Documentatie voor Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


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
   <td> Deze workflow werkt de <strong>Volledig</strong> aggregaat voor de <strong>Voorstel</strong> kubus. Het wordt teweeggebracht elke dag om 6 uur door gebrek. In dit aggregaat worden de volgende afmetingen vastgelegd: Kanaal, levering, marketingaanbieding en datum.<br /> De <strong>Voorstel</strong> kube wordt dan gebruikt om rapporten te produceren die op aanbiedingen worden gebaseerd. Meer informatie over kubussen vindt u in <a href="../../reporting/using/about-cubes.md">deze sectie</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter volledige geaggregeerde berekening</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Deze workflow werkt de <strong>Volledig</strong> aggregaat voor de <strong>Berichtencentrum</strong> kubus. Deze wordt standaard elke dag om 3 uur geactiveerd. In dit aggregaat worden de volgende afmetingen vastgelegd: Het type Kanaal, Datum, Status en Gebeurtenis.<br /> De <strong>Berichtencentrum</strong> kubus wordt dan gebruikt om rapporten te produceren die op gebeurtenissen worden gebaseerd. Meer informatie over kubussen vindt u in <a href="../../reporting/using/about-cubes.md">deze sectie</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

