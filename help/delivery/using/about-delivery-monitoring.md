---
product: campaign
title: Aan de slag met leveringscontrole
description: Meer informatie over de mogelijkheden voor Campaign Classic-bewaking van levering
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 2%

---

# Aan de slag met leveringscontrole {#about-delivery-monitoring}

>[!IMPORTANT]
>
>Deze pagina documenteert **Campaign Classic v7-specifieke controleeigenschappen** voor hybride en op-gebouw plaatsingen.

## Monitorfuncties

### Afleveringscontrole {#monitoring-deliveries}

**voor de hybride/op-gebouw plaatsingen van Campaign Classic v7**, wordt de extra controle vereist voor servermiddelen en (de Agent van de Overdracht van de Post) configuratie MTA.

#### Problemen met in behandeling zijnde leveringen oplossen {#pending-deliveries}

Wat als de leveringen niet worden verzonden en hun status blijft **Hangende**?

* Het uitvoeringsproces wacht op de beschikbaarheid van sommige bronnen. De MTA is mogelijk niet gestart.
Controleer of uw modules mta@instance op uw servers MTA worden gelanceerd en begin indien nodig de module MTA. [Meer informatie](../../production/using/administration.md).

* De levering kan een affiniteit gebruiken die niet op de verzendende instantie is gevormd.
Tip: controleer de configuratie van verkeersbeheer (IP affiniteit). Voor meer op dit, zie het uitgaande verkeer SMTP van de Controle.

>[!NOTE]
>
>Deze stappen kunnen slechts door een deskundige gebruiker op-gebouw installaties worden uitgevoerd.

### Leverbaarheidscontrole {#deliverability-monitoring}

#### Installatie van het leveringspakket {#deliverability-package}

Deze functie is beschikbaar via een speciaal pakket in Adobe Campaign. Dit pakket moet zijn geïnstalleerd om het te kunnen gebruiken. Start vervolgens de server opnieuw om rekening te houden met het pakket.

* Voor ontvangen en hybride cliënten, **de controle van de Leverbaarheid** wordt gevormd op uw geval door de technische steun en de consultants van Adobe. Neem voor meer informatie contact op met de Adobe-accountmanager.

* Voor installaties op locatie moet u het pakket **[!UICONTROL Deliverability monitoring (Email Deliverability)]** installeren via het menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Voor meer op dit, zie [ de standaardpakketten van Campaign Classic installeren ](../../installation/using/installing-campaign-standard-packages.md).

#### Leveringsworkflow {#deliverability-workflow}

In Adobe Campaign Classic, **wordt de controle van de Levering** beheerd door het **[!UICONTROL Refresh for deliverability]** werkschema. Het wordt geïnstalleerd door gebrek op alle instanties en laat u de lijst van de bounce kwalificatieregels van de post, de lijst van domeinen en de lijst van MXs initialiseren. Nadat het **[!UICONTROL Deliverability monitoring (Email Deliverability)]** -pakket is geïnstalleerd, wordt deze workflow elke avond uitgevoerd om de lijst met regels regelmatig bij te werken en kunt u de leverbaarheid van het platform actief beheren.

**het pakket van de Levering geeft u toegang tot:**

* Het [ Inbox teruggevend rapport ](inbox-rendering.md) dat u toelaat om uw berichten op belangrijke e-mailcliënten voor te vertonen om inhoud en reputatie af te tasten.
* Overzicht van berichtkwaliteit (inbox, spam).

#### Monitoringinstrumenten {#monitoring-tools}

**voor op-gebouw installaties**, kunt u de volgende controlehulpmiddelen gebruiken:

* Het **[!UICONTROL Delivery throughput]** -rapport geeft u een overzicht van de doorvoer van het gehele platform gedurende een bepaalde periode. Zie [deze sectie](../../reporting/using/global-reports.md#delivery-throughput)voor meer informatie.
* Elke levering produceert een rapport van uitzendingsstatistieken voor de verschillende dienstverleners van Internet (ISPs). Het toont sommige gegevenskwaliteit en reputatie metriek die uw leverbaarheid, met inbegrip van de volgende aantallen kunnen beïnvloeden:
   * **[!UICONTROL Hard bounces]** geeft de gegevenskwaliteit aan. Dit getal moet lager zijn dan 2%.
   * **[!UICONTROL Soft bounces]** geeft reputatie aan. Dit aantal zou niet hoger moeten zijn dan 10% voor om het even welke bepaalde ISP.

  Voor meer op dit, zie de [ statistieken van de Levering ](../../reporting/using/global-reports.md#delivery-statistics) sectie.

#### Controlerichtlijnen {#monitoring-guidelines}

**voor op-gebouw installaties**, zijn hier sommige extra richtlijnen op leverbaarheidscontrole:

* Controleer regelmatig de [ leveringsproductie ](../../reporting/using/global-reports.md#delivery-throughput) voor het volledige platform om te verifiëren of het met de originele opstelling verenigbaar is.
* Controle dat [ opnieuw probeert ](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) opstelling correct (30 minuten voor herbeproefperiode en meer dan 20 herpogingen) in leveringsmalplaatjes is.
* Verifieer regelmatig dat de [ stuiteren ](understanding-delivery-failures.md#bounce-mail-management) brievenbus toegankelijk is en dat de rekening niet op het punt staat te verlopen.
* Controleer elke leveringsproductie, die van het [ leveringsdashboard ](delivery-dashboard.md) toegankelijk is, om ervoor te zorgen dat het met de geldigheid van de leveringsinhoud verenigbaar is (b.v. &quot;flitsverkoop&quot;zou in notulen, niet dagen moeten worden geleverd).
* Wanneer het gebruiken van golven, verifieer dat elke golf genoeg tijd heeft om te beëindigen alvorens volgende wordt teweeggebracht.
* Controleer dat het aantal fouten en nieuwe [ quarantines ](understanding-quarantine-management.md) met andere leveringen verenigbaar zijn.
* Raadpleeg zorgvuldig de [ leveringslogboeken ](delivery-dashboard.md#delivery-logs-and-history) in detail om het soort fouten te controleren die worden benadrukt (lijsten van gewezen personen, DNS kwesties, anti-spamregels, enz.).

### Problemen oplossen {#delivery-troubleshooting}

De specifieke acties kunnen worden uitgevoerd wanneer het ontmoeten van kwesties met leveringen op **hybride/op-gebouw plaatsingen**:

* [Leverbaarheidsproblemen](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemen met weergave van afbeeldingen](../../production/using/image-display-issues.md)
* [Leveringsprestaties](delivery-performances.md)
* [ Tijdelijke dossiers kwesties ](../../production/using/temporary-files.md) - *op-gebouw slechts klanten*

## Algemene monitoringonderwerpen

**monitor uw leveringen:**

* [ controleert uw leveringen in Campagne UI ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (de documentatie van de Campagne v8)
* [Leveringsprestaties en beste praktijken](delivery-performances.md)
* [ Begrijpend leveringsmislukkingen ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (de documentatie van de Campagne v8 - uitvoerige gids voor zowel v7 als v8)

**v7-specifieke configuratie:**

* [ Bounce de beheerconfiguratie van de post ](understanding-delivery-failures.md) (v7 hybride/op-gebouw)
* [ het beheer van de quarantaine ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (de documentatie van de Campagne v8 - uitvoerige gids voor zowel v7 als v8)
* [ de configuratie van de quarantaine ](understanding-quarantine-management.md) (v7 hybride/op-gebouw)

**de berichten van het Spoor:**

* [Aan de slag met bericht bijhouden](about-message-tracking.md)

## Verwante onderwerpen

* [ leveringsstatussen ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (de documentatie van de Campagne v8)
