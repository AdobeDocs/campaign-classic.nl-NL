---
solution: Campaign Classic
product: campaign
title: Data importeren en exporteren met behulp van workflows
description: Leer hoe u gegevens importeert en exporteert met workflows in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 8%

---


# Data importeren en exporteren met behulp van workflows {#import-export-workflows}

## Gegevens {#collecting-data-workflows} verzamelen

Workflows kunnen handig zijn om een aantal importprocessen te automatiseren. Of u nu gegevens uit een lokaal bestand of uit een SFTP importeert, u kunt workflows gebruiken om de procedures voor gegevensbeheer te standaardiseren.

### Gegevens uit een lijst gebruiken: Leeslijst {#using-data-from-a-list--read-list}

De gegevens die in een werkstroom worden verzonden, kunnen afkomstig zijn van lijsten waarin de gegevens vooraf zijn voorbereid en gestructureerd.

Deze lijst is mogelijk rechtstreeks gemaakt in Adobe Campaign of geïmporteerd door de optie **[!UICONTROL Import a list]**. Voor meer op deze optie, verwijs naar deze [pagina](../../platform/using/about-generic-imports-exports.md).

Raadpleeg [deze pagina](../../workflow/using/read-list.md) voor meer informatie over het gebruik van de activiteit in de leeslijst in een workflow.

### Gegevens laden uit een bestand {#loading-data-from-a-file}

De gegevens die in een werkstroom worden verwerkt, kunnen uit een gestructureerd bestand worden geëxtraheerd, zodat het bestand in Adobe Campaign kan worden geïmporteerd.

Een beschrijving van de activiteit van de ladingsgegevens kan in [het laden van gegevens (dossier)](../../workflow/using/data-loading--file-.md) sectie worden gevonden.

Voorbeeld van gestructureerd bestand dat moet worden geïmporteerd:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

Nadat gegevens zijn verzameld, kunt u deze gebruiken in uw workflows, bijvoorbeeld om een levering te verrijken of de database bij te werken. Raadpleeg [deze pagina](../../workflow/using/how-to-use-workflow-data.md) voor meer informatie.

## Data exporteren {#exporting-data-via-a-workflow}

Workflows kunnen een handige manier zijn om een aantal van uw exportprocessen te automatiseren of om nauwkeurige sets gegevens te exporteren nadat u een aantal van de beschikbare activiteiten voor gegevensbeheer hebt gebruikt om uw gegevens te transformeren.

Exportbewerkingen worden uitgevoerd met een **[!UICONTROL Data extraction (file) activity]**. Raadpleeg [deze pagina](../../workflow/using/extraction--file-.md) voor meer informatie over het configureren en gebruiken van de activiteit.
