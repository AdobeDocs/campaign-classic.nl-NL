---
title: Een externe database openen
seo-title: Een externe database openen
description: Een externe database openen
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Een externe database openen{#accessing-an-external-database}

## Over Federale gegevenstoegang {#about-federated-data-access}

Adobe Campaign biedt de optie **Federated Data Access** (FDA) om gegevens te verwerken die zijn opgeslagen in een of meer externe databases: u hebt toegang tot externe gegevens zonder de structuur van Adobe Campagne-gegevens te wijzigen.

>[!CAUTION]
>
>De module **Federated Data Access** (FDA) is optioneel. Controleer uw licentieovereenkomst voor Adobe Campagne.
>  
>Bovendien is toegang tot een externe databank via de FDA alleen mogelijk voor installaties op locatie of hybride installaties.

### Exploitatiebeginsel {#operating-principle}

Met de optie FDA kunt u gegevens verzamelen van de SQL-bronnen en automatisch de structuur van de beoogde tabellen detecteren.

Als u deze functionaliteit wilt gebruiken, moet u:

1. Een externe database hebben die compatibel is met de Adobe Campagne FDA-module. De lijst met databasesystemen en compatibele versies wordt gedetailleerd weergegeven in de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). Gebruikers moeten ook over de [benodigde machtigingen](#remote-database-access-rights) beschikken in Adobe Campaign en in de externe database.
1. [Installeer de stuurprogramma](#specific-configurations-by-database-type) &#39;s die overeenkomen met uw database op de Adobe Campaign-server.
1. [Maak en configureer een extern account](#connecting-to-the-database) waarmee u de verbinding tussen Adobe Campagne en de externe database tot stand kunt brengen. Raadpleeg deze [pagina](../../platform/using/external-accounts.md)voor meer informatie over beschikbare externe accounts.
1. [Maak het leesschema](#creating-the-data-schema) van de externe database in Adobe Campaign. Hierdoor kunt u de gegevensstructuur van de externe database herkennen.
1. Uiteindelijk, [creeer een nieuwe doelafbeelding](#defining-data-mapping) van het eerder gecreeerd schema, in het geval waar de ontvangers van uw leveringen uit het externe gegevensbestand komen. Dit brengt bepaalde beperkingen met zich mee, met name wat betreft de personalisering van de leveringen.

Zodra het schema voor het lezen van gegevens is gemaakt, kunnen gegevens worden verwerkt in de workflows van Adobe Campagne. Zie [deze sectie](../../workflow/using/executing-a-workflow.md#architecture)voor meer informatie.

### Beste praktijken en aanbevelingen {#best-practices-and-recommendations}

De optie FDA is bedoeld om de gegevens in externe databases in batchmodus te manipuleren in workflows. Het gebruik van de FDA in een andere context, bijvoorbeeld voor eenheidsoperaties, moet met voorzichtigheid plaatsvinden (personalisatie, interactie, real-time leveringen, enz.).

Voordat u de externe database gaat misbruiken, moet u prestatietests uitvoeren om mogelijke problemen op te sporen en optimaliseren met deze optie.

Vermijd zoveel mogelijk de bewerkingen die zowel de Adobe-campagne als de externe database moeten gebruiken. Hiervoor kunt u:

* Exporteer de Adobe Campagne-database naar de externe database en voer de bewerkingen alleen uit vanuit de externe database voordat u de resultaten opnieuw importeert in Adobe Campagne.
* Verzamel de gegevens in de externe Adobe Campagne-database en voer de bewerkingen lokaal uit.

Als u personalisatie in uw leveringen wilt uitvoeren gebruikend gegevens van het externe gegevensbestand, verzamel de gegevens in een werkschema te gebruiken om het ter beschikking te stellen in een tijdelijke lijst. Dan gebruik de gegevens van de tijdelijke lijst om uw levering te personaliseren.

### Beperkingen {#limitations}

De optie FDA wordt onderworpen aan de beperking van het externe databasesysteem dat u gebruikt.

Om redenen van prestaties raden we u niet aan deze functionaliteit te gebruiken voor het uitvoeren van eenheidsbewerkingen (levering, personalisatie, Interactie-module, real-time).

## Specifieke configuraties per databasetype {#specific-configurations-by-database-type}

Afhankelijk van de externe databases die u vanuit Adobe Campaign kunt openen, moet u bepaalde specifieke configuraties uitvoeren. Bij deze configuraties worden vooral stuurprogramma&#39;s geïnstalleerd en worden omgevingsvariabelen opgegeven die bij elke RDBMS op de Adobe Campagneserver horen.

Als algemene regel geldt dat u de corresponderende clientlaag in de externe database op de Adobe Campaign-server moet installeren.

>[!NOTE]
>
>Compatibele versies worden vermeld in de Matrix [van de Verenigbaarheid van de](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA) Campagne.

### Toegang tot Hadoop configureren {#configure-access-to-hadoop}

Voor het maken van een verbinding met een externe database in Hadoop in FDA zijn de volgende configuraties op de Adobe Campagneserver vereist.

#### Voor Windows {#for-windows}

1. Installeer ODBC- en [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) -stuurprogramma&#39;s voor Windows.
1. Creeer DSN (de Naam van de Gegevensbron) door het hulpmiddel van de Beheerder van ODBC DataSource in werking te stellen. Een steekproef van DSN van het Systeem voor Hive wordt verstrekt voor u om te wijzigen.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Maak de externe account van Hadoop, zoals wordt beschreven in de sectie [Een gedeelde verbinding](#creating-a-shared-connection) maken.

#### Voor Linux {#for-linux}

1. Installeer unixodbc voor Linux.

   ```
   apt-get install unixodbc
   ```

1. Download en installeer ODBC-stuurprogramma&#39;s voor Apache Hive van HortonWorks: [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. Controleer de locatie van ODBC-bestanden.

   ```
   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. Maak de DSN (naam gegevensbron) en bewerk het bestand odbc.ini. Maak vervolgens een DSN voor uw Hive-verbinding.

   Hier volgt een voorbeeld voor HDInsight voor het instellen van een verbinding met de naam &quot;viral&quot;:

   ```
   [ODBC Data Sources]
   vorac 
   
   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >De parameter **UseNativeQuery** is hier erg belangrijk. De campagne is Hive-bewust en zal niet correct werken tenzij UseNativeQuery wordt geplaatst. Doorgaans herschrijft het stuurprogramma of de SQL-connector van Hive query&#39;s en wordt de kolomvolgorde gewijzigd.

   De authenticatie-instelling is afhankelijk van de Hive/Hadoop-configuratie. Bijvoorbeeld, voor HD Insight, gebruik AuthMech=6 voor gebruiker/wachtwoordauthentificatie, zoals [hier](http://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)beschreven.

1. Exporteer de variabelen.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. Stel Hortonworks-stuurprogramma&#39;s in via /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini.

   U moet UTF-16 gebruiken om verbinding te kunnen maken met Campagne en unix-odbc (libodbcinst).

   ```
   [Driver]
   
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp
   
   ODBCInstLib=libodbcinst.so
   ```

1. U kunt de verbinding nu testen met isql.

   ```
   isql vorac
   isql vorac -v
   ```

1. Maak de externe account van Hadoop, zoals wordt beschreven in de sectie [Een gedeelde verbinding](#creating-a-shared-connection) maken.

### Toegang tot MySQL configureren {#configure-access-to-mysql}

Voor meer informatie over hoe te om uw gegevensbestand te vormen MySQL, verwijs naar dit [artikel](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html).

### Toegang tot Netezza configureren {#configure-access-to-netezza}

Als u verbinding maakt met een externe Netezza-database in FDA, hebt u hieronder aanvullende configuraties op de Adobe Campagneserver nodig:

1. Installeer de ODBC-stuurprogramma&#39;s voor Netezza volgens het besturingssysteem dat u gebruikt:

   * **nz-linuxclient-v7.2.0.0.tar.gz** voor Linux. Selecteer de map die overeenkomt met uw besturingssysteem (linux of linux64) en start de opdracht Uitpakken. U kunt de installatie laten uitvoeren in de opslagplaats die standaard wordt voorgesteld: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip** voor Windows. Pak het bestand uit en start het uitvoerbare script dat overeenkomt met uw besturingssysteem: nzodbcsetup.exe of nzodbcsetup64.exe. Volg de aanwijzingen van de wizard om de installatie van de stuurprogramma&#39;s te voltooien.

1. Configureer het ODBC-stuurprogramma. De configuratie kan in de standaarddossiers worden uitgevoerd: **/etc/odbc.ini** voor algemene parameters en **/etc/odbcinst.ini** voor het declareren van stuurprogramma&#39;s.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; komt overeen met de locatie van het bestand odbcinst.ini.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Geef de omgevingsvariabelen van de Adobe Campaign-server op:

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib en /usr/local/nz/lib64. &quot;/usr/local/nz&quot; komt overeen met de standaardopslagplaats voor de installatie van de stuurprogramma&#39;s. Hier moet u de opslagplaats specificeren die u voor de installatie hebt geselecteerd.
   * **ODBCINI**: locatie van het bestand odbc.ini (bijvoorbeeld /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: locatie van het bestand odbc.ini. Netezza vereist ook deze tweede variabele voor het gebruiken van het odbc.ini- dossier.

1. Maak de externe Netezza-account, zoals wordt beschreven in het gedeelte [Een gedeelde verbinding](#creating-a-shared-connection) maken.

>[!NOTE]
>
>Bewerkingen op schema&#39;s die automatisch gegenereerde primaire sleutels bevatten, worden niet in aanmerking genomen.
>
>De tabel gebruikt de component **Indelen op** de eerste index die in het schema is gedefinieerd. Aangezien deze clausule tot 1 tot 4 kolommen met Netezza beperkt is, kan deze index niet meer dan 4 kolommen bevatten.

### Toegang tot Oracle configureren {#configure-access-to-oracle}

Als u verbinding wilt maken met een externe Oracle-database in FDA, hebt u hieronder aanvullende configuraties op de Adobe Campaign-server nodig.

#### Voor Linux {#for-linux-1}

1. Installeer de volledige Oracle-client die overeenkomt met uw versie van Oracle.
1. Voeg uw definities TNS aan uw installatie toe. Om dit te doen, specificeer hen in een **tnsnames.ora** - dossier in de /etc/oracle bewaarplaats. Als deze gegevensopslagruimte niet bestaat, maakt u deze.

   Maak vervolgens een nieuwe omgevingsvariabele TNS_ADMIN: Exporteer TNS_ADMIN=/etc/oracle en start de computer opnieuw op.

1. Integreer Oracle in uw Adobe Campaign-server (nlserver). Hiervoor controleert u of het bestand **customer.sh** aanwezig is in de map &quot;nl6&quot; van de boomstructuur van de Adobe Campagne-server en of dit bestand de koppelingen naar de Oracle-bibliotheken bevat.

   Bijvoorbeeld voor een client in 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Deze waarden (in het bijzonder ORACLE_HOME) zijn afhankelijk van de installatieregisters. Controleer de boomstructuur voordat u naar deze waarden verwijst.

1. Installeer de bibliotheken die nodig zijn voor Oracle:

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

#### Voor Windows {#for-windows-1}

1. Installeer de Oracle-client.
1. Maak in de map C:Oracle een bestand **tnsnames.ora** met uw TNS-definitie.

   Voeg een omgevingsvariabele TNS_ADMIN toe met C:Oracle als waarde en start de computer opnieuw op.

### Toegang tot Sybase IQ configureren {#configure-access-to-sybase-iq}

Als u verbinding maakt met een externe Sybase-IQ-database in FDA, hebt u hieronder aanvullende configuraties op de Adobe Campagneserver nodig:

1. Zorg ervoor dat het unixodbc-pakket zich op de server bevindt.
1. Installeer **iq_odbc**. Er kan een fout optreden aan het einde van de installatie. Deze fout kan worden genegeerd.
1. Installeer **iq_client_common**. Er kan een Java-fout optreden aan het einde van de installatie. Deze fout kan worden genegeerd.
1. Configureer het ODBC-stuurprogramma. De configuratie kan in de standaarddossiers worden uitgevoerd: /etc/odbc.ini voor algemene parameters en /etc/odbcinst.ini voor het declareren van stuurprogramma&#39;s:

   * **/etc/odbc.ini** (vervang uw eigen waarden, zoals `<server_alias>` tekens):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Voeg het pad voor de nieuwe bibliotheek libodbc16.so toe in de variabele LD_LIBRARY_PATH. Dat doet u als volgt:

   * Als u een bestand customer.sh gebruikt om het pad te declareren: Voeg het pad /opt/sybase/IQ-16_0/lib64 toe voor de variabele LD_LIBRARY_PATH.
   * Gebruik anders een Unix-opdracht.

1. Maak een nieuwe externe FDA-account, zoals wordt beschreven in de sectie [Een gedeelde verbinding](#creating-a-shared-connection) maken. Voor Sybase IQ komt de servernaam overeen met de ODBC-verbinding (`<server_alias>`) die is gedefinieerd in stap 5. Het is niet noodzakelijkerwijs de naam van de server zelf.

>[!NOTE]
>
>Voor Windows moet u de Sybase IQ-client installeren op de Adobe Campaign-server en een ODBC-verbinding maken. Zorg ervoor u een systeemgegevensbron creeert wanneer de server van de Campagne van Adobe (nlserver) als dienst in Vensters loopt.

### Toegang tot metagegevens configureren {#configure-access-to-teradata}

Als u verbinding wilt maken met een externe database met Teradata in FDA, hebt u bepaalde aanvullende configuraties op de Adobe Campagneserver nodig. Raadpleeg dit [artikel](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html)voor meer informatie over het configureren van uw Teradata-database.

1. Installeer het [ODBC-stuurprogramma voor Teradata](http://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   Het bestaat uit drie pakketten die in de volgende volgorde op Red Hat (of CentOS)/Suse kunnen worden geïnstalleerd:

   * TeraGSS
   * tdicu1510 (installeer het met setup_wrapper.sh)
   * tdodbc1510 (installeer het met setup_wrapper.sh)

1. Configureer het ODBC-stuurprogramma. De configuratie kan in de standaarddossiers worden uitgevoerd: **/etc/odbc.ini** voor algemene parameters en /etc/odbcinst.ini voor het declareren van bestuurders:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; komt overeen met de locatie van het bestand **odbcinst.ini** .

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. Geef de omgevingsvariabelen van de Adobe Campaign-server op:

   * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64 and /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: locatie van het bestand odbc.ini (bijvoorbeeld /etc/odbc.ini).
   * **NLSPATH**: locatie van het bestand opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)

### Toegang tot SAP HANA configureren {#configure-access-to-sap-hana}

Als u verbinding maakt met een externe SAP HANA-database in FDA, hebt u bepaalde aanvullende configuraties op de Adobe Campagneserver nodig:

1. Installeer de ODBC-stuurprogramma&#39;s voor SAP HANA, afhankelijk van het besturingssysteem dat u gebruikt:

   * **hdb_client_linux.tgz** voor Linux. Nadat u de installatie hebt beëindigd, start u de hdbinst-opdracht en volgt u de instructies om de installatie van de stuurprogramma&#39;s te voltooien.
   * **hdb_client_windows.zip** voor Windows. Pak het bestand uit en start het uitvoerbare bestand: **hdbinst.exe**. Volg de aanwijzingen van de wizard om de installatie van de stuurprogramma&#39;s te voltooien.

1. Configureer het ODBC-stuurprogramma. De configuratie kan in de standaarddossiers worden uitgevoerd: /etc/odbc.ini voor algemene parameters en /etc/odbcinst.ini voor het declareren van stuurprogramma&#39;s.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot; komt overeen met de locatie van het bestand **odbcinst.ini** .

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Geef de omgevingsvariabelen van de Adobe Campaign-server op:

   * **LD_LIBRARY_PATH**: De koppeling naar uw SAP Hana-client (standaard is dit de koppeling /usr/sap/hdbclient/ [libodbcHDB.so](http://libodbchdb.so/) ).
   * **ODBCINI**: locatie van het bestand odbc.ini (bijvoorbeeld /etc/odbc.ini).

1. Maak de externe SAP Hana-account, zoals wordt beschreven in de sectie [Een gedeelde verbinding](#creating-a-shared-connection) maken.

## Toegangsrechten externe database {#remote-database-access-rights}

Ten eerste, zodat de gebruiker bewerkingen kan uitvoeren op een externe database via FDA, moet de gebruiker een specifiek benoemd recht hebben in Adobe Campaign.

1. Selecteer het **[!UICONTROL Administration > Access Management > Named Rights]** knooppunt in de Adobe Campaign Explorer.
1. Maak een nieuw recht door het gekozen label op te geven.
1. Het **[!UICONTROL Name]** veld moet de volgende **indelingsgebruiker hebben:base@server**, waarbij:

   * **gebruiker** komt overeen met de naam van de gebruiker in de externe database.
   * **de basis** komt overeen met de naam van de externe database.
   * **server** komt overeen met de naam van de externe databaseserver.

      >[!NOTE]
      >
      >Het **:base** -onderdeel is optioneel in Oracle.

1. Sla het benoemde recht op en koppel het aan de door u gekozen gebruiker vanuit het **[!UICONTROL Administration > Access Management > Operators]** knooppunt van de Adobe Campagneverkenner.

Als u vervolgens de gegevens in een externe database wilt verwerken, moet de Adobe Campagnegebruiker ten minste schrijfrechten voor de database hebben om werktabellen te kunnen maken. Deze worden automatisch verwijderd door Adobe Campaign.

In het algemeen zijn de volgende rechten noodzakelijk:

* **VERBINDING**: verbinding met de externe database,
* **LEESgegevens**: alleen-lezen toegang tot tabellen met klantgegevens,
* **&#39;MetaData&#39;** LEZEN: toegang tot de catalogi van servergegevens om de tabelstructuur te verkrijgen;
* **LADEN**: massabelasting in werktafels (vereist bij het werken aan verzamelingen en verbindingen);
* **CREATE/DROP** for **TABLE/INDEX/PROCEDURE/FUNCTION**,
* **EXPLAIN** (aanbevolen): voor het toezicht op prestaties in geval van problemen;
* **SCHRIJF Gegevens** (afhankelijk van het integratiescenario).

>[!NOTE]
>
>De gegevensbestandbeheerder moet deze rechten met de rechten aanpassen specifiek voor elke gegevensbestandmotor. Raadpleeg de specifieke rechten [van](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html)RDBMS voor meer informatie.

## Verbinding maken met de database {#connecting-to-the-database}

Als u een verbinding met de externe database wilt inschakelen, moet u de verbindingsparameters aangeven, dat wil zeggen de doelgegevensbron en de naam van de tabel met gegevens die moeten worden geladen.

>[!CAUTION]
>
>De gebruiker van de Campagne van Adobe heeft specifieke rechten voor het externe gegevensbestand en de de toepassingsserver van de Campagne van Adobe nodig om gegevens van een externe gegevensbestand te verwerken. Voor meer op dit, verwijs naar de [Verre sectie van de de toegangsrechten](#remote-database-access-rights) van het gegevensbestandtoegang.
>
>Om storingen te voorkomen, moeten operatoren die toegang krijgen tot externe, gedeelde gegevens werken vanuit aparte ruimten.

### Een gedeelde verbinding maken {#creating-a-shared-connection}

Als u een verbinding met een gedeelde externe database wilt inschakelen, zolang deze verbinding actief is, kunt u de database openen via Adobe Campaign.

1. De configuratie moet vooraf via de **[!UICONTROL Administration > Platform > External accounts]** knoop worden bepaald.
1. Klik op de **[!UICONTROL New]** knop en selecteer het **[!UICONTROL External database]** type.
1. Definieer de **[!UICONTROL Connection]** parameters van de externe database.

   Voor verbindingen met een **ODBC** typedatabase moet het **[!UICONTROL Server]** veld de naam van de ODBC-gegevensbron bevatten en niet de servernaam. Bovendien kunnen bepaalde aanvullende configuraties noodzakelijk zijn, afhankelijk van de gebruikte databanken. Raadpleeg de sectie [Specifieke configuraties per databasetype](#specific-configurations-by-database-type) .

1. Nadat de parameters zijn ingevoerd, klikt u op de **[!UICONTROL Test the connection]** knop om deze goed te keuren.

   ![](assets/wf-external-account-create.png)

1. Schakel indien nodig de **[!UICONTROL Enabled]** optie uit om toegang tot deze database uit te schakelen zonder de configuratie ervan te verwijderen.
1. Als u Adobe Campaign toegang wilt geven tot deze database, moet u de SQL-functies implementeren. Klik op het **[!UICONTROL Parameters]** tabblad en vervolgens op de **[!UICONTROL Deploy functions]** knop.

   ![](assets/wf-external-account-functions.png)

U kunt specifieke werktabelruimten definiëren voor de tabellen en voor de index op het **[!UICONTROL Parameters]** tabblad.

### Verbinding maken met Windows-verificatie {#creating-a-connection-with-windows-authentication}

U kunt ook verbinding maken via FDA met Windows-verificatie. Dit doet u als volgt:

* Zorg ervoor dat de Adobe Campagne-service wordt uitgevoerd door een Windows-account die afwijkt van het lokale systeemaccount.
* Zorg ervoor dat de Adobe Campaign-operator voldoende rechten heeft voor de Adobe Campagne-toepassingsserver en de externe database.
* Maak de corresponderende externe account zonder de **[!UICONTROL Account]** en de **[!UICONTROL Password]**. Geef alleen de naam van de database op.

### Tijdelijke verbinding maken {#creating-a-temporary-connection}

U kunt rechtstreeks vanuit workflowactiviteiten een verbinding met een externe database definiëren. In dit geval bevindt het bestand zich in een lokale externe database die is gereserveerd voor gebruik in een huidige workflow: het wordt niet opgeslagen op de externe accounts. Dit type punctuele verbinding kan op verschillende activiteiten van het werkschema worden tot stand gebracht, met name de **[!UICONTROL Query]**, de **[!UICONTROL Data loading (RDBMS)]**, de **[!UICONTROL Enrichment]** activiteit of de **[!UICONTROL Split]** activiteit.

>[!CAUTION]
>
>Dit type configuratie wordt niet aanbevolen, maar kan periodiek worden gebruikt om gegevens te verzamelen. Desalniettemin moet u een externe account maken, zoals wordt weergegeven in de sectie [Een gedeelde verbinding](#creating-a-shared-connection) maken.

In de queryactiviteit ziet u bijvoorbeeld de volgende stappen voor het maken van een periodieke verbinding met een externe database:

1. Klik op de knop **[!UICONTROL Add data...]** en selecteer de **[!UICONTROL External data]** opties.
1. Selecteer de **[!UICONTROL Locally defining the data source]** optie.

   ![](assets/wf_add_data_local_external_data.png)

1. Selecteer de doeldatabase-engine in de vervolgkeuzelijst. Voer de naam van de server in en geef de verificatieparameters op.

   Geef ook de naam van de externe database op.

   ![](assets/wf_add_data_local_external_data_param.png)

   Klik op de **[!UICONTROL Next]** knop.

1. Selecteer de tabel waarin de gegevens zijn opgeslagen.

   U kunt de naam van de tabel rechtstreeks in het desbetreffende veld invoeren of op het pictogram Bewerken klikken om de lijst met databasetabellen te openen.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. Klik op de **[!UICONTROL Add]** knop om een of meerdere afstemmingsvelden te definiëren tussen de externe databasegegevens en de gegevens in de Adobe Campagne-database. De **[!UICONTROL Edit expression]** pictogrammen van de tabel **[!UICONTROL Remote field]** en **[!UICONTROL Local field]** bieden u toegang tot de lijst met velden van elk van de tabellen.

   ![](assets/wf_add_data_local_external_data_join.png)

1. Geef zo nodig een filtervoorwaarde en de gegevenssorteermodus op.
1. Selecteer de aanvullende gegevens die in de externe database moeten worden verzameld. Dubbelklik hiertoe op de velden die u wilt toevoegen om deze weer te geven in het **[!UICONTROL Output columns]** deelvenster.

   ![](assets/wf_add_data_local_external_data_select.png)

   Klik **[!UICONTROL Finish]** om deze configuratie te bevestigen.

### Beveiligde verbinding {#secure-connection}

U kunt toegang tot een extern gegevensbestand beveiligen wanneer het vormen van een externe rekening FDA.

Hiervoor voegt u &quot;**:ssl**&quot; toe na het serveradres en het adres van de gebruikte poort. Bijvoorbeeld: **192.168.0.52:4501:ssl**.

De gegevens worden vervolgens verzonden via het veilige SSL-protocol.

### Aanvullende configuraties {#additional-configurations}

Indien nodig, kunt u het schema voor de verwerking van gegevens in een extern gegevensbestand tot stand brengen. Op dezelfde manier kunt u in Adobe Campaign toewijzingen definiëren voor de gegevens in een externe tabel. Deze configuraties zijn algemeen en zijn niet uitsluitend van toepassing op workflows.

>[!NOTE]
>
>Raadpleeg [deze pagina](../../configuration/using/about-schema-edition.md)voor meer informatie over het maken van schema&#39;s in Adobe Campaign en het definiëren van een nieuwe gegevenstoewijzing.

## Het gegevensschema maken {#creating-the-data-schema}

Als u een schema wilt maken voor een externe database, klikt u op de **[!UICONTROL New]** knop boven de lijst met gegevensschema&#39;s en kiest u **[!UICONTROL Access external data]**.

![](assets/wf_new_schema_fda.png)

Voer een naam en beschrijving in voor het schema en selecteer de externe account waarmee verbinding met de database kan worden gemaakt. Hierdoor hebt u toegang tot de lijst met tabellen die beschikbaar zijn in de externe basis. Kies de tabel met de gegevens die moeten worden verzameld.

![](assets/wf_new_schema_select_table_fda.png)

Klik **[!UICONTROL OK]** om te bevestigen. Adobe Campaign detecteert automatisch de structuur van de geselecteerde tabel en genereert het logische schema.

>[!NOTE]
>
>Adobe Campaign genereert geen koppelingen.

Klik **[!UICONTROL Save]** om het maken te bevestigen.

![](assets/wf_new_schema_generate_fda.png)

De indexen worden automatisch gemaakt wanneer een tabel (standaard- of FDA-toewijzing) wordt toegewezen.

## Gegevenstoewijzing definiëren {#defining-data-mapping}

Met Adobe Campaign kunt u toewijzingen definiëren voor de gegevens in een externe tabel.

Om dit te doen, zodra het schema van de externe lijst is gecreeerd, moet u een nieuwe leveringsafbeelding tot stand brengen om de gegevens in deze lijst als leveringsdoel te gebruiken.

Hiervoor voert u de volgende stappen uit:

1. Maak een nieuwe leveringstoewijzing en kies de doeldimensie, het schema dat u net hebt gemaakt, bijvoorbeeld.

   ![](assets/wf_new_mapping_create_fda.png)

1. Geef de velden op waarin de leveringsgegevens zijn opgeslagen (achternaam, voornaam, e-mail, adres, enz.).

   ![](assets/wf_new_mapping_define_join.png)

1. Specificeer de parameters voor informatieopslag, met inbegrip van het achtervoegsel van de uitbreidingsregelingen om hen gemakkelijk identificeerbaar te zijn.

   ![](assets/wf_new_mapping_define_names.png)

   U kunt kiezen of u uitsluitingen (**excludelog**), berichten (**broadlog**) of in een aparte tabel wilt opslaan.

   U kunt ook kiezen of u het bijhouden van gegevens voor deze leveringstoewijzing (**trackinglog**) wilt beheren.

1. Selecteer vervolgens de extensies waarmee u rekening wilt houden. Het extensietype is afhankelijk van de parameters en opties van uw platform (uw licentiecontract weergeven).

   ![](assets/wf_new_mapping_define_extensions.png)

   Klik op de **[!UICONTROL Save]** knop om het maken van de leveringstoewijzing te starten: alle gekoppelde tabellen worden automatisch gemaakt op basis van de geselecteerde parameters.

## Aanvullende opties {#additional-options}

### HTTP-relais naar een externe instantie {#http-relay-to-a-remote-instance}

U kunt tot externe gegevensbestanden toegang hebben die in verre instanties worden gevormd gebruikend het protocol van HTTP.

>[!NOTE]
>
>Niet alle SQL-gegevenstypen worden door deze functie ondersteund. Blob-gegevenstypen worden helemaal niet ondersteund. Het is mogelijk dat andere gegevenstypen niet werken afhankelijk van de beoogde database (bijvoorbeeld Tijdstempel op Microsoft SQL Server). Neem contact op met de ondersteuning van Adobe voor meer informatie.

Dit vereenvoudigt het overbrengen van en het synchroniseren van gegevens tussen twee instanties. Het laat u ook toe om het even welke het een tunnel graven tussen een instantie en een ver gegevensbestand evenals de installatie van de cliëntlagen te negeren om tot dit gegevensbestand toegang te hebben. De doelinstantie kan een gehoste instantie zijn.

>[!CAUTION]
>
>Deze optie is alleen bedoeld om gegevensreplicatiestromen (ETL) te vergemakkelijken.
>
>Zo kan een in de cloud gehoste instantie rechtstreeks toegang krijgen tot de gegevens in een op locatie gehoste database. Het is echter niet de bedoeling toe te staan dat gerichte toepassingen rechtstreeks vanuit de cloud worden uitgevoerd in een op locatie gehoste database.

Hiervoor moet u de externe accounts van de twee instanties configureren, zodat de lokale instantie kan communiceren met de externe instantie via het HTTP-protocol:

* Lokale instantie: Selecteer het nieuwe **[!UICONTROL HTTP relay to a remote database]** verbindingstype.

   Geef in het geval van gegevensoverdracht met bulkgegevens ook de buffergrootte op. Selecteer de compressieoptie als u de grootte van de overgedragen gegevens wilt verkleinen.

   De syntaxis **[!UICONTROL Data source]** moet als volgt worden gedefinieerd: &quot;nms:extAccount: `<internal_name_of_the_external_account>`&quot;

   ![](assets/fda_over_http_1.png)

   >[!NOTE]
   >
   >We raden u aan een HTTPS-verbinding te gebruiken.

* Externe instantie: in de FDA externe rekening van het gegevensbestand dat via het HTTP relais wordt betreden, controleer het Doel van een **[!UICONTROL 'HTTP relay to a remote database' account option]**.

   ![](assets/fda_over_http_2.png)

In het volgende voorbeeld wordt de nieuwe mogelijke besturingsmodus getoond:

![](assets/schema_fda_over_http_2.png)

>[!CAUTION]
>
>De standaarddatabase van de externe instantie moet ook via een externe account worden geopend.

Deze werkende methode vermijdt dat het schoonmaakwerkschema van elke instantie de het werklijsten van de gegevensbestanden schrapt die de instantie als relais gebruiken.

In het vorige voorbeeld voert de opschoonworkflow van de externe instantie dus geen actie uit op de rode FDA-database, zoals deze wordt gebruikt door de lokale instantie.

### Direct tijdelijke schema&#39;s maken {#directly-creating-temporary-schemas}

Als u meerdere toegangsmogelijkheden tot een externe FDA-database wilt beheren, kunt u met een nieuwe optie rechtstreeks een werkschema maken wanneer u een externe account configureert.

>[!NOTE]
>
>Deze optie werkt alleen met PostgreSQL.

![](assets/fda_work_table.png)

### E-mailpersonalisatie optimaliseren met externe gegevens {#optimizing-email-personalization-with-external-data}

Vanaf build 8740 **[!UICONTROL Prepare the personalization data with a workflow]** is de optie nu beschikbaar op het **[!UICONTROL Analysis]** tabblad van de leveringseigenschappen.

Tijdens de leveringsanalyse, leidt deze optie automatisch tot en voert een werkschema uit dat alle gegevens met betrekking tot het doel in een tijdelijke lijst, met inbegrip van gegevens van lijsten verbonden in FDA opslaat.

Door deze optie in te schakelen, kunt u een aanzienlijke prestatieverbetering bereiken voor het uitvoeren van personalisatie.

### Cloud Messaging - FDA-synchronisatie {#cloud-messaging---fda-synchronization}

Wanneer de server van het Overseinen van de Wolk en de server van de Marketing niet lange periode zijn gesynchroniseerd, kan het volume van ontbrekende uitzendingen op de server van de Marketing significant zijn. Om de synchronisatie van de uitzending via FDA te optimaliseren, is de optie **NmsMidSourcing_LogsPeriodHour** toegevoegd. Hierdoor kan een maximumperiode (uitgedrukt in uren) worden opgegeven om het aantal herstelde uitzendingen te beperken telkens wanneer de synchronisatieworkflow wordt uitgevoerd.

De optie moet in de console, in de **[!UICONTROL Administration > Options]** knoop worden toegevoegd.

>[!CAUTION]
>
>Deze optie mag **alleen** worden gebruikt voor het synchroniseren van een significant volume van uitzendingen via de FDA.

>[!NOTE]
>
>Met deze optie wordt alleen rekening gehouden als er een laatste hersteldatum bestaat (optie **NmsMidSourcing_LastBroadLog_*** ).

### Berichtcentrum - Toegang lezen op de tabel XtkFolder {#message-center---read-access-on-the-xtkfolder-table}

Vanaf build 8141 en hoger is handmatige actie vereist als Message Center de FDA als archiveringsmodus gebruikt.

U moet leestoegang op de tabel XtKFolder verlenen aan de gebruiker die is gekoppeld aan de externe FDA-account.

Voor bijvoorbeeld een PostSQL-database is de opdracht als volgt:

```
GRANT SELECT ON XtkFolder TO DBUSER;
```

Deze gebruiker moet lees toegang tot de volgende lijsten hebben:

* NmsBroadLogRtEvent
* NmsBroadLogBatchEvent
* NmsTrackingLogRtEvent
* NmsTrackingLogBatchEvent
* NmsRtEvent
* NmsBatchEvent
* NmsBroadLogMsg
* NmsTrackingUrl
* NmsDelivery
* NmsWebTrackingLog

>[!NOTE]
Deze wijziging verwijdert het foutbericht &quot;Permission deny for relation xtkfolder&quot;.

Als het werkschema dat in de externe FDA-account is geselecteerd, niet de uit-de-box Neolane-account is, is deze wijziging van de toegangsrechten niet nodig.

## Gegevens uit een externe database gebruiken in een workflow {#using-data-from-an-external-database-in-a-workflow}

Bij verschillende Adobe Campagne-workflowactiviteiten kunt u de gegevens gebruiken die in een externe database zijn opgeslagen.

### Filteren op externe gegevens {#filtering-on-external-data}

De vraagactiviteit staat u toe om externe gegevens toe te voegen en het in de bepaalde filterconfiguraties te gebruiken.

Raadpleeg de sectie [Query](../../workflow/using/targeting-data.md#selecting-data) voor meer informatie.

### Subsets maken {#creating-sub-sets}

Met de splitsingsactiviteit kunt u subsets maken. U kunt externe gegevens gebruiken om de filtercriteria te bepalen aan gebruik.

Raadpleeg de sectie [Splitsen](../../workflow/using/split.md) voor meer informatie hierover.

### Externe database laden {#loading-external-database}

U kunt de externe gegevens gebruiken in het laden van gegevens (RDBMS). Deze activiteit wordt voorgesteld in de het laden [van](../../workflow/using/data-loading--rdbms-.md) Gegevens sectie.

### Informatie en koppelingen toevoegen {#adding-information-and-links}

Met de verrijkingsactiviteit kunt u aanvullende gegevens toevoegen aan de werktabel van de workflow en koppelingen naar een externe tabel. Om deze reden, kan het de gegevens van een extern gegevensbestand exploiteren. Deze activiteit wordt vermeld in het gedeelte [Verrijking](../../workflow/using/enrichment.md) .
