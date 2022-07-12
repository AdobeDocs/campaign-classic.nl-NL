---
product: campaign
title: Technische workflows controleren
description: Technische workflows controleren
feature: Workflows
exl-id: 5e77d196-5c71-438e-8dae-10c6a6e4f29c
source-git-commit: 25e8acdc449c7002e467db17e7c70e3dc017dded
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 5%

---

# Technische workflows controleren {#monitoring-technical-workflows}

![](../../assets/common.svg)

De technische werkstromen moeten worden bewaakt en er moeten maatregelen worden genomen wanneer ze mislukken.

Aanvullende manieren om de verschillende campagneprocessen te bewaken worden weergegeven in [deze pagina](../../production/using/monitoring-guidelines.md).

## Instance Monitoring dashboard {#instance-monitoring-dashboard}

Het dashboard voor instance-controle is toegankelijk via de **[!UICONTROL Monitoring]** tab.

![](assets/monitoring_technical_workflows1.png)

Controleer onder Systeemindicatoren en kernbestanden of er geen rode indicatoren zijn. Als dit het geval is en sommige zijn, zou u moeten:

* Controleer of de vereiste processen altijd worden uitgevoerd.
* Controleer of geen van de processen te oud is.
* Controleer of de logbestanden van de verschillende processen geen alarmerende en terugkerende fouten bevatten.

## Technische workflows {#technical-workflows}

Technische workflows zijn beschikbaar via **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

Afhankelijk van de technische werkstroom, volg de hieronder beschreven stappen om ervoor te zorgen dat alles zoals verwacht werkt.

Om beter te begrijpen wat elke technische werkstroom wordt verondersteld te doen, verwijs naar dit [sectie](about-technical-workflows.md).

Voor **[!UICONTROL Database Cleanup workflow (‘cleanup’)]**:

1. Controleer of de **[!UICONTROL Database Cleanup]** de workflow wordt elke dag uitgevoerd en voltooid. Raadpleeg de volgende secties voor meer informatie [page](../../production/using/database-cleanup-workflow.md)..
1. Bekijk het dagboek om te verifiëren dat de verstreken tijd in tijd vrij constant is en zich niet in andere werkschema&#39;s mengt.

Voor **[!UICONTROL Tracking workflow (‘tracking’)]**:

Controleer of de workflow voor bijhouden volgens schema wordt uitgevoerd (standaard elk uur) en of het dagboek geen terugkerende fouten markeert. Raadpleeg deze [sectie](delivery.md) voor meer informatie.

Voor **[!UICONTROL Refresh for Deliverability (deliverabilityUpdate)]**:

1. Controleer of de **[!UICONTROL Refresh for Deliverability]** de workflow wordt elke dag uitgevoerd en voltooid.
1. Verifieer in het dagboek dat de regels regelmatig worden bijgewerkt.

Voor **[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. Bekijk alle workflows onder de **[!UICONTROL Campaign process]** map. Raadpleeg [deze pagina](about-technical-workflows.md) voor meer informatie.
1. Controleer of de workflows worden uitgevoerd zoals gepland en of het dagboek geen terugkerende fouten markeert.

## Workflowcontrole {#workflow-supervision}

De **[!UICONTROL Workflow supervisors]** de groep moet exploitanten omvatten die op de hoogte moeten worden gehouden van tekortkomingen en die tijdig kunnen optreden.

![](assets/monitoring_technical_workflows3.png)

In geval van een probleem moet een waarschuwing worden gegenereerd en naar de juiste groep worden verzonden.

Controleer of elke operator een geldig e-mailadres heeft.

Elke workflow die moet worden uitgevoerd om het platform draaiende te houden, zoals dagelijkse gegevensimporten, moet worden aangegeven als &quot;Productie&quot; (selectievakje) en moet vet worden weergegeven.

## Werkstroomonderhoudslijst {#workflow-maintenance-list}

Alle aangepaste technische workflows moeten worden gedocumenteerd in een werkblad dat het volgende bevat:

* Naam en locatie van de workflow.
* Doel.
* Planning en afhankelijkheden.
* Exploitant die belast is met de bewaking.
* Instructies over wat te doen in het geval van fout.

![](assets/monitoring_technical_workflows4.png)

## Planning en automatisering van de controle {#planning-and-automation-of-monitoring}

Controle van de planningsworkflow verbetert de efficiëntie. Sommige taken moeten dagelijks plaatsvinden, terwijl andere taken wekelijks of maandelijks kunnen worden uitgevoerd.

Door workflows in mappen in te stellen die worden genoemd door terugkerende en gesorteerd op uitvoeringsschema, wordt de controle efficiënter.

De automatisering van controle vermindert middelenoverheadkosten en zorgt ervoor dat de taken bij de aangewezen frequentie worden gepland.

U kunt een controlewerkstroom bouwen om een e-mail te verzenden wanneer bepaalde taken ontbreken of wanneer een kritieke lijst te groot wordt.

U kunt een weergave maken zodat alle werkstromen in een functioneel gebied of in het hele systeem kunnen worden gecontroleerd.

U kunt ook de functie Adobe Campaign-taak of -rapport gebruiken om documentatie op aanvraag te maken. Dit is altijd up-to-date.
