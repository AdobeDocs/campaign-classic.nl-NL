---
product: campaign
title: Gegevens importeren en exporteren met behulp van workflows
description: Leer hoe u gegevens importeert en exporteert met workflows in Campagne
feature: Data Management, Workflows
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# Gegevens importeren en exporteren met workflows {#import-export-workflows}



## Gegevens verzamelen {#collecting-data-workflows}

Workflows kunnen handig zijn om een aantal importprocessen te automatiseren. Of u nu gegevens uit een lokaal bestand of uit een SFTP importeert, u kunt workflows gebruiken om de procedures voor gegevensbeheer te standaardiseren.

### Gegevens uit een lijst gebruiken: lijst lezen {#using-data-from-a-list--read-list}

De gegevens die in een werkstroom worden verzonden, kunnen afkomstig zijn van lijsten waarin de gegevens vooraf zijn voorbereid en gestructureerd.

Deze lijst is mogelijk rechtstreeks gemaakt in Adobe Campaign of geïmporteerd door de **[!UICONTROL Import a list]** -optie. Raadpleeg voor meer informatie over deze optie [page](../../platform/using/about-generic-imports-exports.md).

Raadpleeg voor meer informatie over het gebruik van de activiteit in een leeslijst in een workflow de [deze pagina](../../workflow/using/read-list.md).

### Gegevens uit een bestand laden {#loading-data-from-a-file}

De gegevens die in een werkstroom worden verwerkt, kunnen uit een gestructureerd bestand worden geëxtraheerd, zodat het bestand in Adobe Campaign kan worden geïmporteerd.

Een beschrijving van de activiteit van de ladingsgegevens is te vinden in [Gegevens laden (bestand)](../../workflow/using/data-loading-file.md) sectie.

Voorbeeld van gestructureerd bestand dat moet worden geïmporteerd:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

Nadat gegevens zijn verzameld, kunt u deze gebruiken in uw workflows, bijvoorbeeld om een levering te verrijken of de database bij te werken. Raadpleeg [deze pagina](../../workflow/using/how-to-use-workflow-data.md) voor meer informatie.

## Gegevens exporteren {#exporting-data-via-a-workflow}

Workflows kunnen een handige manier zijn om een aantal van uw exportprocessen te automatiseren of om nauwkeurige sets gegevens te exporteren nadat u een aantal van de beschikbare activiteiten voor gegevensbeheer hebt gebruikt om uw gegevens te transformeren.

Exportbewerkingen worden uitgevoerd met een **[!UICONTROL Data extraction (file) activity]**. Voor meer op om de activiteit te vormen en te gebruiken, verwijs naar [deze pagina](../../workflow/using/extraction-file.md).
