---
product: campaign
title: Aanbevelingen voor Campaign Classic-database
description: Aanbevelingen voor databases
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 3%

---

# Database{#database}



De databaseserver kan op elk besturingssysteem worden uitgevoerd, ongeacht het besturingssysteem dat door de toepassingsserver of -servers wordt gebruikt, zolang er tussen de servers netwerkconnectiviteit is.

Het besturingssysteem van de databaseserver is niet belangrijk zolang er verbinding met de verschillende componenten van Adobe Campaign beschikbaar is.

Controleer ook de [Databasetoegangslagen](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) sectie.

## Microsoft SQL Server {#microsoft-sql-server}

De native client moet op de Adobe Campaign-toepassingsservers zijn geïnstalleerd.

U kunt controleren op de native client op de server via het configuratiescherm van het ODBC-stuurprogramma, onder **SQL Server Native Client 11.0**.

De volgende toegang DLL moet aanwezig zijn: **sqlncli11.dll**.

Toegang tot DLL&#39;s vindt u op de Microsoft-website.

>[!NOTE]
>
>Toegang tot Microsoft SQL Server vanaf een toepassingsserver die in Linux wordt uitgevoerd, wordt niet ondersteund.

## Oracle {#oracle}

>[!NOTE]
>
>Kolomnamen met multi-bytetekens worden niet ondersteund.

De **NLS_NCHAR_CHARACTERSET** en **NLS_CHARACTERSET** parameters moeten correct worden gevormd opdat het gegevensbestand in Unicode of ANSI werkt.

Adobe Campaign gebruikt standaardcodering voor Oracles. Het gebruik van andere codering kan compatibiliteitsproblemen veroorzaken: in dit geval kunt u contact opnemen met de technische ondersteuning.

Ga als volgt te werk om meer te weten te komen over uw codering **sqlplus** opdracht:

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

Aanmelden bij **sqlplus** en gebruik het gebruikersprofiel van het Oracle:

```
su - oracle 
sqlplus 
[login] [password]
```

U kunt ook verwijzen naar [Oracle Client in Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

Wij adviseren dat u UTF-8 steun wanneer het installeren van de gegevensbestandmotor installeert. Op deze manier kunt u Unicode-databases maken.

**Verwante onderwerpen**

* [Niet-geregistreerde optie in Adobe Campaign Classic-tabellen](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
