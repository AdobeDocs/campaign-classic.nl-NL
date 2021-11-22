---
product: campaign
title: Toegang tot Google BigQuery configureren
description: Leer hoe u toegang tot Google BigQuery configureert in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 6d53ba957fb567a9a921544418a73a9bde37c97b
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 2%

---

# Toegang tot Google BigQuery configureren {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Adobe Campaign Classic gebruiken **Federale gegevenstoegang** (FDA) om informatie te verwerken die in een externe database is opgeslagen. Voer de onderstaande stappen uit om toegang te configureren voor [!DNL Google BigQuery].

1. Configureren [!DNL Google BigQuery] op [Windows](#google-windows) of [Linux](#google-linux)
1. Configureer de [!DNL Google BigQuery] [externe rekening](#google-external) in Adobe Campaign Classic
1. Instellen [!DNL Google BigQuery] bulkbelasting van connector aan [Windows](#bulk-load-windows) of [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] -aansluiting is beschikbaar voor hybride en on-premise implementaties. Raadpleeg [deze pagina](../../installation/using/capability-matrix.md) voor meer informatie.

![](assets/snowflake_3.png)

## Google BigQuery in Windows {#google-windows}

### Stuurprogramma ingesteld op Windows {#driver-window}

1. Download de [ODBC-stuurprogramma voor Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configureer het ODBC-stuurprogramma in Windows. Raadpleeg [deze pagina](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf) voor meer informatie.

1. Voor de [!DNL Google BigQuery] -connector werkt, vereist Adobe Campaign Classic de volgende parameters om verbinding te maken:

   * **[!UICONTROL Project]**: een bestaand project maken of gebruiken.

      Raadpleeg deze voor meer informatie [page](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: Maak een serviceaccount.

      Raadpleeg deze voor meer informatie [page](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: de **[!UICONTROL Service account]** vereist een **[!UICONTROL Key File]** voor een [!DNL Google BigQuery] verbinding via ODBC.

      Raadpleeg deze voor meer informatie [page](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** is optioneel voor een ODBC-verbinding. Aangezien elke vraag de dataset moet verstrekken waar de lijst wordt gevestigd, die a specificeren **[!UICONTROL Dataset]** is verplicht voor [!DNL Google BigQuery] FDA Connector in Adobe Campaign Classic.

      Raadpleeg deze voor meer informatie [page](https://cloud.google.com/bigquery/docs/datasets).

1. In Adobe Campaign Classic kunt u vervolgens uw [!DNL Google BigQuery] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#google-external).

### Bulkbelasting ingesteld in Windows {#bulk-load-window}

>[!NOTE]
>
>Voor Google Cloud SDK moet Python zijn geïnstalleerd om te kunnen werken.
>
>We raden u aan Python3 te gebruiken. Zie dit [page](https://www.python.org/downloads/).

Met het hulpprogramma Bulk Load kunt u sneller overdragen, wat wordt bereikt via de Google Cloud SDK.

1. Windows 64-bits archief (x86_64) downloaden uit dit [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) en extraheer het in de corresponderende directory.

1. Voer de `google-cloud-sdk\install.sh` script. U moet het plaatsen van wegvariabele goedkeuren.

1. Controleer na de installatie of de padvariabele `...\google-cloud-sdk\bin` is ingesteld. Als dat niet het geval is, voegt u het handmatig toe.

1. In de  `..\google-cloud-sdk\bin\bq.cmd` bestand toevoegen `CLOUDSDK_PYTHON` lokale variabele, die wordt omgeleid naar de locatie van de Python-installatie.

   Bijvoorbeeld:

   ![](assets/google-big-query_1.png)

1. Start Adobe Campaign Classic opnieuw om rekening te houden met de wijzigingen.

## Google BigQuery op Linux {#google-linux}

### Stuurprogramma ingesteld op Linux {#driver-linux}

1. Voordat u het ODBC-stuurprogramma installeert, moet u uw systeem bijwerken. Voer in Linux of CentOS de volgende opdracht uit:

   ```
   yum update
   # install unixODBC driver manager
   yum install unixODBC
   ```

1. Vervolgens moet u het stuurprogramma unixODBC installeren met de volgende opdracht:

   ```
   # switch to root user
   sudo su
   ```

   In Debian:

   ```
   apt-get update
   apt-get upgrade
   # install unixODBC driver manager
   apt-get install unixODBC
   ```

1. Download de [Magnitude Simba Linux ODBC-stuurprogramma (.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers). Breng het balbestand vervolgens over naar een tijdelijke map op uw computer of gebruik de opdracht Doel:

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. Extraheer het hoofdbalbestand als volgt: **TarballName** de naam is van het tarball-pakket dat de bestuurder bevat:

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. Open de map die u hebt uitgepakt en extraheer het binnenste tarball-bestand dat overeenkomt met de versie van het stuurprogramma. Installeer het in een andere tijdelijke map, in het volgende voorbeeld BigQueryDriver:

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. Open de tijdelijke locatie waar het hoofdbalbestand is geëxtraheerd en kopieer de `GoogleBigQueryODBC.did` en `setup/simba.googlebigqueryodbc.ini` bestanden naar de nieuwe map die in de vorige stap is gemaakt:

   ```
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   cp GoogleBigQueryODBC.did /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   cp setup/simba.googlebigqueryodbc.ini /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   ```

1. Maak als volgt de installatiemap:

   ```
   mkdir -p /opt/simba/googlebigqueryodbc/
   ```

1. Kopieer de inhoud van de map naar de nieuwe installatiemap:

   ```
   cp -r /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/* /opt/simba/googlebigqueryodbc/
   ```

1. Vervangen `<INSTALLDIR>` with `/opt/simba/googlebigqueryodbc` in `simba.googlebigqueryodbc.ini` in de installatiemap:

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. Wijzig de `DriverManagerEncoding` naar UTF-16 en `SwapFilePath` in `simba.googlebigqueryodbc.ini`. Indien nodig kunt u ook de loginstellingen wijzigen.

   Hieronder ziet u een voorbeeld van een bijgewerkt configuratiebestand voor het hele stuurprogramma:

   ```
   # /opt/simba/googlebigqueryodbc/lib/simba.googlebigqueryodbc.ini
   [Driver]
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=opt/simba/googlebigqueryodbc/ErrorMessages
   LogLevel=6
   LogPath=/tmp
   SwapFilePath=/tmp
   ```

1. Als u een systeemstuurprogramma of een ander huidig bestand gebruikt `odbcinst.ini` bestand, configureren `/etc/odbcinst.ini` naar de locatie van het Google BigQuery-stuurprogramma `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`.

   Bijvoorbeeld:

   ```
   # /etc/odbcinst.ini
   # Make sure to use Simba ODBC Driver for Google BigQuery as a driver name.
   
   [ODBC Drivers]
   Simba ODBC Driver for Google BigQuery=Installed
   
   [Simba ODBC Driver for Google BigQuery]
   Description=Simba ODBC Driver for Google BigQuery(64-bit)
   Driver=/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   ```

1. Zoek de locatie van de UnixODBC-beheerbibliotheken voor stuurprogramma&#39;s en voeg de `unixODBC` en `googlebigqueryodbc` bibliotheekpaden naar de `LD_LIBRARY_PATH environment` variabele.

   ```
   find / -name 'lib*odbc*.so*' -print
   #output:
   /usr/lib/x86_64-linux-gnu/libodbccr.so.2
   /usr/lib/x86_64-linux-gnu/libodbcinst.so.2.0.0
   /usr/lib/x86_64-linux-gnu/libodbccr.so.1
   .
   .
   /opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   
   #the command would look like this
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/simba/googlebigqueryodbc:/usr/lib
   ```

1. In Adobe Campaign Classic kunt u vervolgens uw [!DNL Google BigQuery] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#google-external).

### Bulkbelasting ingesteld op Linux {#bulk-load-linux}

>[!NOTE]
>
>Voor Google Cloud SDK moet Python zijn geïnstalleerd om te kunnen werken.
>
>We raden u aan Python3 te gebruiken. Zie dit [page](https://www.python.org/downloads/).

Met het hulpprogramma Bulk Load kunt u sneller overdragen, wat wordt bereikt via de Google Cloud SDK.

1. Download Linux 64-bits (x86_64) archief in deze [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) en extraheren in de corresponderende directory.

1. Voer de `google-cloud-sdk\install.sh` script. U moet het plaatsen van wegvariabele goedkeuren.

1. Controleer na de installatie of de padvariabele `...\google-cloud-sdk\bin` is ingesteld. Als dat niet het geval is, voegt u het handmatig toe.

1. Als u het gebruik van de `PATH` of als u de `google-cloud-sdk` naar een andere locatie, gebruik de `bqpath` optiewaarde bij het configureren van de **[!UICONTROL External account]** om het exacte pad naar de map bin op uw systeem op te geven.

1. Start Adobe Campaign Classic opnieuw om rekening te houden met de wijzigingen.

## Google BigQuery, externe account {#google-external}

U moet een [!DNL Google BigQuery] externe account om uw Adobe Campaign Classic-exemplaar aan te sluiten op uw [!DNL Google BigQuery] externe database.

1. Van Adobe Campaign Classic **[!UICONTROL Explorer]**, klikt u op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

1. Configureer de [!DNL Google BigQuery] externe account, moet u opgeven:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: E-mail van uw **[!UICONTROL Service account]**. Raadpleeg voor meer informatie hierover [Google Cloud-documentatie](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: Naam van uw **[!UICONTROL Project]**. Raadpleeg voor meer informatie hierover [Google Cloud-documentatie](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: selecteren **[!UICONTROL Click here to upload]** als u ervoor kiest de toets te uploaden via Adobe Campaign Classic.

      * **[!UICONTROL Enter manually the key file path]**: Kopieer/plak het absolute pad in dit veld als u een bestaande sleutel wilt gebruiken.
   * **[!UICONTROL Dataset]**: Naam van uw **[!UICONTROL Dataset]**. Raadpleeg voor meer informatie hierover [Google Cloud-documentatie](https://cloud.google.com/bigquery/docs/datasets-intro).
   ![](assets/google-big-query.png)
