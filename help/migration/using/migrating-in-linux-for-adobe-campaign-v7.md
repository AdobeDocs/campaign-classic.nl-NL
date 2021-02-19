---
solution: Campaign Classic
product: campaign
title: Migreren in Linux voor Adobe Campaign v7
description: Migreren in Linux voor Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---


# Migreren in Linux voor Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

## Algemene procedure {#general-procedure}

De migratiestappen in Linux zijn als volgt:

1. Stopservices: zie [Servicestop](#service-stop).
1. Sla de database op: zie [Een back-up maken van de database en de bestaande installatie](#back-up-the-database-and-the-existing-installation).
1. Verwijder vorige Adobe Campaign-versiepakketten: zie [Verwijderen van vorige Adobe Campaign-versiepakketten](#uninstalling-adobe-campaign-previous-version-packages).
1. Het platform migreren: Raadpleeg [Adobe Campaign v7](#deploying-adobe-campaign-v7) implementeren.
1. Herstart service: Raadpleeg [Services opnieuw starten](#re-starting-services).

## Servicestop {#service-stop}

In de eerste plaats moeten alle processen met toegang tot de database op alle betrokken machines worden stopgezet.

1. Meld u aan als **root**.
1. Alle servers die gebruikmaken van de omleidingsmodule (**webmdl** service) moeten worden gestopt. Voer voor Apache de volgende opdracht uit:

   ```
   /etc/init.d/apache2 stop
   ```

1. Meld u opnieuw aan als **root**.
1. Stop de vorige Adobe Campaign-versieservices op alle servers.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Als u migreert op basis van versie 5.11, voert u de volgende opdracht uit:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Zorg ervoor dat Adobe Campaign-services op elke server worden gestopt.

   ```
   ps waux | grep nlserver
   ```

   De lijst met actieve processen wordt samen met hun id (PID) weergegeven.

1. Als een of meer Adobe Campaign-processen na een paar minuten nog actief zijn of geblokkeerd zijn, moet u ze doden.

   ```
   killall nlserver
   ```

1. Als sommige processen na een paar minuten nog actief zijn, kunt u ze dwingen te sluiten met de opdracht:

   ```
   killall -9 nlserver
   ```

## Maak een back-up van de database en de bestaande installatie {#back-up-the-database-and-the-existing-installation}

De procedure is afhankelijk van de vorige versie van Adobe Campaign.

### Migreren vanuit Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Maak een back-up van de Adobe Campaign-database.
1. Meld u aan als **neolane** en maak een back-up van de map **nl5** met behulp van de volgende opdracht:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Als voorzorgsmaatregel, adviseren wij dat u **nl5.back** omslag en bewaart het aan een veilige plaats buiten de server.

1. Bewerk de **config-`<instance name>`.xml** (in de map **nl5.back**) om **mta**, **wfserver**, **stat** enz. te voorkomen. services worden automatisch gestart. Vervang bijvoorbeeld **autoStart** door **_autoStart** (nog steeds als **neolane**).

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

### Migreren vanuit Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Maak een back-up van de Adobe Campaign-database.
1. Meld u aan als **neolane** en maak een back-up van de map **nl6** met behulp van de volgende opdracht:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Als voorzorgsmaatregel, adviseren wij dat u **nl6.back** omslag wegrijpt en het aan een veilige plaats buiten de server bewaart.

1. Bewerk **config-`<instance name>`.xml** (in de map **nl6.back**) om **mta**, **wfserver**, **stat**, enz. te voorkomen. services worden automatisch gestart. Vervang bijvoorbeeld **autoStart** door **_autoStart** (nog steeds als **Adobe Campaign**).

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

### Migreren vanuit Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Maak een back-up van de Adobe Campaign-database.
1. Meld u aan als **neolane** en maak een back-up van de map **nl6** met behulp van de volgende opdracht:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Als voorzorgsmaatregel, adviseren wij dat u **nl6.back** omslag wegrijpt en het aan een veilige plaats buiten de server bewaart.

## Verwijderen van vorige Adobe Campaign-versiepakketten {#uninstalling-adobe-campaign-previous-version-packages}

De procedure is afhankelijk van de vorige versie van Adobe Campaign.

### Adobe Campaign v5-pakketten verwijderen {#uninstalling-adobe-campaign-v5-packages}

1. Meld u aan als **root**.
1. Identificeer de geïnstalleerde pakketten van Adobe Campaign gebruikend het volgende bevel.

   * In **Debian**:

      ```
      dpkg -l | grep nl
      ```

      De lijst met geïnstalleerde pakketten wordt weergegeven:

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * In **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Verwijder Adobe Campaign v5-pakketten.

   * In **Debian**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * In **Red Hat**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Adobe Campaign v6-pakketten verwijderen {#uninstalling-adobe-campaign-v6-packages}

In deze sectie wordt getoond hoe u Adobe Campaign v6.02- of v6.1-pakketten kunt verwijderen.

1. Meld u aan als **root**.
1. Identificeer de geïnstalleerde pakketten van Adobe Campaign gebruikend het volgende bevel.

   * In **Debian**:

      ```
      dpkg -l | grep nl
      ```

      De lijst met geïnstalleerde pakketten wordt weergegeven:

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * In **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Verwijder Adobe Campaign v6-pakketten.

   * In **Debian**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * In **Red Hat**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Adobe Campaign v7 {#deploying-adobe-campaign-v7} implementeren

De procedure is afhankelijk van de vorige versie van Adobe Campaign.

### Migreren vanuit Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Bij het implementeren van Adobe Campaign worden twee stappen uitgevoerd:

* Adobe Campaign v7-pakketten installeren: deze bewerking moet op elke server worden uitgevoerd.
* De postupgrade: deze opdracht moet voor elke instantie worden gestart.

Voer de volgende stappen uit om Adobe Campaign te implementeren:

1. Installeer de meest recente Adobe Campaign v7-pakketten met de volgende opdracht:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * In **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >U moet de pakketten met succes installeren alvorens aan de volgende stap te gaan.

   >[!NOTE]
   >
   >Bij het migreren vanaf v5.11 wordt Adobe Campaign standaard geïnstalleerd in de map **/usr/local/neolane/nl6/**.
   >
   >Nadat de pakketten zijn geïnstalleerd, wordt het volgende bericht weergegeven: **&#39;WdbcTimeZone&#39; optie ontbreekt**. Dit is normaal.

1. Als u het installatieprogramma van de clientconsole beschikbaar wilt maken, kopieert u dit naar de installatiemap van Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Raadpleeg [deze sectie](../../installation/using/installing-campaign-standard-packages.md) voor meer informatie over het installeren van Adobe Campaign in Linux.

1. Wijzig het **.bashrd** dossier dat **neolane** gebruiker aanpast. Meld u aan als **neolaan** en voer de volgende opdracht uit:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Wanneer u zich aanmeldt als **neolane**, wordt het volgende bericht weergegeven: **nl5/env.sh: Bestand of map** bestaat niet. Dit is normaal.

   Aan het einde van het bestand vervangt u **nl5/env.sh** door **nl6/env.sh**.

1. Meld u aan als **root** en bereid de instantie voor met de volgende opdrachten:

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
   >Met deze opdrachten kunt u het interne bestandssysteem van Adobe Campaign v6 maken: **conf** directory (met de map **config-default.xml** en **serverConf.xml**), **var** directory.

1. Ga naar **nl5.back** reserveomslag en kopieer (overschrijf) de configuratiedossiers en subfolders van elke instantie. Meld u aan als **neolane** en voer de volgende opdracht uit:

   >[!IMPORTANT]
   >
   >Kopieer voor de eerste opdracht hieronder niet het bestand **config-default.xml**.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. Pas in de Adobe Campaign v7 **serverConf.xml** en **config-default.xml** dossiers, de specifieke configuraties toe die u voor Adobe Campaign v5 had. Gebruik voor het bestand **serverConf.xml** het bestand **nl5/conf/serverConf.xml.diff**.

   >[!NOTE]
   >
   >Wanneer u configuraties van Adobe Campaign v5 naar Adobe Campaign v7 rapporteert, moet u ervoor zorgen dat de paden naar de fysieke mappen leiden naar Adobe Campaign v7 en niet naar Adobe Campaign v5.

1. Aangezien migratie geen generieke installatie is, moet u het opnieuw beginnen van de **trackinglogd** dienst dwingen. Hiervoor opent u het bestand **nl6/conf/config-default.xml** en controleert u of de service **trackinglogd** is geactiveerd (alleen op de trackingserver(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Als de service **trackinglogd** niet is gestart op de trackingserver, worden geen trackinggegevens doorgestuurd.

1. Laad de Adobe Campaign v7 configuratie opnieuw gebruikend het volgende bevel:

   ```
   nlserver config -reload
   ```

1. Start het naupgradeproces met de volgende opdracht (nog steeds **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >U moet specificeren welke tijdzone als verwijzing tijdens postupgrade (gebruikend **- timezone** optie) te gebruiken. In dit geval gebruiken we de tijdzone Europa/Parijs **-tijdzone: &quot;Europe/Paris&quot;**.

   >[!NOTE]
   >
   >We raden u ten zeerste aan uw basis te upgraden naar &quot;multi timezone&quot;. Raadpleeg de sectie [Tijdzones](../../migration/using/general-configurations.md#time-zones) voor meer informatie over tijdzoneopties.

>[!IMPORTANT]
>
>Start nog geen Adobe Campaign-services: In Apache moeten nog wijzigingen worden aangebracht.

### Migreren vanuit Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Bij het implementeren van Adobe Campaign worden twee stappen uitgevoerd:

* Adobe Campaign v7-pakketten installeren: deze bewerking moet op elke server worden uitgevoerd.
* De postupgrade: deze opdracht moet voor elke instantie worden gestart.

Voer de volgende stappen uit om Adobe Campaign te implementeren:

1. Installeer de meest recente Adobe Campaign v7-pakketten met de volgende opdracht:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * In **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >U moet de pakketten met succes installeren alvorens aan de volgende stap te gaan.

   >[!NOTE]
   >
   >Adobe Campaign v7 wordt standaard in dezelfde map geïnstalleerd als Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. Als u het installatieprogramma van de clientconsole beschikbaar wilt maken, kopieert u dit naar de installatiemap van Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Raadpleeg [deze sectie](../../installation/using/installing-campaign-standard-packages.md) voor meer informatie over het installeren van Adobe Campaign in Linux.

1. Aangezien migratie geen generieke installatie is, moet u het opnieuw beginnen van de **trackinglogd** dienst dwingen. Hiervoor opent u het bestand **nl6/conf/config-default.xml** en controleert u of de service **trackinglogd** is geactiveerd (alleen op de trackingserver(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Als de service **trackinglogd** niet is gestart op de trackingserver, worden geen trackinggegevens doorgestuurd.

1. Ga naar **nl6.back** reserveomslag en kopieer (overschrijf) de configuratiedossiers en subfolders van elke instantie. Meld u aan als **neolane** en voer de volgende opdracht uit:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Laad de Adobe Campaign v7 configuratie opnieuw gebruikend het volgende bevel:

   ```
   nlserver config -reload
   ```

1. Start het naupgradeproces met de volgende opdracht (nog steeds **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >De modus &quot;multi timezone&quot; was alleen beschikbaar in v6.02 voor PostgreSQL-databasemotoren. Het is nu beschikbaar ongeacht welke versie van de database-engine wordt gebruikt. We raden u ten zeerste aan uw basis te upgraden naar &quot;multi timezone&quot;. Raadpleeg de sectie [Tijdzones](../../migration/using/general-configurations.md#time-zones) voor meer informatie over tijdzoneopties.

### Migreren vanuit Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

Bij het implementeren van Adobe Campaign worden twee stappen uitgevoerd:

* Adobe Campaign v7-pakketten installeren: deze bewerking moet op elke server worden uitgevoerd.
* De postupgrade: deze opdracht moet voor elke instantie worden gestart.

Voer de volgende stappen uit om Adobe Campaign te implementeren:

1. Installeer de meest recente Adobe Campaign v7-pakketten met de volgende opdracht:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * In **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >U moet de pakketten met succes installeren alvorens aan de volgende stap te gaan.

   >[!NOTE]
   >
   >Adobe Campaign v7 is standaard geïnstalleerd in de map **/usr/local/neolane/nl6/**.

1. Als u het installatieprogramma van de clientconsole beschikbaar wilt maken, kopieert u dit naar de installatiemap van Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Raadpleeg [deze sectie](../../installation/using/installing-campaign-standard-packages.md) voor meer informatie over het installeren van Adobe Campaign in Linux.

1. Ga naar **nl6.back** reserveomslag en kopieer (overschrijf) de configuratiedossiers en subfolders van elke instantie. Meld u aan als **neolane** en voer de volgende opdracht uit:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Laad de Adobe Campaign v7 configuratie opnieuw gebruikend het volgende bevel:

   ```
   nlserver config -reload
   ```

1. Start het naupgradeproces met de volgende opdracht (nog steeds **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## De omleidingsserver (Apache) {#migrating-the-redirection-server--apache-} migreren

>[!NOTE]
>
>Deze sectie is alleen van toepassing wanneer u migreert vanaf Adobe Campaign v5.11.

In dit stadium moet Apache worden stopgezet. Zie: [Servicestop](#service-stop).

1. Meld u aan als **root**.
1. Wijzig de Apache-omgevingsvariabelen om deze te koppelen aan de map **nl6**.

   * In **Debian**:

      ```
      vi /etc/apache2/envvars
      ```

   * In **Red Hat**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. Voer vervolgens de volgende opdrachten uit:

   * In **Debian**:

      Vervang **nl5** in het bestand **nlsrv.load** door **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Verwijder de koppeling van het bestand **nlsrv.conf** en maak een nieuw bestand.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * In **Red Hat**:

      Ga naar de map **/usr/local/apache2/conf**, bewerk het bestand **http.conf** en vervang **nl5** door **nl6** in de volgende regels.

      In **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Ga naar het **alias.conf**-bestand en vervang alle **nl5** door **nl6**. Voer de volgende opdracht uit om dit in Debian te doen:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Beveiligingszones {#security-zones}

Als u vanaf v6.02 of eerder migreert, moet u uw veiligheidsstreken vormen alvorens de diensten te beginnen. Raadpleeg [Security](../../migration/using/general-configurations.md#security) voor meer informatie.

## Services {#re-starting-services} opnieuw starten

De procedure is afhankelijk van de vorige versie van Adobe Campaign.

### Migreren vanuit Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

In **config-`<instance name>`.xml** dossiers, activeer het automatische opstarten van **mta**, **wfserver**, **stat**, enz. diensten.

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

Start Apache- en Adobe Campaign-services op elk van de volgende servers:

1. Tracking and redirection server.
1. Midsourcingserver.
1. Marketingsserver.

Voordat u verdergaat met de volgende stap, voert u een volledige test van de nieuwe installatie uit. Zorg ervoor dat er geen regressies zijn en dat alles werkt door alle aanbevelingen in de sectie [Algemene configuraties](../../migration/using/general-configurations.md) op te volgen.

### Migreren vanuit Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

In **config-`<instance name>`.xml** dossiers, activeer het automatische opstarten van **mta**, **wfserver**, **stat**, enz. diensten.

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

Start Apache- en Adobe Campaign-services op elk van de volgende servers:

1. Tracking and redirection server.
1. Midsourcingserver.
1. Marketingsserver.

Test de nieuwe installatie volledig, controleer dat het niet regres en zorg ervoor dat alles correct werkt door alle aanbevelingen in [Algemene configuraties](../../migration/using/general-configurations.md) sectie te volgen.

### Migreren vanuit Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Start Apache- en Adobe Campaign-services op elk van de volgende servers:

1. Tracking and redirection server.
1. Midsourcingserver.
1. Marketingsserver.

Test de nieuwe installatie volledig, controleer dat het niet regres en zorg ervoor dat alles correct werkt door alle aanbevelingen in [Algemene configuraties](../../migration/using/general-configurations.md) sectie te volgen.

## Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5} verwijderen en opschonen

>[!NOTE]
>
>Deze sectie is alleen van toepassing wanneer u migreert vanaf Adobe Campaign v5.11.

Voordat u de Adobe Campaign v5-installatie verwijdert en wist, moet u de volgende aanbevelingen uitvoeren:

* Krijg de functionele teams om een volledige controle van de nieuwe installatie in werking te stellen.
* Verwijder Adobe Campaign v5 alleen als u er zeker van bent dat terugdraaien niet nodig is.

Verwijder de map **nl5.back**. Meld u aan als **neolane** en voer de volgende opdracht uit:

```
su - neolane
rm -rf nl5.back
```

Start de server opnieuw.
