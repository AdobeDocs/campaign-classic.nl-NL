---
product: campaign
title: Een Linux-platform migreren naar Adobe Campaign v7
description: Leer hoe u een Linux-platform kunt migreren naar Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 63aca25a8d1ae24ef83849b35a44d1b37cfa5e96
workflow-type: tm+mt
source-wordcount: '1858'
ht-degree: 0%

---

# Een Linux-platform migreren naar Campagne v7{#migrating-in-linux-for-adobe-campaign-v}

![](../../assets/v7-only.svg)

De migratiestappen in Linux zijn als volgt:

1. Stop alle services - [Meer informatie](#service-stop).
1. De database opslaan - [Meer informatie](#back-up-the-database).
1. Verwijder vorige Adobe Campaign-versiepakketten - [Meer informatie](#uninstalling-adobe-campaign-previous-version-packages).
1. Het platform migreren - [Meer informatie](#deploying-adobe-campaign-v7).
1. Service opnieuw starten - [Meer informatie](#re-starting-services).

## Servicestop {#service-stop}

In de eerste plaats moeten alle processen met toegang tot de database op alle betrokken machines worden stopgezet.

1. Aanmelden als **basis**.
1. Alle servers die de omleidingsmodule gebruiken (**webmdl** (service) moet worden gestopt. Voer voor Apache de volgende opdracht uit:

   ```
   /etc/init.d/apache2 stop
   ```

1. Opnieuw aanmelden als **basis**.
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

## Back-up maken van uw database {#back-up-the-database}

De procedure is afhankelijk van de vorige versie van Adobe Campaign.

### Voor Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Maak een back-up van de Adobe Campaign-database.
1. Aanmelden als **neolane** en maakt een back-up van de **nl5** map met de volgende opdracht:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Als voorzorgsmaatregel raden we u aan het **nl5.back** en sla deze op een andere beveiligde locatie dan de server op.

1. Bewerk de **config-`<instance name>`.xml** (in de **nl5.back** map), om de **mta**, **wfserver**, **stat** enz. services worden automatisch gestart. Bijvoorbeeld, vervang **autoStart** with **_autoStart** (nog steeds **neolane**).

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

### Voor Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Maak een back-up van de Adobe Campaign-database.
1. Aanmelden als **neolane** en maakt een back-up van de **nl6** map met de volgende opdracht:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Als voorzorgsmaatregel raden we u aan het **nl6.back** en sla deze op een andere beveiligde locatie dan de server op.

1. Bewerk de **config-`<instance name>`.xml** (in de **nl6.back** (map) om de **mta**, **wfserver**, **stat**, enz. services worden automatisch gestart. Bijvoorbeeld, vervang **autoStart** with **_autoStart** (nog steeds **Adobe Campaign**).

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

### Voor Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Maak een back-up van de Adobe Campaign-database.
1. Aanmelden als **neolane** en maakt een back-up van de **nl6** map met de volgende opdracht:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Als voorzorgsmaatregel raden we u aan het **nl6.back** en sla deze op een andere beveiligde locatie dan de server op.

## Oude Adobe Campaign-versiepakketten verwijderen {#uninstalling-adobe-campaign-previous-version-packages}

De procedure is afhankelijk van de vorige versie van Adobe Campaign.

### Voor v5-pakketten {#uninstalling-adobe-campaign-v5-packages}

1. Aanmelden als **basis**.
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

   * In **Rode hoed**:

      ```
      rpm -qa | grep nl
      ```

1. Verwijder Adobe Campaign v5-pakketten.

   * In **Debian**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * In **Rode hoed**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Voor v6-pakketten {#uninstalling-adobe-campaign-v6-packages}

In deze sectie wordt getoond hoe u Adobe Campaign v6.02- of v6.1-pakketten kunt verwijderen.

1. Aanmelden als **basis**.
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

   * In **Rode hoed**:

      ```
      rpm -qa | grep nl
      ```

1. Verwijder Adobe Campaign v6-pakketten.

   * In **Debian**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * In **Rode hoed**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Adobe Campaign v7 implementeren {#deploying-adobe-campaign-v7}

De procedure is afhankelijk van de vorige versie van Adobe Campaign.

### Uit Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Bij het implementeren van Adobe Campaign worden twee stappen uitgevoerd:

* Adobe Campaign v7-pakketten installeren: deze bewerking moet op elke server worden uitgevoerd.
* De postupgrade: deze opdracht moet voor elke instantie worden gestart.

Voer de volgende stappen uit om Adobe Campaign te implementeren:

1. Installeer de meest recente Adobe Campaign v7-pakketten met de volgende opdracht:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * In **Rode hoed**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >U moet de pakketten met succes installeren alvorens aan de volgende stap te gaan.

   >[!NOTE]
   >
   >Bij het migreren vanaf v5.11 wordt Adobe Campaign geïnstalleerd in het dialoogvenster **/usr/local/neolane/nl6/** standaard.
   >
   >Nadat de pakketten zijn geïnstalleerd, wordt het volgende bericht weergegeven: **De optie WdbcTimeZone ontbreekt**. Dit is normaal.

1. Als u het installatieprogramma van de clientconsole beschikbaar wilt maken, kopieert u dit naar de installatiemap van Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Raadpleeg voor meer informatie over het installeren van Adobe Campaign in Linux [deze sectie](../../installation/using/installing-campaign-standard-packages.md).

1. De **.bashrd** bestand dat overeenkomt met het **neolane** gebruiker. Aanmelden als **neolane** en voer de volgende opdracht uit:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Wanneer u zich aanmeldt als **neolane**, wordt het volgende bericht weergegeven: **nl5/env.sh: Bestand of map bestaat niet**. Dit is normaal.

   Aan het einde van het bestand vervangt u **nl5/env.sh** with **nl6/env.sh**.

1. Aanmelden als **basis** en bereid de instantie voor gebruikend de volgende bevelen:

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
   >Met deze opdrachten kunt u het interne bestandssysteem van Adobe Campaign v6 maken: **conf** directory (met de **config-default.xml** en **serverConf.xml** bestanden), **var** directory.

1. Ga naar de **nl5.back** back-upmap en kopieer (overschrijf) de configuratiebestanden en submappen van elke instantie. Aanmelden als **neolane** en voer de volgende opdracht uit:

   >[!IMPORTANT]
   >
   >Voor de eerste onderstaande opdracht kopieert u de opdracht **config-default.xml** bestand.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. In de Adobe Campaign v7 **serverConf.xml** en **config-default.xml** , past u de specifieke configuraties toe die u voor Adobe Campaign v5 had. Voor de **serverConf.xml** bestand gebruiken **nl5/conf/serverConf.xml.diff** bestand.

   >[!NOTE]
   >
   >Wanneer u configuraties van Adobe Campaign v5 naar Adobe Campaign v7 rapporteert, moet u ervoor zorgen dat de paden naar de fysieke mappen leiden naar Adobe Campaign v7 en niet naar Adobe Campaign v5.

1. Aangezien migratie geen algemene installatie is, moet u het opnieuw opstarten van **trackinglogd** service. Om dit te doen, open **nl6/conf/config-default.xml** en zorg ervoor dat de **trackinglogd** service is geactiveerd (alleen op de traceer-/omleidingsserver(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Als de **trackinglogd** de dienst is niet begonnen op de volgende server, zal geen het volgen informatie worden doorgestuurd.

1. Laad de Adobe Campaign v7 configuratie opnieuw gebruikend het volgende bevel:

   ```
   nlserver config -reload
   ```

1. Begin het postupgrade proces gebruikend het volgende bevel (nog **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >U moet specificeren welke tijdzone als verwijzing tijdens postupgrade (gebruiken **-timezone** ). In dit geval gebruiken we de tijdzone Europa/Parijs **-timezone: &quot;Europa/Parijs&quot;**.

   >[!NOTE]
   >
   >We raden u ten zeerste aan uw basis te upgraden naar &quot;multi timezone&quot;. Raadpleeg voor meer informatie over tijdzoneopties de [Tijdzones](../../migration/using/general-configurations.md#time-zones) sectie.

>[!IMPORTANT]
>
>Start nog geen Adobe Campaign-services: In Apache moeten nog wijzigingen worden aangebracht.

### Uit Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Bij het implementeren van Adobe Campaign worden twee stappen uitgevoerd:

* Adobe Campaign v7-pakketten installeren: deze bewerking moet op elke server worden uitgevoerd.
* De postupgrade: deze opdracht moet voor elke instantie worden gestart.

Voer de volgende stappen uit om Adobe Campaign te implementeren:

1. Installeer de meest recente Adobe Campaign v7-pakketten met de volgende opdracht:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * In **Rode hoed**:

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
   >Raadpleeg voor meer informatie over het installeren van Adobe Campaign in Linux [deze sectie](../../installation/using/installing-campaign-standard-packages.md).

1. Aangezien migratie geen algemene installatie is, moet u het opnieuw opstarten van **trackinglogd** service. Om dit te doen, open **nl6/conf/config-default.xml** en zorg ervoor dat de **trackinglogd** service is geactiveerd (alleen op de traceer-/omleidingsserver(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Als de **trackinglogd** de dienst is niet begonnen op de volgende server, zal geen het volgen informatie worden doorgestuurd.

1. Ga naar de **nl6.back** back-upmap en kopieer (overschrijf) de configuratiebestanden en submappen van elke instantie. Aanmelden als **neolane** en voer de volgende opdracht uit:

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

1. Begin het postupgrade proces gebruikend het volgende bevel (nog **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >De modus &quot;multi timezone&quot; was alleen beschikbaar in v6.02 voor PostgreSQL-databasemotoren. Het is nu beschikbaar ongeacht welke versie van de database-engine wordt gebruikt. We raden u ten zeerste aan uw basis te upgraden naar &quot;multi timezone&quot;. Raadpleeg voor meer informatie over tijdzoneopties de [Tijdzones](../../migration/using/general-configurations.md#time-zones) sectie.

### Van Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

Bij het implementeren van Adobe Campaign worden twee stappen uitgevoerd:

* Adobe Campaign v7-pakketten installeren: deze bewerking moet op elke server worden uitgevoerd.
* De postupgrade: deze opdracht moet voor elke instantie worden gestart.

Voer de volgende stappen uit om Adobe Campaign te implementeren:

1. Installeer de meest recente Adobe Campaign v7-pakketten met de volgende opdracht:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * In **Rode hoed**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >U moet de pakketten met succes installeren alvorens aan de volgende stap te gaan.

   >[!NOTE]
   >
   >Adobe Campaign v7 is geïnstalleerd in het dialoogvenster **/usr/local/neolane/nl6/** standaard.

1. Als u het installatieprogramma van de clientconsole beschikbaar wilt maken, kopieert u dit naar de installatiemap van Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Raadpleeg voor meer informatie over het installeren van Adobe Campaign in Linux [deze sectie](../../installation/using/installing-campaign-standard-packages.md).

1. Ga naar de **nl6.back** back-upmap en kopieer (overschrijf) de configuratiebestanden en submappen van elke instantie. Aanmelden als **neolane** en voer de volgende opdracht uit:

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

1. Begin het postupgrade proces gebruikend het volgende bevel (nog **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## De omleidingsserver migreren (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Deze sectie is alleen van toepassing wanneer u migreert vanaf Adobe Campaign v5.11.

In dit stadium moet Apache worden stopgezet. Zie: [Servicestop](#service-stop).

1. Aanmelden als **basis**.
1. Wijzig de Apache-omgevingsvariabelen om deze te koppelen aan de **nl6** directory.

   * In **Debian**:

      ```
      vi /etc/apache2/envvars
      ```

   * In **Rode hoed**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. Voer vervolgens de volgende opdrachten uit:

   * In **Debian**:

      In de **nlsrv.load** bestand vervangen **nl5** with **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      De koppeling van het dialoogvenster **nlsrv.conf** en maak een nieuw bestand.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * In **Rode hoed**:

      Ga naar de **/usr/local/apache2/conf** map, bewerkt u de **http.conf** bestand en vervangen **nl5** with **nl6** in de volgende regels.

      In **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Ga naar de **alias.conf** bestand en alles vervangen **nl5** with **nl6**. Voer de volgende opdracht uit om dit in Debian te doen:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Beveiligingszones {#security-zones}

Als u vanaf v6.02 of eerder migreert, moet u uw veiligheidsstreken vormen alvorens de diensten te beginnen. Raadpleeg voor meer informatie [Beveiliging](../../migration/using/general-configurations.md#security).

## Herstart {#re-starting-services}

De procedure is afhankelijk van de vorige versie van Adobe Campaign.

### Voor Adobe Campaign v5 {#migrating-from-adobe-campaign-v5_11-2}

In de **config-`<instance name>`.xml** bestanden, activeer het automatisch opstarten van de **mta**, **wfserver**, **stat**, enz. diensten.

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

Voordat u verdergaat met de volgende stap, voert u een volledige test van de nieuwe installatie uit, controleert u of er geen regressies zijn en of alles werkt door alle aanbevelingen in het deelvenster [Algemene configuraties](../../migration/using/general-configurations.md) sectie.

### Voor Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

In de **config-`<instance name>`.xml** bestanden, activeer het automatisch opstarten van de **mta**, **wfserver**, **stat**, enz. diensten.

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

Test de nieuwe installatie volledig, controleer of deze niet achteruitgaat en zorg ervoor dat alles correct werkt door alle aanbevelingen in de [Algemene configuraties](../../migration/using/general-configurations.md) sectie.

### Voor Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Start Apache- en Adobe Campaign-services op elk van de volgende servers:

1. Tracking and redirection server.
1. Midsourcingserver.
1. Marketingsserver.

Test de nieuwe installatie volledig, controleer of deze niet achteruitgaat en zorg ervoor dat alles correct werkt door alle aanbevelingen in de [Algemene configuraties](../../migration/using/general-configurations.md) sectie.

## Vorige versie van Adobe Campaign verwijderen {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Deze sectie is alleen van toepassing wanneer u migreert vanaf Adobe Campaign v5.11.

Voordat u de Adobe Campaign v5-installatie verwijdert en wist, moet u de volgende aanbevelingen uitvoeren:

* Krijg de functionele teams om een volledige controle van de nieuwe installatie in werking te stellen.
* Verwijder Adobe Campaign v5 alleen als u er zeker van bent dat terugdraaien niet nodig is.

Verwijder de **nl5.back** directory. Aanmelden als **neolane** en voer de volgende opdracht uit:

```
su - neolane
rm -rf nl5.back
```

Start de server opnieuw.
