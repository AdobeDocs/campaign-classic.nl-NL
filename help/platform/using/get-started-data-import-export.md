---
solution: Campaign Classic
product: campaign
title: Aan de slag met het importeren en exporteren van gegevens
description: Meer informatie over het importeren en exporteren van gegevens in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 37cc6cd8b71ec82cd4e6a910d6664a51ed5c091e
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 6%

---


# Aan de slag met het importeren en exporteren van gegevens {#get-started-data-import-export}

Adobe Campaign Classic biedt mogelijkheden voor gegevensbeheer waarmee u gegevens kunt importeren en exporteren. Deze bewerkingen kunnen worden uitgevoerd met behulp van workflows of generieke import en export.

>[!IMPORTANT]
>
>Houd bij het gebruik van deze functionaliteit rekening met de beperkingen voor SFTP-opslag, databaseopslag en actief profiel zoals vastgelegd in uw Adobe Campaign-contract.

## Workflows {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflows** zijn een handige manier om uw importprocessen te automatiseren. Of u nu gegevens uit een lokaal bestand of uit een SFTP importeert, u kunt hiermee de procedures voor gegevensbeheer standaardiseren.

Met workflows kunnen import- en exportbewerkingen automatisch volgens een schema worden herhaald, bijvoorbeeld om de gegevensuitwisseling tussen verschillende informatiesystemen te automatiseren.

Raadpleeg [deze sectie](../../platform/using/import-export-workflows.md) voor meer informatie.

## Algemene import- en exportbewerkingen {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

Bovendien, verstrekt Campaign Classic **generische invoer en de uitvoer** die u toestaan om af en toe invoer of uitvoerbanen tot stand te brengen.

De invoer en de uitvoer worden gevormd in specifieke malplaatjes, die u kunt vormen en gebruiken om invoer en de uitvoerbanen te lanceren en te controleren.

Raadpleeg [deze sectie](../../platform/using/about-generic-imports-exports.md) voor meer informatie over generieke import en export.

>[!IMPORTANT]
>Algemene invoer en uitvoer mogen alleen voor incidentele transacties worden gebruikt. Om de consistentie van de gegevens te waarborgen en de efficiëntie te verbeteren, wordt aangeraden de import- en exportbewerkingen uit te voeren met behulp van workflows.

## Gegevenscodering en -compressie {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Met Campaign Classic kunt u gecomprimeerde of gecodeerde bestanden importeren en gecomprimeerde of gecodeerde bestanden exporteren.

Deze bewerkingen worden uitgevoerd in workflows door het toepassen van voorbewerkingsfasen op de gegevens die u wilt gebruiken.

Raadpleeg deze secties voor meer informatie hierover:

* [Een bestand ontsleutelen of ontsleutelen](../../platform/using/unzip-decrypt.md)
* [Een bestand zoeken of versleutelen](../../platform/using/zip-encrypt.md)

## Aanbevolen procedures en problemen oplossen {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

Bij het uitvoeren van import- en exportbewerkingen moeten diverse [aanbevolen procedures worden gevolgd om de consistentie van gegevens binnen de database te waarborgen en om een veel voorkomende fout tijdens het bijwerken of exporteren te voorkomen.](../../platform/using/import-export-best-practices.md)

Daarnaast zijn aanbevelingen en algemene problemen met betrekking tot het gebruik van SFTP-servers beschikbaar in [deze sectie](../../platform/using/sftp-server-usage.md).
