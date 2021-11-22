---
product: campaign
title: Zelfstandige implementatie
description: Zelfstandige implementatie
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1086'
ht-degree: 2%

---

# Zelfstandige implementatie{#standalone-deployment}

![](../../assets/v7-only.svg)

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
* Apache,
* PostgreSQL,
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

* Firewall geconfigureerd voor het openen van SMTP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 voor Oracle, 5432 voor PostgreSQL, enz.) poorten. Zie voor meer informatie [Netwerkconfiguratie](../../installation/using/network-configuration.md).

In de volgende voorbeelden zijn de parameters van de instantie:

* Naam van de instantie: **demo**
* DNS-masker: **console.campagne.net*** (alleen voor clientconsoleverbindingen en voor rapporten)
* Database: **campagne:demo@dbsrv**

### Installeren en configureren (één computer) {#installing-and-configuring--single-machine-}

Voer de volgende stappen uit:

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

   * Voor Linux: [Eerste start van de server](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Voor Windows: [Eerste start van de server](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

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

1. Bewerk de **config-demo.xml** bestand (gemaakt in de vorige stap naast **config-default.xml**) en zorg ervoor dat de **mta** (levering), **wfserver** (workflow), **inMail** (stuiterende berichten) en **stat** (statistiek) processen zijn ingeschakeld. Dan vorm het adres van de statistiekserver:

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

   Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#enabling-processes) voor meer informatie.

1. Bewerk de **serverConf.xml** en specificeer het leveringsdomein, dan specificeer IP (of gastheer) adressen van de DNS servers die door de module MTA worden gebruikt om MX type DNS vragen te beantwoorden.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >De **nameServers** wordt alleen gebruikt in Windows.

   Raadpleeg voor meer informatie hierover [Configuratie van campagneserver](../../installation/using/configuring-campaign-server.md).

1. Het installatieprogramma van de clientconsole kopiëren (**setup-client-7.XX**, **YYYY.exe** voor v7 of **setup-client-6.XX**, **YYYY.exe** voor v6.1) aan de **/datakit/nl/eng/jsp** map. [Meer info](../../installation/using/client-console-availability-for-windows.md).

1. Volg de procedure van de de serverintegratie van het Web (IIS, Apache) in de volgende secties wordt beschreven die:

   * Voor Linux: [Integratie in een webserver voor Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Voor Windows: [Integratie in een webserver voor Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Start de website en test omleiding met de URL: https://tracking.campaign.net/r/test.

   De browser moet het volgende bericht weergeven:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: [De server van het Web lanceren en de configuratie testen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Voor Windows: [De server van het Web lanceren en de configuratie testen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

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

1. Test de **nlserver-web** met de URL: https://console.campaign.net/nl/jsp/logon.jsp

   Met deze URL hebt u toegang tot de downloadpagina voor het installatieprogramma van de client.

   Voer de **internal** login en bijbehorend wachtwoord wanneer u de pagina van de toegangscontrole bereikt. [Meer info](../../installation/using/client-console-availability-for-windows.md).

   ![](assets/s_ncs_install_access_client.png)

1. Start de Adobe Campaign-clientconsole (vanaf de vorige downloadpagina of die rechtstreeks op de server wordt gestart voor een Windows-installatie), stel de URL van de serververbinding in op https://console.campaign.net en maak verbinding met de **internal** aanmelden.

   Zie [deze pagina](../../installation/using/creating-an-instance-and-logging-on.md) en [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier).

   De wizard voor het maken van de database wordt weergegeven wanneer u zich voor het eerst aanmeldt:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Voer de stappen in de wizard uit en maak de database die aan de verbindingsinstantie is gekoppeld.

   Raadpleeg voor meer informatie hierover [De database maken en configureren](../../installation/using/creating-and-configuring-the-database.md).

   Als de database eenmaal is gemaakt, meldt u zich af.

1. Meld u weer aan bij de clientconsole met de **beheerder** aanmelden zonder wachtwoord en de wizard starten ( **[!UICONTROL Tools > Advanced]** (menu) om het configureren van de instantie te voltooien.

   Raadpleeg voor meer informatie hierover [Een instantie implementeren](../../installation/using/deploying-an-instance.md).

   De belangrijkste parameters die moeten worden ingesteld zijn:

   * E-maillevering: afzender en antwoordadressen en de foutenbrievenbus voor stuitende post.
   * Tekstspatiëring: Vul de externe URL voor omleiding en de interne URL in en klik op **Registratie op de trackingserver(s)** en vervolgens valideren op het tabblad **demo** instantie van de trackingserver.

      Raadpleeg voor meer informatie hierover [Configuratie bijhouden](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      Aangezien de Adobe Campaign-server zowel als de toepassingsserver als de omleidingsserver wordt gebruikt, is de interne URL die wordt gebruikt voor het verzamelen van trackinglogboeken en het overbrengen van URL&#39;s een directe interne verbinding met Tomcat (https://localhost:8080).

   * Stuitbeheer: Voer de parameters in voor het afhandelen van stuiterende e-mail (neem de parameter niet **Onverwerkte stuitberichten** rekening).
   * Toegang vanaf: Geef de twee URL&#39;s op voor rapporten, webformulieren en spiegel.

      ![](assets/d_ncs_install_web_url.png)
