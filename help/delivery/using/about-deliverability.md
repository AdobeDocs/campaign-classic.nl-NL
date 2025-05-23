---
product: campaign
title: Ga aan de slag met de prestaties in Campagne
description: Tips en trucs voor het leveren van informatie
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
role: User
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 7%

---

# Wat is afleverbaarheid?{#about-deliverability}

Met de prestaties kunt u het succes meten van uw campagnes die de inbox van uw ontvangers bereiken zonder te stuiteren, of als spam worden gemerkt. [ leer waarom de leverbaarheid ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=nl-NL#why-deliverability-matters) van belang is.

Meer bepaald, verwijst de e-maillevering naar de reeks eigenschappen die de capaciteit van een bericht bepalen om zijn bestemming, via een persoonlijk e-mailadres, binnen een korte tijd, en met de verwachte kwaliteit in termen van inhoud en formaat te bereiken.

Voor een diepere duik op welke leverbaarheid is en meer op zeer belangrijke leveringsvoorwaarden, concepten, en benaderingen te leren, verwijs naar de [ Gids van de Beste praktijken van de Levering van de Adobe van de Levering van de Beste ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl).

## Hoe te om leverbaarheid te verbeteren {#deliverability-key-points}

De leveringsproblemen houden gewoonlijk verband met maatregelen van bescherming tegen spam die door Internet dienstverleners en de beheerders van de postserver worden uitgevoerd.

* Voor algemene aanbevelingen op hoe te om succesvolle e-mail marketing campagnes te ontwerpen, verwijs naar [ de strategie en de definitie van de Levering ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=nl-NL).

* Voor specifiekere aanbevelingen voor het optimaliseren van de leverbaarbaarheid van je Adobe Campaign-e-mails raadt Adobe u aan de beste praktijken in deze sectie te gebruiken.

>[!NOTE]
>
>Omdat ISPs verplicht is voortdurend nieuwe verfijnde het filtreren technieken te ontwikkelen om hun klanten tegen spammers te beschermen, wordt de e-maillevering gekenmerkt door voortdurend veranderende criteria en regels. Zorg ervoor u naar de [ Gids van de Beste praktijken van de Levering van de Adobe ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl) verwijst die regelmatig wordt bijgewerkt.

### Leverbaarheidsgraad

Het leverbaarheidstarief is het aantal berichten die de inboxes van ontvangers vergeleken bij het aantal berichten raakten die werden geleverd. Om de leverbaarheid te verbeteren, kunt u werken aan het verhogen van dit tarief.

Bij Adobe Campaign hangt het leverbrengingscijfer af van een groot aantal factoren, met name:

* Correcte configuratie van uw instanties: neem contact op met uw Adobe voor hulp.
* Legitieme netwerkconfiguratie: zie [ de opstelling en de strategie van het Domein ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=nl-NL#domain-setup-and-strategy).
* Uw IP adresreputatie: zie [ IP strategie ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=nl-NL#ip-strategy).
* De lage [ klachten ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html?lang=nl-NL) en [ harde stuiteren ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html?lang=nl-NL#hard-bounces) tarieven.
* Uw berichtinhoud: zie [ Controle de e-mailinhoud ](control-message-content.md).
* De authentificatie van het bericht (SPF, DKIM, DMARC): zie [ deze sectie ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=nl-NL#authentication).
* De reputatie van de afzender: om te leren hoe hoofd ISPs een afzenderreputatie evalueert, zie [ deze sectie ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html?lang=nl-NL).

## Hulpprogramma&#39;s voor het leveren van campagnes {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign biedt verschillende tools om de prestaties van uw platform bij te houden en te verbeteren. Op deze pagina worden ook de belangrijkste beginselen gemarkeerd die u in gedachten moet houden om de prestaties te optimaliseren wanneer u campagne gebruikt.

### Uw bericht zorgvuldig samenstellen

Wanneer het vormen van, het ontwerpen van, en het testen van uw bericht, zorg ervoor u de beste praktijken volgt die in de hieronder vermelde secties worden vermeld. Door gebruik te maken van alle functies die Adobe Campaign biedt, kunt u de leverbaarheid verbeteren.

* [Best practices voor verzending](delivery-best-practices.md)
* [De e-mailinhoud beheren](control-message-content.md)
* [Inboxrendering](inbox-rendering.md)
* [Een proefafdruk verzenden](steps-validating-the-delivery.md#sending-a-proof)

### Verifieer toestemming door dubbele opt-in {#double-opt-in}

Om het verzenden van berichten naar ongeldige adressen te vermijden, onjuiste mededelingen te beperken en afzenderreputatie te verbeteren, adviseert de Adobe om een dubbel opt-in mechanisme in te voeren. Met deze methode kunt u ervoor zorgen dat de ontvangers zich bewust hebben geabonneerd.

Zie [Een lidmaatschapsformulier maken met dubbele opt-in](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in) voor meer informatie.

Voor meer op beste praktijken wanneer het verzamelen van gegevens van uw klanten, verwijs naar de [ Gids van de Beste praktijken van de Levering van de Adobe Beste ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html?lang=nl-NL#data-quality-and-hygiene).

### Gebruik quarantainebeheer

Adobe Campaign beheert een lijst met spamklachten, harde stuitingen en zachte stuitingen die consistent voorkomen.

Om uw leverbaarheid te beschermen, worden de ontvangers van wie adressen op die lijst zijn uitgesloten door gebrek van alle toekomstige leveringen, omdat het verzenden naar deze contacten uw verzendende reputatie zou kunnen schaden.

Sommige internetproviders beschouwen e-mails automatisch als spam als het aantal ongeldige adressen te hoog is. Met quarantaine kunt u dus voorkomen dat deze providers aan de lijst van gewezen personen worden toegevoegd.

Raadpleeg de volgende secties voor meer informatie hierover:

* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Quarantainebeheer begrijpen](understanding-quarantine-management.md)
* [Quarantine versus lijst van gewezen personen](understanding-quarantine-management.md#quarantine-vs-denylist)

### Gereedschappen voor bewaking en rapportage gebruiken

Gebruik de functies die Adobe Campaign biedt om de prestaties te controleren.

Met Adobe Campaign kunt u controleren hoe uw leveringen presteren aan de hand van een reeks ingebouwde real-time indicatoren en rapporten voor een beter inzicht in uw leveringen.

Raadpleeg de volgende secties voor meer informatie hierover:

* [Te leveren items bewaken](monitoring-deliverability.md)
* [Aan de slag met leveringscontrole](about-delivery-monitoring.md)
* [Ga aan de slag met ingebouwde campagnerapporten](../../reporting/using/about-campaign-built-in-reports.md)
