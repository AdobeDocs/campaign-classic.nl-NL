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
   <td> Deze workflow werkt aggregaten bij die worden gebruikt in rapporten. Het wordt teweeggebracht elke dag om 2am door gebrek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Facturering</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> Deze workflow stuurt het systeemactiviteitenrapport per e-mail naar de 'factureringsoperator'. Deze wordt standaard op de 25e van elke maand geactiveerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aantal actieve factureringsprofielen</span> <br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span> <br /> </td> 
   <td> <p>Deze workflow telt het aantal actieve profielen. Het wordt elke nacht teweeggebracht om 1 uur door gebrek.</p> <p>"<strong>Profiel</strong>" betekent een record met informatie (bijvoorbeeld: een record in de nmsRecipient-tabel of een externe tabel met een cookie-id, de klant-id, de mobiele id of andere informatie die relevant is voor een bepaald kanaal) die een eindklant, perspectief of lead vertegenwoordigt. Facturering heeft alleen betrekking op profielen die "actief" zijn. Een profiel wordt als "actief" beschouwd als het profiel in de afgelopen twaalf maanden via een kanaal is geactiveerd of gecommuniceerd.</p> <p>Er wordt geen rekening gehouden met de kanalen Facebook en Twitter.</p> <p>U kunt een overzicht van <span class="uicontrol">Aantal actieve profielen</span> van <span class="uicontrol">Beheer</span> &gt; <span class="uicontrol">Campagnebeheer</span> &gt; <span class="uicontrol">Metriek van de Klant</span> menu hebben.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aliasreiniging</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Deze werkstroom normaliseert opsommingswaarden. Het wordt teweeggebracht elke dag om 3am door gebrek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Update for deliverability</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Met deze workflow kunt u een lijst maken met regels voor stuiterende mailkwalificatie en een lijst met domeinen en MX's in het platform. Deze workflow werkt alleen als de HTTPS-poort geopend is. Deze lijsten worden niet bijgewerkt tenzij de module van de Leverbaarheid wordt geïnstalleerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Database opschonen</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Deze workflow is de workflow voor databaseonderhoud: het maakt verschillende berekeningen van de statistieken en de processen, en schrapt verouderde gegevens van het gegevensbestand volgens de bepaalde configuratie in de plaatsingsmedewerker. Het wordt teweeggebracht elke dag om 4am door gebrek.</p> <p>Raadpleeg deze <a href="../../production/using/database-cleanup-workflow.md">pagina</a> voor meer informatie.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Opschonen van gepauzeerde workflows</span> <br /> </td> 
   <td> <span class="uicontrol">cleanPausedWorkflows</span> <br /> </td> 
   <td> <p>In deze workflow worden gepauzeerde workflows geanalyseerd waarvoor de ernst is ingesteld op Normaal en worden waarschuwingen en meldingen geactiveerd wanneer deze al te lang zijn gepauzeerd. Na een maand worden gepauzeerde technische workflows onvoorwaardelijk gestopt. Standaard wordt de activering elke maandag om 17.00 uur gestart.</p> <p>Raadpleeg <a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Handling van gepauzeerde workflows</a> voor meer informatie.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Melding voorstel</span> <br /> </td> 
   <td> <span class="uicontrol">aanbiedingsbeheer</span> <br /> </td> 
   <td> Deze workflow implementeert goedgekeurde aanbiedingen in de online omgeving, en in elke categorie in de aanbiedingencatalogus.<br /> </td> 
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

