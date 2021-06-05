---
solution: Campaign Classic
product: campaign
title: Toegang tot Google BigQuery configureren
description: Leer hoe u toegang tot Google BigQuery configureert in FDA
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 911302475b5ece96d527575148ee611fdb839753
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 2%

---


# Toegang tot Google BigQuery {#configure-fda-google-big-query} configureren

Gebruik de optie Adobe Campaign Classic **Federated Data Access** (FDA) om informatie te verwerken die is opgeslagen in een externe database. Voer de onderstaande stappen uit om toegang tot [!DNL Google BigQuery] te configureren.

1. [!DNL Google BigQuery] configureren op [Windows](#google-windows) of [Linux](#google-linux)
1. [!DNL Google BigQuery] [externe account](#google-external) in Adobe Campaign Classic configureren
1. [!DNL Google BigQuery] bulkload van connector instellen op [Windows](#bulk-load-windows) of [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] -aansluiting is beschikbaar voor hybride en on-premise implementaties. Raadpleeg [deze pagina](../../installation/using/capability-matrix.md) voor meer informatie.

![](assets/snowflake_3.png)

## Google BigQuery in Windows {#google-windows}

### Stuurprogramma ingesteld op Windows {#driver-window}

1. Download het [ODBC-stuurprogramma voor Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configureer het ODBC-stuurprogramma in Windows. Raadpleeg [deze pagina](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf) voor meer informatie.

1. Voor het functioneren van de [!DNL Google BigQuery]-connector vereist Adobe Campaign Classic de volgende parameters om verbinding te maken:

   * **[!UICONTROL Project]**: een bestaand project maken of gebruiken.

      Raadpleeg deze [pagina](https://cloud.google.com/resource-manager/docs/creating-managing-projects) voor meer informatie.

   * **[!UICONTROL Service account]**: Maak een serviceaccount.

      Raadpleeg deze [pagina](https://cloud.google.com/iam/docs/creating-managing-service-accounts) voor meer informatie.

   * **[!UICONTROL Key File Path]**: de  **[!UICONTROL Service account]** vereist  **[!UICONTROL Key File]** voor een  [!DNL Google BigQuery] verbinding door ODBC.

      Raadpleeg deze [pagina](https://cloud.google.com/iam/docs/creating-managing-service-account-keys) voor meer informatie.

   * **[!UICONTROL Dataset]**:  **[!UICONTROL Dataset]** is optioneel voor een ODBC-verbinding. Aangezien elke vraag de dataset moet verstrekken waar de lijst wordt gevestigd, is het specificeren van **[!UICONTROL Dataset]** verplicht voor [!DNL Google BigQuery] de Schakelaar van FDA in Adobe Campaign Classic.

      Raadpleeg deze [pagina](https://cloud.google.com/bigquery/docs/datasets) voor meer informatie.

1. In Adobe Campaign Classic kunt u vervolgens uw [!DNL Google BigQuery] externe account configureren. Raadpleeg [deze sectie](#google-external) voor meer informatie over het configureren van uw externe account.

### Bulkbelasting ingesteld in Windows {#bulk-load-window}

>[!NOTE]
>
>Voor Google Cloud SDK moet Python zijn geïnstalleerd om te kunnen werken.
>
>We raden u aan Python3 te gebruiken. Zie deze [pagina](https://www.python.org/downloads/).

Met het hulpprogramma Bulk Load kunt u sneller overdragen, wat wordt bereikt met Google Cloud SDK.

1. Download Windows 64-bits archief (x86_64) van deze [pagina](https://cloud.google.com/sdk/docs/downloads-versioned-archives) en extraheer het archief naar de corresponderende directory.

1. Voer het script `google-cloud-sdk\install.sh` uit. U moet de instelling van een padvariabele accepteren.

1. Controleer na de installatie of de padvariabele `...\google-cloud-sdk\bin` is ingesteld. Als dat niet het geval is, voegt u het handmatig toe.

1. Voeg in het `..\google-cloud-sdk\bin\bq.cmd`-bestand de lokale variabele `CLOUDSDK_PYTHON` toe, die wordt omgeleid naar de locatie van de Python-installatie.

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

1. Download het [Magnitude Simba Linux ODBC-stuurprogramma (.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers). Breng het balbestand vervolgens over naar een tijdelijke map op uw computer of gebruik de opdracht Doel:

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. Extraheer het hoofdbalbestand als volgt, waarbij **TarballName** de naam is van het tarball-pakket dat de bestuurder bevat:

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. Open de map die u hebt uitgepakt en extraheer het binnenste tarball-bestand dat overeenkomt met de versie van het stuurprogramma. Installeer het in een andere tijdelijke map, in het volgende voorbeeld BigQueryDriver:

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. Open de tijdelijke locatie waar het hoofdbalbestand is geëxtraheerd en kopieer de bestanden `GoogleBigQueryODBC.did` en `setup/simba.googlebigqueryodbc.ini` naar de nieuwe map die in de vorige stap is gemaakt:

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

1. Vervang `<INSTALLDIR>` door `/opt/simba/googlebigqueryodbc` in `simba.googlebigqueryodbc.ini` in de installatiemap:

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. Wijzig `DriverManagerEncoding` in UTF-16 en `SwapFilePath` in `simba.googlebigqueryodbc.ini`. Indien nodig kunt u ook de loginstellingen wijzigen.

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

1. Als u een bestand met systeemstuurprogramma&#39;s of een huidig `odbcinst.ini`-bestand gebruikt, configureert u `/etc/odbcinst.ini` zodanig dat dit verwijst naar de locatie `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so` van het Google BigQuery-stuurprogramma.

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

1. Zoek de locatie van de UnixODBC-beheerbibliotheken voor stuurprogramma&#39;s en voeg de bibliotheekpaden `unixODBC` en `googlebigqueryodbc` toe aan de variabele `LD_LIBRARY_PATH environment`.

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

1. In Adobe Campaign Classic kunt u vervolgens uw [!DNL Google BigQuery] externe account configureren. Raadpleeg [deze sectie](#google-external) voor meer informatie over het configureren van uw externe account.

### Bulkbelasting ingesteld op Linux {#bulk-load-linux}

>[!NOTE]
>
>Voor Google Cloud SDK moet Python zijn geïnstalleerd om te kunnen werken.
>
>We raden u aan Python3 te gebruiken. Zie deze [pagina](https://www.python.org/downloads/).

Met het hulpprogramma Bulk Load kunt u sneller overdragen, wat wordt bereikt met Google Cloud SDK.

1. Download Linux 64-bits (x86_64)-archief in deze [pagina](https://cloud.google.com/sdk/docs/downloads-versioned-archives) en extraheer het in de corresponderende directory.

1. Voer het script `google-cloud-sdk\install.sh` uit. U moet het plaatsen van wegvariabele goedkeuren.

1. Controleer na de installatie of de padvariabele `...\google-cloud-sdk\bin` is ingesteld. Als dat niet het geval is, voegt u het handmatig toe.

1. Als u wilt vermijden gebruikend `PATH` variabele of als u `google-cloud-sdk` folder naar een andere plaats wilt verplaatsen, gebruik `bqpath` optiewaarde wanneer het vormen van **[!UICONTROL External account]** om de nauwkeurige weg aan de bakfolder op uw systeem te specificeren.

1. Start Adobe Campaign Classic opnieuw om rekening te houden met de wijzigingen.

## Externe Google BigQuery-account {#google-external}

U moet een [!DNL Google BigQuery] externe rekening tot stand brengen om uw instantie van Adobe Campaign Classic met uw [!DNL Google BigQuery] externe gegevensbestand te verbinden.

1. Klik in Adobe Campaign Classic **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteer **[!UICONTROL External database]** als **[!UICONTROL Type]** van uw externe rekening.

1. Configureer de externe account [!DNL Google BigQuery]. Geef de volgende instellingen op:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: E-mail van uw  **[!UICONTROL Service account]**. Raadpleeg [Google Cloud-documentatie](https://cloud.google.com/iam/docs/creating-managing-service-accounts) voor meer informatie hierover.

   * **[!UICONTROL Project]**: Naam van uw  **[!UICONTROL Project]**. Raadpleeg [Google Cloud-documentatie](https://cloud.google.com/resource-manager/docs/creating-managing-projects) voor meer informatie hierover.

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: Selecteer  **[!UICONTROL Click here to upload]** als u de sleutel via Adobe Campaign Classic wilt uploaden.

      * **[!UICONTROL Enter manually the key file path]**: Kopieer/plak het absolute pad in dit veld als u een bestaande sleutel wilt gebruiken.
   * **[!UICONTROL Dataset]**: Naam van uw  **[!UICONTROL Dataset]**. Raadpleeg [Google Cloud-documentatie](https://cloud.google.com/bigquery/docs/datasets-intro) voor meer informatie hierover.
   ![](assets/google-big-query.png)
