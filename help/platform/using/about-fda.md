---
title: Een externe database openen
description: Leer hoe u gegevens in een externe database kunt openen en verwerken
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 3acf2359c74a3dc4b18c8976fee14dcbaf3fa510
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 13%

---


# Over Federale gegevenstoegang {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

>[!CAUTION]
>
>Toegang tot een externe database via FDA is alleen mogelijk voor installaties op locatie of hybride installaties, behalve met de Snowflake-aansluitingen. For more on this, refer [to this page](../../installation/using/capability-matrix.md).

## Werkwijze {#operating-principle}

Met de optie FDA kunt u uw gegevensmodel uitbreiden in een database van derden. Het zal automatisch de structuur van de gerichte lijsten ontdekken en gegevens van de SQL bronnen gebruiken.

Als u deze functionaliteit wilt gebruiken, moet u:

1. Een externe database hebben die compatibel is met de Adobe Campaign FDA-module. De lijst met databasesystemen en compatibele versies wordt gedetailleerd weergegeven in de [compatibiliteitsmatrix](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html). Gebruikers moeten ook over de [benodigde machtigingen](../../platform/using/remote-database-access-rights.md) in Adobe Campaign en de externe database beschikken.
1. [Installeer de stuurprogramma](../../platform/using/specific-configuration-database.md) &#39;s die overeenkomen met uw database op de Adobe Campaign-server.
1. [Maak en configureer een externe account](../../platform/using/connecting-to-database.md) waarmee u de verbinding tussen Adobe Campaign en de externe database tot stand kunt brengen. Raadpleeg deze [pagina](../../platform/using/external-accounts.md)voor meer informatie over beschikbare externe accounts.
1. [Maak het schema](../../platform/using/creating-data-schema.md) van de externe database in Adobe Campaign. Hierdoor kunt u de gegevensstructuur van de externe database herkennen.
1. Uiteindelijk, [creeer een nieuwe doelafbeelding](../../platform/using/defining-data-mapping.md) van het eerder gecreeerd schema, in het geval waar de ontvangers van uw leveringen uit het externe gegevensbestand komen. Dit brengt bepaalde beperkingen met zich mee, met name wat betreft de personalisering van de leveringen.

Zodra het gegevensschema wordt gecreeerd, kunnen de gegevens in de werkschema&#39;s van Adobe Campaign worden verwerkt. Raadpleeg [deze sectie](../../workflow/using/accessing-an-external-database--fda-.md) voor meer informatie.

## Beschikbare externe databases {#external-database}

U vindt hieronder de lijst met alle externe databases die compatibel zijn met de Adobe Campaign FDA-module:

* Microsoft Azure Synapse Analytics. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#azure-external) voor meer informatie.
* Snowflake. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake) voor meer informatie.
* Hadoop. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3) voor meer informatie.
* Oracle. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#configure-access-to-oracle) voor meer informatie.
* Netezza. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#configure-access-to-netezza) voor meer informatie.
* IQ van Sybase. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#configure-access-to-sybase-iq) voor meer informatie.
* Tera-gegevens. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md#configure-access-to-teradata) voor meer informatie.
* SAP HANA. Raadpleeg deze [sectie](../../platform/using/specific-configuration-database.md) voor meer informatie.

## Beste praktijken en aanbevelingen {#best-practices-and-recommendations}

De optie FDA is bedoeld om de gegevens in externe databases in batchmodus te manipuleren in workflows. Het gebruik van de FDA in een andere context, bijvoorbeeld voor eenheidsoperaties, moet met voorzichtigheid plaatsvinden (personalisatie, interactie, real-time leveringen, enz.).

Vermijd de bewerkingen die zowel de Adobe Campaign als de externe database zoveel mogelijk moeten gebruiken. Hiervoor kunt u:

* Exporteer de Adobe Campaign-database naar de externe database en voer de bewerkingen alleen uit vanuit de externe database voordat u de resultaten opnieuw importeert in Adobe Campaign.
* Verzamel de gegevens in de externe Adobe Campaign-database en voer de bewerkingen lokaal uit.

Als u personalisatie in uw leveringen wilt uitvoeren gebruikend gegevens van het externe gegevensbestand, verzamel de gegevens in een werkschema te gebruiken om het ter beschikking te stellen in een tijdelijke lijst. Dan gebruik de gegevens van de tijdelijke lijst om uw levering te personaliseren.

## Beperkingen {#limitations}

De optie FDA wordt onderworpen aan de beperking van het externe databasesysteem dat u gebruikt.

Om redenen van prestaties raden we u niet aan deze functionaliteit te gebruiken voor het uitvoeren van eenheidsbewerkingen (levering, personalisatie, Interactie-module, real-time).
