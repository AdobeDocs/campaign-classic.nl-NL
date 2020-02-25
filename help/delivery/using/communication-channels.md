---
title: Communicatiekanalen
seo-title: Communicatiekanalen
description: Communicatiekanalen
seo-description: null
page-status-flag: never-activated
uuid: 42975431-64c9-4ecb-98ed-b1f9b13c157e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 2e2d1134-9b83-4ada-b74f-c3842a0cf044
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3641e438784d40aa097f8c89ca19bdbb52f4bc7d

---


# Communicatiekanalen{#communication-channels}

Met de Campagne van Adobe, kunt u kanaalcampagnes met inbegrip van e-mail, SMS, LIJNberichten, Push berichten en directe berichten verzenden, en hun doeltreffendheid meten gebruikend diverse specifieke [rapporten](../../reporting/using/delivery-reports.md). Deze berichten worden ontworpen en verzonden door leveringen, en kunnen voor elke ontvanger worden gepersonaliseerd.

De kernfuncties omvatten het richten, het bepalen en het personaliseren van berichten, de uitvoering van mededelingen, en de bijbehorende operationele rapporten. Het belangrijkste functionele toegangspunt is de leveringstovenaar. Dit toegangspunt leidt tot verschillende mogelijkheden die door Adobe Campaign worden gedekt.

>[!NOTE]
>
>Adobe Campaign beschikt over een aantal gereedschappen om de prestaties te controleren en het verzenden van e-mailberichten te optimaliseren. Raadpleeg voor meer informatie de [introductie](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) en het [leveringsbeheer](../../delivery/using/about-deliverability.md).

Het verzenden van leveringen kan worden geautomatiseerd door de levering voor te bereiden en/of te verzenden tijdens een workflow. Voor meer op levering-type activiteiten in werkschema&#39;s, verwijs naar [deze sectie](../../workflow/using/about-action-activities.md).

Adobe Campaign biedt de volgende leveringskanalen:

1. **E-mailkanaal**: Met e-mailleveringen kunt u persoonlijke e-mails sturen naar de doelgroep. Zie [Informatie over e-mailkanaal](../../delivery/using/about-email-channel.md).
1. **Direct-mailkanaal**: met direct mail kunt u een extractiebestand genereren dat gegevens over de doelpopulatie bevat. Zie [Informatie over direct-mailkanaal](../../delivery/using/about-direct-mail-channel.md).
1. **Mobiel kanaal**: Met leveringen op mobiele kanalen kunt u persoonlijke SMS- of LINE-berichten naar de doelgroep sturen. Zie [SMS-kanaal](../../delivery/using/sms-channel.md).
1. **Mobiel toepassingskanaal**: Met levering voor mobiele apps kunt u meldingen verzenden naar iOS- en Android-systemen. Raadpleeg het hoofdstuk over het kanaal [van de](../../delivery/using/about-mobile-app-channel.md) mobiele app.

   Andere kanalen worden beschreven in [deze pagina](../../delivery/using/other-channels.md).

   >[!NOTE]
   >
   >Het gebruik van meerdere kanalen is afhankelijk van het pakket. Controleer uw licentieovereenkomst.

Leveringen kunnen **online** (via e-mail, een van de mobiele kanalen en pushmeldingen) en **offline** (direct-mailkanaal) worden uitgevoerd.

Afhankelijk van het kanaal, kunnen de leveringswijzen zijn:

* Directe levering van massa via Adobe Campaign (standaardmodus voor e-mailkanaal).
* Externe levering via een gespecialiseerde operator die het uitvoerbestand krijgt dat wordt gegenereerd door de wizard voor levering (standaardmodus voor direct-mailkanaal).

Externe accounts worden geconfigureerd via het **[!UICONTROL Administration > Platform > External accounts]** knooppunt. Deze configuratie moet alleen door deskundige gebruikers worden uitgevoerd.

## E-mailleveringen {#email-deliveries}

Het [e-mailkanaal](../../delivery/using/about-email-channel.md) is een van de kernkanalen van Adobe Campaign, waarmee u persoonlijke e-mailberichten kunt plannen en verzenden naar specifieke doelgroepen.

U kunt verschillende typen e-mailberichten verzenden:

* E-mails met één verzending: e-mails die u één keer naar een bepaald doel kunt verzenden. Deze worden gewoonlijk gebruikt om een specifieke inhoud te promoten die maar één keer wordt voorbereid en verzonden (nieuwsbrief, promotionele e-mail, enz.).
* E-mails terugsturen: in een campagne regelmatig dezelfde e-mail sturen en elk bericht en de bijbehorende verslagen samenvoegen. Dezelfde e-mail wordt verzonden, maar doorgaans naar een ander doel, op basis van het in aanmerking komende doel voor de dag van de verzending. Een veelvoorkomend voorbeeld is een e-mailbericht voor verjaardagen. Raadpleeg [Terugkerende leveringen](../../workflow/using/recurring-delivery.md)voor meer informatie hierover.
* Transactiee-mails: Eenvoudige e-mailberichten die worden geactiveerd op basis van het gedrag van uw klanten. Zie [Transactioneel overseinen](../../message-center/using/about-transactional-messaging.md).

Als u meer wilt weten over het gebruik en de aanbevelingen van de [levering, raadpleegt u de best practices](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)voor de levering van campagnes.

Raadpleeg [deze sectie](../../delivery/using/types-of-deliveries.md)voor meer informatie over de verschillende typen leveringen.

## Mobiele leveringen {#mobile-deliveries}

Met Adobe Campaign kunt u [SMS](../../delivery/using/sms-channel.md) - en [LINE](../../delivery/using/line-channel.md) -berichten op mobiele apparaten verzenden.

Voor SMS-berichten kunt u alleen in tekstindeling berichten maken, wijzigen en personaliseren. Je kunt ook een voorbeeld van je SMS-berichten bekijken voordat ze worden verzonden.

Voor lijnberichten kunt u tekst of afbeeldingen en koppelingen verzenden.

Als u SMS- of lijnberichten wilt verzenden naar een mobiele telefoon die u nodig hebt:

* Een externe account die op het **[!UICONTROL Mobile (SMS)]** kanaal of op het **[!UICONTROL LINE]** kanaal is geconfigureerd.
* Een SMS- of REGELS-leveringssjabloon die correct is gekoppeld aan deze externe account.

## Pushmeldingen {#push-notifications}

Met Adobe Campaign kunt u persoonlijke en gesegmenteerde [pushmeldingen](../../delivery/using/about-mobile-app-channel.md) verzenden naar mobiele iOS- en Android-apparaten via speciale apps. Nadat configuratie- en integratiestappen zijn uitgevoerd, kunnen iOS- en Android-leveringen worden gemaakt en verzonden. U kunt ook veelzijdige meldingen ontwerpen met afbeeldingen of video&#39;s.

## Direct mail {#direct-mail}

[Directe post](../../delivery/using/about-direct-mail-channel.md) is een off-line kanaal dat u toestaat om het dossier te personaliseren en te produceren dat door directe postleveranciers wordt vereist. Het biedt u de mogelijkheid om online en off-line kanalen in uw klantenreizen te mengen.

Met onlinekanalen kunt u uw berichten maken (e-mail, sms, levering van mobiele apps, enz.) en stuur ze rechtstreeks vanuit Adobe Campaign naar uw doelgroep. Bij offlinekanalen is dit anders. Wanneer u een directe postbestelling voorbereidt, genereert Adobe Campagne een dossier met alle gerichte profielen en de gekozen contactinformatie (postadres bijvoorbeeld). U kunt dit bestand dan naar uw directe-mailprovider sturen, die voor de verzending zal zorgen.
