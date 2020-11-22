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

## Een instantie maken {#creating-an-instance}

Het maken van instanties kan worden uitgevoerd met behulp van opdrachtregels, met de syntaxis:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(waarbij **eng** en **fra** mogelijke waarden voor de `[lang]` parameter zijn)

Met de command **nlserver config -addinstance:instance1/demo*/eng** kunt u een instantie met de naam **instance1** in het Engels maken met de DNS-maskerdemo*.

## Database declareren {#declaring-a-database}

U kunt een bestaande database aan een instantie koppelen via de opdrachtregel door de volgende syntaxis te gebruiken:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

De volgende waarden zijn mogelijk voor de **`[rdbms]`** parameter:

* **postgresql**: voor PostgreSQL,
* **oracle**: voor Oracle,
* **mssql**: voor Microsoft SQL Server,
* **DB2**: voor de DB2-engine.

Het volgende bevel vormt de **demo** instantie met SQL typeserver die als **base6** wordt bekend, met de **campagnerekening** en zijn **wachtwoord** op de **dbsrv** server wordt verbonden:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

