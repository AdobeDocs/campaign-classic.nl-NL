---
product: campaign
title: HeatMap van de Campagne Workflow
description: Uw workflows controleren met Workflow HeatMap
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: f1016ddf-0c87-4611-a878-d01f3684935f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 3%

---

# Workflowheatmap {#workflow-heatmap}

![](../../assets/common.svg)

De werkstroom HeatMap van de campagne bestaat uit een kleur-gecodeerde grafische vertegenwoordiging van alle werkschema&#39;s die momenteel lopen. Het is alleen beschikbaar voor **Campagnebeheerders**.

Ontdek extra manieren om de processen van de Campagne in te controleren [deze pagina](../../production/using/monitoring-guidelines.md).

## Aan de slag met de workflow HeatMap {#about-the-workflow-heatmap}

Door een snel overzicht te geven van het aantal gelijktijdige workflows, stelt de Workflow HeatMap de beheerders van het Adobe Campaign-platform in staat de belasting op de instantie te controleren en de workflows dienovereenkomstig te plannen.

Meer bepaald, helpt het de platformbeheerders om:

* Gelijktijdige workflows bekijken en begrijpen
* Workflows filteren op duur om te zien in welke workflows problemen kunnen optreden
* Filteren van activiteiten op duur om te zien welke activiteiten problemen kunnen tegenkomen
* Gemakkelijk individuele workflows en alle verwante activiteiten (met hun duur) vinden
* Filteren op workflowtype: [technische werkstromen](building-a-workflow.md#technical-workflows) of [campagneworkflows](building-a-workflow.md#campaign-workflows)
* Zoeken naar een specifieke workflow die moet worden geanalyseerd

>[!NOTE]
>
>Naast de **Workflow Heatmap** kunt u een workflow maken waarmee u de status van een set workflows kunt controleren en terugkerende berichten kunt verzenden aan toezichthouders. Raadpleeg voor meer informatie de [speciale sectie](supervising-workflows.md).

Het gebruiken van het Werkschema HeatMap vereist om een goed inzicht in de volgende concepten te hebben: [Workflows](about-workflows.md), [Activiteiten](about-activities.md) en [Best practices voor workflow](workflow-best-practices.md).

## De workflow HeatMap aanpassen {#using-the-heatmap}

>[!NOTE]
>
>Als er geen gegevens worden weergegeven in de Workflow HeatMap, klikt u op de knop **[!UICONTROL Load data]** knop.

1. Ga naar **[!UICONTROL Monitoring]** en klik op de knop **[!UICONTROL Workflow HeatMap]** koppeling om de **[!UICONTROL Campaign Workflow HeatMap]** pagina.

   ![](assets/wkf_monitoring_path.png)

1. Klik op de kalender om een dag te selecteren.

   Standaard geeft de pagina de werkstroomactiviteit voor de huidige dag weer. U kunt deze wijzigen en elke dag uit het verleden selecteren.

   >[!NOTE]
   >
   >Alleen de workflows die niet zijn verwijderd door de **[!UICONTROL Database cleanup]** de workflow is zichtbaar. Raadpleeg voor meer informatie over de workflow voor het opschonen van databases [deze sectie](../../production/using/database-cleanup-workflow.md).\
   >Door gebrek, is de de tijdzone van de Werkstroom HeatMap die voor de huidige beheerdergebruiker wordt bepaald. U kunt deze bijvoorbeeld wijzigen als u zich niet in hetzelfde gebied bevindt als de marketinggebruikers waarmee u werkt.

1. Klik op de knop **[!UICONTROL Filters]**.

   ![](assets/wkf_monitoring_filters.png)

1. Gebruik de schuifregelaar om de minimale duur in te stellen van 0 seconden tot 1 uur. Hierdoor kunt u alleen werkstromen doorzoeken die langer dan een bepaald aantal seconden of minuten duren.

   ![](assets/wkf_monitoring_filters_duration.png)

1. U kunt ook een specifieke workflow kiezen in het menu **[!UICONTROL Workflows]** vervolgkeuzelijst.

   ![](assets/wkf_monitoring_filters_workflows.png)

   >[!NOTE]
   >
   >De **[!UICONTROL Min duration]** wordt toegepast. Als u geen specifieke workflow kunt vinden, stelt u de minimale duur in op 0, zodat alle workflows in de lijst worden weergegeven.

1. U kunt ook filteren op het tabblad **[!UICONTROL Workflow type]** :

   * **[!UICONTROL Technical]** : Alleen [out-of-the-box-technische workflows](building-a-workflow.md#technical-workflows) en [workflows voor gegevensbeheer](targeting-data.md#data-management) worden weergegeven.
   * **[!UICONTROL Marketing]** : Alleen workflows die zijn gekoppeld aan een marketingcampagne, beter bekend als [campagneworkflows](building-a-workflow.md#campaign-workflows), worden weergegeven.

1. Als u een specifieke workflow op naam wilt doorzoeken, kunt u ook de opdracht **[!UICONTROL Workflow name filter]** veld.

1. Als u enkele workflows hebt bewerkt in de tussenliggende tijd, klikt u op de knop **[!UICONTROL Reload data]** om de gegevens die in het raster worden weergegeven te vernieuwen.

## Interpreteer de Workflow HeatMap {#reading-the-heatmap}

De Campagne Workflow HeatMap is een raster dat van linksboven naar rechtsonder kan worden gelezen, zodat de &#39;hot zones&#39; kunnen worden gevonden met een groen tot rood kleurgecodeerd bereik.

* De donkerdere rode cellen komen overeen met de periodes waarin een groot aantal workflows tegelijkertijd wordt uitgevoerd.
* De grijze cellen komen overeen met periodes waarin geen workflow wordt uitgevoerd.

Als u wilt weten hoe de kleurcode wordt toegepast en hoe u door de HeatMap kunt navigeren, klikt u op de knop **[!UICONTROL Help]** knop.

![](assets/wkf_monitoring_legend.png)

Elke rij vertegenwoordigt een uur van de dag en elke cel vertegenwoordigt 5 minuten van dat uur.

In het raster worden alle workflows weergegeven die tegelijkertijd worden uitgevoerd voor elk van deze periodes van 5 minuten.

In het onderstaande voorbeeld worden tussen 8.00 uur en 8.05 uur drie workflows uitgevoerd (ongeacht de individuele duur):

![](assets/wkf_monitoring_ex_8am.png)

1. Klik op een gekleurde cel om de details weer te geven van alle gelijktijdige workflows die tijdens deze periode worden uitgevoerd.

   ![](assets/wkf_monitoring_details.png)

   Voor elke werkstroom worden alle activiteiten in de werkstroom vermeld, met hun duur.

1. Klik op de werkstroom-id of naam om een werkstroom rechtstreeks te openen.
1. Ga terug naar de **[!UICONTROL Campaign Workflow HeatMap]** klik op de knop **[!UICONTROL Home]** knop.

## Gebruik hoofdletters/kleine letters: HeatMap gebruiken om handelingen uit te voeren {#use-cases--using-the-heatmap-to-take-actions}

Er zijn twee belangrijke gevallen waar het de werkschema HeatMap van de Campagne nuttig kan zijn.

### Het aantal gelijktijdige workflows verminderen {#reducing-the-number-of-concurrent-workflows}

Als beheerder van de Campagne, kan het Werkschema HeatMap u helpen om de lading op de instantie te begrijpen en bestaande of nieuwe werkschema&#39;s op aangewezen tijden te plannen.

1. Van de **[!UICONTROL Campaign Workflow HeatMap]** klik op de knop **[!UICONTROL Filters]** knop.
1. Stel de duur in op een paar seconden of een paar minuten.
1. Sluit de kortste werkstromen uit die niet significant zijn door het duurfilter te verhogen.

   ![](assets/wkf_monitoring_short_duration.png)

1. Onderzoek de resultaten om de lading op de instantie te begrijpen en neem aangewezen acties:

   * Als er prestatieproblemen optreden en er een of meer rode cellen in het raster worden weergegeven, kunt u de begintijd van verschillende workflows wijzigen. Vraag de marketinggebruikers om de werkstromen handmatig van bezige (&quot;hot&quot;) perioden naar meer beschikbare tijdsleuven te verplaatsen. Dit moet de dag een stabiel niveau van activiteit handhaven.
   * Om pieken te vermijden en de instantie te verhinderen overbelasting, bekijk HeatMap alvorens nieuwe werkschema&#39;s te plannen en de beste tijd te kiezen. Overweeg tijdsleuven die overeenkomen met grijze of groene cellen in het raster om nieuwe workflows te starten.

### Langlopende workflows zoeken die van invloed zijn op prestaties {#finding-long-running-workflows-that-impact-performance}

Als Campagnebeheerder, helpt het Werkschema HeatMap u om de langste werkschema&#39;s te vinden die de activiteit kunnen vertragen.

1. Van de **[!UICONTROL Campaign Workflow HeatMap]** klik op de knop **[!UICONTROL Filters]** knop.
1. Stel de duur in op 1 uur.

   ![](assets/wkf_monitoring_long_duration.png)

1. Neem meer resultaten op door de **[!UICONTROL Min duration]** filter.
1. Onderzoek de resultaten om de langste werkschema&#39;s te vinden, die potentieel meer invloed op de server en gegevensbestandmiddelen (cpu, RAM, netwerk, IOPS, etc.) kunnen hebben.
1. Voer passende maatregelen uit:

   * Adviseer marketinggebruikers om de langste workflows te splitsen om de verwerkingstijd te verminderen.
   * Start een diepgaande analyse van specifieke workflows en specifieke activiteiten (zoals JavaScript, importeren, exporteren, enzovoort) om de problemen te isoleren en eenvoudiger op te lossen.

## Met HeatMap kunt u de planning van de workflow verbeteren {#example--using-the-heatmap-to-improve-workflow-planning}

In het onderstaande voorbeeld ziet u hoe planning efficiënter kan zijn en hoe de prestaties kunnen worden verbeterd bij gebruik van de Adobe Campaign Workflow HeatMap.

In dit geval klagen veel gebruikers over workflowprestaties. U moet controleren wat de activiteit vertraagt en hoe te om het probleem op te lossen.

1. Ga naar **[!UICONTROL Monitoring]** en klik op de knop **[!UICONTROL Workflows]** koppeling om de **[!UICONTROL Campaign Workflow HeatMap]** pagina.
1. Stel de **[!UICONTROL Min duration]** filteren tot 5 minuten.
1. Stel de **[!UICONTROL Workflow type]** filteren naar **[!UICONTROL Marketing]** .
1. Neem het volgende in acht vanaf het HeatMap-raster:

   ![](assets/wkf_monitoring_without.png)

   * De vijftig langdurige (meer dan 5 minuten) campagneworkflows worden uitgevoerd om 10.00 uur.
   * De meesten van hen hebben een hangende staat (door gebrek, wordt de gelijktijdig grens geplaatst aan 20).
   * De werkstromen in behandeling moeten elke dag handmatig opnieuw worden gestart.
   * De prestaties zijn laag.

1. In plaats van vijftig workflows te hebben die om 10.00 uur beginnen, verdeel de werkstromen&#39; beginnende tijden gelijkelijk over de rest van de dag.
1. Ga terug naar de **[!UICONTROL Campaign Workflow HeatMap]** en klik op de knop **[!UICONTROL Reload data]** knop.
1. Neem nu het volgende in acht:

   ![](assets/wkf_monitoring_with.png)

   * Slechts achttien langdurige campagneworkflows worden nog steeds om 10.00 uur uitgevoerd.
   * Er zijn geen workflows meer in behandeling (de limiet voor gelijktijdige uitvoering is nog steeds ingesteld op 20).
   * De werkstroombegintijden worden gelijkmatig over de dag verdeeld.
   * Geen gebruikers klagen meer over prestatieproblemen.
