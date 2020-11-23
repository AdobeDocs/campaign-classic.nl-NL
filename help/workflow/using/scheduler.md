---
solution: Campaign Classic
product: campaign
title: De activiteit Planner
description: Meer informatie over de workflowactiviteit van de planner
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 10%

---


# Planner {#scheduler}

De **Planner** is een blijvende taak die zijn overgang op de tijden activeert die door zijn programma worden gespecificeerd.

De **[!UICONTROL Scheduler]**-activiteit kan dus worden beschouwd als een geplande start. De regels voor het positioneren van de activiteit in het diagram zijn hetzelfde als voor de **[!UICONTROL Start]**-activiteit. Deze activiteit mag geen binnenkomende overgang hebben.

## Aanbevolen procedures {#best-practices}

* Plan geen workflow die meer dan om de 15 minuten wordt uitgevoerd, aangezien dit de algehele systeemprestaties kan belemmeren en blokken in de database kan maken.

* Gebruik nooit meer dan één **[!UICONTROL Scheduler]** activiteit per tak in een werkschema. Zie [Activiteiten](../../workflow/using/workflow-best-practices.md#using-activities)gebruiken.

* Het gebruiken van een planneractiviteit kan tot verscheidene uitvoeringen van een werkschema leiden die tezelfdertijd lopen. Bijvoorbeeld, kunt u een planner hebben die de werkschemauitvoering elk uur teweegbrengt, maar soms neemt de uitvoering van het volledige werkschema meer dan een uur.

   U kunt de uitvoering overslaan als de workflow al wordt uitgevoerd. Raadpleeg [deze pagina](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)voor meer informatie over het voorkomen van gelijktijdige uitvoering van een workflow.

* Merk op dat de overgang verscheidene uren later kan worden geactiveerd als het werkschema een taak op lange termijn, zoals het invoeren uitvoerde, of als de wfserver module voor een tijd werd tegengehouden. In dit geval, kan het noodzakelijk zijn om de uitvoering van de taak te beperken die door de planner tot een bepaalde tijdwaaier wordt geactiveerd.

## De planneractiviteit configureren {#configuring-scheduler-activity}

De planner bepaalt het activeringsprogramma van de overgang. Om het te vormen, klik het grafische voorwerp tweemaal, dan klik **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

Met een wizard kunt u de frequentie en de geldigheidsperiode van de activiteit definiëren. De configuratiestappen zijn als volgt:

1. Selecteer de activeringsfrequentie en klik op **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. Geef de activeringstijden en -dagen op. De parameters voor deze stap zijn afhankelijk van de frequentie die u in de vorige stap hebt geselecteerd. Als u ervoor kiest om de activiteit meerdere keren per dag te lanceren, zullen de configuratieopties als volgt zijn:

   ![](assets/s_user_segmentation_scheduler3.png)

1. Bepaal de geldigheidsperiode van het programma of specificeer hoe vaak het zal worden uitgevoerd.

   ![](assets/s_user_segmentation_scheduler4.png)

1. Controleer de configuratie en klik **[!UICONTROL Finish]** om op te slaan.

   ![](assets/s_user_segmentation_scheduler5.png)
