---
solution: Campaign Classic
product: campaign
title: Drempelwaarden voor verbinding
description: Drempelwaarden voor verbinding
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---


# Drempelwaarden voor verbinding{#connection-thresholds}

Voor zwaar geladen servers, zou de verbindingsdrempel kunnen worden overschreden. Hoe dan ook, het is nuttig om te weten te komen waarom.

Er zijn drie verschillende drempels:

1. De verbindingsdrempel van het Web, die in uw Webserver wordt gevormd. Neem contact op met de systeembeheerder om het bestand te wijzigen.
1. De drempel voor databaseverbinding. Neem contact op met de databasebeheerder om deze te wijzigen.
1. De Adobe Campaign-verbindingsdrempel, beschikbaar op twee plaatsen:

   * Tomcat-zijde: alle vragen die daadwerkelijk op de Adobe Campaign Tomcat-client aankomen.

      Deze drempel wordt gevormd in **nl6/tomcat-8/conf/server.xml** dossier. Met het kenmerk **maxThreads** kunt u de drempel verhogen voor het aantal query&#39;s dat tegelijkertijd wordt verwerkt. Het kan bijvoorbeeld worden gewijzigd in 250.

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

   * Database: reeks van alle verbindingen opent tezelfdertijd op het gegevensbestand door een proces.

      Deze drempel wordt gevormd in het dossier **nl6/conf/serverConf.xml**. Met het **maxCnx**-kenmerk in **datasource pool** kunt u de drempel verhogen voor gelijktijdig verwerkte query&#39;s.

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

