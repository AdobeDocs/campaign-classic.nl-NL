---
product: campaign
title: Gepersonaliseerde content maken
description: Leer hoe u persoonlijke inhoud kunt maken in Adobe Campaign-leveringen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Email Design, Personalization
role: User
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1293'
ht-degree: 3%

---

# Gepersonaliseerde content maken {#build-personalized-content}

Probeer bij het ontwerpen van de inhoud van uw bericht algemene problemen te vermijden die ertoe kunnen leiden dat u de levering niet kunt uitvoeren. Meestal hebben mogelijke fouten betrekking op [personalisatie](about-personalization.md), [opmaken](defining-the-email-content.md#message-content) en [afbeeldingen](defining-the-email-content.md#adding-images).

## Aanpassing optimaliseren {#optimize-personalization}

Om veelvoorkomende problemen te voorkomen die ertoe kunnen leiden dat u uw levering niet kunt uitvoeren en om de ervaring van uw ontvangers te verbeteren, kunt u uw berichten aan uw persoonlijke voorkeur aanpassen.

U kunt de gegevens van ontvangers gebruiken die in de Adobe Campaign-database zijn opgeslagen, of die worden verzameld via tracking, landing pages, subscriptions, etc.
De grondbeginselen van personalisatie worden weergegeven in [deze sectie](personalization-fields.md).

Zorg ervoor dat de inhoud van uw bericht goed is ontworpen om fouten te voorkomen die over het algemeen te maken hebben met personalisatie.

**Tips**: In verpersoonlijkingsgebieden die uit externe dossiers komen die door derdeverkopers worden verstrekt, kan de externe inhoud van HTML verkeerd zijn. Om dit te voorkomen, controleert u de syntaxis, het gebruik van tags, tekens, enzovoort. Een Adobe Campaign-personalisatietag heeft bijvoorbeeld altijd de volgende vorm: &lt;%=table.field%>. Zie [deze sectie](about-personalization.md)voor meer informatie.

Het onjuiste gebruik van parameters in verpersoonlijkingsblokken kan een kwestie zijn. Variabelen in JavaScript moeten bijvoorbeeld als volgt worden gebruikt:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

Raadpleeg voor meer informatie over aanpassingsblokken de [deze sectie](personalization-blocks.md).

U kunt aanpassingsgegevens voorbereiden in een workflow om de voorbereiding van de levering te verbeteren. Dit moet speciaal worden gebruikt als de personalisatiegegevens afkomstig zijn van een externe tabel via Federated Data Access (FDA). Deze optie wordt in deze [deze sectie](personalization-fields.md#optimizing-personalization)

## Geoptimaliseerde inhoud maken {#optimize-content}

Houd rekening met de onderstaande algemene tips bij het samenstellen van e-mails.

* Ontwerp eenvoudig houden

* Houd mobiele gebruikers in gedachten

* Vermijd volledig op afbeeldingen gebaseerde e-mails

* E-mailveilige lettertypen gebruiken

* Speciale tekens coderen

### Onderwerpregel

Werken met de [onderwerpregel](defining-the-email-content.md#message-content) verbetering van de open tarieven :

* Vermijd personen die te lang zijn. Maximaal 50 tekens gebruiken

* Vermijd het gebruik van herhalende woorden zoals &quot;gratis&quot; of &quot;aanbieding&quot;, die als spam kunnen worden beschouwd

* Vermijd hoofdletters en speciale tekens zoals &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

### Pagina spiegelen

Neem altijd een koppeling naar een spiegelpagina op. De voorkeurspositie boven aan het e-mailbericht. [Meer informatie](sending-messages.md#generating-the-mirror-page)

### Koppeling met abonnement opheffen

De koppeling om uw abonnement op te zeggen is essentieel. Het formulier moet zichtbaar en geldig zijn en moet functioneel zijn. Wanneer het bericht wordt geanalyseerd, wordt standaard een [typologieregel](steps-validating-the-delivery.md#validation-process-with-typologies) Hiermee wordt gecontroleerd of een opt-out-koppeling is opgenomen en wordt een waarschuwing gegenereerd als deze ontbreekt.

**Tip**: Omdat menselijke fout altijd mogelijk is, controleer dat de opt-out verbinding correct vóór elke keer werkt u verzendt. Als u bijvoorbeeld de proefdruk verzendt, controleert u of de koppeling geldig is, of het formulier online is en of het veld Geen contact meer opnemen met deze ontvanger is gewijzigd in Ja.

Meer informatie over het invoegen van een koppeling om te weigeren [in deze sectie](personalization-blocks.md#personalization-blocks-example).

### E-mailformaat

Om problemen met prestaties of leverbaarheid te voorkomen, is de aanbevolen maximale grootte van een e-mail ongeveer **35 kB**. Als u de grootte van het bericht wilt controleren, gaat u naar **[!UICONTROL Preview]** en kiest u een testprofiel. Zodra geproduceerd, zal de berichtgrootte in de hoogste juiste hoek worden getoond.

Houd rekening met het volgende om uw e-mailadres onder de limiet te houden:

* Overbodige of ongebruikte stijlen verwijderen

* Een deel van de e-mailinhoud naar een openingspagina verplaatsen

* Miniatuur uw code

Zorg ervoor dat u wijzigingen test voordat u de definitieve verzending uitvoert

### Sms-lengte

Standaard voldoet het aantal tekens in een SMS aan de GSM-standaarden (Global System for Mobile Communications). Sms-berichten met gsm-codering mogen maximaal 160 tekens bevatten of 153 tekens per sms voor berichten die in meerdere delen worden verzonden.

Vertaling bestaat erin een teken van een SMS door een ander te vervangen wanneer dat teken niet in aanmerking wordt genomen door de GSM-standaard. Als u personalisatievelden in de inhoud van uw SMS-bericht invoegt, kunnen er tekens worden ingevoerd waarmee de GSM-codering geen rekening houdt. U kunt tekenomzetting autoriseren door het corresponderende vak te selecteren op het tabblad met SMPP-kanaalinstellingen van het corresponderende **[!UICONTROL External account]**.
Meer informatie [in deze sectie](sms-set-up.md#creating-an-smpp-external-account).

**Tips**:

* Als u alle tekens in uw SMS-berichten wilt behouden, bijvoorbeeld als u eigennamen niet wilt wijzigen, moet u transliteratie niet inschakelen.

* Als uw SMS-berichten echter veel tekens bevatten waarmee de GSM-standaard geen rekening houdt, kunt u met transliteratie de verzendkosten van uw berichten beperken.

Meer informatie [in deze sectie](sms-set-up.md#about-character-transliteration).

## Werken met opmaak {#formatting}

Controleer de volgende elementen om algemene opmaakfouten te voorkomen:

* Juist **datumnotatie**: Adobe Campaign biedt functies voor datumnotatie voor de JavaScript-sjablonen en XSL-opmaakmodellen. [Meer informatie](formatting.md#date-display)

* Gebruik van **geautoriseerde tekens** in e-mailberichten: de lijst met geldige tekens voor e-mailadressen wordt gedefinieerd in de optie &quot;XtkEmail_Characters&quot;. Leer hoe u de opties voor campagnes kunt openen [in deze sectie](../../installation/using/configuring-campaign-options.md). Adobe Campaign moet in Unicode zijn geïnstalleerd om speciale tekens correct te kunnen verwerken.

* Configuratie van **E-mailverificatie**: zorg ervoor dat de e-mailkopteksten de DKIM-handtekening bevatten. DKIM (Domeinsleutels Identified Mail) authentificatie staat de ontvangende e-mailserver toe om te verifiëren dat een bericht inderdaad werd verzonden door de persoon of de entiteit het beweert werd verzonden door, en of de berichtinhoud binnen tussen de tijd werd veranderd het oorspronkelijk werd verzonden (en DKIM &quot;ondertekend&quot;) en de tijd het werd ontvangen. Deze standaard gebruikt typisch het domein in van of de kopbal van de Afzender. Raadpleeg voor meer informatie de [Handleiding voor beste praktijken bij de levering van Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Responsief e-mailontwerp

Het responsieve ontwerp zorgt ervoor dat een e-mail optimaal wordt weergegeven voor het apparaat waarop het wordt geopend.

* Responsieve e-mail HTML gebruiken in plaats van web HTML

* Gebruik de voorvertoningsmodus en verzend proefdrukken om de rendering op zoveel mogelijk apparaten te testen

* De module Adobe Campaign Classic Digital Content Editor (DCE) bevat een aantal responsieve ontwerpopgemaakte sjablonen voor mobiele apparaten die beschikbaar zijn via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Meer informatie [in dit artikel](https://theblog.adobe.com/responsive-email-design-101/)

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

* Vanuit de wizard voor levering kunt u een HTML-pagina met afbeeldingen importeren of rechtstreeks via de HTML-editor afbeeldingen invoegen **[!UICONTROL Image]** pictogram. [Meer informatie](defining-the-email-content.md#adding-images)

* Als afbeeldingen niet worden weergegeven, controleert u of de afbeeldingen beschikbaar zijn op de server. Klik hiertoe op het tabblad Bron van uw levering. Zoek uw afbeeldingen en kopieer en plak de URL van elke afbeelding in een webbrowser. Als de afbeeldingen niet worden weergegeven, neemt u contact op met uw IT-beheerder of de externe leverancier die uw leveringsinhoud levert.

## Een voorbeeld van uw bericht bekijken {#preview-msg}

Adobe raadt u aan een voorbeeld van uw bericht te bekijken om na te gaan hoe de inhoud van het bericht wordt aangepast en hoe de ontvangers de levering zien.

* In de bezorgwizard **[!UICONTROL Preview]** Met de subtab kunt u de rendering van elke inhoud voor een ontvanger bekijken. De verpersoonlijkingsgebieden en de voorwaardelijke elementen van inhoud worden vervangen met de overeenkomstige informatie voor het geselecteerde profiel. [Meer informatie](defining-the-email-content.md#message-content)

* Tijdens elke voorvertoning wordt een automatische controle op anti-spam uitgevoerd. In de **[!UICONTROL Preview]** subtabblad, controleren [SpamAssassin](spamassassin.md) spamscoring.  Klikken **[!UICONTROL More...]** voor meer informatie over de waarschuwing .  Controleer voordat u dit doet of SpamAssassin op de juiste wijze is geïnstalleerd en geconfigureerd op de Adobe Campaign-toepassingsserver. [Meer informatie](../../installation/using/configuring-spamassassin.md)
