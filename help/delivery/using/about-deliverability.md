---
product: campaign
title: Ga aan de slag met de prestaties in de campagne
description: Tips en trucs voor levering
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 8%

---

# Wat is afleverbaarheid?{#about-deliverability}



Met de prestaties kunt u het succes meten van uw campagnes die de inbox van uw ontvangers bereiken zonder te stuiteren, of als spam worden gemerkt. [Meer weten waarom het van belang is om te leveren](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

Meer bepaald, verwijst de e-maillevering naar de reeks eigenschappen die de capaciteit van een bericht bepalen om zijn bestemming, via een persoonlijk e-mailadres, binnen een korte tijd, en met de verwachte kwaliteit in termen van inhoud en formaat te bereiken.

Voor een diepgaander inzicht in wat de te leveren prestaties zijn en meer te leren over zeer belangrijke leverbaarheidsvoorwaarden, concepten, en benaderingen, verwijs naar [Adobe Handleiding voor beste praktijken voor aflevering](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl).

## Hoe te om leverbaarheid te verbeteren {#deliverability-key-points}

De leveringsproblemen houden gewoonlijk verband met maatregelen van bescherming tegen spam die door Internet dienstverleners en de beheerders van de postserver worden uitgevoerd.

* Voor algemene aanbevelingen over het ontwerpen van succesvolle e-mailmarketingcampagnes raadpleegt u [Leverbaarheidsstrategie en definitie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* Adobe raadt u aan de beste praktijken in deze sectie te gebruiken voor meer specifieke aanbevelingen voor het optimaliseren van de leverbaarheid van Adobe Campaign-e-mails.

>[!NOTE]
>
>Omdat ISPs verplicht is voortdurend nieuwe verfijnde het filtreren technieken te ontwikkelen om hun klanten tegen spammers te beschermen, wordt de e-maillevering gekenmerkt door voortdurend veranderende criteria en regels. Zorg ervoor dat u naar de [Adobe Handleiding voor beste praktijken voor aflevering](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl) die regelmatig wordt bijgewerkt.

### Leverbaarheidsgraad

Het leverbaarheidstarief is het aantal berichten die de ontvangers&#39; in dozen vergeleken bij het aantal berichten raakten die werden geleverd. Om de leverbaarheid te verbeteren, kunt u aan verhoging dit tarief werken.

Bij Adobe Campaign hangt het leverbrengingscijfer af van een groot aantal factoren, met name:

* Correcte configuratie van uw instanties: Neem contact op met uw Adobe-vertegenwoordiger voor hulp.
* Legitieme netwerkconfiguratie: zie [deze sectie](optimize-delivery.md#network-config) en [Instellen en strategie van domeinen](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* Uw IP adresreputatie: zie [IP-strategie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Kwaliteit van de beoogde adressen: zie [Quarantainebeheer](optimize-delivery.md#quarantine-management).
* Laag [klachten](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) en [harde stoot](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces) tarieven.
* Uw berichtinhoud: zie [De e-mailinhoud beheren](control-message-content.md).
* Berichtverificatie (SPF, DKIM, DMARC): zie [deze sectie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* Afkorting van afzender: om te leren hoe belangrijkste ISPs een afzenderreputatie evalueert, zie [deze sectie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Hulpprogramma&#39;s voor het leveren van campagnes {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign biedt verschillende tools om de prestaties van uw platform bij te houden en te verbeteren. Op deze pagina worden ook de belangrijkste beginselen gemarkeerd die u in gedachten moet houden om de prestaties te optimaliseren wanneer u campagne gebruikt.

### Uw bericht zorgvuldig samenstellen

Wanneer het vormen van, het ontwerpen van, en het testen van uw bericht, zorg ervoor u de beste praktijken volgt die in de hieronder vermelde secties worden vermeld. Door gebruik te maken van alle functies die Adobe Campaign biedt, kunt u de leverbaarheid verbeteren.

* [Best practices voor verzending](delivery-best-practices.md)
* [De e-mailinhoud beheren](control-message-content.md)
* [Inboxrendering](inbox-rendering.md)
* [Een proef verzenden](steps-validating-the-delivery.md#sending-a-proof)

### Verifieer toestemming door dubbele opt-in {#double-opt-in}

Om het verzenden van berichten naar ongeldige adressen te vermijden, onjuiste mededelingen te beperken en afzenderreputatie te verbeteren, adviseert Adobe het uitvoeren van een dubbel opt-in mechanisme. Met deze methode kunt u ervoor zorgen dat de ontvangers zich bewust hebben geabonneerd.

Zie [Een lidmaatschapsformulier maken met dubbele opt-in](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in) voor meer informatie.

Raadpleeg voor meer informatie over aanbevolen procedures bij het verzamelen van gegevens van uw klanten de [Adobe Handleiding voor beste praktijken voor aflevering](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### Gebruik quarantainebeheer

Adobe Campaign beheert een lijst met spamklachten, harde stuitingen en zachte stuitingen die consistent voorkomen.

Om uw leverbaarheid te beschermen, worden de ontvangers van wie adressen op die lijst zijn uitgesloten door gebrek van alle toekomstige leveringen, omdat het verzenden naar deze contacten uw verzendende reputatie zou kunnen schaden.

Sommige internetproviders beschouwen e-mails automatisch als spam als het aantal ongeldige adressen te hoog is. Met quarantaine kunt u dus voorkomen dat u door deze providers aan de lijst van gewezen personen wordt toegevoegd.

Raadpleeg de volgende secties voor meer informatie hierover:

* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Quarantainebeheer begrijpen](understanding-quarantine-management.md)
* [Quarantine versus lijst van gewezen personen](understanding-quarantine-management.md#quarantine-vs-denylist)

### Gereedschappen voor bewaking en rapportage gebruiken

Gebruik de functies die Adobe Campaign biedt om de prestaties te controleren.

Met Adobe Campaign kunt u controleren hoe uw leveringen presteren aan de hand van een reeks ingebouwde real-time indicatoren en rapporten voor een beter inzicht in uw leveringen.

Raadpleeg de volgende secties voor meer informatie hierover:

* [Te leveren items controleren](monitoring-deliverability.md)
* [Aan de slag met verzendingscontrole](about-delivery-monitoring.md)
* [Ga aan de slag met ingebouwde campagnerapporten](../../reporting/using/about-campaign-built-in-reports.md)
