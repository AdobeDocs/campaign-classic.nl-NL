---
title: Verbindingsdrempels
seo-title: Verbindingsdrempels
description: Verbindingsdrempels
seo-description: null
page-status-flag: never-activated
uuid: a4b6959a-0f5b-41a2-b4c3-d7d6613d1a18
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f3db77db-94cc-4d75-a59b-2dddce776759
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Verbindingsdrempels{#connection-thresholds}

Voor zwaar geladen servers, zou de verbindingsdrempel kunnen worden overschreden. Hoe dan ook, het is nuttig om te weten te komen waarom.

Er zijn drie verschillende drempels:

1. De verbindingsdrempel van het Web, die in uw Webserver wordt gevormd. Neem contact op met de systeembeheerder om het bestand te wijzigen.
1. De drempel voor databaseverbinding. Neem contact op met de databasebeheerder om deze te wijzigen.
1. De verbindingsdrempel voor Adobe Campagne, die op twee plaatsen beschikbaar is:

   * Tomcat-zijde: alle query&#39;s die daadwerkelijk op de Adobe Campaign Tomcat-client worden ontvangen.

      Deze drempelwaarde is geconfigureerd in het bestand **nl6/tomcat-7/conf/server.xml** . Het **maxThreads** attribuut laat u de drempel van het aantal vragen verhogen die tegelijkertijd worden verwerkt. Het kan bijvoorbeeld worden gewijzigd in 250.

      ```
      <Connector protocol="HTTP/1.1" port="8080"
                     maxThreads="75"
                     minSpareThreads="5"
                     enableLookups="true" redirectPort="8443"
                     acceptCount="100" connectionTimeout="20000"
                     disableUploadTimeout="true" />
          <Engine name="Tomcat-Standalone" defaultHost="localhost">
            <Host name="localhost" appBase="./"
                  unpackWARs="true" autoDeploy="true">
      ```

   * Database: reeks van alle verbindingen die tezelfdertijd op het gegevensbestand door een proces worden geopend.

      Deze drempelwaarde is geconfigureerd in het bestand **nl6/conf/serverConf.xml**. De **attributen maxCnx** die in **datasource pool** worden gevestigd laten u de drempel van gelijktijdig verwerkte vragen verhogen.

      ```
          <!-- Data source
               -->
            <dataSource name="default">
              <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
              <sqlParams funcPrefix="">
                <postConnectSQL/>
              </sqlParams>
              <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
            </dataSource>
      ```

