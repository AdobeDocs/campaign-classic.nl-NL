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
source-git-commit: 4f1f1cd9c5ebb77fbb01cadad6c587ed2fe64dcc
workflow-type: tm+mt
source-wordcount: '1835'
ht-degree: 0%

---


# Specifieke configuraties per databasetype {#specific-configurations-by-database-type}

Afhankelijk van de externe databases die u vanuit Adobe Campaign wilt kunnen openen, moet u bepaalde specifieke configuraties uitvoeren. Bij deze configuraties worden vooral stuurprogramma&#39;s geïnstalleerd en worden omgevingsvariabelen opgegeven die bij elke RDBMS op de Adobe Campaign-server horen.

Raadpleeg deze [pagina](../../platform/using/legacy-connectors.md)voor meer informatie over verouderde connectors zoals Teradata, Hadoop 2.1 of Netezza.

Als algemene regel geldt dat u de corresponderende clientlaag op de externe database op de Adobe Campaign-server moet installeren.

>[!NOTE]
>
>Compatibele versies worden vermeld in de Matrix [van de Verenigbaarheid van de](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA)Campagne.

## Toegang tot Azure Synapse configureren {#configure-access-to-azure-synapse}

### Azure synapse external account {#azure-external}

Met de [!DNL Azure] externe account kunt u uw Campagne-instantie verbinden met uw externe database van Azure Synapse.
Een externe [!DNL Azure Synapse] account maken:

1. Configureer in Campaign Classic uw [!DNL Azure Synapse] externe account. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

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

1. In Campaign Classic kunt u vervolgens uw [!DNL Azure Synapse] externe account configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#azure-external)voor meer informatie over het configureren van uw externe account.

1. Aangezien Azure Synapse Analytics communiceert via de TCP 1433-poort, moet u deze poort openen op uw firewall. Gebruik de volgende opdracht:

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Om communicatie van de zijde van Analytics van de Stedelijke Synapse toe te staan zou u uw openbare IP aan de lijst van gewenste personen kunnen moeten toevoegen. Raadpleeg de [Azure-documentatie](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)om dit te doen.

1. Voer in het geval van iptables de volgende opdracht uit:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

### Azure Synapse in Windows {#azure-windows}

>[!NOTE]
>
>Dit is exclusief aan versie 13 van de Bestuurder ODBC maar Adobe Campaign Classic kan SQL de Inheemse bestuurders van de Cliënt van de Server 11.0 en 10.0 ook gebruiken.

Om Azure Synapse op Vensters te vormen:

1. Installeer eerst het Microsoft ODBC-stuurprogramma. U vindt deze op deze [pagina](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Kies de volgende bestanden om te installeren:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. Nadat het ODBC-stuurprogramma is geïnstalleerd, kunt u het indien nodig testen. Raadpleeg deze [pagina](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server)voor meer informatie.

1. In Campaign Classic kunt u vervolgens uw [!DNL Azure Synapse] externe account configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#azure-external)voor meer informatie over het configureren van uw externe account.

1. Aangezien Azure Synapse Analytics communiceert via de TCP 1433-poort, moet u deze poort openen op de Windows Defender Firewall. Raadpleeg de documentatie [bij](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule)Windows voor meer informatie.

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

1. Om iptables op Debian te vormen om de verbinding met Azure Synapse Analytics te verzekeren, laat de uitgaande haven van TCP 1433 voor uw hostname met het volgende bevel toe:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Om communicatie van de zijde van Analytics van de Stedelijke Synapse toe te staan zou u uw openbare IP aan de lijst van gewenste personen kunnen moeten toevoegen. Raadpleeg de [Azure-documentatie](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)om dit te doen.

## Toegang tot Snowflake configureren {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake] de schakelaar is beschikbaar voor ontvangen en on-premise plaatsingen. For more on this, refer to [this article](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Sneeuwvlokken externe account {#snowflake-external}

Met de [!DNL Snowflake] externe account kunt u uw Campagne-instantie verbinden met uw Snowflake externe database.

1. Configureer in Campaign Classic uw [!DNL Snowflake] externe account. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

1. Configureer de **[!UICONTROL Snowflake]** externe account. Geef de volgende instellingen op:

   * **[!UICONTROL Type]**: [!DNL Snowflake]

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
| TimeZoneName | Standaard leeg, wat betekent dat de systeemtijdzone van de Campaign Classic-toepassingsserver wordt gebruikt. De optie kan worden gebruikt om de TIMEZONE-sessieparameter te forceren. <br>Raadpleeg [deze pagina](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)voor meer informatie. |
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

1. In Campaign Classic kunt u vervolgens uw [!DNL Snowflake] externe account configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#snowflake-external)voor meer informatie over het configureren van uw externe account.

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

1. In Campaign Classic kunt u vervolgens uw [!DNL Snowflake] externe account configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#snowflake-external)voor meer informatie over het configureren van uw externe account.

### Sneeuwvlok in Windows {#snowflake-windows}

1. Download het [ODBC-stuurprogramma voor Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). U hebt beheerdersrechten nodig om het stuurprogramma te installeren. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configureer het ODBC-stuurprogramma. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. In Campaign Classic kunt u vervolgens uw [!DNL Snowflake] externe account configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#snowflake-external)voor meer informatie over het configureren van uw externe account.

## Toegang tot Hadoop 3.0 configureren {#configure-access-to-hadoop-3}

### Externe rekening {#hadoop-external}

Met de [!DNL Hadoop] externe account kunt u uw Campagne-instantie verbinden met uw externe database van Hadoop.

1. Configureer in Campaign Classic uw [!DNL Hadoop] externe account. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

1. Configureer de **[!UICONTROL Hadoop]** externe account. Geef de volgende instellingen op:

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

### Hadoop 3.0 configureren {#configuring-hadoop}

Als u verbinding wilt maken met een externe Hadoop-database in FDA, hebt u de volgende configuraties op de Adobe Campaign-server nodig. Deze configuratie is zowel voor Windows als voor Linux beschikbaar.

1. Download de ODBC-stuurprogramma&#39;s voor Hadoop, afhankelijk van uw OS-versie. Drivers vindt u op [deze pagina](https://www.cloudera.com/downloads.html).

1. Vervolgens moet u de ODBC-stuurprogramma&#39;s installeren en een DSN maken voor uw Hive-verbinding. Instructies vindt u op [deze pagina](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Nadat u de ODBC-stuurprogramma&#39;s hebt gedownload en geïnstalleerd, moet u Campaign Classic opnieuw starten. Voer hiertoe de volgende opdracht uit:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic kunt u vervolgens uw [!DNL Hadoop] externe account configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#hadoop-external)voor meer informatie over het configureren van uw externe account.

## Toegang tot Oracle configureren {#configure-access-to-oracle}

### Externe Oracle-account {#oracle-external}

Met de [!DNL Oracle] externe account kunt u uw Campagne-instantie verbinden met uw externe database van Hadoop.

1. Configureer in Campaign Classic uw [!DNL oracle] externe account. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

1. Configureer de **[!UICONTROL Oracle]** externe account. Geef de volgende instellingen op:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: Naam van de DNS

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Time zone]**: Tijdzone van server
   ![](assets/oracle_config.png)

### Oracle op Linux {#for-linux-1}

Voor verbinding met een externe Oracle-database in FDA zijn hieronder aanvullende configuraties op de Adobe Campaign-server vereist.

1. Installeer de volledige Oracle-client die overeenkomt met uw versie van Oracle.
1. Voeg uw definities TNS aan uw installatie toe. Om dit te doen, specificeer hen in een **tnsnames.ora** - dossier in de /etc/oracle bewaarplaats. Als deze gegevensopslagruimte niet bestaat, maakt u deze.

   Maak vervolgens een nieuwe omgevingsvariabele TNS_ADMIN: Exporteer TNS_ADMIN=/etc/oracle en start de computer opnieuw op.

1. Integreer Oracle in uw Adobe Campaign-server (nlserver). Hiervoor controleert u of het bestand **customer.sh** aanwezig is in de map &quot;nl6&quot; van de structuur van de Adobe Campaign-serverstructuur en of het bestand de koppelingen naar de Oracle-bibliotheken bevat.

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

1. In Campaign Classic kunt u vervolgens uw [!DNL Oracle] externe account configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#oracle-external)voor meer informatie over het configureren van uw externe account.

### Oracle in Windows {#for-windows-1}

Voor verbinding met een externe Oracle-database in FDA zijn hieronder aanvullende configuraties op de Adobe Campaign-server vereist.

1. Installeer de Oracle-client.

1. Maak in de map C:Oracle een bestand **tnsnames.ora** met uw TNS-definitie.

1. Voeg een omgevingsvariabele TNS_ADMIN toe met C:Oracle als waarde en start de computer opnieuw op.

1. In Campaign Classic kunt u vervolgens uw [!DNL Oracle] externe account configureren. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#oracle-external)voor meer informatie over het configureren van uw externe account.