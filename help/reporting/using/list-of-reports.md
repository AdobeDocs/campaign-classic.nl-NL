---
product: campaign
title: Lijst met rapporten
description: Lijst met rapporten
badge: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 2%

---

# Lijst met rapporten{#list-of-reports}



## Rapporten over leveringen {#reports-on-deliveries}

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Voor meer op de inhoud van deze rapporten, verwijs naar [ deze sectie ](../../reporting/using/delivery-reports.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong> Etiket en Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong> Schema </strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Gebruikersactiviteiten (receivingActivity) <br /> </td> 
   <td> Uitsplitsing van opent, klikt en transacties door tijdspanne.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> De productie van de levering (productie) <br /> </td> 
   <td> De grafieken van de productie van de levering, in berichten/uur en Mbits/s.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> De mislukkingen en de stuitingen (fouten) <br /> </td> 
   <td> Stuitingen en niet-te leveren posten door oorzaak en domein.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Trackingindicatoren (deliveryFeedback) <br /> </td> 
   <td> Samenvatting van zeer belangrijke indicatoren voor het volgen van ontvankelijk gedrag.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Trackingindicatoren (mobileAppDeliveryFeedback) <br /> </td> 
   <td> Het volgen indicatoren van een levering aan een mobiele toepassing.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Browsers (browserStatistics) <br /> </td> 
   <td> Statistieken over browsers die door ontvangers worden gebruikt die in berichten klikten.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Het delen aan sociale netwerken (deliveryForward) <br /> </td> 
   <td> Het delen van activiteit en post open statistieken.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Hete kliks (hoeken) <br /> </td> 
   <td> Toont het bericht en de overlappende kliktarieven.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Het rapport van de hypothese (deliveryHypothesis) <br /> </td> 
   <td> Toont de samenvatting van maatregelen op leveringshypothesen.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistieken van de levering (statisticsPerDelivery) <br /> </td> 
   <td> Statistieken (verwerkte berichten, geleverde berichten, harde stuitingen, zachte stuiters, kliks, unsubscriptions) per e-maildomein.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Het delen van activiteitenstatistieken (forwardActivity) <br /> </td> 
   <td> Analyse van het delen van activiteiten, opent en abonnementen per tijdspanne.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Het volgen statistieken (trackingStatistics) <br /> </td> 
   <td> Open, klik en het rapport van de transactietarieven.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Overzicht van de levering (deliverySending) <br /> </td> 
   <td> Samenvatting van leveringsindicatoren: doel, uitsluiting en verzonden berichten.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Overzicht van de levering (deliveryStatistics) <br /> </td> 
   <td> Summiere lijst voor geselecteerde leveringen: Doelen, Uitsluitingen en Verzonden Berichten.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> De werkende systemen (osStatistics) <br /> </td> 
   <td> Statistieken over de werkende systemen die door ontvangers worden gebruikt die in een bericht klikte.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Reactivity rate (deliveryFeedbackSocial) <br /> </td> 
   <td> Uitsplitsing naar reactiviteit en reactie van de aflevering.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URLs en klik productie (topUrlDelivery) <br /> </td> 
   <td> Meest reactieve URLs en bijbehorende klikstromen.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Verslagen over campagnes {#reports-on-campaigns}

De rapporten over campagnes betreffen de gegevens in de **nms:operation** lijst.

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Voor meer op de inhoud van deze rapporten, verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html){target=_blank}.

<table> 
 <tbody> 
  <tr> 
   <td> <strong> Etiket en Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Gebruikersactiviteiten (operationRecipientActivity) <br /> </td> 
   <td> De onderverdeling van opent, klikt en transacties door tijdspanne, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> De productie van de levering (operationThroughput) <br /> </td> 
   <td> De grafieken van de productie van de levering, in post/uur en Mbits/s, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Campagneuitgaven (budgetOperationExpenses) <br /> </td> 
   <td> Toont de punten van de campagnelijn in detail, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Mislukkingen en stuitingen (operationErrors) <br /> </td> 
   <td> Stuitingen en niet-te leveren zijn door oorzaak en domein, afhankelijk van Campagne.<br /> </td> 
  </tr> 
  <tr> 
   <td> Het onderzoeken van kostenlijnen (budgetExplorerOperation) <br /> </td> 
   <td> De beschrijvende analyse van kostenlijnen, hangt van MRM af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Trackingindicatoren (operationFeedback) <br /> </td> 
   <td> Overzicht van zeer belangrijke volgende indicatoren: opent, klikt en Transacties, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Het delen aan sociale netwerken (operationForward) <br /> </td> 
   <td> Het delen van activiteit en post open statistieken, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Het rapport van de hypothese (operationHypothesis) <br /> </td> 
   <td> Toont de samenvatting van hypothesemetingen voor de campagneleveringen, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Het delen van activiteitenstatistieken (forwardActivityOpt) <br /> </td> 
   <td> De analyse van het delen van activiteiten, opent en abonnementen per tijdspanne, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Overzicht van de levering (operationStatistics) <br /> </td> 
   <td> Summiere grafiek van de campagneleveringen: Doelen, Uitsluitingen en Verzonden Berichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> URLs en klik productie (operationTopUrlDelivery) <br /> </td> 
   <td> De meeste reactieve URLs en bijbehorende klikstromen, hangt van Campagne af.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporten over diensten {#reports-on-services}

De rapporten over de diensten betreffen de gegevens in de **nms:service** lijst.

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Raadpleeg de desbetreffende handleidingen voor meer informatie over de inhoud van deze rapporten.

<table> 
 <tbody> 
  <tr> 
   <td> <strong> Etiket en Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> De verwervingen van de waaier (socialAcquisitionsByWebapp) <br /> </td> 
   <td> Welke Webtoepassingen lieten de perspectiefverwervingen toe? Afhankelijk van sociale marketing toe:voegen-aan.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uitsplitsing van abonnementen (mobileAppDistribution) <br /> </td> 
   <td> De uitsplitsing van actieve abonnementen per mobiele toepassing is afhankelijk van de add-on voor het kanaal van de mobiele app.<br /> </td> 
  </tr> 
  <tr> 
   <td> Het volgen van het abonnement (subscriptionsProgress) <br /> </td> 
   <td> Evolutie van de abonnementen op informatiediensten <br /> </td> 
  </tr> 
  <tr> 
   <td> Reactivity rate (socialReactionRate) <br /> </td> 
   <td> Wat zijn de reactiviteitspercentages voor de meest recente leveringen? Afhankelijk van sociale marketing toe:voegen-aan.<br /> </td> 
  </tr> 
  <tr> 
   <td> Reactivity rate (mobileAppReactivityRate) <br /> </td> 
   <td> De mate van reactiviteit voor de meest recente leveringen is afhankelijk van de add-on voor het kanaal van de mobiele app.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Begrotingsverslagen {#budget-reports}

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Voor meer op de inhoud van deze rapporten, verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html){target=_blank}.

<table> 
 <tbody> 
  <tr> 
   <td> <strong> Etiket en Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong> Schema </strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Kosten in verband met programma(s) (budgetProgramCost) <br /> </td> 
   <td> Uitsplitsing van programmakosten.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> De evolutie van de begroting (budgetEvolution) <br /> </td> 
   <td> Ontwikkeling van de begrotingskosten per vastleggingsniveau.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Cumulatieve ontwikkeling van de begroting (budgetCumulativeEvolution) <br /> </td> 
   <td> Evolutie van de gecumuleerde begrotingskosten, uitgesplitst naar komma <br /> - niveau. </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Het onderzoeken van kostenlijnen (budgetExplorerBudget) <br /> </td> 
   <td> Beschrijvende analyse van kostenlijnen.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Het onderzoeken van kostenlijnen (budgetExplorer) <br /> </td> 
   <td> Beschrijvende analyse van kostenlijnen.<br /> </td> 
   <td> nms:costLine <br /> </td> 
  </tr> 
  <tr> 
   <td> Het onderzoeken van kostenlijnen (budgetExplorerPlan) <br /> </td> 
   <td> Beschrijvende analyse van kostenlijnen.<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> Het onderzoeken van kostenlijnen (budgetExplorerProgram) <br /> </td> 
   <td> Beschrijvende analyse van kostenlijnen.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Samenvatting van de begroting(en) (begroting) <br /> </td> 
   <td> Momentopname van de belangrijkste kosten, uitgavencategorieën en begrotingen.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporten over simulaties {#reports-on-simulations}

De rapporten over simulaties betreffen de gegevens in de **nms:simulation** lijst.

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Raadpleeg de desbetreffende handleidingen voor meer informatie over de inhoud van deze rapporten.

<table> 
 <tbody> 
  <tr> 
   <td> <strong> Etiket en Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Detail van simulatieuitsluitingen (dlvSimuLossesDetail) <br /> </td> 
   <td> Gedetailleerde lijst van alle oorzaken van uitsluiting.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uitsplitsing van aanbiedingen door rang (offerSimulationRanking) <br /> </td> 
   <td> Uitsplitsing van aanbiedingen in de simulatie, door rang.<br /> </td> 
  </tr> 
  <tr> 
   <td> Samenvatting van de simulatie (dlvSimuLossesSummary) <br /> </td> 
   <td> Samenvatting van simulatievolumes en uitsluitingen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistieken overlappen (dlvSimuOverlapping) <br /> </td> 
   <td> Het doel van de levering overlapt volumes.<br /> </td> 
  </tr> 
  <tr> 
   <td> Samenvatting van uitsluitingen toe te schrijven aan de simulatie (dlvSimuLossesSimu) <br /> </td> 
   <td> Lijst van uitsluitingen toe te schrijven aan de simulatie.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporten over webtoepassingen {#reports-on-web-applications}

De rapporten over de toepassingen van het Web betreffen de gegevens in de **nms:WebApp** lijst.

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Voor meer op de inhoud van deze rapporten, verwijs naar [ deze sectie ](../../web/using/about-web-applications.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong> Etiket en Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Documentatie (surveyDictionary) <br /> </td> 
   <td> De beschrijving van de onderzoeksstructuur, hangt van de toe:voegen-op van de Manager van het Onderzoek af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Hoofd (surveyProperties) <br /> </td> 
   <td> Eigenschappen van enquêtes <br /> </td> 
  </tr> 
  <tr> 
   <td> Uitsplitsing van reacties (surveyDistribution) <br /> </td> 
   <td> Uitsplitsing van antwoorden op vragen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Overige taakrapporten {#other-ootb-reports}

De volgende rapporten worden ook ingebouwd verstrekt. Raadpleeg voor meer informatie het desbetreffende document over de functionaliteit.

<table> 
 <tbody> 
  <tr> 
   <td> <strong> Etiket en Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong> Schema </strong><br /> </td> 
  </tr> 
  <tr> 
   <td> De analyse van het aanbod (offerAnalysis) <br /> </td> 
   <td> De analyse van het aanbod per datum en kanaal, hangt van toe:voegen-aan de Interactie af.<br /> </td> 
   <td> nms:aanbieding<br /> </td> 
  </tr> 
  <tr> 
   <td> Efficiëntie van hermarketing (remarketingEffect) <br /> </td> 
   <td> Meting van de efficiëntie van het opnieuw in de handel brengen <br /> </td> 
   <td> nms:webEvent <br /> </td> 
  </tr> 
  <tr> 
   <td> Geschiedenis van sociale perspectiefverwervingen (socialVisitorStatistics) <br /> </td> 
   <td> De geschiedenis van X (voorheen bekend als Twitter) en de perspectiefverwervingen van Facebook, hangt van de sociale marketing toe:voegen-op.<br /> </td> 
   <td> nms:bezoeker <br /> </td> 
  </tr> 
  <tr> 
   <td> Recente voorstel het volgen (recentProposities) <br /> </td> 
   <td> Real-time proposition tracking <br /> </td> 
   <td> nms:propositionRcp <br /> </td> 
  </tr> 
 </tbody> 
</table>
