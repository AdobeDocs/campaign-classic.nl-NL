---
solution: Campaign Classic
product: campaign
title: Lijst met rapporten
description: Lijst met rapporten
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 1%

---


# Lijst met rapporten{#list-of-reports}

## Rapporten over leveringen {#reports-on-deliveries}

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Raadpleeg [deze sectie](../../reporting/using/delivery-reports.md) voor meer informatie over de inhoud van deze rapporten.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label en interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Gebruikersactiviteiten (receivingActivity)<br /> </td> 
   <td> Uitsplitsing van openen, klikken en transacties naar tijdsperiode.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Productiedoorvoer (doorvoer)<br /> </td> 
   <td> Leveringsdoorvoergrafieken, in berichten/uur en Mbits/s.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Fouten en stuitingen (fouten)<br /> </td> 
   <td> Stuiterwaarden en niet-te leveren items per oorzaak en domein.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Trackingindicatoren (deliveryFeedback)<br /> </td> 
   <td> Samenvatting van zeer belangrijke indicatoren voor het volgen van ontvankelijk gedrag.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Trackingindicatoren (mobileAppDeliveryFeedback)<br /> </td> 
   <td> Indicatoren voor het bijhouden van een levering aan een mobiele toepassing.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Browsers (browserStatistics)<br /> </td> 
   <td> Statistieken over browsers die door ontvangers worden gebruikt die in berichten klikten.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Delen naar sociale netwerken (deliveryForward)<br /> </td> 
   <td> Het delen van activiteit en post open statistieken.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Hete kliks (hoturls)<br /> </td> 
   <td> Toont het bericht en de kliktarieven bovenop.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Hypotheseverslag (deliveryHypothesis)<br /> </td> 
   <td> Toont de samenvatting van maatregelen op leveringshypothesen.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveringsstatistieken (statisticsPerDelivery)<br /> </td> 
   <td> Statistieken (verwerkte berichten, geleverde berichten, harde stuitingen, zachte stuitingen, klikken, abonnementen) per e-maildomein.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistieken betreffende de deelactiviteit (forwardActivity)<br /> </td> 
   <td> Analyse van het delen van activiteiten, opent en abonnementen per tijdsperiode.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Tracking statistics (trackingStatistics)<br /> </td> 
   <td> Open, klik en het rapport van de transactietarieven.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Overzicht van levering (deliverySending)<br /> </td> 
   <td> Samenvatting van de leveringsindicatoren: doel, uitsluiting en verzonden berichten.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Overzicht van levering (deliveryStatistics)<br /> </td> 
   <td> Samenvattingstabel voor geselecteerde leveringen: Doelstellingen, uitsluitingen en verzonden berichten.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> Besturingssystemen (osStatistics)<br /> </td> 
   <td> Statistieken over de werkende systemen die door ontvangers worden gebruikt die in een bericht klikte.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Reactiviteitsgraad (deliveryFeedbackSocial)<br /> </td> 
   <td> Afbraak van de reactiviteitssnelheid en reactie.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
  <tr> 
   <td> URL's en klik op doorvoer (topUrlDelivery)<br /> </td> 
   <td> Meest reactieve URLs en bijbehorende klikstromen.<br /> </td> 
   <td> nms:bezorging<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporten over campagnes {#reports-on-campaigns}

Rapporten over campagnes betreffen de gegevens in de **nms:operation** tabel.

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Raadpleeg [deze sectie](../../campaign/using/designing-marketing-campaigns.md) voor meer informatie over de inhoud van deze rapporten.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label en interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Gebruikersactiviteiten (operationRecipientActivity)<br /> </td> 
   <td> De uitsplitsing van opent, klikt en transacties door tijdspanne, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveringsdoorvoer (operationThroughput)<br /> </td> 
   <td> De leveringsproductietrafieken, in post/uur en Mbits/s, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Campagneuitgaven (budgetOperationExpenses)<br /> </td> 
   <td> Toont de punten van de campagnelijn in detail, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Fouten en stormen (operationErrors)<br /> </td> 
   <td> Stuiterwaarden en niet-te leveren items per oorzaak en domein zijn afhankelijk van campagne.<br /> </td> 
  </tr> 
  <tr> 
   <td> Het onderzoeken van kostenlijnen (budgetExplorerOperation)<br /> </td> 
   <td> Beschrijvende analyse van kostenlijnen, hangt van MRM.<br /> af </td> 
  </tr> 
  <tr> 
   <td> Trackingindicatoren (operationFeedback)<br /> </td> 
   <td> Overzicht van belangrijke volgindicatoren: Opent, klikt en Transacties, is afhankelijk van campagne.<br /> </td> 
  </tr> 
  <tr> 
   <td> Delen naar sociale netwerken (operationForward)<br /> </td> 
   <td> Het delen van activiteit en post open statistieken, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Hypotheseverslag (operationHypothesis)<br /> </td> 
   <td> Hiermee geeft u het overzicht weer van hypothesemetingen voor de campagneleveringen, afhankelijk van campagne.<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistieken over de deelactiviteit (forwardActivityOpt)<br /> </td> 
   <td> Analyse van het delen van activiteiten, opent en abonnementen per tijdspanne, hangt van Campagne af.<br /> </td> 
  </tr> 
  <tr> 
   <td> Overzicht van levering (operationStatistics)<br /> </td> 
   <td> Samenvattend overzicht van de campagneleveringen: Doelstellingen, uitsluitingen en verzonden berichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> URL's en klik op doorvoer (operationTopUrlDelivery)<br /> </td> 
   <td> De meeste reactieve URL's en de bijbehorende klikstreams zijn afhankelijk van Campagne.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporten over services {#reports-on-services}

Rapporten over services hebben betrekking op de gegevens in de tabel **nms:service**.

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Raadpleeg de desbetreffende handleidingen voor meer informatie over de inhoud van deze rapporten.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label en interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Verwervingen ventilator (socialAcquisitionsByWebapp)<br /> </td> 
   <td> Welke Webtoepassingen lieten de perspectiefverwervingen toe? Afhankelijk van de invoegtoepassing voor sociale marketing.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uitsplitsing van abonnementen (mobileAppDistribution)<br /> </td> 
   <td> De onderverdeling van actieve abonnementen per mobiele toepassing is afhankelijk van de add-on voor mobiele toepassingskanalen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Abonnement bijhouden (subscriptionsProgress)<br /> </td> 
   <td> Ontwikkeling van de abonnementen op informatiediensten<br /> </td> 
  </tr> 
  <tr> 
   <td> Reactiviteitspercentage (socialReactionRate)<br /> </td> 
   <td> Wat zijn de reactiviteitspercentages voor de meest recente leveringen? Afhankelijk van de invoegtoepassing voor sociale marketing.<br /> </td> 
  </tr> 
  <tr> 
   <td> Reactiviteitssnelheid (mobileAppReactivityRate)<br /> </td> 
   <td> De mate van reactiviteit voor de meest recente leveringen is afhankelijk van de add-on voor mobiele toepassingskanalen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Begrotingsrapporten {#budget-reports}

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Raadpleeg [deze sectie](../../campaign/using/designing-marketing-campaigns.md) voor meer informatie over de inhoud van deze rapporten.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label en interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Kosten in verband met de programma('s) (budgetProgramCost)<br /> </td> 
   <td> Uitsplitsing van de programmakosten.<br /> </td> 
   <td> nms:programma<br /> </td> 
  </tr> 
  <tr> 
   <td> Begrotingsontwikkeling (budgetEvolution)<br /> </td> 
   <td> Ontwikkeling van de begrotingskosten per vastleggingsniveau.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Cumulatieve ontwikkeling van de begroting (budgetCumulativeEvolution)<br /> </td> 
   <td> Ontwikkeling van de gecumuleerde begrotingskosten, uitgesplitst naar komma<br /> begrotingsniveau. </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Het onderzoeken van kostenlijnen (budgetExplorerBudget)<br /> </td> 
   <td> Beschrijvende analyse van kostenlijnen.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Het onderzoeken van kostenlijnen (budgetExplorer)<br /> </td> 
   <td> Beschrijvende analyse van kostenlijnen.<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> Het onderzoeken van kostenlijnen (budgetExplorerPlan)<br /> </td> 
   <td> Beschrijvende analyse van kostenlijnen.<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> Het onderzoeken van kostenlijnen (budgetExplorerProgram)<br /> </td> 
   <td> Beschrijvende analyse van kostenlijnen.<br /> </td> 
   <td> nms:programma<br /> </td> 
  </tr> 
  <tr> 
   <td> Samenvatting van de begroting(en) (begroting)<br /> </td> 
   <td> Opname van de belangrijkste kosten, uitgavencategorieën en budgetten.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporten over simulaties {#reports-on-simulations}

Rapporten over simulaties hebben betrekking op de gegevens in de tabel **nms:simulatie**.

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Raadpleeg de desbetreffende handleidingen voor meer informatie over de inhoud van deze rapporten.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label en interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Detail van simulatieuitsluitingen (dlvSimuLossesDetail)<br /> </td> 
   <td> Gedetailleerde tabel met alle oorzaken van uitsluiting.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uitsplitsing van aanbiedingen naar rang (offerSimulationRanking)<br /> </td> 
   <td> Uitsplitsing van aanbiedingen in de simulatie, op rang.<br /> </td> 
  </tr> 
  <tr> 
   <td> Samenvatting simulatie (dlvSimuLossesSummary)<br /> </td> 
   <td> Overzicht van simulatievolumes en -uitsluitingen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistieken overlappen (dlvSimuOverlapping)<br /> </td> 
   <td> Leveringsdoel overlapt volumes.<br /> </td> 
  </tr> 
  <tr> 
   <td> Overzicht van uitsluitingen als gevolg van de simulatie (dlvSimuLossesSimu)<br /> </td> 
   <td> Uitsluitingstabel ten gevolge van de simulatie.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporten over de toepassingen {#reports-on-web-applications} van het Web

Rapporten over de toepassingen van het Web betreffen de gegevens in **nms:WebApp** lijst.

De ingebouwde rapporten van Adobe Campaign zijn te vinden in de onderstaande tabel.

Raadpleeg [deze sectie](../../web/using/about-web-applications.md) voor meer informatie over de inhoud van deze rapporten.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label en interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Documentatie (surveyDictionary)<br /> </td> 
   <td> Beschrijving van de structuur van de enquête is afhankelijk van de invoegtoepassing Beoordelingsmanager.<br /> </td> 
  </tr> 
  <tr> 
   <td> Main (surveyProperties)<br /> </td> 
   <td> Beoordelingseigenschappen<br /> </td> 
  </tr> 
  <tr> 
   <td> Uitsplitsing van antwoorden (surveyDistribution)<br /> </td> 
   <td> Uitsplitsing van antwoorden op vragen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Overige taakrapporten {#other-ootb-reports}

De volgende rapporten worden ook ingebouwd verstrekt. Raadpleeg voor meer informatie het desbetreffende document over de functionaliteit.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label en interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Analyse van aanbieding (offerAnalysis)<br /> </td> 
   <td> De analyse van het aanbod per datum en kanaal, hangt van toe:voegen-op de Interactie af.<br /> </td> 
   <td> nms:aanbieding<br /> </td> 
  </tr> 
  <tr> 
   <td> Efficiëntie van hermarketing (remarketingEffect)<br /> </td> 
   <td> Meting van de efficiëntie van het opnieuw in de handel brengen<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> Geschiedenis van overnames van sociale vooruitzichten (socialVisitorStatistics)<br /> </td> 
   <td> De geschiedenis van Twitter- en Facebook-perspectiefaankopen is afhankelijk van de sociale marketinginvoegtoepassing.<br /> </td> 
   <td> nms:bezoeker<br /> </td> 
  </tr> 
  <tr> 
   <td> Recente propositie-tracking (recentProposities)<br /> </td> 
   <td> Real-time proposition tracking<br /> </td> 
   <td> nms:propositionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

