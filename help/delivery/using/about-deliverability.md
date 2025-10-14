---
product: campaign
title: Ga aan de slag met de prestaties in Campagne
description: Tips en trucs voor het leveren van informatie
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
role: User
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 7%

---

# Wat is afleverbaarheid?{#about-deliverability}

Met de prestaties kunt u het succes meten van uw campagnes die de inbox van uw ontvangers bereiken zonder te stuiteren, of als spam worden gemerkt. [&#x200B; leer waarom de leverbaarheid &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters) van belang is.

Meer bepaald, verwijst de e-maillevering naar de reeks eigenschappen die de capaciteit van een bericht bepalen om zijn bestemming, via een persoonlijk e-mailadres, binnen een korte tijd, en met de verwachte kwaliteit in termen van inhoud en formaat te bereiken.

Voor een diepere duik op wat de leverbaarheid is en meer op zeer belangrijke leveringsvoorwaarden, concepten, en benaderingen te leren, verwijs naar de [&#x200B; Gids van de Beste praktijken van de Levering van Adobe &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl).

## Hoe te om leverbaarheid te verbeteren {#deliverability-key-points}

De leveringsproblemen houden gewoonlijk verband met maatregelen van bescherming tegen spam die door Internet dienstverleners en de beheerders van de postserver worden uitgevoerd.

* Voor algemene aanbevelingen op hoe te om succesvolle e-mail marketing campagnes te ontwerpen, verwijs naar [&#x200B; de strategie en de definitie van de Levering &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* Adobe raadt u aan de beste praktijken in deze sectie te gebruiken voor specifieke aanbevelingen voor het optimaliseren van de leverbaarheid van uw Adobe Campaign-e-mails.

>[!NOTE]
>
>Omdat ISPs verplicht is voortdurend nieuwe verfijnde het filtreren technieken te ontwikkelen om hun klanten tegen spammers te beschermen, wordt de e-maillevering gekenmerkt door voortdurend veranderende criteria en regels. Zorg ervoor u naar de [&#x200B; Gids van de Beste praktijken van de Levering van Adobe &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl) verwijst die regelmatig wordt bijgewerkt.

### Leverbaarheidsgraad

Het leverbaarheidstarief is het aantal berichten die de inboxes van ontvangers vergeleken bij het aantal berichten raakten die werden geleverd. Om de leverbaarheid te verbeteren, kunt u werken aan het verhogen van dit tarief.

Bij Adobe Campaign hangt het leverbrengingscijfer af van een groot aantal factoren, met name:

* Correcte configuratie van uw instanties: neem contact op met uw Adobe-vertegenwoordiger voor hulp.
* Legitieme netwerkconfiguratie: zie [&#x200B; de opstelling en de strategie van het Domein &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* Uw IP adresreputatie: zie [&#x200B; IP strategie &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* De lage [&#x200B; klachten &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) en [&#x200B; harde stuiteren &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces) tarieven.
* Uw berichtinhoud: zie [&#x200B; Controle de e-mailinhoud &#x200B;](control-message-content.md).
* De authentificatie van het bericht (SPF, DKIM, DMARC): zie [&#x200B; deze sectie &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* De reputatie van de afzender: om te leren hoe hoofd ISPs een afzenderreputatie evalueert, zie [&#x200B; deze sectie &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Hulpprogramma&#39;s voor het leveren van campagnes {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign biedt verschillende tools om de prestaties van uw platform bij te houden en te verbeteren. Op deze pagina worden ook de belangrijkste beginselen gemarkeerd die u in gedachten moet houden om de prestaties te optimaliseren wanneer u campagne gebruikt.

### Uw bericht zorgvuldig samenstellen

Wanneer het vormen van, het ontwerpen van, en het testen van uw bericht, zorg ervoor u de beste praktijken volgt die in de hieronder vermelde secties worden vermeld. Door gebruik te maken van alle functies die Adobe Campaign biedt, kunt u de leverbaarheid verbeteren.

* [&#x200B; beste praktijken van de Levering &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html){target="_blank"}.
* [De e-mailinhoud beheren](control-message-content.md)
* [Inboxrendering](inbox-rendering.md)
* [Een proef verzenden](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html){target="_blank"}

### Verifieer toestemming door dubbele opt-in {#double-opt-in}

Om te voorkomen dat berichten naar ongeldige adressen worden verzonden, onjuiste communicatie wordt beperkt en de reputatie van de afzender wordt verbeterd, raadt Adobe aan een dubbele opt-in-mechanisme in te voeren. Met deze methode kunt u ervoor zorgen dat de ontvangers zich bewust hebben geabonneerd.

Zie [Een lidmaatschapsformulier maken met dubbele opt-in](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in) voor meer informatie.

Voor meer op beste praktijken wanneer het verzamelen van gegevens van uw klanten, verwijs naar de [&#x200B; Gids van de Beste praktijken van de Levering van Adobe &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

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

Met Adobe Campaign kunt u controleren hoe uw leveringen presteren aan de hand van een reeks ingebouwde real-time indicatoren en rapporten voor een verbeterde insight voor uw leveringen.

Raadpleeg de volgende secties voor meer informatie hierover:

* [Te leveren items bewaken](monitoring-deliverability.md)
* [Aan de slag met leveringscontrole](about-delivery-monitoring.md)
* [Ga aan de slag met ingebouwde campagnerapporten](../../reporting/using/about-campaign-built-in-reports.md)
