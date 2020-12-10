---
solution: Campaign Classic
product: campaign
title: Leverbaarheid in Adobe Campaign Classic bewaken
description: Meer informatie over gereedschappen en richtlijnen voor het controleren van de prestaties in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 2%

---


# Leverbaarheid controleren{#monitoring-deliverability}

Hieronder vindt u nadere informatie over de verschillende monitoringinstrumenten die door Adobe Campaign worden geleverd en enkele aanvullende richtlijnen voor de controle op de leverantie.

## Monitoringtools {#monitoring-tools}

Gebruik de functies van Adobe Campaign om de prestaties van uw platform te controleren.

Met het leveringspakket hebt u toegang tot:

* Technisch traceringsrapport voor de prestaties van de dagelijks te leveren prestaties (technische controle). Met dit rapport, dat op aanvraag beschikbaar is, kunt u dagelijks een rapport ontvangen via e-mail op een opgegeven adres. Neem voor meer informatie contact op met het Adobe Customer Care-team.
* Met het [Inbox-renderrapport](../../delivery/using/inbox-rendering.md) kunt u uw berichten voorvertonen op belangrijke e-mailclients om inhoud en reputatie te scannen.
* Overzicht van berichtkwaliteit (inbox, spam).

U kunt ook de volgende gereedschappen gebruiken:

* Het **[!UICONTROL Delivery throughput]** rapport geeft u een overzicht van de productie van het volledige platform voor een bepaalde periode. Zie [deze sectie](../../reporting/using/global-reports.md#delivery-throughput)voor meer informatie.
* Het **[!UICONTROL Technical deliverability monitoring]**-rapport bevat een aantal kwaliteitsindicatoren voor de prestaties van uw platform. Zie [deze sectie](#technical-deliverability-monitoring)voor meer informatie.
* Elke levering produceert een rapport van uitzendingsstatistieken voor de verschillende dienstverleners van Internet (ISPs). Het toont sommige gegevenskwaliteit en reputatie metriek die uw leverbaarheid, met inbegrip van de volgende aantallen kunnen beïnvloeden:
   * **[!UICONTROL Hard bounces]** de gegevenskwaliteit aangeven. Dit getal moet lager zijn dan 2%.
   * **[!UICONTROL Soft bounces]** duidt op reputatie. Dit aantal zou niet hoger moeten zijn dan 10% voor om het even welke bepaalde ISP.

   Zie de sectie [Leveringsstatistieken](../../reporting/using/global-reports.md#delivery-statistics) voor meer informatie.
* Meer in het algemeen biedt het [bezorgdashboard](../../delivery/using/about-delivery-monitoring.md) u toegang tot:
   * het [leveringsoverzicht](../../delivery/using/delivery-dashboard.md#delivery-summary), dat de details van het verzenden en het aantal berichten toont om te verzenden, te verwerken en met succes te verzenden;
   * de [leveringslogboeken en de geschiedenis](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history), waaruit blijkt welk doel is uitgesloten en waarom;
   * de [trackinglogboeken](../../delivery/using/delivery-dashboard.md#tracking-logs), die het volgen informatie zoals opent tonen en klikt.

## Bewakingsrichtlijnen {#monitoring-guidelines}

Hier volgen enkele aanvullende richtlijnen voor het controleren van de leverbaarheid:

* Controleer regelmatig de [leveringdoorvoer](../../reporting/using/global-reports.md#delivery-throughput) voor het hele platform om te controleren of deze overeenkomt met de oorspronkelijke installatie.
* Controleer of [retry](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) correct is ingesteld (30 minuten voor herbestellingsperiode en meer dan 20 pogingen) in leveringssjablonen.
* Verifieer regelmatig dat [bounce](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) brievenbus toegankelijk is en dat de rekening niet op het punt staat te verlopen.
* Controleer elke leveringsproductie om ervoor te zorgen dat het met de geldigheid van de leveringsinhoud (b.v. &#39;Flash-verkoop&#39; moet in minuten worden geleverd, niet in dagen).
* Wanneer het gebruiken van [golven](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), verifieer dat elke golf genoeg tijd heeft om te beëindigen alvorens volgende wordt teweeggebracht.
* Controleer of het aantal fouten en het aantal nieuwe [quarantines](../../delivery/using/understanding-quarantine-management.md) consistent zijn met andere leveringen.
* Raadpleeg de [leveringslogboeken](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) zorgvuldig om het soort fouten te controleren die worden benadrukt (lijsten van afgewezen personen, DNS kwesties, anti-spamregels, enz.).

## Spam {#signal-spam}

Spam van het signaal is de Franse dienst die anonymized terugkoppel meldt voor Franse ISPs (Orange, SFR).

* Deze dienst staat u toe om de reputatie van Franse ISPs te volgen en de activiteitenevolutie van klanten te volgen.

* Spam van het signaal verstrekt ook directe klachten dat het eind - gebruikers door een specifieke interface registreren. Die klachten worden dan in quarantaine geplaatst van het e-mailadresgegevensbestand.

## 250ok {#deliverability-250ok}

[250](https://250ok.com/) okis een complementaire controleoplossing aan de interne hulpmiddelen van de Adobe leverbaarheid die IP en domeinlijsten van afgewezen personen, en reputatie-indicatoren verstrekken.

De verstrekte informatie is real-time, wat een pro-actieve bijstand mogelijk maakt.

## Technisch rapport van de bewaking van de aflevering {#technical-deliverability-monitoring}

Het technische rapport voor de bewaking van de leverantie wordt dagelijks bijgewerkt en is beschikbaar door naar **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** te navigeren en op de koppeling **[!UICONTROL Technical monitoring]** op het tabblad Adobe Campaign **[!UICONTROL Home]** te klikken. Het bevat een aantal kwaliteitsindicatoren voor de prestaties van uw platform.

Deze indicatoren worden dagelijks om 9.00 uur bijgewerkt.

>[!NOTE]
>
>Bovendien kunt u een dagelijks rapport per e-mail op een bepaald adres ontvangen. Laat ons het gewenste e-mailadres weten via e-mail of via het Adobe Campaign Extranet.

![](assets/s_tn_del_monitoring.png)

In het verslag worden de volgende indicatoren gebruikt:

* **[!UICONTROL Reverse DNS]** : Adobe Campaign controleert of omgekeerde DNS voor een IP adres wordt gegeven en dat dit correct naar IP wijst.

* **[!UICONTROL SPF]** (Beleidskader voor verzender): Een authentificatiemechanisme dat ISPs en brievenbusleveranciers toelaat om te controleren of de e-mailafzender op het verzendende domein wordt gemachtigd.

* **[!UICONTROL DomainKeys]** : Een service die door Yahoo is ontwikkeld en waarmee de identiteit van een e-mailafzender wordt gecertificeerd.

* **[!UICONTROL IP and RBL domain]** (Lijst voor realtime zwarte gaten): Een lijst van IP adressen en domeinen die door de organisaties van de lijst van afgewezen personen voor slechte verzendende reputatie zijn gemarkeerd. Deze lijsten worden bijgehouden door speciale organisaties zoals Spamhaus, Spamcop, SURBL/URIBL, enz. Adobe Campaign verwerkt momenteel controles tegen RBL&#39;s die een significant effect op de leverbaarbaarheid hebben. Deze RBLs wijzen op het verzenden van reputatie, en kan door ISPs worden van verwijzingen voorzien alvorens om uw e-mails te aanvaarden.

* **[!UICONTROL SNDS]** (Smart Network Data Services): Een  [Windows Live Hotmail-service](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx) tegen spam. Hotmail is enige ISP die dit type van informatie verstrekt. Benchmarkscores zijn een groen filterresultaat, een klachtenpercentage van minder dan 0,1% en geen spamvallen.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
