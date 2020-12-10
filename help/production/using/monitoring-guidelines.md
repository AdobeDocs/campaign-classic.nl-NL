---
solution: Campaign Classic
product: campaign
title: Bewakingsrichtlijnen
description: Ontdek richtlijnen en beste praktijken om de instantie en processen van de Campagne te controleren.
audience: production
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 9aa0ecd423bfbf1082e9ce5bdb36aaf1611dea54
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 6%

---


# Bewakingsrichtlijnen {#monitoring-guidelines}

## Instance Monitoring dashboard {#instance-monitoring-dashboard}

Het tabblad **[!UICONTROL Monitoring]**, dat toegankelijk is vanaf de startpagina van Campaign Classic, is het belangrijkste ingangspunt waarmee u uw instantie kunt controleren.

Het verstrekt een dashboard van wat op uw geval voorkomt: de status (versie van de build, geïnstalleerde pakketten, enz.), systeemindicatoren, logboeken, workflows die momenteel worden uitgevoerd, de status van de laatst verzonden leveringen, enz.

Gedetailleerde informatie is [hier](../../production/using/monitoring-processes.md) beschikbaar.

![](assets/monitoring_tab.png)

## Bewaking van Campaign Classic-processen {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Uw instantie controleren</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">Workflows controleren</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Leveringen controleren</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">De database controleren</a></p></td></tr>
</table>

Er zijn aanvullende manieren beschikbaar om de verschillende campagneprocessen te controleren. Zij verstrekken verscheidene manieren om uw instanties te controleren om ervoor te zorgen dat uw systeem gezond is en uiteindelijk problemen problemen op te lossen die zich kunnen voordoen wanneer vestiging werkschema&#39;s, verzendende leveringen, enz.

### Uw instantie {#monitoring-instance} controleren

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Automatische bewakingsgereedschappen**

Er zijn verschillende automatische methoden beschikbaar. om u te helpen uw instantie controleren. U kunt bijvoorbeeld e-mailrapporten instellen met opgespoorde anomalieën, een lijst met indicatoren ophalen in XML-indeling, enzovoort. [Klik ](../../production/using/monitoring-processes.md#automatic-monitoring) hier voor meer informatie.

**Audittrail**

Met het audittrail kunt u de volledige geschiedenis van wijzigingen met betrekking tot opties, workflows en schema&#39;s binnen uw instantie visualiseren. [Klik ](../../production/using/audit-trail.md) hier voor meer informatie.

**Configuratiescherm**

In het Configuratiescherm kunt u verschillende instellingen van uw exemplaar beheren: beheer URL toestemmingen, controleer uw instantiedetails zoals de bouwstijlversies van uw servers, enz. Hiermee kunt u ook de beschikbare ruimte op de SFTP-servers controleren die met uw instantie zijn verbonden. [Klik ](https://docs.adobe.com/content/help/nl-NL/control-panel/using/control-panel-home.html) hier voor meer informatie.

>[!NOTE]
>
>Houd er rekening mee dat het Configuratiescherm alleen toegankelijk is voor gebruikers met beheerdersrechten en beschikbaar is voor alle klanten die Adobe Managed Services gebruiken.

### Workflows controleren {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflow HeatMap**

De Werkstroom HeatMap verstrekte een visuele vertegenwoordiging van alle werkschema&#39;s die op uw instantie lopen. Het staat u toe om de lading op de instantie gemakkelijk te controleren en werkschema&#39;s dienovereenkomstig te plannen. [Klik ](../../workflow/using/heatmap.md) hier voor meer informatie.

**Audittrail**

Met het audittrail kunt u alle wijzigingen visualiseren die in workflows zijn aangebracht, plus de huidige status. [Klik hier](../../production/using/audit-trail.md).

**Problemen met werkstromen oplossen**

Er kunnen specifieke acties worden uitgevoerd wanneer er problemen optreden met de uitvoering van een workflow. [Klik ](../../production/using/workflow-execution.md) hier voor meer informatie

**Workflow Status Monitoring**

Naast de heatmap kunt u ook een workflow maken waarmee u de status van een set workflows kunt controleren en terugkerende berichten naar supervisors kunt verzenden. [Klik ](../../workflow/using/supervising-workflows.md) hier voor meer informatie.

**Algemene richtsnoeren**

De volgende richtlijnen en beste praktijken wanneer het gebruiken van werkschema&#39;s kunnen helpen prestaties verbeteren. Raadpleeg de volgende secties voor meer informatie:
* [Tips en trucs bij het gebruik van workflows](../../workflow/using/workflow-best-practices.md)
* [Workflowuitvoering controleren](../../workflow/using/monitoring-workflow-execution.md)

### Leveringen controleren{#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP-rapporten**

In SMTP-rapporten worden leveringsstatistieken en SMTP-fouten per domein weergegeven. [Meer informatie](../../production/using/monitoring-processes.md)

**Best practices**

[De beste praktijken voor levering verzenden en ](../../delivery/using/delivery-best-practices.md) ontwerpen kunnen u helpen hun prestaties verbeteren.

**Het**
oplossen van problemen van de leveringSpecifieke acties kunnen worden uitgevoerd wanneer het ontmoeten van kwesties met leveringen:
* [Leverbaarheidsproblemen](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemen met weergave van afbeeldingen](../../production/using/image-display-issues.md)
* [Leveringsprestaties](../../delivery/using/delivery-performances.md)
* [Uitgave](../../production/using/temporary-files.md)  van tijdelijke bestanden - alleen  *op locatie voor hostingmodellen*

### De database {#monitoring-database} controleren

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Workflow voor opschonen van databases**

Met de workflow voor het opschonen van databases kunt u verouderde gegevens uit uw database verwijderen. Het wordt aanbevolen exponentiële groei van de database te vermijden. [Klik ](../../production/using/database-cleanup-workflow.md) hier voor meer informatie.

**Problemen met databaseprestaties oplossen**

Specifieke acties kunnen worden uitgevoerd wanneer er problemen optreden met databaseprestaties. [Klik ](../../production/using/database-performances.md) hier voor meer informatie.

**Databaseonderhoud**

*alleen op locatie en hybride hostingmodellen*

Wij adviseren dat u gegevensbestandonderhoud op een regelmatige basis uitvoert om overconsumptie van schijfruimte te vermijden, waarbij gegevensbestandtoegang wordt beïnvloed. [Klik ](../../production/using/recommendations.md) hier voor meer informatie.

**Back-up en herstel**

*alleen op locatie en hybride hostingmodellen*

Back-up is van essentieel belang om gegevensverlies te voorkomen in geval van een fysiek of systeemgerelateerd probleem op een computer. [Klik ](../../production/using/backup.md) hier voor meer informatie. De herstelprocedure wordt beschreven in [deze sectie](../../production/using/restoration.md).

## Technische beginselen van Campaign Classic {#campaign-classic-technical-principles}

De technische middelen zijn beschikbaar in de documentatie van Campaign Classic. Wij adviseren u vertrouwd met deze onderwerpen alvorens om het even welke technische verrichting op uw instantie uit te voeren.

**Modellen en mogelijkheden hosten**

* [Campaign Classic-hostmodellen](../../installation/using/hosting-models.md)
* [Mogelijkheden van het hostmodel](../../installation/using/capability-matrix.md)

**Serverconfiguratie**

*Alleen On-premisse en hybride hostingmodellen*

* [Verplichte serverconfiguraties](../../installation/using/campaign-server-configuration.md)
* [Configuratie van serverconf.xml-bestand](../../installation/using/the-server-configuration-file.md)
* [Serverconfiguratie voor te leveren items](../../installation/using/email-deliverability.md)
* [Opdrachtlijnen om een instantie te maken en een database te declareren](../../installation/using/command-lines.md)

**Algemene beginselen**

* [Campaign Classic-architectuur](../../production/using/general-architecture.md)
* [Campaign Classic-modules](../../production/using/operating-principle.md)
* [Campaign Classic-opties](../../installation/using/configuring-campaign-options.md)
* [Het automatisch opstarten van modules instellen](../../production/using/administration.md)
* [Configuratiebeginsel voor campagne](../../production/using/configuration-principle.md)
* [Problemen oplossen](../../production/using/performance-and-throughput-issues.md)
