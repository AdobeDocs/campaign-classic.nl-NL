---
solution: Campaign Classic
product: campaign
title: Opdrachtregels
description: Opdrachtregels
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---


# Opdrachtregels{#command-lines}

De volgende opdrachtregels vereisen toegang tot de toepassingsserver. Voor plaatsingen die door Adobe worden ontvangen, kunnen deze bevelen slechts door Adobe worden uitgevoerd.

## Een instantie {#creating-an-instance} maken

Het maken van instanties kan worden uitgevoerd met behulp van opdrachtregels, met de syntaxis:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(waarbij **eng** en **fra** mogelijke waarden zijn voor de parameter `[lang]`)

Met de opdracht **nlserver config -addinstance:instance1/demo*/eng** kunt u een instantie maken met de naam **instance1** in het Engels met de DNS-maskerdemo*.

## Database {#declaring-a-database} declareren

U kunt een bestaande database aan een instantie koppelen via de opdrachtregel door de volgende syntaxis te gebruiken:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

De volgende waarden zijn mogelijk voor de parameter **`[rdbms]`**:

* **postgresql**: voor PostgreSQL,
* **oracle**: voor Oracle,
* **mssql**: voor Microsoft SQL Server,
* **DB2**: voor de DB2-engine.

Met de volgende opdracht configureert u de **demo**-instantie met de SQL-typeserver die bekend staat als **base6**, gekoppeld aan de **campagne**-account en zijn **password** op de **dbsrv**-server:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

