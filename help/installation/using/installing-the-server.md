---
product: campaign
title: De server installeren
description: De server installeren
feature: Installation, Instance Settings
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---

# De server installeren{#installing-the-server}



## Het installatieprogramma uitvoeren {#executing-the-installation-program}

Installeer Adobe Campaign 32-bits voor een Windows 32-bits platform. Installeer Adobe Campaign 64-bits voor een Windows 64-bits platform.

De installatiestappen voor de Adobe Campaign-server zijn als volgt:

1. Het bestand uitvoeren **setup.exe**.

   ![](assets/s_ncs_install_installer_01.png)

1. Selecteer het installatietype.

   ![](assets/s_ncs_install_installer_01a.png)

   Er zijn verschillende installatietypen beschikbaar:

   * **[!UICONTROL Installation of an application server]** : Installeer de Adobe Campaign-toepassingsserver en de clientconsole.
   * **[!UICONTROL Minimal installation (Network)]** : Installatie van de clientcomputer vanaf het netwerk. Slechts zal een beperkt aantal DLLs op de computer, indien nodig worden geïnstalleerd, en alle andere componenten zullen van een netwerkaandrijving worden gebruikt.
   * **[!UICONTROL Installation of a client]** : Installatie van de vereiste componenten voor de Adobe Campaign-client.
   * **[!UICONTROL Custom installation]** : De gebruiker kiest de te installeren elementen.

   Selecteren **Installatie van een toepassingsserver** en doorloop de verschillende stappen zoals hieronder aangegeven:

   ![](assets/s_ncs_install_installer_02.png)

1. Selecteer de installatiemap:

   ![](assets/s_ncs_install_installer_03.png)

1. Klikken **[!UICONTROL Finish]** de installatie starten:

   ![](assets/s_ncs_install_installer_04.png)

   De voortgangsbalk laat zien hoe ver de installatie is:

   ![](assets/s_ncs_install_installer_05.png)

   Nadat de installatie is voltooid, verschijnt er een bericht om u op de hoogte te stellen van:

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >Wanneer de serverinstallatie is voltooid, moet de server opnieuw worden opgestart om mogelijke netwerkproblemen te voorkomen.

   Als de installatie is voltooid, start u Adobe Campaign om de configuratiebestanden te maken. Zie [Eerste start van de server](#first-start-up-of-the-server).

## Samenvattende installatietests {#summary-installation-testing}

U kunt de eerste installatie testen met de volgende opdracht:

```
nlserver pdump
```

Als Adobe Campaign niet wordt gestart, is het antwoord:

```
No task
```

## Eerste start van de server {#first-start-up-of-the-server}

Zodra de installatietest volledig is, open een bevelherinnering via **[!UICONTROL Start > Programs > Adobe Campaign]** en voert u de volgende opdracht in:

```
nlserver web
```

De bestanden in de installatiemap worden gebruikt om de Adobe Campaign-servermodules te configureren.

De volgende informatie wordt weergegeven:

```
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

Druk **Ctrl+C** om het proces tegen te houden, dan ga het volgende bevel in:

```
nlserver start web
```

De volgende informatie wordt weergegeven:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Als u het wilt stoppen, voert u in:

```
nlserver stop web
```

De volgende informatie wordt weergegeven:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Wachtwoord voor de interne id {#password-for-the-internal-identifier}

De Adobe Campaign-server definieert een technische aanmeldingsnaam **internal** dat heeft alle rechten . Vlak na de installatie heeft de aanmelding geen wachtwoord. Het is verplicht om er een te definiëren.

Lees meer in [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier).

## Adobe Campaign-services starten {#starting-adobe-campaign-services}

Om de diensten van Adobe Campaign te beginnen, kunt u de de dienstmanager gebruiken of het volgende bij de bevellijn (met de aangewezen rechten) ingaan:

```
net start nlserver6
```

Als u de processen van Adobe Campaign later moet tegenhouden, gebruik het bevel:

```
net stop nlserver6
```

## LibreOffice installeren {#installing-libreoffice}

Download LibreOffice en volg de gebruikelijke installatiestappen.

Voeg de volgende omgevingsvariabele toe:

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```
