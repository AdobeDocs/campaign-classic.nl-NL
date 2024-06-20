---
product: campaign
title: Opdrachtregels
description: Opdrachtregels
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 4%

---

# Opdrachtregels{#command-lines}



De volgende opdrachtregels vereisen toegang tot de toepassingsserver. Voor plaatsingen die door Adobe worden ontvangen, kunnen deze bevelen slechts door Adobe worden uitgevoerd.

## Een instantie maken {#creating-an-instance}

Het maken van instanties kan worden uitgevoerd met behulp van opdrachtregels, met de syntaxis:

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

waarbij **eng** en **fra** zijn mogelijke waarden voor de `[lang]` parameter)

De opdracht **nlserver config -addinstance:instance1/demo&#42;/nl** laat u toe om een instantie tot stand te brengen genoemd **instance1** in het Engels met de DNS maskerdemo&#42;.

## Een database declareren {#declaring-a-database}

U kunt een bestaande database aan een instantie koppelen via de opdrachtregel door de volgende syntaxis te gebruiken:

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

De volgende waarden zijn mogelijk voor de **`[rdbms]`** parameter:

* **postgresql**: voor PostgreSQL
* **oracle**: voor Oracle,
* **mssql**: voor Microsoft SQL Server,

Het volgende bevel vormt het **demo** instantie met de SQL-typeserver die bekend staat als **base6**, gekoppeld aan de **campagne** en **password** op de **dbsrv** server:

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
