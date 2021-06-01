---
product: campaign
title: Workflow voor het opschonen van databases
description: Leer hoe verouderde gegevens automatisch worden opgeschoond
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2910'
ht-degree: 0%

---

# Workflow voor het opschonen van databases{#database-cleanup-workflow}

## Inleiding {#introduction}

Met de **[!UICONTROL Database cleanup]**-workflow die toegankelijk is via het **[!UICONTROL Administration > Production > Technical workflows]**-knooppunt kunt u verouderde gegevens verwijderen om exponentiële groei van de database te voorkomen. De workflow wordt automatisch geactiveerd zonder tussenkomst van de gebruiker.

![](assets/ncs_cleanup_workflow.png)

## Configuratie {#configuration}

De database wordt op twee niveaus opgeschoond: in de werkstroomplanner en in de plaatsingstovenaar.

### Workflowplanner {#the-scheduler}

>[!NOTE]
>
>Voor meer op de planner, verwijs naar [deze sectie](../../workflow/using/scheduler.md).

Standaard is de **[!UICONTROL Database cleanup]**-workflow geconfigureerd om elke dag om 4.00 uur te beginnen. De planner laat u het werkschema veranderen die frequentie teweegbrengen. De volgende frequenties zijn beschikbaar:

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>De workflow **[!UICONTROL Database cleanup]** kan pas worden gestart op de datum en tijd die in de planner zijn gedefinieerd als de workflowengine (wfserver). Als dit niet het geval is, zal het zuiveren van gegevensbestand niet plaatsvinden tot volgende tijd de werkschemamotor wordt begonnen.

### Implementatiewizard {#deployment-wizard}

Met het menu **[!UICONTROL Deployment wizard]**, dat u opent via het menu **[!UICONTROL Tools > Advanced]**, kunt u configureren hoe lang gegevens worden opgeslagen voor. Waarden worden uitgedrukt in dagen. Als deze waarden niet worden gewijzigd, gebruikt de workflow de standaardwaarden.

![](assets/ncs_cleanup_deployment-wizard.png)

De velden van het venster **[!UICONTROL Purge of data]** komen overeen met de volgende opties. Deze worden gebruikt door sommige taken die door het **[!UICONTROL Database cleanup]** werkschema worden uitgevoerd:

* Geconsolideerde reeksspatiëring: **NmsCleanup_TrackingStatPurgeDelay** (zie [Opschonen van trackinglogbestanden](#cleanup-of-tracking-logs))
* Leveringslogboeken: **NmsCleanup_BroadLogPurgeDelay** (zie [Overbodig verwijderen van leveringslogbestanden](#cleanup-of-delivery-logs))
* Logbestanden bijhouden: **NmsCleanup_TrackingLogPurgeDelay** (zie [Opschonen van trackinglogbestanden](#cleanup-of-tracking-logs))
* Verwijderde leveringen: **NmsCleanup_RecycledDeliveryPurgeDelay** (zie [Opschonen van te verwijderen of te recyclen leveringen](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* Import weigert: **NmsCleanup_RejectsPurgeDelay** (zie [Schoonmaken van door invoer gegenereerde afwijzingen](#cleanup-of-rejects-generated-by-imports-))
* Bezoekersprofielen: **NmsCleanup_VisitorPurgeDelay** (zie [Opschonen van bezoekers](#cleanup-of-visitors))
* Voorstellen voorstellen: **NmsCleanup_PropositionPurgeDelay** (zie [Overbodig verwijderen van proposities](#cleanup-of-propositions))

   >[!NOTE]
   >
   >Het veld **[!UICONTROL Offer propositions]** is alleen beschikbaar wanneer de module **Interaction** is geïnstalleerd.

* Gebeurtenissen: **NmsCleanup_EventPurgeDelay** (verwijs naar [Uitverlopen gebeurtenissen verwijderen](#cleansing-expired-events))
* Gearchiveerde gebeurtenissen: **NmsCleanup_EventHistoPurgeDelay** (verwijs naar [Uitverlopen gebeurtenissen verwijderen](#cleansing-expired-events))

   >[!NOTE]
   >
   >De velden **[!UICONTROL Events]** en **[!UICONTROL Archived events]** zijn alleen beschikbaar als de module **Message Center** is geïnstalleerd.

* Audittrail: **XtkCleanup_AuditTrailPurgeDelay** (zie [Overbodig verwijderen van audittrail](#cleanup-of-audit-trail))

Alle taken die door **[!UICONTROL Database cleanup]** werkschema worden uitgevoerd worden beschreven in de volgende sectie.

## Taken die worden uitgevoerd door de workflow voor het opschonen van databases {#tasks-carried-out-by-the-database-cleanup-workflow}

Op de datum en de tijd die in de werkschemaplanner worden bepaald (verwijs naar [De planner](#the-scheduler)), begint de werkschemamotor het gegevensbestand schoonmaakproces. De schoonmaakbeurt van het Gegevensbestand verbindt met het gegevensbestand en voert de taken in de hieronder getoonde opeenvolging uit.

>[!IMPORTANT]
>
>Als een van deze taken mislukt, worden de volgende niet uitgevoerd.\
>SQL de vragen met een **LIMIT** attribuut zullen herhaaldelijk worden uitgevoerd tot alle informatie wordt verwerkt.

>[!NOTE]
>
>De secties hieronder die de taken beschrijven die door het opschoonwerkschema van het Gegevensbestand worden uitgevoerd zijn gereserveerd voor gegevensbestandbeheerders of gebruikers vertrouwd met SQL taal.

### Lijsten om opschoonbewerking {#lists-to-delete-cleanup} te verwijderen

De eerste taak die door **[!UICONTROL Database cleanup]** werkschema wordt uitgevoerd schrapt alle groepen met **deleteStatus!= 0** attribuut van **NmsGroup**. De verslagen verbonden aan deze groepen en die in andere lijsten bestaan worden ook geschrapt.

1. Lijsten die moeten worden verwijderd, worden hersteld met de volgende SQL-query:

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Elke lijst bevat verschillende koppelingen naar andere tabellen. Al deze verbindingen worden geschrapt in bulk gebruikend de volgende vraag:

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   waarbij **$(relatedTable)** een tabel is die betrekking heeft op **NmsGroup** en **$(l)** is de lijst-id.

1. Wanneer de lijst een lijst van het type &quot;Lijst&quot;is, wordt de bijbehorende lijst geschrapt gebruikend de volgende vraag:

   ```
   DROP TABLE grp$(l)
   ```

1. Elke **Select** typelijst die door de verrichting wordt teruggekregen wordt geschrapt gebruikend de volgende vraag:

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   waarbij **$(l)** de lijst-id is

### Opschonen van te verwijderen of te recyclen leveringen {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Met deze taak worden alle leveringen verwijderd of gerecycleerd.

1. Met de **[!UICONTROL Database cleanup]**-workflow worden alle leveringen geselecteerd waarvoor het veld **deleteStatus** de waarde **[!UICONTROL Yes]** of **[!UICONTROL Recycled]** heeft en waarvan de verwijderingsdatum eerder is dan de periode die is gedefinieerd in het veld **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**) van de implementatiewizard. Raadpleeg [Implementatiewizard](#deployment-wizard) voor meer informatie. Deze periode wordt berekend op basis van de huidige serverdatum.
1. Voor elke server voor midsourcing selecteert de taak de lijst met te verwijderen leveringen.
1. Met de **[!UICONTROL Database cleanup]**-workflow worden leveringslogbestanden, bijlagen, spiegelpaginagegevens en alle andere gerelateerde gegevens verwijderd.
1. Voordat de levering goed wordt verwijderd, worden de gekoppelde gegevens in de volgende tabellen gewist:

   * In de lijst van de leveringsuitsluiting (**NmsDlvExclusion**), wordt de volgende vraag gebruikt:

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      waarbij **$(l)** de id van de levering is.

   * In de coupontabel (**NmsCouponValue**) wordt de volgende query gebruikt (met massa-deleties):

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      waarbij **$(l)** de id van de levering is.

   * In de lijsten van het leveringslogboek (**NmsBroadlogXxx**), worden massa-schrappingen uitgevoerd in partijen van 20.000 verslagen.
   * In de lijsten van het aanbiedingsvoorstel (**NmsPropositionXxx**), worden massa-schrappingen uitgevoerd in partijen van 20.000 verslagen.
   * In de volgende logboeklijsten (**NmsTrackinglogXxx**), worden massa-schrappingen uitgevoerd in partijen van 20.000 verslagen.
   * In de leverfragmentlijst (**NmsDeliveryPart**), massa-deletions worden uitgevoerd in partijen van 500.000 verslagen. Deze lijst bevat verpersoonlijkingsinformatie over de resterende te leveren berichten.
   * In de tabel met gegevensfragmenten op de spiegelpagina (**NmsMirrorPageInfo**) worden massaverwijderingen uitgevoerd in batches van 20.000 records voor verlopen leveringsonderdelen en voor voltooide of geannuleerde onderdelen. Deze lijst bevat verpersoonlijkingsinformatie over alle berichten die voor het produceren van spiegelpagina&#39;s worden gebruikt.
   * In de spiegel pagina onderzoekslijst (**NmsMirrorPageSearch**), massa-schrappingen worden uitgevoerd in partijen van 20.000 verslagen. Deze lijst is een onderzoeksindex die toegang tot verpersoonlijkingsinformatie verleent die in **NmsMirrorPageInfo** lijst wordt opgeslagen.
   * In de tabel in het logbestand van het batchproces (**XtkJobLog**) worden massaverwijderingen uitgevoerd in batches van 20.000 records. Deze tabel bevat het logboek met te verwijderen leveringen.
   * In de leverings URL die lijst (**NmsTrackingUrl**) volgen, wordt de volgende vraag gebruikt:

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      waarbij **$(l)** de id van de levering is.

      Deze tabel bevat de URL&#39;s in de te verwijderen items, zodat deze kunnen worden bijgehouden.

1. De levering wordt geschrapt uit de leveringslijst (**NmsDelivery**):

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   waarbij **$(l)** de id van de levering is.

#### Leveringen met behulp van midsourcing {#deliveries-using-mid-sourcing}

De **[!UICONTROL Database cleanup]**-workflow verwijdert ook leveringen op de server(s) voor midsourcing.

1. Hiervoor controleert de workflow of elke levering inactief is (op basis van de status). Als een levering actief is, wordt deze gestopt voordat deze wordt verwijderd. De controle wordt uitgevoerd door de volgende vraag uit te voeren:

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   waarbij **$(l)** de id van de levering is.

1. Als de waarde van de status **[!UICONTROL Start pending]**, **[!UICONTROL In progress]**, **[!UICONTROL Recovery pending]**, **[!UICONTROL Recovery in progress]**, **[!UICONTROL Pause requested]**, **[!UICONTROL Pause in progress]** of **[!UICONTROL Paused]** (waarden 51, 55, 61, 62, 71, 72, 75) is, wordt de levering gestopt en wordt de gekoppelde informatie gewist.

### Opschonen van verlopen leveringen {#cleanup-of-expired-deliveries}

Met deze taak worden leveringen gestopt waarvan de geldigheidsperiode is verlopen.

1. Met de **[!UICONTROL Database cleanup]**-workflow maakt u een lijst met leveringen die zijn verlopen. Deze lijst bevat alle verlopen leveringen met een andere status dan **[!UICONTROL Finished]**, en ook onlangs beëindigde leveringen met meer dan 10.000 niet-verwerkte berichten. De volgende query wordt gebruikt:

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   waarbij **leveringsmodus 1** overeenkomt met de **[!UICONTROL Mass delivery]**-modus, **status 51** komt overeen met de **[!UICONTROL Start pending]**-status, **status 85** komt overeen met de **[!UICONTROL Stopped]**-status en het hoogste aantal leveringslogbestanden dat op de leveringsserver is bijgewerkt, is gelijk aan 10.0000.

1. De workflow bevat vervolgens een lijst met onlangs verlopen leveringen die gebruikmaken van mid-sourcing. Leveringen waarvoor nog geen leveringslogs via de server voor midsourcing zijn hersteld, zijn uitgesloten.

   De volgende query wordt gebruikt:

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. De volgende vraag wordt gebruikt om te ontdekken al dan niet de externe rekening nog actief is, voor het filtreren leveringen door datum:

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. In de lijst met verlopen leveringen, leveringslogboeken met de status **[!UICONTROL Pending]**, schakelt u over naar **[!UICONTROL Delivery cancelled]** en alle leveringen in deze lijst schakelen naar **[!UICONTROL Finished]**.

   De volgende query&#39;s worden gebruikt:

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   waarbij **$(curdate)** de huidige datum van de databaseserver is, **$(bl)** is de id van het bericht van de leveringslogboekregistratie, **$(dl)** is de bezorgingsidentificatie, **leveringsstatus 6** komt overeen met de status **[!UICONTROL Pending]** en **leveringsstatus 7 a10/> komt overeen met de status **[!UICONTROL Delivery cancelled]**.**

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   waarbij **leveringsstatus 95** overeenkomt met de status **[!UICONTROL Finished]** en **$(dl)** de id van de levering is.

1. Alle fragmenten (**deliveryParts**) van verouderde leveringen worden verwijderd en alle verouderde fragmenten van lopende berichtleveringen worden verwijderd. Mass-delete wordt gebruikt voor beide taken.

   De volgende query&#39;s worden gebruikt:

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   waarbij **leveringsstatus 95** overeenkomt met de status **[!UICONTROL Finished]**, **leveringsstatus 85** overeenkomt met de status **[!UICONTROL Stopped]** en **$(curDate)** is de huidige serverdatum.

### Opschonen van spiegelpagina&#39;s {#cleanup-of-mirror-pages}

Met deze taak verwijdert u de webbronnen (spiegel-pagina&#39;s) die door leveringen worden gebruikt.

1. Ten eerste wordt de lijst met te wissen leveringen hersteld met behulp van de volgende query:

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   waarbij **$(curDate)** de huidige serverdatum is.

1. De tabel **NmsMirrorPageInfo** wordt vervolgens gewist, zo nodig met de id van de eerder herstelde levering. De massa-schrapping wordt gebruikt om de volgende vragen te produceren:

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   waarbij **$(dl)** de id van de levering is.

1. Een ingang wordt dan toegevoegd aan het leveringslogboek.
1. De geraffineerde leveringen worden vervolgens geïdentificeerd, zodat ze niet later opnieuw hoeven te worden verwerkt. De volgende query wordt uitgevoerd:

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   waarbij **$(strIn)** de lijst van leveringsherkenningstekens is.

### Opschonen van werktabellen {#cleanup-of-work-tables}

Deze taak verwijdert uit de database, alle werktabellen die overeenkomen met leveringen met de status **[!UICONTROL Being edited]**, **[!UICONTROL Stopped]** of **[!UICONTROL Deleted]**.

1. De lijst van lijsten met namen die met **wkDlv_** beginnen wordt teruggekregen eerst met de volgende vraag (postgresql):

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. De tabellen die worden gebruikt door werkstromen die worden uitgevoerd, worden dan uitgesloten. Hiervoor wordt de lijst met lopende leveringen hersteld met behulp van de volgende query:

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   waarbij 0 de waarde is die overeenkomt met de **[!UICONTROL Being edited]** leveringsstatus, komt 85 overeen met de status **[!UICONTROL Stopped]** en 100 met de status **[!UICONTROL Deleted]**.

1. De lijsten die niet meer worden gebruikt zullen worden geschrapt gebruikend de volgende vraag:

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### Opschonen van door invoer gegenereerde afkappen {#cleanup-of-rejects-generated-by-imports-}

Met deze stap kunt u records verwijderen waarvoor niet alle gegevens tijdens het importeren zijn verwerkt.

1. De massa-schrapping wordt uitgevoerd op **XtkReject** lijst met de volgende vraag:

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   waarbij **$(curDate)** de huidige serverdatum is waarvan we de periode aftrekken die is gedefinieerd voor de optie **NmsCleanup_RejectsPurgeDelay** (zie [Implementatietovenaar](#deployment-wizard)) en **$(l)** is het maximumaantal records dat moet worden ingevoerd geschrapt.

1. Alle wezen worden dan geschrapt gebruikend de volgende vraag:

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Opschonen van workflowinstanties {#cleanup-of-workflow-instances}

Deze taak zuiveert elke werkschemainstantie gebruikend zijn identiteitskaart (**lWorkflowId**) en geschiedenis (**lHistory**). Het schrapt inactieve lijsten door de werktable schoonmaakbeurttaak opnieuw in werking te stellen. De opschoning verwijdert ook alle zwevende werktabellen (wkf% en wkfhisto%) van verwijderde workflows.

>[!NOTE]
>
>De zuiveringsfrequentie van de geschiedenis wordt gespecificeerd voor elke werkschema in **Geschiedenis in dagen** gebied (standaardwaarde 30 dagen). Dit veld vindt u op het tabblad **Uitvoering** van de workfloweigenschappen. Raadpleeg [deze sectie](../../workflow/using/workflow-properties.md#execution) voor meer informatie.

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

   waarbij **$(workflow)** de id van de workflow is en **$(historie)** de id van de historie.

1. Alle ongebruikte tabellen worden verwijderd. Hiertoe worden alle tabellen verzameld via een **wkf%**-typemasker met behulp van de volgende query (postgresql):

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

   waarbij **$(strcondition)** de lijst van lijsten is die **wkfhisto%** masker aanpassen.

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

Met deze taak verwijdert u zwevende werktabellen die aan groepen zijn gekoppeld. In de tabel **NmsGroup** worden de groepen opgeslagen die moeten worden gereinigd (met een ander type dan 0). Het voorvoegsel van de tabelnamen is **grp**. Om de te reinigen groepen te identificeren, wordt de volgende vraag gebruikt:

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Opschonen van bezoekers {#cleanup-of-visitors}

Met deze taak verwijdert u overbodige records uit de bezoekerstabel door middel van massaverwijdering. De verouderde verslagen zijn die waarvoor de laatste wijziging vroeger is dan de behoudsperiode die in de plaatsingstovenaar wordt bepaald (verwijs naar [de tovenaar van de Plaatsing](#deployment-wizard)). De volgende query wordt gebruikt:

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

waarbij **$(tsDate)** de huidige serverdatum is, waarvan we de periode aftrekken die is gedefinieerd voor de optie **NmsCleanup_VisitorPurgeDelay**.

### Opruiming van NPAI {#cleanup-of-npai}

Met deze taak kunt u records verwijderen die overeenkomen met geldige adressen uit de tabel **NmsAddress**. De volgende vraag wordt gebruikt om massa-schrapping uit te voeren:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

waarbij **status 2** overeenkomt met de status **[!UICONTROL Valid]**, **$(tsDate1)** is de huidige serverdatum en **$(tsDate2)** komt overeen met de optie **NmsCleanup_LastCleanup**.

### Opschonen van abonnementen {#cleanup-of-subscriptions-}

Met deze taak worden alle abonnementen verwijderd die de gebruiker heeft verwijderd uit de tabel **NmsSubscription**, waarbij massale verwijdering wordt gebruikt. De volgende query wordt gebruikt:

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Opschonen van logbestanden voor bijhouden {#cleanup-of-tracking-logs}

Met deze taak verwijdert u overbodige records uit de logtabellen voor bijhouden en webtracking. Verouderde records zijn de records die eerder zijn dan de bewaarperiode die is gedefinieerd in de implementatiewizard (zie [Implementatiewizard](#deployment-wizard)).

1. Eerst, wordt de lijst van het volgen logboeklijsten teruggekregen gebruikend de volgende vraag:

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. Massa-schrapping wordt gebruikt om alle lijsten in de lijst van eerder teruggekregen lijsten te zuiveren. De volgende query wordt gebruikt:

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   waarbij **$(tsDate)** de huidige serverdatum is waarvan we de periode aftrekken die is gedefinieerd voor de optie **NmsCleanup_TrackingLogPurgeDelay**.

1. De tabel met volgstatistieken wordt gewist door middel van massale verwijdering. De volgende query wordt gebruikt:

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   waarbij **$(tsDate)** de huidige serverdatum is waarvan we de periode aftrekken die is gedefinieerd voor de optie **NmsCleanup_TrackingStatePurgeDelay**.

### Opschonen van leveringslogboeken {#cleanup-of-delivery-logs}

Met deze taak kunt u de leveringslogboeken die in verschillende tabellen zijn opgeslagen, leegmaken.

1. Hiertoe wordt de lijst van schema&#39;s van het leveringslogboek teruggekregen gebruikend de volgende vraag:

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Bij gebruik van mid-sourcing wordt in de leveringstoewijzingen niet verwezen naar de tabel **NmsBroadLogMid**. Het schema **nms:wideLogMid** wordt toegevoegd aan de lijst die door de vorige vraag wordt teruggekregen.
1. De **Opschonen van het Gegevensbestand** werkschema zuivert dan verouderde gegevens van eerder teruggekregen lijsten. De volgende query wordt gebruikt:

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   waarbij **$(tableName)** de naam is van elke tabel in de lijst met schema&#39;s en **$(option)** de datum is die is gedefinieerd voor de optie **NmsCleanup_BroadLogPurgeDelay** (zie [Implementatietovenaar](#deployment-wizard)).

1. Tot slot controleert het werkschema of **NmsProviderMsgId** lijst bestaat. Als dat het geval is, worden alle verouderde gegevens verwijderd met de volgende query:

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   waarbij **$(option)** overeenkomt met de datum die is gedefinieerd voor de optie **NmsCleanup_BroadLogPurgeDelay** (zie [Implementatietovenaar](#deployment-wizard)).

### Opschonen van de tabel NmsEmailErrorStat {#cleanup-of-the-nmsemailerrorstat-table-}

Deze taak schoonmaakt de **NmsEmailErrorStat** lijst. Het hoofdprogramma (**coalesceErrors**) bepaalt twee data:

* **Begindatum**: datum van het volgende proces dat overeenkomt met de  **** NmsLastErrorStateCoalesceoption of de meest recente datum in de tabel.
* **Einddatum**: huidige serverdatum.

Als de begindatum groter dan of gelijk is aan de einddatum, vindt er geen proces plaats. In dit geval wordt het bericht **coalesceUpToDate** weergegeven.

Als de begindatum eerder is dan de einddatum, wordt de tabel **NmsEmailErrorState** gewist.

Het totale aantal fouten in de tabel **NmsEmailErrorState**, tussen de begin- en einddatum, wordt hersteld met behulp van de volgende query:

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

waarbij **$end** en **$start** de eerder gedefinieerde begin- en einddatums zijn.

Als het totaal groter is dan 0:

1. De volgende query wordt uitgevoerd om alleen fouten boven een bepaalde drempel (gelijk aan 20) te houden:

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. Het **coalescingErrors** bericht wordt getoond.
1. Er wordt een nieuwe verbinding gemaakt om alle fouten tussen de begin- en einddatum te verwijderen. De volgende query wordt gebruikt:

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. Elke fout wordt opgeslagen in de **NmsEmailErrorStatus** lijst gebruikend de volgende vraag:

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   waarbij elke variabele overeenkomt met een waarde die door de vorige query is hersteld.

1. De **start** variabele wordt bijgewerkt met de waarden van het vorige proces om de lijn te beëindigen.

De lus en de taakstop.

Schoonmaakbewerkingen worden uitgevoerd in de tabellen **NmsEmailError** en **CleupNmsMxDomain**.

### Opschonen van de tabel NmsEmailError {#cleanup-of-the-nmsemailerror-table-}

De volgende query wordt gebruikt:

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Deze query verwijdert alle regels zonder gekoppelde records in de **NmsEmailErrorState** uit de tabel **NmsEmailError**.

### Opschonen van de tabel NmsMxDomain {#cleanup-of-the-nmsmxdomain-table-}

De volgende query wordt gebruikt:

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Deze query verwijdert alle regels zonder een gekoppelde record in de tabel **NmsEmailErrorState** uit de tabel **NmsMxDomain**.

### Opschonen van voorstellen {#cleanup-of-propositions}

Als de **Interaction** module geïnstalleerd is, wordt deze taak uitgevoerd om de **NmsPropositionXxx** lijsten te zuiveren.

De lijst met voorstellingstabellen wordt teruggewonnen en de massa-schrapping wordt uitgevoerd op elk, gebruikend de volgende vraag:

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

waarbij **$(option)** de datum is die is gedefinieerd voor de optie **NmsCleanup_PropositionPurgeDelay** (zie [Implementatiewizard](#deployment-wizard)).

### Opruimen van simulatietabellen {#cleanup-of-simulation-tables}

Deze taak zuivert wezen simulatietabellen (die niet meer aan een aanbiedingssimulatie of een leveringssimulatie verbonden zijn).

1. Om de lijst van simulaties terug te krijgen die schoonmaakbeurt vereisen, wordt de volgende vraag gebruikt:

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. De naam van de te schrappen lijsten wordt samengesteld uit **wkSimu_** prefix die door het herkenningsteken van de simulatie wordt gevolgd (bijvoorbeeld: **wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### Opschonen van audittrail {#cleanup-of-audit-trail}

De volgende query wordt gebruikt:

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

waarbij **$(tsDate)** de huidige serverdatum is vanaf welke de periode die is gedefinieerd voor de optie **XtkCleanup_AuditTrailPurgeDelay** is afgebroken.

### Opschonen van Nmsaddress {#cleanup-of-nmsaddress}

De volgende query wordt gebruikt:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Met deze query worden alle items verwijderd die betrekking hebben op iOS en Android.

### Statistieken bijwerken en optimaliseren van opslag {#statistics-update}

Met de optie **XtkCleanup_NoStats** kunt u het gedrag bepalen van de stap voor opslagoptimalisatie van de opschoningsworkflow.

Als de optie **XtkCleanup_NoStats** niet bestaat of als zijn waarde 0 is, zal dit de opslagoptimalisering op uitgebreide wijze (VACUUM VERBOSE ANALYZE) op PostgreSQL uitvoeren en statistieken op alle andere gegevensbestanden bijwerken. Om ervoor te zorgen dat dit bevel wordt uitgevoerd, controleer de logboeken PostgreSQL. VACUUM zal lijnen in het formaat uitvoeren: `INFO: vacuuming "public.nmsactivecontact"` en ANALYZE zullen lijnen in het formaat uitvoeren: `INFO: analyzing "public.nmsactivecontact"`.

Als de waarde van de optie 1 is, worden statistieken het bijwerken niet uitgevoerd op om het even welk gegevensbestand. De volgende loglijn zal in de werkschemalogboeken verschijnen: `Option 'XtkCleanup_NoStats' is set to '1'`.

Als de waarde van de optie 2 is, zal dit de opslaganalyse op uitgebreide wijze (ANALYZE VERBOSE) op PostgreSQL uitvoeren en statistieken op alle andere gegevensbestanden bijwerken. Om ervoor te zorgen dat dit bevel wordt uitgevoerd, controleer de logboeken PostgreSQL. ANALYZE geeft de regels in de volgende notatie: `INFO: analyzing "public.nmsactivecontact"`.

### Opschonen van abonnementen (NMAC) {#subscription-cleanup--nmac-}

Met deze taak verwijdert u alle abonnementen die betrekking hebben op verwijderde services of mobiele toepassingen.

Om de lijst van breedbandschema&#39;s terug te krijgen, wordt de volgende vraag gebruikt:

```
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

De taak herstelt dan de namen van de lijsten verbonden aan **appSubscription** verbinding en schrapt deze lijsten.

Deze opschoningsworkflow verwijdert ook alle items waarvoor de optie = 1 is uitgeschakeld en die niet zijn bijgewerkt sinds de tijd die is ingesteld in de optie **NmsCleanup_AppSubscriptionRcpPurgeDelay**.

### Sessiegegevens {#cleansing-session-information} wissen

Deze taak schoont informatie van de **sessionInfo** lijst, wordt de volgende vraag gebruikt:

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Bezig met opschonen van verlopen gebeurtenissen {#cleansing-expired-events}

Deze taak schoonmaakt de gebeurtenissen die op de uitvoeringsinstanties en de gebeurtenissen worden ontvangen en worden opgeslagen die op een controleinstantie worden gearchiveerd.

### Reacties reinigen {#cleansing-reactions}

Met deze taak worden de reacties (tabel **NmsRemaMatchRcp**) gewist waarin de hypothesen zelf zijn verwijderd.
