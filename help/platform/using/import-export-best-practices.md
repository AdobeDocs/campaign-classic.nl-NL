---
solution: Campaign Standard
product: campaign
title: Beste werkwijzen importeren en exporteren
description: Meer informatie over de aanbevolen procedures voor het importeren of exporteren van gegevens.
audience: automating
content-type: reference
topic-tags: workflow-general-operation
translation-type: tm+mt
source-git-commit: a2a99135bdd74d87c04262b53e074b6aa05e7915
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---


# Beste werkwijzen importeren en exporteren {#import-export-best-practices}

Voorzichtig zijn en het volgen van de weinige hieronder gedetailleerde eenvoudige regels zullen veel helpen om gegevensconsistentie binnen het gegevensbestand te verzekeren en gemeenschappelijke fouten tijdens gegevensbestandupdate of gegevensuitvoer te vermijden.

## Workflowsjablonen gebruiken {#using-import-templates}

De meeste werkstromen die gericht zijn op het importeren van gegevens moeten de volgende activiteiten bevatten: **[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

Door workflowsjablonen te gebruiken is het heel handig om vergelijkbare importbewerkingen voor te bereiden en ervoor te zorgen dat de gegevensbestanden consistent zijn.

In vele projecten, wordt de invoer gebouwd zonder **[!UICONTROL Deduplication]** activiteit omdat de dossiers die in het project worden gebruikt geen duplicaten hebben. Soms worden duplicaten weergegeven van het importeren van verschillende bestanden. De-duplicatie is dan moeilijk. Daarom is een deduplicatiestap een goede voorzorgsmaatregel in alle importworkflows.

Ga niet uit van de veronderstelling dat de inkomende gegevens consistent en correct zijn, of dat de afdeling van IT of de supervisor van Adobe Campaign het zal behandelen. Houd tijdens het project rekening met het opschonen van gegevens. U kunt gegevens dedupliceren, op elkaar afstemmen en de consistentie behouden bij het importeren van gegevens.

Een voorbeeld van een generiek werkschemamalplaatje dat voor het invoeren van gegevens wordt ontworpen is beschikbaar in [Voorbeeld: Workflowsjabloon voor het importeren van gegevens](../../platform/using/creating-import-export-templates.md)-sectie.

## Vlakke bestandsindelingen {#using-flat-file-formats} gebruiken

De meest efficiënte indeling voor importeren is platte bestanden. Vlakke bestanden kunnen in de bulkmodus op databaseniveau worden geïmporteerd.

Bijvoorbeeld:

* Scheidingsteken: tab of puntkomma
* Eerste regel met kopteksten
* Geen scheidingsteken voor tekenreeks
* Datumnotatie: YYYY/MM/DD HH:mm:SS

Voorbeeld van te importeren bestand:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## Compressie {#using-compression} gebruiken

Gebruik indien mogelijk gecomprimeerde bestanden voor importeren en exporteren. GZIP wordt standaard ondersteund. U kunt voorbewerking toevoegen bij het importeren van bestanden of naverwerking bij het extraheren van gegevens, respectievelijk in de **[!UICONTROL Load file]**- en **[!UICONTROL Extract file]**-workflowactiviteiten.

**Verwante onderwerpen:**

* [Activiteit bij laden van gegevens (bestand)](../../workflow/using/data-loading--file-.md)
* [Activiteit voor gegevensextractie (bestand)](../../workflow/using/extraction--file-.md)

## Importeren in Deltamodus {#importing-in-delta-mode}

Regelmatige invoer moet plaatsvinden in de deltamodus. Dit betekent dat alleen gewijzigde of nieuwe gegevens telkens naar Adobe Campaign worden verzonden in plaats van naar de hele tabel.

Volledige invoer mag alleen voor eerste lading worden gebruikt.

## Consistentie {#maintaining-consistency} behouden

Om de consistentie van de gegevens in de Adobe Campaign-database te waarborgen, volgt u de volgende beginselen:

* Als de geïmporteerde gegevens overeenkomen met een referentietabel in Adobe Campaign, moet de tabel in de workflow overeenkomen met die tabel. Records die niet overeenkomen, moeten worden afgewezen.
* Zorg ervoor dat de geïmporteerde gegevens altijd **&quot;genormaliseerd&quot;** (e-mail, telefoonnummer, direct-mailadres) zijn en dat deze normalisatie betrouwbaar is en in de loop der jaren niet zal veranderen. Als dit niet het geval is, zullen sommige duplicaten waarschijnlijk in het gegevensbestand verschijnen, en aangezien Adobe Campaign geen hulpmiddelen verstrekt om &quot;vage&quot;aanpassing te doen, zal het zeer moeilijk zijn om hen te beheren en te verwijderen.
* Transactionele gegevens moeten een afstemmingssleutel hebben en in overeenstemming zijn met de bestaande gegevens om het creëren van duplicaten te voorkomen.
* **Verwante bestanden op volgorde** importeren. Als het importeren uit meerdere bestanden bestaat die van elkaar afhankelijk zijn, moet de workflow ervoor zorgen dat de bestanden in de juiste volgorde worden geïmporteerd. Wanneer een bestand mislukt, worden de andere bestanden niet geïmporteerd.
* **U kunt gegevens dedupliceren**, combineren en de consistentie behouden wanneer u ze importeert.
