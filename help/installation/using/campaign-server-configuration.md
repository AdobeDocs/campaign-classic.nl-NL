---
solution: Campaign Classic
product: campaign
title: Configuratie van de Campaign-server
description: Configuratie van de Campaign-server
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 1%

---


# Configuratie van de Campaign-server{#campaign-server-configuration}

In de volgende secties worden verplichte serverconfiguraties beschreven die de efficiënte werking van Adobe Campaign voor de meeste sets garanderen.

Aanvullende configuraties worden aangeboden in [Campagneserver configureren](../../installation/using/configuring-campaign-server.md).

>[!NOTE]
>
>Serverconfiguraties kunnen alleen worden uitgevoerd door Adobe voor implementaties die worden gehost door Adobe. Voor meer informatie over de verschillende plaatsingen, verwijs naar [Het ontvangen modellen](../../installation/using/hosting-models.md) sectie of aan [de capaciteitmatrijs](../../installation/using/capability-matrix.md).

## Interne id {#internal-identifier}

De **interne**-id is een technische aanmelding die moet worden gebruikt voor installatie-, beheer- en onderhoudsdoeleinden. Deze aanmelding is niet gekoppeld aan een instantie.

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

De configuratiebestanden worden opgeslagen in de map **conf** van de installatiemap van Adobe Campaign. De configuratie wordt verspreid over twee bestanden:

* **`config-<instance>.xml`** (waarbij  **** instantie de naam van de instantie is): specifieke configuratie van de instantie. Als u uw server onder verschillende exemplaren deelt, gelieve de parameters specifiek voor elk geval in hun relevant dossier in te gaan.
* **serverConf.xml**: algemene configuratie voor alle instanties. In dit bestand worden de technische parameters van de Adobe Campaign-server gecombineerd: deze worden door alle instanties gedeeld . Hieronder wordt een beschrijving van een aantal van deze parameters gegeven. Raadpleeg het bestand zelf om alle beschikbare parameters weer te geven. De verschillende knooppunten en parameters en vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

U kunt de opslagdirectory (**var** directory) van Adobe Campaign-gegevens (logbestanden, downloads, omleidingen, enz.) configureren. Hiervoor gebruikt u de systeemvariabele **XTK_VAR_DIR**:

* Geef in Windows de volgende waarde op in de systeemvariabele **XTK_VAR_DIR**

   ```
   D:\log\AdobeCampaign
   ```

* Ga in Linux naar het bestand **customer.sh** en geef aan: **exporteer XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Raadpleeg [Parameters aanpassen](../../installation/using/installing-packages-with-linux.md#personalizing-parameters) voor meer informatie.

## Bezig met inschakelen van processen {#enabling-processes}

Adobe Campaign-processen op de server worden ingeschakeld (en uitgeschakeld) via de bestanden **config-default.xml** en **`config-<instance>.xml`**.

Als u de wijzigingen op deze bestanden wilt toepassen en de Adobe Campaign-service is gestart, moet u de opdracht **nlserver config -reload** uitvoeren.

Er zijn twee soorten processen: meerdere instanties en één instantie.

* **meerdere instanties**: één proces is voor alle gevallen gestart . Dit is het geval voor **web**, **syslogd** en **trackinglogd** processen.

   Enablement kan van het **config-default.xml** dossier worden gevormd.

   Adobe Campaign-server declareren voor toegang tot clientconsoles en voor omleiding (tracking):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   In dit voorbeeld wordt het bestand bewerkt met de opdracht **vi** in Linux. Het kan worden uitgegeven gebruikend om het even welke **.txt** of **.xml** redacteur.

* **mono-instantie**: voor elke instantie wordt één proces gestart (modules:  **mta**,  **wfserver**,  **inMail**,  **** smand  **stat**).

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

De leveringsparameters moeten worden geconfigureerd in de map **serverConf.xml**.

* **DNS-configuratie**: specificeer het leveringsdomein en de IP adressen (of gastheer) van de DNS servers die worden gebruikt om aan MX-type DNS vragen te antwoorden die door de MTA module van de  **`<dnsconfig>`** vanaf worden gemaakt.

   >[!NOTE]
   >
   >De **nameServers** parameter is essentieel voor een installatie in Vensters. Voor een installatie in Linux, moet het leeg worden verlaten.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

De andere leveringsparameters in dit bestand worden weergegeven in [Leveringsparameters aanpassen](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

Raadpleeg ook [E-mailleverbaarbaarheid](../../installation/using/email-deliverability.md).
