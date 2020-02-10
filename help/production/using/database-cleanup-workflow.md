---
title: Workflow voor opschonen van databases
seo-title: Workflow voor opschonen van databases
description: Workflow voor opschonen van databases
seo-description: null
page-status-flag: never-activated
uuid: a7478641-cdf6-4bd4-9dd7-0c84416c9de6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 6b188d78-abb4-4f03-80b9-051ce960f43c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5813af76e3cad16d9094a19509dcb855e36c01f

---


# Workflow voor opschonen van databases{#database-cleanup-workflow}

## Inleiding {#introduction}

Met de **[!UICONTROL Database cleanup]** workflow die via het **[!UICONTROL Administration > Production > Technical workflows]** knooppunt toegankelijk is, kunt u verouderde gegevens verwijderen om exponentiële groei van de database te voorkomen. De workflow wordt automatisch geactiveerd zonder tussenkomst van de gebruiker.

![](assets/ncs_cleanup_workflow.png)

## Configuratie {#configuration}

De database wordt op twee niveaus opgeschoond: in de werkstroomplanner en in de plaatsingstovenaar.

### De planner {#the-scheduler}

>[!NOTE]
>
>Voor meer op de planner, verwijs naar [deze sectie](../../workflow/using/scheduler.md).

Standaard wordt de **[!UICONTROL Database cleanup]** workflow zo geconfigureerd dat deze elke dag om 4.00 uur wordt gestart. De planner laat u het werkschema veranderen die frequentie teweegbrengen. De volgende frequenties zijn beschikbaar:

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!CAUTION]
>
>Opdat het **[!UICONTROL Database cleanup]** werkschema bij de datum en de tijd te beginnen die in de planner wordt bepaald, moet de werkschemamotor (wfserver) zijn begonnen. Als dit niet het geval is, zal het zuiveren van gegevensbestand niet plaatsvinden tot volgende tijd de werkschemamotor wordt begonnen.

### Implementatiewizard {#deployment-wizard}

Met **[!UICONTROL Deployment wizard]** , dat via het **[!UICONTROL Tools > Advanced]** menu wordt geopend, kunt u configureren hoe lang gegevens worden opgeslagen. Waarden worden uitgedrukt in dagen. Als deze waarden niet worden gewijzigd, gebruikt de workflow de standaardwaarden.

![](assets/ncs_cleanup_deployment-wizard.png)

De velden van het **[!UICONTROL Purge of data]** venster komen overeen met de volgende opties. Deze worden gebruikt door een aantal van de taken die door de **[!UICONTROL Database cleanup]** workflow worden uitgevoerd:

* Geconsolideerde reeksspatiëring: **NmsCleanup_TrackingStatPurgeDelay** (verwijs naar [Overbodig bijhouden van logbestanden](#cleanup-of-tracking-logs))
* Leveringslogboeken: **NmsCleanup_BroadLogPurgeDelay** (zie [Overbodig verwijderen van leveringslogboeken](#cleanup-of-delivery-logs))
* Logbestanden bijhouden: **NmsCleanup_TrackingLogPurgeDelay** (verwijs naar [Overbodig bijhouden van logbestanden](#cleanup-of-tracking-logs))
* Verwijderde leveringen: **NmsCleanup_RecycledDeliveryPurgeDelay** (verwijs naar [Opschonen van te verwijderen of te recyclen](#cleanup-of-deliveries-to-be-deleted-or-recycled)leveringen)
* Import weigert: **NmsCleanup_RejectsPurgeDelay** (verwijs naar [Overbodig verwijderen van door invoer](#cleanup-of-rejects-generated-by-imports-)gegenereerde afwijzingen)
* Bezoekersprofielen: **NmsCleanup_VisitorPurgeDelay** (zie [Overbodig verwijderen van bezoekers](#cleanup-of-visitors))
* Voorstellen voorstellen: **NmsCleanup_PropositionPurgeDelay** (zie [Overbodig verwijderen van voorstellen](#cleanup-of-propositions))

   >[!NOTE]
   >
   >Het **[!UICONTROL Offer propositions]** veld is alleen beschikbaar wanneer de module **Interactie** is geïnstalleerd.

* Gebeurtenissen: **NmsCleanup_EventPurgeDelay** (verwijs naar [het opschonen van verlopen gebeurtenissen](#cleansing-expired-events))
* Gearchiveerde gebeurtenissen: **NmsCleanup_EventHistoPurgeDelay** (verwijs naar [het opschonen van verlopen gebeurtenissen](#cleansing-expired-events))

   >[!NOTE]
   >
   >De **[!UICONTROL Events]** velden en **[!UICONTROL Archived events]** velden zijn alleen beschikbaar als de module **Berichtcentrum** is geïnstalleerd.

* Audittrail: **XtkCleanup_AuditTrailPurgeDelay** (verwijs naar [Overbodig verwijderen van audittrail](#cleanup-of-audit-trail))

Alle taken die door de **[!UICONTROL Database cleanup]** workflow worden uitgevoerd, worden in de volgende sectie beschreven.

## Taken die worden uitgevoerd door de workflow voor het opschonen van databases {#tasks-carried-out-by-the-database-cleanup-workflow}

Op de datum en de tijd die in de werkschemaplanner worden bepaald (verwijs naar [de planner](#the-scheduler)), begint de werkschemamotor het gegevensbestand schoonmaakproces. De schoonmaakbeurt van het Gegevensbestand verbindt met het gegevensbestand en voert de taken in de hieronder getoonde opeenvolging uit.

>[!CAUTION]
>
>Als een van deze taken mislukt, worden de volgende niet uitgevoerd.\
>SQL-query&#39;s met een **LIMIT** -kenmerk worden herhaaldelijk uitgevoerd totdat alle informatie wordt verwerkt.

>[!NOTE]
>
>De secties hieronder die de taken beschrijven die door het opschoonwerkschema van het Gegevensbestand worden uitgevoerd zijn gereserveerd voor gegevensbestandbeheerders of gebruikers vertrouwd met SQL taal.

### Lijsten om opschoonbewerking te verwijderen {#lists-to-delete-cleanup}

De eerste taak die door het **[!UICONTROL Database cleanup]** werkschema wordt uitgevoerd schrapt alle groepen met **deleteStatus!= 0** attribuut van **NmsGroup**. De verslagen verbonden aan deze groepen en die in andere lijsten bestaan worden ook geschrapt.

1. Lijsten die moeten worden verwijderd, worden hersteld met de volgende SQL-query:

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Elke lijst bevat verschillende koppelingen naar andere tabellen. Al deze verbindingen worden geschrapt in bulk gebruikend de volgende vraag:

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   waarbij **$(relatedTable)** een tabel is die betrekking heeft op **NmsGroup** en **$(l)** de lijst-id is.

1. Wanneer de lijst een lijst van het type &quot;Lijst&quot;is, wordt de bijbehorende lijst geschrapt gebruikend de volgende vraag:

   ```
   DROP TABLE grp$(l)
   ```

1. Elke lijst van het type **Uitgezocht** die door de verrichting wordt teruggekregen wordt geschrapt gebruikend de volgende vraag:

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   waarbij **$(l)** de lijst-id is

### Reiniging van te verwijderen of te recyclen leveringen {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Met deze taak worden alle leveringen verwijderd of gerecycleerd.

1. De **[!UICONTROL Database cleanup]** werkstroom selecteert alle leveringen waarvoor het **deleteStatus** gebied de waarde **[!UICONTROL Yes]** of **[!UICONTROL Recycled]** heeft en waarvan schrappingsdatum vroeger is dan de periode die in het **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**) gebied van de plaatsingstovenaar wordt bepaald. Raadpleeg de wizard [Implementatie voor meer informatie](#deployment-wizard). Deze periode wordt berekend op basis van de huidige serverdatum.
1. Voor elke server voor midsourcing selecteert de taak de lijst met te verwijderen leveringen.
1. De **[!UICONTROL Database cleanup]** werkstroom verwijdert leveringslogboeken, bijlagen, spiegelpaginagegevens en alle andere gerelateerde gegevens.
1. Voordat de levering goed wordt verwijderd, worden de gekoppelde gegevens in de volgende tabellen gewist:

   * In de lijst van de leveringsuitsluiting (**NmsDlvExclusion**), wordt de volgende vraag gebruikt:

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      waarbij **$(l)** de identificatiecode van de levering is.

   * In de coupontabel (**NmsCouponValue**) wordt de volgende query gebruikt (met massa-deleties):

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      waarbij **$(l)** de identificatiecode van de levering is.

   * In de lijsten van het leveringslogboek (**NmsBroadlogXxx**), massa-schrappingen worden uitgevoerd in partijen van 10.000 verslagen.
   * In de lijsten van het aanbiedingsvoorstel (**NmsPropositionXxx**), worden massa-schrappingen uitgevoerd in partijen van 10.000 verslagen.
   * In de het volgen logboeklijsten (**NmsTrackinglogXxx**), massa-schrappingen worden uitgevoerd in partijen van 5.000 verslagen.
   * In de leverfragmenttabel (**NmsDeliveryPart**) worden massa-deletions uitgevoerd in batches van 5.000 records. Deze lijst bevat verpersoonlijkingsinformatie over de resterende te leveren berichten.
   * In de tabel met gegevensfragmenten op de spiegelpagina (**NmsMirrorPageInfo**) worden massaverwijderingen uitgevoerd in batches van 5.000 records. Deze lijst bevat verpersoonlijkingsinformatie over alle berichten die voor het produceren van spiegelpagina&#39;s worden gebruikt.
   * In de zoektabel met spiegelpagina&#39;s (**NmsMirrorPageSearch**) worden massaverwijderingen uitgevoerd in batches van 5.000 records. Deze lijst is een onderzoeksindex die toegang tot verpersoonlijkingsinformatie verleent die in de **lijst NmsMirrorPageInfo** wordt opgeslagen.
   * In de logtabel van het batchproces (**XtkJobLog**) worden massaverwijderingen uitgevoerd in batches van 5.000 records. Deze tabel bevat het logboek met te verwijderen leveringen.
   * In de URL-tabel voor levering (**NmsTrackingUrl**) wordt de volgende query gebruikt:

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      waarbij **$(l)** de identificatiecode van de levering is.

      Deze tabel bevat de URL&#39;s in de te verwijderen items, zodat deze kunnen worden bijgehouden.

1. De levering wordt geschrapt van de leveringslijst (**NmsDelivery**):

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   waarbij **$(l)** de identificatiecode van de levering is.

#### Leveringen met behulp van mid-sourcing {#deliveries-using-mid-sourcing}

De **[!UICONTROL Database cleanup]** workflow verwijdert ook leveringen op de server(s) voor midsourcing.

1. Hiervoor controleert de workflow of elke levering inactief is (op basis van de status). Als een levering actief is, wordt deze gestopt voordat deze wordt verwijderd. De controle wordt uitgevoerd door de volgende vraag uit te voeren:

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   waarbij **$(l)** de identificatiecode van de levering is.

1. Als de waarde van de status **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** of **[!UICONTROL Paused]** (waarden 51, 55, 61, 62, 71, 72, 75) is, wordt de levering gestopt en wordt de bijbehorende informatie opgeschoond.

### Opschonen van verlopen leveringen {#cleanup-of-expired-deliveries}

Met deze taak worden leveringen gestopt waarvan de geldigheidsperiode is verlopen.

1. De **[!UICONTROL Database cleanup]** workflow maakt een lijst met verlopen leveringen. Deze lijst bevat alle verlopen leveringen met een andere status dan **[!UICONTROL Finished]** , en ook de onlangs gestopt leveringen met meer dan 10.000 niet-verwerkte berichten. De volgende query wordt gebruikt:

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   waarbij **leveringswijze 1** de **[!UICONTROL Mass delivery]** wijze aanpast, **staat 51** de **[!UICONTROL Start pending]** staat aanpast, **staat 85** de **[!UICONTROL Stopped]** staat aanpast, en het hoogste aantal leveringslogboeken massa-bijgewerkt op de leveringsserver evenaart 10.000.

1. De workflow bevat vervolgens een lijst met onlangs verlopen leveringen die gebruikmaken van mid-sourcing. Leveringen waarvoor nog geen leveringslogs via de server voor midsourcing zijn hersteld, zijn uitgesloten.

   De volgende query wordt gebruikt:

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. De volgende vraag wordt gebruikt om te ontdekken al dan niet de externe rekening nog actief is, voor het filtreren leveringen door datum:

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. In de lijst van verlopen leveringen, leveringslogboeken waarvan status is **[!UICONTROL Pending]** , schakelaar aan **[!UICONTROL Delivery cancelled]** , en alle leveringen in deze lijst schakelen naar **[!UICONTROL Finished]** .

   De volgende query&#39;s worden gebruikt:

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   waarbij **$(curdate)** de huidige datum van de databaseserver is, is **$(bl)** de id van het bericht met leveringslogbestanden, **$(dl)** de leverings-id, komt de **leveringsstatus 6** overeen met de **[!UICONTROL Pending]** status en **** **[!UICONTROL Delivery cancelled]** leveringsstatus 7 met de status van de levering.

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   waarbij **leveringsstatus 95** overeenkomt met de **[!UICONTROL Finished]** status, en **$(dl)** de id van de levering is.

1. Alle fragmenten (**deliveryParts**) van verouderde leveringen worden verwijderd en alle verouderde fragmenten van lopende meldingsleveringen worden verwijderd. Mass-delete wordt gebruikt voor beide taken.

   De volgende query&#39;s worden gebruikt:

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   waarbij **leveringsstatus 95** overeenkomt met de **[!UICONTROL Finished]** status, **leveringsstatus 85** overeenkomt met de **[!UICONTROL Stopped]** status en **$(curDate)** de huidige serverdatum is.

### Overbodig verwijderen van spiegelpagina&#39;s {#cleanup-of-mirror-pages}

Met deze taak verwijdert u de webbronnen (spiegel-pagina&#39;s) die door leveringen worden gebruikt.

1. Ten eerste wordt de lijst met te wissen leveringen hersteld met behulp van de volgende query:

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   waarbij **$(curDate)** de huidige serverdatum is.

1. De **tabel NmsMirrorPageInfo** wordt vervolgens gewist, zo nodig met de id van de eerder herstelde levering. De massa-schrapping wordt gebruikt om de volgende vragen te produceren:

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   waarbij **$(dl)** de identificatiecode van de levering is.

1. Een ingang wordt dan toegevoegd aan het leveringslogboek.
1. De geraffineerde leveringen worden vervolgens geïdentificeerd, zodat ze niet later opnieuw hoeven te worden verwerkt. De volgende query wordt uitgevoerd:

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   waarbij **$(strIn)** de lijst met leverings-id&#39;s is.

### Opschonen van werktabellen {#cleanup-of-work-tables}

Deze taak schrapt uit het gegevensbestand, alle werklijsten die leveringen aanpassen de waarvan status is, **[!UICONTROL Being edited]** of **[!UICONTROL Stopped]** **[!UICONTROL Deleted]** .

1. De lijst van lijsten met namen die met **wkDlv_** beginnen wordt teruggekregen eerst met de volgende vraag (postgresql):

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. De tabellen die worden gebruikt door werkstromen die worden uitgevoerd, worden dan uitgesloten. Hiervoor wordt de lijst met lopende leveringen hersteld met behulp van de volgende query:

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   waarbij 0 de waarde is die overeenkomt met de **[!UICONTROL Being edited]** leveringsstatus, komen 85 overeen met de **[!UICONTROL Stopped]** status en 100 met de **[!UICONTROL Deleted]** status.

1. De lijsten die niet meer worden gebruikt zullen worden geschrapt gebruikend de volgende vraag:

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### Reiniging van door invoer gegenereerde afwijzingen {#cleanup-of-rejects-generated-by-imports-}

Met deze stap kunt u records verwijderen waarvoor niet alle gegevens tijdens het importeren zijn verwerkt.

1. De massa-schrapping wordt uitgevoerd op de **lijst XtkReject** met de volgende vraag:

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   waarbij **$(curDate)** de huidige serverdatum is waarvan wij de periode aftrekken die voor de optie **NmsCleanup_RejectsPurgeDelay** wordt bepaald (verwijs naar de tovenaar [van de](#deployment-wizard)Plaatsing) en **$(l)** is het maximumaantal te massa schrappen verslagen.

1. Alle wezen worden dan geschrapt gebruikend de volgende vraag:

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Opschonen van workflowinstanties {#cleanup-of-workflow-instances}

Deze taak leegt elke werkschemainstantie gebruikend zijn identiteitskaart (**lWorkflowId**) en geschiedenis (**lHistory**). Het schrapt inactieve lijsten door de werktable schoonmaakbeurttaak opnieuw in werking te stellen.

>[!NOTE]
>
>De zuiveringsfrequentie van de historie wordt voor elke workflow in het veld **Geschiedenis opgegeven in dagen** (standaardwaarde 30 dagen). Dit veld vindt u op het tabblad **Uitvoering** van de workfloweigenschappen. Zie [deze sectie](../../workflow/using/workflow-properties.md#execution)voor meer informatie.

1. De volgende query wordt gebruikt om de lijst met te verwijderen workflows te herstellen:

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Deze vraag produceert de lijst van werkschema&#39;s die zal worden gebruikt om alle verbonden logboeken, gebeëindigde taken en gebeëindigde gebeurtenissen te schrappen, gebruikend de volgende vragen:

   ```
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   waarbij **$(workflow)** de id van de workflow is en **$(geschiedenis)** de id van de geschiedenis.

1. Alle ongebruikte tabellen worden verwijderd. Hiertoe worden alle tabellen verzameld via een **wkf%** -typemasker met behulp van de volgende query (postgresql):

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Vervolgens worden alle tabellen die worden gebruikt door een instantie van een werkstroom die in behandeling is, uitgesloten. De lijst met actieve workflows wordt hersteld met behulp van de volgende query:

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Elke werkstroom-id wordt vervolgens hersteld om de naam te vinden van de tabellen die worden gebruikt door werkstromen die worden uitgevoerd. Deze namen zijn uitgesloten van de lijst met eerder herstelde tabellen.
1. De &quot;stijgende vraag&quot;de lijsten van het type van vraagactiviteit zijn uitgesloten gebruikend de volgende vragen:

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   waarbij **$(strcondition)** de lijst van lijsten is die het **wkfhisto%** masker aanpassen.

1. De overige tabellen worden verwijderd met de volgende query:

   ```
   DROP TABLE wkf15487_12;
   ```

### Opschonen van workflowlogins {#cleanup-of-workflow-logins}

Met deze taak verwijdert u workflowaanmeldingen met de volgende query:

```
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Opruiming van verweesde werktabellen {#cleanup-of-orphan-work-tables}

Met deze taak verwijdert u zwevende werktabellen die aan groepen zijn gekoppeld. In de **tabel NmsGroup** worden de groepen opgeslagen die moeten worden gereinigd (met een ander type dan 0). Het voorvoegsel van de tabelnamen is **grp**. Om de te reinigen groepen te identificeren, wordt de volgende vraag gebruikt:

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Opschonen van bezoekers {#cleanup-of-visitors}

Met deze taak verwijdert u overbodige records uit de bezoekerstabel door middel van massaverwijdering. De verouderde verslagen zijn die waarvoor de laatste wijziging vroeger is dan de behoudsperiode die in de plaatsingstovenaar wordt bepaald (verwijs naar de tovenaar [van de](#deployment-wizard)Plaatsing). De volgende query wordt gebruikt:

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < $(tsDate) LIMIT 5000)
```

waarbij **$(tsDate)** de huidige serverdatum is, waarvan we de periode aftrekken die is gedefinieerd voor de optie **NmsCleanup_VisitorPurgeDelay** .

### Opruiming van NPAI {#cleanup-of-npai}

Met deze taak kunt u records verwijderen die overeenkomen met geldige adressen uit de tabel **NmsAddress** . De volgende vraag wordt gebruikt om massa-schrapping uit te voeren:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

waarbij **status 2** overeenkomt met de **[!UICONTROL Valid]** status, is **$(tsDate1)** de huidige serverdatum en **$(tsDate2)** overeenkomt met de optie **NmsCleanup_LastCleanup** .

### Opschonen van abonnementen {#cleanup-of-subscriptions-}

Met deze taak worden alle abonnementen verwijderd die door de gebruiker zijn verwijderd uit de tabel **NmsSubscription** , waarbij massale verwijdering wordt gebruikt. De volgende query wordt gebruikt:

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Opschonen van trackinglogboeken {#cleanup-of-tracking-logs}

Met deze taak verwijdert u overbodige records uit de logtabellen voor bijhouden en webtracking. De verouderde verslagen zijn die die vroeger zijn dan de behoudsperiode die in de plaatsingstovenaar wordt bepaald (verwijs naar de tovenaar [van de](#deployment-wizard)Plaatsing).

1. Eerst, wordt de lijst van het volgen logboeklijsten teruggekregen gebruikend de volgende vraag:

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. Massa-schrapping wordt gebruikt om alle lijsten in de lijst van eerder teruggekregen lijsten te zuiveren. De volgende query wordt gebruikt:

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   waarbij **$(tsDate)** de huidige serverdatum is waarvan we de periode aftrekken die is gedefinieerd voor de optie **NmsCleanup_TrackingLogPurgeDelay** .

1. De tabel met volgstatistieken wordt gewist door middel van massale verwijdering. De volgende query wordt gebruikt:

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   waarbij **$(tsDate)** de huidige serverdatum is waarvan we de periode aftrekken die is gedefinieerd voor de optie **NmsCleanup_TrackingStatePurgeDelay** .

### Opschonen van leveringslogboeken {#cleanup-of-delivery-logs}

Met deze taak kunt u de leveringslogboeken die in verschillende tabellen zijn opgeslagen, leegmaken.

1. Hiertoe wordt de lijst van schema&#39;s van het leveringslogboek teruggekregen gebruikend de volgende vraag:

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Wanneer u medio-sourcing gebruikt, wordt in de **leveringstoewijzingen niet verwezen naar de tabel NmsBroadLogMid** . Het schema **nms:wideLogMid** wordt toegevoegd aan de lijst die door de vorige vraag wordt teruggekregen.
1. De workflow voor het opschonen van **databases** zuivert vervolgens verouderde gegevens uit eerder herstelde tabellen. De volgende query wordt gebruikt:

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   waarbij **$(tableName)** de naam van elke lijst in de lijst van schema&#39;s is, en **$ (optie)** is de datum die voor de **optie NmsCleanup_BroadLogPurgeDelay** wordt bepaald (verwijs naar de tovenaar [van de](#deployment-wizard)Plaatsing).

1. Tot slot controleert het werkschema of de **lijst NmsProviderMsgId** bestaat. Als dat het geval is, worden alle verouderde gegevens verwijderd met de volgende query:

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   waarbij **$(option)** overeenkomt met de datum die is gedefinieerd voor de optie **NmsCleanup_BroadLogPurgeDelay** (zie de wizard [](#deployment-wizard)Implementatie).

### Opschonen van de tabel NmsEmailErrorStat {#cleanup-of-the-nmsemailerrorstat-table-}

Hierdoor wordt de tabel **NmsEmailErrorStat** gewist. Het hoofdprogramma (**coalesceErrors**) definieert twee datums:

* **Begindatum**: datum van het volgende proces dat overeenkomt met de optie **NmsLastErrorStateCoalesce** of de meest recente datum in de tabel.
* **Einddatum**: huidige serverdatum.

Als de begindatum groter dan of gelijk is aan de einddatum, vindt er geen proces plaats. In dit geval wordt het **clickUpToDate** -bericht weergegeven.

Als de begindatum eerder is dan de einddatum, wordt de **tabel NmsEmailErrorState** gewist.

Het totale aantal fouten in de tabel **NmsEmailErrorState** tussen de begin- en einddatum wordt hersteld met de volgende query:

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

waarbij **$end** en **$start** de eerder gedefinieerde begin- en einddatums zijn.

Als het totaal groter is dan 0:

1. De volgende query wordt uitgevoerd om alleen fouten boven een bepaalde drempel (gelijk aan 20) te houden:

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. Het bericht **coalescingErrors** wordt weergegeven.
1. Er wordt een nieuwe verbinding gemaakt om alle fouten tussen de begin- en einddatum te verwijderen. De volgende query wordt gebruikt:

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. Elke fout wordt opgeslagen in de **tabel NmsEmailErrorState** met de volgende query:

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   waarbij elke variabele overeenkomt met een waarde die door de vorige query is hersteld.

1. De **beginvariabele** wordt bijgewerkt met de waarden van het vorige proces om de lus te beëindigen.

De lus en de taakstop.

Schoonmakingen worden uitgevoerd op de **tabellen NmsEmailError** en **CleanupNmsMxDomain** .

### Opschonen van de tabel NmsEmailError {#cleanup-of-the-nmsemailerror-table-}

De volgende query wordt gebruikt:

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Met deze query worden alle regels zonder gekoppelde records in de **NmsEmailErrorState** verwijderd uit de **tabel NmsEmailError** .

### Opschonen van de tabel NmsMxDomain {#cleanup-of-the-nmsmxdomain-table-}

De volgende query wordt gebruikt:

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Met deze query worden alle regels zonder een gekoppelde record uit de tabel **NmsEmailErrorStatus** verwijderd uit de tabel **NmsMxDomain** .

### Opschonen van voorstellen {#cleanup-of-propositions}

Als de module **Interactie** is geïnstalleerd, wordt deze taak uitgevoerd om de **tabellen NmsPropositionXxx** leeg te maken.

De lijst met voorstellingstabellen wordt teruggewonnen en de massa-schrapping wordt uitgevoerd op elk, gebruikend de volgende vraag:

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

waarbij **$(option)** de datum is die is gedefinieerd voor de optie **NmsCleanup_PropositionPurgeDelay** (zie de wizard [](#deployment-wizard)Implementatie).

### Opschonen van simulatietabellen {#cleanup-of-simulation-tables}

Deze taak zuivert wezen simulatietabellen (die niet meer aan een aanbiedingssimulatie of een leveringssimulatie verbonden zijn).

1. Om de lijst van simulaties terug te krijgen die schoonmaakbeurt vereisen, wordt de volgende vraag gebruikt:

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. De naam van de te schrappen lijsten wordt samengesteld uit **wkSimu_** prefix die door het herkenningsteken van de simulatie wordt gevolgd (bijvoorbeeld: **wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### Statistieken bijwerken en optimaliseren van opslag {#statistics-update}

Met de optie **XtkCleanup_NoStats** kunt u het gedrag van de stap voor opslagoptimalisatie van de opschoonworkflow bepalen.

Als de optie **XtkCleanup_NoStats** niet bestaat of als zijn waarde 0 is, zal dit de opslagoptimalisering in uitgebreide wijze (VACUUM VERBOSE ANALYZE) op PostgreSQL uitvoeren en statistieken op alle andere gegevensbestanden bijwerken. Controleer de PostSQL-logboeken om ervoor te zorgen dat deze opdracht wordt uitgevoerd. VACUUM zal lijnen in het formaat uitvoeren: `INFO: vacuuming "public.nmsactivecontact"` en ANALYZE zullen lijnen in het formaat uitvoeren: `INFO: analyzing "public.nmsactivecontact"`.

Als de waarde van de optie 1 is, worden statistieken het bijwerken niet uitgevoerd op om het even welk gegevensbestand. De volgende loglijn zal in de werkschemalogboeken verschijnen: `Option 'XtkCleanup_NoStats' is set to '1'`.

Als de waarde van de optie 2 is, zal dit de opslaganalyse op uitgebreide wijze (ANALYZE VERBOSE) op PostgreSQL uitvoeren en statistieken op alle andere gegevensbestanden bijwerken. Controleer de PostSQL-logboeken om ervoor te zorgen dat deze opdracht wordt uitgevoerd. ANALYZE geeft de regels in de volgende notatie: `INFO: analyzing "public.nmsactivecontact"`.

### Opschonen van abonnementen (NMAC) {#subscription-cleanup--nmac-}

Met deze taak verwijdert u alle abonnementen die betrekking hebben op verwijderde services of mobiele toepassingen.

1. Om de lijst van breedbandschema&#39;s terug te krijgen, wordt de volgende vraag gebruikt:

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
   ```

1. De taak herstelt dan de namen van de lijsten verbonden aan de **appSubscription** verbinding en schrapt deze lijsten.

### Sessiegegevens wissen {#cleansing-session-information}

Deze taak schoont informatie van de **sessionInfo** lijst, wordt de volgende vraag gebruikt:

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Verlopen gebeurtenissen wissen {#cleansing-expired-events}

Deze taak schoonmaakt de gebeurtenissen die op de uitvoeringsinstanties en de gebeurtenissen worden ontvangen en worden opgeslagen die op een controleinstantie worden gearchiveerd.

### Reacties {#cleansing-reactions}

Deze taak maakt een einde aan de reacties (tabel **NmsRemaMatchRcp**) waarin de hypothesen zelf zijn verwijderd.

### Reiniging van audittrail {#cleanup-of-audit-trail}

De volgende query wordt gebruikt:

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

waarbij **$(tsDate)** de huidige serverdatum is vanaf welke de periode die voor de optie **XtkCleanup_AuditTrailPurgeDelay** is gedefinieerd, wordt afgebroken.
