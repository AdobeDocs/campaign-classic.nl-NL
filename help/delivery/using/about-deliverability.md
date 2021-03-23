---
solution: Campaign Classic
product: campaign
title: Over de beschikbaarheid in Campagne
description: Tips en trucs voor levering
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 0420de856d1506ab92d8f0e0824bf439e0ac7dc7
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 5%

---


# Wat is leverbaar{#about-deliverability}

Met de prestaties kunt u het succes meten van uw campagnes die de inbox van uw ontvangers bereiken zonder te stuiteren, of als spam worden gemerkt. [Leer waarom leverbaarheid van belang](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters) is.

Meer bepaald, verwijst de e-maillevering naar de reeks eigenschappen die de capaciteit van een bericht bepalen om zijn bestemming, via een persoonlijk e-mailadres, binnen een korte tijd, en met de verwachte kwaliteit in termen van inhoud en formaat te bereiken.

Raadpleeg de [Handleiding best practice](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html) voor een dieper inzicht in wat de leverbaarbaarheid is en voor meer informatie over de belangrijkste leverbare termen, concepten en benaderingen.

## Hoe te om leverbaarheid {#deliverability-key-points} te verbeteren

De leveringsproblemen houden gewoonlijk verband met maatregelen van bescherming tegen spam die door Internet dienstverleners en de beheerders van de postserver worden uitgevoerd.

* Raadpleeg [Deliverability strategy and definition](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html) voor algemene aanbevelingen over het ontwerpen van geslaagde e-mailmarketingcampagnes.

* Adobe raadt u aan de beste praktijken in deze sectie te gebruiken voor meer specifieke aanbevelingen voor het optimaliseren van de leverbaarheid van Adobe Campaign-e-mails.

>[!NOTE]
>
>Omdat ISPs verplicht is voortdurend nieuwe verfijnde het filtreren technieken te ontwikkelen om hun klanten tegen spammers te beschermen, wordt de e-maillevering gekenmerkt door voortdurend veranderende criteria en regels. Zorg ervoor u naar [Gids van de Beste praktijken van de Levering van de Adobe verwijst ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html) die regelmatig wordt bijgewerkt.

### Leverbaarheidsgraad

Het leverbaarheidspercentage is het aantal berichten dat de inboxes van de ontvangers bereikte in vergelijking met het aantal berichten dat werd geleverd. Om de leverbaarheid te verbeteren, kunt u aan verhoging dit tarief werken.

Bij Adobe Campaign hangt het leverbrengingscijfer af van een groot aantal factoren, met name:

* Correcte configuratie van uw instanties: Neem contact op met uw Adobe-vertegenwoordiger voor hulp.
* Legitieme netwerkconfiguratie: zie [deze sectie](../../delivery/using/optimize-delivery.md#network-config) en [Domeininstelling en -strategie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* Uw IP adresreputatie: zie [IP strategie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Kwaliteit van de beoogde adressen: zie [Quarantainebeheer](../../delivery/using/optimize-delivery.md#quarantine-management).
* Lage [aantal klachten](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) en [harde stuit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces).
* Uw berichtinhoud: zie [E-mailinhoud beheren](../../delivery/using/control-message-content.md).
* Berichtverificatie (SPF, DKIM, DMARC): zie [deze sectie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* Afkorting van afzender: om te leren hoe de belangrijkste ISPs een afzenderreputatie evalueert, zie [deze sectie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Gereedschappen voor het leveren van campagnes {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign biedt verschillende tools om de prestaties van uw platform bij te houden en te verbeteren. Op deze pagina worden ook de belangrijkste beginselen gemarkeerd die u in gedachten moet houden om de prestaties te optimaliseren wanneer u campagne gebruikt.

### Uw bericht zorgvuldig samenstellen

Wanneer het vormen van, het ontwerpen van, en het testen van uw bericht, zorg ervoor u de beste praktijken volgt die in de hieronder vermelde secties worden vermeld. Door gebruik te maken van alle functies die Adobe Campaign biedt, kunt u de leverbaarheid verbeteren.

* [Best practices voor levering](../../delivery/using/delivery-best-practices.md)
* [E-mailcontent beheren](../../delivery/using/control-message-content.md)
* [Inboxrendering](../../delivery/using/inbox-rendering.md)
* [Een proef verzenden](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)

### Verifieer toestemming door dubbele opt-in {#double-opt-in}

Om het verzenden van berichten naar ongeldige adressen te vermijden, onjuiste mededelingen te beperken en afzenderreputatie te verbeteren, adviseert Adobe het uitvoeren van een dubbel opt-in mechanisme. Met deze methode kunt u ervoor zorgen dat de ontvangers zich bewust hebben geabonneerd.

Zie [Een abonnementsformulier maken met dubbele opt-in](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in) voor meer informatie.

Raadpleeg de [Handleiding best practices voor Adobe-levering](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene) voor meer informatie over de beste praktijken bij het verzamelen van gegevens van uw klanten.

### Gebruik quarantainebeheer

Adobe Campaign beheert een lijst met spamklachten, harde stuitingen en zachte stuitingen die consistent voorkomen.

Om uw leverbaarheid te beschermen, worden de ontvangers van wie adressen op die lijst zijn uitgesloten door gebrek van alle toekomstige leveringen, omdat het verzenden naar deze contacten uw verzendende reputatie zou kunnen schaden.

Sommige internetproviders beschouwen e-mails automatisch als spam als het aantal ongeldige adressen te hoog is. Met quarantaine kunt u dus voorkomen dat u door deze providers aan de lijst van gewezen personen wordt toegevoegd.

Raadpleeg de volgende secties voor meer informatie hierover:

* [Leveringsfouten begrijpen](../../delivery/using/understanding-delivery-failures.md)
* [Quarantainebeheer begrijpen](../../delivery/using/understanding-quarantine-management.md)
* [Quarantine versus lijst van gewezen personen](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

### Gereedschappen voor bewaking en rapportage gebruiken

Gebruik de functies die Adobe Campaign biedt om de prestaties te controleren.

Met Adobe Campaign kunt u controleren hoe uw leveringen presteren aan de hand van een reeks ingebouwde real-time indicatoren en rapporten voor een beter inzicht in uw leveringen.

Raadpleeg de volgende secties voor meer informatie hierover:

* [Leverbaarheid controleren](../../delivery/using/monitoring-deliverability.md)
* [Informatie over leveringscontrole](../../delivery/using/about-delivery-monitoring.md)
* [Ingebouwde Campaign-rapporten](../../reporting/using/about-campaign-built-in-reports.md)

<!--TO REMOVE
## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)-->
