---
solution: Campaign Classic
product: campaign
title: Tijdzones beheren
description: Tijdzones beheren
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 3%

---


# Tijdzones beheren{#managing-time-zones}

Met Adobe Campaign kunt u de tijd tussen verschillende landen beheren die bij hetzelfde geval betrokken zijn. De toegepaste configuratie wordt gevormd tijdens instantieverwezenlijking.

Raadpleeg deze [sectie](../../installation/using/time-zone-management.md) voor meer informatie over het configureren van tijdzones in Adobe Campaign.

In een werkschema, kunt u de programma&#39;s van de activiteitenuitvoering aanpassen en een specifieke tijdzone verbinden met een activiteit of met het volledige werkschema. Deze configuratie kan nuttig zijn wanneer het invoeren van het dossier, of binnen het kader van levering het plannen.

## Uitvoerings planning {#execution-scheduling}

U kunt de uitvoering van taken plannen gebruikend de planner (verwijs naar [Planner](../../workflow/using/scheduler.md)). U kunt ook de planningsopties gebruiken die beschikbaar zijn in de activiteiten die deze functionaliteit aanbieden. Deze activiteiten bieden een **[!UICONTROL Schedule]** tabel aan: **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**, enz.

Voor alle geplande taken, d.w.z. alle activiteiten met het plannen opties, kunt u de tijdzone selecteren om toe te passen. De tijdzone wordt geselecteerd via het tabblad **[!UICONTROL Advanced]** van de betreffende activiteit:

![](assets/wf-timezone-in-a-box.png)

Mogelijke waarden zijn:

* Tijdzone van server

   Gebruikt de tijdzone van de Adobe Campaign-toepassingsserver.

* Tijdzone gebruiker

   Gebruikt de tijdzone van de exploitant van Adobe Campaign die het werkschema uitvoert.

* Tijdzone database

   Gebruikt de tijdzone van de gebruikte gegevensbestandserver.

* Specifieke tijdzones

   Hiermee gebruikt u de geselecteerde tijdzone.

Als de waarde **[!UICONTROL By default]** wordt geselecteerd, wordt de tijdzone van het werkschema toegepast, of anders, die van de toepassingsserver.

## Een tijdzone koppelen aan een activiteit {#linking-a-time-zone-to-an-activity}

Op het tabblad **[!UICONTROL Advanced]** van de workflowactiviteiten kunt u de tijdzone selecteren. Hoewel de tijdzone van de workflows meestal voldoende is, kan het nodig zijn om deze nu en opnieuw te overladen voor een specifieke activiteit, zoals het importeren van gegevens, om datums te koppelen aan hun juiste tijdzone.
