---
product: campaign
title: Leverbaarheid in Adobe Campaign Classic bewaken
description: Meer informatie over gereedschappen en richtlijnen voor het controleren van de prestaties in Adobe Campaign Classic.
feature: Deliverability
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 1%

---

# Controleer uw prestaties{#monitoring-deliverability}

![](../../assets/common.svg)

Hieronder vindt u meer informatie over de verschillende bewakingstools van Adobe Campaign en enkele aanvullende richtlijnen voor het benutten van de functies die Adobe Campaign biedt om de prestaties van uw platform te controleren.

## Informatie over de controle op de prestaties {#about-deliverability-monitoring}

Deze functie is beschikbaar via een speciaal pakket in Adobe Campaign. Dit pakket moet zijn geïnstalleerd om het te kunnen gebruiken. Start vervolgens de server opnieuw om rekening te houden met het pakket.
* Voor gehoste en hybride clients **Leverbaarheidscontrole** wordt op uw exemplaar gevormd door de technische steun en de consultants van Adobe. Neem voor meer informatie contact op met de manager van uw Adobe-account.

* Voor on-premise installaties, moet u installeren **[!UICONTROL Deliverability monitoring (Email Deliverability)]** pakket via de **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** -menu. Zie voor meer informatie [Campaign Classic-standaardpakketten installeren](../../installation/using/installing-campaign-standard-packages.md).

In Adobe Campaign Classic: **Leverbaarheidscontrole** wordt beheerd door de **[!UICONTROL Refresh for deliverability]** workflow. Het wordt geïnstalleerd door gebrek op alle instanties en laat u de lijst van de bounce kwalificatieregels van de post, de lijst van domeinen en de lijst van MXs initialiseren. Wanneer de **[!UICONTROL Deliverability monitoring (Email Deliverability)]** Deze workflow wordt elke avond geïnstalleerd, zodat u de lijst met regels regelmatig kunt bijwerken en de leverbaarheid van het platform actief kunt beheren.

Met het leveringspakket hebt u toegang tot:

* De [Inbox rendering report](inbox-rendering.md) Hiermee kunt u uw berichten voorvertonen op belangrijke e-mailclients om inhoud en reputatie te scannen.
* Overzicht van berichtkwaliteit (inbox, spam).

## Monitoringinstrumenten {#monitoring-tools}

U kunt ook de volgende gereedschappen gebruiken:

* De **[!UICONTROL Delivery throughput]** het rapport geeft u een overzicht van de productie van het volledige platform voor een bepaalde periode. Zie [deze sectie](../../reporting/using/global-reports.md#delivery-throughput)voor meer informatie.
* Elke levering produceert een rapport van uitzendingsstatistieken voor de verschillende dienstverleners van Internet (ISPs). Het toont sommige gegevenskwaliteit en reputatie metriek die uw leverbaarheid, met inbegrip van de volgende aantallen kunnen beïnvloeden:
   * **[!UICONTROL Hard bounces]** de gegevenskwaliteit aangeven. Dit getal moet lager zijn dan 2%.
   * **[!UICONTROL Soft bounces]** duidt op reputatie. Dit aantal zou niet hoger moeten zijn dan 10% voor om het even welke bepaalde ISP.

   Zie voor meer informatie de [Leveringsstatistieken](../../reporting/using/global-reports.md#delivery-statistics) sectie.
* Meer in het algemeen geldt het [bezorgdashboard](about-delivery-monitoring.md) geeft u toegang tot:
   * de [Overzicht van levering](delivery-dashboard.md#delivery-summary), waarin de details van de verzending en het aantal berichten dat met succes moet worden verzonden, verwerkt en verzonden, worden vermeld;
   * de [leveringslogs en geschiedenis](delivery-dashboard.md#delivery-logs-and-history), waaruit blijkt welke doelstelling is uitgesloten en waarom;
   * de [trackinglogboeken](delivery-dashboard.md#tracking-logs), waarin trackinggegevens worden weergegeven, zoals die worden geopend en waarop wordt geklikt.

## Controlerichtlijnen {#monitoring-guidelines}

Hier volgen enkele aanvullende richtlijnen voor het controleren van de leverbaarheid:

* Controleer regelmatig de [leveringsproductie](../../reporting/using/global-reports.md#delivery-throughput) voor het hele platform om na te gaan of het in overeenstemming is met de oorspronkelijke installatie.
* Controleren of [opnieuw](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) correct zijn ingesteld (30 minuten voor herbeidsperiode en meer dan 20 pogingen) in leveringssjablonen.
* Controleer regelmatig of de [stuiten](understanding-delivery-failures.md#bounce-mail-management) de brievenbus is toegankelijk en dat de rekening niet op het punt staat te verlopen.
* Controleer elke leveringstijd, toegankelijk van [bezorgdashboard](delivery-dashboard.md)om ervoor te zorgen dat de inhoud consistent is met de geldigheid van de inhoud van de levering (bijvoorbeeld &#39;Flash-verkoop&#39; moet in minuten worden geleverd, niet in dagen).
* Wanneer u [golven](steps-sending-the-delivery.md#sending-using-multiple-waves), verifieer dat elke golf genoeg tijd heeft om te beëindigen alvorens volgende wordt teweeggebracht.
* Controleer of het aantal fouten en het aantal nieuwe fouten [quarantaine](understanding-quarantine-management.md) consistent zijn met andere leveringen.
* Raadpleeg de [leveringslogs](delivery-dashboard.md#delivery-logs-and-history) in detail om het soort fouten te controleren die worden benadrukt (lijsten van gewezen personen, DNS kwesties, anti-spamregels, enz.).
