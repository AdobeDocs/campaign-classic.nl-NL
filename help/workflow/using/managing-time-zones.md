---
title: Tijdzones beheren
seo-title: Tijdzones beheren
description: Tijdzones beheren
seo-description: null
page-status-flag: never-activated
uuid: a253861a-fc15-406d-969d-33cfb4169839
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 8bcbcd23-9251-412a-ae72-11f15db74112
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Tijdzones beheren{#managing-time-zones}

Met Adobe Campaign kunt u de tijd tussen verschillende landen beheren die bij hetzelfde exemplaar betrokken zijn. De toegepaste configuratie wordt gevormd tijdens instantieverwezenlijking.

Raadpleeg deze [sectie](../../installation/using/time-zone-management.md)voor meer informatie over het configureren van tijdzones in Adobe Campaign.

In een werkschema, kunt u de programma&#39;s van de activiteitenuitvoering aanpassen en een specifieke tijdzone verbinden met een activiteit of met het volledige werkschema. Deze configuratie kan nuttig zijn wanneer het invoeren van het dossier, of binnen het kader van levering het plannen.

## Uitvoerings planning {#execution-scheduling}

U kunt de uitvoering van taken plannen gebruikend de planner (verwijs naar [Planner](../../workflow/using/scheduler.md)). U kunt ook de planningsopties gebruiken die beschikbaar zijn in de activiteiten die deze functionaliteit aanbieden. Deze activiteiten bieden een **[!UICONTROL Schedule]** tabblad aan: **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**, enz.

Voor alle geplande taken, d.w.z. alle activiteiten met het plannen opties, kunt u de tijdzone selecteren om toe te passen. De tijdzone wordt geselecteerd via het **[!UICONTROL Advanced]** tabblad van de desbetreffende activiteit:

![](assets/wf-timezone-in-a-box.png)

Mogelijke waarden zijn:

* Tijdzone van server

   Gebruikt de tijdzone van de toepassingsserver van de Campagne van Adobe.

* Tijdzone gebruiker

   Gebruikt de tijdzone van de Adobe Campagneexploitant die het werkschema uitvoert.

* Tijdzone database

   Gebruikt de tijdzone van de gebruikte gegevensbestandserver.

* Specifieke tijdzones

   Hiermee gebruikt u de geselecteerde tijdzone.

Als de **[!UICONTROL By default]** waarde wordt geselecteerd, wordt de tijdzone van het werkschema toegepast, of anders, dat van de toepassingsserver.

## Een tijdzone koppelen aan een activiteit {#linking-a-time-zone-to-an-activity}

Op het **[!UICONTROL Advanced]** tabblad van de workflowactiviteiten kunt u de tijdzone selecteren. Hoewel de tijdzone van de workflows meestal voldoende is, kan het nodig zijn om deze nu en opnieuw te overladen voor een specifieke activiteit, zoals het importeren van gegevens, om datums te koppelen aan hun juiste tijdzone.
