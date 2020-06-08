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
source-git-commit: cc9ea59a9925930d4a4b260ce73a6bd4b615db5a
workflow-type: tm+mt
source-wordcount: '2857'
ht-degree: 0%

---


# Specifieke configuraties per databasetype {#specific-configurations-by-database-type}

Afhankelijk van de externe databases die u vanuit Adobe Campaign kunt openen, moet u bepaalde specifieke configuraties uitvoeren. Bij deze configuraties worden vooral stuurprogramma&#39;s geïnstalleerd en worden omgevingsvariabelen opgegeven die bij elke RDBMS op de Adobe Campagneserver horen.

Als algemene regel geldt dat u de corresponderende clientlaag in de externe database op de Adobe Campaign-server moet installeren.

>[!NOTE]
>
>Compatibele versies worden vermeld in de Matrix [van de Verenigbaarheid van de](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA)Campagne.

## Toegang tot Azure Synapse configureren {#configure-access-to-azure-synapse}

### Azure synapse external account {#azure-external}

Met de [!DNL Azure] externe account kunt u uw Campagne-instantie verbinden met uw externe database van Azure Synapse.
Een externe [!DNL Azure Synapse] account maken:

1. Configureer uw [!DNL Azure Synapse] externe account in Campaign Classic. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL Create]**.

1. Configureer de [!DNL Azure Synapse] externe account. Geef de volgende instellingen op:

   * **[!UICONTROL Type]**: Azure Synapse Analytics

   * **[!UICONTROL Server]**: URL van de Azure Synapse-server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database
   ![](assets/azure_1.png)

### Azure Synapse op CentOS {#azure-centos}

**Vereisten:**

* U hebt basisrechten nodig om een ODBC-stuurprogramma te installeren.
* Red Hat Enterprise ODBC-stuurprogramma&#39;s van Microsoft kunnen ook worden gebruikt met CentOS om verbinding te maken met SQL Server.
* Versie 13.0 werkt met Red Hat 6 en 7.

Om Azure Synapse op CentOS te vormen:

1. Installeer eerst het ODBC-stuurprogramma. U vindt deze op deze [pagina](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

   >[!NOTE]
   >
   >Dit is exclusief voor versie 13 van het ODBC-stuurprogramma.

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   # Uninstall if already installed Unix ODBC driver
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   
   sudo ACCEPT_EULA=Y yum install msodbcsql
   
   sudo ACCEPT_EULA=Y yum install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   
   # the Microsoft driver expects unixODBC to be here /usr/lib64/libodbc.so.1, so add soft links to the '.so.2' files
   cd /usr/lib64
   sudo ln -s libodbccr.so.2   libodbccr.so.1
   sudo ln -s libodbcinst.so.2 libodbcinst.so.1
   sudo ln -s libodbc.so.2     libodbc.so.1
   
   # Set the path for unixODBC
   export ODBCINI=/usr/local/etc/odbc.ini
   export ODBCSYSINI=/usr/local/etc
   source ~/.bashrc
   
   #Add a DSN information to /etc/odbc.ini
   sudo vi /etc/odbc.ini
   
   #Add the following:
   [Azure Synapse Analytics]
   Driver      = ODBC Driver 13 for SQL Server
   Description = Azure Synapse Analytics DSN
   Trace       = No
   Server      = [insert your server here]
   ```

1. Indien nodig, kunt u UnixODBC ontwikkelingsheaders installeren door het volgende bevel in werking te stellen:

   ```
   sudo yum install unixODBC-devel
   ```

1. Nadat u de stuurprogramma&#39;s hebt geïnstalleerd, kunt u het ODBC-stuurprogramma testen en controleren en zo nodig een query uitvoeren op uw database. Voer de volgende opdracht uit:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. In Campaign Classic kunt u uw [!DNL Azure Synapse] externe account vervolgens configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#azure-external)voor meer informatie over het configureren van uw externe account.

1. Aangezien Azure Synapse Analytics via de haven van TCP 1433 communiceert, moet u deze haven op uw firewall openen. Gebruik de volgende opdracht:

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Om communicatie van de zijde van Analytics van de Stedelijke Synapse toe te staan zou u uw openbare IP kunnen moeten whitelist. Raadpleeg de [Azure-documentatie](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)om dit te doen.

1. Voer in het geval van iptables de volgende opdracht uit:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

### Azure Synapse in Windows {#azure-windows}

>[!NOTE]
>
>Dit is exclusief voor versie 13 van het ODBC-stuurprogramma, maar Adobe Campaign Classic kan ook SQL Server Native Client drivers 11.0 en 10.0 gebruiken.

Om Azure Synapse op Vensters te vormen:

1. Installeer eerst het Microsoft ODBC-stuurprogramma. U vindt deze op deze [pagina](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Kies de volgende bestanden om te installeren:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. Nadat het ODBC-stuurprogramma is geïnstalleerd, kunt u het indien nodig testen. Raadpleeg deze [pagina](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server)voor meer informatie.

1. In Campaign Classic kunt u uw [!DNL Azure Synapse] externe account vervolgens configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#azure-external)voor meer informatie over het configureren van uw externe account.

1. Aangezien Azure Synapse Analytics door de haven van TCP 1433 communiceert, moet u deze haven op de Firewall van de Verdediger van Vensters openen. Raadpleeg de documentatie [bij](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule)Windows voor meer informatie.

### Azure Synapse on Debian {#azure-debian}

**Vereisten:**

* U hebt basisrechten nodig om een ODBC-stuurprogramma te installeren.
* Er is een curve nodig om het msodbcsql-pakket te installeren. Als u het geïnstalleerd hebt, stel het volgende bevel in werking:

   ```
   sudo apt-get install curl
   ```

Om Azure Synapse op Debian te vormen:

1. Installeer eerst het Microsoft ODBC-stuurprogramma voor SQL Server. Gebruik de volgende bevelen om Bestuurder ODBC 13.1 voor SQL Server te installeren:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. Als u de volgende fout krijgt **&quot;Het methodebestuurder /usr/lib/apt/methods/https kon niet worden gevonden&quot;** wanneer het roepen van **sudo apt-get update**, zou u het bevel moeten in werking stellen:

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. U moet nu mssql-hulpmiddelen met de volgende bevelen installeren. Mssq-hulpmiddelen zijn nodig om het bulkexemplaarprogramma (of BCP) nut te gebruiken en vragen in werking te stellen.

   ```
   sudo ACCEPT_EULA=Y apt-get install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

1. Indien nodig, kunt u UnixODBC ontwikkelingsheaders installeren door het volgende bevel in werking te stellen:

   ```
   sudo yum install unixODBC-devel
   ```

1. Nadat u de stuurprogramma&#39;s hebt geïnstalleerd, kunt u het ODBC-stuurprogramma testen en controleren en zo nodig een query uitvoeren op uw database. Voer de volgende opdracht uit:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. In Campaign Classic kunt u nu uw [!DNL Azure Synapse] externe account configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#azure-external)voor meer informatie over het configureren van uw externe account.

1. Om iptables op Debian te vormen om de verbinding met Azure Analytics van de Synapse te verzekeren, laat de uitgaande haven TCP 1433 voor uw hostname met het volgende bevel toe:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Om communicatie van de zijde van Analytics van de Stedelijke Synapse toe te staan zou u uw openbare IP kunnen moeten whitelist. Raadpleeg de [Azure-documentatie](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)om dit te doen.

## Toegang tot Snowflake configureren {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake] de schakelaar is beschikbaar voor ontvangen en on-premise plaatsingen. For more on this, refer to [this article](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Sneeuwvlokken externe account {#snowflake-external}

Met de [!DNL Snowflake] externe account kunt u uw Campagne-instantie verbinden met uw Snowflake externe database.

1. Configureer uw [!DNL Snowflake] externe account in Campaign Classic. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Selecteer de ingebouwde **[!UICONTROL Snowflake]** externe account.

1. Configureer de **[!UICONTROL Snowflake]** externe account. Geef de volgende instellingen op:

   * **[!UICONTROL Server]**: URL van de [!DNL Snowflake] server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database
   ![](assets/snowflake.png)

1. Klik op het **[!UICONTROL Parameters]** tabblad en vervolgens op de **[!UICONTROL Deploy functions]** knop om functies te maken.

   ![](assets/snowflake_2.png)

De connector ondersteunt de volgende opties:

| Option | Beschrijving |
|---|---|
| werkschema | Databaseschema dat moet worden gebruikt voor werktabellen |
| entrepot | Naam van het standaardentrepot aan gebruik. De standaardinstelling van de gebruiker wordt hierdoor genegeerd. |
| TimeZoneName | Door gebrek leeg, zo betekent het dat de systeemtijdzone van de Klassieke toepassingsserver van de Campagne wordt gebruikt. De optie kan worden gebruikt om de TIMEZONE-sessieparameter te forceren. <br>Raadpleeg [deze pagina](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)voor meer informatie. |
| WeekStart | WEEK_START, sessieparameter. Standaard ingesteld op 0. <br>Raadpleeg [deze pagina](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start)voor meer informatie. |
| UseCachedResult | USE_CACHED_RESULTS sessieparameter. Standaard ingesteld op TRUE. U kunt deze optie gebruiken om de resultaten van Sneeuwvlokken in cache uit te schakelen. <br>Raadpleeg [deze pagina](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)voor meer informatie. |

### Sneeuwvlok op CentOS {#snowflake-centos}

1. Download de ODBC-stuurprogramma&#39;s voor [!DNL Snowflake]. [Klik hier](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) om te beginnen met downloaden.
1. Vervolgens moet u de ODBC-stuurprogramma&#39;s op CentOs installeren met de volgende opdracht:

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. Nadat u de ODBC-stuurprogramma&#39;s hebt gedownload en geïnstalleerd, moet u Campaign Classic opnieuw starten. Voer hiertoe de volgende opdracht uit:

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. In Campaign Classic kunt u uw [!DNL Snowflake] externe account vervolgens configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#snowflake-external)voor meer informatie over het configureren van uw externe account.

### Sneeuwvlok op Debian {#snowflake-debian}

1. Download de ODBC-stuurprogramma&#39;s voor [!DNL Snowflake]. [Klik hier](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) om te downloaden.

1. Vervolgens moet u de ODBC-stuurprogramma&#39;s op Debian installeren met de volgende opdracht:

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. Nadat u de ODBC-stuurprogramma&#39;s hebt gedownload en geïnstalleerd, moet u Campaign Classic opnieuw starten. Voer hiertoe de volgende opdracht uit:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic kunt u uw [!DNL Snowflake] externe account vervolgens configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#snowflake-external)voor meer informatie over het configureren van uw externe account.

### Sneeuwvlok in Windows {#snowflake-windows}

1. Download het [ODBC-stuurprogramma voor Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). U hebt beheerdersrechten nodig om het stuurprogramma te installeren. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configureer het ODBC-stuurprogramma. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. In Campaign Classic kunt u uw [!DNL Snowflake] externe account vervolgens configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#snowflake-external)voor meer informatie over het configureren van uw externe account.

## Toegang tot Hadoop 3.0 configureren {#configure-access-to-hadoop-3}

Als u verbinding wilt maken met een externe database in Hadoop in FDA, hebt u de volgende configuraties op de Adobe Campaign-server nodig. Deze configuratie is zowel voor Windows als voor Linux beschikbaar.

1. Download de ODBC-stuurprogramma&#39;s voor Hadoop, afhankelijk van uw OS-versie. Drivers vindt u op [deze pagina](https://www.cloudera.com/downloads.html).

1. Vervolgens moet u de ODBC-stuurprogramma&#39;s installeren en een DSN maken voor uw Hive-verbinding. Instructies vindt u op [deze pagina](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Nadat u de ODBC-stuurprogramma&#39;s hebt gedownload en geïnstalleerd, moet u Campaign Classic opnieuw starten. Voer hiertoe de volgende opdracht uit:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic kunt u vervolgens uw Snowflake externe account configureren. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klik **[!UICONTROL Create]** en selecteer **[!UICONTROL External database]** als Accounttype.

1. Als u de **[!UICONTROL  Hadoop]** externe account wilt configureren, moet u opgeven:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Naam van de DNS

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database als deze niet is opgegeven in DSN. Deze kan leeg worden gelaten, indien opgegeven in de DSN

   * **[!UICONTROL Time zone]**: Tijdzone van server
   ![](assets/hadoop3.png)

De schakelaar steunt de volgende opties ODBC:

| Naam | Waarde |
|---|---|
| ODBCMgr | iODBC |
| entrepot | 1/2/4 |

De aansluiting ondersteunt ook de volgende opties voor Hive:

| Naam | Waarde | Beschrijving |
|---|---|---|
| bulkKey | Azure-blob of DataLake-toegangssleutel | Voor wasb:// of wasbs:// (als het gereedschap voor bulkladen begint met wasb:// of wasbs://). <br>Het is de toegangstoets voor blok of DataLake emmertje voor bulklading. |
| hdfsPort | poortnummer <br>standaard ingesteld op 8020 | Voor HDFS bulkload (d.w.z. als het gereedschap voor bulkladen begint met webhdfs:// of webhdfss://). |
| bucketsNumber | 20 | Aantal emmers wanneer het creëren van een gegroepeerde lijst. |
| fileFormat | PARQUET | Standaardbestandsindeling voor werktabellen. |

## Toegang tot Hadoop 2.1 configureren {#configure-access-to-hadoop}

### Voor Windows {#for-windows}

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

1. Maak de externe account van Hadoop, zoals beschreven in [deze pagina](../../platform/using/external-accounts.md#hadoop-external-account) sectie.

### Voor Linux {#for-linux}

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

   De authenticatie-instelling is afhankelijk van de Hive/Hadoop-configuratie. Bijvoorbeeld, voor HD Insight, gebruik AuthMech=6 voor gebruiker/wachtwoordauthentificatie, zoals [hier](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)beschreven.

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

1. Maak de externe account van Hadoop, zoals beschreven in [deze pagina](../../platform/using/external-accounts.md#hadoop-external-account) sectie.

## Toegang tot Netezza configureren {#configure-access-to-netezza}

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

1. In Campaign Classic, kunt u uw externe rekening van Netezza dan vormen. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om de **[!UICONTROL Netezza]** externe rekening te vormen, moet u specificeren:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: URL van de Netezza-server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database

>[!NOTE]
>
>Bewerkingen op schema&#39;s die automatisch gegenereerde primaire sleutels bevatten, worden niet in aanmerking genomen.
>
>De tabel gebruikt de component **Indelen op** de eerste index die in het schema is gedefinieerd. Aangezien deze clausule tot 1 tot 4 kolommen met Netezza beperkt is, kan deze index niet meer dan 4 kolommen bevatten.

## Toegang tot Oracle configureren {#configure-access-to-oracle}

Als u verbinding wilt maken met een externe Oracle-database in FDA, hebt u hieronder aanvullende configuraties op de Adobe Campaign-server nodig.

### Voor Linux {#for-linux-1}

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

### Voor Windows {#for-windows-1}

1. Installeer de Oracle-client.
1. Maak in de map C:Oracle een bestand **tnsnames.ora** met uw TNS-definitie.

   Voeg een omgevingsvariabele TNS_ADMIN toe met C:Oracle als waarde en start de computer opnieuw op.

## Toegang tot Sybase IQ configureren {#configure-access-to-sybase-iq}

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

1. In Campaign Classic, kunt u uw externe rekening van Sybase IQ dan vormen. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om de **[!UICONTROL Sybase IQ]** externe rekening te vormen, moet u specificeren:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Komt overeen met de ODBC-verbinding (`<server_alias>`) die is gedefinieerd in stap 5. Niet noodzakelijkerwijs de naam van de server zelf.

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database

>[!NOTE]
>
>Voor Windows moet u de Sybase IQ-client installeren op de Adobe Campaign-server en een ODBC-verbinding maken. Zorg ervoor dat u een systeemgegevensbron maakt wanneer de Adobe Campaign-server (nlserver) als service in Windows wordt uitgevoerd.

## Toegang tot metagegevens configureren {#configure-access-to-teradata}

Als u verbinding wilt maken met een externe database met Teradata in FDA, hebt u bepaalde aanvullende configuraties op de Adobe Campagneserver nodig. Raadpleeg dit [artikel](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html)voor meer informatie over het configureren van uw Teradata-database.

1. Installeer het [ODBC-stuurprogramma voor Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   Het bestaat uit drie pakketten die in de volgende volgorde op Red Hat (of CentOS)/Suse kunnen worden geïnstalleerd:

   * TeraGSS
   * tdicu1510 (installeer het met setup_wrapper.sh)
   * tdodbc1510 (installeer het met setup_wrapper.sh)

1. Configureer het ODBC-stuurprogramma. De configuratie kan in de standaarddossiers worden uitgevoerd: **/etc/odbc.ini** voor algemene parameters en /etc/odbcinst.ini voor het declareren van stuurprogramma&#39;s:

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

1. In Campaign Classic kunt u vervolgens uw externe account voor metagegevens configureren. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om de **[!UICONTROL Teradata]** externe rekening te vormen, moet u specificeren:

   * **[!UICONTROL Type]**: TeraData

   * **[!UICONTROL Server]**: URL van de Teradata-server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database

## Toegang tot SAP-HANA configureren {#configure-access-to-sap-hana}

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

   * **LD_LIBRARY_PATH**: Het zou de verbinding aan uw cliënt van SAP Hana (/usr/sap/hdbclient/libodbcHDB.so) door gebrek moeten omvatten.
   * **ODBCINI**: locatie van het bestand odbc.ini (bijvoorbeeld /etc/odbc.ini).

1. In Campaign Classic, kunt u uw externe rekening van SAP Hana dan vormen. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om de **[!UICONTROL SAP Hana]** externe rekening te vormen, moet u specificeren:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL van de SAP Hana-server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount
