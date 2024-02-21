---
product: campaign
title: De beste praktijken en beperkingen van de FDA bestrijden
description: Leer beste praktijken en beperkingen wanneer het werken met een externe gegevensbestand (FDA)
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 6%

---

# Best practices en beperkingen



## E-mailpersonalisatie optimaliseren met externe gegevens {#optimizing-email-personalization-with-external-data}

U kunt berichtpersonalisatie vooraf verwerken in een specifieke workflow. Om dit uit te voeren, gebruik **[!UICONTROL Prepare the personalization data with a workflow]** beschikbaar in het dialoogvenster **[!UICONTROL Analysis]** tabblad van de leveringseigenschappen.

Tijdens de leveringsanalyse, leidt deze optie automatisch tot en voert een werkschema uit dat alle gegevens met betrekking tot het doel in een tijdelijke lijst, met inbegrip van gegevens van lijsten verbonden in een extern gegevensbestand opslaat.

Met deze optie worden de prestaties aanzienlijk verbeterd wanneer de stap voor personalisatie wordt uitgevoerd.

## Gegevens uit een externe database gebruiken in een workflow {#using-data-from-an-external-database-in-a-workflow}

Bij meerdere Adobe Campaign-workflowactiviteiten kunt u de gegevens gebruiken die in een externe database zijn opgeslagen.

* **Filter op externe gegevens** - de [Query](../../workflow/using/targeting-data.md#selecting-data) Met activiteit kunt u externe gegevens toevoegen en gebruiken in de gedefinieerde filterconfiguraties. Raadpleeg [deze pagina](../../workflow/using/targeting-data.md#selecting-data) voor meer informatie.

* **Subsets maken** - de [Splitsen](../../workflow/using/split.md) kunt u subsets maken. U kunt externe gegevens gebruiken om de filtercriteria te bepalen aan gebruik. Raadpleeg [deze pagina](../../workflow/using/split.md) voor meer informatie.

* **Externe database laden** - U kunt de externe gegevens gebruiken in het dialoogvenster [Gegevens laden](../../workflow/using/data-loading-rdbms.md) (RDBMS) activiteit. Meer informatie in [deze pagina](../../workflow/using/data-loading-rdbms.md).

* **Informatie en koppelingen toevoegen** - de [Verrijking](../../workflow/using/enrichment.md) Met activiteit kunt u aanvullende gegevens toevoegen aan de werktabel van de werkstroom en koppelingen maken naar een externe tabel. In deze context kan het gegevens uit een externe database gebruiken. Meer informatie in [deze pagina](../../workflow/using/enrichment.md).

## FDA-beperkingen {#limitations}

De optie FDA is bedoeld om de gegevens in externe databases in batchmodus te manipuleren in workflows. Om prestatieproblemen te voorkomen, wordt het niet aanbevolen de FDA-module te gebruiken in het kader van eenheidsbewerkingen, zoals personalisatie, interactie, realtime berichten, enz.

Vermijd de bewerkingen die zowel de Adobe Campaign als de externe database zoveel mogelijk moeten gebruiken. Hiervoor kunt u:

* Exporteer de Adobe Campaign-database naar de externe database en voer de bewerkingen alleen uit vanuit de externe database voordat u de resultaten opnieuw importeert in Adobe Campaign.

* Verzamel de gegevens in de externe Adobe Campaign-database en voer de bewerkingen lokaal uit.

Als u personalisatie in uw leveringen wilt uitvoeren gebruikend gegevens van het externe gegevensbestand, verzamel de gegevens in een werkschema te gebruiken om het ter beschikking te stellen in een tijdelijke lijst. Dan gebruik de gegevens van de tijdelijke lijst om uw levering te personaliseren.

De optie FDA is afhankelijk van de beperkingen van het externe databasesysteem dat u gebruikt.
