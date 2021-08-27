---
product: campaign
title: Configuratie Campagne Tomcat
description: Configuratie Campagne Tomcat
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf,b4a422b4-4b8b-4883-8d74-0dccda4a5ef3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Apache Tomcat configureren {#configuring-tomcat}

![](../../assets/v7-only.svg)

Adobe Campaign gebruikt een **ingesloten webserver met de naam Apache Tomcat** om HTTP/HTTPS-aanvragen tussen de toepassing en elke externe interface te verwerken (zoals Client Console, bijgehouden URL-koppelingen, SOAP-aanroepen en andere). Er is vaak een externe webserver (meestal IIS of Apache) voor deze server voor naar buiten gerichte Adobe Campaign-instanties.

Meer informatie over Tomcat in Campaign en hoe u uw Tomcat-versie kunt vinden op [deze pagina](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Deze procedure is beperkt tot **on-premise** plaatsingen.

## Standaardpoort voor Apache Tomcat {#default-port-for-tomcat}

Wanneer de 8080 luisterpoort van de Tomcat-server al bezig is met een andere toepassing die vereist is voor uw configuratie, moet u de 8080-poort vervangen door een gratis poort (bijvoorbeeld 8090). Als u dit wilt wijzigen, bewerkt u het bestand **server.xml** dat is opgeslagen in de map **/tomcat-8/conf** van de installatiemap van Adobe Campaign.

Pas dan de haven van de JSP relaispagina&#39;s aan. Hiervoor wijzigt u het bestand **serverConf.xml** dat is opgeslagen in de map **/conf** van de installatiemap van Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Een map toewijzen in Apache Tomcat {#mapping-a-folder-in-tomcat}

Als u klantspecifieke instellingen wilt definiëren, kunt u een bestand **user_context.xml** maken in de map **/tomcat-8/conf**, die ook het bestand **context.xml** bevat.

Dit bestand bevat het volgende type informatie:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Deze bewerking kan zo nodig op de server worden gereproduceerd.
