---
title: Standaardimplementatie
seo-title: Standaardimplementatie
description: Standaardimplementatie
seo-description: null
page-status-flag: never-activated
uuid: e2f9c4d9-4b36-4899-9954-493135597057
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: d714b759-cc08-4656-876c-9820d5c56216
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Standaardimplementatie{#standard-deployment}

Voor deze configuratie zijn drie computers vereist:

* Een toepassingsserver binnen LAN voor het eind - gebruikers (voorbereidend campagnes, rapportering, enz.),
* Twee frontale servers in DMZ achter een taakverdelingsmechanisme.

De twee servers in DMZ behandelen het volgen, spiegelen pagina&#39;s en levering en zijn overtollig voor hoge beschikbaarheid.

De toepassingsserver in LAN dient het eind - gebruikers en voert alle terugkomende processen (werkschemamotor) uit. Wanneer piekbelastingen op de frontservers worden bereikt, heeft dit dus geen gevolgen voor de gebruikers van de toepassing.

De databaseserver kan op een andere computer dan deze drie worden gehost. De toepassingsserver en de databaseserver kunnen anders dezelfde computer delen in het LAN, zolang het besturingssysteem wordt ondersteund door Adobe Campagne (Linux of Windows).

De algemene communicatie tussen servers en processen wordt uitgevoerd volgens het volgende schema:

![](assets/s_001_ncs_install_standardconfig.png)

Dit type van configuratie kan een groot aantal ontvangers (500.000 tot 1.000.000) behandelen aangezien de gegevensbestandserver (en de beschikbare bandbreedte) de belangrijkste beperkende factor is.

## Functies {#features}

### Voordelen {#advantages}

* Failover-functionaliteit: de mogelijkheid om processen naar de ene computer te schakelen in het geval van een hardwareprobleem aan de andere.
* Betere algemene prestaties, aangezien de MTA en redirection functies op beide computers achter een taakverdelingsmechanisme kunnen worden opgesteld. Met twee actieve MTAs en genoeg bandbreedte, is het mogelijk om uitzendingstarieven in het gebied van 100.000 post per uur te bereiken.

## Installatie- en configuratiestappen {#installation-and-configuration-steps}

### Vereisten {#prerequisites}

* JDK op alle drie computers,
* Webserver (IIS, Apache) op beide fronten,
* Toegang tot een databaseserver op alle drie de computers,
* Bounce mailbox toegankelijk via POP3,
* Maken van twee DNS-aliassen:

   * de eerste die aan het publiek voor het volgen van en het richten aan het taakverdelingsmechanisme op een virtueel IP adres (VIP) wordt blootgesteld en die dan aan de twee frontale servers wordt verdeeld;
   * de tweede die aan de interne gebruikers voor toegang via de console wordt blootgesteld en aan de zelfde toepassingsserver richt.

* Firewall geconfigureerd voor het openen van STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 voor Oracle, 5432 voor PostgreSQL, enz.) poorten. Voor meer informatie, verwijs naar sectie [Toegang](../../installation/using/network-configuration.md#database-access)van het Gegevensbestand.

### De toepassingsserver installeren {#installing-the-application-server}

Voer de stappen uit om een zelfstandige instantie van de Adobe Campagne-toepassingsserver te installeren tot de database is gemaakt (stap 12). Zie [Installeren en configureren (enkele computer)](#installing-and-configuring--single-machine-).

Aangezien de computer geen volgende server is, neem niet de integratie met de server van het Web in rekening.

In de volgende voorbeelden zijn de parameters van de instantie:

* Naam van de instantie: **demo**
* DNS-masker: **console.campagne.net*** (slechts voor de verbindingen van de cliëntconsole en voor rapporten)
* Taal: Engels
* Database: **campagne:demo@dbsrv**

### De twee frontservers installeren {#installing-the-two-frontal-servers}

De installatie en configuratieprocedure is identiek op beide computers.

De stappen zijn als volgt:

1. Installeer de Adobe Campagneserver.

   Raadpleeg voor meer informatie de [vereisten voor de installatie van Campagne in Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) en [de vereisten voor de installatie van Campagne in Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Volg de procedure van de de serverintegratie van het Web (IIS, Apache) in de volgende secties wordt beschreven die:

   * Voor Linux: [Integratie in een webserver voor Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Voor Windows: [Integratie in een server van het Web voor Vensters](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Maak de **demo** -instantie. Er zijn twee manieren om dit te doen:

   * Maak de instantie via de console:

      ![](assets/install_create_new_connexion.png)

      Raadpleeg [Een instantie maken en aanmelden](../../installation/using/creating-an-instance-and-logging-on.md)voor meer informatie hierover.

      of

   * Maak de instantie met behulp van opdrachtregels:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*
      ```

      Raadpleeg [Een instantie](../../installation/using/command-lines.md#creating-an-instance)maken voor meer informatie hierover.
   De naam van de instantie is gelijk aan die van de toepassingsserver.

   De verbinding met de server met de **webmodule** van de server (mirror pages, unsubscription) wordt tot stand gebracht via de URL van het taakverdelingsmechanisme (tracking.campagne.net).

1. Verander **intern** in het zelfde als de toepassingsserver.

   Raadpleeg de [interne id](../../installation/using/campaign-server-configuration.md#internal-identifier)voor meer informatie hierover.

1. Koppel de database aan de instantie:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Schakel in de bestanden **config-default.xml** en **config-demo.xml** de modules **web**, **trackinglogd** en **mta** in.

   Raadpleeg [Processen](../../installation/using/campaign-server-configuration.md#enabling-processes)inschakelen voor meer informatie.

1. Bewerk het bestand **serverConf.xml** en vul het in:

   * de DNS-configuratie van de MTA-module:

      ```
      <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
      ```

      >[!NOTE]
      >
      >De parameter **nameServers** wordt alleen in Windows gebruikt.

      Raadpleeg de [leveringsinstellingen](../../installation/using/campaign-server-configuration.md#delivery-settings)voor meer informatie.

   * de overtollige het volgen servers in de omleidingsparameters:

      ```
      <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
      <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
      ```

      Raadpleeg [Overbodige reeksspatiëring](../../installation/using/configuring-campaign-server.md#redundant-tracking)voor meer informatie.

1. Start de website en test de omleiding via de URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   De browser moet de volgende berichten weergeven (afhankelijk van de URL die door het taakverdelingsmechanisme is omgeleid):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   of

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Raadpleeg de volgende secties voor meer informatie hierover:

   * Voor Linux: De server van het Web [lanceren en de configuratie testen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Voor Windows: De server van het Web [lanceren en de configuratie testen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Start de Adobe Campagneserver.
1. Maak in de Adobe Campaign-console verbinding met de **beheerdersaanmelding** zonder wachtwoord en start de implementatietovenaar.

   Raadpleeg Een instantie [](../../installation/using/deploying-an-instance.md)implementeren voor meer informatie.

   De configuratie is identiek aan een standalone instantie behalve de configuratie van de volgende module.

1. Vul de externe URL (die van het taakverdelingsmechanisme) die wordt gebruikt voor omleiding en de interne URL&#39;s van de twee frontale servers.

   Voor meer op dit, verwijs naar het [Volgen configuratie](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >We gebruiken de bestaande instantie van de twee eerder gemaakte trackingservers en gebruiken de **interne** aanmelding.

