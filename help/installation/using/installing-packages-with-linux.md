---
product: campaign
title: Pakketten installeren met Linux
description: Pakketten installeren met Linux
feature: Installation, Application Settings
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: 1ab08a89b17fca20e9497696417ecba580e26802
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Pakketten installeren met Linux{#installing-packages-with-linux}

Adobe Campaign komt met het **pakket 0} nlserver {dat de binaire getallen en configuratiedossiers voor een bepaalde versie bevat.**



Met de installatieopdrachten kunt u:

* De bestanden kopiëren naar **/usr/local/neolane**
* Maak een Adobe Campaign Linux-account (en de bijbehorende groep), die wordt gemaakt met **/usr/local/neolane** als de thuismap
* Creeer een automatisch manuscript **/etc/init.d/nlserver6** voor gebruik bij opstarten, of creeer een systeemeenheid

>[!NOTE]
>
>De **neolane** systeemgebruiker moet niet gecreeerd zijn alvorens het bevel werd in werking gesteld. De **neolane** gebruiker wordt gecreeerd automatisch tijdens installatie.
>
>De **huis** folder verbonden aan de **neolane** gebruiker wordt ook gecreeerd automatisch in **[!UICONTROL /usr/local/neolane]**. Controleer of er voldoende ruimte beschikbaar is op de **[!UICONTROL /usr/local]** -schijf.

U kunt **in werking stellen pingelen`hostname`** bevel om ervoor te zorgen de server zich kan bereiken.

## Distributie op basis van RPM-pakketten {#distribution-based-on-rpm--packages}

>[!AVAILABILITY]
>
>Vanaf versie 7.4.1 worden bibliotheken voor RPM Linux-pakketten niet meer opgenomen in de campagne. U moet deze bibliotheken installeren.
> 

Voer de volgende stappen uit om Adobe Campaign op een RPM-besturingssysteem (RHEL, CentOS) te installeren:

1. Get the Adobe Campaign package. De naam van het dossier is **nlserver6-v7-XXXX-0.x86_64.rpm**, waar **XXXX** het Adobe Campaign bouwstijlaantal is.

   >[!CAUTION]
   >
   >Gebruik de juiste bestandsnaam voor uw versie van Adobe Campaign in de opdrachtvoorbeelden van deze sectie.

1. Om het te installeren, verbind als **wortel** en voer het volgende bevel uit, waar **XXXX** het Adobe Campaign bouwstijlaantal is:

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   Het rpm-bestand is afhankelijk van pakketten die u kunt vinden op CentOS/Red Hat-distributies. Als u sommige van deze gebiedsdelen niet wilt gebruiken (bijvoorbeeld, als u Oracle JDK in plaats van OpenJDK wilt gebruiken), kunt u de &quot;nodeps&quot;optie van rpm moeten gebruiken:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Het `bc` bevel, verplicht voor het uitvoeren van [ netreport ](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts), is niet beschikbaar door gebrek op alle distributies van Linux. Als u wilt controleren of de opdracht beschikbaar is, voert u de opdracht `which bc` uit. Als dat niet het geval is, moet u het installeren.

Met CentOS, moet u het pakket installeren bc.x86_64: verbind als **wortel** en stel het volgende bevel in werking:

```
yum install bc.x86_64
```

## Distributie op basis van APT (Debian) {#distribution-based-on-apt--debian-}

Voer de volgende stappen uit om Adobe Campaign op een Debian 64-bits besturingssysteem te installeren:

1. Get the Adobe Campaign package. De naam van het dossier is **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, waar **** het Adobe Campaign bouwstijlaantal is.

   >[!CAUTION]
   >
   >Gebruik de juiste bestandsnaam voor uw versie van Adobe Campaign in de opdrachtvoorbeelden van deze sectie.

1. Om het te installeren, verbind als **wortel** en voer het volgende bevel uit, waar **XXXX** het Adobe Campaign bouwstijlaantal is:

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   Als er ontbrekende gebiedsdelen zijn, stel het volgende bevel in werking:

   ```
   apt-get install -f
   ```


1. Houd rekening met het volgende wanneer u Adobe Campaign op een Debian-besturingssysteem installeert:

* OpenSSL moet vooraf zijn geïnstalleerd.
* Installeer libicu en libc-aresYY, waarbij XX de versie is, met de volgende opdrachten:

  ```
  apt install libicuXX
  ```

  ```
  apt install libc-aresXX
  ```

  ```
  apt install openjdk-XX-jdk
  ```

## Parameters aanpassen {#personalizing-parameters}

Sommige parameters kunnen via het {**dossier worden gepersonaliseerd 0} customer.sh**

Als u de installatie voor het eerst uitvoert, zou het {**dossier 0} customer.sh nog niet op de server kunnen bestaan.**

Maak het bestand en zorg ervoor dat het uitvoeringsrechten heeft. Als dit niet het geval is, ga het volgende bevel in:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Servercodering {#server-encoding}

Standaard wordt de server gestart in een iso8859-15-omgeving. De server kan echter wel in een UTF-8-omgeving worden gestart.

>[!CAUTION]
>
>Deze wijziging is van invloed op de interactie met het bestandssysteem (bestanden die via een workflow of een JavaScript-script zijn geladen) en op de bestandscodering. Daarom raden we u aan de standaardomgeving te gebruiken.

Om a **Japanse instantie** tot stand te brengen, moet u een milieu UTF-8 gebruiken.

Gebruik de volgende opdracht om de UTF-8-omgeving in te schakelen:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Omgevingsvariabelen {#environment-variables}

De volgende omgevingsvariabelen moeten correct worden gedefinieerd.

Bepaalde combinaties vereisen wijzigingen in de omgeving die wordt gebruikt voor het uitvoeren van Adobe Campaign. Een specifiek dossier (`/usr/local/neolane/nl6/customer.sh`) kan worden gecreeerd en worden uitgegeven om wijzigingen toe te voegen specifiek voor de milieu van Adobe Campaign.

Indien noodzakelijk, geef het {**dossier 0} customer.sh uit gebruikend het {** bevel 2} vi customer.sh en pas de configuratie aan of voeg ontbrekende lijnen toe:****

* Voor de client Oracle:

  ```
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  De inhoud van de omgevingsvariabele ORACLE_HOME komt overeen met de installatiemap van het Oracle.

  De inhoud van de variabele TNS_ADMIN moet de plaats van het {**dossier aanpassen 0} tnsnames.ora.**

* Voor LibreOffice:

  Voor het uitvoeren van Adobe Campaign op een bestaande versie van LibreOffice zijn aanvullende configuraties vereist: u moet de toegangspaden naar de installatiemap opgeven. Bijvoorbeeld:

   * Debian

     De standaardwaarden voor OO_INSTALL_DIR en OOO_BASIS_INSTALL_DIR worden verstrekt. U kunt hen in **met voeten treden customer.sh** als uw lay-out van de installatie LibreOffice verschillend is:

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
     export OOO_INSTALL_DIR=/usr/lib/libreoffice/
     ```

   * CentOs

     Gebruik de volgende standaardwaarden:

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
     export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
     ```

* Voor Java Development Kit (JDK):

  Door gebrek, zoekt het configuratiescript van het milieu van Adobe Campaign (`~/nl6/env.sh`) naar de JDK installatiemap. Het wordt echter aanbevolen aan te geven welke JDK moet worden gebruikt. Om dit te doen, kunt u **JDK_HOME** milieuvariabele dwingen gebruikend het volgende bevel:

  ```
  export JDK_HOME=/usr/java/jdkX.Y.Z
  ```

  >[!NOTE]
  >
  >Zorg ervoor dat de gebruikte JDK-versie overeenkomt met de mapnaam.

  Als u de JDK-configuratie wilt testen, meldt u zich aan als de Adobe Campaign-systeemgebruiker met de volgende opdracht:

  ```
  su - neolane
  ```

U moet de Adobe Campaign-service opnieuw starten om rekening te houden met de wijzigingen.

De opdrachten zijn als volgt:

```
systemctl stop nlserver
systemctl start nlserver
```

### Oracle Client in Linux {#oracle-client-in-linux}

Als u Oracle gebruikt met Adobe Campaign, moet u de clientlagen van het Oracle configureren in Linux.

* De volledige client gebruiken
* TNS-definitie

  De TNS-definities moeten tijdens de installatiefase worden toegevoegd. Hiervoor gebruikt u de volgende opdrachten:

  ```
  cd /etc
  mkdir oracle
  cd oracle
  vi tnsnames.ora
  ```

* Omgevingsvariabelen

  Verwijs naar [ variabelen van het Milieu ](#environment-variables).

* Configuratie voor Adobe Campaign

  Om de installatie van de cliënt van het Oracle voor Adobe Campaign te voltooien, moet u een symbolische verbinding voor het **.so** dossier tot stand brengen dat door Adobe Campaign wordt gebruikt.

  Hiervoor gebruikt u de volgende opdrachten:

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

Zorg ervoor dat de pakketten die in de installatiedocumentatie van het Oracle worden vermeld, in het geval van een probleem correct zijn geïnstalleerd.

## Installatiecontroles {#installation-checks}

U kunt nu een eerste installatietest uitvoeren met de volgende opdrachten:

```
su - neolane
nlserver pdump
```

Wanneer Adobe Campaign niet wordt gestart, wordt het volgende antwoord gegeven:

```
no task
```

## Eerste start van de server {#first-start-up-of-the-server}

Zodra de installatietest volledig is, ga het volgende bevel in:

```
nlserver web
```

De volgende informatie wordt dan getoond:

```sql
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Deze bevelen laten u **config-default.xml** en **serverConf.xml** configuratiedossiers tot stand brengen. Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [ sectie ](../../installation/using/the-server-configuration-file.md).

Pers **Ctrl+C** om het proces tegen te houden, dan het volgende bevel in te gaan:

```
nlserver start web
```

De volgende informatie wordt dan getoond:

```sql
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Als u het wilt stoppen, voert u in:

```
nlserver stop web
```

De volgende informatie wordt dan getoond:

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Wachtwoord voor de interne id {#password-for-the-internal-identifier}

De server van Adobe Campaign bepaalt technische login genoemd **intern** die alle rechten op alle instanties heeft. Vlak na de installatie heeft de aanmelding geen wachtwoord. Het is verplicht om er een te definiëren.

Lees meer in [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier).
