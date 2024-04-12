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
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---

# Pakketten installeren met Linux{#installing-packages-with-linux}



Installeer Adobe Campaign 32-bits voor een Linux 32-bits platform. Installeer Adobe Campaign 64-bits voor een Linux 64-bits platform.

Voor elk van deze versies wordt in Adobe Campaign één pakket geleverd: **nlserver**. Dit pakket bevat de binaire bestanden en configuratiebestanden voor een bepaalde versie.

Met de installatieopdrachten kunt u:

* Bestanden kopiëren naar **/usr/local/neolane**
* Een Adobe Campaign Linux-account maken (en de bijbehorende groep) die is gemaakt met **/usr/local/neolane** als thuismap
* Een automatisch script maken **/etc/init.d/nlserver6** voor gebruik bij het opstarten, of creeer een systeemeenheid (beginnend 20.1).

>[!NOTE]
>
>De **neolane** systeemgebruiker moet niet gecreeerd zijn alvorens het bevel in werking werd gesteld. De **neolane** de gebruiker automatisch tijdens de installatie wordt gemaakt.
>
>De **thuis** aan de **neolane** gebruiker wordt ook automatisch gemaakt in **[!UICONTROL /usr/local/neolane]**. Zorg ervoor dat er voldoende ruimte is op de knop **[!UICONTROL /usr/local]** schijf (meerdere GB).

U kunt de **pingelen`hostname`** om ervoor te zorgen dat de server zichzelf kan bereiken.

## Distributie op basis van RPM-pakketten {#distribution-based-on-rpm--packages}

Voer de volgende stappen uit om Adobe Campaign op een RPM-besturingssysteem (RHEL, CentOS en SUSE) te installeren:

1. U moet eerst het Adobe Campaign-pakket ophalen.

   Het bestand krijgt de naam hieronder, waarbij **XXXX** is het Adobe Campaign-buildnummer: **nlserver6-v7-XXXX-0.x86_64.rpm**.

   >[!CAUTION]
   >
   >Gebruik de juiste bestandsnaam voor uw versie van Adobe Campaign in de opdrachtvoorbeelden van deze sectie.

1. Maak verbinding als u het wilt installeren **basis** en voert de volgende opdracht uit (waarbij **XXXX** is het Adobe Campaign-buildnummer):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   Het rpm-bestand is afhankelijk van pakketten die u kunt vinden op CentOS/Red Hat-distributies. Als u sommige van deze gebiedsdelen niet wilt gebruiken (bijvoorbeeld, als u Oracle JDK in plaats van OpenJDK wilt gebruiken), kunt u de &quot;nodeps&quot;optie van rpm moeten gebruiken:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Het &quot;bc&quot;bevel, noodzakelijk voor het uitvoeren van netreport (verwijs naar [deze sectie](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) voor meer informatie), is niet standaard beschikbaar op alle distributies van Linux. Als u wilt controleren of de opdracht beschikbaar is, voert u de opdracht &#39;which bc&#39; uit. Als dat niet het geval is, moet u het installeren.

Met CentOS moet u het pakket bc.x86_64: connect as installeren **basis** en voer de volgende opdracht uit:

```
yum install bc.x86_64
```

## Distributie op basis van APT (Debian) {#distribution-based-on-apt--debian-}

### In Debian 64 bits {#in-debian-64-bits}

Voer de volgende stappen uit om Adobe Campaign 64-bits te installeren op een Debian 64-bits besturingssysteem:

1. U moet eerst het Adobe Campaign-pakket ophalen: **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, waarbij **XXXX** is het bouwstijlaantal.

   >[!CAUTION]
   >
   >Gebruik de juiste bestandsnaam voor uw versie van Adobe Campaign in de opdrachtvoorbeelden van deze sectie.

1. Maak verbinding als u het wilt installeren **basis** en voert de volgende opdracht uit (waarbij **XXXX** is het Adobe Campaign-buildnummer):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   Als er ontbrekende gebiedsdelen zijn, stel het volgende bevel in werking:

   ```
   apt-get install -f
   ```

**Debian 8/9-specificaties**

Houd rekening met het volgende wanneer u Adobe Campaign op een Debian 8/9-besturingssysteem installeert:

* OpenSSL moet vooraf zijn geïnstalleerd.
* Installeer libicu52 (Debian 8) of libicu57 (Debian 9), libprotobuf9 (Debian8) en libc-ares2 met de volgende opdrachten:

  ```
  aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
  ```

  ```
  aptitude install libc-ares2
  ```

  ```
  aptitude install libprotobuf9 (only Debian 8)
  ```

* Installeer JDK7 met de volgende opdracht:

  ```
  aptitude install openjdk-7-jdk (Debian 8)
  ```

  ```
  aptitude install openjdk-7-jdk (Debian 9)
  ```

## Parameters aanpassen {#personalizing-parameters}

Sommige parameters kunnen via de **klant.sh** file

Als u de installatie voor de eerste keer uitvoert, **klant.sh** bestand bestaat mogelijk nog niet op de server. Maak het bestand en zorg ervoor dat het uitvoeringsrechten heeft. Als dit niet het geval is, ga het volgende bevel in:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Servercodering {#server-encoding}

Standaard wordt de server gestart in een iso8859-15-omgeving. De server kan echter wel in een UTF-8-omgeving worden gestart.

>[!CAUTION]
>
>Deze wijziging is van invloed op de interactie met het bestandssysteem (bestanden die via een workflow of een JavaScript-script zijn geladen) en op de bestandscodering. Daarom raden we u aan de standaardomgeving te gebruiken.

Voor het instellen van een **Japanse instantie**, moet u een UTF-8-omgeving gebruiken.

Gebruik de volgende opdracht om de UTF-8-omgeving in te schakelen:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Standaardtaal voor de server {#default-language-for-the-server}

De installatie ondersteunt zowel Engels als Frans. Engels wordt standaard gebruikt.

Als u naar het Frans wilt schakelen, voert u de volgende opdrachten in:

```
su - neolane
vi nl6/customer.sh
```

en voeg de volgende regel toe:

```
export neolane_LANG=fra
```

Om ervoor te zorgen dat de systeemberichten correct worden gelezen, moeten de consoles in een codepagina zijn die aan de taal (ISO-8859-1 of -15 voor Frans) beantwoordt.

### Omgevingsvariabelen {#environment-variables}

De volgende omgevingsvariabelen moeten correct worden gedefinieerd.

Bepaalde combinaties vereisen wijzigingen in de omgeving die wordt gebruikt voor het uitvoeren van Adobe Campaign. Een specifiek bestand (`/usr/local/neolane/nl6/customer.sh`) kan worden gemaakt en bewerkt om wijzigingen toe te voegen die specifiek zijn voor de Adobe Campaign-omgeving.

Bewerk indien nodig de **klant.sh** bestand gebruiken met de **vi customer.sh** en pas de configuratie aan of voeg ontbrekende lijnen toe:

* Voor de client Oracle:

  ```
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  De inhoud van de omgevingsvariabele ORACLE_HOME komt overeen met de installatiemap van het Oracle.

  De inhoud van de TNS_ADMIN-variabele moet overeenkomen met de locatie van de **tnsnames.ora** bestand.

* Voor LibreOffice:

  Voor het uitvoeren van Adobe Campaign op een bestaande versie van LibreOffice zijn aanvullende configuraties vereist: u moet de toegangspaden naar de installatiemap opgeven. Bijvoorbeeld:

   * Debian

     De standaardwaarden voor OO_INSTALL_DIR en OOO_BASIS_INSTALL_DIR worden verstrekt. U kunt deze overschrijven in **klant.sh** als uw lay-out van de installatie LibreOffice verschillend is:

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

  Standaard wordt het configuratiescript van de Adobe Campaign-omgeving (`~/nl6/env.sh`) zoekt naar de JDK-installatiemap. Aangezien dit gedrag niet 100% betrouwbaar is, moet u opgeven welke JDK moet worden gebruikt. Om dit te doen, kunt u dwingen **JDK_HOME** omgevingsvariabele met de volgende opdracht:

  ```
  export JDK_HOME=/usr/java/jdk1.6.0_07
  ```

  >[!NOTE]
  >
  >Dit is een voorbeeld. Zorg ervoor dat de gebruikte JDK-versie overeenkomt met de mapnaam.

  Als u de JDK-configuratie wilt testen, meldt u zich aan als de Adobe Campaign-systeemgebruiker met de volgende opdracht:

  ```
  su - neolane
  ```

U moet de Adobe Campaign-service opnieuw starten om rekening te houden met de wijzigingen.

De opdrachten zijn als volgt:

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

Vanaf 20.1, adviseren wij in plaats daarvan het gebruiken van de volgende bevelen:

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

  Zie [Omgevingsvariabelen](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Configuratie voor Adobe Campaign

  Als u de Oracle-client voor Adobe Campaign wilt installeren, moet u een symbolische koppeling maken voor de **.so** bestand gebruikt door Adobe Campaign.

  Hiervoor gebruikt u de volgende opdrachten:

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

Als er een probleem optreedt, controleert u of de pakketten in het dialoogvenster [Installatiedocumentatie oracle](https://docs.oracle.com/) correct zijn geïnstalleerd.

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

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Met deze opdrachten kunt u **config-default.xml** en **serverConf.xml** configuratiebestanden. Alle parameters die beschikbaar zijn in het dialoogvenster **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

Druk **Ctrl+C** om het proces tegen te houden, dan ga het volgende bevel in:

```
nlserver start web
```

De volgende informatie wordt dan getoond:

```
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

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Wachtwoord voor de interne id {#password-for-the-internal-identifier}

De Adobe Campaign-server definieert een technische aanmeldingsnaam **internal** dat heeft alle rechten . Vlak na de installatie heeft de aanmelding geen wachtwoord. Het is verplicht om er een te definiëren.

Lees meer in [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier).
