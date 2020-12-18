---
solution: Campaign Classic
product: campaign
title: De server installeren
description: De server installeren
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 2%

---


# De server installeren{#installing-the-server}

## Installatieprogramma {#executing-the-installation-program} uitvoeren

Installeer Adobe Campaign 32-bits voor een Windows 32-bits platform. Installeer Adobe Campaign 64-bits voor een Windows 64-bits platform.

De installatiestappen voor de Adobe Campaign-server zijn als volgt:

1. Voer het bestand **setup.exe** uit.

   ![](assets/s_ncs_install_installer_01.png)

1. Selecteer het installatietype.

   ![](assets/s_ncs_install_installer_01a.png)

   Er zijn verschillende installatietypen beschikbaar:

   * **[!UICONTROL Installation of an application server]** : Installeer de Adobe Campaign-toepassingsserver en de clientconsole.
   * **[!UICONTROL Minimal installation (Network)]** : Installatie van de clientcomputer vanaf het netwerk. Slechts zal een beperkt aantal DLLs op de computer, indien nodig worden geïnstalleerd, en alle andere componenten zullen van een netwerkaandrijving worden gebruikt.
   * **[!UICONTROL Installation of a client]** : Installatie van de vereiste componenten voor de Adobe Campaign-client.
   * **[!UICONTROL Custom installation]** : De gebruiker kiest de te installeren elementen.

   Selecteer **Installatie van een toepassingsserver** en doorloop de verschillende stappen zoals hieronder getoond:

   ![](assets/s_ncs_install_installer_02.png)

1. Selecteer de installatiemap:

   ![](assets/s_ncs_install_installer_03.png)

1. Klik **[!UICONTROL Finish]** om de installatie te starten:

   ![](assets/s_ncs_install_installer_04.png)

   De voortgangsbalk laat zien hoe ver de installatie is:

   ![](assets/s_ncs_install_installer_05.png)

   Nadat de installatie is voltooid, verschijnt er een bericht om u op de hoogte te stellen van:

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >Wanneer de serverinstallatie is voltooid, moet de server opnieuw worden opgestart om mogelijke netwerkproblemen te voorkomen.

   Als de installatie is voltooid, start u Adobe Campaign om de configuratiebestanden te maken. Zie [Eerste start van de server](#first-start-up-of-the-server).

## Samenvattende installatietest {#summary-installation-testing}

U kunt de eerste installatie testen met de volgende opdracht:

```
nlserver pdump
```

Als Adobe Campaign niet wordt gestart, is het antwoord:

```
No task
```

## Eerste start van de server {#first-start-up-of-the-server}

Nadat de installatietest is voltooid, opent u een opdrachtregel via het menu **[!UICONTROL Start > Programs > Adobe Campaign]** en voert u de volgende opdracht in:

```
nlserver web
```

![](assets/s_ncs_install_cmd_nlserverweb.png)

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

Druk op **Ctrl+C** om het proces te stoppen en voer vervolgens de volgende opdracht in:

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

De Adobe Campaign-server definieert een technische aanmelding met de naam **internal** die alle rechten heeft op alle instanties. Vlak na de installatie heeft de aanmelding geen wachtwoord. Het is verplicht om er een te definiëren.

Zie sectie [Interne id](../../installation/using/campaign-server-configuration.md#internal-identifier).

## Adobe Campaign-services {#starting-adobe-campaign-services} starten

Om de diensten van Adobe Campaign te beginnen, kunt u de de dienstmanager gebruiken of het volgende bij de bevellijn (met de aangewezen rechten) ingaan:

```
net start nlserver6
```

Als u de processen van Adobe Campaign later moet tegenhouden, gebruik het bevel:

```
net stop nlserver6
```

## LibreOffice {#installing-libreoffice} installeren

Download LibreOffice, bijvoorbeeld via [https://www.libreoffice.org/download/libreoffice-fresh/](https://www.libreoffice.org/download/libreoffice-fresh/) en volg de gebruikelijke installatiestappen.

Voeg de volgende omgevingsvariabele toe:

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```

