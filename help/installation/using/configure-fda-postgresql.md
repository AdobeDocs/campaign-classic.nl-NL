---
product: campaign
title: Toegang tot PostgreSQL configureren
description: Leer hoe u toegang tot PostgreSQL configureert
feature: Installation, Instance Settings
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# Toegang tot PostgreSQL configureren {#configure-fda-postgresql}



Campagne gebruiken **Federale gegevenstoegang** (FDA) om informatie te verwerken die is opgeslagen in een externe PostSQL-database.

## PostSQL-configuratie {#postgresql-configuration}

U moet eerst Libpq installeren. Met Libpq kunnen clientprogramma&#39;s query&#39;s verzenden naar de PostgreSQL-backendserver en de resultaten van deze query&#39;s ontvangen.

Voer de onderstaande stappen uit om toegang te configureren voor [!DNL PostgreSQL]:

* Voor CentOS voert u de volgende opdracht uit `sudo apt-get -y install libpq-dev`.

* Voor Linux voert u de volgende opdracht uit `yum install postgresql-devel`.

* Voor Windows wordt Libpq geïmplementeerd via `libpq.dll` die is opgenomen in de installatie van Adobe Campaign.

In Adobe Campaign kunt u vervolgens uw [!DNL PostgreSQL] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#postgresql-external).

## PostgreSQL-externe account {#postgresql-external}

>[!NOTE]
>
> PostgreSQL is beschikbaar op CentOS 7 en 6.

U moet een [!DNL PostgreSQL] externe account om uw Campagne-instantie aan te sluiten op uw [!DNL PostgreSQL] externe database.

1. Van campagne **[!UICONTROL Explorer]**, klikt u op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

1. Onder **[!UICONTROL Configuration]**, selecteert u [!DNL PostgreSQL, Greenplum] van de **[!UICONTROL Type]** vervolgkeuzelijst.

   ![](assets/postgresql_1.png)

1. Vorm **[!UICONTROL PostgreSQL]** externe accountverificatie:

   * **[!UICONTROL Server]**: URL van de [!DNL PostgreSQL] server.

   * **[!UICONTROL Account]**: Naam van de gebruiker.

   * **[!UICONTROL Password]**: Wachtwoord voor gebruikersaccount.

   * **[!UICONTROL Database]**: Naam van de database (optioneel).

   * **[!UICONTROL Working schema]**: Naam van uw werkschema. [Meer informatie](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**: Tijdzone ingesteld in [!DNL PostgreSQL]. [Meer informatie](https://www.postgresql.org/docs/7.2/timezones.html)

1. Klik op de knop **[!UICONTROL Parameters]** en vervolgens de **[!UICONTROL Deploy functions]** om functies te maken.

   >[!NOTE]
   >
   >Alle functies zijn alleen beschikbaar als u de Adobe Campaign SQL-functies maakt in de externe database. Raadpleeg deze voor meer informatie [page](../../configuration/using/adding-additional-sql-functions.md).

1. Klikken **[!UICONTROL Save]** wanneer uw configuratie wordt gebeëindigd.

De connector ondersteunt de volgende opties:

| Optie | Beschrijving |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Maximale wachttijd op verbinding, in seconden. <br>Raadpleeg voor meer informatie hierover [PostSQL-documentatie](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Aantal seconden van inactiviteit waarna TCP een keeplive bericht naar de server zou moeten verzenden. <br>Raadpleeg voor meer informatie hierover [PostSQL-documentatie](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Aantal seconden waarna TCP keeplive bericht niet erkend door de server opnieuw zou moeten worden overgebracht.  <br>Raadpleeg voor meer informatie hierover [PostSQL-documentatie](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Het aantal keepalives van TCP dat kan worden verloren alvorens de verbinding van de cliënt aan de server als dood wordt beschouwd. <br>Raadpleeg voor meer informatie hierover [PostSQL-documentatie](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
