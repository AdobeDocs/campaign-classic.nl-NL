---
product: campaign
title: Toegang tot Snowflake configureren
description: Leer hoe u toegang tot Snowflake kunt configureren in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 6%

---

# Toegang tot Snowflake configureren {#configure-access-to-snowflake}

![](../../assets/v7-only.svg)

Campagne gebruiken **Federale gegevenstoegang** (FDA) om informatie te verwerken die in een externe database is opgeslagen. Voer de onderstaande stappen uit om toegang te configureren voor [!DNL Snowflake].

1. Configureren [!DNL Snowflake] op [Linux](#snowflake-linux).
1. Configureer de [!DNL Snowflake] [externe rekening](#snowflake-external) in Campagne

>[!NOTE]
>
>[!DNL Snowflake] de schakelaar is beschikbaar voor ontvangen en on-premise plaatsingen. Raadpleeg [deze pagina](../../installation/using/capability-matrix.md) voor meer informatie.

![](assets/snowflake_3.png)

## Snowflake op Linux {#snowflake-linux}

Om te vormen [!DNL Snowflake] Voer in Linux de onderstaande stappen uit:

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

1. Voordat u het script uitvoert, hebt u toegang tot meer informatie via de `--help` optie:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./snowflake_odbc-setup.sh --help
   ```

1. Open de map waarin het script zich bevindt en voer het volgende script als een hoofdgebruiker uit:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./snowflake_odbc-setup.sh
   ```

1. Nadat u de ODBC-stuurprogramma&#39;s hebt geïnstalleerd, moet u Campaign Classic opnieuw starten. Voer hiertoe de volgende opdracht uit:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campagne, kunt u uw [!DNL Snowflake] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#snowflake-external).

## Snowflake externe rekening {#snowflake-external}

U moet een [!DNL Snowflake] externe account om uw Campagne-instantie aan te sluiten op uw [!DNL Snowflake] externe database.

1. Van campagne **[!UICONTROL Explorer]**, klikt u op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

1. Onder **[!UICONTROL Configuration]**, selecteert u [!DNL Snowflake] van de **[!UICONTROL Type]** vervolgkeuzelijst.

   ![](assets/snowflake_5.png)

1. Voeg uw **[!UICONTROL Server]** URL en **[!UICONTROL Database]**.

1. Configureer de **[!UICONTROL Snowflake]** externe accountverificatie:

   * Voor account-/wachtwoordverificatie moet u opgeven:

      * **[!UICONTROL Account]**: Naam van de gebruiker

      * **[!UICONTROL Password]**: Wachtwoord voor gebruikersaccount.

      ![](assets/snowflake.png)

   * Voor Keypair-verificatie klikt u op de knop **[!UICONTROL Keypair Auth]** tabblad gebruiken **[!UICONTROL Private key]** om uw gegevens te verifiëren en te kopiëren **[!UICONTROL Private key]**.

      ![](assets/snowflake_4.png)


1. Klik op de knop **[!UICONTROL Parameters]** dan de **[!UICONTROL Deploy functions]** om functies te maken.

   >[!NOTE]
   >
   >Alle functies zijn alleen beschikbaar als u de Adobe Campaign SQL-functies maakt in de externe database. Raadpleeg deze voor meer informatie [page](../../configuration/using/adding-additional-sql-functions.md).

   ![](assets/snowflake_2.png)

1. Klikken **[!UICONTROL Save]** wanneer uw configuratie wordt gebeëindigd.

De connector ondersteunt de volgende opties:

| Option | Beschrijving |
|---|---|
| werkschema | Databaseschema dat moet worden gebruikt voor werktabellen |
| entrepot | Naam van het standaardentrepot aan gebruik. De standaardinstelling van de gebruiker wordt hierdoor genegeerd. |
| TimeZoneName | Standaard leeg, wat betekent dat de systeemtijdzone van de Campaign Classic-toepassingsserver wordt gebruikt. De optie kan worden gebruikt om de TIMEZONE-sessieparameter te forceren. <br>Raadpleeg [deze pagina](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone) voor meer informatie. |
| WeekStart | WEEK_START, sessieparameter. Standaard ingesteld op 0. <br>Raadpleeg [deze pagina](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start) voor meer informatie. |
| UseCachedResult | USE_CACHED_RESULTS sessieparameter. Standaard ingesteld op TRUE. U kunt deze optie gebruiken om resultaten in de Snowflake-cache uit te schakelen. <br>Raadpleeg [deze pagina](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html) voor meer informatie. |
| bulkThreads | Het aantal threads dat moet worden gebruikt voor Snowflake bulksgewijs loader: meer threads betekenen betere prestaties voor grotere bulkladingen. Standaard ingesteld op 1. Het aantal kan, afhankelijk van het aantal van de machindraad worden aangepast. |
| chunkSize | Hiermee bepaalt u de bestandsgrootte van het segment voor bulksloader. Standaard ingesteld op 128 MB. Kan worden aangepast voor een betere prestatie, wanneer gebruikt met bulkThreads. Meer tegelijkertijd actieve threads betekenen betere prestaties. <br>Raadpleeg voor meer informatie hierover [Snowflake-documentatie](https://docs.snowflake.net/manuals/sql-reference/sql/put.html). |
| StageName | Naam van het vooraf ingestelde interne werkgebied. Het wordt gebruikt in bulk lading in plaats van het creëren van een nieuwe tijdelijke fase. |
