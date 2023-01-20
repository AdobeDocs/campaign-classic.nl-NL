---
product: campaign
title: Configuratie Campagne Tomcat
description: Configuratie Campagne Tomcat
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: f05cea5c9a7b9088d0b86986373b6a0188315aae
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 1%

---

# Apache Tomcat configureren {#configuring-tomcat}

![](../../assets/v7-only.svg)

Adobe Campaign gebruikt een **ingesloten webservlet genaamd Apache Tomcat** om HTTP/HTTPS- verzoeken tussen de toepassing en om het even welke externe interface (met inbegrip van de Console van de Cliënt, gevolgde verbindingen URL, de vraag van de ZEEP, en anderen) te verwerken. Voor alle naar buiten gerichte Adobe Campaign-instanties is er vaak een externe webserver (gewoonlijk IIS of Apache) aanwezig.

Meer informatie over Tomcat in Campaign en hoe u uw Tomcat-versie kunt vinden in [deze pagina](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Deze procedure is beperkt tot **op locatie** implementaties.

## Standaardpoort voor Apache Tomcat {#default-port-for-tomcat}

Wanneer de 8080 luisterpoort van de Tomcat-server al bezig is met een andere toepassing die vereist is voor uw configuratie, moet u de 8080-poort vervangen door een gratis poort (bijvoorbeeld 8090). Als u het bestand wilt wijzigen, bewerkt u het **server.xml** bestand opgeslagen in het dialoogvenster **/tomcat-8/conf** directory van de installatiemap van Adobe Campaign.

Pas dan de haven van de JSP relaispagina&#39;s aan. Om dit te doen, verander **serverConf.xml** bestand opgeslagen in het dialoogvenster **/conf** directory van de installatiemap van Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Een map toewijzen in Apache Tomcat {#mapping-a-folder-in-tomcat}

Als u klantspecifieke instellingen wilt definiëren, kunt u een **user_context.xml** in het **/tomcat-8/conf** map die ook de **context.xml** bestand.

Dit bestand bevat het volgende type informatie:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Deze bewerking kan zo nodig op de server worden gereproduceerd.

## Het Tomcat-foutrapport verbergen {#hide-tomcat-error-report}

Om veiligheidsredenen raden we u ten zeerste aan het Tomcat-foutrapport te verbergen. Dit zijn de stappen die u moet uitvoeren.

1. Open de **server.xml** bestand in het dialoogvenster **/tomcat-8/conf** directory van de installatiemap van Adobe Campaign:  `/usr/local/neolane/nl6/tomcat-8/conf`
1. Voeg het volgende element bij de bodem na alle bestaande contextelementen toe:

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Start de Nlserver- en Apache-webservers opnieuw.
