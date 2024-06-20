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
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Apache Tomcat configureren {#configuring-tomcat}

Adobe Campaign gebruikt een **ingesloten webservlet genaamd Apache Tomcat** om HTTP/HTTPS- verzoeken tussen de toepassing en om het even welke externe interface (met inbegrip van de Console van de Cliënt, gevolgde verbindingen URL, SOAP vraag, en anderen) te verwerken. Er is vaak een externe webserver (meestal IIS of Apache) voor deze server voor naar buiten gerichte Adobe Campaign-instanties.

Meer informatie over Tomcat in Campaign en hoe u uw Tomcat-versie kunt vinden in [deze pagina](../../production/using/locate-tomcat-version.md).

>[!AVAILABILITY]
>
> Vanaf v7.4.1 is Tomcat 10.1 de standaardversie.
>


## Standaardpoort voor Apache Tomcat {#default-port-for-tomcat}


>[!NOTE]
>
>Deze procedure is beperkt tot **op locatie** implementaties.
>

Wanneer de 8080 luisterpoort van de Tomcat-server al bezig is met een andere toepassing die vereist is voor uw configuratie, moet u de 8080-poort vervangen door een gratis poort (bijvoorbeeld 8090). Als u het bestand wilt wijzigen, bewerkt u het **server.xml** bestand opgeslagen in **/tomcat-X/conf** directory van de installatiemap van Adobe Campaign.

Pas dan de haven van de JSP relaispagina&#39;s aan. Om dit te doen, verander **serverConf.xml** bestand opgeslagen in **/conf** directory van de installatiemap van Adobe Campaign.

```xml
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Een map toewijzen in Apache Tomcat {#mapping-a-folder-in-tomcat}


>[!NOTE]
>
>Deze procedure is beperkt tot **op locatie** implementaties.
>

Als u klantspecifieke instellingen wilt definiëren, kunt u een **user_context.xml** in het **/tomcat-X/conf** map die ook de **context.xml** bestand.

Dit bestand bevat het volgende type informatie:

```xml
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Deze bewerking kan zo nodig op de server worden gereproduceerd.

## Het Tomcat-foutrapport verbergen {#hide-tomcat-error-report}


>[!NOTE]
>
>Deze procedure is beperkt tot **op locatie** implementaties.
>
>Deze wijziging is niet meer nodig vanaf Campagne v7.4.1.
>

Om veiligheidsredenen raden we u aan het Tomcat-foutrapport te verbergen. Voer de volgende stappen uit:

1. Open de **server.xml** bestand in het dialoogvenster **/tomcat-X/conf** directory van de installatiemap van Adobe Campaign:  `/usr/local/neolane/nl6/tomcat-X/conf`
1. Voeg het volgende element bij de bodem na alle bestaande contextelementen toe:

   ```xml
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Start de Nlserver- en Apache-webservers opnieuw.
