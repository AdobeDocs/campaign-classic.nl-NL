---
product: campaign
title: Toegang tot Google BigQuery configureren
description: Leer hoe u toegang tot Google BigQuery configureert in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 2%

---

# Toegang tot Google BigQuery configureren {#configure-fda-google-big-query}



Adobe Campaign Classic gebruiken **Federale gegevenstoegang** (FDA) om informatie te verwerken die in een externe database is opgeslagen. Voer de onderstaande stappen uit om toegang te configureren voor [!DNL Google BigQuery].

1. Configureren [!DNL Google BigQuery] op [Windows](#google-windows) of [Linux](#google-linux)
1. Vorm [!DNL Google BigQuery] [externe rekening](#google-external) in Adobe Campaign Classic
1. Instellen [!DNL Google BigQuery] bulkbelasting van connector aan [Windows](#bulk-load-windows) of [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] -aansluiting is beschikbaar voor gehoste, hybride en on-premise implementaties. Raadpleeg [deze pagina](../../installation/using/capability-matrix.md) voor meer informatie.

![](assets/snowflake_3.png)

## Google BigQuery in Windows {#google-windows}

### Stuurprogramma ingesteld op Windows {#driver-window}

1. Download de [ODBC-stuurprogramma voor Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configureer het ODBC-stuurprogramma in Windows. Raadpleeg [deze pagina](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf) voor meer informatie.

1. Voor de [!DNL Google BigQuery] -connector werkt, vereist Adobe Campaign Classic de volgende parameters om verbinding te maken:

   * **[!UICONTROL Project]**: maak of gebruik een bestaand project.

     Raadpleeg deze voor meer informatie [page](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: maak een serviceaccount.

     Raadpleeg deze voor meer informatie [page](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: de **[!UICONTROL Service account]** vereist een **[!UICONTROL Key File]** voor een [!DNL Google BigQuery] verbinding via ODBC.

     Raadpleeg deze voor meer informatie [page](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** is optioneel voor een ODBC-verbinding. Aangezien elke vraag de dataset moet verstrekken waar de lijst wordt gevestigd, die a specificeren **[!UICONTROL Dataset]** is verplicht voor [!DNL Google BigQuery] FDA Connector in Adobe Campaign Classic.

     Raadpleeg deze voor meer informatie [page](https://cloud.google.com/bigquery/docs/datasets).

1. In Adobe Campaign Classic kunt u vervolgens uw [!DNL Google BigQuery] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#google-external).

### Bulkbelasting ingesteld in Windows {#bulk-load-window}

>[!NOTE]
>
>Voor Google Cloud SDK moet Python zijn geïnstalleerd om te werken.
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

Voordat u het stuurprogramma instelt, moet u het script en de opdrachten uitvoeren op de hoofdgebruiker. Het wordt ook aanbevolen om Google DNS 8.8.8.8 te gebruiken terwijl het script wordt uitgevoerd.

Om te vormen [!DNL Google BigQuery] Voer in Linux de onderstaande stappen uit:

1. Controleer vóór de ODBC-installatie of de volgende pakketten op uw Linux-distributie zijn geïnstalleerd:

   * Voor Red Hat/CentOS:

     ```
     yum update
     yum upgrade
     yum install -y grep sed tar wget perl curl
     ```

   * Voor Debian:

     ```
     apt-get update
     apt-get upgrade
     apt-get install -y grep sed tar wget perl curl
     ```

1. Systeem bijwerken vóór installatie:

   * Voor Red Hat/CentOS:

     ```
     # install unixODBC driver manager
     yum install -y unixODBC
     ```

   * Voor Debian:

     ```
     # install unixODBC driver manager
     apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
     ```

1. Voordat u het script uitvoert, kunt u meer informatie opvragen door het —help-argument op te geven:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh --help
   ```

1. Open de map waarin het script zich bevindt en voer het volgende script als hoofdgebruiker uit:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### Bulkbelasting ingesteld op Linux {#bulk-load-linux}

>[!NOTE]
>
>Voor Google Cloud SDK moet Python zijn geïnstalleerd om te werken.
>
>We raden u aan Python3 te gebruiken. Zie dit [page](https://www.python.org/downloads/).

Met het hulpprogramma Bulk Load kunt u sneller overdragen, wat wordt bereikt via de Google Cloud SDK.

1. Controleer vóór de ODBC-installatie of de volgende pakketten op uw Linux-distributie zijn geïnstalleerd:

   * Voor Red Hat/CentOS:

     ```
     yum update
     yum upgrade
     yum install -y python3
     ```

   * Voor Debian:

     ```
     apt-get update
     apt-get upgrade
     apt-get install -y python3
     ```

1. Open de map waarin het script zich bevindt en voer het volgende script uit:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

## Google BigQuery, externe account {#google-external}

U moet een [!DNL Google BigQuery] externe account om uw Adobe Campaign Classic-exemplaar aan te sluiten op uw [!DNL Google BigQuery] externe database.

1. Van Adobe Campaign Classic **[!UICONTROL Explorer]**, klikt u op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

1. Vorm [!DNL Google BigQuery] externe account, moet u opgeven:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: E-mail met uw **[!UICONTROL Service account]**. Raadpleeg voor meer informatie hierover [Google Cloud-documentatie](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: Naam van uw **[!UICONTROL Project]**. Raadpleeg voor meer informatie hierover [Google Cloud-documentatie](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: select **[!UICONTROL Click here to upload]** als u ervoor kiest de toets te uploaden via Adobe Campaign Classic.

      * **[!UICONTROL Enter manually the key file path]**: kopieer/plak het absolute pad in dit veld als u een bestaande sleutel wilt gebruiken.

   * **[!UICONTROL Dataset]**: Naam van uw **[!UICONTROL Dataset]**. Raadpleeg voor meer informatie hierover [Google Cloud-documentatie](https://cloud.google.com/bigquery/docs/datasets-intro).

   ![](assets/google-big-query.png)

De connector ondersteunt de volgende opties:

| Optie | Beschrijving |
|:-:|:-:|
| ProxyType | Het type proxy dat wordt gebruikt om verbinding te maken met BigQuery via ODBC- en SDK-connectors. </br>HTTP (standaard), http_no_tunnel, socks4 en socks5 worden momenteel ondersteund. |
| ProxyHost | Hostnaam of IP-adres waar de proxy kan worden bereikt. |
| ProxyPort | Poortnummer waarop de proxy wordt uitgevoerd, bijvoorbeeld 8080 |
| ProxyUid | Gebruikersnaam voor de geverifieerde proxy |
| ProxyPwd | Wachtwoord ProxyUid |
| bqpath | Dit is alleen van toepassing voor bulkload (Cloud SDK). </br> Als u wilt voorkomen dat de PATH-variabele wordt gebruikt of als de google-cloud-sdk-map naar een andere locatie moet worden verplaatst, kunt u met deze optie het exacte pad naar de SDK-binmap van de cloud op de server opgeven. |
| GCloudConfigName | Dit is alleen van toepassing vanaf versie 7.3.4 en voor bulkload (Cloud SDK).</br> De Google Cloud SDK gebruikt configuraties om gegevens in BigQuery-tabellen te laden. Benoemde configuratie `accfda` slaat de parameters voor het laden van de gegevens op. Met deze optie kunnen gebruikers echter een andere naam voor de configuratie opgeven. |
| GCloudDefaultConfigName | Dit is alleen van toepassing vanaf versie 7.3.4 en voor bulkload (Cloud SDK).</br> De actieve Google Cloud SDK-configuratie kan niet worden verwijderd zonder de actieve tag eerst over te brengen naar een nieuwe configuratie. Deze tijdelijke configuratie is nodig om de hoofdconfiguratie voor het laden van gegevens opnieuw te maken. De standaardnaam voor de tijdelijke configuratie is `default`, kan dit indien nodig worden gewijzigd. |
| GCloudRecreateConfig | Dit is alleen van toepassing vanaf versie 7.3.4 en voor bulkload (Cloud SDK).</br> Wanneer ingesteld op `false`Het mechanisme voor het laden van grote hoeveelheden voorkomt dat wordt geprobeerd de Google Cloud SDK-configuraties opnieuw te maken, te verwijderen of te wijzigen. In plaats daarvan worden gegevens geladen met behulp van de bestaande configuratie op de computer. Deze functie is nuttig wanneer andere bewerkingen afhankelijk zijn van Google Cloud SDK-configuraties. </br> Als de gebruiker deze motoroptie inschakelt zonder de juiste configuratie, geeft het mechanisme voor het laden van grote hoeveelheden een waarschuwingsbericht weer: `No active configuration found. Please either create it manually or remove the GCloudRecreateConfig option`. Om verdere fouten te voorkomen, zal het dan aan het gebruiken van het standaard ODBC de bulkladingsmechanisme van het Tussenvoegsel van de Serie terugkeren. |

