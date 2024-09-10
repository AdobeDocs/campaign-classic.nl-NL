---
product: campaign
title: Zelfstandige implementatie
description: Zelfstandige implementatie
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 2%

---

# Zelfstandige implementatie{#standalone-deployment}



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
* PostSQL,
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

* Firewall geconfigureerd voor het openen van SMTP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 voor Oracle, 5432 voor PostSQL, enz.) poorten. Voor verdere informatie, verwijs naar [ configuratie van het Netwerk ](../../installation/using/network-configuration.md).

In de volgende voorbeelden zijn de parameters van de instantie:

* Naam van de instantie: **demo**
* DNS masker: **console.campagne.net&#42;** (slechts voor de verbindingen van de cliëntconsole en voor rapporten)
* Database: **campagne:demo@dbsrv**

### Installeren en configureren (één computer) {#installing-and-configuring--single-machine-}

Voer de volgende stappen uit:

1. Volg de installatieprocedure voor de server van Adobe Campaign: **nlserver** pakket op Linux of **setup.exe** op Vensters.

   Voor meer op dit, verwijs naar [ Eerste vereisten van de installatie van de Campagne in Linux ](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) en [ Eerste vereisten van de installatie van de Campagne in Vensters ](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Vensters).

1. Zodra de server van Adobe Campaign wordt geïnstalleerd, begin de toepassingsserver (Web) gebruikend het bevel **nlserver web -tomcat** (de module van het Web laat u toe om Tomcat op standalone de serverwijze van het Web te beginnen luisterend op haven 8080) en ervoor te zorgen begint Tomcat correct:

   ```sql
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >De eerste keer wordt de module van het Web uitgevoerd het leidt tot de {**en** serverConf.xml **dossiers in de** conf **folder onder de installatiemap.** Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [ sectie ](../../installation/using/the-server-configuration-file.md).

   Pers **Ctrl+C** om de server tegen te houden.

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: [ Eerste begin-up van de server ](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Voor Vensters: [ Eerste opstarten van de server ](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. Verander het **interne** wachtwoord gebruikend het bevel:

   ```
   nlserver config -internalpassword
   ```

   Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) voor meer informatie.

1. Creeer de **demo** instantie met de DNS maskers voor het volgen (in dit geval, **tracking.campagne.net**) en toegang tot cliëntconsoles (in dit geval, **console.campagne.net**). Er zijn twee manieren om dit te doen:

   * Maak de instantie via de console:

     ![](assets/install_create_new_connexion.png)

     Voor meer op dit, verwijs naar [ creeer een geval en login ](../../installation/using/creating-an-instance-and-logging-on.md).

     of

   * Maak de instantie met behulp van opdrachtregels:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     Voor meer op dit, verwijs naar [ Creërend een instantie ](../../installation/using/command-lines.md#creating-an-instance).

1. Bewerk het {**dossier 0} config-demo.xml (dat in de vorige stap naast** wordt gecreeerd config-default.xml **) en zorg de** mta **(levering),** wfserver **(werkschema),** inMail **(stuiterende berichten) en** staat **(statistieken) processen worden toegelaten.** Dan vorm het adres van de statistiekserver:

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

1. Bewerk het {**dossier 0} serverConf.xml en specificeer het leveringsdomein, dan specificeer IP (of gastheer) adressen van de DNS servers die door de MTA module worden gebruikt om MX type DNS vragen te beantwoorden.**

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >De **nameServers** parameter wordt slechts gebruikt in Vensters.

   Voor meer op dit, verwijs naar [ de serverconfiguratie van de Campagne ](../../installation/using/configuring-campaign-server.md).

1. Kopieer het de opstellingsprogramma van de cliëntconsole **opstelling-cliënt-7.XXX.exe** aan de **/datakit/nl/eng/jsp** omslag. [Meer informatie](../../installation/using/client-console-availability-for-windows.md).

1. Volg de procedure van de de serverintegratie van het Web (IIS, Apache) in de volgende secties wordt beschreven die:

   * Voor Linux: [ Integratie in een server van het Web voor Linux ](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Voor Vensters: [ Integratie in een server van het Web voor Vensters ](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Start de website en test omleiding met de URL: https://tracking.campaign.net/r/test.

   De browser moet het volgende bericht weergeven:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: [ lanceert de server van het Web en het testen van de configuratie ](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Voor Vensters: [ lanceert de server van het Web en het testen van de configuratie ](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Begin de server van Adobe Campaign (**netto begin nlserver6** in Vensters, **/etc/init.d/nlserver6 begin** in Linux) en stel het bevel **in werking nlserver pomp** opnieuw om aanwezigheid van alle toegelaten modules te controleren.

   >[!NOTE]
   >
   >Beginnend 20.1, adviseren wij het gebruiken van het volgende bevel in plaats daarvan (voor Linux): **systeemctl begin nlserver**

   ```sql
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

1. Test de **module van het 0} nlserverWeb {die URL gebruikt: https://console.campaign.net/nl/jsp/logon.jsp**

   Met deze URL hebt u toegang tot de downloadpagina voor het installatieprogramma van de client.

   Ga **interne** login en geassocieerd wachtwoord in wanneer u de pagina van de toegangscontrole bereikt. [Meer informatie](../../installation/using/client-console-availability-for-windows.md).

   ![](assets/s_ncs_install_access_client.png)

1. Begin de de cliëntconsole van Adobe Campaign (van de vorige downloadpagina of direct gelanceerd op de server voor een installatie van Vensters), plaats de server verbinding URL aan https://console.campaign.net en verbindt gebruikend **interne** login.

   Verwijs naar [ deze pagina ](../../installation/using/creating-an-instance-and-logging-on.md) en [ deze sectie ](../../installation/using/configuring-campaign-server.md#internal-identifier).

   De assistent voor het maken van de database wordt weergegeven wanneer u zich voor het eerst aanmeldt:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Volg de stappen in de medewerker en creeer het gegevensbestand verbonden aan de verbindingsinstantie.

   Voor meer op dit, verwijs naar [ Creërend en vormend het gegevensbestand ](../../installation/using/creating-and-configuring-the-database.md).

   Als de database eenmaal is gemaakt, meldt u zich af.

1. Logterug op de cliëntconsole gebruikend **admin** login zonder een wachtwoord en begin de plaatsingstovenaar ( **[!UICONTROL Tools > Advanced]** menu) om het vormen van de instantie te beëindigen.

   Voor meer op dit, verwijs naar [ het Opstellen van een instantie ](../../installation/using/deploying-an-instance.md).

   De belangrijkste parameters die moeten worden ingesteld zijn:

   * E-maillevering: verzender- en antwoordadressen en de foutbrievenbus voor stuiterende berichten.
   * Het volgen: Vul externe URL die voor redirection en interne URL wordt gebruikt, klik **Registratie op de volgende server(s)** en bevestig het dan op de **demo** instantie van de volgende server.

     Voor meer op dit, verwijs naar [ het Volgen configuratie ](../../installation/using/deploying-an-instance.md#tracking-configuration).

     ![](assets/s_ncs_install_deployment_wiz_09.png)

     Aangezien de Adobe Campaign-server zowel als de toepassingsserver als de omleidingsserver wordt gebruikt, is de interne URL die wordt gebruikt voor het verzamelen van trackinglogboeken en het overbrengen van URL&#39;s een directe interne verbinding met Tomcat (https://localhost:8080).

   * Stuitbeheer: Ga de parameters in om stuiterende post te behandelen (neem niet de **Onverwerkte stuitpost** sectie in rekening).
   * Toegang van: Geef twee URL&#39;s op voor rapporten, webformulieren en spiegel.

     ![](assets/d_ncs_install_web_url.png)
