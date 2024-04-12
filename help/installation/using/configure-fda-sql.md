---
product: campaign
title: Toegang tot Microsoft SQL Server configureren
description: Leer hoe u toegang tot Microsoft SQL Server configureert
feature: Installation, Federated Data Access
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Toegang tot Microsoft SQL Server configureren {#configure-fda-sql}



Campagne gebruiken **Federale gegevenstoegang** (FDA) om informatie te verwerken die is opgeslagen in een externe Microsoft SQL Server-database. Voer de onderstaande stappen uit om toegang te configureren voor [!DNL Microsoft SQL Server].

1. Configureren [!DNL Microsoft SQL Server] op [CentOS](#sql-centos).
1. Configureren [!DNL Microsoft SQL Server] op [Linux](#sql-linux).
1. Configureren [!DNL Microsoft SQL Server] op [Windows](#sql-windows).
1. Vorm [!DNL Microsoft SQL Server] [externe rekening](#sql-external) in Campagne

## Microsoft SQL Server op CentOS {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] is beschikbaar op CentOS 7 en 6.

Om te vormen [!DNL Microsoft SQL Server] Voer in CentOS de onderstaande stappen uit:

1. Download en installeer SQL ODBC-stuurprogramma met de volgende opdracht:

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. In Adobe Campaign kunt u vervolgens uw [!DNL Microsoft SQL Server] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#sql-external).

## Microsoft SQL Server op Linux {#sql-linux}

>[!NOTE]
>
> Als u een oudere versie van Adobe Campaign (ouder dan 7.2.1) uitvoert, moet u `unix ODBC drivers`.

1. Download het MS ODBC-stuurprogramma van [deze pagina](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/).

1. Voer de volgende opdracht als basisgebruiker uit:

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. In Adobe Campaign kunt u vervolgens uw [!DNL Microsoft SQL Server] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#sql-external).

## Microsoft SQL Server in Windows {#sql-windows}

Om te vormen [!DNL Microsoft SQL Server] in Windows:

1. Klik in Windows op **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**.

1. Van de **[!UICONTROL ODBC Data Sources (64-bit)]** nieuw venster, klik **[!UICONTROL Add...]**.

1. Controleren of SQL Server Native Client v11 wordt vermeld in het dialoogvenster **[!UICONTROL Create New Data Source]** venster.

1. Als de SQL Inheemse Cliënt van de Server niet vermeld is, kunt u het binnen downloaden [deze pagina](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. In Adobe Campaign kunt u vervolgens uw [!DNL Microsoft SQL Server] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#sql-external).

## Externe Microsoft SQL Server-account {#sql-external}

U moet een [!DNL Microsoft SQL Server] externe account om uw Campagne-instantie aan te sluiten op uw [!DNL Microsoft SQL Server] externe database.

1. Van campagne **[!UICONTROL Explorer]**, klikt u op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

1. Onder **[!UICONTROL Configuration]**, selecteert u [!DNL Microsoft SQL Server] van de **[!UICONTROL Type]** vervolgkeuzelijst.

   ![](assets/sql.png)

1. Vorm **[!UICONTROL Microsoft SQL Server]** externe accountverificatie:

   * **[!UICONTROL Server]**: URL van de [!DNL Microsoft SQL Server] server.

   * **[!UICONTROL Account]**: Naam van de gebruiker.

   * **[!UICONTROL Password]**: Wachtwoord voor gebruikersaccount.

   * **[!UICONTROL Database]**: Naam van de database (optioneel).

   * **[!UICONTROL Timezone]**: Tijdzone ingesteld in [!DNL Microsoft SQL Server]. [Meer informatie](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. Klik op de knop **[!UICONTROL Parameters]** en vervolgens de **[!UICONTROL Deploy functions]** om functies te maken.

   >[!NOTE]
   >
   >Alle functies zijn alleen beschikbaar als u de Adobe Campaign SQL-functies maakt in de externe database. Raadpleeg deze voor meer informatie [page](../../configuration/using/adding-additional-sql-functions.md).

1. Klikken **[!UICONTROL Save]** wanneer uw configuratie wordt gebeëindigd.

De connector ondersteunt de volgende opties:

| Optie | Beschrijving |
|---|---|
| Verificatie | Type van authentificatie die door de schakelaar wordt gesteund. Huidige ondersteunde waarde: ActiveDirectoryMSI. <br> Zie voorbeeld 8 van [Microsoft-documentatie](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| Coderen | Geeft aan of verbindingen de TLS-codering via het netwerk gebruiken. Mogelijke waarden zijn **ja/verplicht (18.0 en hoger)**, **neen/optioneel (18.0 en hoger)**, en **strikt (18.0 en hoger)**. De standaardwaarde is **ja** in versie 18.0 en hoger en **nee** in eerdere versies. <br>Raadpleeg voor meer informatie hierover [Microsoft-documentatie](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | Hiermee wordt codering ingeschakeld met behulp van een zelfondertekend servercertificaat, indien gebruikt met **Coderen**. <br>Geaccepteerde waarden: **ja** of **nee** (standaardwaarde, wat betekent dat het servercertificaat wordt gevalideerd). |
