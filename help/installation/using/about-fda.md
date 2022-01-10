---
product: campaign
title: Toegang tot een externe database
description: Leer hoe u gegevens in een externe database kunt openen en verwerken
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: a23f66a4822f3c87770c5c9741e91f78778931cb
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 3%

---

# Aan de slag met Federatieve gegevenstoegang {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign biedt de **Federale gegevenstoegang** (FDA) optie om informatie te verwerken die is opgeslagen in een of meer externe databases: u hebt toegang tot externe gegevens zonder de structuur van Adobe Campaign-gegevens te wijzigen.

## Vereisten {#operating-principle}

Met de optie FDA kunt u uw gegevensmodel uitbreiden in een database van derden. Het zal automatisch de structuur van de gerichte lijsten ontdekken en gegevens van de SQL bronnen gebruiken.

Voor het gebruik van deze functie worden de volgende voorwaarden vermeld:

* **Configuratie**: de lijst met compatibele externe databases is afhankelijk van uw [hostmodel](../../installation/using/hosting-models.md).
* **Externe databaseversie**: u hebt een externe database nodig die compatibel is met de Adobe Campaign FDA-module.

   De lijst met databasesystemen en compatibele versies per hostingmodel wordt gedetailleerd weergegeven in de campagne [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Machtigingen**: de gebruikers moeten ook [noodzakelijke machtigingen](../../installation/using/remote-database-access-rights.md) in Adobe Campaign en in de externe database.

