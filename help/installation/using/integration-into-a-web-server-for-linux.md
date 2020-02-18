---
title: Integratie in een webserver voor Linux
seo-title: Integratie in een webserver voor Linux
description: Integratie in een webserver voor Linux
seo-description: null
page-status-flag: never-activated
uuid: 7b18d176-4458-46a8-8da4-3621f90c6b13
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 752ba848-aee9-4bb0-b2c5-490f3124f74e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a37daa8e31afd3d2ab7d5b70bd8ae02c59ce9ee0

---


# Integratie in een webserver voor Linux{#integration-into-a-web-server-for-linux}

Adobe Campagne omvat Apache Tomcat die via HTTP (en SOAP) als ingangspunt in de toepassingsserver fungeert.

U kunt deze geïntegreerde Tomcat-server gebruiken om HTTP-aanvragen te bedienen.

In dit geval:

* de standaard luisterpoort is 8080. Om het te veranderen, verwijs naar het [Vormen Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat).
* De clientconsoles maken vervolgens verbinding met een URL, zoals:

   ```
   http://<computer>:8080
   ```

Nochtans, voor veiligheid en beleid, adviseren wij gebruikend een specifieke server van het Web als belangrijkste ingangspunt voor het verkeer van HTTP wanneer de computer die de Campagne van Adobe in werking stelt op Internet wordt blootgesteld en u wenst om toegang tot de console buiten uw netwerk te openen.

Een server van het Web laat u ook gegevensvertrouwelijkheid met het protocol van HTTPs waarborgen.

Eveneens, moet u een server van het Web gebruiken wanneer u wenst om de volgende functionaliteit te gebruiken, die slechts als uitbreidingsmodule aan een server van het Web beschikbaar is.

>[!NOTE]
>
>Als u de trackingfunctionaliteit niet gebruikt, kunt u een standaardinstallatie van Apache of IIS uitvoeren met een omleiding naar Campagne. De volgende de serveruitbreidingsmodule van het Web wordt niet vereist.

## De Apache-webserver configureren met Debian {#configuring-the-apache-web-server-with-debian}

Dit proces is van toepassing als u Apache hebt geïnstalleerd onder een distributie op basis van APT.

Voer de volgende stappen uit:

1. Schakel de modules uit die standaard met de volgende opdracht zijn geladen:

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Zorg ervoor dat de modules **alias**, **authz_host** en **mime** nog steeds zijn ingeschakeld. Hiervoor gebruikt u de volgende opdracht:

   ```
   a2enmod  alias authz_host mime
   ```

1. Maak het bestand **nlsrv.load** in **/etc/apache2/mods-available** en voeg de volgende inhoud in:

   In het Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Maak het bestand **nlsrv.conf** in **/etc/apache2/mods-available** met de volgende opdracht:

   ```
   ln -s /usr/local/[INSTALL]/nl6/tomcat-7/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Activeer deze module met de volgende opdracht:

   ```
    a2enmod nlsrv
   ```

   Als u de module **mod_rewrite** voor de pagina&#39;s van de Campagne van Adobe gebruikt, moet u de **nlsrv.load** en **nlsrv.conf** dossiers anders noemen aan **zz-nlsrv.load** en **zz-nlsrv.conf**. Voer de volgende opdracht uit om de module te activeren:

   ```
   a2enmod zz-nlsrv
   ```

1. Bewerk het bestand **/etc/apache2/envars** en voeg de volgende regels toe:

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   Sla de wijzigingen op.

1. Voeg vervolgens gebruikers van Adobe Campagne toe aan de Apache-gebruikersgroep en vice versa met het volgende type opdracht:

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Apache opnieuw starten:

   ```
   invoke-rc.d apache2 restart
   ```

## Apache-webserver configureren in RHEL {#configuring-apache-web-server-in-rhel}

Deze procedure is van toepassing als u Apache hebt geïnstalleerd en beveiligd onder een op RPM (RHEL, CentOS en Suse) gebaseerd pakket.

Voer de volgende stappen uit:

1. Activeer in het `httpd.conf` bestand de volgende Apache-modules:

   ```
   alias
   authz_host
   mime
   ```

1. Deactiveer de volgende modules:

   ```
   auth_basic
   authn_file
   authz_default
   authz_user
   autoindex
   cgi
   dir
   env
   negotiation
   userdir
   ```

   Opmerkingen maken over de functies die aan gedeactiveerde modules zijn gekoppeld:

   ```
   DirectoryIndex
   IndexOptions    
   AddIconByEncoding    
   AddIconByType    
   AddIcon    
   DefaultIcon    
   ReadmeName    
   HeaderName    
   IndexIgnore    
   LanguagePriority    
   ForceLanguagePriority
   ```

1. Maak een specifiek configuratiebestand voor Adobe Campagne in de `/etc/httpd/conf.d/` map. Bijvoorbeeld `CampaignApache.conf`

1. Voeg voor **RHEL7** de volgende instructies toe aan het bestand:

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/tomcat-7/conf/apache_neolane.conf
   ```

1. Voor **RHEL7**:

   Voeg het `/etc/systemd/system/httpd.service` bestand toe met de volgende inhoud:

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   Werk de module bij die door systeem wordt gebruikt:

   ```
   systemctl daemon-reload
   ```

1. Voeg vervolgens Adobe Campagne-operatoren toe aan de groep Apache-operatoren en vice versa door de opdracht uit te voeren:

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   Welke groepsnamen moeten worden gebruikt, is afhankelijk van de manier waarop Apache is geconfigureerd.

1. Voer Apache en de Adobe Campaign-server uit.

   Voor RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## De server van het Web lanceren en de configuratie testen{#launching-the-web-server-and-testing-the-configuration}

U kunt de configuratie nu testen door Apache te starten. De Adobe Campagne-module moet nu zijn banner op de console weergeven (twee banners op bepaalde besturingssystemen):

```
 /etc/init.d/apache start
```

De volgende informatie wordt weergegeven:

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

Controleer vervolgens of de URL reageert door een test-URL in te dienen.

U kunt dit testen vanaf de opdrachtregel door het volgende uit te voeren:

```
 telnet localhost 80  
```

U zou moeten verkrijgen:

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
````

Voer vervolgens het volgende in:

```
GET /r/test
````

De volgende informatie wordt weergegeven:

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
````

U kunt de URL ook aanvragen [`https://<computer>`](https://machine/r/test) vanuit een webbrowser.