---
title: Toegang tot Hadoop configureren
description: Leer hoe u toegang tot Hadoop kunt configureren in FDA
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: acb505fac39222e53a3acab6b5c93d10c9d11ba8
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---


# Toegang tot Hadoop configureren {#configure-access-to-hadoop}

Gebruik de optie Campagne **Federated Data Access** (FDA) om informatie te verwerken die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Hadoop te configureren.

1. Hadoop- [database configureren](#configuring-hadoop)
1. De [externe Hadoop-account](#hadoop-external) configureren in Campagne

## Hadoop 3.0 configureren {#configuring-hadoop}

Als u verbinding wilt maken met een externe Hadoop-database in FDA, hebt u de volgende configuraties op de Adobe Campaign-server nodig. Deze configuratie is zowel voor Windows als voor Linux beschikbaar.

1. Download de ODBC-stuurprogramma&#39;s voor Hadoop, afhankelijk van uw OS-versie. Drivers vindt u op [deze pagina](https://www.cloudera.com/downloads.html).

1. Vervolgens moet u de ODBC-stuurprogramma&#39;s installeren en een DSN maken voor uw Hive-verbinding. Instructies vindt u op [deze pagina](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Nadat u de ODBC-stuurprogramma&#39;s hebt gedownload en geïnstalleerd, moet u Campaign Classic opnieuw starten. Voer hiertoe de volgende opdracht uit:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic kunt u vervolgens uw [!DNL Hadoop] externe account configureren. Raadpleeg [deze sectie](#hadoop-external)voor meer informatie over het configureren van uw externe account.

## Externe hadoop-account {#hadoop-external}

Met de [!DNL Hadoop] externe account kunt u uw Campagne-instantie verbinden met uw externe Hadoop-database.

1. In Campaign Classic, vorm uw [!DNL Hadoop] externe rekening. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

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


## Hadoop 2.1 configureren {#configure-access-hadoop-2}

Als u verbinding wilt maken met Hadoop 2.1, voert u de onderstaande stappen voor [Windows](#for-windows) of [Linux](#for-linux)uit.

### Hadoop 2.1 voor Windows {#for-windows}

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

1. Maak de externe Hadoop-account, zoals beschreven in [deze sectie](#hadoop-external).

### Hadoop 2.1 voor Linux {#for-linux}

1. Installeer unixodbc voor Linux.

   ```
   apt-get install unixodbc
   ```

1. Download en installeer ODBC-stuurprogramma&#39;s voor Apache Hive van HortonWorks: [https://www.cloudera.com/downloads.html](https://www.cloudera.com/downloads.html).

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

   De verificatie-instelling is afhankelijk van de configuratie Hive/Hadoop. Bijvoorbeeld, voor HD Insight, gebruik AuthMech=6 voor gebruiker/wachtwoordauthentificatie, zoals [hier](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)beschreven.

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

1. Maak de externe Hadoop-account, zoals beschreven in [deze sectie](#hadoop-external).

