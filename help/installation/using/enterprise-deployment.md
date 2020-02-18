---
title: Implementatie in ondernemingen
seo-title: Implementatie in ondernemingen
description: Implementatie in ondernemingen
seo-description: null
page-status-flag: never-activated
uuid: 2c2b5cef-86cb-4cb5-801a-ca6afeae90bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 066d0ac1-033c-467b-aa6c-43a97ecd8632
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6b631f8456ad1f61cec1630334d76752f6af9866

---


# Implementatie in ondernemingen{#enterprise-deployment}

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

   * de eerste die aan het publiek voor het volgen van en het richten aan het taakverdelingsmechanisme op een virtueel IP adres (VIP) wordt blootgesteld en die dan aan de twee frontale servers wordt verdeeld;
   * de tweede die aan de interne gebruikers voor toegang via de console wordt blootgesteld en aan een taakverdelingsmechanisme op een virtueel IP adres (VIP) richt en die dan aan de twee toepassingsservers wordt verdeeld.

* Firewall geconfigureerd voor het openen van STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 voor Oracle, 5432 voor PostgreSQL, enz.) poorten. Voor meer informatie, verwijs naar sectie [Toegang](../../installation/using/network-configuration.md#database-access)van het Gegevensbestand.

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
* DNS-masker: tracking.campagne.net*, console.campagne.net* (de toepassingsserver verwerkt de URL&#39;s voor verbindingen en rapporten van de clientconsole en voor spiegelpagina&#39;s en pagina&#39;s zonder abonnement)
* Taal: Engels
* Database: campagne:demo@dbsrv

De stappen voor het installeren van de eerste server zijn:

1. Voer de installatieprocedure voor de Adobe Campagneserver uit: **nlserver** -pakket in Linux of **setup.exe** in Windows.

   Raadpleeg voor meer informatie de [vereisten voor de installatie van Campagne in Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) en [de vereisten voor de installatie van Campagne in Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Zodra de server van de Campagne van Adobe wordt geïnstalleerd, begin de toepassingsserver (Web) gebruikend het bevel **nlserver web -tomcat** (de module van het Web laat u toe om Tomcat op standalone de serverwijze van het Web te beginnen luisterend op haven 8080) en ervoor te zorgen Tomcat correct begint:

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >De eerste keer wordt de module van het Web uitgevoerd leidt het tot de **config-default.xml** en **serverConf.xml** - dossiers in de **conf** folder onder de installatiemap. Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

   Druk op **Ctrl+C** om de server te stoppen.

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: [Eerste start-up van de server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Voor Windows: [Eerste start-up van de server](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Wijzig het **interne** wachtwoord met de opdracht:

   ```
   nlserver config -internalpassword
   ```

   Raadpleeg de [interne id](../../installation/using/campaign-server-configuration.md#internal-identifier)voor meer informatie hierover.

1. Creeer de **demo** instantie met de DNS maskers voor het volgen (in dit geval, **tracking.campagne.net**) en toegang tot cliëntconsoles (in dit geval, **console.campagne.net**). Er zijn twee manieren om dit te doen:

   * Maak de instantie via de console:

      ![](assets/install_create_new_connexion.png)

      Raadpleeg [Een instantie maken en aanmelden](../../installation/using/creating-an-instance-and-logging-on.md)voor meer informatie hierover.

      of

   * Maak de instantie met behulp van opdrachtregels:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      Raadpleeg [Een instantie](../../installation/using/command-lines.md#creating-an-instance)maken voor meer informatie hierover.

1. Bewerk het bestand **config-demo.xml** (gemaakt via de vorige opdracht en gelokaliseerd naast het bestand **config-default.xml** ), controleer of de **mta** (levering), **wfserver** (workflow), **inMail** **** **** (rebound mails) en stat (statistiek) zijn ingeschakeld en configureer vervolgens het adres van de gegevens van de RoAppAppsConfiguratieserserver:

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

   Raadpleeg [Processen](../../installation/using/campaign-server-configuration.md#enabling-processes)inschakelen voor meer informatie.

1. Bewerk het bestand **serverConf.xml** en geef het leveringsdomein op. Geef vervolgens de IP-adressen (of de host) van de DNS-servers op die door de MTA-module worden gebruikt om DNS-vragen van het MX-type te beantwoorden.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >De parameters **nameServers** worden alleen in Windows gebruikt.

   Raadpleeg de configuratie [van de](../../installation/using/campaign-server-configuration.md)Campagneserver voor meer informatie hierover.

1. Kopieer het installatieprogramma van de clientconsole (**setup-client-7.XX**, **YYYY.exe** voor v7 of **setup-client-6.XX**, **YYY.exe** voor v6.1) naar de map **/datakit/nl/eng/jsp** .

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: Beschikbaarheid van [clientconsole voor Linux](../../installation/using/client-console-availability-for-linux.md)
   * Voor Windows: Beschikbaarheid van [clientconsole voor Windows](../../installation/using/client-console-availability-for-windows.md).

1. Start de Adobe Campagne-server (**Net start Nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux) en voer de PDump **van de** opdrachtserver opnieuw uit om de aanwezigheid van alle ingeschakelde modules te controleren.

   >[!NOTE]
   >
   >Vanaf 20.1 raden we u aan in plaats daarvan de volgende opdracht te gebruiken (voor Linux): **systemctl start nlserver**


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

   Met deze opdracht weet u ook de versie en het buildnummer van de Adobe Campagne-server die op de computer is geïnstalleerd.

1. Test de **webmodule** van de server met de URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Met deze URL hebt u toegang tot de downloadpagina voor het installatieprogramma van de client.

   Ga **interne** login en het bijbehorende wachtwoord in wanneer u de pagina van de toegangscontrole bereikt.

   ![](assets/s_ncs_install_access_client.png)

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: Beschikbaarheid van [clientconsole voor Linux](../../installation/using/client-console-availability-for-linux.md)
   * Voor Windows: Beschikbaarheid van [clientconsole voor Windows](../../installation/using/client-console-availability-for-windows.md)

### De toepassingsserver 2 installeren en configureren {#installing-and-configuring-the-application-server-2}

Voer de volgende stappen uit:

1. Installeer de Adobe Campagneserver.
1. Kopieer de bestanden van de instantie die u hebt gemaakt naar toepassingsserver 1.

   Wij houden de zelfde instantienaam zoals toepassingsserver 1.

1. Verander **intern** in het zelfde als toepassingsserver 1.
1. Koppel de database aan de instantie:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Bewerk het bestand **config-demo.xml** (gemaakt via de vorige opdracht en gelokaliseerd naast het bestand **config-default.xml** ), controleer of de **mta** (levering), **wfserver** (workflow), **inMail** **** **** (rebound mails) en stat (statistiek) zijn ingeschakeld en configureer vervolgens het adres van de gegevens van de RoAppAppsConfiguratieserserver:

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

   Raadpleeg [Processen](../../installation/using/campaign-server-configuration.md#enabling-processes)inschakelen voor meer informatie.

1. Bewerk het bestand **serverConf.xml** en vul de DNS-configuratie van de MTA-module in:

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >De parameter **nameServers** wordt alleen in Windows gebruikt.

   Raadpleeg de configuratie [van de](../../installation/using/campaign-server-configuration.md)Campagneserver voor meer informatie hierover.

1. Start de Adobe Campagne-servers.

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: [Eerste start-up van de server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Voor Windows: [Eerste start-up van de server](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### De frontservers installeren en configureren {#installing-and-configuring-the-frontal-servers}

Installatie- en configuratieprocedures zijn op beide computers identiek.

De stappen zijn als volgt:

1. Installeer de Adobe Campaign-server,
1. Voldoe aan de procedure van de de serverintegratie van het Web (IIS, Apache) die in de volgende secties wordt beschreven:

   * Voor Linux: [Integratie in een server van het Web voor Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * Voor Windows: [Integratie in een server van het Web voor Vensters](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Kopieer de bestanden **config-demo.xml** en **serverConf.xml** die tijdens de installatie zijn gemaakt. Activeer in het bestand **config-demo.xml** het **trackinglogd** -proces en deactiveer de **mta**-, **inmail**-, **wfserver** **** - en-processen.
1. Bewerk het bestand **serverConf.xml** en vul de overtollige trackingservers in de parameters van de omleiding in:

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

   * Voor Linux: De server van het Web [lanceren en de configuratie](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)testen,
   * Voor Windows: De server van het Web [lanceren en het testen van de configuratie](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Start de Adobe Campagneserver.

