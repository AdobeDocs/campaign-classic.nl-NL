---
title: Configuratie van de Campaign-server
seo-title: Configuratie van de Campaign-server
description: Configuratie van de Campaign-server
seo-description: null
page-status-flag: never-activated
uuid: a1fadad2-e888-4dd8-bc1f-04df16ba7d46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: f296676e-3bf1-47da-8239-f5ae54e52fc0
translation-type: tm+mt
source-git-commit: 3acf2359c74a3dc4b18c8976fee14dcbaf3fa510
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 2%

---


# Configuratie van de Campaign-server{#campaign-server-configuration}

In de volgende secties worden verplichte serverconfiguraties beschreven die de efficiënte werking van Adobe Campaign voor de meeste sets garanderen.

Er worden extra configuraties aangeboden in de [Campagneserver](../../installation/using/configuring-campaign-server.md)configureren.

>[!NOTE]
>
>Serverconfiguraties kunnen alleen worden uitgevoerd door Adobe voor implementaties die worden gehost door Adobe. Meer over de verschillende plaatsingen leren, verwijs naar de het [Ontvangen modelsectie](../../installation/using/hosting-models.md) of naar [de vermogensmatrijs](../../installation/using/capability-matrix.md).

## Interne id {#internal-identifier}

De **interne** identificatiecode is een technische aanmelding die voor installatie-, beheer- en onderhoudsdoeleinden moet worden gebruikt. Deze aanmelding is niet gekoppeld aan een instantie.

Operatoren die verbinding hebben met deze aanmelding, beschikken over alle rechten. Deze aanmelding heeft geen wachtwoord in het geval van een nieuwe installatie. U moet dit wachtwoord handmatig definiëren.

Gebruik de volgende opdracht:

```
nlserver config -internalpassword
```

De volgende informatie wordt dan getoond. Voer het wachtwoord in en bevestig het:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Configuratiebestanden {#configuration-files}

De configuratiebestanden worden opgeslagen in de map **conf** in de installatiemap van Adobe Campaign. De configuratie wordt verspreid over twee bestanden:

* **`config-<instance>.xml`** (waarbij de **instantie** de naam van de instantie is): specifieke configuratie van de instantie. Als u uw server onder verschillende exemplaren deelt, gelieve de parameters specifiek voor elke instantie in hun relevant dossier in te gaan.
* **serverConf.xml**: algemene configuratie voor alle instanties. In dit bestand worden de technische parameters van de Adobe Campaign-server gecombineerd: deze worden door alle instanties gedeeld . Hieronder wordt een beschrijving van een aantal van deze parameters gegeven. Raadpleeg het bestand zelf om alle beschikbare parameters weer te geven. De verschillende knooppunten en parameters en vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

U kunt de opslagdirectory (**var** directory) van Adobe Campaign-gegevens (logbestanden, downloads, omleidingen, enz.) configureren. Hiervoor gebruikt u de **systeemvariabele XTK_VAR_DIR** :

* Geef in Windows de volgende waarde op in de **systeemvariabele XTK_VAR_DIR**

   ```
   D:\log\AdobeCampaign
   ```

* Ga in Linux naar het bestand **customer.sh** en geef aan: **XTK_VAR_DIR=/app/log/AdobeCampaign** exporteren.

   For more on this, refer to [Personalizing parameters](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Processen inschakelen {#enabling-processes}

Adobe Campaign-processen op de server worden ingeschakeld (en uitgeschakeld) via **config-default.xml** en **`config-<instance>.xml`** bestanden.

Als u de wijzigingen op deze bestanden wilt toepassen en de Adobe Campaign-service is gestart, moet u de opdracht **nlserver config -reload** uitvoeren.

Er zijn twee soorten processen: meerdere instanties en één instantie.

* **meerdere instanties**: één proces is voor alle gevallen gestart . Dit geldt voor **web**-, **syslogd** - en **trackinglogd** -processen.

   Enablement kan van het **config-default.xml** - dossier worden gevormd.

   Adobe Campaign-server declareren voor toegang tot clientconsoles en voor omleiding (tracking):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   In dit voorbeeld wordt het bestand bewerkt met de opdracht **vi** in Linux. Deze kan worden bewerkt met elke **.txt** - of **.xml** -editor.

* **mono-instantie**: voor elke instantie wordt één proces gestart (modules: **mta**, **wfserver**, **inMail**, **sms** en **stat**).

   Enablement kan worden gevormd gebruikend het configuratiedossier van de instantie:

   ```
   config-<instance>.xml
   ```

   Een server declareren voor levering, workflowinstanties uitvoeren en stuiterende berichten herstellen:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## Afleveringsinstellingen {#delivery-settings}

De leveringsparameters moeten worden geconfigureerd in de map **serverConf.xml** .

* **DNS-configuratie**: specificeer het leveringsdomein en de IP adressen (of gastheer) van de DNS servers die worden gebruikt om aan MX-type DNS vragen te antwoorden die door de MTA module van **`<dnsconfig>`** vanaf worden gemaakt.

   >[!NOTE]
   >
   >De parameter **nameServers** is essentieel voor een installatie in Windows. Voor een installatie in Linux, moet het leeg worden verlaten.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

De andere leveringsparameters in dit bestand worden weergegeven in [leveringsparameters](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)aanpassen.

Raadpleeg ook de [e-mailleverbaarheid](../../installation/using/email-deliverability.md).
