---
product: campaign
title: Drempelwaarden voor verbinding
description: Drempelwaarden voor verbinding
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 8%

---

# Drempelwaarden voor verbinding{#connection-thresholds}



Bij zwaar geladen servers kan de verbindingsdrempel worden overschreden. Hoe dan ook, het is nuttig om te weten te komen waarom.

Er zijn drie verschillende drempels:

* De **Drempel webverbinding**, geconfigureerd in uw webserver. Neem contact op met de systeembeheerder om het bestand te wijzigen.

* De **drempel voor databaseverbinding**. Neem contact op met de databasebeheerder om deze te wijzigen.

* De **Adobe Campaign-verbindingsdrempel**, beschikbaar op twee plaatsen:

   * **Tomcat** zij: alle vragen die daadwerkelijk bij de Adobe Campaign Tomcat-client aankomen.

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

   * **Database**: set van alle verbindingen die tegelijkertijd via een proces in de database worden geopend.

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
