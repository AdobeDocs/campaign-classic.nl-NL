---
solution: Campaign Classic
product: campaign
title: Standaardimplementatie
description: Standaardimplementatie
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---


# Standaardimplementatie{#standard-deployment}

Voor deze configuratie zijn drie computers vereist:

* Een toepassingsserver binnen LAN voor het eind - gebruikers (voorbereidend campagnes, rapportering, enz.),
* Twee frontale servers in DMZ achter een taakverdelingsmechanisme.

De twee servers in DMZ behandelen het volgen, spiegelen pagina&#39;s en levering en zijn overtollig voor hoge beschikbaarheid.

De toepassingsserver in LAN dient het eind - gebruikers en voert alle terugkomende processen (werkschemamotor) uit. Wanneer piekbelastingen op de frontservers worden bereikt, heeft dit dus geen gevolgen voor de gebruikers van de toepassing.

De databaseserver kan op een andere computer dan deze drie worden gehost. De toepassingsserver en de databaseserver kunnen anders dezelfde computer delen in het LAN, zolang het besturingssysteem wordt ondersteund door Adobe Campaign (Linux of Windows).

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

   * de eerste die aan het publiek wordt blootgesteld voor het volgen en aanwijzen van het taakverdelingsmechanisme op een virtueel IP adres (VIP) en die dan aan de twee frontale servers wordt verdeeld;
   * de tweede die aan de interne gebruikers voor toegang via de console wordt blootgesteld en aan de zelfde toepassingsserver richt.

* Firewall geconfigureerd voor het openen van STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 voor Oracle, 5432 voor PostgreSQL, enz.) poorten. Voor meer informatie, verwijs naar sectie [Toegang](../../installation/using/network-configuration.md#database-access)van het Gegevensbestand.

### De toepassingsserver installeren {#installing-the-application-server}

Voer de stappen uit om een zelfstandige instantie van de Adobe Campaign-toepassingsserver te installeren tot de database is gemaakt (stap 12). Zie [Installeren en configureren (enkele computer)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Aangezien de computer geen volgende server is, neem niet de integratie met de server van het Web in rekening.

In de volgende voorbeelden zijn de parameters van de instantie:

* Naam van de instantie: **demo**
* DNS-masker: **console.campagne.net*** (slechts voor de verbindingen van de cliëntconsole en voor rapporten)
* Taal: Engels
* Database: **campagne:demo@dbsrv**

### De twee frontservers installeren {#installing-the-two-frontal-servers}

De installatie en configuratieprocedure is identiek op beide computers.

De stappen zijn als volgt:

1. Installeer de Adobe Campaign-server.

   Raadpleeg voor meer informatie de [vereisten voor de installatie van Campagne in Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) en [de vereisten voor de installatie van Campagne in Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Volg de procedure van de de serverintegratie van het Web (IIS, Apache) in de volgende secties wordt beschreven die:

   * For Linux: [Integration into a Web server for Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * For Windows: [Integration into a Web server for Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

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

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. Koppel de database aan de instantie:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Schakel in de bestanden **config-default.xml** en **config-demo.xml** de modules **web**, **trackinglogd** en **mta** in.

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Bewerk het bestand **serverConf.xml** en vul het in:

   * de DNS-configuratie van de MTA-module:

      ```
      <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
      ```

      >[!NOTE]
      >
      >De parameter **nameServers** wordt alleen in Windows gebruikt.

      For more on this, refer to [Delivery settings](../../installation/using/campaign-server-configuration.md#delivery-settings).

   * de overtollige het volgen servers in de omleidingsparameters:

      ```
      <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
      <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
      ```

      For more on this, refer to [Redundant tracking](../../installation/using/configuring-campaign-server.md#redundant-tracking).

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

   * Voor Linux: [De server van het Web lanceren en de configuratie testen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Voor Windows: [De server van het Web lanceren en de configuratie testen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Start de Adobe Campaign-server.
1. Maak in de Adobe Campaign-console verbinding met de **beheerdersaanmelding** zonder wachtwoord en start de implementatietovenaar.

   Raadpleeg Een instantie [](../../installation/using/deploying-an-instance.md)implementeren voor meer informatie.

   De configuratie is identiek aan een standalone instantie behalve de configuratie van de volgende module.

1. Vul de externe URL (die van het taakverdelingsmechanisme) die wordt gebruikt voor omleiding en de interne URL&#39;s van de twee frontale servers.

   For more on this, refer to [Tracking configuration](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >We gebruiken de bestaande instantie van de twee eerder gemaakte trackingservers en gebruiken de **interne** aanmelding.

