---
title: Een externe database openen
seo-title: Een externe database openen
description: Een externe database openen
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 4%

---


# Aanvullende opties {#additional-options}

<!--

## HTTP relay to a remote instance {#http-relay-to-a-remote-instance}

You can access external databases configured in remote instances using the HTTP protocol.

>[!NOTE]
>
>Not all SQL data types are supported by this feature. Blob data types are not supported at all. It is possible that other data types may not work depending on the targeted database (Timestamp on Microsoft SQL Server, for example). Please contact Adobe support for more information.

This simplifies transferring and synchronizing data between two instances. It also enables you to sidestep any tunneling between an instance and a remote database as well as the installation of the client layers to access this database. The destination instance can be a hosted instance.

>[!CAUTION]
>
>This option is only for facilitating data replication flows (ETL).   
>
>For example, it allows a cloud-hosted instance to have direct access to the data in an "on-premise" hosted database. However, it is not intended to allow targeting to be carried on an "on-premise" hosted database directly from the cloud.

To do this, you must configure the external accounts of the two instances so that the local instance can communicate with the remote instance using the HTTP protocol:

* Local instance: select the new **[!UICONTROL HTTP relay to a remote database]** connection type.

  In case of bulk load data transfer, also specify the buffer size. Select the compression option if you want to reduce the size of the transferred data.

  The **[!UICONTROL Data source]** must be defined with the following syntax: "nms:extAccount : `<internal_name_of_the_external_account>`"

  ![](assets/fda_over_http_1.png)

  >[!NOTE]
  >
  >We recommend that you use an HTTPS connection.

* Remote instance: in the FDA external account of the database accessed via the HTTP relay, check the Target of an **[!UICONTROL 'HTTP relay to a remote database' account option]**.

  ![](assets/fda_over_http_2.png)

The following example shows the new possible operating mode:

![](assets/schema_fda_over_http_2.png)

>[!CAUTION]
>
>The default database of the remote instance must be accessed via an external account as well.

This operating method avoids that the cleanup workflow of each instance deletes the work tables of the databases that use the instance as relay.

Thus, in the previous example, the cleanup workflow of the remote instance will not perform any action on the red FDA database as it is used by the local instance.

-->

## Direct tijdelijke schema&#39;s maken {#directly-creating-temporary-schemas}

Als u meerdere toegangsmogelijkheden tot een externe FDA-database wilt beheren, kunt u met een nieuwe optie rechtstreeks een werkschema maken wanneer u een externe account configureert.

>[!NOTE]
>
>Deze optie werkt alleen met PostgreSQL.

![](assets/fda_work_table.png)

## E-mailpersonalisatie optimaliseren met externe gegevens {#optimizing-email-personalization-with-external-data}

Vanaf build 8740 **[!UICONTROL Prepare the personalization data with a workflow]** is de optie nu beschikbaar op het **[!UICONTROL Analysis]** tabblad van de leveringseigenschappen.

Tijdens de leveringsanalyse, leidt deze optie automatisch tot en voert een werkschema uit dat alle gegevens met betrekking tot het doel in een tijdelijke lijst, met inbegrip van gegevens van lijsten verbonden in FDA opslaat.

Door deze optie in te schakelen, kunt u een aanzienlijke prestatieverbetering bereiken voor het uitvoeren van personalisatie.

## Data uit een externe database gebruiken in een workflow {#using-data-from-an-external-database-in-a-workflow}

Bij verschillende Adobe Campaign-workflowactiviteiten kunt u de gegevens gebruiken die in een externe database zijn opgeslagen.

### Filteren op externe gegevens {#filtering-on-external-data}

De vraagactiviteit staat u toe om externe gegevens toe te voegen en het in de bepaalde filterconfiguraties te gebruiken.

For more on this, refer to the [Query](../../workflow/using/targeting-data.md#selecting-data) section.

### Subsets maken {#creating-sub-sets}

Met de splitsingsactiviteit kunt u subsets maken. U kunt externe gegevens gebruiken om de filtercriteria te bepalen aan gebruik.

For more on this, refer to the [Split](../../workflow/using/split.md) section.

### Externe database laden {#loading-external-database}

U kunt de externe gegevens gebruiken in het laden van gegevens (RDBMS). Deze activiteit wordt voorgesteld in de het laden [van](../../workflow/using/data-loading--rdbms-.md) Gegevens sectie.

### Informatie en koppelingen toevoegen {#adding-information-and-links}

Met de verrijkingsactiviteit kunt u aanvullende gegevens toevoegen aan de werktabel van de workflow en koppelingen naar een externe tabel. Om deze reden, kan het de gegevens van een extern gegevensbestand exploiteren. Deze activiteit wordt vermeld in het gedeelte [Verrijking](../../workflow/using/enrichment.md) .
<!--

## Cloud Messaging - FDA synchronization {#cloud-messaging---fda-synchronization}

When the Cloud Messaging server and the Marketing server have not been synchronized for a long period, the volume of missing broadlogs on the Marketing server can be significant. To optimize broadlog synchronization via the FDA, the **NmsMidSourcing_LogsPeriodHour** option has been added. This allows a maximum period (expressed in hours) to be specified as to limit the number of broadlogs recovered every time the synchronization workflow is executed.

The option is to be added in the console, in the **[!UICONTROL Administration > Options]** node.

>[!CAUTION]
>
>This option must **only** be used for synchronizing a significant volume of broadlogs via the FDA.

>[!NOTE]
>
>The option is only taken into account if a last recovery date exists (**NmsMidSourcing_LastBroadLog_&#42;** option).

## Message Center - Read access on the XtkFolder table {#message-center---read-access-on-the-xtkfolder-table}

From build 8141 and above, manual action is necessary if Message Center uses the FDA as an archiving mode.

You need to grant read access on the XtKFolder table to the user linked with the external FDA account.

For a PostgreSQL database for example, the command is as follows:

```
GRANT SELECT ON XtkFolder TO DBUSER;
```

This user must have read access to the following tables:

* NmsBroadLogRtEvent
* NmsBroadLogBatchEvent
* NmsTrackingLogRtEvent
* NmsTrackingLogBatchEvent
* NmsRtEvent
* NmsBatchEvent
* NmsBroadLogMsg
* NmsTrackingUrl
* NmsDelivery
* NmsWebTrackingLog

>[!NOTE]
>
>This modification deletes the "Permission denied for relation xtkfolder" error message.

If the working schema selected in the external FDA account is not the out-of-the-box Neolane account, then this modification to the access rights is not necessary.

-->

