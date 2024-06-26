---
product: campaign
title: Communicatiekanalen
description: Maak leveringen om gepersonaliseerde berichten via verschillende kanalen te verzenden
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 8fbfc211c4e791b324c34d3d180daa7597c00c7f
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 10%

---

# Communicatiekanalen{#communication-channels}

Met Adobe Campaign kunt u kanaalcampagnes verzenden, waaronder e-mails, SMS, LIJN-berichten, pushmeldingen en directe mails, en de doeltreffendheid van deze campagnes meten met behulp van verschillende speciale [rapporten](../../reporting/using/delivery-reports.md). Deze berichten worden ontworpen en verzonden door leveringen, en kunnen voor elke ontvanger worden gepersonaliseerd.

De kernfuncties omvatten het richten, het bepalen en het personaliseren van berichten, de uitvoering van mededelingen, en de bijbehorende operationele rapporten. Het belangrijkste functionele toegangspunt is de leveringstovenaar. Dit toegangspunt leidt tot meerdere mogelijkheden die door Adobe Campaign worden gedekt.

>[!NOTE]
>
>Adobe Campaign beschikt over een set gereedschappen om de prestaties te controleren en het verzenden van e-mail te optimaliseren. Lees meer in [deze sectie](about-deliverability.md).

Het verzenden van leveringen kan worden geautomatiseerd door de levering voor te bereiden en/of te verzenden tijdens een workflow. Raadpleeg voor meer informatie over activiteiten van het type levering in workflows de [deze sectie](../../workflow/using/about-action-activities.md).

Adobe Campaign biedt de volgende leveringskanalen:

1. **Email channel**: Met e-mailleveringen kunt u persoonlijke e-mails sturen naar de doelgroep. Zie [E-mailkanaal](about-email-channel.md).
1. **Direct mailkanaal**: Met direct mail kunt u een extractiebestand genereren dat gegevens over de doelpopulatie bevat. Zie [Over direct-mailkanaal](about-direct-mail-channel.md).
1. **Mobiel kanaal**: Met leveringen op mobiele kanalen kunt u persoonlijke sms- of lijnberichten naar de doelgroep sturen. Zie [SMS-kanaal](sms-channel.md).
1. **Mobiel toepassingskanaal**: met de levering van mobiele apps kunt u meldingen verzenden naar iOS- en Android-systemen. Zie de [Mobiel toepassingskanaal](about-mobile-app-channel.md) hoofdstuk.

   Andere kanalen worden beschreven op [deze sectie](#other-channels).

   >[!NOTE]
   >
   >Het aantal beschikbare kanalen is afhankelijk van uw contract. Controleer hiervoor uw licentieovereenkomst.

Leveringen kunnen worden uitgevoerd **online** (via e-mail, een van de mobiele kanalen en pushberichten), en **offline** (direct-mailkanaal).

Afhankelijk van het kanaal, kunnen de leveringswijzen zijn:

* Directe levering van massa via Adobe Campaign (standaardmodus voor e-mailkanaal).
* Externe levering via een gespecialiseerde operator die het uitvoerbestand krijgt dat wordt gegenereerd door de wizard voor levering (standaardmodus voor direct-mailkanaal).

Externe accounts worden geconfigureerd via de **[!UICONTROL Administration > Platform > External accounts]** knooppunt. Deze configuratie moet alleen door deskundige gebruikers worden uitgevoerd.

## E-mailleveringen {#email-deliveries}

De [Email channel](about-email-channel.md) is een van de kernkanalen in Adobe Campaign, zodat u persoonlijke e-mails kunt plannen en verzenden naar specifieke doelgroepen.

U kunt verschillende typen e-mailberichten verzenden:

* E-mailberichten voor één verzending: e-mails die u één keer naar een bepaald doel kunt verzenden. Deze worden gewoonlijk gebruikt om een specifieke inhoud te promoten die maar één keer wordt voorbereid en verzonden (nieuwsbrief, promotiemail, enz.).
* Herhalende e-mails: in een campagne verzendt u regelmatig dezelfde e-mail en aggregeert u elke verzending en de bijbehorende rapporten op gezette tijden. Dezelfde e-mail wordt verzonden, maar doorgaans naar een ander doel, op basis van het in aanmerking komende doel voor de dag van de verzending. Een veelvoorkomend voorbeeld is een e-mailbericht voor verjaardagen. Raadpleeg voor meer informatie hierover [Terugkerende leveringen](../../workflow/using/recurring-delivery.md).
* Transactiee-mails: eenheidse e-mails die worden geactiveerd op basis van het gedrag van uw klanten. Zie [Transactieberichten](../../message-center/using/about-transactional-messaging.md).

Raadpleeg Campagne voor meer informatie over het gebruik en de aanbevelingen van de levering [Best practices voor levering](delivery-best-practices.md).

Raadpleeg voor meer informatie over de verschillende typen leveringen [deze sectie](#types-of-deliveries).

## Mobiele leveringen {#mobile-deliveries}

Met Adobe Campaign kunt u leveren [SMS](sms-channel.md) en [REGEL](line-channel.md) berichten op mobiele apparaten.

Voor SMS-berichten kunt u alleen in tekstindeling berichten maken, wijzigen en personaliseren. Je kunt ook een voorbeeld van je SMS-berichten bekijken voordat ze worden verzonden.

Voor lijnberichten kunt u tekst of afbeeldingen en koppelingen verzenden.

Als u SMS- of lijnberichten wilt verzenden naar een mobiele telefoon die u nodig hebt:

* Een externe account geconfigureerd op de **[!UICONTROL Mobile (SMS)]** of op **[!UICONTROL LINE]** kanaal.
* Een SMS- of REGELS-leveringssjabloon die correct is gekoppeld aan deze externe account.

## Pushmeldingen {#push-notifications}

Met Adobe Campaign kunt u gepersonaliseerde en gesegmenteerde [pushmeldingen](about-mobile-app-channel.md) op mobiele iOS- en Android-apparaten, via specifieke apps. Nadat configuratie- en integratiestappen zijn uitgevoerd, kunnen iOS- en Android-leveringen worden gemaakt en verzonden. U kunt ook veelzijdige meldingen ontwerpen met afbeeldingen of video&#39;s.

## Direct mail {#direct-mail}

[Directe post](about-direct-mail-channel.md) is een offlinekanaal waarmee u het bestand dat door directe-mailproviders wordt vereist, kunt aanpassen en genereren. Het biedt u de mogelijkheid om online en offline kanalen in uw klanttrajecten te combineren.

Met online kanalen kunt u uw berichten (e-mail, sms, levering van mobiele apps, enzovoort) maken en ze vanuit Adobe Campaign direct naar uw doelgroep verzenden. Bij offline kanalen is dit anders. Wanneer u een direct-maillevering voorbereidt, genereert Adobe Campaign een bestand met alle doelprofielen en de gekozen contactinformatie (bijvoorbeeld postadres). U kunt dit bestand dan naar uw direct-mailprovider sturen, die voor de werkelijke verzending zorgt.

## Andere kanalen {#other-channels}

Adobe Campaign biedt een sjabloon voor telefonische levering, die wordt gebruikt om externe leveringen te maken. Als u dit kanaal gebruikt, moet u speciale methoden instellen voor het verwerken van uitvoerbestanden. Configuratiestappen zijn hetzelfde als voor [Direct mailkanaal](about-direct-mail-channel.md).

>[!NOTE]
>
>Het telefoonkanaal is niet beschikbaar buiten de doos. Voor de implementatie ervan is overleg met de Adobe of betrokkenheid van een Adobe-partner vereist. Neem contact op met uw Adobe voor meer informatie.

Bovendien gebruiken de &quot;Andere&quot;typeleveringen een specifiek technisch malplaatje dat geen proces uitvoert: dit laat hen marketing acties beheren die buiten het platform van Adobe Campaign worden uitgevoerd.

Dit kanaal heeft geen specifiek mechanisme. Het is een generisch kanaal dat zijn eigen externe rekening heeft die optie, het type van leveringsmalplaatje en activiteit van het campagnewerkschema verpletteren, enkel zoals een ander communicatiekanaal beschikbaar in Adobe Campaign.

Dit kanaal is alleen bedoeld voor beschrijvende doeleinden, bijvoorbeeld om leveringen te definiëren waarvoor u het doel van een campagne die is uitgevoerd in een ander programma dan Adobe Campaign, wilt bijhouden.

## Soorten leveringen{#types-of-deliveries}

Er zijn drie typen leveringsobjecten in campagne:

### Eén levering {#single-delivery}

A **bezorging** is een zelfstandig leveringsobject dat één keer wordt uitgevoerd. Het kan worden gedupliceerd, opnieuw worden bereid, maar zolang het in zijn definitieve staat (geannuleerd, gestopt, gebeëindigd) is, kan het niet opnieuw worden gebruikt.

Leveringen kunnen worden gemaakt op basis van de lijst met leveringen of binnen een workflow via een [Aflevering](../../workflow/using/delivery.md) activiteit.

Workflows bieden ook specifieke leveringsactiviteiten op basis van het type kanaal dat u wilt gebruiken. Raadpleeg voor meer informatie over deze activiteiten [deze sectie](../../workflow/using/cross-channel-deliveries.md).

### Terugkerende levering {#recurring-delivery}

A **terugkerende levering** Hiermee kunt u telkens een nieuwe levering maken wanneer de activiteit wordt uitgevoerd. Zo voorkomt u dat u een nieuwe levering moet maken voor terugkerende taken.

Als u dit soort activiteiten bijvoorbeeld eens per maand uitvoert, krijgt u na een jaar 12 leveringen.

Terugkerende leveringen worden binnen workflows gemaakt via de [Terugkerende leveringsactiviteit](../../workflow/using/recurring-delivery.md). Een voorbeeld van deze activiteit die wordt gebruikt wordt voorgesteld in deze sectie: [Een terugkerende levering maken in een doelworkflow](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Doorlopende levering {#continuous-delivery}

A **continue levering** Hiermee kunt u nieuwe ontvangers toevoegen aan een bestaande levering, zodat u niet telkens een nieuwe levering hoeft te maken wanneer deze wordt uitgevoerd.

Als een informatie in de levering verandert (inhoud, naam, enz.), wordt een nieuw leveringsvoorwerp gecreeerd bij de leveringsuitvoering. Als er geen informatie is gewijzigd, wordt hetzelfde leveringsobject opnieuw gebruikt en worden de logbestanden voor levering en bijhouden toegevoegd aan hetzelfde object.

Als voorbeeld, als u dit type van activiteit eens per maand in werking stelt, zult u eindigen met één enkele levering na een jaar (vooropgesteld u geen verandering in de levering).

Doorlopende leveringen worden binnen workflows gemaakt via de [Continue leveringsactiviteit](../../workflow/using/continuous-delivery.md).
