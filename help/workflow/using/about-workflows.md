---
title: Workflows
description: Automatiseer processen met workflows, beheer gegevens en publiek, verzend berichten, en meer.
page-status-flag: never-activated
uuid: 19adb0e5-042d-47a0-9f92-24e4b3045dbe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: introduction
discoiquuid: 868940d1-f19d-4e9a-bffa-8654abb4441c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eccf0e9899426c2517748c7a72611ff098291cd2
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 16%

---


# Aan de slag met workflows{#about-workflows}

## Workflows

Adobe Campaign bevat een workflowmodule waarmee u het volledige scala aan processen en taken in de verschillende modules van de toepassingsserver kunt ordenen. Met deze uitgebreide grafische omgeving kunt u processen ontwerpen, zoals segmentatie, uitvoering van campagnes, bestandsverwerking, menselijke participatie, enzovoort. Deze processen worden uitgevoerd en bijgehouden door de workflowengine.

U kunt bijvoorbeeld een workflow gebruiken om een bestand van een server te downloaden, het te decomprimeren en vervolgens records in de Adobe Campaign-database te importeren.

Een workflow kan ook een of meer operatoren omvatten die op de hoogte moeten worden gebracht of die keuzes kunnen maken en processen kunnen goedkeuren. Op deze manier is het mogelijk om een leveringsactie te maken, een taak toe te wijzen aan een of meer operatoren om aan content te werken, doelen op te geven en proeven goed te keuren voordat de levering wordt gestart.

Workflows vinden plaats in verschillende contexten en fasen van het campagnebeheerproces.

Adobe Campaign gebruikt workflows om:

* Voer gerichte campagnes uit. For more on this, refer to [Implementation steps](../../workflow/using/building-a-workflow.md#implementation-steps-).
* Campagnes opbouwen: voor elke campagne, laat het **[!UICONTROL Workflow]** lusje u het doel bouwen en de leveringen tot stand brengen. For more on this, refer to [Campaign workflows](../../workflow/using/building-a-workflow.md#campaign-workflows).
* Technische processen uitvoeren: opschonen, trackinggegevens verzamelen of voorlopige berekeningen maken. For more on this, refer to [Technical workflows](../../workflow/using/building-a-workflow.md#technical-workflows).

Een werkstroom kan zowel een procesdefinitie (het werkschemamodel, dat een vertegenwoordiging van is wat verondersteld om is te gebeuren) als een geval van dit proces (een werkschemainstantie, die een vertegenwoordiging van is wat eigenlijk gebeurt) betekenen.

In het werkstroomsjabloon worden de verschillende taken beschreven die moeten worden uitgevoerd en wordt beschreven hoe deze aan elkaar zijn gekoppeld. De taakmalplaatjes worden genoemd activiteiten en door pictogrammen vertegenwoordigd. Ze zijn aan elkaar gekoppeld door overgangen.

![](assets/example1.png)

Elke werkstroom bevat:

* **[!UICONTROL Activities]**

   Een activiteit beschrijft een taakmalplaatje. De verschillende beschikbare activiteiten worden op het diagram weergegeven door pictogrammen. Elk type heeft gemeenschappelijke eigenschappen en specifieke eigenschappen. Terwijl alle activiteiten bijvoorbeeld een naam en label hebben, heeft alleen de **[!UICONTROL Approval]** activiteit een toewijzing.

   In een workflowdiagram kan een bepaalde activiteit meerdere taken produceren, met name wanneer er een lus of terugkerende (periodieke) handelingen zijn.

   Alle workflowactiviteiten worden vermeld in [deze sectie](../../workflow/using/about-activities.md), inclusief gebruiksgevallen en voorbeelden.

* **[!UICONTROL Transitions]**

   Met overgangen kunt u activiteiten koppelen en de volgorde ervan definiëren. Een overgang koppelt een bronactiviteit aan een bestemmingsactiviteit. Er zijn diverse soorten overgangen, die van de bronactiviteit afhangen. Sommige overgangen hebben extra parameters zoals een duur, een voorwaarde of een filter.

   Een overgang die niet is gekoppeld aan een doelactiviteit, wordt oranje gekleurd en de pijlkop wordt weergegeven als een ruit.

   >[!NOTE]
   >
   >Een workflow met niet-afgesloten overgangen kan nog steeds worden uitgevoerd: er wordt een waarschuwingsbericht gegenereerd en de workflow wordt gepauzeerd zodra de overgang is bereikt , maar er wordt geen fout gegenereerd . Het is dus mogelijk om een werkstroom te starten zonder dat deze is voltooid en om deze tijdens het proces toe te voegen.

   Raadpleeg [deze sectie](../../workflow/using/building-a-workflow.md)voor meer informatie over het maken van een workflow.

* **[!UICONTROL Worktables]**

   De werktabel bevat alle informatie die door de overgang wordt overgedragen. Voor elke workflow worden meerdere werktabellen gebruikt. De gegevens in deze tabellen kunnen gedurende de gehele levenscyclus van de werkstroom worden versneld en gebruikt, zolang deze niet worden gewist. Onbenodigde tabellen worden immers gewist wanneer de workflow wordt gepassiveerd en mogelijk tijdens de uitvoering van de grootste workflows om overbelasting van de server te voorkomen.

   Meer informatie over workflowgegevens en tabellen vindt u in [deze sectie](../../workflow/using/how-to-use-workflow-data.md).

## Belangrijkste beginselen en beste praktijken

Raadpleeg de volgende secties voor hulp en tips en trucs om processen te automatiseren met workflows:

* Meer informatie over workflowactiviteiten vindt u op [deze pagina](../../workflow/using/how-to-use-workflow-data.md).
* Leer hoe u een workflow maakt in [deze sectie](../../workflow/using/building-a-workflow.md).
* Ontdek in [deze sectie](../../workflow/using/importing-data.md)hoe u workflows kunt gebruiken om gegevens te importeren in Campagne.
* Best practices voor workflows worden in [deze pagina](../../workflow/using/workflow-best-practices.md)beschreven.
* Raadpleeg de instructies over het uitvoeren van workflows in [deze sectie](../../workflow/using/starting-a-workflow.md).
* Leer hoe u workflows in [deze pagina](../../workflow/using/monitoring-workflow-execution)kunt controleren.
* Leer hoe u gebruikers toegang biedt om workflows te gebruiken op [deze pagina](../../workflow/using/managing-rights.md).
