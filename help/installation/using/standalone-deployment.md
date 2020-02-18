---
title: Standalone-implementatie
seo-title: Standalone-implementatie
description: Standalone-implementatie
seo-description: null
page-status-flag: never-activated
uuid: 48ce793e-cb9f-4102-898f-758512cb9bf2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 9834638f-a8bb-4969-9f8d-99b8d9fdb1ca
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6b631f8456ad1f61cec1630334d76752f6af9866

---


# Standalone-implementatie{#standalone-deployment}

Deze configuratie omvat alle componenten op de zelfde computer:

* toepassingsproces (web),
* leveringsproces (mta),
* omleidingsproces (tracking);
* workflowproces en geplande taken (wfserver);
* stuiterend-mailproces (inMail),
* Statistieken (statussen).

De algemene communicatie tussen de processen wordt uitgevoerd volgens het volgende schema:

![](assets/s_900_ncs_install_standaloneconfig.png)

Dit type van configuratie kan worden in werking gesteld wanneer het beheren van lijsten van minder dan 100.000 ontvangers en met, bijvoorbeeld, de volgende softwarelagen:

* Linux
* Apache
* PostgreSQL
* Qmail.

Naarmate het volume toeneemt, verplaatst een variant van deze architectuur de databaseserver naar een andere computer voor betere prestaties.

>[!NOTE]
>
>Een bestaande databaseserver kan ook worden gebruikt als deze over voldoende bronnen beschikt.

## Functies {#features}

### Voordelen {#advantages}

* Volledig zelfstandig en goedkoop configuratie (geen factureerbare licenties vereist als de hieronder vermelde opensource-software wordt gebruikt).
* Vereenvoudigde installatie en netwerkconfiguratie.

### Nadelen {#disadvantages}

* Een kritieke computer in geval van incident.
* Beperkte bandbreedte bij het uitzenden van berichten (in onze ervaring ongeveer tienduizenden berichten per uur).
* Mogelijke vertraging van de toepassing bij het uitzenden.
* De toepassingsserver moet van buitenaf beschikbaar zijn (terwijl wordt gevestigd in DMZ, bijvoorbeeld) aangezien het gastheren de redirection server.

## Installatie- en configuratiestappen {#installation-and-configuration-steps}

### Vereisten {#prerequisites}

* JDK
* Webserver (IIS, Apache),
* Toegang tot een databaseserver,
* Bounce mailbox toegankelijk via POP3,
* Maken van twee DNS-aliassen:

   * de eerste die aan het publiek voor het volgen van en het richten aan de computer op zijn openbaar IP wordt blootgesteld;
   * de tweede alias die aan interne gebruikers voor consoletoegang wordt blootgesteld en aan de zelfde computer richten.

* Firewall geconfigureerd voor het openen van STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 voor Oracle, 5432 voor PostgreSQL, enz.) poorten. Voor verdere informatie, verwijs naar de configuratie [van het](../../installation/using/network-configuration.md)Netwerk.

In de volgende voorbeelden zijn de parameters van de instantie:

* Naam van de instantie: **demo**
* DNS-masker: **console.campagne.net*** (slechts voor de verbindingen van de cliëntconsole en voor rapporten)
* Database: **campagne:demo@dbsrv**

### Installeren en configureren (één computer) {#installing-and-configuring--single-machine-}

Voer de volgende stappen uit:

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

   * Voor Linux: [Eerste start-up van de server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Voor Windows: [Eerste start-up van de server](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

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

1. Bewerk het bestand **config-demo.xml** (gemaakt in de vorige stap naast **config-default.xml**) en zorg ervoor dat de processen mta **(levering),** wfserver **(workflow),** inMail **** **** (bounce mails) enstat (statistiek) zijn ingeschakeld. Dan vorm het adres van de statistiekserver:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="localhost"/>
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
   >De parameter **nameServers** wordt alleen in Windows gebruikt.

   Raadpleeg de configuratie [van de](../../installation/using/campaign-server-configuration.md)Campagneserver voor meer informatie hierover.

1. Kopieer het installatieprogramma van de clientconsole (**setup-client-7.XX**, **YYYY.exe** voor v7 of **setup-client-6.XX**, **YYY.exe** voor v6.1) naar de map **/datakit/nl/eng/jsp** .

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: Beschikbaarheid van [clientconsole voor Linux](../../installation/using/client-console-availability-for-linux.md)
   * Voor Windows: Beschikbaarheid van [clientconsole voor Windows](../../installation/using/client-console-availability-for-windows.md)

1. Volg de procedure van de de serverintegratie van het Web (IIS, Apache) in de volgende secties wordt beschreven die:

   * Voor Linux: [Integratie in een webserver voor Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Voor Windows: [Integratie in een server van het Web voor Vensters](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Start de website en test omleiding met de URL: https://tracking.campaign.net/r/test.

   De browser moet het volgende bericht weergeven:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: De server van het Web [lanceren en de configuratie testen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Voor Windows: De server van het Web [lanceren en de configuratie testen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

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

1. Test de **webmodule** van de server met de URL: https://console.campaign.net/nl/jsp/logon.jsp

   Met deze URL hebt u toegang tot de downloadpagina voor het installatieprogramma van de client.

   Ga **interne** login en het bijbehorende wachtwoord in wanneer u de pagina van de toegangscontrole bereikt.

   ![](assets/s_ncs_install_access_client.png)

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: Beschikbaarheid van [clientconsole voor Linux](../../installation/using/client-console-availability-for-linux.md)
   * Voor Windows: Beschikbaarheid van [clientconsole voor Windows](../../installation/using/client-console-availability-for-windows.md)

1. Start de Adobe Campaign-clientconsole (vanaf de vorige downloadpagina of die rechtstreeks op de server wordt gestart voor een Windows-installatie), stel de URL van de serververbinding in op https://console.campaign.net en maak verbinding met de **interne** aanmelding.

   Zie Een instantie [maken en aanmelden](../../installation/using/creating-an-instance-and-logging-on.md) en [interne id](../../installation/using/campaign-server-configuration.md#internal-identifier).

   De wizard voor het maken van de database wordt weergegeven wanneer u zich voor het eerst aanmeldt:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Voer de stappen in de wizard uit en maak de database die aan de verbindingsinstantie is gekoppeld.

   Voor meer op dit, verwijs naar het [Creëren van en het vormen van het gegevensbestand](../../installation/using/creating-and-configuring-the-database.md).

   Als de database eenmaal is gemaakt, meldt u zich af.

1. Meld u opnieuw aan bij de clientconsole met de **beheerdersaanmelding** zonder wachtwoord en start de implementatiewizard ( **[!UICONTROL Tools > Advanced]** menu) om de configuratie van de instantie te voltooien.

   Raadpleeg Een instantie [](../../installation/using/deploying-an-instance.md)implementeren voor meer informatie.

   De belangrijkste parameters die moeten worden ingesteld zijn:

   * E-maillevering: afzender en antwoordadressen en de foutenbrievenbus voor stuitende post.
   * Tekstspatiëring: Vul de externe URL die wordt gebruikt voor omleiding en de interne URL, klik op **Registratie op de volgende server(s)** en valideer deze vervolgens op de **demo** -instantie van de trackingserver.

      Voor meer op dit, verwijs naar het [Volgen configuratie](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      Aangezien de Adobe Campaign-server wordt gebruikt als toepassingsserver en omleidingsserver, is de interne URL die wordt gebruikt voor het verzamelen van trackinglogboeken en het overbrengen van URL&#39;s een directe interne verbinding met Tomcat (https://localhost:8080).

   * Stuitbeheer: Voer de parameters in voor het afhandelen van stuiterende berichten (houd geen rekening met de sectie **Onverwerkte stuiterende berichten** ).
   * Toegang vanaf: Geef de twee URL&#39;s op voor rapporten, webformulieren en spiegel.

      ![](assets/d_ncs_install_web_url.png)

