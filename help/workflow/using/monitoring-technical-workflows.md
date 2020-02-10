---
title: Technische workflows controleren
seo-title: Technische workflows controleren
description: Technische workflows controleren
seo-description: null
page-status-flag: never-activated
uuid: 4d215ff4-a61d-4294-8f15-17c612022577
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 6a71f5ee-c8e0-4ac4-acae-6dffbf799d0c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d60f47f03949177b97509166a8d9e640849e5fd7

---


# Technische workflows controleren {#monitoring-technical-workflows}

De technische werkstromen moeten worden bewaakt en er moeten maatregelen worden genomen wanneer ze mislukken.

In [deze pagina](https://helpx.adobe.com/campaign/kb/acc-maintenance.html)worden extra manieren weergegeven om de verschillende campagneprocessen te controleren.

## Instance Monitoring dashboard {#instance-monitoring-dashboard}

Het dashboard voor instance-controle is toegankelijk via het **[!UICONTROL Monitoring]** universum.

![](assets/monitoring_technical_workflows1.png)

Controleer onder Systeemindicatoren en kernbestanden of er geen rode indicatoren zijn. Als dit het geval is en sommige zijn, zou u moeten:

* Controleer of de vereiste processen altijd worden uitgevoerd.
* Controleer of geen van de processen te oud is.
* Controleer of de logbestanden van de verschillende processen geen alarmerende en terugkerende fouten bevatten.

## Technische workflows {#technical-workflows}

Technische workflows zijn beschikbaar via **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

Afhankelijk van de technische werkstroom, volg de hieronder beschreven stappen om ervoor te zorgen dat alles zoals verwacht werkt.

Raadpleeg deze [sectie](../../workflow/using/about-technical-workflows.md)voor een beter begrip van wat elke technische workflow moet doen.

Voor **[!UICONTROL Database Cleanup workflow (‘cleanup’)]**:

1. Controleer of de **[!UICONTROL Database Cleanup]** workflow elke dag wordt uitgevoerd en voltooid. Raadpleeg deze [pagina](../../workflow/using/delivery.md)voor meer informatie.
1. Bekijk het dagboek om te verifiëren dat de verstreken tijd in tijd vrij constant is en zich niet in andere werkschema&#39;s mengt.
1. Raadpleeg deze [pagina](../../production/using/database-cleanup-workflow.md)voor meer informatie.

Voor **[!UICONTROL Tracking workflow (‘tracking’)]**:

Controleer of de workflow voor bijhouden volgens schema wordt uitgevoerd (standaard elk uur) en of het dagboek geen terugkerende fouten markeert. Zie deze [sectie](../../workflow/using/delivery.md)voor meer informatie.

Voor **[!UICONTROL Deliverability update (‘deliverabilityUpdate’)]**:

1. Controleer of de **[!UICONTROL Deliverability update]** workflow elke dag wordt uitgevoerd en voltooid. Raadpleeg deze [pagina](../../workflow/using/delivery.md)voor meer informatie.
1. Verifieer in het dagboek dat de regels regelmatig worden bijgewerkt.

Voor **[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. Bekijk alle workflows die zich onder de **[!UICONTROL Campaign process]** map bevinden. Raadpleeg deze [pagina](../../workflow/using/campaign.md)voor meer informatie.
1. Controleer of de workflows worden uitgevoerd zoals gepland en of het dagboek geen terugkerende fouten markeert.

## Workflowcontrole {#workflow-supervision}

De **[!UICONTROL Workflow supervisors]** groep moet operatoren bevatten die op de hoogte moeten worden gehouden van tekortkomingen en die tijdig actie kunnen ondernemen.

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

U kunt een controlewerkschema bouwen om een e-mail te verzenden wanneer bepaalde taken ontbreken of wanneer een kritieke lijst te groot wordt.

U kunt een weergave maken zodat alle werkstromen in een functioneel gebied of in het hele systeem kunnen worden gecontroleerd.

U kunt ook de functie Adobe Campagne of de rapportfunctionaliteit gebruiken om documentatie op verzoek samen te stellen, die altijd up-to-date is.
