---
product: campaign
title: Workflow voor het opschonen van databases
description: Leer hoe verouderde gegevens automatisch worden opgeschoond
feature: Monitoring, Workflows
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '2827'
ht-degree: 0%

---

# Workflow voor het opschonen van databases{#database-cleanup-workflow}



## Inleiding {#introduction}

Met de **[!UICONTROL Database cleanup]** -workflow die toegankelijk is via het knooppunt **[!UICONTROL Administration > Production > Technical workflows]** kunt u verouderde gegevens verwijderen om exponentiële groei van de database te voorkomen. De workflow wordt automatisch geactiveerd zonder tussenkomst van de gebruiker.

![ schoonmaakbeurt ](assets/ncs_cleanup_workflow.png)

## Configuratie {#configuration}

De database wordt op twee niveaus opgeschoond: in de workflowplanner en in de implementatietovenaar.

### Workflowplanner {#the-scheduler}

>[!NOTE]
>
>Voor meer op de planner, verwijs naar [ deze sectie ](../../workflow/using/scheduler.md).

Standaard is de **[!UICONTROL Database cleanup]** -workflow zo geconfigureerd dat deze elke dag om 4.00 uur wordt gestart. De planner laat u het werkschema veranderen die frequentie teweegbrengen. De volgende frequenties zijn beschikbaar:

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![ planner ](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>De workflow van **[!UICONTROL Database cleanup]** kan alleen worden gestart op de datum en tijd die in de planner zijn gedefinieerd als de workflowengine (wfserver).

### implementatiewizard {#deployment-assistant}

Via het menu **[!UICONTROL Tools > Advanced]** , dat u opent via **[!UICONTROL deployment wizard]** , kunt u configureren hoe lang gegevens worden opgeslagen voor. Waarden worden uitgedrukt in dagen. Als deze waarden niet worden gewijzigd, gebruikt de workflow de standaardwaarden.

![](assets/ncs_cleanup_deployment-wizard.png)

De velden van het venster **[!UICONTROL Purge of data]** komen overeen met de volgende opties. Deze worden gebruikt door een aantal van de taken die worden uitgevoerd door de **[!UICONTROL Database cleanup]** -workflow:

* Geconsolideerde het volgen: **NmsCleanup_TrackingStatPurgeDelay** (verwijs naar [ Opruiming van het volgen logboeken ](#cleanup-of-tracking-logs))
* Logboeken van de levering: **NmsCleanup_BroadLogPurgeDelay** (verwijs naar [ Opschoning van leveringslogboeken ](#cleanup-of-delivery-logs))
* Het volgen logboeken: **NmsCleanup_TrackingLogPurgeDelay** (verwijs naar [ Opruiming van het volgen logboeken ](#cleanup-of-tracking-logs))
* Gewiste leveranties: **NmsCleanup_RecycledDeliveryPurgeDelay** (verwijs naar [ Schoonmaak van te schrappen of te recyclen leveringen ](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* De invoer verwerpt: **NmsCleanup_RejectsPurgeDelay** (verwijs naar [ Schoonmaak van verwerpingen die door de invoer ](#cleanup-of-rejects-generated-by-imports-) worden geproduceerd)
* De profielen van de bezoeker: **NmsCleanup_VisitorPurgeDelay** (verwijs naar [ Opschoning van bezoekers ](#cleanup-of-visitors))
* Voorstellen van de aanbieding: **NmsCleanup_PropositionPurgeDelay** (verwijs naar [ Schoonmaak van voorstellen ](#cleanup-of-propositions))

  >[!NOTE]
  >
  >Het **[!UICONTROL Offer propositions]** gebied is slechts beschikbaar wanneer de **Interactie** module geïnstalleerd is.

* Gebeurtenissen: **NmsCleanup_EventPurgeDelay** (verwijs naar [ het Schonen van verlopen gebeurtenissen ](#cleansing-expired-events))
* Gearchiveerde gebeurtenissen: **NmsCleanup_EventHistoPurgeDelay** (verwijs naar [ het Schoonmaken van verlopen gebeurtenissen ](#cleansing-expired-events))

  >[!NOTE]
  >
  >De **[!UICONTROL Events]** en **[!UICONTROL Archived events]** gebieden zijn slechts beschikbaar als het **Centrum van het Bericht** module geïnstalleerd is.

* Het spoor van de controle: **XtkCleanup_AuditTrailPurgeDelay** (verwijs naar [ Schoonmaak van het spoor van de Controle ](#cleanup-of-audit-trail))

Alle taken die door de **[!UICONTROL Database cleanup]** -workflow worden uitgevoerd, worden in de volgende sectie beschreven.

## Taken die worden uitgevoerd door de workflow voor het opschonen van databases {#tasks-carried-out-by-the-database-cleanup-workflow}

Op de datum en de tijd die in de werkschemaplanner wordt bepaald (verwijs naar [ de planner ](#the-scheduler)), begint de werkschemamotor het proces van de gegevensbestandschoonmaak. De schoonmaakbeurt van het Gegevensbestand verbindt met het gegevensbestand en voert de taken in de hieronder getoonde opeenvolging uit.

>[!IMPORTANT]
>
>Als een van deze taken mislukt, worden de volgende niet uitgevoerd.
>
>SQL de vragen met a **LIMIT** attributen worden herhaaldelijk uitgevoerd tot alle informatie wordt verwerkt.


### Lijsten om opschoonbewerking te verwijderen {#lists-to-delete-cleanup}

De eerste taak die door het **[!UICONTROL Database cleanup]** werkschema wordt uitgevoerd schrapt alle groepen met **deleteStatus!= 0** attribuut van **NmsGroup**. De verslagen verbonden aan deze groepen en die in andere lijsten bestaan worden ook geschrapt.

1. Lijsten die moeten worden verwijderd, worden hersteld met de volgende SQL-query:

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Elke lijst bevat verschillende koppelingen naar andere tabellen. Al deze verbindingen worden geschrapt in bulk gebruikend de volgende vraag:

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   waar `$(relatedTable)` een lijst verwant met **NmsGroup** is en `$(l)` is het lijstherkenningsteken.

1. Wanneer de lijst een lijst van het type &quot;Lijst&quot;is, wordt de bijbehorende lijst geschrapt gebruikend de volgende vraag:

   ```sql
   DROP TABLE grp$(l)
   ```

1. Elk **Uitgezochte** type lijst die door de verrichting wordt teruggekregen wordt geschrapt gebruikend de volgende vraag:

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   waarbij `$(l)` de lijst-id is

### Reiniging van te verwijderen of te recyclen leveringen {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Met deze taak worden alle leveringen verwijderd of gerecycleerd.

1. Het **[!UICONTROL Database cleanup]** werkschema selecteert alle leveringen waarvoor het **deleteStatus** gebied de waarde **[!UICONTROL Yes]** of **[!UICONTROL Recycled]** heeft en waarvan schrappingsdatum vroeger is dan de periode die in **[!UICONTROL Deleted deliveries]** wordt bepaald (**NmsCleanup_RecycledDeliveryPurgeDelay**) gebied van de plaatsingstovenaar. Voor meer op dit, verwijs naar [ plaatsingstovenaar ](#deployment-assistant). Deze periode wordt berekend op basis van de huidige serverdatum.
1. Voor elke server voor midsourcing selecteert de taak de lijst met te verwijderen leveringen.
1. De **[!UICONTROL Database cleanup]** -workflow verwijdert leveringslogbestanden, bijlagen, spiegelpagina-informatie en alle andere gerelateerde gegevens.
1. Voordat de levering goed wordt verwijderd, worden de gekoppelde gegevens in de volgende tabellen gewist:

   * In de lijst van de leveringsuitsluiting (**NmsDlvExclusion**), wordt de volgende vraag gebruikt:

     ```sql
     DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
     ```

     waarbij **$(l)** het herkenningsteken van de levering is.

   * In de couponlijst (**NmsCouponValue**), wordt de volgende vraag gebruikt (met massa-schrappingen):

     ```sql
     DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
     ```

     waarbij `$(l)` de id van de levering is.

   * In de lijsten van het leveringslogboek (**NmsBroadlogXxx**), worden de massa-schrappingen uitgevoerd in partijen van 20.000 verslagen.
   * In de lijsten van het aanbiedingsvoorstel (**NmsPropositionXxx**), worden massa-schrappingen uitgevoerd in partijen van 20.000 verslagen.
   * In de volgende logboeklijsten (**NmsTrackinglogXxx**), worden de massa-schrappingen uitgevoerd in partijen van 20.000 verslagen.
   * In de lijst van het leveringsfragment (**NmsDeliveryPart**), worden massa-deletions uitgevoerd in partijen van 500.000 verslagen. Deze lijst bevat verpersoonlijkingsinformatie over de resterende te leveren berichten.
   * In de het fragmentlijst van de spiegelpaginagegevens (**NmsMirrorPageInfo**), worden de massa-schrappingen uitgevoerd in partijen van 20.000 verslagen voor verlopen leveringsdelen en voor gebeëindigde of geannuleerde degenen. Deze lijst bevat verpersoonlijkingsinformatie over alle berichten die voor het produceren van spiegelpagina&#39;s worden gebruikt.
   * In de lijst van het het paginacheonderzoek van de spiegelpagina (**NmsMirrorPageSearch**), worden massa-schrappingen uitgevoerd in partijen van 20.000 verslagen. Deze lijst is een onderzoeksindex die toegang tot verpersoonlijkingsinformatie verleent die in de **wordt opgeslagen NmsMirrorPageInfo** lijst.
   * In de lijst van het partijproceslogboek (**XtkJobLog**), wordt massa-schrappingen uitgevoerd in partijen van 20.000 verslagen. Deze tabel bevat het logboek met te verwijderen leveringen.
   * In de levering URL volgende lijst (**NmsTrackingUrl**), wordt de volgende vraag gebruikt:

     ```sql
     DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
     ```

     waarbij `$(l)` de id van de levering is.

     Deze tabel bevat de URL&#39;s in de te verwijderen items, zodat deze kunnen worden bijgehouden.

1. De levering wordt geschrapt van de leveringslijst (**NmsDelivery**):

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   waarbij `$(l)` de id van de levering is.

#### Leveringen met behulp van mid-sourcing {#deliveries-using-mid-sourcing}

De **[!UICONTROL Database cleanup]** -workflow verwijdert ook leveringen op de server(s) voor midsourcing.

1. Hiervoor controleert de workflow of elke levering inactief is (op basis van de status). Als een levering actief is, wordt deze gestopt voordat deze wordt verwijderd. De controle wordt uitgevoerd door de volgende vraag uit te voeren:

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   waarbij **$(l)** het herkenningsteken van de levering is.

1. Als de waarde van de status **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** of **[!UICONTROL Paused]** (waarden 51, 55, 61, 62, 71, 72, 75) is, wordt de levering gestopt en wordt de gekoppelde informatie opgeschoond.

### Opschonen van verlopen leveringen {#cleanup-of-expired-deliveries}

Met deze taak worden leveringen gestopt waarvan de geldigheidsperiode is verlopen.

1. De workflow van **[!UICONTROL Database cleanup]** maakt een lijst met verlopen leveringen. Deze lijst bevat alle verlopen leveringen met een andere status dan **[!UICONTROL Finished]** en ook de onlangs gestopt leveringen met meer dan 10.000 niet-verwerkte berichten. De volgende query wordt gebruikt:

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   waarbij `delivery mode 1` overeenkomt met de **[!UICONTROL Mass delivery]** mode, `state 51` overeenkomt met de **[!UICONTROL Start pending]** state, `state 85` overeenkomt met de **[!UICONTROL Stopped]** state en het hoogste aantal leveringslogboeken dat op de bezorgserver is bijgewerkt, gelijk is aan 10.000.

1. De workflow bevat vervolgens een lijst met onlangs verlopen leveringen die gebruikmaken van mid-sourcing. Leveringen waarvoor nog geen leveringslogs via de server voor midsourcing zijn hersteld, zijn uitgesloten.

   De volgende query wordt gebruikt:

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. De volgende vraag wordt gebruikt om te ontdekken al dan niet de externe rekening nog actief is, voor het filtreren leveringen door datum:

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. In de lijst met verlopen leveringen, leveringslogboeken met de status **[!UICONTROL Pending]** , schakelen naar **[!UICONTROL Delivery cancelled]** en alle leveringen in deze lijst schakelen naar **[!UICONTROL Finished]** .

   De volgende query&#39;s worden gebruikt:

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   waarbij `$(curdate)` de huidige datum van de databaseserver is, is `$(bl)` de id van het bericht met de leveringslogbestanden, is `$(dl)` de leverings-id, komt `delivery status 6` overeen met de **[!UICONTROL Pending]** status en `delivery status 7` komt overeen met de **[!UICONTROL Delivery cancelled]** status.

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   waarbij `delivery state 95` overeenkomt met **[!UICONTROL Finished]** status, en `$(dl)` de id van de levering is.

1. Alle fragmenten (**deliveryParts**) van verouderde leveringen worden geschrapt en alle verouderde fragmenten van berichtleveringen in uitvoering worden geschrapt. Mass-delete wordt gebruikt voor beide taken.

   De volgende query&#39;s worden gebruikt:

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   waarbij `delivery state 95` overeenkomt met **[!UICONTROL Finished]** status, `delivery state 85` overeenkomt met **[!UICONTROL Stopped]** status en `$(curDate)` de huidige serverdatum is.

### Overbodig verwijderen van spiegelpagina&#39;s {#cleanup-of-mirror-pages}

Met deze taak verwijdert u de webbronnen (spiegel-pagina&#39;s) die door leveringen worden gebruikt.

1. Ten eerste wordt de lijst met te wissen leveringen hersteld met behulp van de volgende query:

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   waarbij `$(curDate)` de huidige serverdatum is.

1. De **NmsMirrorPageInfo** lijst wordt dan ontruimd, indien nodig gebruikend het herkenningsteken van de eerder teruggekregen levering. De massa-schrapping wordt gebruikt om de volgende vragen te produceren:

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   waarbij `$(dl)` de id van de levering is.

1. Een ingang wordt dan toegevoegd aan het leveringslogboek.
1. De geraffineerde leveringen worden vervolgens geïdentificeerd, zodat ze niet later opnieuw hoeven te worden verwerkt. De volgende query wordt uitgevoerd:

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   waarbij `$(strIn)` de lijst met leverings-id&#39;s is.

### Opschonen van werktabellen {#cleanup-of-work-tables}

Deze taak verwijdert uit de database, alle werktabellen die overeenkomen met leveringen met de status **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** of **[!UICONTROL Deleted]** .

1. De lijst van lijsten met namen die met **beginnen wkDlv_** wordt teruggekregen eerst met de volgende vraag (postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. De tabellen die worden gebruikt door werkstromen die worden uitgevoerd, worden dan uitgesloten. Hiervoor wordt de lijst met lopende leveringen hersteld met behulp van de volgende query:

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   waarbij `0` de waarde is die overeenkomt met de **[!UICONTROL Being edited]** leveringsstatus, `85` de **[!UICONTROL Stopped]** status en `100` de **[!UICONTROL Deleted]** status.

1. De lijsten die niet meer worden gebruikt zullen worden geschrapt gebruikend de volgende vraag:

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### Reiniging van door invoer gegenereerde afwijzingen {#cleanup-of-rejects-generated-by-imports-}

Met deze stap kunt u records verwijderen waarvoor niet alle gegevens tijdens het importeren zijn verwerkt.

1. De massa-schrapping wordt uitgevoerd op **XtkReject** lijst met de volgende vraag:

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   waar `$(curDate)` de huidige serverdatum is waarvan wij de periode aftrekken die voor de **wordt bepaald NmsCleanup_RejectsPurgeDelay** optie (verwijs naar [ plaatsingstovenaar ](#deployment-assistant)) en `$(l)` is het maximumaantal verslagen dat massaal moet worden geschrapt.

1. Alle wezen worden dan geschrapt gebruikend de volgende vraag:

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Opschonen van workflowinstanties {#cleanup-of-workflow-instances}

Deze taak zuiveert elke werkschemainstantie gebruikend zijn identiteit (**lWorkflowId**) en geschiedenis (**lHistory**). Het schrapt inactieve lijsten door de werktable schoonmaakbeurttaak opnieuw in werking te stellen. De opschoning verwijdert ook alle zwevende werktabellen (wkf% en wkfhisto%) van verwijderde workflows.

>[!NOTE]
>
>De purgefrequentie van de geschiedenis wordt gespecificeerd voor elk werkschema in de **Geschiedenis op dagen** gebied (standaardwaarde 30 dagen). Dit gebied kan op het **lusje van de Uitvoering** van de werkschemaeigenschappen worden gevonden. Raadpleeg [deze sectie](../../workflow/using/workflow-properties.md#execution) voor meer informatie.

1. De volgende query wordt gebruikt om de lijst met te verwijderen workflows te herstellen:

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Deze vraag produceert de lijst van werkschema&#39;s die zal worden gebruikt om alle verbonden logboeken, gebeëindigde taken en gebeëindigde gebeurtenissen te schrappen, gebruikend de volgende vragen:

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   waarbij `$(lworkflow)` de id van de workflow is en `$(lhistory)` de id van de geschiedenis.

1. Alle ongebruikte tabellen worden verwijderd. Voor dit doel, worden alle lijsten verzameld dank aan a **wkf%** typemasker gebruikend de volgende vraag (postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Vervolgens worden alle tabellen die worden gebruikt door een instantie in de wachtrij, uitgesloten. De lijst met actieve workflows wordt hersteld met behulp van de volgende query:

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Elke werkstroom-id wordt vervolgens hersteld om de naam te vinden van de tabellen die worden gebruikt door werkstromen die worden uitgevoerd. Deze namen zijn uitgesloten van de lijst met eerder herstelde tabellen.
1. De &quot;stijgende vraag&quot;de lijsten van het type van vraagactiviteit zijn uitgesloten gebruikend de volgende vragen:

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   waar `$(strcondition)` de lijst van lijsten is die het **wkfhisto%** masker aanpassen.

1. De overige tabellen worden verwijderd met de volgende query:

   ```sql
   DROP TABLE wkf15487_12;
   ```

### Opschonen van workflowlogins {#cleanup-of-workflow-logins}

Met deze taak verwijdert u workflowaanmeldingen met de volgende query:

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Opruiming van verweesde werktabellen {#cleanup-of-orphan-work-tables}

Met deze taak verwijdert u zwevende werktabellen die aan groepen zijn gekoppeld. De **NmsGroup** lijst slaat de te reinigen groepen (met een type verschillend van 0) op. De prefix van de lijstnamen is **grp**. Om de te reinigen groepen te identificeren, wordt de volgende vraag gebruikt:

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Opschonen van bezoekers {#cleanup-of-visitors}

Met deze taak verwijdert u overbodige records uit de bezoekerstabel door middel van massaverwijdering. De verouderde verslagen zijn die waarvoor de laatste wijziging vroeger is dan de behoudsperiode die in de plaatsingstovenaar wordt bepaald (verwijs naar [ plaatsingstovenaar ](#deployment-assistant)). De volgende query wordt gebruikt:

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

waar `$(tsDate)` de huidige serverdatum is, waarvan wij de periode aftrekken die voor de **wordt bepaald NmsCleanup_VisitorPurgeDelay** optie.

### Opruiming van NPAI {#cleanup-of-npai}

Deze taak laat u verslagen schrappen die geldige adressen van de **NmsAddress** lijst aanpassen. De volgende vraag wordt gebruikt om massa-schrapping uit te voeren:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

waar `status 2` de **[!UICONTROL Valid]** status aanpast, `$(tsDate1)` is de huidige serverdatum, en `$(tsDate2)` past de **NmsCleanup_LastCleanup** optie aan.

### Opschonen van abonnementen {#cleanup-of-subscriptions-}

Deze taak ontslaat alle abonnementen die door de gebruiker van de **worden geschrapt NmsSubscription** lijst, gebruikend massa-schrapping. De volgende query wordt gebruikt:

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Opschonen van trackinglogboeken {#cleanup-of-tracking-logs}

Met deze taak verwijdert u overbodige records uit de logtabellen voor bijhouden en webtracking. De verouderde verslagen zijn die die vroeger dan de behoudsperiode zijn die in de plaatsingstovenaar wordt bepaald (verwijs naar [ plaatsingstovenaar ](#deployment-assistant)).

1. Eerst, wordt de lijst van het volgen logboeklijsten teruggekregen gebruikend de volgende vraag:

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. Massa-schrapping wordt gebruikt om alle lijsten in de lijst van eerder teruggekregen lijsten te zuiveren. De volgende query wordt gebruikt:

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   waar `$(tsDate)` de huidige serverdatum is waarvan wij de periode aftrekken die voor de **wordt bepaald NmsCleanup_TrackingLogPurgeDelay** optie.

1. De tabel met volgstatistieken wordt gewist door middel van massale verwijdering. De volgende query wordt gebruikt:

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   waar `$(tsDate)` de huidige serverdatum is waarvan wij de periode aftrekken die voor de **wordt bepaald NmsCleanup_TrackingStatePurgeDelay** optie.

### Opschonen van leveringslogboeken {#cleanup-of-delivery-logs}

Met deze taak kunt u de leveringslogboeken die in verschillende tabellen zijn opgeslagen, leegmaken.

1. Voor dit doel, wordt de lijst van de schema&#39;s van het leveringslogboek teruggekregen gebruikend de volgende vraag:

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Wanneer het gebruiken van midsourcing, wordt de **NmsBroadLogMid** lijst niet van verwijzingen voorzien in leveringsafbeeldingen. Het **nms:wideLogMid** schema wordt toegevoegd aan de lijst die door de vorige vraag wordt teruggekregen.
1. De **schoonmaakbeurt van het Gegevensbestand** werkschema wint dan verouderde gegevens van eerder teruggekregen lijsten. De volgende query wordt gebruikt:

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   waar `$(tableName)` de naam van elke lijst in de lijst van schema&#39;s is, en `$(option)` is de datum die voor **wordt bepaald NmsCleanup_BroadLogPurgeDelay** optie (verwijs naar [ plaatsingstovenaar ](#deployment-assistant)).

1. Tot slot controleert het werkschema of de **NmsProviderMsgId** lijst bestaat. Als dat het geval is, worden alle verouderde gegevens verwijderd met de volgende query:

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   waar `$(option)` de datum aanpast die voor **wordt bepaald NmsCleanup_BroadLogPurgeDelay** optie (verwijs naar [ plaatsingstovenaar ](#deployment-assistant)).

### Opschonen van de tabel NmsEmailErrorStat {#cleanup-of-the-nmsemailerrorstat-table-}

Deze taak schoonmaakt de **NmsEmailErrorStatus** lijst. Het belangrijkste programma (**colesceErrors**) bepaalt twee data:

* **datum van het Begin**: datum van het volgende proces dat de **NmsLastErrorStateCoalesce** optie of de meest recente datum in de lijst aanpast.
* **einddatum**: huidige serverdatum.

Als de begindatum groter dan of gelijk is aan de einddatum, vindt er geen proces plaats. In dit geval, verschijnt het **colesceUpToDate** bericht.

Als de begindatum vroeger dan de einddatum is, wordt de **lijst NmsEmailErrorState** schoongemaakt.

Het totale aantal fouten in de **NmsEmailErrorState** lijst, tussen de begin en einddata, wordt teruggekregen gebruikend de volgende vraag:

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

waarbij `$end` en `$start` de eerder gedefinieerde begin- en einddatum zijn.

Als het totaal groter is dan 0:

1. De volgende query wordt uitgevoerd om alleen fouten boven een bepaalde drempel (gelijk aan 20) te houden:

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. Het **coalescingErrors** bericht wordt getoond.
1. Er wordt een nieuwe verbinding gemaakt om alle fouten tussen de begin- en einddatum te verwijderen. De volgende query wordt gebruikt:

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. Elke fout wordt bewaard in de **NmsEmailErrorStatus** lijst gebruikend de volgende vraag:

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   waarbij elke variabele overeenkomt met een waarde die door de vorige query is hersteld.

1. De **begin** variabele wordt bijgewerkt met de waarden van het vorige proces om de lijn te beëindigen.

De lus en de taakstop.

Schoonmakingen worden uitgevoerd op **NmsEmailError** en **schoonmaakupNmsMxDomain** lijsten.

### Opschonen van de tabel NmsEmailError {#cleanup-of-the-nmsemailerror-table-}

De volgende query wordt gebruikt:

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Deze vraag schrapt alle lijnen zonder verbonden verslagen in **NmsEmailErrorState** van de **NmsEmailError** lijst.

### Opschonen van de tabel NmsMxDomain {#cleanup-of-the-nmsmxdomain-table-}

De volgende query wordt gebruikt:

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Deze vraag schrapt alle lijnen zonder een verbonden verslag in **NmsEmailErrorState** lijst van de **NmsMxDomain** lijst.

### Opschonen van voorstellen {#cleanup-of-propositions}

Als de **module van de Interactie** wordt geïnstalleerd, wordt deze taak uitgevoerd om de **NmsPropositionXxx** lijsten te zuiveren.

De lijst met voorstellingstabellen wordt teruggewonnen en de massa-schrapping wordt uitgevoerd op elk, gebruikend de volgende vraag:

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

waar `$(option)` de datum is die voor de **wordt bepaald NmsCleanup_PropositionPurgeDelay** optie (verwijs naar [ plaatsingstovenaar ](#deployment-assistant)).

### Opschonen van simulatietabellen {#cleanup-of-simulation-tables}

Deze taak zuivert wezen simulatietabellen (die niet meer aan een aanbiedingssimulatie of een leveringssimulatie verbonden zijn).

1. Om de lijst van simulaties terug te krijgen die schoonmaakbeurt vereisen, wordt de volgende vraag gebruikt:

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. De naam van de te schrappen lijsten wordt samengesteld uit **wkSimu_** prefix die door het herkenningsteken van de simulatie wordt gevolgd (bijvoorbeeld: **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### Reiniging van audittrail {#cleanup-of-audit-trail}

De volgende query wordt gebruikt:

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

waar **$ (tsDate)** de huidige serverdatum is waarvan de periode die voor **wordt bepaald XtkCleanup_AuditTrailPurgeDelay** optie wordt afgetrokken.

### Opschonen van Nmsaddress {#cleanup-of-nmsaddress}

De volgende query wordt gebruikt:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Met deze query worden alle items verwijderd die betrekking hebben op iOS en Android.

### Statistieken bijwerken en optimaliseren van opslag {#statistics-update}

De **optie XtkCleanup_NoStats** staat u toe om het gedrag van de stap van de opslagoptimalisering van het schoonmaakprogramma te controleren.

Als de **optie XtkCleanup_NoStats** niet bestaat of als zijn waarde 0 is, zal dit de opslagoptimalisering op uitgebreide wijze (VACUUM VERBOSE ANALYZE) op PostgreSQL en updatestatistieken op alle andere gegevensbestanden uitvoeren. Om ervoor te zorgen dat dit bevel wordt uitgevoerd, controleer de logboeken PostgreSQL. VACUUM zal lijnen in het formaat uitvoeren: `INFO: vacuuming "public.nmsactivecontact"` en ANALYZE zal lijnen in het formaat uitvoeren: `INFO: analyzing "public.nmsactivecontact"`.

Als de waarde van de optie 1 is, worden statistieken het bijwerken niet uitgevoerd op om het even welk gegevensbestand. De volgende logregel wordt weergegeven in de logbestanden van de workflow: `Option 'XtkCleanup_NoStats' is set to '1'` .

Als de waarde van de optie 2 is, zal dit de opslaganalyse op uitgebreide wijze (ANALYZE VERBOSE) op PostgreSQL uitvoeren en statistieken op alle andere gegevensbestanden bijwerken. Om ervoor te zorgen dat dit bevel wordt uitgevoerd, controleer de logboeken PostgreSQL. ANALYZE zal lijnen in het formaat uitvoeren: `INFO: analyzing "public.nmsactivecontact"`.

### Opschonen van abonnementen (NMAC) {#subscription-cleanup--nmac-}

Met deze taak verwijdert u alle abonnementen die betrekking hebben op verwijderde services of mobiele toepassingen.

Om de lijst van uitzendingsschema&#39;s terug te krijgen, wordt de volgende vraag gebruikt:

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

De taak herstelt dan de namen van de lijsten verbonden aan de **appSubscription** verbinding en schrapt deze lijsten.

Deze schoonmaakwerkschema schrapt ook alle ingangen waar gehandicapt = 1 die niet sinds de tijd die in **wordt geplaatst NmsCleanup_AppSubscriptionRcpPurgeDelay** optie zijn bijgewerkt.

### Sessiegegevens wissen {#cleansing-session-information}

Deze taak schoont informatie van de **sessionInfo** lijst, wordt de volgende vraag gebruikt:

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Verlopen gebeurtenissen wissen {#cleansing-expired-events}

Deze taak schoonmaakt de gebeurtenissen die op de uitvoeringsinstanties en de gebeurtenissen worden ontvangen en worden opgeslagen die op een controleinstantie worden gearchiveerd.

### Reacties op schoonmaken {#cleansing-reactions}

Deze taak schoont de reacties (lijst **NmsRemaMatchRcp**) waarin de hypothesen zelf zijn geschrapt.
