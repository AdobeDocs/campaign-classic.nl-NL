---
product: campaign
title: Toegang tot een externe database
description: Leer hoe u gegevens in een externe database kunt openen en verwerken
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# Aan de slag met Federatieve gegevenstoegang {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign biedt de **Federale gegevenstoegang** (FDA) optie om informatie te verwerken die is opgeslagen in een of meer externe databases: u hebt toegang tot externe gegevens zonder de structuur van Adobe Campaign-gegevens te wijzigen.

## Vereisten {#operating-principle}

Met de optie FDA kunt u uw gegevensmodel uitbreiden in een database van derden. Het zal automatisch de structuur van de gerichte lijsten ontdekken en gegevens van de SQL bronnen gebruiken.

Voor het gebruik van deze functie worden de volgende voorwaarden vermeld:

* **Configuratie**: behalve voor Snowflake hebt u een **op locatie** of **hybride** hostingmodel voor instellen van Federated Data Access. [Meer informatie](../../installation/using/hosting-models.md)
* **Externe databaseversie**: u hebt een externe database nodig die compatibel is met de Adobe Campaign FDA-module. De lijst met databasesystemen en compatibele versies wordt gedetailleerd weergegeven in de campagne [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
* **Machtigingen**: de gebruikers moeten ook [noodzakelijke machtigingen](../../installation/using/remote-database-access-rights.md) in Adobe Campaign en in de externe database.

