---
title: Workflows
seo-title: Workflows
description: Workflows
seo-description: null
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
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Workflows{#about-workflows}

Adobe Campagne omvat een werkschemamodule die u machtigt om de volledige waaier van processen en taken over de verschillende modules van de toepassingsserver te ordenen. Met deze uitgebreide grafische omgeving kunt u processen ontwerpen, zoals segmentatie, uitvoering van campagnes, bestandsverwerking, menselijke participatie, enz. Deze processen worden uitgevoerd en bijgehouden door de workflowengine.

U kunt bijvoorbeeld een workflow gebruiken om een bestand van een server te downloaden, het te decomprimeren en vervolgens records in de Adobe Campagne-database te importeren.

Een workflow kan ook een of meer operatoren omvatten die op de hoogte moeten worden gebracht of die keuzes kunnen maken en processen kunnen goedkeuren. Op deze manier is het mogelijk om een leveringsactie te maken, een taak toe te wijzen aan een of meer operatoren om aan inhoud te werken, doelen op te geven en proefdrukken goed te keuren voordat de levering wordt gestart.

Workflows vinden plaats in verschillende contexten en fasen van het campagnebeheerproces.

Adobe Campagne gebruikt workflows om:

* Voer gerichte campagnes uit. Raadpleeg de stappen [voor](../../workflow/using/building-a-workflow.md#implementation-steps-)implementatie voor meer informatie.
* Campagnes opbouwen: voor elke campagne, laat het **[!UICONTROL Workflow]** lusje u het doel bouwen en de leveringen tot stand brengen. Raadpleeg de [campagneworkflows](../../workflow/using/building-a-workflow.md#campaign-workflows)voor meer informatie.
* Technische processen uitvoeren: opschonen, trackinggegevens verzamelen of voorlopige berekeningen maken. Raadpleeg de [technische workflows](../../workflow/using/building-a-workflow.md#technical-workflows)voor meer informatie.

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

