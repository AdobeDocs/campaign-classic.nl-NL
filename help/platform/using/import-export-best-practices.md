---
product: campaign
title: Best practices voor importeren en exporteren
description: Meer informatie over de aanbevolen procedures bij het importeren of exporteren van gegevens
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 2%

---

# Best practices voor importeren en exporteren {#import-export-best-practices}



Voorzichtig zijn en het volgen van de weinige hieronder gedetailleerde eenvoudige regels zullen veel helpen om gegevensconsistentie binnen het gegevensbestand te verzekeren en gemeenschappelijke fouten tijdens gegevensbestandupdate of gegevensuitvoer te vermijden.

## Workflowsjablonen gebruiken {#using-import-templates}

De meeste werkstromen die gericht zijn op het importeren van gegevens moeten de volgende activiteiten bevatten: **[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

Door workflowsjablonen te gebruiken is het heel handig om vergelijkbare importbewerkingen voor te bereiden en ervoor te zorgen dat de gegevensbestanden consistent zijn.

In veel projecten wordt de invoer zonder **[!UICONTROL Deduplication]** activiteit omdat de dossiers in het project worden gebruikt geen duplicaten hebben. Soms worden duplicaten weergegeven van het importeren van verschillende bestanden. De-duplicatie is dan moeilijk. Daarom is een deduplicatiestap een goede voorzorgsmaatregel in alle importworkflows.

Ga niet uit van de veronderstelling dat de inkomende gegevens consistent en correct zijn, of dat de afdeling van IT of de supervisor van Adobe Campaign het zal behandelen. Houd tijdens het project rekening met het opschonen van gegevens. U kunt gegevens dedupliceren, op elkaar afstemmen en de consistentie behouden bij het importeren van gegevens.

Een voorbeeld van een generiek werkschemamalplaatje dat voor het invoeren van gegevens wordt ontworpen is beschikbaar in [Voorbeeld: Workflowsjabloon voor het importeren van gegevens](../../platform/using/creating-import-export-templates.md) sectie.

## Vlakke bestandsindelingen gebruiken {#using-flat-file-formats}

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

## Compressie gebruiken {#using-compression}

Gebruik indien mogelijk gecomprimeerde bestanden voor importeren en exporteren. GZIP wordt standaard ondersteund. U kunt voorbewerking toevoegen bij het importeren van bestanden of naverwerking bij het extraheren van gegevens, respectievelijk in het dialoogvenster **[!UICONTROL Load file]** en **[!UICONTROL Extract file]** workflowactiviteiten.

**Verwante onderwerpen:**

* [Activiteit bij laden van gegevens (bestand)](../../workflow/using/data-loading--file-.md)
* [Activiteit voor gegevensextractie (bestand)](../../workflow/using/extraction--file-.md)

## Importeren in de Delta-modus {#importing-in-delta-mode}

Regelmatige invoer moet plaatsvinden in de deltamodus. Dit betekent dat alleen gewijzigde of nieuwe gegevens telkens naar Adobe Campaign worden verzonden in plaats van naar de hele tabel.

Volledige invoer mag alleen voor eerste lading worden gebruikt.

## Consistentie behouden {#maintaining-consistency}

Om de consistentie van de gegevens in de Adobe Campaign-database te waarborgen, volgt u de volgende beginselen:

* Als de geïmporteerde gegevens overeenkomen met een referentietabel in Adobe Campaign, moet de tabel in de workflow overeenkomen met die tabel. Records die niet overeenkomen, moeten worden afgewezen.
* Zorg ervoor dat de geïmporteerde gegevens altijd zijn **&quot;normalized&quot;** (e-mail, telefoonnummer, direct mailadres) en dat deze normalisatie betrouwbaar is en in de loop der jaren niet zal veranderen. Als dit niet het geval is, zullen sommige duplicaten waarschijnlijk in het gegevensbestand verschijnen, en aangezien Adobe Campaign geen hulpmiddelen verstrekt om &quot;vage&quot;aanpassing te doen, zal het zeer moeilijk zijn om hen te beheren en te verwijderen.
* Transactionele gegevens moeten een afstemmingssleutel hebben en in overeenstemming zijn met de bestaande gegevens om het creëren van duplicaten te voorkomen.
* **Gerelateerde bestanden op volgorde importeren**. Als het importeren uit meerdere bestanden bestaat die van elkaar afhankelijk zijn, moet de workflow ervoor zorgen dat de bestanden in de juiste volgorde worden geïmporteerd. Wanneer een bestand mislukt, worden de andere bestanden niet geïmporteerd.
* **Dedupliceren** te behouden, te combineren en consistentie te behouden bij het importeren van gegevens.
