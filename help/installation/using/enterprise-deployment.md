---
product: campaign
title: Zakelijke implementatie
description: Zakelijke implementatie
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 38c14010-203a-47ab-b23d-6f431dab9a88
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1221'
ht-degree: 3%

---

# Zakelijke implementatie{#enterprise-deployment}



Dit is de meest volledige configuratie. Het bouwt op de standaardconfiguratie voor grotere veiligheid en beschikbaarheid voort:

* specifieke omleidingsservers achter een HTTP- of TCP-taakverdelingsmechanisme, voor schaalbaarheid en beschikbaarheid;
* twee toepassingsservers voor betere productie en failover vermogen (foutentolerantie) en die in LAN geïsoleerd zijn.

De algemene communicatie tussen servers en processen wordt uitgevoerd volgens het volgende schema:

![](assets/s_901_ncs_install_enterpriseconfig.png)

Met dit type van configuratie, kan de verwachte productie 100.000 post per uur met aangewezen bandbreedte en het stemmen overschrijden.

## Functies {#features}

### Voordelen {#advantages}

* Geoptimaliseerde beveiliging: Slechts die servers die aan de buitenkant moeten worden blootgesteld zijn geïnstalleerd op de computer in DMZ.
* Hoge beschikbaarheid is gemakkelijker te garanderen: Alleen de computer die van buitenaf zichtbaar is, moet met het oog op hoge beschikbaarheid worden beheerd.

### Nadelen {#disadvantages}

Hogere hardware- en beheerkosten.

### Aanbevolen apparatuur {#recommended-equipment}

* Toepassingsservers: 2 GHz quad-core CPU, 4 GB RAM, software RAID 1 80 GB SATA harde schijf.
* Redirection servers: 2 GHz quad-core CPU, 4 GB RAM, software RAID 1 80 GB SATA harde schijf.

>[!NOTE]
>
>Het is mogelijk om een bestaand taakverdelingsmechanisme voor verkeer aan de omleidingsservers opnieuw te gebruiken.

## Installatie- en configuratiestappen {#installation-and-configuration-steps}

### Vereisten {#prerequisites}

* JDK op beide toepassingsservers,
* Webserver (IIS, Apache) op beide fronten,
* Toegang tot een databaseserver op beide toepassingsservers,
* Bounce mailbox toegankelijk via POP3,
* Het maken van twee DNS-aliassen op het taakverdelingsmechanisme:

   * de eerste die aan het publiek wordt blootgesteld voor het volgen en aanwijzen van het taakverdelingsmechanisme op een virtueel IP adres (VIP) en die dan aan de twee frontale servers wordt verdeeld;
   * de tweede die aan de interne gebruikers voor toegang via de console wordt blootgesteld en aan een taakverdelingsmechanisme op een virtueel IP adres (VIP) richt en die dan aan de twee toepassingsservers wordt verdeeld.

* Firewall geconfigureerd voor het openen van STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 voor Oracle, 5432 voor PostgreSQL, enz.) poorten. Zie voor meer informatie de sectie [Toegang tot database](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>Als uw toepassingsservers naar één database-instantie wijzen, wordt het schema in het pakket na het importeren van een standaardpakket op de ene instantie niet op de andere instantie geladen.
>  
>Als uw toepassingsservers naar één database-instantie wijzen, wordt het schema na het wijzigen van het schema in één instantie niet in de andere instantie geladen.
>
>Als u deze problemen wilt herstellen, moet u het proces &quot;web@default&quot; opnieuw opstarten in de tweede instantie waar de fout is opgetreden.

### De toepassingsserver installeren en configureren 1 {#installing-and-configuring-the-application-server-1}

In de volgende voorbeelden zijn de parameters van de instantie:

* Naam van de instantie: demo
* DNS-masker: tracking.campagne.net&#42;, console.campagne.net&#42; (De toepassingsserver verwerkt de URL&#39;s voor verbindingen en rapporten van de clientconsole en voor spiegel- en niet-abonnementspagina&#39;s)
* Taal: Engels
* Database: campagne:demo@dbsrv

De stappen voor het installeren van de eerste server zijn:

1. Volg de installatieprocedure voor de Adobe Campaign-server: **nlserver** pakket op Linux of **setup.exe** in Windows.

   Raadpleeg voor meer informatie hierover [Vereisten voor installatie van campagne in Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) en [Vereisten voor installatie van campagne in Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Zodra de Adobe Campaign-server is geïnstalleerd, start u de toepassingsserver (web) met de opdracht **nlserver web-tomcat** (de module van het Web laat u toe om Tomcat in standalone de serverwijze van het Web te beginnen luisterend op haven 8080) en ervoor te zorgen begint Tomcat correct:

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >De eerste keer dat de module Web wordt uitgevoerd, wordt het **config-default.xml** en **serverConf.xml** in de **conf** onder de installatiemap. Alle parameters die beschikbaar zijn in het dialoogvenster **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

   Druk **Ctrl+C** om de server te stoppen.

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: [Eerste start van de server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Voor Windows: [Eerste start van de server](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Wijzig de **internal** wachtwoord met behulp van de opdracht:

   ```
   nlserver config -internalpassword
   ```

   Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) voor meer informatie.

1. Maak de **demo** instantie met de DNS-maskers voor tracering (in dit geval, **tracking.campagne.net**) en de toegang tot clientconsoles (in dit geval, **console.campagne.net**). Er zijn twee manieren om dit te doen:

   * Maak de instantie via de console:

      ![](assets/install_create_new_connexion.png)

      Raadpleeg voor meer informatie hierover [Een instantie maken en aanmelden](../../installation/using/creating-an-instance-and-logging-on.md).

      of

   * Maak de instantie met behulp van opdrachtregels:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      Raadpleeg voor meer informatie hierover [Een instantie maken](../../installation/using/command-lines.md#creating-an-instance).

1. Bewerk de **config-demo.xml** bestand (gemaakt via de vorige opdracht en bevindt zich naast de **config-default.xml** bestand), controleert u of de **mta** (levering), **wfserver** (workflow), **inMail** (rebound mails) en **stat** (statistiek) processen worden toegelaten, dan vorm het adres van **app** Statistische server:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#enabling-processes) voor meer informatie.

1. Bewerk de **serverConf.xml** en specificeer het leveringsdomein, dan specificeer IP (of gastheer) adressen van de DNS servers die door de module MTA worden gebruikt om MX type DNS vragen te beantwoorden.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >De **nameServers** parameters worden alleen in Windows gebruikt.

   Raadpleeg voor meer informatie hierover [Configuratie van campagneserver](../../installation/using/configuring-campaign-server.md).

1. Het installatieprogramma van de clientconsole kopiëren (**setup-client-7.XX**, **YYYY.exe** voor v7 of **setup-client-6.XX**, **YYYY.exe** voor v6.1) aan de **/datakit/nl/eng/jsp** map. [Meer informatie](../../installation/using/client-console-availability-for-windows.md).

1. De Adobe Campaign-server starten (**netwerkbeginserver6** in Windows **/etc/init.d/nlserver6 start** in Linux) en voer de opdracht uit **nlserver pdump** nogmaals de aanwezigheid van alle ingeschakelde modules te controleren.

   >[!NOTE]
   >
   >Vanaf 20.1 raden we u aan in plaats daarvan de volgende opdracht te gebruiken (voor Linux): **systeemserver voor opstarten**


   ```
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   Met deze opdracht weet u ook de versie en het buildnummer van de Adobe Campaign-server die op de computer is geïnstalleerd.

1. Test de **nlserver-web** met de URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Met deze URL hebt u toegang tot de downloadpagina voor het installatieprogramma van de client. [Meer informatie](../../installation/using/client-console-availability-for-windows.md).

   Voer de **internal** login en bijbehorend wachtwoord wanneer u de pagina van de toegangscontrole bereikt.

   ![](assets/s_ncs_install_access_client.png)

### De toepassingsserver 2 installeren en configureren {#installing-and-configuring-the-application-server-2}

Voer de volgende stappen uit:

1. Installeer de Adobe Campaign-server.
1. Kopieer de bestanden van de instantie die u hebt gemaakt naar toepassingsserver 1.

   Wij houden de zelfde instantienaam zoals toepassingsserver 1.

1. Wijzig de **internal** op dezelfde manier als toepassingsserver 1.
1. Koppel de database aan de instantie:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Bewerk de **config-demo.xml** bestand (gemaakt via de vorige opdracht en bevindt zich naast de **config-default.xml** bestand), controleert u of de **mta** (levering), **wfserver** (workflow), **inMail** (rebound mails) en **stat** (statistiek) processen worden toegelaten, dan vorm het adres van **app** Statistische server:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#enabling-processes) voor meer informatie.

1. Bewerk de **serverConf.xml** dossier en bevolk de DNS configuratie van de module MTA:

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >De **nameServers** wordt alleen gebruikt in Windows.

   Raadpleeg voor meer informatie hierover [Configuratie van campagneserver](../../installation/using/configuring-campaign-server.md).

1. Start de Adobe Campaign-servers.

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: [Eerste start van de server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Voor Windows: [Eerste start van de server](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### De frontservers installeren en configureren {#installing-and-configuring-the-frontal-servers}

Installatie- en configuratieprocedures zijn op beide computers identiek.

De stappen zijn als volgt:

1. Installeer de Adobe Campaign-server.
1. Voldoe aan de procedure van de de serverintegratie van het Web (IIS, Apache) die in de volgende secties wordt beschreven:

   * Voor Linux: [Integratie in een webserver voor Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * Voor Windows: [Integratie in een webserver voor Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Kopieer de **config-demo.xml** en **serverConf.xml** bestanden die tijdens de installatie zijn gemaakt. In de **config-demo.xml** bestand, activeer het **trackinglogd** de **mta**, **inmail**, **wfserver** en **stat** processen.
1. Bewerk de **serverConf.xml** en vult de overtollige het volgen servers in de parameters van de omleiding:

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Start de website en test de omleiding via de URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   De browser moet de volgende berichten weergeven (afhankelijk van de URL die door het taakverdelingsmechanisme is omgeleid):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   of

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: [De server van het Web lanceren en de configuratie testen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * Voor Windows: [De server van het Web lanceren en de configuratie testen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Start de Adobe Campaign-server.
