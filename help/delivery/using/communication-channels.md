---
title: Communicatiekanalen
seo-title: Communicatiekanalen
description: Maak leveringen om gepersonaliseerde berichten op verschillende kanalen te verzenden.
seo-description: null
page-status-flag: never-activated
uuid: 42975431-64c9-4ecb-98ed-b1f9b13c157e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 2e2d1134-9b83-4ada-b74f-c3842a0cf044
translation-type: tm+mt
source-git-commit: e01acc00d0b15df99c009fe29d170ed0fc9fa956
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 11%

---


# Communicatiekanalen{#communication-channels}

Met Adobe Campaign kunt u kanaalcampagnes verzenden, waaronder e-mails, SMS, LIJN-berichten, pushberichten en directe mails, en de doeltreffendheid van deze campagnes meten aan de hand van verschillende speciale [rapporten](../../reporting/using/delivery-reports.md). Deze berichten worden ontworpen en verzonden door leveringen, en kunnen voor elke ontvanger worden gepersonaliseerd.

De kernfuncties omvatten het richten, het bepalen en het personaliseren van berichten, de uitvoering van mededelingen, en de bijbehorende operationele rapporten. Het belangrijkste functionele toegangspunt is de leveringstovenaar. Dit toegangspunt leidt tot meerdere mogelijkheden die door Adobe Campaign worden gedekt.

>[!NOTE]
>
>Adobe Campaign beschikt over een set gereedschappen om de prestaties te controleren en het verzenden van e-mail te optimaliseren. Raadpleeg voor meer informatie de [introductie](../../delivery/using/deliverability-key-points.md) en het [leveringsbeheer](../../delivery/using/about-deliverability.md).

Het verzenden van leveringen kan worden geautomatiseerd door de levering voor te bereiden en/of te verzenden tijdens een workflow. Voor meer op levering-type activiteiten in werkschema&#39;s, verwijs naar [deze sectie](../../workflow/using/about-action-activities.md).

Adobe Campaign biedt de volgende leveringskanalen:

1. **E-mailkanaal**: Met e-mailleveringen kunt u persoonlijke e-mails sturen naar de doelgroep. Zie [Informatie over e-mailkanaal](../../delivery/using/about-email-channel.md).
1. **Direct-mailkanaal**: met direct mail kunt u een extractiebestand genereren dat gegevens over de doelpopulatie bevat. Zie [Informatie over direct-mailkanaal](../../delivery/using/about-direct-mail-channel.md).
1. **Mobiel kanaal**: Met leveringen op mobiele kanalen kunt u persoonlijke SMS- of LINE-berichten naar de doelgroep sturen. Zie [SMS-kanaal](../../delivery/using/sms-channel.md).
1. **Mobiel toepassingskanaal**: Met levering voor mobiele apps kunt u meldingen verzenden naar iOS- en Android-systemen. Raadpleeg het hoofdstuk over het kanaal [van de](../../delivery/using/about-mobile-app-channel.md) mobiele app.

   Andere kanalen worden beschreven op [deze pagina](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >Het aantal beschikbare kanalen is afhankelijk van uw contract. Controleer hiervoor uw licentieovereenkomst.

Leveringen kunnen **online** (via e-mail, een van de mobiele kanalen en pushmeldingen) en **offline** (direct-mailkanaal) worden uitgevoerd.

Afhankelijk van het kanaal, kunnen de leveringswijzen zijn:

* Directe levering van massa via Adobe Campaign (standaardmodus voor e-mailkanaal).
* Externe levering via een gespecialiseerde operator die het uitvoerbestand krijgt dat wordt gegenereerd door de wizard voor levering (standaardmodus voor direct-mailkanaal).

Externe accounts worden geconfigureerd via het **[!UICONTROL Administration > Platform > External accounts]** knooppunt. Deze configuratie moet alleen door deskundige gebruikers worden uitgevoerd.

## E-mailleveringen {#email-deliveries}

Het [e-mailkanaal](../../delivery/using/about-email-channel.md) is een van de belangrijkste kanalen in Adobe Campaign, zodat u persoonlijke e-mails kunt plannen en verzenden naar specifieke doelen.

U kunt verschillende typen e-mailberichten verzenden:

* E-mails met één verzending: e-mails die u één keer naar een bepaald doel kunt verzenden. Deze worden gewoonlijk gebruikt om een specifieke inhoud te promoten die maar één keer wordt voorbereid en verzonden (nieuwsbrief, promotiemail, enz.).
* E-mails terugsturen: in een campagne regelmatig dezelfde e-mail sturen en elk bericht en de bijbehorende verslagen samenvoegen. Dezelfde e-mail wordt verzonden, maar doorgaans naar een ander doel, op basis van het in aanmerking komende doel voor de dag van de verzending. Een veelvoorkomend voorbeeld is een e-mailbericht voor verjaardagen. For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* Transactiee-mails: Eenvoudige e-mailberichten die worden geactiveerd op basis van het gedrag van uw klanten. Zie [Transactioneel overseinen](../../message-center/using/about-transactional-messaging.md).

Als u meer wilt weten over het gebruik en de aanbevelingen van de [levering, raadpleegt u de best practices](../../delivery/using/delivery-best-practices.md)voor de levering van campagnes.

Raadpleeg [deze sectie](#types-of-deliveries)voor meer informatie over de verschillende typen leveringen.

## Mobiele leveringen {#mobile-deliveries}

Met Adobe Campaign kunt u [SMS](../../delivery/using/sms-channel.md) - en [LINE](../../delivery/using/line-channel.md) -berichten op mobiele apparaten verzenden.

Voor SMS-berichten kunt u alleen in tekstindeling berichten maken, wijzigen en personaliseren. Je kunt ook een voorbeeld van je SMS-berichten bekijken voordat ze worden verzonden.

Voor lijnberichten kunt u tekst of afbeeldingen en koppelingen verzenden.

Als u SMS- of lijnberichten wilt verzenden naar een mobiele telefoon die u nodig hebt:

* Een externe account die op het **[!UICONTROL Mobile (SMS)]** kanaal of op het **[!UICONTROL LINE]** kanaal is geconfigureerd.
* Een SMS- of REGELS-leveringssjabloon die correct is gekoppeld aan deze externe account.

## Pushmeldingen {#push-notifications}

Adobe Campaign allows you to send personalized and segmented [push notifications](../../delivery/using/about-mobile-app-channel.md) on iOS and Android mobile devices, through dedicated apps. Nadat configuratie- en integratiestappen zijn uitgevoerd, kunnen iOS- en Android-leveringen worden gemaakt en verzonden. U kunt ook veelzijdige meldingen ontwerpen met afbeeldingen of video&#39;s.

## Direct mail {#direct-mail}

[Direct mail is een offline kanaal waarmee u het bestand dat wordt vereist door direct-mailproviders kunt personaliseren en genereren. ](../../delivery/using/about-direct-mail-channel.md) Het biedt u de mogelijkheid om online en offline kanalen in uw klanttrajecten te combineren.

Met online kanalen kunt u uw berichten (e-mail, sms, levering van mobiele apps, enzovoort) maken en ze vanuit Adobe Campaign direct naar uw doelgroep verzenden. Bij offline kanalen is dit anders. Wanneer u een direct-maillevering voorbereidt, genereert Adobe Campaign een bestand met alle doelprofielen en de gekozen contactinformatie (bijvoorbeeld postadres). U kunt dit bestand dan naar uw direct-mailprovider sturen, die voor de werkelijke verzending zorgt.

## Andere kanalen {#other-channels}

Adobe Campaign biedt leveringssjablonen van het Bureau of de Telefoon aan, die worden gebruikt om externe leveringen tot stand te brengen. Als u deze kanalen gebruikt, moet u speciale methoden instellen voor het verwerken van uitvoerbestanden. De stappen van de configuratie zijn het zelfde als voor [Directe post kanaal](../../delivery/using/about-direct-mail-channel.md).

Bovendien gebruiken de &quot;Andere&quot;typeleveringen een specifiek technisch malplaatje dat geen proces uitvoert: hiermee kunnen ze marketingacties beheren die buiten het Adobe Campaign-platform worden uitgevoerd.

Dit kanaal heeft geen specifiek mechanisme. Het is een generisch kanaal dat zijn eigen externe rekening heeft die optie, het type van leveringsmalplaatje en activiteit van het campagnewerkschema verpletteren, enkel zoals een ander communicatiekanaal beschikbaar in Adobe Campaign.

Dit kanaal is alleen bedoeld voor beschrijvende doeleinden, bijvoorbeeld om leveringen te definiëren waarvoor u het doel van een campagne die is uitgevoerd in een ander programma dan Adobe Campaign, wilt bijhouden.

## Typen leveringen{#types-of-deliveries}

Er zijn drie typen leveringsobjecten in campagne:

### Eén levering {#single-delivery}

Een **levering** is een standalone leveringsvoorwerp dat eens wordt uitgevoerd. Het kan worden gedupliceerd, opnieuw worden bereid, maar zolang het in zijn definitieve staat (geannuleerd, gestopt, gebeëindigd) is, kan het niet opnieuw worden gebruikt.

Leveringen kunnen worden gemaakt op basis van de lijst met leveringen of binnen een workflow via een [leveringsactiviteit](../../workflow/using/delivery.md) .

Workflows bieden ook specifieke leveringsactiviteiten op basis van het type kanaal dat u wilt gebruiken. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

### Terugkerende levering {#recurring-delivery}

Met een **terugkerende levering** kunt u elke keer dat de activiteit wordt uitgevoerd, een nieuwe levering maken. Zo voorkomt u dat u een nieuwe levering moet maken voor terugkerende taken.

Als u dit soort activiteiten bijvoorbeeld eens per maand uitvoert, krijgt u na een jaar 12 leveringen.

De terugkomende leveringen worden gecreeerd binnen werkschema&#39;s via de [Terugkomende leveringsactiviteit](../../workflow/using/recurring-delivery.md). Een voorbeeld van deze activiteit die wordt gebruikt wordt voorgesteld in deze sectie: [Een terugkerende levering maken in een doelworkflow](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Doorlopende levering {#continuous-delivery}

Met een **doorlopende levering** kunt u nieuwe ontvangers toevoegen aan een bestaande levering, zodat u niet telkens een nieuwe levering hoeft te maken wanneer deze wordt uitgevoerd.

Als een informatie in de levering verandert (inhoud, naam, enz.), wordt een nieuw leveringsvoorwerp gecreeerd bij de leveringsuitvoering. Als er geen informatie is gewijzigd, wordt hetzelfde leveringsobject opnieuw gebruikt en worden de logbestanden voor levering en bijhouden toegevoegd aan hetzelfde object.

Als voorbeeld, als u dit type van activiteit eens per maand in werking stelt, zult u eindigen met één enkele levering na een jaar (vooropgesteld u geen verandering in de levering).

De ononderbroken leveringen worden gecreeerd binnen werkschema&#39;s via de [Ononderbroken leveringsactiviteit](../../workflow/using/continuous-delivery.md).
