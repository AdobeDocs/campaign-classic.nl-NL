---
product: campaign
title: Leverbaarheid in Adobe Campaign Classic bewaken
description: Meer informatie over gereedschappen en richtlijnen voor het controleren van de prestaties in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 2%

---

# Leverbaarheid controleren{#monitoring-deliverability}

Hieronder vindt u meer informatie over de verschillende bewakingstools van Adobe Campaign en enkele aanvullende richtlijnen voor het benutten van de functies die Adobe Campaign biedt om de prestaties van uw platform te controleren.

## Leverbaarheidscontrole {#configuration}

Deze functie is beschikbaar via een speciaal pakket in Adobe Campaign. Dit pakket moet geïnstalleerd zijn om het te kunnen gebruiken. Start vervolgens de server opnieuw om rekening te houden met het pakket.
* Voor gehoste en hybride clients wordt **Deliverability monitoring** op uw exemplaar geconfigureerd door technische support en consultants van Adobe. Neem voor meer informatie contact op met de manager van uw Adobe-account.

* Voor installaties op locatie moet u het **[!UICONTROL Deliverability monitoring (Email Deliverability)]**-pakket installeren via het menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**. Zie [Campaign Classic-standaardpakketten installeren](../../installation/using/installing-campaign-standard-packages.md) voor meer informatie.

In Adobe Campaign Classic wordt **Deliverability monitoring** beheerd door de **[!UICONTROL Refresh for deliverability]** workflow. Het wordt geïnstalleerd door gebrek op alle instanties en laat u de lijst van de bounce kwalificatieregels van de post, de lijst van domeinen en de lijst van MXs initialiseren. Nadat het **[!UICONTROL Deliverability monitoring (Email Deliverability)]**-pakket is geïnstalleerd, wordt deze workflow elke avond uitgevoerd om de lijst met regels regelmatig bij te werken en kunt u de leverbaarheid van het platform actief beheren.

Met het leveringspakket hebt u toegang tot:

* Met het [Inbox-renderrapport](inbox-rendering.md) kunt u uw berichten voorvertonen op belangrijke e-mailclients om inhoud en reputatie te scannen.
* Overzicht van berichtkwaliteit (inbox, spam).

## Monitoringinstrumenten {#monitoring-tools}

U kunt ook de volgende gereedschappen gebruiken:

* Het **[!UICONTROL Delivery throughput]** rapport geeft u een overzicht van de productie van het volledige platform voor een bepaalde periode. Zie [deze sectie](../../reporting/using/global-reports.md#delivery-throughput)voor meer informatie.
* Elke levering produceert een rapport van uitzendingsstatistieken voor de verschillende dienstverleners van Internet (ISPs). Het toont sommige gegevenskwaliteit en reputatie metriek die uw leverbaarheid, met inbegrip van de volgende aantallen kunnen beïnvloeden:
   * **[!UICONTROL Hard bounces]** de gegevenskwaliteit aangeven. Dit getal moet lager zijn dan 2%.
   * **[!UICONTROL Soft bounces]** duidt op reputatie. Dit aantal zou niet hoger moeten zijn dan 10% voor om het even welke bepaalde ISP.

   Zie de sectie [Leveringsstatistieken](../../reporting/using/global-reports.md#delivery-statistics) voor meer informatie.
* Meer in het algemeen biedt het [bezorgdashboard](about-delivery-monitoring.md) u toegang tot:
   * het [leveringsoverzicht](delivery-dashboard.md#delivery-summary), dat de details van het verzenden en het aantal berichten toont om te verzenden, te verwerken en met succes te verzenden;
   * de [leveringslogboeken en de geschiedenis](delivery-dashboard.md#delivery-logs-and-history), waaruit blijkt welk doel is uitgesloten en waarom;
   * de [trackinglogboeken](delivery-dashboard.md#tracking-logs), die het volgen informatie zoals opent tonen en klikt.

## Controlerichtlijnen {#monitoring-guidelines}

Hier volgen enkele aanvullende richtlijnen voor het controleren van de leverbaarheid:

* Controleer regelmatig de [leveringdoorvoer](../../reporting/using/global-reports.md#delivery-throughput) voor het hele platform om te controleren of deze overeenkomt met de oorspronkelijke installatie.
* Controleer of [retry](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) correct is ingesteld (30 minuten voor herbestellingsperiode en meer dan 20 pogingen) in leveringssjablonen.
* Verifieer regelmatig dat [bounce](understanding-delivery-failures.md#bounce-mail-management) brievenbus toegankelijk is en dat de rekening niet op het punt staat te verlopen.
* Controleer elke leveringstijd, die van [leveringsdashboard](delivery-dashboard.md) toegankelijk is, om ervoor te zorgen dat het met de geldigheid van de leveringsinhoud (b.v. &#39;Flash-verkoop&#39; moet in minuten worden geleverd, niet in dagen).
* Wanneer het gebruiken van [golven](steps-sending-the-delivery.md#sending-using-multiple-waves), verifieer dat elke golf genoeg tijd heeft om te beëindigen alvorens volgende wordt teweeggebracht.
* Controleer of het aantal fouten en het aantal nieuwe [quarantines](understanding-quarantine-management.md) consistent zijn met andere leveringen.
* Raadpleeg de [leveringslogboeken](delivery-dashboard.md#delivery-logs-and-history) zorgvuldig om het soort fouten te controleren die worden benadrukt (lijsten van gewezen personen, DNS kwesties, anti-spamregels, enz.).

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
