---
product: campaign
title: Aan de slag met leveringscontrole
description: Meer informatie over de mogelijkheden voor Campaign Classic-bewaking van levering
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: e60a8391416bc9899548971bddb61705467a80e5
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 1%

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

* Voor installaties op locatie moet u het pakket **[!UICONTROL Deliverability monitoring (Email Deliverability)]** installeren via het menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Voor meer op dit, zie [&#x200B; de standaardpakketten van Campaign Classic installeren &#x200B;](../../installation/using/installing-campaign-standard-packages.md).

#### Leveringsworkflow {#deliverability-workflow}

In Adobe Campaign Classic, **wordt de controle van de Levering** beheerd door het **[!UICONTROL Refresh for deliverability]** werkschema. Het wordt geïnstalleerd door gebrek op alle instanties en laat u de lijst van de bounce kwalificatieregels van de post, de lijst van domeinen en de lijst van MXs initialiseren. Nadat het **[!UICONTROL Deliverability monitoring (Email Deliverability)]** -pakket is geïnstalleerd, wordt deze workflow elke avond uitgevoerd om de lijst met regels regelmatig bij te werken en kunt u de leverbaarheid van het platform actief beheren.

**het pakket van de Levering geeft u toegang tot:**

* Het [&#x200B; Inbox teruggevend rapport &#x200B;](inbox-rendering.md) dat u toelaat om uw berichten op belangrijke e-mailcliënten voor te vertonen om inhoud en reputatie af te tasten.
* Overzicht van berichtkwaliteit (inbox, spam).

#### Monitoringinstrumenten {#monitoring-tools}

**voor op-gebouw installaties**, kunt u de volgende controlehulpmiddelen gebruiken:

* Het **[!UICONTROL Delivery throughput]** -rapport geeft u een overzicht van de doorvoer van het gehele platform gedurende een bepaalde periode. Zie [deze sectie](../../reporting/using/global-reports.md#delivery-throughput)voor meer informatie.
* Elke levering produceert een rapport van uitzendingsstatistieken voor de verschillende dienstverleners van Internet (ISPs). Het toont sommige gegevenskwaliteit en reputatie metriek die uw leverbaarheid, met inbegrip van de volgende aantallen kunnen beïnvloeden:
   * **[!UICONTROL Hard bounces]** geeft de gegevenskwaliteit aan. Dit getal moet lager zijn dan 2%.
   * **[!UICONTROL Soft bounces]** geeft reputatie aan. Dit aantal zou niet hoger moeten zijn dan 10% voor om het even welke bepaalde ISP.

  Voor meer op dit, zie de [&#x200B; statistieken van de Levering &#x200B;](../../reporting/using/global-reports.md#delivery-statistics) sectie.

#### Controlerichtlijnen {#monitoring-guidelines}

**voor op-gebouw installaties**, zijn hier sommige extra richtlijnen op leverbaarheidscontrole:

* Controleer regelmatig de [&#x200B; leveringsproductie &#x200B;](../../reporting/using/global-reports.md#delivery-throughput) voor het volledige platform om te verifiëren of het met de originele opstelling verenigbaar is.
* Controle dat [&#x200B; opnieuw probeert &#x200B;](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) opstelling correct (30 minuten voor herbeproefperiode en meer dan 20 herpogingen) in leveringsmalplaatjes is.
* Verifieer regelmatig dat de [&#x200B; stuiteren &#x200B;](understanding-delivery-failures.md#bounce-mail-management) brievenbus toegankelijk is en dat de rekening niet op het punt staat te verlopen.
* Controleer elke leveringsproductie, die van het [&#x200B; leveringsdashboard &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} toegankelijk is, om ervoor te zorgen dat het met de geldigheid van de leveringsinhoud verenigbaar is (b.v. &quot;flitsverkoop&quot;zou in notulen, niet dagen moeten worden geleverd).
* Wanneer het gebruiken van golven, verifieer dat elke golf genoeg tijd heeft om te beëindigen alvorens volgende wordt teweeggebracht.
* Controleer dat het aantal fouten en nieuwe [&#x200B; quarantines &#x200B;](understanding-quarantine-management.md) met andere leveringen verenigbaar zijn.
* Raadpleeg zorgvuldig de [&#x200B; leveringslogboeken &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"} in detail om het soort fouten te controleren die worden benadrukt (lijsten van gewezen personen, DNS kwesties, anti-spamregels, enz.).

### Problemen oplossen {#delivery-troubleshooting}

De specifieke acties kunnen worden uitgevoerd wanneer het ontmoeten van kwesties met leveringen op **hybride/op-gebouw plaatsingen**:

* [Leverbaarheidsproblemen](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemen met weergave van afbeeldingen](../../production/using/image-display-issues.md)
* [Leveringsprestaties](delivery-performance-troubleshooting.md)
* [&#x200B; Tijdelijke dossiers kwesties &#x200B;](../../production/using/temporary-files.md) - *op-gebouw slechts klanten*

## Uw leveringen controleren

Met de volgende bronnen kunt u de prestaties van uw levering in Campaign Classic v7 controleren en volgen:

### Toegang tot het dashboard voor levering

Leer hoe te om tot leveringslijsten toegang te hebben en het leveringsdashboard te gebruiken om uw verzendende activiteit te controleren:

* [&#x200B; leveringen van de Monitor in Campagne UI &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (de documentatie van de Campagne v8 - is op zowel v7 als v8 van toepassing)
* [&#x200B; leveringsstatussen &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; Geavanceerd: Pas leveringslogboeken &#x200B;](customize-delivery-logs.md) aan (v7 hybride/op-gebouw slechts - schemaversie)

### Berichtinteracties bijhouden

Het spoor opent, klikt, en ontvankelijke interactie met uw leveringen:

* [&#x200B; het volgen van het bericht documentatie &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"} (de documentatie van de Campagne v8 - is op zowel v7 als v8 van toepassing)
* [&#x200B; vorm bijgehouden verbindingen &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; het volgen van de Toegang logboeken &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"} (de documentatie van Campagne v8)

### Prestaties optimaliseren

Aanbevolen werkwijzen en probleemoplossing voor prestatieproblemen bij levering:

* [&#x200B; beste praktijken van de Levering &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (de documentatie van de Campagne v8 - is op zowel v7 als v8 van toepassing)
* [&#x200B; prestaties van de Levering en het oplossen van problemen &#x200B;](delivery-performance-troubleshooting.md) (v7 hybride/op-gebouw specifieke configuraties)

### Fouten en quarantaine begrijpen

De leveringsmislukkingen, stuitpost, en quarantined adressen beheren:

* [&#x200B; Begrijpend leveringsmislukkingen &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (de documentatie van de Campagne v8 - uitvoerige gids voor zowel v7 als v8)
* [&#x200B; het beheer van de quarantaine &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (de documentatie van de Campagne v8 - uitvoerige gids voor zowel v7 als v8)
* [&#x200B; mislukkingen van de Levering en quarantaineconfiguratie &#x200B;](delivery-failures-quarantine.md) (v7 hybride/op-gebouw specifieke configuraties)
