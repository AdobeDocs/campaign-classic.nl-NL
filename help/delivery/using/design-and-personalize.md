---
product: campaign
title: Gepersonaliseerde content maken
description: Leer hoe u persoonlijke inhoud kunt maken in Adobe Campaign-leveringen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Email Design, Personalization
role: User
hide: true
hidefromtoc: true
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 3%

---

# Gepersonaliseerde content maken {#build-personalized-content}

Probeer bij het ontwerpen van de inhoud van uw bericht algemene problemen te vermijden die ertoe kunnen leiden dat u de levering niet kunt uitvoeren. De meeste tijd, de mogelijke fouten zijn verwant met [ verpersoonlijking ](about-personalization.md), [ formatterend ](defining-the-email-content.md#message-content) en [ beelden ](defining-the-email-content.md#adding-images).

## Aanpassing optimaliseren {#optimize-personalization}

Om veelvoorkomende problemen te voorkomen die ertoe kunnen leiden dat u uw levering niet kunt uitvoeren en om de ervaring van uw ontvangers te verbeteren, kunt u uw berichten aan uw persoonlijke voorkeur aanpassen.

U kunt de gegevens van ontvangers gebruiken die in de Adobe Campaign-database zijn opgeslagen, of die worden verzameld via tracking, landing pages, subscriptions, etc.
De grondbeginselen van Personalization worden voorgesteld in [ deze sectie ](personalization-fields.md).

Zorg ervoor dat de inhoud van uw bericht goed is ontworpen om fouten te voorkomen die over het algemeen te maken hebben met personalisatie.

**Uiteinden**: In verpersoonlijkingsgebieden die uit externe dossiers komen die door derdeverkopers worden verstrekt, kan de externe inhoud van HTML verkeerd zijn. Om dit te voorkomen, controleert u de syntaxis, het gebruik van tags, tekens, enzovoort. Een Adobe Campaign-personalisatietag heeft bijvoorbeeld altijd de volgende vorm: &lt;%=table.field%>. Zie [deze sectie](about-personalization.md)voor meer informatie.

Het onjuiste gebruik van parameters in verpersoonlijkingsblokken kan een kwestie zijn. Variabelen in JavaScript moeten bijvoorbeeld als volgt worden gebruikt:

    &lt;% 
    
     var merk = &quot;xxx&quot;
    
    %> 

Voor meer op verpersoonlijkingsblokken, verwijs naar [ deze sectie ](personalization-blocks.md).

U kunt aanpassingsgegevens voorbereiden in een workflow om de voorbereiding van de levering te verbeteren. Dit moet speciaal worden gebruikt als de personalisatiegegevens afkomstig zijn van een externe tabel via Federated Data Access (FDA). Deze optie wordt beschreven in dit [ deze sectie ](personalization-fields.md#optimizing-personalization)

## Geoptimaliseerde inhoud maken {#optimize-content}

Houd rekening met de onderstaande algemene tips bij het samenstellen van e-mails.

* Ontwerp eenvoudig houden

* Houd mobiele gebruikers in gedachten

* Vermijd volledig op afbeeldingen gebaseerde e-mails

* E-mailveilige lettertypen gebruiken

* Speciale tekens coderen

### Onderwerpregel

Het werk op de [ onderwerpregel ](defining-the-email-content.md#message-content) om open tarieven te verbeteren:

* Vermijd personen die te lang zijn. Maximaal 50 tekens gebruiken

* Vermijd het gebruik van herhalende woorden zoals &quot;gratis&quot; of &quot;aanbieding&quot;, die als spam kunnen worden beschouwd

* Vermijd hoofdletters en speciale tekens zoals &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

### Pagina spiegelen

Neem altijd een koppeling naar een spiegelpagina op. De voorkeurspositie boven aan het e-mailbericht. [Meer informatie](sending-messages.md#generating-the-mirror-page)

### Koppeling met abonnement opheffen

De koppeling om uw abonnement op te zeggen is essentieel. Het formulier moet zichtbaar en geldig zijn en moet functioneel zijn. Door gebrek, wanneer het bericht wordt geanalyseerd, controleert de a [ typologieregel ](steps-validating-the-delivery.md#validation-process-with-typologies) of een opt-out verbinding is omvat en produceert een waarschuwing als het mist.

**Uiteinde**: Omdat de menselijke fout altijd mogelijk is, controleer dat de opt-out verbinding correct vóór elke keer werkt u verzendt. Als u bijvoorbeeld de proefdruk verzendt, controleert u of de koppeling geldig is, of het formulier online is en of het veld Geen contact meer opnemen met deze ontvanger is gewijzigd in Ja.

Leer hoe te om een opt-out verbinding [ in deze sectie ](personalization-blocks.md#personalization-blocks-example) op te nemen.

### E-mailformaat

Om prestaties of leveringsproblemen te vermijden, is de geadviseerde maximumgrootte van een e-mail ongeveer **35KB**. Als u de berichtgrootte wilt controleren, gaat u naar de tab **[!UICONTROL Preview]** en kiest u een testprofiel. Zodra geproduceerd, zal de berichtgrootte in de hoogste juiste hoek worden getoond.

Houd rekening met het volgende om uw e-mailadres onder de limiet te houden:

* Overbodige of ongebruikte stijlen verwijderen

* Een deel van de e-mailinhoud naar een openingspagina verplaatsen

* Miniatuur uw code

Zorg ervoor dat u wijzigingen test voordat u de definitieve verzending uitvoert

### Sms-lengte

Standaard voldoet het aantal tekens in een SMS aan de GSM-standaarden (Global System for Mobile Communications). Sms-berichten met gsm-codering mogen maximaal 160 tekens bevatten of 153 tekens per sms voor berichten die in meerdere delen worden verzonden.

Vertaling bestaat erin een teken van een SMS door een ander te vervangen wanneer dat teken niet in aanmerking wordt genomen door de GSM-standaard. Als u personalisatievelden in de inhoud van uw SMS-bericht invoegt, kunnen er tekens worden ingevoerd waarmee de GSM-codering geen rekening houdt. U kunt tekentransliteratie autoriseren door het corresponderende vak te selecteren op het tabblad met SMPP-kanaalinstellingen van het corresponderende **[!UICONTROL External account]** .
Leer meer [ in deze sectie ](sms-set-up.md#creating-an-smpp-external-account).

**Uiteinden**:

* Als u alle tekens in uw SMS-berichten wilt behouden, bijvoorbeeld als u eigennamen niet wilt wijzigen, moet u transliteratie niet inschakelen.

* Als uw SMS-berichten echter veel tekens bevatten waarmee de GSM-standaard geen rekening houdt, kunt u met transliteratie de verzendkosten van uw berichten beperken.

Leer meer [ in deze sectie ](sms-set-up.md#about-character-transliteration).

## Werken met opmaak {#formatting}

Controleer de volgende elementen om algemene opmaakfouten te voorkomen:

* Correct **datum het formatteren**: Adobe Campaign verstrekt datum het formatteren functies voor de malplaatjes van JavaScript en de stijlen van XSL. [Meer informatie](formatting.md#date-display)

* Gebruik van **erkende karakters** in e-mail: de lijst van geldige karakters voor e-mailadressen wordt bepaald in de &quot;optie XtkEmail_Characters&quot;. Leer hoe te om tot de opties van de Campagne [ in deze sectie ](../../installation/using/configuring-campaign-options.md) toegang te hebben. Adobe Campaign moet in Unicode zijn geïnstalleerd om speciale tekens correct te kunnen verwerken.

* Configuratie van **E-mailAuthentificatie**: zorg ervoor dat de e-mailkopballen de handtekening DKIM bevatten. DKIM (Domeinsleutels Identified Mail) authentificatie staat de ontvangende e-mailserver toe om te verifiëren dat een bericht inderdaad werd verzonden door de persoon of de entiteit het beweert werd verzonden door, en of de berichtinhoud binnen tussen de tijd werd veranderd het oorspronkelijk werd verzonden (en DKIM &quot;ondertekend&quot;) en de tijd het werd ontvangen. Deze standaard gebruikt typisch het domein in van of de kopbal van de Afzender. Voor meer op dit, verwijs naar de [ Gids van de Beste praktijken van de Levering van de Adobe ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Responsief e-mailontwerp

Het responsieve ontwerp zorgt ervoor dat een e-mail optimaal wordt weergegeven voor het apparaat waarop het wordt geopend.

* Responsieve e-mail HTML gebruiken in plaats van web HTML

* Gebruik de voorvertoningsmodus en verzend proefdrukken om de rendering op zoveel mogelijk apparaten te testen

* De module Adobe Campaign Classic Digital Content Editor (DCE) bevat een aantal responsieve ontwerpsjablonen voor mobiele apparaten die beschikbaar zijn via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]** .

## Afbeeldingen beheren {#manage-images}

Volg de onderstaande richtlijnen voor het gebruik van afbeeldingen.

### Afbeeldingen blokkeren voorkomen

Sommige e-mailclients blokkeren afbeeldingen standaard en sommige gebruikers wijzigen hun instellingen om afbeeldingen te blokkeren zodat ze op gegevensgebruik kunnen worden opgeslagen. Als afbeeldingen niet worden gedownload, kan het hele bericht verloren gaan. Om dit te voorkomen:

* Verdeel uw inhoud met afbeelding en tekst. Vermijd e-mails die volledig op afbeeldingen zijn gebaseerd.

* Als er tekst in een afbeelding moet staan, gebruikt u de alt- en titeltekst om ervoor te zorgen dat uw bericht overloopt. Maak de alt-/titeltekst op om de weergave te verbeteren.

* Vermijd het gebruik van achtergrondafbeeldingen, omdat deze niet door sommige e-mailclients worden ondersteund.

### Afbeeldingen responsief maken

Probeer afbeeldingen responsief te maken en de grootte ervan te wijzigen. Merk op dat dit een kosteneffect kan hebben aangezien het langer duurt om te bouwen.

### Absolute verwijzingen naar afbeeldingen gebruiken

Om van buitenaf toegankelijk te zijn, moeten de beelden die in e-mail en openbare middelen verbonden aan campagnes worden gebruikt op een extern toegankelijke server aanwezig zijn.

* U kunt controleren als de instantieconfiguratie openbaar middelbeheer toelaat. [Meer informatie](../../installation/using/deploying-an-instance.md#managing-public-resources)

* Vanuit de bezorgingsassistent kunt u een HTML-pagina met afbeeldingen importeren of rechtstreeks afbeeldingen invoegen met de HTML-editor via het pictogram **[!UICONTROL Image]** . [Meer informatie](defining-the-email-content.md#adding-images)

* Als afbeeldingen niet worden weergegeven, controleert u of de afbeeldingen beschikbaar zijn op de server. Klik hiertoe op het tabblad Source van uw levering. Zoek uw afbeeldingen en kopieer en plak de URL van elke afbeelding in een webbrowser. Als de afbeeldingen niet worden weergegeven, neemt u contact op met uw IT-beheerder of de externe leverancier die uw leveringsinhoud levert.

## Een voorbeeld van uw bericht bekijken {#preview-msg}

Adobe raadt u aan een voorbeeld van uw bericht te bekijken om na te gaan hoe de inhoud van het bericht wordt aangepast en hoe de ontvangers de levering zien.

* In de bezorgingsassistent kunt u op het subtabblad **[!UICONTROL Preview]** de rendering van elke inhoud voor een ontvanger weergeven. De verpersoonlijkingsgebieden en de voorwaardelijke elementen van inhoud worden vervangen met de overeenkomstige informatie voor het geselecteerde profiel. [Meer informatie](defining-the-email-content.md#message-content)

* Tijdens elke voorvertoning wordt een automatische controle op anti-spam uitgevoerd. In het **[!UICONTROL Preview]** sub-lusje, controleer [ SpamAssassin ](spamassassin.md) spamscoring.  Klik op **[!UICONTROL More...]** voor meer informatie over de waarschuwing.  Controleer voordat u dit doet of SpamAssassin op de juiste wijze is geïnstalleerd en geconfigureerd op de Adobe Campaign-toepassingsserver. [Meer informatie](../../installation/using/configuring-spamassassin.md)
