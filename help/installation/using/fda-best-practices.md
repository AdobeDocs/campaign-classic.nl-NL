---
product: campaign
title: De beste praktijken en beperkingen van de FDA bestrijden
description: Leer beste praktijken en beperkingen wanneer het werken met een externe gegevensbestand (FDA)
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Best practices en beperkingen



## E-mailpersonalisatie optimaliseren met externe gegevens {#optimizing-email-personalization-with-external-data}

U kunt berichtpersonalisatie vooraf verwerken in een specifieke workflow. Gebruik hiervoor de optie **[!UICONTROL Prepare the personalization data with a workflow]** op het tabblad **[!UICONTROL Analysis]** van de leveringseigenschappen.

Tijdens de leveringsanalyse, leidt deze optie automatisch tot en voert een werkschema uit dat alle gegevens met betrekking tot het doel in een tijdelijke lijst, met inbegrip van gegevens van lijsten verbonden in een extern gegevensbestand opslaat.

Met deze optie worden de prestaties aanzienlijk verbeterd wanneer de stap voor personalisatie wordt uitgevoerd.

## Gegevens uit een externe database gebruiken in een workflow {#using-data-from-an-external-database-in-a-workflow}

Bij meerdere Adobe Campaign-workflowactiviteiten kunt u de gegevens gebruiken die in een externe database zijn opgeslagen.

* **Filter op externe gegevens** - de activiteit van de Vraag staat u toe om externe gegevens toe te voegen en het in de bepaalde filterconfiguraties te gebruiken. Voor meer op dit, verwijs naar de [ Campagne v8 documentatie ] https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html) {target="_blank"}.

* **creeer ondergroepen** - de Gesplitste activiteit staat u toe om ondergroepen tot stand te brengen. U kunt externe gegevens gebruiken om de filtercriteria te bepalen aan gebruik. Verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}.

* **Laad extern gegevensbestand** - u kunt de externe gegevens in de het laden van Gegevens (RDBMS) activiteit gebruiken. Leer meer in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-rdbms.html){target="_blank"}.

* **het Toevoegen van informatie en verbindingen** - de activiteit van de Verrijking laat u extra gegevens aan de werklijst van het werkschema, en verbindingen aan een externe lijst toevoegen. In deze context kan het gegevens uit een externe database gebruiken. Verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}.

## Afvoerkanalen en beperkingen {#fda-limitations}

De optie FDA is bedoeld om de gegevens in externe databases in batchmodus te manipuleren in workflows. Om prestatieproblemen te voorkomen, wordt het niet aanbevolen de FDA-module te gebruiken in het kader van eenheidsbewerkingen, zoals personalisatie, interactie, realtime berichten, enz.

Het richten van gegevens van één gegevensbestand en het fileren van de resultaten gebruikend een het filtreren dimensie die tot een ander gegevensbestand behoort wordt niet gesteund. U kunt zich niet bij lijsten aansluiten die op verschillende gegevensbronnen in één vraag zijn. U kunt deze beperking overwinnen met andere workflowactiviteiten, zoals de dimensie Wijzigen.

Vermijd de bewerkingen die zowel de Adobe Campaign als de externe database zoveel mogelijk moeten gebruiken. De beste manier is om:

* Exporteer de Adobe Campaign-database naar de externe database en voer de bewerkingen alleen uit vanuit de externe database voordat u de resultaten opnieuw importeert in Adobe Campaign.

* Verzamel de gegevens in de externe Adobe Campaign-database en voer de bewerkingen lokaal uit.

Als u personalisatie in uw leveringen wilt uitvoeren gebruikend gegevens van het externe gegevensbestand, verzamel de gegevens in een werkschema te gebruiken om het ter beschikking te stellen in een tijdelijke lijst. Dan gebruik de gegevens van de tijdelijke lijst om uw levering te personaliseren.

De optie FDA is afhankelijk van de beperkingen van het externe databasesysteem dat u gebruikt.
