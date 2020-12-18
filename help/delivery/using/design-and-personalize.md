---
solution: Campaign Classic
product: campaign
title: Gepersonaliseerde content maken
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1266'
ht-degree: 7%

---


# Gepersonaliseerde content maken {#build-personalized-content}

Probeer bij het ontwerpen van de inhoud van uw bericht algemene problemen te vermijden die ertoe kunnen leiden dat u de levering niet kunt uitvoeren. Meestal hebben mogelijke fouten betrekking op [personalisatie](../../delivery/using/about-personalization.md), [formatteren](../../delivery/using/defining-the-email-content.md#message-content) en [afbeeldingen](../../delivery/using/defining-the-email-content.md#adding-images).

## Aanpassing optimaliseren {#optimize-personalization}

Om veelvoorkomende problemen te voorkomen die ertoe kunnen leiden dat u uw levering niet kunt uitvoeren en om de ervaring van uw ontvangers te verbeteren, kunt u uw berichten aan uw persoonlijke voorkeur aanpassen.

U kunt de gegevens van ontvangers gebruiken die in de Adobe Campaign-database zijn opgeslagen, of die worden verzameld via tracking, landing pages, subscriptions, etc.
De grondbeginselen van de aanpassing worden voorgesteld in [deze sectie](../../delivery/using/personalization-fields.md).

Zorg ervoor dat de inhoud van uw bericht goed is ontworpen om fouten te voorkomen die over het algemeen te maken hebben met personalisatie.

**Tips**: In verpersoonlijkingsgebieden die uit externe dossiers komen die door derdeverkopers worden verstrekt, kan de externe inhoud van HTML verkeerd zijn. Om dit te voorkomen, controleert u de syntaxis, het gebruik van tags, tekens, enzovoort. Een Adobe Campaign-personalisatie-tag heeft bijvoorbeeld altijd de volgende vorm: &lt;%=table.field%>. Zie [deze sectie](../../delivery/using/about-personalization.md)voor meer informatie.

Het onjuiste gebruik van parameters in verpersoonlijkingsblokken kan een kwestie zijn. Variabelen in JavaScript moeten bijvoorbeeld als volgt worden gebruikt:

    &lt;>var brand = &quot;xxx&quot;
    
    %>

    
    
Voor meer op verpersoonlijkingsblokken, verwijs naar [deze sectie](../../delivery/using/personalization-blocks.md).

U kunt aanpassingsgegevens voorbereiden in een workflow om de voorbereiding van de levering te verbeteren. Dit moet speciaal worden gebruikt als de personalisatiegegevens afkomstig zijn van een externe tabel via Federated Data Access (FDA). Deze optie wordt beschreven in deze [deze sectie](../../delivery/using/personalization-fields.md#optimizing-personalization)

## Geoptimaliseerde inhoud maken {#optimize-content}

Houd rekening met de onderstaande algemene tips bij het samenstellen van e-mails.

* Ontwerp eenvoudig houden

* Houd mobiele gebruikers in gedachten

* Vermijd e-mails die volledig op afbeeldingen zijn gebaseerd

* E-mailveilige lettertypen gebruiken

* Speciale tekens coderen

### Onderwerpregel

Werk aan [onderwerpregel](../../delivery/using/defining-the-email-content.md#message-content) om open snelheden te verbeteren:

* Vermijd personen die te lang zijn. Gebruik maximaal 50 tekens

* Vermijd het gebruik van herhalende woorden zoals &quot;gratis&quot; of &quot;aanbieding&quot;, die als spam kunnen worden beschouwd

* Vermijd hoofdletters en speciale tekens zoals &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

### Pagina spiegelen

Neem altijd een koppeling naar een spiegelpagina op. De voorkeurspositie boven aan het e-mailbericht. [Meer informatie](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### Unsubscription link

De koppeling om uw abonnement op te zeggen is essentieel. Het formulier moet zichtbaar en geldig zijn en moet functioneel zijn. Wanneer het bericht wordt geanalyseerd, controleert standaard een [typologieregel](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) of een opt-out-koppeling is opgenomen en wordt een waarschuwing gegenereerd als deze ontbreekt.

**Tip**: Omdat menselijke fout altijd mogelijk is, controleer dat de opt-out verbinding correct vóór elke keer werkt u verzendt. Als u bijvoorbeeld de proefdruk verzendt, controleert u of de koppeling geldig is, of het formulier online is en of het veld Geen contact meer opnemen met deze ontvanger is gewijzigd in Ja.

Leer hoe te om een opt-out verbinding [in deze sectie ](../../delivery/using/personalization-blocks.md#personalization-blocks-example) op te nemen.

### E-mailformaat

Om problemen met prestaties of leverbaarheid te voorkomen, is de aanbevolen maximale grootte van een e-mailbericht ongeveer **35KB**. Als u de berichtgrootte wilt controleren, gaat u naar de tab **[!UICONTROL Preview]** en kiest u een testprofiel. Zodra geproduceerd, zal de berichtgrootte in de hoogste juiste hoek worden getoond.

Houd rekening met het volgende om uw e-mailadres onder de limiet te houden:

* Overbodige of ongebruikte stijlen verwijderen

* Een deel van de e-mailinhoud naar een openingspagina verplaatsen

* Miniatuur uw code

Zorg ervoor dat u wijzigingen test voordat u de definitieve verzending uitvoert

### Sms-lengte

Standaard voldoet het aantal tekens in een sms aan de gsm-standaarden (Global System for Mobile Communications). Sms-berichten met gsm-codering mogen maximaal 160 tekens bevatten of 153 tekens per sms voor berichten die in meerdere delen worden verzonden.

Transliteratie houdt in dat een teken van een sms door een ander teken wordt vervangen wanneer dat teken niet in aanmerking wordt genomen door de gsm-standaard. Als u personalisatievelden in de inhoud van uw SMS-bericht invoegt, kunnen er tekens worden ingevoerd waarmee de GSM-codering geen rekening houdt. U kunt tekentransliteratie toestaan door het corresponderende vak te selecteren op het tabblad met SMPP-kanaalinstellingen van het corresponderende **[!UICONTROL External account]**.
Meer informatie [in deze sectie](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Tips**:

* Als u alle tekens in uw SMS-berichten ongewijzigd wilt laten, bijvoorbeeld eigennamen niet wilt wijzigen, moet u transliteratie niet inschakelen.

* Als uw SMS-berichten echter veel tekens bevatten waarmee de GSM-standaard geen rekening houdt, kunt u met transliteratie de verzendkosten van uw berichten beperken.

Meer informatie [in deze sectie](../../delivery/using/sms-channel.md#about-character-transliteration).

## Werken met opmaken {#formatting}

Controleer de volgende elementen om algemene opmaakfouten te voorkomen:

* Corrigeer **datumopmaak**: Adobe Campaign biedt functies voor datumopmaak voor de JavaScript-sjablonen en XSL-opmaakmodellen. [Meer informatie](../../delivery/using/formatting.md#date-display)

* Gebruik van **geoorloofde tekens** in e-mails: De lijst met geldige tekens voor e-mailadressen wordt gedefinieerd in de optie &quot;XtkEmail_Characters&quot;. Leer hoe te om tot de opties [in deze sectie ](../../installation/using/configuring-campaign-options.md) toegang te hebben. Adobe Campaign moet in Unicode zijn geïnstalleerd om speciale tekens correct te kunnen verwerken.

* Configuratie van **E-mailverificatie**: zorg ervoor dat de e-mailkopteksten de DKIM-handtekening bevatten. DKIM (Domeinsleutels Identified Mail) authentificatie staat de ontvangende e-mailserver toe om te verifiëren dat een bericht inderdaad werd verzonden door de persoon of de entiteit het beweert werd verzonden door, en of de berichtinhoud binnen tussen de tijd werd veranderd het oorspronkelijk werd verzonden (en DKIM &quot;ondertekend&quot;) en de tijd het werd ontvangen. Deze standaard gebruikt doorgaans het domein in de kop Van of Afzender. Raadpleeg [deze sectie](../../delivery/using/technical-recommendations.md#dkim) voor meer informatie.

### Responsief e-mailontwerp

Het responsieve ontwerp zorgt ervoor dat een e-mail optimaal wordt weergegeven voor het apparaat waarop het wordt geopend.

* Responsieve HTML-e-mail gebruiken in plaats van HTML-webpagina

* Gebruik de voorvertoningsmodus en verzend proefdrukken om de rendering op zoveel mogelijk apparaten te testen

* De module Adobe Campaign Classic Digital Content Editor (DCE) bevat een aantal responsieve ontwerpopgemaakte sjablonen voor mobiele apparaten die beschikbaar zijn via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Meer informatie vindt u in dit artikel](https://theblog.adobe.com/responsive-email-design-101/)[

## Afbeeldingen beheren {#manage-images}

Volg de onderstaande richtlijnen voor het gebruik van afbeeldingen.

### Afbeeldingen blokkeren voorkomen

Sommige e-mailclients blokkeren afbeeldingen standaard en sommige gebruikers wijzigen hun instellingen om afbeeldingen te blokkeren zodat ze op gegevensgebruik kunnen worden opgeslagen. Als afbeeldingen niet worden gedownload, kan het hele bericht verloren gaan. Om dit te voorkomen:

* Verdeel uw inhoud met afbeelding en tekst. Vermijd e-mails die volledig op afbeeldingen zijn gebaseerd.

* Als er tekst in een afbeelding moet staan, gebruikt u alt- en titeltekst om ervoor te zorgen dat uw bericht overloopt. Maak de alt-/titeltekst op om de weergave te verbeteren.

* Vermijd het gebruik van achtergrondafbeeldingen, omdat deze niet door sommige e-mailclients worden ondersteund.

### Afbeeldingen responsief maken

Probeer afbeeldingen responsief te maken en de grootte ervan te wijzigen. Merk op dat dit een kosteneffect kan hebben aangezien het langer duurt om te bouwen.

### Absolute verwijzingen naar afbeeldingen gebruiken

Om van buitenaf toegankelijk te zijn, moeten de beelden die in e-mail en openbare middelen verbonden aan campagnes worden gebruikt op een extern toegankelijke server aanwezig zijn.

* U kunt controleren als de instantieconfiguratie openbaar middelbeheer toelaat. [Meer informatie](../../installation/using/deploying-an-instance.md#managing-public-resources)

* Vanuit de wizard voor levering kunt u een HTML-pagina met afbeeldingen importeren of afbeeldingen rechtstreeks invoegen met de HTML-editor via het pictogram **[!UICONTROL Image]**. [Meer informatie](../../delivery/using/defining-the-email-content.md#adding-images)

* Als afbeeldingen niet worden weergegeven, controleert u of de afbeeldingen beschikbaar zijn op de server. Klik hiertoe op het tabblad Bron van uw levering. Zoek uw afbeeldingen en kopieer en plak de URL van elke afbeelding in een webbrowser. Als de afbeeldingen niet worden weergegeven, neemt u contact op met uw IT-beheerder of de externe leverancier die uw leveringsinhoud levert.

## Een voorbeeld bekijken van uw bericht {#preview-msg}

Adobe raadt u aan een voorbeeld van uw bericht te bekijken om na te gaan wat de personalisatie is en hoe de ontvangers uw bericht zullen bekijken.

* In het bezorgingsbericht kunt u met het subtabblad **[!UICONTROL Preview]** de rendering van elke inhoud voor een ontvanger weergeven. De verpersoonlijkingsgebieden en de voorwaardelijke elementen van inhoud worden vervangen met de overeenkomstige informatie voor het geselecteerde profiel. [Meer informatie](../../delivery/using/defining-the-email-content.md#message-content)

* Tijdens elke voorvertoning wordt een automatische controle op anti-spam uitgevoerd. Schakel in het subtabblad **[!UICONTROL Preview]** de spamscoring [SpamAssassin](../../delivery/using/spamassassin.md) in.  Klik **[!UICONTROL More...]** om meer over de waarschuwing te weten te komen.  Controleer voordat u dit doet of SpamAssassin op de juiste wijze is geïnstalleerd en geconfigureerd op de Adobe Campaign-toepassingsserver. [Meer informatie](../../installation/using/configuring-spamassassin.md)
