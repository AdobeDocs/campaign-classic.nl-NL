---
product: campaign
title: Workflows
description: Automatiseer processen met workflows, beheer gegevens en doelgroepen, verzend berichten, en meer
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: 51be6b90-2a7a-4757-9754-d16c540a87ff
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 25%

---

# Aan de slag met workflows{#gs-workflows}



## Workflows{#about-workflows}

Adobe Campaign bevat een workflowmodule om het volledige scala aan processen en taken in de verschillende modules van de applicatieserver te organiseren. Met deze uitgebreide grafische omgeving kunt u processen ontwerpen, zoals segmentatie, uitvoering van campagnes, bestandsverwerking, menselijke participatie, enzovoort. Deze processen worden uitgevoerd en bijgehouden door de workflowengine.

U kunt bijvoorbeeld een workflow gebruiken om een bestand van een server te downloaden, het te decomprimeren en vervolgens records in de Adobe Campaign-database te importeren.

Een workflow kan ook een of meer operatoren omvatten die op de hoogte moeten worden gebracht of die keuzes kunnen maken en processen kunnen goedkeuren. Op deze manier is het mogelijk om een leveringsactie te maken, een taak toe te wijzen aan een of meer operatoren om aan content te werken, doelen op te geven en proeven goed te keuren voordat de levering wordt gestart.

Workflows vinden plaats in verschillende contexten en fasen van het campagnemanagementproces.

Adobe Campaign gebruikt workflows om:

* Voer gerichte campagnes uit. [Meer informatie](building-a-workflow.md#implementation-steps-)
* Campagnes opbouwen: voor elke campagne kunt u met het tabblad **[!UICONTROL Workflow]** het doel opbouwen en de leveringen maken. [Meer informatie](building-a-workflow.md#campaign-workflows)
* Technische processen uitvoeren: opschonen, trackinggegevens verzamelen of voorlopige berekeningen uitvoeren. [Meer informatie](building-a-workflow.md#technical-workflows)

Een werkstroom kan zowel een procesdefinitie (het werkschemamodel, dat een vertegenwoordiging van is wat verondersteld om is te gebeuren) als een geval van dit proces (een werkschemainstantie, die een vertegenwoordiging van is wat eigenlijk gebeurt) betekenen.

In het werkstroomsjabloon worden de verschillende taken beschreven die moeten worden uitgevoerd en wordt beschreven hoe deze aan elkaar zijn gekoppeld. De taakmalplaatjes worden genoemd activiteiten en door pictogrammen vertegenwoordigd. Ze zijn aan elkaar gekoppeld door overgangen.

![](assets/example1.png)

Elke werkstroom bevat:

* **[!UICONTROL Activities]**

  Een activiteit beschrijft een taakmalplaatje. De verschillende beschikbare activiteiten worden op het diagram weergegeven door pictogrammen. Elk type heeft gemeenschappelijke eigenschappen en specifieke eigenschappen. Terwijl alle activiteiten bijvoorbeeld een naam en label hebben, heeft alleen de **[!UICONTROL Approval]** -activiteit een toewijzing.

  In een workflowdiagram kan een bepaalde activiteit meerdere taken produceren, met name wanneer er een lus of terugkerende (periodieke) handelingen zijn.

  Alle werkschemaactiviteiten worden vermeld in [ deze sectie ](about-activities.md), met inbegrip van gebruiksgevallen en steekproeven.

* **[!UICONTROL Transitions]**

  Met overgangen kunt u activiteiten koppelen en de volgorde ervan definiëren. Een overgang koppelt een bronactiviteit aan een bestemmingsactiviteit. Er zijn diverse soorten overgangen, die van de bronactiviteit afhangen. Sommige overgangen hebben extra parameters zoals een duur, een voorwaarde of een filter.

  Een overgang die niet is gekoppeld aan een doelactiviteit, wordt oranje gekleurd en de pijlkop wordt weergegeven als een ruit.

  >[!NOTE]
  >
  >Er kan nog steeds een workflow met niet-afgesloten overgangen worden uitgevoerd: er wordt een waarschuwingsbericht gegenereerd en de workflow wordt gepauzeerd zodra de overgang is bereikt, maar er wordt geen fout gegenereerd. Het is dus mogelijk om een werkstroom te starten zonder dat deze is voltooid en om deze tijdens het proces toe te voegen.

  Voor meer informatie over hoe te om een werkschema te bouwen, verwijs naar [ deze sectie ](building-a-workflow.md).

* **[!UICONTROL Worktables]**

  De werktabel bevat alle informatie die door de overgang wordt overgedragen. Voor elke workflow worden meerdere werktabellen gebruikt. De gegevens in deze tabellen kunnen gedurende de gehele levenscyclus van de werkstroom worden versneld en gebruikt, zolang deze niet worden gewist. Onbenodigde tabellen worden immers gewist wanneer de workflow wordt gepassiveerd en mogelijk tijdens de uitvoering van de grootste workflows om overbelasting van de server te voorkomen.

  Leer meer over werkschemagegevens en lijsten in [ deze sectie ](how-to-use-workflow-data.md).

## Belangrijkste beginselen en beste praktijken{#principles-workflows}

Raadpleeg de volgende secties voor hulp en tips en trucs om processen te automatiseren met workflows:

* Leer meer over werkschemaactiviteiten in [ deze pagina ](how-to-use-workflow-data.md).
* Leer hoe te om een werkschema in [ te bouwen deze sectie ](building-a-workflow.md).
* Ontdek hoe te om werkschema&#39;s te gebruiken om gegevens in Campagne in [ in te voeren deze sectie ](../../platform/using/import-export-workflows.md).
* De beste praktijken van het werkschema zijn gedetailleerd in [ deze pagina ](workflow-best-practices.md).
* Vind begeleiding over werkschemauitvoering in [ deze sectie ](starting-a-workflow.md).
* Leer hoe te om werkschema&#39;s in [ te controleren deze pagina ](monitoring-workflow-execution.md).
* Leer hoe te om toegang tot gebruikers te verlenen om werkschema&#39;s in [ te gebruiken deze pagina ](managing-rights.md).
