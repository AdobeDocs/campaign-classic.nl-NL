---
title: Informatie over het klassieke gegevensmodel van Adobe Campagne
description: In dit document worden de grondbeginselen van het gegevensmodel van Adobe Campaign Classic beschreven.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Een aangepaste tabel voor ontvangers gebruiken{#custom-recipient-table}

Bij het ontwerpen van uw Adobe Campagne-gegevensmodel kunt u de [out-of-the-box Ontvanger tabel](../../configuration/using/default-recipient-table.md)gebruiken of besluiten om een niet-standaard ontvangende tabel te maken waarin u marketingprofielen kunt opslaan.

Als uw gegevensmodel niet in de op de ontvanger gerichte structuur past, kunt u in Adobe Campagne andere tabellen instellen als de doeldimensie. Dit kan bijvoorbeeld van belang zijn wanneer u huishoudens, rekeningen (zoals mobiele telefoons) en bedrijven/sites moet aanspreken in plaats van alleen ontvangers.

>[!NOTE]
>
>In dit geval moet u een nieuwe [doeltoewijzing](../../configuration/using/target-mapping.md)maken.

Alle principes en stappen nodig wanneer het gebruiken van een lijst van de douaneontvanger zijn gedetailleerd in deze [sectie](../../configuration/using/about-custom-recipient-table.md).

De voordelen van een aangepaste tabel voor ontvangers zijn als volgt:

## Flexibel gegevensmodel {#flexible-data-model}

De tabel Ontvanger uit de doos is niet bruikbaar als u de meeste tabelvelden Ontvanger niet nodig hebt of als het gegevensmodel niet op de ontvanger is gericht.

## Schaalbaarheid {#scalability}

Grote volumes vereisen een gestroomlijnde tabel met weinig velden voor een efficiënt ontwerp. De out-of-the-box ontvangertabel zou te veel nutteloze velden hebben, wat van invloed kan zijn op de prestaties en een gebrek aan efficiëntie.

## Gegevenslocatie {#data-location}

Als de gegevens op een extern bestaand marketing gegevensbestand verblijven, kan het teveel inspanning vereisen om de uit-van-de-doos Lijst van de Ontvanger te gebruiken. Het maken van een nieuwe op basis van een bestaande structuur is eenvoudiger.

## Eenvoudige migratie {#easy-migration}

Er is geen onderhoud nodig om te controleren of alle extensies nog geldig zijn na de upgrade.

>[!IMPORTANT]
>
>Het gebruiken van een douane ontvankelijke lijst is gereserveerd voor gevorderde gebruikers en is onderworpen aan sommige beperkingen. Zie deze sectie voor meer informatie.
