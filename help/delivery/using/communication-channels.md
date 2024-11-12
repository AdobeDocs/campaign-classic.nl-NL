---
product: campaign
title: Communicatiekanalen
description: Maak leveringen om gepersonaliseerde berichten via verschillende kanalen te verzenden
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 41296a0acaee93d31874bf58287e51085c6c1261
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 8%

---

# Communicatiekanalen{#communication-channels}

Met Adobe Campaign, kunt u kanaalcampagnes met inbegrip van e-mail, SMS, de berichten van de LIJN, de Duw berichten en directe berichten verzenden, en hun doeltreffendheid meten gebruikend diverse specifieke [ rapporten ](../../reporting/using/delivery-reports.md). Deze berichten worden ontworpen en verzonden door leveringen, en kunnen voor elke ontvanger worden gepersonaliseerd.

De kernfuncties omvatten het richten, het bepalen en het personaliseren van berichten, de uitvoering van mededelingen, en de bijbehorende operationele rapporten. Het belangrijkste functionele toegangspunt is de leveringsmedewerker. Dit toegangspunt leidt tot meerdere mogelijkheden die door Adobe Campaign worden gedekt.

>[!NOTE]
>
>Adobe Campaign beschikt over een set gereedschappen om de prestaties te controleren en het verzenden van e-mail te optimaliseren. Lees meer in [deze sectie](about-deliverability.md).

Het verzenden van leveringen kan worden geautomatiseerd door de levering voor te bereiden en/of te verzenden tijdens een workflow. Voor meer op levering-type activiteiten in werkschema&#39;s, verwijs naar [ deze sectie ](../../workflow/using/about-action-activities.md).

Adobe Campaign biedt de volgende leveringskanalen:

1. **E-mailkanaal**: De e-mailleveringen laten u gepersonaliseerde e-mails naar de doelbevolking verzenden. Verwijs naar [ over e-mailkanaal ](about-email-channel.md).
1. **Directe postkanaal**: De directe postleveringen laten u een extractiedossier produceren dat gegevens over de doelbevolking bevat. Verwijs naar [ over direct-mailkanaal ](about-direct-mail-channel.md).
1. **Mobiel kanaal**: de leveringen op mobiele kanalen laten u gepersonaliseerde SMS of de berichten van de LIJN naar de doelbevolking verzenden. Verwijs naar [ het kanaal van SMS ](sms-channel.md).
1. **Mobiel toepassingskanaal**: De mobiele App leveringen laten u berichten naar de systemen van iOS en van Android verzenden. Verwijs naar het [ Mobiele app kanaal ](about-mobile-app-channel.md) hoofdstuk.

   Andere kanalen worden beschreven op [ deze sectie ](#other-channels).

   >[!NOTE]
   >
   >Het aantal beschikbare kanalen is afhankelijk van uw contract. Controleer hiervoor uw licentieovereenkomst.

De leveringen kunnen **online** (via e-mail, één van de mobiele kanalen en dupberichten) worden uitgevoerd, en **offline** (direct postkanaal).

Afhankelijk van het kanaal, kunnen de leveringswijzen zijn:

* Directe levering van massa via Adobe Campaign (standaardmodus voor e-mailkanaal).
* Externe levering via een gespecialiseerde exploitant die het outputdossier wordt gegeven door de leveringsmedewerker (standaardwijze voor direct postkanaal) wordt geproduceerd.

Externe accounts worden geconfigureerd via het knooppunt **[!UICONTROL Administration > Platform > External accounts]** . Deze configuratie moet alleen door deskundige gebruikers worden uitgevoerd.

## E-mailleveringen {#email-deliveries}

Het [ E-mailkanaal ](about-email-channel.md) is één van de kernkanalen in Adobe Campaign, toestaand u om gepersonaliseerde e-mails aan specifieke doelstellingen te plannen en te verzenden.

U kunt verschillende typen e-mailberichten verzenden:

* E-mailberichten voor één verzending: e-mails die u één keer naar een bepaald doel kunt verzenden. Deze worden gewoonlijk gebruikt om een specifieke inhoud te promoten die maar één keer wordt voorbereid en verzonden (nieuwsbrief, promotiemail, enz.).
* Herhalende e-mails: in een campagne verzendt u regelmatig dezelfde e-mail en aggregeert u elke verzending en de bijbehorende rapporten op gezette tijden. Dezelfde e-mail wordt verzonden, maar doorgaans naar een ander doel, op basis van het in aanmerking komende doel voor de dag van de verzending. Een veelvoorkomend voorbeeld is een e-mailbericht voor verjaardagen. Voor meer op dit, verwijs naar [ Terugkomende leveringen ](../../workflow/using/recurring-delivery.md).
* Transactiee-mails: eenheidse e-mails die worden geactiveerd op basis van het gedrag van uw klanten. Verwijs naar [ Transactioneel overseinen ](../../message-center/using/about-transactional-messaging.md).

Om over leveringsgebruik en aanbevelingen te leren, raadpleeg de beste praktijken van de Lading van de Campagne [ ](delivery-best-practices.md).

Voor meer op de verschillende types van leveringen, verwijs naar [ deze sectie ](#types-of-deliveries).

## Mobiele leveringen {#mobile-deliveries}

Adobe Campaign staat u toe om [ SMS ](sms-channel.md) en [ LIJN ](line-channel.md) berichten op mobiele telefoons te leveren.

Voor SMS-berichten kunt u alleen in tekstindeling berichten maken, wijzigen en personaliseren. Je kunt ook een voorbeeld van je SMS-berichten bekijken voordat ze worden verzonden.

Voor lijnberichten kunt u tekst of afbeeldingen en koppelingen verzenden.

Als u SMS- of lijnberichten wilt verzenden naar een mobiele telefoon die u nodig hebt:

* Een externe account die is geconfigureerd op het **[!UICONTROL Mobile (SMS)]** -kanaal of op het **[!UICONTROL LINE]** -kanaal.
* Een SMS- of REGELS-leveringssjabloon die correct is gekoppeld aan deze externe account.

## Pushmeldingen {#push-notifications}

Adobe Campaign staat u toe om gepersonaliseerde en gesegmenteerde [ dupberichten ](about-mobile-app-channel.md) op de mobiele apparaten van iOS en Android, door specifieke apps te verzenden. Nadat configuratie- en integratiestappen zijn uitgevoerd, kunnen iOS- en Android-leveringen worden gemaakt en verzonden. U kunt ook veelzijdige meldingen ontwerpen met afbeeldingen of video&#39;s.

## Direct mail {#direct-mail}

[ Directe post ](about-direct-mail-channel.md) is een off-line kanaal dat u toestaat om het dossier te personaliseren en te produceren dat door directe postleveranciers wordt vereist. Het biedt u de mogelijkheid om online en offline kanalen in uw klanttrajecten te combineren.

Met onlinekanalen kunt u berichten maken (e-mail, SMS, levering van mobiele apps, enz.) en deze rechtstreeks vanuit Adobe Campaign naar uw publiek verzenden. Bij offline kanalen is dit anders. Wanneer u een direct-maillevering voorbereidt, genereert Adobe Campaign een bestand met alle doelprofielen en de gekozen contactinformatie (bijvoorbeeld postadres). U kunt dit bestand dan naar uw direct-mailprovider sturen, die voor de werkelijke verzending zorgt.

## Andere kanalen {#other-channels}

Adobe Campaign biedt een sjabloon voor telefonische levering, die wordt gebruikt om externe leveringen te maken. Als u dit kanaal gebruikt, moet u speciale methoden instellen voor het verwerken van uitvoerbestanden. De stappen van de configuratie zijn het zelfde als voor [ Directe postkanaal ](about-direct-mail-channel.md).

>[!NOTE]
>
>Het telefoonkanaal is niet beschikbaar buiten de doos. Voor de implementatie ervan moet Adobe Consulting of een Adobe-partner worden betrokken. Neem contact op met uw Adobe voor meer informatie.

Bovendien gebruiken de &quot;Andere&quot;typeleveringen een specifiek technisch malplaatje dat geen proces uitvoert: dit laat hen marketing acties beheren die buiten het platform van Adobe Campaign worden uitgevoerd.

Dit kanaal heeft geen specifiek mechanisme. Het is een generisch kanaal dat zijn eigen externe rekening heeft die optie, het type van leveringsmalplaatje en activiteit van het campagnewerkschema verpletteren, enkel zoals een ander communicatiekanaal beschikbaar in Adobe Campaign.

Dit kanaal is alleen bedoeld voor beschrijvende doeleinden, bijvoorbeeld om leveringen te definiëren waarvoor u het doel van een campagne die is uitgevoerd in een ander programma dan Adobe Campaign, wilt bijhouden.

## Soorten leveringen{#types-of-deliveries}

Er zijn drie typen leveringsobjecten in campagne:

### Eén levering {#single-delivery}

A **levering** is een standalone leveringsvoorwerp dat eens wordt uitgevoerd. Het kan worden gedupliceerd, opnieuw worden bereid, maar zolang het in zijn definitieve staat (geannuleerd, gestopt, gebeëindigd) is, kan het niet opnieuw worden gebruikt.

De leveringen kunnen of van de lijst van leveringen, of binnen een werkschema via de activiteit van de a [ Levering ](../../workflow/using/delivery.md) worden gecreeerd.

Workflows bieden ook specifieke leveringsactiviteiten op basis van het type kanaal dat u wilt gebruiken. Voor meer op deze activiteiten, verwijs naar [ deze sectie ](../../workflow/using/cross-channel-deliveries.md).

### Terugkerende levering {#recurring-delivery}

A **terugkomende levering** laat u een nieuwe levering tot stand brengen telkens als de activiteit wordt uitgevoerd. Zo voorkomt u dat u een nieuwe levering moet maken voor terugkerende taken.

Als u dit soort activiteiten bijvoorbeeld eens per maand uitvoert, krijgt u na een jaar 12 leveringen.

De terugkomende leveringen worden gecreeerd binnen werkschema&#39;s via de [ Terugkomende leveringsactiviteit ](../../workflow/using/recurring-delivery.md). Een voorbeeld van deze activiteit die wordt gebruikt wordt voorgesteld in deze sectie: [ Creërend een terugkomende levering in een het richten werkschema ](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Doorlopende levering {#continuous-delivery}

A **ononderbroken levering** laat u nieuwe ontvangers aan een bestaande levering toevoegen, die vermijdt het moeten een nieuwe levering tot stand brengen telkens als het wordt uitgevoerd.

Als een informatie in de levering verandert (inhoud, naam, enz.), wordt een nieuw leveringsvoorwerp gecreeerd bij de leveringsuitvoering. Als er geen informatie is gewijzigd, wordt hetzelfde leveringsobject opnieuw gebruikt en worden de logbestanden voor levering en bijhouden toegevoegd aan hetzelfde object.

Als voorbeeld, als u dit type van activiteit eens per maand in werking stelt, zult u eindigen met één enkele levering na een jaar (vooropgesteld u geen verandering in de levering).

De ononderbroken leveringen worden gecreeerd binnen werkschema&#39;s via de [ Ononderbroken leveringsactiviteit ](../../workflow/using/continuous-delivery.md).
