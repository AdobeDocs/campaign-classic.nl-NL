---
product: campaign
title: Configuratie Campagne Tomcat
description: Configuratie Campagne Tomcat
feature: Installation, Instance Settings
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Apache Tomcat configureren {#configuring-tomcat}

Adobe Campaign gebruikt een **ingebedde Webserver genoemd Apache Tomcat** om HTTP/HTTPS- verzoeken tussen de toepassing en om het even welke externe interface (met inbegrip van de Console van de Cliënt, gevolgde verbindingen URL, SOAP vraag, en anderen) te verwerken. Er is vaak een externe webserver (meestal IIS of Apache) voor deze server voor naar buiten gerichte Adobe Campaign-instanties.

Leer meer over Tomcat in Campaign en hoe te om van uw versie van Tomcat in [ de plaats te bepalen deze pagina ](../../production/using/locate-tomcat-version.md).

>[!AVAILABILITY]
>
>
>* Vanaf Campagne v7.4.1 is Tomcat 10.1 de standaardversie.
>
>* Adobe Campaign Classic maakt geen gebruik van WebSocket- en HTTP2-protocollen.
>



## Standaardpoort voor Apache Tomcat {#default-port-for-tomcat}


>[!NOTE]
>
>Deze procedure wordt beperkt tot **op-gebouw** plaatsingen.
>

Wanneer de 8080 luisterpoort van de Tomcat-server al bezig is met een andere toepassing die vereist is voor uw configuratie, moet u de 8080-poort vervangen door een gratis poort (bijvoorbeeld 8090). Om het te veranderen, geef het {**dossier 0} server.xml uit dat in de** wordt opgeslagen/tomcat-X/conf **folder van de de installatiemap van Adobe Campaign.**

Pas dan de haven van de JSP relaispagina&#39;s aan. Om dit te doen, verander het {**dossier 0} serverConf.xml dat in de** wordt opgeslagen/conf **folder van de de installatiemap van Adobe Campaign.**

```xml
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Een map toewijzen in Apache Tomcat {#mapping-a-folder-in-tomcat}


>[!NOTE]
>
>Deze procedure wordt beperkt tot **op-gebouw** plaatsingen.
>

Om klant specifieke montages te bepalen, kunt u a **user_contextxml** dossier in de **/tomcat-X/conf** omslag tot stand brengen, die ook het {**dossier 4} context.xml bevat.**

Dit bestand bevat het volgende type informatie:

```xml
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Deze bewerking kan zo nodig op de server worden gereproduceerd.

## Het Tomcat-foutrapport verbergen {#hide-tomcat-error-report}


>[!NOTE]
>
>Deze procedure wordt beperkt tot **op-gebouw** plaatsingen.
>
>Deze wijziging is niet meer nodig vanaf Campagne v7.4.1.
>

Om veiligheidsredenen raden we u aan het Tomcat-foutrapport te verbergen. Voer de volgende stappen uit:

1. Open het {**dossier 0} server.xml dat in** wordt gevestigd/tomcat-X/conf **folder van de de installatiemap van Adobe Campaign: `/usr/local/neolane/nl6/tomcat-X/conf`**
1. Voeg het volgende element bij de bodem na alle bestaande contextelementen toe:

   ```xml
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Start de Nlserver- en Apache-webservers opnieuw.
