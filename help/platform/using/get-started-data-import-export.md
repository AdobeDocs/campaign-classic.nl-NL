---
product: campaign
title: Aan de slag met gegevens importeren en exporteren
description: Meer informatie over het importeren en exporteren van gegevens in campagne
feature: Data Management, Encryption
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d6055d97-75fc-4ed7-89bd-8336157454eb
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 9%

---

# Aan de slag met gegevens importeren en exporteren {#get-started-data-import-export}



Adobe Campaign Classic biedt mogelijkheden voor gegevensbeheer waarmee u gegevens kunt importeren en exporteren. Deze bewerkingen kunnen worden uitgevoerd met behulp van workflows of generieke import en export.

>[!IMPORTANT]
>
>Houd bij het gebruik van deze functionaliteit rekening met de beperkingen voor SFTP-opslag, databaseopslag en actief profiel zoals vastgelegd in uw Adobe Campaign-contract.

## Workflows {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflows** Dit is een handige manier om importprocessen te automatiseren. Of u nu gegevens uit een lokaal bestand of uit een SFTP importeert, u kunt hiermee de procedures voor gegevensbeheer standaardiseren.

Met workflows kunnen import- en exportbewerkingen automatisch volgens een schema worden herhaald, bijvoorbeeld om de gegevensuitwisseling tussen verschillende informatiesystemen te automatiseren.

Raadpleeg [deze sectie](../../platform/using/import-export-workflows.md) voor meer informatie.

## Algemene invoer en uitvoer {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

Bovendien biedt Campaign Classic **algemene invoer en uitvoer** waarmee u af en toe import- of exporttaken kunt maken.

De invoer en de uitvoer worden gevormd in specifieke malplaatjes, die u kunt vormen en gebruiken om invoer en de uitvoerbanen te lanceren en te controleren.

Voor meer informatie over de invoer en de uitvoer van generieke geneesmiddelen raadpleegt u [deze sectie](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>Algemene invoer en uitvoer mogen alleen voor incidentele transacties worden gebruikt. Om de consistentie van de gegevens te waarborgen en de efficiëntie te verbeteren, wordt aangeraden de import- en exportbewerkingen uit te voeren met behulp van workflows.

## Gegevensversleuteling en -compressie {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Met Campaign Classic kunt u gecomprimeerde of gecodeerde bestanden importeren en gecomprimeerde of gecodeerde bestanden exporteren.

Deze bewerkingen worden uitgevoerd in workflows door het toepassen van voorbewerkingsfasen op de gegevens die u wilt gebruiken.

Raadpleeg deze secties voor meer informatie hierover:

* [Een bestand decoderen of decoderen](../../platform/using/unzip-decrypt.md)
* [Een bestand comprimeren of versleutelen](../../platform/using/zip-encrypt.md)

## Aanbevolen werkwijzen en problemen oplossen {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

U moet verschillende [best practices](../../platform/using/import-export-best-practices.md) bij het uitvoeren van import- en exportbewerkingen om de consistentie van de gegevens in de database te waarborgen en om veelvoorkomende fouten tijdens update- of exportbewerkingen te voorkomen.

Daarnaast zijn aanbevelingen en algemene problemen met betrekking tot het gebruik van SFTP-servers beschikbaar in [deze sectie](../../platform/using/sftp-server-usage.md).
