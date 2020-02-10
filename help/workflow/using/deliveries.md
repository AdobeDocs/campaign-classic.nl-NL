---
title: Leveringen
seo-title: Leveringen
description: Leveringen
seo-description: null
page-status-flag: never-activated
uuid: d323eb4d-937b-4b37-8400-942336f0a1b4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 37612f62-68c0-4f73-a9a1-6d017aab862f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

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
   <td> <span class="uicontrol">Rapportageaggregaten</span><br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span><br /> </td> 
   <td> Deze workflow werkt aggregaten bij die worden gebruikt in rapporten. Het wordt teweeggebracht elke dag om 2 uur door gebrek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Facturering</span><br /> </td> 
   <td> <span class="uicontrol">facturering</span><br /> </td> 
   <td> Deze workflow stuurt het systeemactiviteitenrapport per e-mail naar de 'factureringsoperator'. Deze wordt standaard geactiveerd op de 25e van elke maand.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aantal actieve factureringsprofielen</span><br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span><br /> </td> 
   <td> <p>Deze workflow telt het aantal actieve profielen. Het wordt elke nacht teweeggebracht om 1 uur door gebrek.</p> <p>"<strong>Profiel</strong>": een informatiedossier (bv.: een record in de nmsRecipient-tabel of een externe tabel met een cookie-id, de klant-id, de mobiele id of andere informatie die relevant is voor een bepaald kanaal) die een eindklant, perspectief of lead vertegenwoordigt. Facturering heeft alleen betrekking op profielen die "actief" zijn. Een profiel wordt als "actief" beschouwd als het profiel in de afgelopen twaalf maanden via een kanaal is geactiveerd of gecommuniceerd.</p> <p>Er wordt geen rekening gehouden met de kanalen Facebook en Twitter.</p> <p>U kunt een overzicht van het <span class="uicontrol">Aantal actieve profielen</span> van het <span class="uicontrol">Beleid</span> &gt; het Beheer van de <span class="uicontrol">Campagne</span> &gt; het menu van de Metriek <span class="uicontrol">van de</span> Klant hebben.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aliasreiniging</span><br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span><br /> </td> 
   <td> Deze werkstroom normaliseert opsommingswaarden. Deze wordt standaard elke dag om 3 uur geactiveerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Update voor leverbaarheid</span><br /> </td> 
   <td> <span class="uicontrol">leverabilityUpdate</span><br /> </td> 
   <td> Met deze workflow kunt u een lijst maken met regels voor stuiterende mailkwalificatie en een lijst met domeinen en MX's in het platform. Deze workflow werkt alleen als de HTTPS-poort geopend is. Deze lijsten worden alleen bijgewerkt als de module Leverbaarheid is geïnstalleerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Database opschonen</span><br /> </td> 
   <td> <span class="uicontrol">opruimen</span><br /> </td> 
   <td> <p>Deze workflow is de workflow voor databaseonderhoud: het maakt verschillende berekeningen van de statistieken en de processen, en schrapt verouderde gegevens van het gegevensbestand volgens de bepaalde configuratie in de plaatsingsmedewerker. Het wordt teweeggebracht elke dag om 4am door gebrek.</p> <p>Raadpleeg deze <a href="../../production/using/database-cleanup-workflow.md">pagina</a>voor meer informatie.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Opschonen van</span> gepauzeerde workflows <br /> </td> 
   <td> <span class="uicontrol">cleanPausedWorkflows</span><br /> </td> 
   <td> <p>In deze workflow worden gepauzeerde workflows geanalyseerd waarvoor de ernst is ingesteld op Normaal en worden waarschuwingen en meldingen geactiveerd wanneer deze al te lang zijn gepauzeerd. Na een maand worden gepauzeerde technische workflows onvoorwaardelijk gestopt. Standaard wordt de activering elke maandag om 17.00 uur gestart.</p> <p>Raadpleeg <a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Behandeling van gepauzeerde workflows</a>voor meer informatie.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Melding</span> voorstel <br /> </td> 
   <td> <span class="uicontrol">aanbiedingsbeheer</span><br /> </td> 
   <td> Deze workflow implementeert goedgekeurde aanbiedingen in de onlineomgeving en in elke categorie in de aanbiedingencatalogus.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Voorvertoning</span><br /> </td> 
   <td> <span class="uicontrol">voorspelling</span><br /> </td> 
   <td> Deze workflow analyseert leveringen die zijn opgeslagen in de voorlopige kalender (maakt voorlopige logbestanden). Het wordt teweeggebracht elke dag bij 1am door gebrek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Tekstspatiëring</span><br /> </td> 
   <td> <span class="uicontrol">bijhouden</span><br /> </td> 
   <td> Deze workflow voert het herstel en de consolidatie van trackinggegevens uit. Het verzekert ook de herberekening van het volgen en leveringsstatistieken, vooral die gebruikt door het archiveren van het Centrum van het Bericht werkschema. Deze wordt standaard één keer per uur geactiveerd. <br /> </td> 
  </tr> 
 </tbody> 
</table>

