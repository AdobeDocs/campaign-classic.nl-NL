---
title: Pakketten installeren met Linux
seo-title: Pakketten installeren met Linux
description: Pakketten installeren met Linux
seo-description: null
page-status-flag: never-activated
uuid: d83f00b5-500b-406a-a3d6-ea5639f244f0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 04faa9f3-d160-4060-b26e-44333f2faf71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# Pakketten installeren met Linux{#installing-packages-with-linux}

Voor een Linux 32-bits platform installeert u Adobe Campagne 32-bits. Installeer Adobe Campagne met 64 bits voor een Linux 64-bits platform.

Voor elk van deze versies wordt in Adobe Campaign één pakket geleverd: **nlserver**. Dit pakket bevat de binaire bestanden en configuratiebestanden voor een bepaalde versie.

Met de installatieopdrachten kunt u:

* Bestanden kopiëren naar **/usr/local/neolane**
* Maak een Adobe Campagne Linux-account (en de bijbehorende groep), die wordt gemaakt met **/usr/local/neolane** als de thuismap
* Maak een automatisch script **/etc/init.d/nlserver6** voor gebruik bij het opstarten of maak een systeemeenheid (vanaf 20.1).

>[!NOTE]
>
>De gebruiker van het **neolaansysteem** moet niet gecreeerd zijn alvorens het bevel werd in werking gesteld. De **neolaangebruiker** wordt automatisch gemaakt tijdens de installatie.
>
>De **thuismap** die is gekoppeld aan de **neolane** -gebruiker wordt ook automatisch gemaakt in **[!UICONTROL /usr/local/neolane]**. Controleer of er voldoende ruimte op de **[!UICONTROL /usr/local]** schijf (meerdere GB) is.

U kunt in werking stellen **pingelt`hostname`**bevel om ervoor te zorgen de server zich kan bereiken.

## Distributie op basis van RPM-pakketten {#distribution-based-on-rpm--packages}

Voer de volgende stappen uit om Adobe Campaign op een RPM-besturingssysteem (RHEL, CentOS en SUSE) te installeren:

1. U moet eerst het Adobe Campagne-pakket opvragen.

   Het bestand krijgt de volgende naam, waarbij **XXXX** het buildnummer van de Adobe-campagne is:

   * **nlserver6-v7-XXXX-0.x86_64.rpm** voor v7.
   * **nlserver6-XXXX-0.x86_64.rpm** voor v6.1.
   >[!CAUTION]
   >
   >Gebruik de juiste bestandsnaam voor uw versie van Adobe Campagne in de opdrachtvoorbeelden van deze sectie.

1. Als u de toepassing wilt installeren, maakt u verbinding als **hoofdmap** en voert u de volgende opdracht uit (waarbij **XXXX** het buildnummer van de Adobe-campagne is):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   Het rpm-bestand is afhankelijk van pakketten die u kunt vinden op CentOS/Red Hat-distributies. Als u sommige van deze afhankelijkheden niet wilt gebruiken (bijvoorbeeld als u Oracle JDK wilt gebruiken in plaats van OpenJDK), moet u mogelijk de optie &quot;nodeps&quot; van rpm gebruiken:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Het &quot;bc&quot;bevel, noodzakelijk voor het uitvoeren van netreport (verwijs naar [deze sectie](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) voor meer informatie), is niet beschikbaar door gebrek op alle distributies van Linux. Als u wilt controleren of de opdracht beschikbaar is, voert u de opdracht &#39;which bc&#39; uit. Als dat niet het geval is, moet u het installeren.

Met CentOS moet u het pakket bc.x86_64 installeren: Verbind als **wortel** en stel het volgende bevel in werking:

```
yum install bc.x86_64
```

## Distributie op basis van APT (Debian) {#distribution-based-on-apt--debian-}

### In Debian 64 bits {#in-debian-64-bits}

Voer de volgende stappen uit om Adobe Campagne 64-bits te installeren op een Debian 64-bits besturingssysteem:

1. U moet eerst het Adobe Campagne-pakket opvragen.

   * **nlserver6-v7-XXXX-linux-2.6-amd64.deb** voor v7.
   * **nlserver6-XXXX-linux-2.6-amd64.deb** voor v6.1.
   **XXXX** is het buildnummer van de Adobe Campagne.

   >[!CAUTION]
   >
   >Gebruik de juiste bestandsnaam voor uw versie van Adobe Campagne in de opdrachtvoorbeelden van deze sectie.

1. Als u de toepassing wilt installeren, maakt u verbinding als **hoofdmap** en voert u de volgende opdracht uit (waarbij **XXXX** het buildnummer van de Adobe-campagne is):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   Als er ontbrekende gebiedsdelen zijn, stel het volgende bevel in werking:

   ```
   apt-get install -f
   ```

**Debian 8/9-specificaties**

Houd rekening met het volgende wanneer u Adobe Campagne installeert op een Debian 8/9-besturingssysteem:

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

Sommige parameters kunnen via het bestand **customer.sh** worden aangepast

Als u de installatie voor het eerst uitvoert, bestaat het bestand **customer.sh** mogelijk nog niet op de server. Maak het bestand en zorg ervoor dat het uitvoeringsrechten heeft. Als dit niet het geval is, ga het volgende bevel in:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Servercodering {#server-encoding}

Standaard wordt de server gestart in een iso8859-15-omgeving. De server kan echter wel in een UTF-8-omgeving worden gestart.

>[!CAUTION]
>
>Deze wijziging is van invloed op de interactie met het bestandssysteem (bestanden die via een workflow of een JavaScript-script zijn geladen) en op de bestandscodering. Daarom raden we u aan de standaardomgeving te gebruiken.

Voor het maken van een **Japanse instantie** moet u echter een UTF-8-omgeving gebruiken.

Gebruik de volgende opdracht om de UTF-8-omgeving in te schakelen:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Standaardtaal voor de server {#default-language-for-the-server}

De installatie ondersteunt zowel Engels als Frans. Engels wordt standaard gebruikt.

Voer de volgende opdrachten in om naar het Frans te schakelen:

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

Bepaalde combinaties vereisen wijzigingen in de omgeving die wordt gebruikt voor het uitvoeren van Adobe-campagne. Er kan een specifiek bestand (`/usr/local/neolane/nl6/customer.sh`) worden gemaakt en bewerkt om wijzigingen toe te voegen die specifiek zijn voor de Adobe Campagne-omgeving.

Bewerk indien nodig het bestand **customer.sh** met de opdracht **vi customer.sh** en pas de configuratie aan of voeg ontbrekende regels toe:

* Voor de Oracle-client:

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   De inhoud van de omgevingsvariabele ORACLE_HOME komt overeen met de installatiemap van Oracle.

   De inhoud van de variabele TNS_ADMIN moet overeenkomen met de locatie van het bestand **tnsnames.ora** .

* Voor LibreOffice:

   Als u Adobe Campagne wilt uitvoeren op een bestaande versie van LibreOffice, hebt u aanvullende configuraties nodig: u moet de toegangspaden naar de installatiemap opgeven. Bijvoorbeeld:

   * Debian

      Er zijn standaardwaarden voor OOO_INSTALL_DIR, OOO_BASIS_INSTALL_DIR, OOO_URE_INSTALL_DIR. U kunt deze in **customer.sh** overschrijven als uw lay-out van de LibreOffice-installatie anders is:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib/ure/share/
      ```

   * CentOs

      Gebruik de volgende standaardwaarden:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib64/libreoffice/ure/share/
      ```

* Voor Java Development Kit (JDK):

   Standaard zoekt het configuratiescript van de Adobe Campagne-omgeving (`~/nl6/env.sh`) naar de JDK-installatiemap. Aangezien dit gedrag niet 100% betrouwbaar is, moet u opgeven welke JDK moet worden gebruikt. Hiervoor kunt u de **JDK_HOME** -omgevingsvariabele forceren met de volgende opdracht:

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >Dit is een voorbeeld. Zorg ervoor dat de gebruikte JDK-versie overeenkomt met de mapnaam.

   Als u de JDK-configuratie wilt testen, meldt u zich aan als de gebruiker van het Adobe Campagne-systeem met de volgende opdracht:

   ```
   su - neolane
   ```

U moet de Adobe Campagne-service opnieuw starten om rekening te houden met de wijzigingen.

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

### Oracle-client in Linux {#oracle-client-in-linux}

Wanneer u Oracle gebruikt met Adobe Campaign, moet u de Oracle-clientlagen in Linux configureren.

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

* Configuratie voor Adobe-campagne

   Als u de installatie van de Oracle-client voor Adobe Campaign wilt voltooien, moet u een symbolische koppeling maken voor het bestand **.so** dat door Adobe Campaign wordt gebruikt.

   Hiervoor gebruikt u de volgende opdrachten:

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

Als u een probleem ondervindt, moet u ervoor zorgen dat de pakketten die in de installatiedocumentatie [van](https://www.oracle.com/pls/db112/portal.portal_db?selected=11) Oracle worden vermeld, correct zijn geïnstalleerd.

## Installatiecontroles {#installation-checks}

U kunt nu een eerste installatietest uitvoeren met de volgende opdrachten:

```
su - neolane
nlserver pdump
```

Wanneer de Campagne van Adobe niet wordt begonnen, is de reactie:

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

Met deze opdrachten kunt u configuratiebestanden **config-default.xml** en **serverConf.xml** maken. Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

Druk op **Ctrl+C** om het proces te stoppen en voer vervolgens de volgende opdracht in:

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

De Adobe Campaign-server definieert een technische aanmelding die **intern** wordt genoemd en alle rechten in alle gevallen heeft. Vlak na de installatie heeft de aanmelding geen wachtwoord. Het is verplicht om er een te definiëren.

Zie de sectie [Interne id](../../installation/using/campaign-server-configuration.md#internal-identifier).
