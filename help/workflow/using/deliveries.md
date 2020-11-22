---
solution: Campaign Classic
product: campaign
title: Leveringen
description: Meer informatie over standaardleveringsworkflows
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 6%

---


# Leveringen{#deliveries}

De hieronder beschreven workflows worden standaard geïnstalleerd.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rapportageaggregaten</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> Deze workflow werkt aggregaten bij die worden gebruikt in rapporten. Het wordt teweeggebracht elke dag om 2 uur door gebrek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Facturering</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> Deze workflow stuurt het systeemactiviteitenrapport per e-mail naar de 'factureringsoperator'. Deze wordt standaard geactiveerd op de 25e van elke maand.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aantal actieve factureringsprofielen</span> <br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span> <br /> </td> 
   <td> <p>Deze workflow telt het aantal actieve profielen. Het wordt elke nacht teweeggebracht om 1 uur door gebrek.</p> <p>“<strong>Profile</strong>” means a record of information (e.g.: a record in the nmsRecipient table or an external table containing a cookie ID, Customer ID, mobile identifier or other information relevant to a particular channel) representing an end-customer, prospect, or lead. Facturering heeft alleen betrekking op profielen die "actief" zijn. Een profiel wordt als "actief" beschouwd als het profiel in de afgelopen twaalf maanden via een kanaal is geactiveerd of gecommuniceerd.</p> <p>Er wordt geen rekening gehouden met de kanalen Facebook en Twitter.</p> <p>U kunt een overzicht van het <span class="uicontrol">Aantal actieve profielen</span> van het <span class="uicontrol">Beleid</span> &gt; het Beheer van de <span class="uicontrol">Campagne</span> &gt; het menu van de Metriek <span class="uicontrol">van de</span> Klant hebben.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aliasreiniging</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Deze werkstroom normaliseert opsommingswaarden. Deze wordt standaard elke dag om 3 uur geactiveerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Update for deliverability</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Met deze workflow kunt u een lijst maken met regels voor stuiterende mailkwalificatie en een lijst met domeinen en MX's in het platform. Deze workflow werkt alleen als de HTTPS-poort geopend is. Deze lijsten worden alleen bijgewerkt als de module Leverbaarheid is geïnstalleerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Database opschonen</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Deze workflow is de workflow voor databaseonderhoud: het maakt verschillende berekeningen van de statistieken en de processen, en schrapt verouderde gegevens van het gegevensbestand volgens de bepaalde configuratie in de plaatsingsmedewerker. Het wordt teweeggebracht elke dag om 4am door gebrek.</p> <p>For more information, refer to this <a href="../../production/using/database-cleanup-workflow.md">page</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Opschonen van gepauzeerde workflows</span> <br /> </td> 
   <td> <span class="uicontrol">cleanPausedWorkflows</span> <br /> </td> 
   <td> <p>In deze workflow worden gepauzeerde workflows geanalyseerd waarvoor de ernst is ingesteld op Normaal en worden waarschuwingen en meldingen geactiveerd wanneer deze al te lang zijn gepauzeerd. Na een maand worden gepauzeerde technische workflows onvoorwaardelijk gestopt. Standaard wordt de activering elke maandag om 17.00 uur gestart.</p> <p>Raadpleeg <a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Behandeling van gepauzeerde workflows</a>voor meer informatie.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Melding voorstel</span> <br /> </td> 
   <td> <span class="uicontrol">aanbiedingsbeheer</span> <br /> </td> 
   <td> Deze workflow implementeert goedgekeurde aanbiedingen in de onlineomgeving en in elke categorie in de aanbiedingencatalogus.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Voorvertoning</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> Deze workflow analyseert leveringen die zijn opgeslagen in de voorlopige kalender (maakt voorlopige logbestanden). Het wordt teweeggebracht elke dag bij 1am door gebrek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Tracking</span> <br /> </td> 
   <td> <span class="uicontrol">bijhouden</span> <br /> </td> 
   <td> Deze workflow voert het herstel en de consolidatie van trackinggegevens uit. Het verzekert ook de herberekening van het volgen en leveringsstatistieken, vooral die gebruikt door het archiveren van het Centrum van het Bericht werkschema. Deze wordt standaard één keer per uur geactiveerd. <br /> </td> 
  </tr> 
 </tbody> 
</table>

