---
title: Veelgestelde vragen over testen en verzenden
seo-title: Berichten valideren, verzenden en opvolgen
description: Veelgestelde vragen over Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 8ef56aa04a3ecc94e9e3dda24562760d6a93739d
workflow-type: ht
source-wordcount: '755'
ht-degree: 100%

---


# Berichten valideren, verzenden en opvolgen {#validate-send-track}

## Testen en valideren {#test-and-validate-before-sending}

Ontdek hoe u test- en validatiestappen uitvoert voordat u berichten verzendt in Adobe Campaign.

### Wat is de leveringsanalyse? {#what-is-the-delivery-analysis-}

De leveringsanalyse is de fase waarin de doelpopulatie wordt berekend en de leveringscontent wordt voorbereid. Zodra deze is voltooid, is de levering klaar om te verzenden. Raadpleeg de logboeken om te controleren of alles correct is.

[Klik hier voor meer informatie](../../delivery/using/steps-validating-the-delivery.md).

### Waarom moet ik proeven maken? {#why-should-i-create-proofs-}

Adobe raadt u ten zeerste aan proefberichten te maken om uw levering op een goedkeuringsgroep te testen voordat u deze naar het hoofddoel verzendt. U kunt dan parameters voor berichtcontent, personalisatie en levering bevestigen.

[Klik hier voor meer informatie](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof). U kunt ook [deze video](https://docs.adobe.com/content/help/nl-NL/campaign-classic-learn/tutorials/getting-started/managing-seed-and-proofs.html) bekijken.

### Hoe kunt u seed-adressen in Adobe Campaign gebruiken? {#how-to-use-seed-addresses-in-adobe-campaign-}

Seed-adressen worden gebruikt om ontvangers die niet aan de gedefinieerde doelcriteria voldoen, doelgericht te benaderen. Deze ontvangers worden aan het doel toegevoegd: ze kunnen rechtstreeks in de levering of de campagne worden geïmporteerd of gemaakt. Voor direct-mailleveringen worden deze tijdens de extractie toegevoegd en in het uitvoerdocument gemengd.

Dit heeft de volgende voordelen:

* Willekeurige vervanging van velden door data uit profielen van ontvangers: hiermee kunt u alleen het e-mailadres invoeren, bijvoorbeeld in de sectie voor het seed-adres.
* Wanneer een workflow met functies voor data management wordt gebruikt, kunnen de extra data die in leveringen worden verwerkt, op het niveau van het seed-adres worden ingevoerd om waarden af te dwingen: dit omzeilt de vervanging van willekeurige waarden.

[Klik hier voor meer informatie over seed-adressen](../../delivery/using/about-seed-addresses.md).

### Hoe kan ik een goedkeuringsproces instellen alvorens berichten te verzenden? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

Adobe raadt u ten zeerste aan een cyclus voor leveringsvalidatie in te stellen om mogelijke fouten in de berichtconfiguratie op te sporen. Zorg ervoor dat de content zo vaak als nodig wordt goedgekeurd door proeven naar testontvangers te verzenden. Telkens wanneer een wijziging wordt aangebracht, moet voor de goedkeuring van de content een proef worden verzonden.

[Klik hier voor meer informatie](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Wat is een typologieregel? {#what-is-a-typology-rule-}

Om conflicten tussen campagnes te vermijden kan Adobe Campaign diverse combinaties testen door specifieke beperkingsregels toe te passen. Dit garandeert dat de verzonden berichten het best aan de behoeften en de verwachtingen van klanten voldoen, in overeenstemming met het beleid inzake bedrijfscommunicatie.

[Klik hier voor meer informatie](../../campaign/using/about-campaign-typologies.md).

## Uw berichten verzenden {#send-your-messages}

Ontdek hoe u berichten in verschillende kanalen kunt verzenden met Adobe Campaign.

### Hoe kan ik e-mails sturen in golven? {#how-can-i-send-emails-in-waves-}

Alvorens een levering naar een grote populatie te verzenden, kunt u [golven configureren](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) om berichten in verscheidene batches te verdelen en de lading te spreiden.

### Welke zijn de belangrijkste stappen om een e-mail in Campaign te maken? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

Nadat de e-maillevering is gemaakt en gevalideerd, kunt u deze verzenden. U kunt besluiten de e-mail onmiddellijk naar het hoofddoel te verzenden of een levering voor een latere datum te plannen. Indien nodig kunt u vooraf ook de doelpopulatie inschatten.

[Klik hier voor meer informatie](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Hoe moet ik een levering plannen? {#how-to-schedule-a-delivery-}

U kunt de levering van berichten uitstellen om de levering te plannen of om de salesdruk te beheren en te voorkomen dat een populatie overbevraagd wordt.

[Klik hier voor meer informatie](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

### Kan ik een bijlage toevoegen aan e-mails? {#can-i-add-an-attachment-to-emails-}

Met Campaign Classic kunt u gepersonaliseerde bijlagen toevoegen aan uw e-mails.

[Klik hier voor meer informatie over e-mailbijlagen](../../delivery/using/attaching-files.md).

## Uw berichten bijhouden en de impact ervan meten {#track-your-messages-and-measure-their-impact}

Nadat u berichten hebt verzonden, kunt u leren hoe u met Adobe Campaign de berichten kunt opvolgen en de impact ervan meten.

### Hoe kan ik bijgehouden koppelingen in een e-maillevering configureren? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

Voor elke levering kunt u de ontvangst van berichten en de activering van de koppelingen die in de berichtcontent zijn opgenomen, opvolgen. Hierdoor kunt u het gedrag van ontvangers volgen na de leveringsacties waarvoor ze als doel zijn opgegeven.

Voor elke URL van het bericht kunt u kiezen of u bijvoorbeeld het bijhouden wilt activeren, het koppelingslabel wilt wijzigen of koppelingen voor rapportagedoeleinden op categorieën wilt groeperen.

[Klik hier voor meer informatie](../../delivery/using/about-message-tracking.md) over het opvolgen van berichten in Campaign Classic.

### Waar heb ik toegang tot leverings- en trackinglogboeken? {#where-can-i-access-delivery-and-tracking-logs-}

Ontdek hoe u uw leveringen kunt bijhouden en het gedrag van de ontvangers kunt begrijpen [op deze pagina](../../delivery/using/monitoring-a-delivery.md).

### Waar kan ik leveringsrapporten krijgen? {#where-can-i-get-delivery-reports-}

Adobe Campaign wordt geleverd met een set rapporten om uw leveringen te controleren en uw berichten op te volgen.

[Klik hier voor meer informatie over ingebouwde rapporten](../../reporting/using/delivery-reports.md).

### Hoe kwalificeert en beheert Adobe Campaign quarantaineadressen? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign beheert een lijst met in quarantaine geplaatste adressen. Ontvangers van wie het adres in quarantaine is geplaatst, worden standaard tijdens de leveringsanalyse uitgesloten, en zullen niet doelgericht worden benaderd. Een e-mailadres kan in quarantaine worden geplaatst, bijvoorbeeld, wanneer het postvak vol is of als het adres niet bestaat.

[Klik hier voor meer informatie over quarantainebeheer](../../delivery/using/understanding-quarantine-management.md).
