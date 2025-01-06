---
product: campaign
title: Toegang tot Hadoop configureren
description: Leer hoe te om toegang tot Hadoop in FDA te vormen
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: e3a97e55-dd8b-41e1-b48c-816d973f62a8
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Toegang tot Hadoop configureren {#configure-access-to-hadoop}



De optie van de Toegang van Gegevens van de Campagne van het gebruik **Federated** (FDA) om informatie te verwerken die in externe gegevensbestanden wordt opgeslagen. Voer de onderstaande stappen uit om toegang tot Hadoop te configureren.

1. Vorm [ gegevensbestand van de Hadoop ](#configuring-hadoop)
1. Vorm de Hadoop [ externe rekening ](#hadoop-external) in Campagne

## Hadoop 3.0 configureren {#configuring-hadoop}

Voor het verbinden met een externe database van een Hadoop in FDA zijn de volgende configuraties op de Adobe Campaign-server vereist. Deze configuratie is zowel voor Windows als voor Linux beschikbaar.

1. Download de ODBC-stuurprogramma&#39;s voor Hadoop, afhankelijk van uw OS-versie. De bestuurders kunnen op [ worden gevonden deze pagina ](https://www.cloudera.com/downloads.html).

1. Vervolgens moet u de ODBC-stuurprogramma&#39;s installeren en een DSN maken voor uw Hive-verbinding. De instructies kunnen in [ worden gevonden deze pagina ](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Nadat u de ODBC-stuurprogramma&#39;s hebt gedownload en geïnstalleerd, moet u het Campaign Classic opnieuw starten. Voer hiertoe de volgende opdracht uit:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic kunt u vervolgens uw [!DNL Hadoop] externe account configureren. Voor meer op hoe te om uw externe rekening te vormen, verwijs naar [ deze sectie ](#hadoop-external).

## Externe rekening van hadoop {#hadoop-external}

Met de externe account van [!DNL Hadoop] kunt u uw Campagne-instantie verbinden met de externe database van uw Hadoop.

1. Configureer in Campaign Classic uw [!DNL Hadoop] externe account. Klik in het **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]** .

1. Klik op **[!UICONTROL New]**.

1. Selecteer **[!UICONTROL External database]** als de externe account van uw account **[!UICONTROL Type]** .

1. Configureer de externe account van **[!UICONTROL Hadoop]** , u moet het volgende opgeven:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: naam van de DNS

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: naam van de database indien niet opgegeven in DSN. Deze kan leeg worden gelaten, indien opgegeven in de DSN

   * **[!UICONTROL Time zone]**: Tijdzone server

   ![](assets/hadoop3.png)

De schakelaar steunt de volgende opties ODBC:

| Naam | Waarde |
|---|---|
| ODBCMgr | iODBC |
| entrepot | 02-01-4 |

De aansluiting ondersteunt ook de volgende opties voor Hive:

| Naam | Waarde | Beschrijving |
|---|---|---|
| bulkKey | Azure-blob of DataLake-toegangssleutel | Voor wasb:// of wasbs:// (als het gereedschap voor bulkladen begint met wasb:// of wasbs://). <br> het is de toegangssleutel voor blob of Emmer DataLake voor bulklading. |
| hdfsPort | havenaantal <br> dat door gebrek aan 8020 wordt geplaatst | Voor HDFS bulkload (d.w.z. als het gereedschap voor bulkladen begint met webhdfs:// of webhdfss://). |
| bucketsNumber | 20 | Aantal emmers wanneer het creëren van een gegroepeerde lijst. |
| fileFormat | PARQUET | Standaardbestandsindeling voor werktabellen. |


## Hadoop 2.1 configureren {#configure-access-hadoop-2}

Als u met Hadoop 2.1 moet verbinden, volg de hieronder beschreven stappen voor [ Vensters ](#for-windows) of [ Linux ](#for-linux).

### Hadoop 2.1 voor Windows {#for-windows}

1. Installeer ODBC en [ Azure HD Insight ](https://www.microsoft.com/en-us/download/details.aspx?id=40886) bestuurders voor Vensters.
1. Maak de DSN (Data Source Name) door het hulpprogramma ODBC DataSource Administrator uit te voeren. Een steekproef van DSN van het Systeem voor Hive wordt verstrekt voor u om te wijzigen.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Creeer de externe rekening van de Hadoop, zoals die in [ wordt gedetailleerd deze sectie ](#hadoop-external).

### Hadoop 2.1 voor Linux {#for-linux}

1. Installeer unixodbc voor Linux.

   ```
   apt-get install unixodbc
   ```

1. Download en installeer ODBC bestuurders voor Apache Hive van HortonWorks: [ https://www.cloudera.com/downloads.html ](https://www.cloudera.com/downloads.html).

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

1. Maak de DSN (Data Source Name) en bewerk het bestand odbc.ini. Maak vervolgens een DSN voor uw Hive-verbinding.

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
   >De **parameter UseNativeQuery** is hier zeer belangrijk. De campagne is Hive-bewust en zal niet correct werken tenzij UseNativeQuery wordt geplaatst. Doorgaans herschrijft het stuurprogramma of de SQL-connector van Hive query&#39;s en wordt de kolomvolgorde gewijzigd.

   De authentificatieopstelling hangt van de configuratie van de Bieg/Hadoop af. Bijvoorbeeld, voor HD Inzicht, gebruik AuthMech=6 voor gebruiker/wachtwoordauthentificatie, zoals [ hier ](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm) wordt beschreven.

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

1. Creeer de externe rekening van de Hadoop, zoals die in [ wordt gedetailleerd deze sectie ](#hadoop-external).
