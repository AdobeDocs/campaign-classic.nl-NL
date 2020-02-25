---
title: Een externe database openen
seo-title: Een externe database openen
description: Een externe database openen
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 47fd157e369ddf6c67f0b2b467799cecc6e5a822

---


# Over Federale gegevenstoegang {#about-federated-data-access}

Adobe Campaign biedt de optie **Federated Data Access** (FDA) om gegevens te verwerken die zijn opgeslagen in een of meer externe databases: u hebt toegang tot externe gegevens zonder de structuur van Adobe Campagne-gegevens te wijzigen.

>[!CAUTION]
>
>Toegang tot een externe database via de FDA is alleen mogelijk voor installaties op locatie of hybride installaties, behalve met de Snowflake-aansluitingen. Raadpleeg deze [pagina](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)voor meer informatie.

## Exploitatiebeginsel {#operating-principle}

Met de optie FDA kunt u uw gegevensmodel uitbreiden in een database van derden. Het zal automatisch de structuur van de gerichte lijsten ontdekken en gegevens van de SQL bronnen gebruiken.


Als u deze functionaliteit wilt gebruiken, moet u:

1. Een externe database hebben die compatibel is met de Adobe Campagne FDA-module. De lijst met databasesystemen en compatibele versies wordt gedetailleerd weergegeven in de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). Gebruikers moeten ook over de [benodigde machtigingen](../../platform/using/remote-database-access-rights.md) beschikken in Adobe Campaign en in de externe database.
1. [Installeer de stuurprogramma](../../platform/using/specific-configuration-database.md) &#39;s die overeenkomen met uw database op de Adobe Campaign-server.
1. [Maak en configureer een extern account](../../platform/using/connecting-to-database.md) waarmee u de verbinding tussen Adobe Campagne en de externe database tot stand kunt brengen. Raadpleeg deze [pagina](../../platform/using/external-accounts.md)voor meer informatie over beschikbare externe accounts.
1. [Maak het schema](../../platform/using/creating-data-schema.md) van de externe database in Adobe Campaign. Hierdoor kunt u de gegevensstructuur van de externe database herkennen.
1. Uiteindelijk, [creeer een nieuwe doelafbeelding](../../platform/using/defining-data-mapping.md) van het eerder gecreeerd schema, in het geval waar de ontvangers van uw leveringen uit het externe gegevensbestand komen. Dit brengt bepaalde beperkingen met zich mee, met name wat betreft de personalisering van de leveringen.

Zodra het gegevensschema wordt gecreeerd, kunnen de gegevens in de werkschema&#39;s van de Campagne van Adobe worden verwerkt. Zie [deze sectie](../../workflow/using/executing-a-workflow.md#architecture)voor meer informatie.

## Beste praktijken en aanbevelingen {#best-practices-and-recommendations}

De optie FDA is bedoeld om de gegevens in externe databases in batchmodus te manipuleren in workflows. Het gebruik van de FDA in een andere context, bijvoorbeeld voor eenheidsoperaties, moet met voorzichtigheid plaatsvinden (personalisatie, interactie, real-time leveringen, enz.).

Vermijd zoveel mogelijk de bewerkingen die zowel de Adobe-campagne als de externe database moeten gebruiken. Hiervoor kunt u:

* Exporteer de Adobe Campagne-database naar de externe database en voer de bewerkingen alleen uit vanuit de externe database voordat u de resultaten opnieuw importeert in Adobe Campagne.
* Verzamel de gegevens in de externe Adobe Campagne-database en voer de bewerkingen lokaal uit.

Als u personalisatie in uw leveringen wilt uitvoeren gebruikend gegevens van het externe gegevensbestand, verzamel de gegevens in een werkschema te gebruiken om het ter beschikking te stellen in een tijdelijke lijst. Dan gebruik de gegevens van de tijdelijke lijst om uw levering te personaliseren.

## Beperkingen {#limitations}

De optie FDA wordt onderworpen aan de beperking van het externe databasesysteem dat u gebruikt.

Om redenen van prestaties raden we u niet aan deze functionaliteit te gebruiken voor het uitvoeren van eenheidsbewerkingen (levering, personalisatie, Interactie-module, real-time).
