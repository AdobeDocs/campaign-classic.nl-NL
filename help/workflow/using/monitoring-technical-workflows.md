---
product: campaign
title: Technische workflows controleren
description: Technische workflows controleren
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 5e77d196-5c71-438e-8dae-10c6a6e4f29c
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 5%

---

# Technische workflows controleren {#monitoring-technical-workflows}



De technische werkstromen moeten worden bewaakt en er moeten maatregelen worden genomen wanneer ze mislukken.

De extra manieren om de verschillende processen van de Campagne te controleren worden voorgesteld in [&#x200B; deze pagina &#x200B;](../../production/using/monitoring-guidelines.md).

## Instance Monitoring dashboard {#instance-monitoring-dashboard}

Het dashboard voor instance-controle is toegankelijk via het tabblad **[!UICONTROL Monitoring]** .

![](assets/monitoring_technical_workflows1.png)

Controleer onder Systeemindicatoren en kernbestanden of er geen rode indicatoren zijn. Als dit het geval is en sommige zijn, zou u moeten:

* Controleer of de vereiste processen altijd worden uitgevoerd.
* Controleer of geen van de processen te oud is.
* Controleer of de logbestanden van de verschillende processen geen alarmerende en terugkerende fouten bevatten.

## Technische workflows {#technical-workflows}

Technische workflows zijn beschikbaar via **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** .

Afhankelijk van de technische werkstroom, volg de hieronder beschreven stappen om ervoor te zorgen dat alles zoals verwacht werkt.

Om beter te begrijpen wat elk technisch werkschema zou moeten doen, verwijs naar dit [&#x200B; sectie &#x200B;](about-technical-workflows.md).

Voor **[!UICONTROL Database Cleanup workflow (‘cleanup’)]**:

1. Controleer of de **[!UICONTROL Database Cleanup]** -workflow elke dag wordt uitgevoerd en voltooid. Voor meer op dit, verwijs naar deze [&#x200B; pagina &#x200B;](../../production/using/database-cleanup-workflow.md).
1. Bekijk het dagboek om te verifiëren dat de verstreken tijd in tijd vrij constant is en zich niet in andere werkschema&#39;s mengt.

Voor **[!UICONTROL Tracking workflow (‘tracking’)]**:

Controleer of de workflow voor bijhouden volgens schema wordt uitgevoerd (standaard elk uur) en of het dagboek geen terugkerende fouten markeert. Raadpleeg deze [sectie](delivery.md) voor meer informatie.

Voor **[!UICONTROL Refresh for Deliverability (deliverabilityUpdate)]**:

1. Controleer of de **[!UICONTROL Refresh for Deliverability]** -workflow elke dag wordt uitgevoerd en voltooid.
1. Verifieer in het dagboek dat de regels regelmatig worden bijgewerkt.

Voor **[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. Kijk naar alle workflows onder de map **[!UICONTROL Campaign process]** . Raadpleeg [deze pagina](about-technical-workflows.md) voor meer informatie.
1. Controleer of de workflows worden uitgevoerd zoals gepland en of het dagboek geen terugkerende fouten markeert.

## Workflowcontrole {#workflow-supervision}

De **[!UICONTROL Workflow supervisors]** -groep moet operatoren bevatten die op de hoogte moeten worden gehouden van fouten en die tijdig actie kunnen ondernemen.

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

De controle van de planningswerkstroom verbetert zijn efficiency. Sommige taken moeten dagelijks plaatsvinden, terwijl andere taken wekelijks of maandelijks kunnen worden uitgevoerd.

Door workflows in mappen in te stellen die worden genoemd door terugkerende en gesorteerd op uitvoeringsschema, wordt de controle efficiënter.

De automatisering van controle vermindert middelenoverheadkosten en zorgt ervoor dat de taken bij de aangewezen frequentie worden gepland.

U kunt een controlewerkstroom bouwen om een e-mail te verzenden wanneer bepaalde taken ontbreken of wanneer een kritieke lijst te groot wordt.

U kunt een weergave maken zodat alle werkstromen in een functioneel gebied of in het hele systeem kunnen worden gecontroleerd.

U kunt ook de functie Adobe Campaign-taak of -rapport gebruiken om documentatie op aanvraag te maken. Deze functie is altijd up-to-date.
