---
product: campaign
title: Controlerichtlijnen
description: Ontdek richtlijnen en best practices om de Campaign-instantie en -processen te controleren
feature: Monitoring
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 18%

---

# Controlerichtlijnen {#monitoring-guidelines}



## Instance Monitoring dashboard {#instance-monitoring-dashboard}

De **[!UICONTROL Monitoring]** tab, dat toegankelijk is vanaf de startpagina van het Campaign Classic, is het belangrijkste ingangspunt waarmee u uw instantie kunt controleren.

Het verstrekt een dashboard van wat op uw instantie voorkomt: zijn status (bouwstijlversie, geïnstalleerde pakketten, enz.), systeemindicatoren, logboeken, werkschema&#39;s die momenteel lopen, staat van laatste verzonden leveringen, enz.

Gedetailleerde informatie is [hier](../../production/using/monitoring-processes.md) beschikbaar.

![](assets/monitoring_tab.png)

## Bewaking van Campaigns Classic {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Uw instantie controleren</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#monitoring-workflows">Workflows bewaken</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Leveringen controleren</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">De database controleren</a></p></td></tr>
</table>

Er zijn aanvullende manieren beschikbaar om de verschillende campagneprocessen te controleren. Zij verstrekken verscheidene manieren om uw instanties te controleren om ervoor te zorgen dat uw systeem gezond is en uiteindelijk problemen problemen op te lossen die zich kunnen voordoen wanneer vestiging werkschema&#39;s, verzendende leveringen, enz.

### Uw exemplaar controleren {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Automatische bewakingsgereedschappen**

Er zijn verschillende automatische methoden beschikbaar. om u te helpen uw instantie controleren. U kunt bijvoorbeeld e-mailrapporten instellen met opgespoorde anomalieën, een lijst met indicatoren ophalen in XML-indeling, enzovoort. [Klik hier](../../production/using/monitoring-processes.md#automatic-monitoring) voor meer informatie.

**Audittrail**

Met het audittrail kunt u de volledige geschiedenis van wijzigingen met betrekking tot opties, workflows en schema&#39;s binnen uw instantie visualiseren. [Klik hier](../../production/using/audit-trail.md) voor meer informatie.

**Configuratiescherm**

In het Configuratiescherm kunt u verschillende instellingen van uw instantie beheren: beheer de URL-machtigingen, controleer de instantiedetails zoals de buildversies van uw servers, enzovoort. Hiermee kunt u ook de beschikbare ruimte op de SFTP-servers controleren die met uw instantie zijn verbonden. [Klik hier](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=nl) voor meer informatie.

>[!NOTE]
>
>Het configuratiescherm is toegankelijk voor alle gebruikers met beheerdersrechten. De stappen om toegang met beheerdersrechten aan een gebruiker te verlenen worden gedetailleerd beschreven op [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=nl#discover-control-panel).
>
>Merk op dat uw exemplaar op AWS moet worden gehost en geüpgraded met de [nieuwste GA-build](../../rn/using/rn-overview.md). Leer hoe u uw versie kunt controleren in [dit gedeelte](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Controleer of uw versie wordt gehost op AWS door de volgende stappen te volgen op [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=nl).

### Workflows controleren {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflow HeatMap**

De Werkstroom HeatMap verstrekte een visuele vertegenwoordiging van alle werkschema&#39;s die op uw instantie lopen. Het staat u toe om de lading op de instantie gemakkelijk te controleren en werkschema&#39;s dienovereenkomstig te plannen. [Klik hier](../../workflow/using/heatmap.md) voor meer informatie.

**Audittrail**

Met het audittrail kunt u alle wijzigingen visualiseren die in workflows zijn aangebracht, plus de huidige status. [Klik hier](../../production/using/audit-trail.md).

**Problemen met werkstromen oplossen**

Er kunnen specifieke acties worden uitgevoerd wanneer er problemen optreden met de uitvoering van een workflow. [Klik hier](../../production/using/workflow-execution.md) voor meer informatie

**Workflowstatuscontrole**

Naast de heatmap kunt u ook een workflow maken waarmee u de status van een set workflows kunt controleren en terugkerende berichten naar supervisors kunt verzenden. [Klik hier](../../workflow/using/supervising-workflows.md) voor meer informatie.

**Algemene richtsnoeren**

De volgende richtlijnen en beste praktijken wanneer het gebruiken van werkschema&#39;s kunnen helpen prestaties verbeteren. Raadpleeg de volgende secties voor meer informatie:
* [Tips en trucs bij het gebruik van workflows](../../workflow/using/workflow-best-practices.md)
* [Workflowuitvoering controleren](../../workflow/using/monitoring-workflow-execution.md)

### Bewaking van leveringen {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP-rapporten**

In SMTP-rapporten worden leveringsstatistieken en SMTP-fouten per domein weergegeven. [Meer informatie](../../production/using/monitoring-processes.md)

**Best practices**

[Aanbevolen procedures voor verzending en ontwerp van levering](../../delivery/using/delivery-best-practices.md) kan u helpen hun prestaties te verbeteren.

**Problemen met levering oplossen**
Specifieke acties kunnen worden uitgevoerd wanneer problemen met leveringen optreden:
* [Leverbaarheidsproblemen](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemen met weergave van afbeeldingen](../../production/using/image-display-issues.md)
* [Leveringsprestaties](../../delivery/using/delivery-performances.md)
* [Problemen met tijdelijke bestanden](../../production/using/temporary-files.md) - *alleen hostingmodellen op locatie*

### Toezicht op de database {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Workflow voor opschonen van databases**

Met de workflow voor het opschonen van databases kunt u verouderde gegevens uit uw database verwijderen. Het wordt aanbevolen exponentiële groei van de database te vermijden. [Klik hier](../../production/using/database-cleanup-workflow.md) voor meer informatie.

**Problemen met databaseprestaties oplossen**

Specifieke acties kunnen worden uitgevoerd wanneer er problemen optreden met databaseprestaties. [Klik hier](../../production/using/database-performances.md) voor meer informatie.

**Databaseonderhoud**

*alleen op locatie en hybride hostingmodellen*

Wij adviseren dat u gegevensbestandonderhoud op een regelmatige basis uitvoert om overconsumptie van schijfruimte te vermijden, waarbij gegevensbestandtoegang wordt beïnvloed. [Klik hier](../../production/using/recommendations.md) voor meer informatie.

**Back-up en herstel**

*alleen op locatie en hybride hostingmodellen*

Back-up is van essentieel belang om gegevensverlies te voorkomen in geval van een fysiek of systeemgerelateerd probleem op een computer. [Klik hier](../../production/using/backup.md) voor meer informatie . De herstelprocedure wordt beschreven in [deze sectie](../../production/using/restoration.md).

## Technische beginselen van Campaign Classic {#campaign-classic-technical-principles}

De technische middelen zijn beschikbaar in de documentatie van het Campaign Classic. Wij adviseren u vertrouwd met deze onderwerpen alvorens om het even welke technische verrichting op uw instantie uit te voeren.

**Modellen en mogelijkheden hosten**

* [Campaign Classic-hostmodellen](../../installation/using/hosting-models.md)
* [Mogelijkheden van het hostmodel](../../installation/using/capability-matrix.md)

**Serverconfiguratie**

*Alleen On-premisse en hybride hostingmodellen*

* [Serverconfiguraties](../../installation/using/configuring-campaign-server.md)
* [Configuratie van serverconf.xml-bestand](../../installation/using/the-server-configuration-file.md)
* [Serverconfiguratie voor te leveren items](../../installation/using/email-deliverability.md)
* [Opdrachtlijnen om een instantie te maken en een database te declareren](../../installation/using/command-lines.md)

**Algemene beginselen**

* [Campaign Classic architectuur](../../production/using/general-architecture.md)
* [Campaigns Classic](../../production/using/operating-principle.md)
* [Opties voor Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Het automatisch opstarten van modules instellen](../../production/using/administration.md)
* [Configuratiebeginsel voor campagne](../../production/using/configuration-principle.md)
* [Problemen oplossen](../../production/using/performance-and-throughput-issues.md)
