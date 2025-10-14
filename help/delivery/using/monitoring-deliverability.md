---
product: campaign
title: Leverbaarheid in Adobe Campaign bewaken
description: Meer informatie over gereedschappen en richtlijnen voor het controleren van de prestaties in Adobe Campaign
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
role: User, Admin
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 1%

---

# Controleer uw prestaties{#monitoring-deliverability}

Hieronder vindt u meer informatie over de verschillende bewakingstools van Adobe Campaign en enkele aanvullende richtlijnen voor het benutten van de functies die Adobe Campaign aanbiedt om de prestaties van uw platform te controleren.

## Informatie over de controle op de prestaties {#about-deliverability-monitoring}

Deze functie is beschikbaar via een speciaal pakket in Adobe Campaign. Dit pakket moet zijn geïnstalleerd om het te kunnen gebruiken. Start vervolgens de server opnieuw om rekening te houden met het pakket.
* Voor ontvangen en hybride cliënten, **de controle van de Leverbaarheid** wordt gevormd op uw geval door de technische steun en de consultants van Adobe. Neem voor meer informatie contact op met de Adobe-accountmanager.

* Voor installaties op locatie moet u het pakket **[!UICONTROL Deliverability monitoring (Email Deliverability)]** installeren via het menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Voor meer op dit, zie [&#x200B; de standaardpakketten van Campaign Classic installeren &#x200B;](../../installation/using/installing-campaign-standard-packages.md).

In Adobe Campaign Classic, **wordt de controle van de Levering** beheerd door het **[!UICONTROL Refresh for deliverability]** werkschema. Het wordt geïnstalleerd door gebrek op alle instanties en laat u de lijst van de bounce kwalificatieregels van de post, de lijst van domeinen en de lijst van MXs initialiseren. Nadat het **[!UICONTROL Deliverability monitoring (Email Deliverability)]** -pakket is geïnstalleerd, wordt deze workflow elke avond uitgevoerd om de lijst met regels regelmatig bij te werken en kunt u de leverbaarheid van het platform actief beheren.

Met het leveringspakket hebt u toegang tot:

* Het [&#x200B; Inbox teruggevend rapport &#x200B;](inbox-rendering.md) dat u toelaat om uw berichten op belangrijke e-mailcliënten voor te vertonen om inhoud en reputatie af te tasten.
* Overzicht van berichtkwaliteit (inbox, spam).

## Monitoringinstrumenten {#monitoring-tools}

U kunt ook de volgende gereedschappen gebruiken:

* Het **[!UICONTROL Delivery throughput]** -rapport geeft u een overzicht van de doorvoer van het gehele platform gedurende een bepaalde periode. Zie [deze sectie](../../reporting/using/global-reports.md#delivery-throughput)voor meer informatie.
* Elke levering produceert een rapport van uitzendingsstatistieken voor de verschillende dienstverleners van Internet (ISPs). Het toont sommige gegevenskwaliteit en reputatie metriek die uw leverbaarheid, met inbegrip van de volgende aantallen kunnen beïnvloeden:
   * **[!UICONTROL Hard bounces]** geeft de gegevenskwaliteit aan. Dit getal moet lager zijn dan 2%.
   * **[!UICONTROL Soft bounces]** geeft reputatie aan. Dit aantal zou niet hoger moeten zijn dan 10% voor om het even welke bepaalde ISP.

  Voor meer op dit, zie de [&#x200B; statistieken van de Levering &#x200B;](../../reporting/using/global-reports.md#delivery-statistics) sectie.
* Meer over het algemeen, geeft het [&#x200B; leveringsdashboard &#x200B;](about-delivery-monitoring.md) u toegang tot:
   * de [&#x200B; leveringssamenvatting &#x200B;](delivery-dashboard.md#delivery-summary), die het detail van het verzenden en het aantal berichten toont om te verzenden, te verwerken en met succes te verzenden;
   * de [&#x200B; leveringslogboeken en geschiedenis &#x200B;](delivery-dashboard.md#delivery-logs-and-history), die tonen welk doel is uitgesloten en waarom;
   * het [&#x200B; volgen logboeken &#x200B;](delivery-dashboard.md#tracking-logs), die het volgen informatie zoals opent tonen en klikt.

## Controlerichtlijnen {#monitoring-guidelines}

Hier volgen enkele aanvullende richtlijnen voor het controleren van de leverbaarheid:

* Controleer regelmatig de [&#x200B; leveringsproductie &#x200B;](../../reporting/using/global-reports.md#delivery-throughput) voor het volledige platform om te verifiëren of het met de originele opstelling verenigbaar is.
* Controle dat [&#x200B; opnieuw probeert &#x200B;](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) opstelling correct (30 minuten voor herbeproefperiode en meer dan 20 herpogingen) in leveringsmalplaatjes is.
* Verifieer regelmatig dat de [&#x200B; stuiteren &#x200B;](understanding-delivery-failures.md#bounce-mail-management) brievenbus toegankelijk is en dat de rekening niet op het punt staat te verlopen.
* Controleer elke leveringsproductie, die van het [&#x200B; leveringsdashboard &#x200B;](delivery-dashboard.md) toegankelijk is, om ervoor te zorgen dat het met de geldigheid van de leveringsinhoud verenigbaar is (b.v. &quot;flitsverkoop&quot;zou in notulen, niet dagen moeten worden geleverd).
* Wanneer het gebruiken van golven, verifieer dat elke golf genoeg tijd heeft om te beëindigen alvorens volgende wordt teweeggebracht. Zie de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/configure-and-send.html#sending-using-multiple-waves){target="_blank"}.
* Controleer dat het aantal fouten en nieuwe [&#x200B; quarantines &#x200B;](understanding-quarantine-management.md) met andere leveringen verenigbaar zijn.
* Raadpleeg zorgvuldig de [&#x200B; leveringslogboeken &#x200B;](delivery-dashboard.md#delivery-logs-and-history) in detail om het soort fouten te controleren die worden benadrukt (lijsten van gewezen personen, DNS kwesties, anti-spamregels, enz.).
