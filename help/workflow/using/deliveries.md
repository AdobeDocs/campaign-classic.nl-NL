---
product: campaign
title: Leveringen
description: Meer informatie over standaardleveringsworkflows
hide: true
hidefromtoc: true
feature: Workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 4%

---


# Leveringen{#deliveries}



De hieronder gedetailleerde werkschema&#39;s worden geïnstalleerd met de **Geleveringen** module door gebrek.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong> Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rapportageaggregaten</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> Deze workflow werkt aggregaten bij die worden gebruikt in rapporten. Het wordt teweeggebracht elke dag bij 2am door gebrek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Facturering</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> Deze workflow stuurt het systeemactiviteitenrapport per e-mail naar de 'factureringsoperator'. Het wordt teweeggebracht 25th van elke maand door gebrek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Alias het zuiveren </span> <br /> </td> 
   <td> <span class="uicontrol"> aliasCleansing </span> <br /> </td> 
   <td> Deze werkstroom normaliseert opsommingswaarden. Het wordt teweeggebracht elke dag bij 3am door gebrek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> verfrissen zich voor leverability </span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Met deze workflow kunt u een lijst maken met regels voor stuiterende mailkwalificatie en een lijst met domeinen en MX's in het platform. Deze workflow werkt alleen als de HTTPS-poort geopend is. Deze lijsten worden niet bijgewerkt tenzij de module van de Leverbaarheid wordt geïnstalleerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Database opschonen</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Dit werkschema is het werkschema van het gegevensbestandonderhoud: het maakt verschillende berekeningen van de statistieken en de processen, en schrapt verouderde gegevens uit het gegevensbestand volgens de bepaalde configuratie in de plaatsingstovenaar. Het wordt teweeggebracht elke dag om 4.00 uur door gebrek.</p> <p>Voor meer informatie, verwijs naar deze <a href="../../production/using/database-cleanup-workflow.md"> pagina </a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Gepauzeerde werkschema's schoonmaken </span> <br /> </td> 
   <td> <span class="uicontrol"> cleanPausedWorkflows </span> <br /> </td> 
   <td> <p>In deze workflow worden gepauzeerde workflows geanalyseerd waarvoor de ernst is ingesteld op Normaal en worden waarschuwingen en meldingen geactiveerd wanneer deze al te lang zijn gepauzeerd. Na een maand worden gepauzeerde technische workflows onvoorwaardelijk gestopt. Standaard wordt de activering elke maandag om 17.00 uur gestart.</p> <p>Voor meer informatie, verwijs naar <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank"> Behandeling van gepauzeerde werkschema's </a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> het bericht van de Aanbieding </span> <br /> </td> 
   <td> <span class="uicontrol"> aanbiedingMgt </span> <br /> </td> 
   <td> Deze werkschema stelt goedgekeurde aanbiedingen op het online milieu, evenals elke categorie in de aanbiedingscatalogus op.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Prognose</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> Deze workflow analyseert leveringen die zijn opgeslagen in de voorlopige kalender (maakt voorlopige logbestanden). Het wordt teweeggebracht elke dag bij 1am door gebrek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> het Volgen </span> <br /> </td> 
   <td> <span class="uicontrol"> het volgen </span> <br /> </td> 
   <td> Deze workflow voert het herstel en de consolidatie van trackinggegevens uit. Het verzekert ook de herberekening van het volgen en leveringsstatistieken, vooral die gebruikt door het archiveren van het Centrum van het Bericht werkschema. Deze wordt standaard één keer per uur geactiveerd. <br /> </td> 
  </tr> 
 </tbody> 
</table>

