---
title: Veelgestelde vragen testen en verzenden
seo-title: Berichten valideren, verzenden en volgen
description: Klassieke veelgestelde vragen over campagne
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
translation-type: tm+mt
source-git-commit: 994ec35e37a1c26e83a8dd2ae31f6594cadd4c45

---


# Berichten valideren, verzenden en volgen {#validate-send-track}

## Testen en valideren {#test-and-validate-before-sending}

Leer hoe u test- en validatiestappen uitvoert voordat u berichten verzendt in Adobe Campaign.

### Wat is de leveringanalyse? {#what-is-the-delivery-analysis-}

De leveringsanalyse is de fase waarin de doelpopulatie wordt berekend en de leveringsinhoud wordt voorbereid. Zodra het volledig is, is de levering klaar om te verzenden. Raadpleeg de logboeken om te controleren of alles correct is.

[Klik hier voor meer](../../delivery/using/steps-validating-the-delivery.md)informatie.

### Waarom zou ik proefdrukken maken? {#why-should-i-create-proofs-}

Adobe raadt u ten zeerste aan proefdrukberichten te maken om uw levering op een goedkeuringsgroep te testen voordat u deze naar het hoofddoel verzendt. U kunt dan berichtinhoud, verpersoonlijking en leveringsparameters bevestigen.

[Klik hier voor meer](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)informatie. U kunt ook [deze video](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/managing-seed-and-proofs.html)bekijken.

### Hoe te om zaadadressen in de Campagne van Adobe te gebruiken? {#how-to-use-seed-addresses-in-adobe-campaign-}

De zaadadressen worden gebruikt aan doelontvangers die niet de bepaalde doelcriteria aanpassen. Deze ontvangers worden toegevoegd aan het doel: ze kunnen rechtstreeks in de levering of de campagne worden geïmporteerd of gemaakt. Voor direct-mailleveringen worden deze tijdens de extractie toegevoegd en in het uitvoerdocument gemengd.

Dit heeft de volgende voordelen:

* Willekeurige vervanging van velden door gegevens uit ontvangende profielen: hiermee kunt u alleen het e-mailadres invoeren, bijvoorbeeld in de sectie zaadadres.
* Wanneer een werkstroom met functies voor gegevensbeheer wordt gebruikt, kunnen de extra gegevens die in leveringen worden verwerkt op zaadniveau worden ingevoerd om waarden af te dwingen: dit negeert de vervanging van willekeurige waarden .

[Klik hier voor meer informatie over zaadadressen](../../delivery/using/about-seed-addresses.md).

### Hoe kan ik opstelling een goedkeuringsproces alvorens berichten te verzenden? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

Adobe raadt u ten zeerste aan een validatiecyclus voor levering in te stellen om mogelijke fouten in de berichtconfiguratie op te sporen. Zorg ervoor dat de inhoud zo vaak als nodig wordt goedgekeurd door proefdrukken naar testontvangers te verzenden. Telkens wanneer een wijziging wordt aangebracht, moet voor de goedkeuring van de inhoud een bewijs worden verzonden.

[Klik hier voor meer](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)informatie.

### Wat is een typologieregel? {#what-is-a-typology-rule-}

Om conflicten tussen campagnes te vermijden, kan de Campagne van Adobe diverse combinaties testen door specifieke beperkingsregels toe te passen. Dit garandeert dat de verzonden berichten het best aan de behoeften en de verwachtingen van klanten voldoen, in overeenstemming met het beleid van het bedrijfs communicatie.

[Klik hier voor meer](../../campaign/using/about-campaign-typologies.md)informatie.

## Uw berichten verzenden {#send-your-messages}

Leer hoe u berichten op verschillende kanalen kunt verzenden met Adobe Campaign.

### Hoe kan ik e-mails sturen in golven? {#how-can-i-send-emails-in-waves-}

Alvorens een levering naar een grote bevolking te verzenden, kunt u golven [](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) vormen om berichten in verscheidene partijen te verdelen en de lading in evenwicht te brengen.

### Welke zijn de belangrijkste stappen om een e-mail in Campagne tot stand te brengen? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

Nadat de e-maillevering is gemaakt en gevalideerd, kunt u deze verzenden. U kunt besluiten de e-mail naar het hoofddoel onmiddellijk te verzenden of een levering voor een latere datum te plannen. Indien nodig kunt u daarvoor ook de doelpopulatie inschatten.

[Klik hier voor meer](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)informatie.

### Hoe een levering te plannen? {#how-to-schedule-a-delivery-}

U kunt de levering van berichten uitstellen om de levering te plannen of om verkoopdruk te beheren en te voorkomen dat een populatie te groot wordt.

[Klik hier voor meer](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending)informatie.

### Kan ik een bijlage toevoegen aan e-mails? {#can-i-add-an-attachment-to-emails-}

Met Campagne Classic kunt u persoonlijke bijlagen toevoegen aan uw e-mails.

[Klik hier voor meer informatie over e-mailbijlagen](../../delivery/using/attaching-files.md).

## Houd je berichten bij en meet de impact ervan {#track-your-messages-and-measure-their-impact}

Nadat u uw berichten hebt verzonden, leert u hoe u de effecten van deze berichten kunt bijhouden en meten met Adobe Campagne.

### Hoe kan ik bijgehouden koppelingen in een e-maillevering configureren? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

Voor elke levering, kunt u de ontvangst van berichten en de activering van de verbindingen volgen die in de berichtinhoud worden opgenomen. Hierdoor kunt u het gedrag van ontvangers volgen na de leveringsacties waarop ze waren gericht.

Voor elke URL van het bericht kunt u kiezen of u het bijhouden van wijzigingen wilt activeren, het koppelingslabel wilt wijzigen, koppelingen voor rapportagedoeleinden op categorieën wilt groeperen.

[Klik hier voor meer](../../delivery/using/about-message-tracking.md) informatie over het bijhouden van uw berichten in Campaign Classic.

### Waar heb ik toegang tot bezorgings- en trackinglogboeken? {#where-can-i-access-delivery-and-tracking-logs-}

Leer hoe u uw leveringen kunt bijhouden en het gedrag van de ontvangers [op deze pagina](../../delivery/using/monitoring-a-delivery.md)kunt begrijpen.

### Waar kan ik leveringsrapporten krijgen? {#where-can-i-get-delivery-reports-}

Adobe Campagne wordt geleverd met een reeks rapporten om uw leveringen te controleren en uw berichten te volgen.

[Klik hier voor meer informatie over ingebouwde rapporten](../../reporting/using/reports-on-deliveries.md#delivery-reports).

### Hoe kwalificeert en beheert de Campagne van Adobe quarantaineadressen? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign beheert een lijst met in quarantaine geplaatste adressen. Ontvangers van wie adres in quarantaine is geplaatst worden door gebrek tijdens leveringsanalyse uitgesloten, en zullen niet worden gericht. Een e-mailadres kan in quarantaine worden geplaatst, bijvoorbeeld, wanneer de brievenbus volledig is of als het adres niet bestaat.

[Klik hier voor meer informatie over quarantainebeheer](../../delivery/using/understanding-quarantine-management.md).
