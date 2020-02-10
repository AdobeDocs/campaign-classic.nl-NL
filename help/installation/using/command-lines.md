---
title: Opdrachtlijnen
seo-title: Opdrachtlijnen
description: Opdrachtlijnen
seo-description: null
page-status-flag: never-activated
uuid: fa897d6a-0326-4922-8936-2471af2f213c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 3621d4ec-8839-40c3-a574-486c408f79ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Opdrachtlijnen{#command-lines}

De volgende opdrachtregels vereisen toegang tot de toepassingsserver. Voor implementaties die worden gehost door Adobe, kunnen deze opdrachten alleen door Adobe worden uitgevoerd.

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
* **orakel**: voor Oracle,
* **mssql**: voor Microsoft SQL Server,
* **DB2**: voor de DB2-engine.

Het volgende bevel vormt de **demo** instantie met SQL typeserver die als **base6** wordt bekend, met de **campagnerekening** en zijn **wachtwoord** op de **dbsrv** server wordt verbonden:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

