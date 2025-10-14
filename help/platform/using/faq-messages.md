---
product: campaign
title: Veelgestelde vragen over testen en verzenden
description: Veelgestelde vragen over Campaign Classic
feature: Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7fc24ef2-b021-440b-b1f2-8c77e2425328
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 72%

---

# Berichten valideren, verzenden en opvolgen {#validate-send-track}



## Testen en valideren {#test-and-validate-before-sending}

Ontdek hoe u test- en validatiestappen uitvoert voordat u berichten verzendt in Adobe Campaign.

### Wat is de leveringanalyse? {#what-is-the-delivery-analysis-}

De leveringsanalyse is de fase waarin de doelpopulatie wordt berekend en de leveringscontent wordt voorbereid. Zodra deze is voltooid, is de levering klaar om te verzenden. Raadpleeg de logboeken om te controleren of alles correct is.

Leer meer in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/delivery-analysis.html?lang=nl-NL){target="_blank"}.

### Waarom zou ik proefdrukken maken? {#why-should-i-create-proofs-}

Adobe raadt u ten zeerste aan proefberichten te maken om uw levering op een goedkeuringsgroep te testen voordat u deze naar het hoofddoel verzendt. U kunt dan parameters voor berichtcontent, personalisatie en levering bevestigen.

Leer meer in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html?lang=nl-NL){target="_blank"}.

### Hoe te om zaadadressen in Adobe Campaign te gebruiken? {#how-to-use-seed-addresses-in-adobe-campaign-}

Seed-adressen worden gebruikt om ontvangers die niet aan de gedefinieerde doelcriteria voldoen, doelgericht te benaderen. Deze ontvangers worden aan het doel toegevoegd: ze kunnen rechtstreeks in de levering of de campagne worden geïmporteerd of gemaakt. Voor direct-mailleveringen worden deze tijdens de extractie toegevoegd en in het uitvoerdocument gemengd.

Dit heeft de volgende voordelen:

* Willekeurige vervanging van velden door data uit profielen van ontvangers: hiermee kunt u alleen het e-mailadres invoeren, bijvoorbeeld in de sectie voor het seed-adres.
* Wanneer een workflow met functies voor data management wordt gebruikt, kunnen de extra data die in leveringen worden verwerkt, op het niveau van het seed-adres worden ingevoerd om waarden af te dwingen: dit omzeilt de vervanging van willekeurige waarden.

[Klik hier voor meer informatie over seed-adressen](../../delivery/using/about-seed-addresses.md).

### Hoe kan ik opstelling een goedkeuringsproces alvorens berichten te verzenden? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

Adobe raadt u ten zeerste aan een cyclus voor leveringsvalidatie in te stellen om mogelijke fouten in de berichtconfiguratie op te sporen. Zorg ervoor dat de content zo vaak als nodig wordt goedgekeurd door proeven naar testontvangers te verzenden. Telkens wanneer een wijziging wordt aangebracht, moet voor de goedkeuring van de content een proef worden verzonden.

Leer meer in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html?lang=nl-NL){target="_blank"}.

### Wat is een typologieregel? {#what-is-a-typology-rule-}

Om conflicten tussen campagnes te vermijden kan Adobe Campaign diverse combinaties testen door specifieke beperkingsregels toe te passen. Dit garandeert dat de verzonden berichten het best aan de behoeften en de verwachtingen van klanten voldoen, in overeenstemming met het beleid inzake bedrijfscommunicatie.

Verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=nl-NL){target="_blank"}.

## Uw berichten verzenden {#send-your-messages}

Ontdek hoe u berichten in verschillende kanalen kunt verzenden met Adobe Campaign.

### Hoe kan ik e-mails sturen in golven? {#how-can-i-send-emails-in-waves-}

Alvorens een levering naar een grote bevolking te verzenden, kunt u golven vormen om berichten in verscheidene partijen te verdelen en de lading in evenwicht te brengen. Zie de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/configure-and-send.html?lang=nl-NL#sending-using-multiple-waves){target="_blank"}.

### Welke zijn de belangrijkste stappen om een e-mail in Campagne tot stand te brengen? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

Nadat de e-maillevering is gemaakt en gevalideerd, kunt u deze verzenden. U kunt besluiten de e-mail onmiddellijk naar het hoofddoel te verzenden of een levering voor een latere datum te plannen. Indien nodig kunt u vooraf ook de doelpopulatie inschatten.

Leer meer in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html?lang=nl-NL){target="_blank"}.

### Hoe een levering te plannen? {#how-to-schedule-a-delivery-}

U kunt de levering van berichten uitstellen om de levering te plannen of om de salesdruk te beheren en te voorkomen dat een populatie overbevraagd wordt.

Leer meer in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/configure-and-send.html?lang=nl-NL#schedule-delivery-sending){target="_blank"}.

### Kan ik een bijlage toevoegen aan e-mails? {#can-i-add-an-attachment-to-emails-}

Met Campaign Classic kunt u gepersonaliseerde bijlagen toevoegen aan uw e-mails.

Leer meer over e-mailgehechtheid in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=nl-NL){target="_blank"}.

## Houd je berichten bij en meet de impact ervan {#track-your-messages-and-measure-their-impact}

Nadat u berichten hebt verzonden, kunt u leren hoe u met Adobe Campaign de berichten kunt opvolgen en de impact ervan meten.

### Hoe kan ik bijgehouden koppelingen in een e-maillevering configureren? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

Voor elke levering kunt u de ontvangst van berichten en de activering van de koppelingen die in de berichtcontent zijn opgenomen, opvolgen. Hierdoor kunt u het gedrag van ontvangers volgen na de leveringsacties waarvoor ze als doel zijn opgegeven.

Voor elke URL van het bericht kunt u kiezen of u bijvoorbeeld het bijhouden wilt activeren, het koppelingslabel wilt wijzigen of koppelingen voor rapportagedoeleinden op categorieën wilt groeperen.

[Klik hier voor meer informatie](../../delivery/using/about-message-tracking.md) over het opvolgen van berichten in Campaign Classic.

### Waar heb ik toegang tot bezorgings- en trackinglogboeken? {#where-can-i-access-delivery-and-tracking-logs-}

Leer hoe te om uw leveringen te volgen en het gedrag van ontvangers [&#x200B; van deze pagina &#x200B;](../../delivery/using/delivery-dashboard.md) te begrijpen.

### Waar kan ik leveringsrapporten krijgen? {#where-can-i-get-delivery-reports-}

Adobe Campaign wordt geleverd met een set rapporten om uw leveringen te controleren en uw berichten op te volgen.

[Klik hier voor meer informatie over ingebouwde rapporten](../../reporting/using/delivery-reports.md).

### Hoe kwalificeert en beheert Adobe Campaign quarantaineadressen? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign beheert een lijst met in quarantaine geplaatste adressen. Ontvangers van wie het adres in quarantaine is geplaatst, worden standaard tijdens de leveringsanalyse uitgesloten, en zullen niet doelgericht worden benaderd. Een e-mailadres kan in quarantaine worden geplaatst, bijvoorbeeld, wanneer het postvak vol is of als het adres niet bestaat.

[Klik hier voor meer informatie over quarantainebeheer](../../delivery/using/understanding-quarantine-management.md).
