---
title: Migreren in Linux voor Adobe Campagne v7
seo-title: Migreren in Linux voor Adobe Campagne v7
description: Migreren in Linux voor Adobe Campagne v7
seo-description: null
page-status-flag: never-activated
uuid: 47870ea4-b07b-4db7-8094-7a8b6f4b6936
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: 8f6519e8-5c8d-4974-b193-a9f1cf78b3a3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Migreren in Linux voor Adobe Campagne v7{#migrating-in-linux-for-adobe-campaign-v}

## Algemene procedure {#general-procedure}

De migratiestappen in Linux zijn als volgt:

1. Stopservices: zie [Servicestop](#service-stop).
1. Sla de database op: zie [Een back-up maken van de database en de bestaande installatie](#back-up-the-database-and-the-existing-installation).
1. Verwijder vorige Adobe Campagne versiepakketten: Zie [Adobe Campagne-pakketten van vorige versies](#uninstalling-adobe-campaign-previous-version-packages)verwijderen.
1. Het platform migreren: raadpleeg [Adobe Campagne v7](#deploying-adobe-campaign-v7)implementeren.
1. Herstart service: verwijzen naar [herstartservices](#re-starting-services).

## Servicestop {#service-stop}

In de eerste plaats moeten alle processen met toegang tot de database op alle betrokken machines worden stopgezet.

1. Meld u aan als **hoofdmap**.
1. Alle servers die gebruikmaken van de omleidingsmodule (**webmdl** -service) moeten worden gestopt. Voer voor Apache de volgende opdracht uit:

   ```
   /etc/init.d/apache2 stop
   ```

1. Meld u opnieuw aan als **hoofdmap**.
1. Stop Adobe Campagne vorige versieservices op alle servers.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Als u migreert op basis van versie 5.11, voert u de volgende opdracht uit:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Zorg ervoor dat de Adobe Campagnediensten op elke server worden tegengehouden.

   ```
   ps waux | grep nlserver
   ```

   De lijst met actieve processen wordt samen met hun id (PID) weergegeven.

1. Als een of meer Adobe Campagne-processen na een paar minuten nog actief zijn of geblokkeerd zijn, kunt u ze doden.

   ```
   killall nlserver
   ```

1. Als sommige processen na een paar minuten nog actief zijn, kunt u ze dwingen te sluiten met de opdracht:

   ```
   killall -9 nlserver
   ```

## Maak een back-up van de database en de bestaande installatie {#back-up-the-database-and-the-existing-installation}

De procedure is afhankelijk van de vorige versie van uw Adobe-campagne.

### Migreren van Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Maak een back-up van de Adobe Campaign-database.
1. Meld u aan als **neolane** en maak een back-up van de map **nl5** met de volgende opdracht:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >We raden u uit voorzorg aan de map **nl5.back** te comprimeren en op een andere beveiligde locatie dan de server op te slaan.

1. Bewerk de map **config-`<instance name>`.xml** (in de map **nl5.back** ) om de **mta**, **wfserver**, **** stat enz. te voorkomen. services worden automatisch gestart. Vervang bijvoorbeeld **autoStart** door **_autoStart** (nog steeds **neolane**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migreren van Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Maak een back-up van de Adobe Campaign-database.
1. Meld u aan als **neolane** en maak een back-up van de map **nl6** met de volgende opdracht:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >We raden u uit voorzorg aan de map **nl6.back** te comprimeren en op een andere beveiligde locatie dan de server op te slaan.

1. Bewerk de map **config-`<instance name>`.xml** (in de map **nl6.back** ) om de **mta**, **wfserver**, **** stat, enz. te voorkomen. services worden automatisch gestart. Vervang bijvoorbeeld **autoStart** door **_autoStart** (nog steeds **Adobe Campagne**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migreren van Adobe-campagne v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Maak een back-up van de Adobe Campaign-database.
1. Meld u aan als **neolane** en maak een back-up van de map **nl6** met de volgende opdracht:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >We raden u uit voorzorg aan de map **nl6.back** te comprimeren en op een andere beveiligde locatie dan de server op te slaan.

## Installatie van pakketten van vorige versies van Adobe Campagne verwijderen {#uninstalling-adobe-campaign-previous-version-packages}

De procedure is afhankelijk van de vorige versie van uw Adobe-campagne.

### Adobe Campagne v5-pakketten verwijderen {#uninstalling-adobe-campaign-v5-packages}

1. Meld u aan als **hoofdmap**.
1. Identificeer de Adobe Campagnepakketten die met het volgende bevel worden geïnstalleerd.

   * In **Debian**:

      ```
      dpkg -l | grep nl
      ```

      De lijst met geïnstalleerde pakketten wordt weergegeven:

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * In **rode hoed**:

      ```
      rpm -qa | grep nl
      ```

1. Verwijder Adobe Campagne v5-pakketten.

   * In **Debian**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * In **rode hoed**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Adobe Campagne v6-pakketten verwijderen {#uninstalling-adobe-campaign-v6-packages}

In deze sectie ziet u hoe u pakketten van Adobe Campagne versie 6.02 of v6.1 kunt verwijderen.

1. Meld u aan als **hoofdmap**.
1. Identificeer de Adobe Campagnepakketten die met het volgende bevel worden geïnstalleerd.

   * In **Debian**:

      ```
      dpkg -l | grep nl
      ```

      De lijst met geïnstalleerde pakketten wordt weergegeven:

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * In **rode hoed**:

      ```
      rpm -qa | grep nl
      ```

1. Verwijder Adobe Campagne v6-pakketten.

   * In **Debian**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * In **rode hoed**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Adobe Campagne v7 implementeren {#deploying-adobe-campaign-v7}

De procedure is afhankelijk van de vorige versie van uw Adobe-campagne.

### Migreren van Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Het implementeren van Adobe Campaign bestaat uit twee fasen:

* Adobe Campagne v7-pakketten installeren: deze bewerking moet op elke server worden uitgevoerd.
* De postupgrade: deze opdracht moet voor elke instantie worden gestart.

Voer de volgende stappen uit om Adobe Campaign te implementeren:

1. Installeer de meest recente pakketten van de Campagne van Adobe v7 gebruikend het volgende bevel:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * In **rode hoed**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >U moet de pakketten met succes installeren alvorens aan de volgende stap te gaan.

   >[!NOTE]
   >
   >Wanneer u migreert vanaf v5.11, wordt Adobe Campaign standaard geïnstalleerd in de map **/usr/local/neolane/nl6/** .
   >
   >Nadat de pakketten zijn geïnstalleerd, wordt het volgende bericht weergegeven: De optie **&#39;WdbcTimeZone&#39; ontbreekt**. Dit is normaal.

1. Als u het installatieprogramma van de clientconsole beschikbaar wilt maken, kopieert u dit naar de installatiemap van Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Raadpleeg [deze sectie](../../installation/using/installing-campaign-standard-packages.md)voor meer informatie over het installeren van Adobe Campaign in Linux.

1. Wijzig het bestand **.bashrd** dat overeenkomt met de **neolane** -gebruiker. Meld u aan als **neolaan** en voer de volgende opdracht uit:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Wanneer u zich aanmeldt als **neolane**, wordt het volgende bericht weergegeven: **nl5/env.sh : Bestand of map** bestaat niet. Dit is normaal.

   Vervang **nl5/env.sh** aan het einde van het bestand door **nl6/env.sh**.

1. Meld u aan als **hoofdmap** en bereid de instantie voor met de volgende opdrachten:

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >Met deze opdrachten kunt u het interne bestandssysteem van Adobe Campagne v6 maken: **conf** directory (met de bestanden **config-default.xml** en **serverConf.xml** ), **var** directory.

1. Ga naar de back-upmap **nl5.back** en kopieer (overschrijf) de configuratiebestanden en submappen van elke instantie. Meld u aan als **neolaan** en voer de volgende opdracht uit:

   >[!IMPORTANT]
   >
   >Kopieer voor de eerste onderstaande opdracht het bestand **config-default.xml** niet.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. Pas in de Adobe Campagne v7 **serverConf.xml** - en **config-default.xml** -bestanden de specifieke configuraties toe die u voor Adobe Campagne v5 had. Gebruik voor het bestand **serverConf.xml** het bestand **nl5/conf/serverConf.xml.diff** .

   >[!NOTE]
   >
   >Wanneer u configuraties van Adobe Campaign v5 naar Adobe Campaign v7 rapporteert, moet u ervoor zorgen dat de paden naar de fysieke mappen leiden naar Adobe Campaign v7 en niet naar Adobe Campaign v5.

1. Aangezien de migratie geen generische installatie is, moet u het opnieuw beginnen van de **gevolgde logd** dienst dwingen. Open hiertoe het bestand **nl6/conf/config-default.xml** en zorg ervoor dat de service **trackinglogd** is geactiveerd (alleen op de server(s) voor bijhouden/omleiden):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Als de **gevolgde logd** dienst niet op de volgende server is begonnen, zal geen het volgen informatie door:sturen.

1. Laad de configuratie van Adobe Campagne v7 opnieuw gebruikend het volgende bevel:

   ```
   nlserver config -reload
   ```

1. Start het postupgrade-proces met de volgende opdracht (nog steeds als **neolaan**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >U moet specificeren welke tijdzone als verwijzing tijdens postupgrade (gebruikend de **-timezone** optie) te gebruiken. In dit geval gebruiken we de tijdzone Europa/Parijs **-tijdzone: &quot;Europa/Parijs&quot;**.

   >[!NOTE]
   >
   >We raden u ten zeerste aan uw basis te upgraden naar &quot;multi timezone&quot;. Raadpleeg de sectie [Tijdzones](../../migration/using/general-configurations.md#time-zones) voor meer informatie over tijdzoneopties.

>[!IMPORTANT]
>
>Start Adobe Campagne-services nog niet: In Apache moeten nog wijzigingen worden aangebracht.

### Migreren van Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Het implementeren van Adobe Campaign bestaat uit twee fasen:

* Adobe Campagne v7-pakketten installeren: deze bewerking moet op elke server worden uitgevoerd.
* De postupgrade: deze opdracht moet voor elke instantie worden gestart.

Voer de volgende stappen uit om Adobe Campaign te implementeren:

1. Installeer de meest recente pakketten van de Campagne van Adobe v7 gebruikend het volgende bevel:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * In **rode hoed**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >U moet de pakketten met succes installeren alvorens aan de volgende stap te gaan.

   >[!NOTE]
   >
   >Adobe Campagne v7 is standaard in dezelfde map geïnstalleerd als Adobe Campagne v6.02: **/usr/local/neolane/nl6/**.

1. Als u het installatieprogramma van de clientconsole beschikbaar wilt maken, kopieert u dit naar de installatiemap van Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Raadpleeg [deze sectie](../../installation/using/installing-campaign-standard-packages.md)voor meer informatie over het installeren van Adobe Campaign in Linux.

1. Aangezien de migratie geen generische installatie is, moet u het opnieuw beginnen van de **gevolgde logd** dienst dwingen. Open hiertoe het bestand **nl6/conf/config-default.xml** en zorg ervoor dat de service **trackinglogd** is geactiveerd (alleen op de server(s) voor bijhouden/omleiden):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Als de **gevolgde logd** dienst niet op de volgende server is begonnen, zal geen het volgen informatie door:sturen.

1. Ga naar de back-upmap **nl6.back** en kopieer (overschrijf) de configuratiebestanden en submappen van elke instantie. Meld u aan als **neolaan** en voer de volgende opdracht uit:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Laad de configuratie van Adobe Campagne v7 opnieuw gebruikend het volgende bevel:

   ```
   nlserver config -reload
   ```

1. Start het postupgrade-proces met de volgende opdracht (nog steeds als **neolaan**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >De modus &quot;multi timezone&quot; was alleen beschikbaar in v6.02 voor PostgreSQL-databasemotoren. Het is nu beschikbaar ongeacht welke versie van de database-engine wordt gebruikt. We raden u ten zeerste aan uw basis te upgraden naar &quot;multi timezone&quot;. Raadpleeg de sectie [Tijdzones](../../migration/using/general-configurations.md#time-zones) voor meer informatie over tijdzoneopties.

### Migreren van Adobe-campagne v6.1 {#migrating-from-adobe-campaign-v6_1-1}

Het implementeren van Adobe Campaign bestaat uit twee fasen:

* Adobe Campagne v7-pakketten installeren: deze bewerking moet op elke server worden uitgevoerd.
* De postupgrade: deze opdracht moet voor elke instantie worden gestart.

Voer de volgende stappen uit om Adobe Campaign te implementeren:

1. Installeer de meest recente pakketten van de Campagne van Adobe v7 gebruikend het volgende bevel:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * In **rode hoed**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >U moet de pakketten met succes installeren alvorens aan de volgende stap te gaan.

   >[!NOTE]
   >
   >Adobe Campaign v7 is standaard geïnstalleerd in de map **/usr/local/neolane/nl6/** .

1. Als u het installatieprogramma van de clientconsole beschikbaar wilt maken, kopieert u dit naar de installatiemap van Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Raadpleeg [deze sectie](../../installation/using/installing-campaign-standard-packages.md)voor meer informatie over het installeren van Adobe Campaign in Linux.

1. Ga naar de back-upmap **nl6.back** en kopieer (overschrijf) de configuratiebestanden en submappen van elke instantie. Meld u aan als **neolaan** en voer de volgende opdracht uit:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Laad de configuratie van Adobe Campagne v7 opnieuw gebruikend het volgende bevel:

   ```
   nlserver config -reload
   ```

1. Start het postupgrade-proces met de volgende opdracht (nog steeds als **neolaan**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## De omleidingsserver (Apache) migreren {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Deze sectie is alleen van toepassing wanneer u migreert van Adobe Campagne v5.11.

In dit stadium moet Apache worden stopgezet. Zie: [Servicestop](#service-stop).

1. Meld u aan als **hoofdmap**.
1. Wijzig de Apache-omgevingsvariabelen om deze aan de map **nl6** te koppelen.

   * In **Debian**:

      ```
      vi /etc/apache2/envvars
      ```

   * In **rode hoed**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. Voer vervolgens de volgende opdrachten uit:

   * In **Debian**:

      Vervang **nl5** in het bestand **nlsrv.load** door **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Verwijder de koppeling van het bestand **nlsrv.conf** en maak een nieuwe koppeling.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * In **rode hoed**:

      Ga naar de map **/usr/local/apache2/conf** , bewerk het bestand **http.conf** en vervang **nl5** door **nl6** in de volgende regels.

      In **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Ga naar het bestand **alias.conf** en vervang alle **nl5** door **nl6**. Voer de volgende opdracht uit om dit in Debian te doen:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Beveiligingszones {#security-zones}

Als u vanaf v6.02 of eerder migreert, moet u uw veiligheidsstreken vormen alvorens de diensten te beginnen. Raadpleeg [Beveiliging](../../migration/using/general-configurations.md#security)voor meer informatie.

## Herstart {#re-starting-services}

De procedure is afhankelijk van de vorige versie van uw Adobe-campagne.

### Migreren van Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

In de **config-`<instance name>`.xml** dossiers, activeer het automatische opstarten van **mta**, **wfserver**, **staat**, enz. diensten.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Start Apache en Adobe Campaign-services op elk van de volgende servers:

1. Tracking and redirection server.
1. Midden-sourcingserver.
1. Marketingsserver.

Voordat u verdergaat met de volgende stap, voert u een volledige test van de nieuwe installatie uit. Zorg ervoor dat er geen regressies zijn en dat alles werkt door alle aanbevelingen in de sectie [Algemene configuraties](../../migration/using/general-configurations.md) op te volgen.

### Migreren van Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

In de **config-`<instance name>`.xml** dossiers, activeer het automatische opstarten van **mta**, **wfserver**, **staat**, enz. diensten.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Start Apache en Adobe Campaign-services op elk van de volgende servers:

1. Tracking and redirection server.
1. Midden-sourcingserver.
1. Marketingsserver.

Test de nieuwe installatie volledig, controleer dat het niet regres en zorg ervoor dat alles correct werkt door alle aanbevelingen in de [Algemene configuratiesectie](../../migration/using/general-configurations.md) te volgen.

### Migreren van Adobe-campagne v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Start Apache en Adobe Campaign-services op elk van de volgende servers:

1. Tracking and redirection server.
1. Midden-sourcingserver.
1. Marketingsserver.

Test de nieuwe installatie volledig, controleer dat het niet regres en zorg ervoor dat alles correct werkt door alle aanbevelingen in de [Algemene configuratiesectie](../../migration/using/general-configurations.md) te volgen.

## Adobe Campagne v5 verwijderen en opschonen {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Deze sectie is alleen van toepassing wanneer u migreert van Adobe Campagne v5.11.

Voordat u de installatie van Adobe Campagne v5 verwijdert en wist, moet u de volgende aanbevelingen uitvoeren:

* Krijg de functionele teams om een volledige controle van de nieuwe installatie in werking te stellen.
* Verwijder Adobe Campagne v5 alleen als u zeker weet dat u het programma niet hoeft terug te draaien.

Verwijder de map **nl5.back** . Meld u aan als **neolaan** en voer de volgende opdracht uit:

```
su - neolane
rm -rf nl5.back
```

Start de server opnieuw.
