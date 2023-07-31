---
product: campaign
title: Aan de slag met Federatieve gegevenstoegang
description: Leer hoe u gegevens in een externe database kunt openen en verwerken
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 1%

---

# Aan de slag met Federatieve gegevenstoegang {#about-federated-data-access}



Adobe Campaign biedt de **Federale gegevenstoegang** (FDA) om informatie te verwerken die is opgeslagen in een of meer externe databases: u hebt toegang tot externe gegevens zonder de structuur van Adobe Campaign-gegevens te wijzigen.

## Vereisten {#operating-principle}

Met de optie FDA kunt u uw gegevensmodel uitbreiden in een database van derden. Het zal automatisch de structuur van de gerichte lijsten ontdekken en gegevens van de SQL bronnen gebruiken.

Voor het gebruik van deze functie worden de volgende voorwaarden vermeld:

* **Configuratie**: de lijst met compatibele externe databases is afhankelijk van uw [hostmodel](../../installation/using/hosting-models.md).
* **Externe databaseversie**: u hebt een externe database nodig die compatibel is met de Adobe Campaign FDA-module.

  De lijst met databasesystemen en compatibele versies per hostingmodel wordt gedetailleerd weergegeven in de campagne [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Machtigingen**: gebruikers moeten ook beschikken over de [noodzakelijke machtigingen](../../installation/using/remote-database-access-rights.md) in Adobe Campaign en in de externe database.

