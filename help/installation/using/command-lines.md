---
product: campaign
title: Opdrachtregels
description: Opdrachtregels
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# Opdrachtregels{#command-lines}

![](../../assets/v7-only.svg)

De volgende opdrachtregels vereisen toegang tot de toepassingsserver. Voor plaatsingen die door Adobe worden ontvangen, kunnen deze bevelen slechts door Adobe worden uitgevoerd.

## Een instantie maken {#creating-an-instance}

Het maken van instanties kan worden uitgevoerd met behulp van opdrachtregels, met de syntaxis:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

waarbij **eng** en **fra** zijn mogelijke waarden voor de `[lang]` parameter)

De opdracht **nlserver config -addinstance:instance1/demo*/eng** laat u toe om een instantie tot stand te brengen genoemd **instance1** in het Engels met de DNS mask demo*.

## Een database declareren {#declaring-a-database}

U kunt een bestaande database aan een instantie koppelen via de opdrachtregel door de volgende syntaxis te gebruiken:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

De volgende waarden zijn mogelijk voor de **`[rdbms]`** parameter:

* **postgresql**: voor PostgreSQL,
* **oracle**: voor Oracle,
* **mssql**: voor Microsoft SQL Server,
* **DB2**: voor de DB2-engine.

Het volgende bevel vormt het **demo** instantie met de SQL-typeserver die bekend staat als **base6**, gekoppeld aan de **campagne** en **password** op de **dbsrv** server:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
