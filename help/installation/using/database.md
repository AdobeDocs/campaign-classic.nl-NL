---
title: Aanbevelingen voor Campaign Classic-database
description: Aanbevelingen voor databases
page-status-flag: never-activated
uuid: b318365c-8846-4c1d-b5f7-ece55fb8c4af
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1dcf01af-c2f3-4975-ba05-628d52952064
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 1%

---


# Database{#database}

De databaseserver kan op elk besturingssysteem worden uitgevoerd, ongeacht het besturingssysteem dat door de toepassingsserver of -servers wordt gebruikt, zolang er tussen de servers netwerkconnectiviteit is.

Het besturingssysteem van de databaseserver is niet belangrijk zolang er verbinding met de verschillende componenten van Adobe Campaign beschikbaar is.

Controleer ook de sectie van de de toegangslagen [van het](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) Gegevensbestand.

## Microsoft SQL Server {#microsoft-sql-server}

De native client moet op de Adobe Campaign-toepassingsservers zijn geïnstalleerd.

U kunt controleren op de inheemse cliënt op de server via het ODBC bestuurdersconfiguratievenster, onder **SQL de Inheemse Cliënt 11.0** van de Server.

De volgende toegang DLL moet aanwezig zijn: **sqlncli11.dll**.

Toegang-DLL&#39;s vindt u op de Microsoft-website.

>[!NOTE]
>
>Toegang tot Microsoft SQL Server vanaf een toepassingsserver die in Linux wordt uitgevoerd, wordt niet ondersteund.

## Oracle {#oracle}

>[!NOTE]
>
>Kolomnamen met multi-bytetekens worden niet ondersteund.

De parameters **NLS_NCHAR_CHARACTERSET** en **NLS_CHARACTERSET** moeten correct worden gevormd opdat het gegevensbestand in Unicode of ANSI werkt.

Adobe Campaign gebruikt standaard Oracle-codering. Het gebruik van andere codering kan compatibiliteitsproblemen veroorzaken: in dit geval kunt u contact opnemen met de technische ondersteuning .

Gebruik de volgende opdracht **sqlplus** om meer te weten te komen over uw codering:

```
SELECT * FROM nls_database_parameters ;
```

* Voor een Unicode-installatie worden de volgende coderingen ondersteund:

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* Voor een ANSI installatie (niet-unicode), slechts wordt de volgende het coderen gesteund:

```
  NLS_CHARACTERSET WE8MSWIN1252
```

Als u zich wilt aanmelden bij **sqlplus**, gebruikt u het Oracle-gebruikersprofiel:

```
su - oracle 
sqlplus 
[login] [password]
```

U kunt ook verwijzen naar de [Oracle-client in Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

Wij adviseren dat u UTF-8 steun wanneer het installeren van de gegevensbestandmotor installeert. Op deze manier kunt u Unicode-databases maken.

**Verwant onderwerp**

* [Niet-geregistreerde optie in Adobe Campaign Classic-tabellen](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
