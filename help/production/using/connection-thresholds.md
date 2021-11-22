---
product: campaign
title: Drempelwaarden voor verbinding
description: Drempelwaarden voor verbinding
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# Drempelwaarden voor verbinding{#connection-thresholds}

![](../../assets/v7-only.svg)

Voor zwaar geladen servers, zou de verbindingsdrempel kunnen worden overschreden. Hoe dan ook, het is nuttig om te weten te komen waarom.

Er zijn drie verschillende drempels:

* De **Drempel webverbinding**, geconfigureerd in uw webserver. Neem contact op met de systeembeheerder om het bestand te wijzigen.

* De **drempel voor databaseverbinding**. Neem contact op met de databasebeheerder om deze te wijzigen.

* De **Adobe Campaign-verbindingsdrempel**, beschikbaar op twee plaatsen:

   * **Tomcat** zijde: alle vragen die daadwerkelijk op de Adobe Campaign Tomcat-client aankomen.

      Deze drempel wordt geconfigureerd in de **nl6/tomcat-8/conf/server.xml** bestand. De **maxThreads** Met kenmerk kunt u de drempel verhogen voor het aantal query&#39;s dat tegelijkertijd wordt verwerkt. Het kan bijvoorbeeld worden gewijzigd in 250.

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

   * **Database**: reeks van alle verbindingen die tezelfdertijd op het gegevensbestand door een proces worden geopend.

      Deze drempel is geconfigureerd in het bestand **nl6/conf/serverConf.xml**. De **maxCnx** kenmerk bevindt zich in **gegevensbrongroep** laat u de drempel van gelijktijdig verwerkte vragen verhogen.

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
