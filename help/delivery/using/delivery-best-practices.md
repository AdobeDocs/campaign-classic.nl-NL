---
title: Aanbevolen werkwijzen voor het leveren van campagnes
seo-title: Best practices voor levering
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f599bc5483779ae62dd4d5eb1936cbc2760639b5
workflow-type: tm+mt
source-wordcount: '4348'
ht-degree: 3%

---


# Best practices voor levering {#delivery-best-practices}

## Levering optimaliseren {#optimize-delivery}

Voordat u zelfs begint met het maken van leveringen, kunt u verschillende acties uitvoeren om het verzendingsproces te beveiligen en te optimaliseren.

In de volgende sectie worden aanbevolen procedures en aanbevolen procedures voor de optimale configuratie van Adobe Campaign beschreven. Als u deze praktijken volgt, worden de problemen die u later tegenkomt, tot een minimum beperkt.

### Prestaties van Platforms

Verschillende factoren kunnen de serverprestaties rechtstreeks beïnvloeden en het platform vertragen:

* Het aantal en het type van verpersoonlijkingselementen: personalisatie in e-mailberichten haalt gegevens uit de database voor elke ontvanger. Als er vele verpersoonlijkingselementen zijn, verhoogt dat de hoeveelheid gegevens nodig om de levering voor te bereiden.  Meer informatie over personalisatie in [deze sectie](../../delivery/using/about-personalization.md)

* De server wordt geladen: wanneer de marketingserver verschillende taken tegelijk afhandelt, kan dit de prestaties vertragen. De marketingserver moet alle inkomende en uitgaande gegevens voor alle leveringen coördineren om ervoor te zorgen dat de gegevens correct en op tijd zijn.

   **TIP** - om dit te vermijden, coördineert het plannen van leveringen met de andere leden van uw team om de beste prestaties te verzekeren.

* De workflowuitvoering: het controleren van uw workflows is essentieel om problemen met de prestaties van het platform te voorkomen. Volg de richtlijnen [in dit document](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Als gehoste klant kunt u de mogelijkheden [van het deelvenster](https://docs.adobe.com/content/help/en/control-panel/using/discover-control-panel/key-features.html) Campagne Control gebruiken om uw platform te bewaken met behulp van de functies voor [prestatiebewaking](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) .

### Netwerkconfiguratie controleren {#network-config}

Om levering te optimaliseren wanneer het behandelen van e-mails in grote volumes en vermijd wordt verward voor spammer, zorg ervoor dat u een wettige netwerkconfiguratie hebt die niet probeert om de identiteit van de server te verbergen.

**Tip**:  Gebruik een transparant verzendadres dat overeenkomt met de website van uw merk. Het bedrijf TravelAgency beheert bijvoorbeeld de hotelketen Valentino. Zijn bezit het domein valentino.com voor zijn website. Om het hotel Valentino in Parijs te promoten, gebruikt het subdomein paris.valentino.com. Daarom kan een relevant afzenderadres hotel@paris.valentino.com zijn.

### Leverbaarheidsbeheer {#deliverability-management}

Om uw ontvangers&#39; te bereiken inbox zonder te stuiteren of als spam worden gemerkt, moet u het leverbaarheidstarief van uw berichten verbeteren.

* Wat is leverbaarheid?

   * Het verwijst naar de factoren van een e-mail die zijn capaciteit bepalen om door de server van een ontvanger worden goedgekeurd. ISPs (de Dienstverleners van Internet) filter uit e-mails die zij als SPAM identificeren, of zij blokkeren beelden van het downloaden. Als ze vaststellen dat een bepaald domein te veel e-mails verzendt, stellen ze een limiet in voor het aantal e-mails dat ze van die afzender accepteren.

   * Wanneer u uw e-mail controleert op leverbaarheid, wilt u zich op vier hoofdcategorieën concentreren: gegevenskwaliteit, bericht en inhoud, verzendende infrastructuur, en reputatie. Raadpleeg [deze sectie](../../delivery/using/about-deliverability.md)voor een dieper overzicht van dit onderwerp.

* Pas de aanbevelingen toe die [in dit document](../../delivery/using/deliverability-key-points.md)worden beschreven.

* Neem contact op met uw Adobe-vertegenwoordiger voor hulp.

### Quarantainebeheer {#quarantine-management}

Het is in uw belang om goede processen van het quarantainebeheer te handhaven.

Wanneer u e-mailberichten op een nieuw platform gaat verzenden, kunt u een lijst met adressen gebruiken die niet volledig zijn gekwalificeerd. Als u naar ongeldige adressen of naar honeypot-adressen (brievenbussen slechts die aan truc spammers worden gecreeerd) verzendt, zal dit de reputatie van uw platform beginnen te verminderen. Goede quarantainebeheerprocessen helpen: Houd de adreskwaliteit in stand, vermijd lijst van afgewezen personen door internettoegangsproviders en verlaag uw foutenpercentage, waardoor leveringen en doorvoer sneller verlopen.

**Tips**

* Als u een lijst met ongeldige adressen hebt, raadt Adobe u aan deze te importeren in de quarantainetabel via **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* De ontvangers de waarvan adressen quarantined zijn uitgesloten door gebrek tijdens de leveringsanalyse: zij zijn niet gericht . Hierdoor wordt de levering versneld, omdat het foutenpercentage een belangrijk effect heeft op de leveringssnelheid. Een e-mailadres kan in quarantaine worden geplaatst bijvoorbeeld wanneer inbox volledig is of als het adres niet bestaat. [Meer informatie](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign beheert onjuiste adressen op basis van het type geretourneerde fout. Raadpleeg [deze sectie](../../delivery/using/understanding-quarantine-management.md) voor meer informatie.


* Sommige internetproviders beschouwen e-mails automatisch als spam als het aantal ongeldige adressen te hoog is. Met quarantaine kunt u dus voorkomen dat u door deze providers aan een lijst van afgewezen personen wordt toegevoegd.

* Het beheer van quarantaines zal ook de verzendkosten van SMS helpen verminderen door onjuiste telefoonnummers uit te sluiten van leveringen.

### Dubbele opt-in-regeling {#double-opt-in}

Om te voorkomen dat berichten naar ongeldige adressen worden verzonden, onjuiste communicatie wordt beperkt en de reputatie van de afzender wordt verbeterd, raadt Adobe aan een dubbele opt-in-mechanisme in te voeren voor bevestiging na abonnement. Zo weet u zeker dat een ontvanger met opzet is geabonneerd.

De details voor de implementatie van dit mechanisme worden beschreven in [deze sectie](../../web/using/use-cases--web-forms.md).

## Sjablonen gebruiken {#use-templates}

De malplaatjes van de levering staan voor verhoogde efficiency toe door kant-en-klare scenario&#39;s voor de meeste gemeenschappelijke soorten activiteiten te verstrekken. Met malplaatjes, kunnen de marketers nieuwe campagnes met minimale aanpassing in een kortere hoeveelheid tijd opstellen.

Meer informatie over leveringssjablonen vindt u in [deze sectie](../../delivery/using/creating-a-delivery-template.md).

### Aan de slag met leveringssjablonen {#gs-templates}

Een [leveringsmalplaatje](../../delivery/using/creating-a-delivery-template.md) laat u toe om eens een reeks technische en functionele eigenschappen te bepalen die aan uw behoeften aanpassen en die voor toekomstige leveringen kunnen worden opnieuw gebruikt. U kunt dan tijd besparen en leveringen standaardiseren wanneer dat nodig is.

Als u meerdere merken beheert in Adobe Campaign, raadt Adobe aan één subdomein per merk te hebben. Een bank kan bijvoorbeeld verschillende subdomeinen hebben die overeenkomen met elk van haar regionale agentschappen. Als een bank eigenaar is van het domein bluebank.com, kunnen de subdomeinen @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, enz. zijn. Als u één leveringssjabloon per subdomein hebt, kunt u altijd de juiste vooraf geconfigureerde parameters voor elk merk gebruiken. Hierdoor worden fouten voorkomen en bespaart u tijd.

**Tip**:  Om configuratiefouten in Campaign Standard te vermijden, adviseren wij dat u een inheemse malplaatje dupliceert en zijn eigenschappen verandert eerder dan een nieuw malplaatje tot stand te brengen.

**Adressen configureren**

* Het adres van de afzender is verplicht om het verzenden van een e-mail toe te staan.

* Sommige ISPs (de Dienstverleners van Internet) controleren de geldigheid van het afzenderadres alvorens berichten goed te keuren.

* Een slecht geformuleerd adres kan ertoe leiden dat het door de ontvangende server wordt verworpen. U moet ervoor zorgen een correct adres wordt gegeven.

* Het adres moet de afzender uitdrukkelijk identificeren. Het domein moet eigendom zijn van en geregistreerd zijn bij de afzender.

* Adobe raadt u aan e-mailaccounts te maken die overeenkomen met de adressen die zijn opgegeven voor leveringen en antwoorden. Vraag de beheerder van het berichtensysteem om advies.

Voer de onderstaande stappen uit om adressen in de Campagne-interface te configureren:

1. Klik in de [leveringssjabloon](../../delivery/using/creating-a-delivery-template.md)op de **[!UICONTROL From]** koppeling. Vul in het **[!UICONTROL Email header parameters]** venster de volgende velden in:

   ![](assets/d_best_practices_email_header.png)

1. Controleer in het **[!UICONTROL Sender address]** veld of het adresdomein hetzelfde is als het subdomein dat u aan Adobe hebt gedelegeerd. U kunt het deel vóór &#39;@&#39; maar niet het domeinadres wijzigen.

1. Gebruik in het **[!UICONTROL From]** veld een naam die gemakkelijk kan worden herkend door de ontvangers, zoals de naam van uw merk, om de openingsfrequentie van uw leveringen te verhogen. Om de ervaring van de ontvanger verder te verbeteren, kunt u de naam van een persoon toevoegen, bijvoorbeeld &quot;Emma van Megastore&quot;.

1. In de **[!UICONTROL Reply address text]** dossiers, wordt het adres van de afzender gebruikt door gebrek voor antwoorden. Adobe raadt echter aan een bestaand reëel adres te gebruiken, zoals de klantenservice van uw merk. In dit geval, als een ontvanger een antwoord verzendt, zal de klantenzorg het kunnen behandelen.

**Een controlegroep instellen**

Nadat de levering is verzonden, kunt u het gedrag van de uitgesloten ontvangers vergelijken met de ontvangers die de levering wel hebben ontvangen. Vervolgens kunt u de efficiëntie van uw campagnes meten. Meer informatie over controlegroepen vindt u in [deze sectie](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Klik op de **[!UICONTROL To]** koppeling als u een controlegroep wilt instellen. Selecteer de **[!UICONTROL Select target]** tab in het **[!UICONTROL Control group]** venster. U kunt een gedeelte van het doel extraheren, bijvoorbeeld een willekeurig monster van 5%.

![](assets/d_best_practices_control_group.png)

**Typologieën gebruiken om filters of controleregels toe te passen**

Een typologie bevat controleregels die tijdens de analysefase worden toegepast, alvorens om het even welk bericht te verzenden.

Wijzig op het **[!UICONTROL Typology]** tabblad van de eigenschappen van de sjabloon de standaardtypologie naar wens.

Bijvoorbeeld, om het uitgaande verkeer beter te controleren, kunt u bepalen welke IP adressen kunnen worden gebruikt door één affiniteit per subdomein te bepalen en één typologie per affiniteit te creëren. De affiniteiten worden gedefinieerd in het configuratiebestand van de instantie. Neem contact op met uw Adobe Campaign-beheerder.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## Ontwerpen en aanpassen {#design-and-personalize}

Probeer bij het ontwerpen van de inhoud van uw bericht algemene problemen te vermijden die ertoe kunnen leiden dat u de levering niet kunt uitvoeren. Meestal hebben mogelijke fouten te maken met [personalisatie](../../delivery/using/about-personalization.md), [opmaak](../../delivery/using/defining-the-email-content.md#message-content) en [afbeeldingen](../../delivery/using/defining-the-email-content.md#adding-images).

### Aanpassing optimaliseren {#optimize-personalization}

Om veelvoorkomende problemen te voorkomen die ertoe kunnen leiden dat u uw levering niet kunt uitvoeren en om de ervaring van uw ontvangers te verbeteren, kunt u uw berichten aan uw persoonlijke voorkeur aanpassen.

U kunt de gegevens van ontvangers gebruiken die in de Adobe Campaign-database zijn opgeslagen, of die worden verzameld via tracking, landing pages, subscriptions, etc.
De grondbeginselen van de Personalisatie worden voorgesteld in [deze sectie](../../delivery/using/personalization-fields.md).

Zorg ervoor dat de inhoud van uw bericht goed is ontworpen om fouten te voorkomen die over het algemeen te maken hebben met personalisatie.

**Tips**: In verpersoonlijkingsgebieden die uit externe dossiers komen die door derdeverkopers worden verstrekt, kan de externe inhoud van HTML verkeerd zijn. Om dit te voorkomen, controleert u de syntaxis, het gebruik van tags, tekens, enzovoort. Een Adobe Campaign-personalisatie-tag heeft bijvoorbeeld altijd de volgende vorm: &lt;%=table.field%>. Zie [deze sectie](../../delivery/using/about-personalization.md)voor meer informatie.

Het onjuiste gebruik van parameters in verpersoonlijkingsblokken kan een kwestie zijn. Variabelen in JavaScript moeten bijvoorbeeld als volgt worden gebruikt:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

Voor meer op verpersoonlijkingsblokken, verwijs naar [deze sectie](../../delivery/using/personalization-blocks.md).

U kunt aanpassingsgegevens voorbereiden in een workflow om de voorbereiding van de levering te verbeteren. Dit moet speciaal worden gebruikt als de personalisatiegegevens afkomstig zijn van een externe tabel via Federated Data Access (FDA). Deze optie wordt beschreven in deze [sectie](../../delivery/using/personalization-fields.md#optimizing-personalization)

### Geoptimaliseerde inhoud maken {#optimize-content}

Houd rekening met de onderstaande algemene tips bij het samenstellen van e-mails.

* Ontwerp eenvoudig houden

* Houd mobiele gebruikers in gedachten

* Vermijd e-mails die volledig op afbeeldingen zijn gebaseerd

* E-mailveilige lettertypen gebruiken

* Speciale tekens coderen

**Onderworpen lijn** - Werk aan de [onderwerpregel](../../delivery/using/defining-the-email-content.md#message-content) om de open tarieven te verbeteren:

* Vermijd personen die te lang zijn. Gebruik maximaal 50 tekens

* Vermijd het gebruik van herhalende woorden zoals &quot;gratis&quot; of &quot;aanbieding&quot;, die als spam kunnen worden beschouwd

* Vermijd hoofdletters en speciale tekens zoals &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

**De pagina** van de spiegel - omvat altijd een spiegel paginakoppeling. De voorkeurspositie boven aan het e-mailbericht. [Meer informatie](../../delivery/using/sending-messages.md#generating-the-mirror-page)

**Unsubscription-koppeling** - De koppeling voor het opzeggen van abonnementen is essentieel. Het formulier moet zichtbaar en geldig zijn en moet functioneel zijn. Wanneer het bericht wordt geanalyseerd, controleert standaard een [typologische regel](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) of een opt-out-koppeling is opgenomen en wordt een waarschuwing gegenereerd als deze ontbreekt.

**Tip**: Omdat menselijke fout altijd mogelijk is, controleer dat de opt-out verbinding correct vóór elke keer werkt u verzendt. Als u bijvoorbeeld de proefdruk verzendt, controleert u of de koppeling geldig is, of het formulier online is en of het veld Geen contact meer opnemen met deze ontvanger is gewijzigd in Ja.

Leer hoe u een koppeling om te weigeren [in deze sectie](../../delivery/using/personalization-blocks.md#personalization-blocks-example)invoegt.

**E-mailgrootte** - Om problemen met prestaties of leverbaarheid te voorkomen, is de aanbevolen maximale grootte van een e-mailbericht ongeveer **35 kB**. Als u de berichtgrootte wilt controleren, gaat u naar het **[!UICONTROL Preview]** tabblad en kiest u een testprofiel. Zodra geproduceerd, zal de berichtgrootte in de hoogste juiste hoek worden getoond.

Houd rekening met het volgende om uw e-mailadres onder de limiet te houden:

* Overbodige of ongebruikte stijlen verwijderen

* Een deel van de e-mailinhoud naar een openingspagina verplaatsen

* Miniatuur uw code

Zorg ervoor dat u wijzigingen test voordat u de definitieve verzending uitvoert

**Sms-lengte**

Standaard voldoet het aantal tekens in een sms aan de gsm-standaarden (Global System for Mobile Communications). Sms-berichten met gsm-codering mogen maximaal 160 tekens bevatten of 153 tekens per sms voor berichten die in meerdere delen worden verzonden.

Transliteratie houdt in dat een teken van een sms door een ander teken wordt vervangen wanneer dat teken niet in aanmerking wordt genomen door de gsm-standaard. Als u personalisatievelden in de inhoud van uw SMS-bericht invoegt, kunnen er tekens worden ingevoerd waarmee de GSM-codering geen rekening houdt. U kunt tekentransliteratie autoriseren door het corresponderende vak te selecteren op het tabblad met SMPP-kanaalinstellingen van het corresponderende **[!UICONTROL External account]**.
Meer informatie [in deze sectie](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Tips**:

* Als u alle tekens in uw SMS-berichten wilt behouden, bijvoorbeeld als u eigennamen niet wilt wijzigen, moet u transliteratie niet inschakelen.

* Als uw SMS-berichten echter veel tekens bevatten waarmee de GSM-standaard geen rekening houdt, kunt u met transliteratie de verzendkosten van uw berichten beperken.

Meer informatie [in deze sectie](../../delivery/using/sms-channel.md#about-character-transliteration).

### Werken met opmaak {#formatting}

Controleer de volgende elementen om algemene opmaakfouten te voorkomen:

* Correcte **datumopmaak**: Adobe Campaign biedt functies voor datumopmaak voor de JavaScript-sjablonen en XSL-opmaakmodellen. [Meer informatie](../../delivery/using/formatting.md#date-display)

* Gebruik van **geoorloofde tekens** in e-mails: De lijst met geldige tekens voor e-mailadressen wordt gedefinieerd in de optie &quot;XtkEmail_Characters&quot;. Leer hoe u [in deze sectie](../../installation/using/configuring-campaign-options.md)toegang krijgt tot de opties voor campagnes. Adobe Campaign moet in Unicode zijn geïnstalleerd om speciale tekens correct te kunnen verwerken.

* Configuratie van **e-mailverificatie**: zorg ervoor dat de e-mailkopteksten de DKIM-handtekening bevatten. DKIM (Domeinsleutels Identified Mail) authentificatie staat de ontvangende e-mailserver toe om te verifiëren dat een bericht inderdaad werd verzonden door de persoon of de entiteit het beweert werd verzonden door, en of de berichtinhoud binnen tussen de tijd werd veranderd het oorspronkelijk werd verzonden (en DKIM &quot;ondertekend&quot;) en de tijd het werd ontvangen. Deze standaard gebruikt doorgaans het domein in de kop Van of Afzender. Raadpleeg [deze sectie](../../delivery/using/technical-recommendations.md#dkim) voor meer informatie.

* **Het responsieve e-mailontwerp** zorgt ervoor dat een e-mailbericht optimaal wordt weergegeven voor het apparaat waarop het wordt geopend.

   * Gebruik responsieve HTML-e-mail in plaats van HTML-webpagina.

   * Gebruik de voorvertoningsmodus en verzend proefdrukken om de rendering op zoveel mogelijk apparaten te testen.

   * De module Adobe Campaign Classic Digital Content Editor (DCE) bevat een aantal responsieve ontwerpsjablonen voor mobiele apparaten die beschikbaar zijn via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Lees meer [in dit artikel](https://theblog.adobe.com/responsive-email-design-101/).



### Afbeeldingen beheren {#manage-images}

Volg de onderstaande richtlijnen voor het gebruik van afbeeldingen.

* **Afbeeldingen blokkeren** voorkomen - Sommige e-mailclients blokkeren afbeeldingen standaard en sommige gebruikers wijzigen hun instellingen om afbeeldingen te blokkeren zodat ze op gegevensgebruik kunnen worden opgeslagen. Als afbeeldingen niet worden gedownload, kan het hele bericht verloren gaan. Om dit te voorkomen:

   * Verdeel uw inhoud met afbeelding en tekst. Vermijd e-mails die volledig op afbeeldingen zijn gebaseerd.

   * Als er tekst in een afbeelding moet staan, gebruikt u alt- en titeltekst om ervoor te zorgen dat uw bericht overloopt. Maak de alt-/titeltekst op om de weergave te verbeteren.

   * Vermijd het gebruik van achtergrondafbeeldingen, omdat deze niet door sommige e-mailclients worden ondersteund.

* **Afbeeldingen responsief** maken - Probeer afbeeldingen responsief te maken en de grootte ervan te wijzigen. Merk op dat dit een kosteneffect kan hebben aangezien het langer duurt om te bouwen.

* **Absolute verwijzingen naar** afbeeldingen gebruiken - Als u van buitenaf toegang wilt krijgen, moeten de afbeeldingen die worden gebruikt in e-mails en openbare bronnen die aan campagnes zijn gekoppeld, aanwezig zijn op een extern toegankelijke server.

   * U kunt controleren als de instantieconfiguratie openbaar middelbeheer toelaat. [Meer informatie](../../installation/using/deploying-an-instance.md#managing-public-resources)

   * Vanuit de wizard voor levering kunt u een HTML-pagina met afbeeldingen importeren of afbeeldingen rechtstreeks via het **[!UICONTROL Image]** pictogram invoegen in de HTML-editor. [Meer informatie](../../delivery/using/defining-the-email-content.md#adding-images)

   * Als afbeeldingen niet worden weergegeven, controleert u of de afbeeldingen beschikbaar zijn op de server. Klik hiertoe op het tabblad Bron van uw levering. Zoek uw afbeeldingen en kopieer en plak de URL van elke afbeelding in een webbrowser. Als de afbeeldingen niet worden weergegeven, neemt u contact op met uw IT-beheerder of de externe leverancier die uw leveringsinhoud levert.

### Een voorbeeld van uw bericht bekijken {#preview-msg}

Adobe raadt u aan een voorbeeld van uw bericht te bekijken om na te gaan wat de personalisatie is en hoe de ontvangers uw bericht zullen bekijken.

* In het bezorgingsbericht kunt u met het **[!UICONTROL Preview]** subtabblad de rendering van elke inhoud voor een ontvanger bekijken. De verpersoonlijkingsgebieden en de voorwaardelijke elementen van inhoud worden vervangen met de overeenkomstige informatie voor het geselecteerde profiel. [Meer informatie](../../delivery/using/defining-the-email-content.md#message-content)

* Tijdens elke voorvertoning wordt een automatische controle op anti-spam uitgevoerd. In het **[!UICONTROL Preview]** sub-lusje, controleer [SpamAssassin](../../delivery/using/spamassassin.md) spamscoring.  Klik voor meer informatie **[!UICONTROL More...]** over de waarschuwing.  Controleer voordat u dit doet of SpamAssassin op de juiste wijze is geïnstalleerd en geconfigureerd op de Adobe Campaign-toepassingsserver. [Meer informatie](../../installation/using/configuring-spamassassin.md)

## Het juiste doel definiëren {#define-the-right-target}

Gerichte populatie is van essentieel belang: uw lijsten zorgvuldig samen te stellen, uw e-mailberichten te testen op populaire e-mailclients en mobiele apparaten en ervoor te zorgen dat uw e-maillijsten up-to-date zijn (zonder onbekende of verouderde adressen). U kunt ook proefdrukken verzenden waarmee u een volledige validatiecyclus kunt instellen.

Meer informatie over doelpopulaties [in deze sectie](../../delivery/using/steps-defining-the-target-population.md)

### Doelgroep {#target-the-right-audience}

Wanneer u uw inhoud klaar hebt, moet u zorgvuldig bepalen wie uw bericht zal ontvangen.

Om uw levering succesvol te maken, wilt u de meest relevante gepersonaliseerde inhoud naar de juiste ontvangers verzenden. Met Adobe Campaign kunt u het meest nauwkeurige doel maken: u kunt ontvangers selecteren op basis van hun leeftijd, lokalisatie, wat ze hebben gekocht, als ze op een koppeling hebben geklikt in een vorige levering, enzovoort. Met Adobe Campaign kunt u ook testprofielen, controlegroepen en zaadadressen definiëren om te controleren of het doel correct is.

### Doeltoewijzingen {#target-mappings}

In Campaign Classic, door gebrek, richten de leveringsmalplaatjes **Ontvangers**. Adobe Campaign biedt andere doeltoewijzingen voor uw leveringen die u op basis van uw behoeften kunt wijzigen.

U kunt bijvoorbeeld leveren aan bezoekers van wie de profielen via sociale netwerken zijn verzameld of aan bezoekers die zijn geabonneerd op een informatieservice.

Deze toewijzingen worden weergegeven [in deze sectie](../../delivery/using/selecting-a-target-mapping.md).

U kunt ook een aangepaste doeltoewijzing maken en gebruiken. Raadpleeg [deze sectie](../../configuration/using/target-mapping.md) voor meer informatie.

### Externe ontvangers {#external-recipients}

U kunt leveren aan ontvangers die in een extern dossier eerder dan opgeslagen in het gegevensbestand worden opgeslagen. Meer informatie [in deze sectie](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

### Verzenden naar uw abonnees {#send-to-subscribers}

Om berichten naar de abonnees van een nieuwsbrief te verzenden, kunt u de abonnees aan de overeenkomstige informatiedienst direct richten. Meer informatie [in deze sectie](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


### Ontvangers en zaadadressen testen {#test-recipients-seed-addresses}

Om uw levering te testen, gebruik proef alvorens naar het belangrijkste doel te verzenden.

Zorg ervoor dat u de juiste ontvangers voor het bewijs selecteert, omdat deze het formulier en de inhoud van het bericht valideren. De stappen voor het definiëren van de ontvangers van het bewijs worden [in deze sectie](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target)weergegeven.

De zaadadressen worden gebruikt aan doelontvangers die niet aan de bepaalde doelcriteria voldoen om een levering te testen alvorens naar het belangrijkste doel te verzenden. Ze worden [in deze rubriek](../../delivery/using/about-seed-addresses.md)weergegeven.

### Gedupliceerde adressen {#deduplicate-addresses}

Het is belangrijk om dubbele e-mailadressen te vermijden, omdat dit van invloed kan zijn op uw doel:

* Hetzelfde bericht kan meerdere keren worden verzonden wanneer een doel wordt gesplitst.

* Als een ontvanger zich afmeldt na het ontvangen van een bericht, zal hun dubbele profiel nog toekomstige berichten ontvangen.

Deduplicating adressen beschermt uw verzendende reputatie en verzekert goed quarantainebeheer.

Klik hier als je meer wilt weten [over deze kwestie](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery).


### E-mailadressen indexeren {#index-addresses}

Om de prestaties van de SQL vragen te optimaliseren die in de toepassing worden gebruikt, kan een index van het belangrijkste element van het gegevensschema worden verklaard.

De stappen voor het toevoegen van een index aan het e-mailadres worden beschreven [in deze sectie](../../configuration/using/database-mapping.md#indexed-fields).

## Alle controles uitvoeren voordat ze worden verzonden {#perform-all-checks}

Zodra uw bericht klaar is, zorg ervoor zijn inhoud correct, op alle apparaten wordt getoond, en bevat geen fouten zoals verkeerde verpersoonlijking of gebroken verbindingen.

Alvorens uw bericht te verzenden, zorg ook dat de parameters en de configuratie met de levering verenigbaar zijn.

### Validatie is een sleutel {#validation-is-key}

Alvorens een levering te verzenden, moet u ervoor zorgen dat uw ontvangers het bericht zullen ontvangen dat u echt hen wilt verzenden. Hiervoor moet u de inhoud en de leveringsparameters van het bericht valideren.

Met deze stap kunt u mogelijke fouten detecteren en corrigeren voordat u deze aan uw hoofddoel kunt leveren.

De stappen voor het valideren van een levering worden weergegeven [in deze sectie](../../delivery/using/steps-validating-the-delivery.md).

### Inbox rendering {#inbox-and-email-rendering}

Met Postvak-rendering kunt u uw berichten voorvertonen bij belangrijke e-mailclients, inhoud en reputatie scannen en ontdekken hoe ontvangers berichten lezen.

**Tips**:

* U kunt het verzonden bericht bekijken in de verschillende contexten waarin het kan worden ontvangen: webmail, berichtservice, mobiel, enz.

* Rendermogelijkheden in postvakken zijn van cruciaal belang om te bepalen of uw e-mailcampagnes erin slagen het voorbij de filters van belangrijke ISP&#39;s (Internet Service Providers) en webmailservices te maken. Dergelijke hulpmiddelen verzenden een pre-vlucht exemplaar van een e-mail naar een netwerk van testinboxes, zodat kunt u zien hoe het bericht, over deze diensten zal tonen of teruggeven. Ze kunnen ook rapporten en opties voor codecorrectie bevatten die u helpen snel oplossingen te vinden en te maken die de leesbaarheid verbeteren.

Meer informatie [in deze sectie](../../delivery/using/inbox-rendering.md).

### Proefberichten {#proof-messages}

Door proefdrukken te verzenden, kunt u de koppeling om te weigeren controleren, de pagina spiegelen en andere koppelingen controleren, het bericht valideren, controleren of afbeeldingen worden weergegeven, mogelijke fouten opsporen, enz. Mogelijk wilt u ook uw ontwerp en rendering op verschillende apparaten controleren.

Meer informatie [in deze sectie](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### A/B-testleveringen instellen {#a-b-testing-deliveries}

Als u meerdere inhoud voor een e-maillevering hebt, kunt u A/B-tests gebruiken om na te gaan welke versie de grootste invloed heeft op de doelpopulatie.

**Tips**:

* Verschillende versies naar sommige ontvangers verzenden

* Selecteer het bestand met de hoogste successnelheid en stuur het naar de rest van het doel

Meer informatie [in deze sectie](../../workflow/using/a-b-testing.md).

### Controleer of je bericht is bezorgd {#make-sure-your-message-is-delivered}

Als laatste stap maximaliseert u uw kansen en gebruikt u de kracht van Adobe Campaign Classic om ervoor te zorgen dat uw bericht ook daadwerkelijk aan de relevante ontvangers wordt bezorgd.

**Doorloop een validatieproces** - U kunt een volledig validatieproces definiëren, waarbij Adobe Campaign-operatoren en -groepen betrokken zijn, om zowel het doel als de berichtinhoud te valideren. Dit zal zorgen voor volledige controle en controle op de verschillende processen van de campagne: het richten, inhoud, begroting, extractie, en het verzenden van een bewijs. Afhankelijk van hun machtigingen zullen gebruikers op de hoogte worden gesteld, proefdrukken ontvangen en het bericht kunnen valideren of afwijzen. Meer informatie [in deze sectie](../../campaign/using/marketing-campaign-approval.md#approval-process).

**Golven** gebruiken - U kunt het verzonden volume progressief verhogen gebruikend golven. Zo voorkomt u dat uw berichten als spam worden gemarkeerd of dat u het aantal berichten per dag wilt beperken. Met golven kunt u leveringen in verschillende batches verdelen in plaats van tegelijkertijd grote volumes berichten te verzenden. Meer informatie [in deze sectie](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

**Prioriteit geven aan berichten** - U kunt de verzendende orde voor uw leveringen plaatsen door het prioritaire niveau te verklaren. Dit doet u als volgt:

1. Bewerk de leveringseigenschappen en selecteer het **[!UICONTROL Delivery]** tabblad.

1. Definieer het prioriteitsniveau voor de levering op een schaal van **[!UICONTROL Very low]** naar **[!UICONTROL Very high]**.

>[!NOTE]
>
>Het is niet mogelijk om de volgorde te bepalen waarin berichten worden verzonden vanuit een levering.

**IP van de opstelling Verbindingen** - om het uitgaande verkeer beter te controleren SMTP, kunt u affiniteiten beheren door te bepalen welke specifieke IP adressen voor elke affiniteit kunnen worden gebruikt. Hiermee kunt u het aantal e-mails voor specifieke leveringen beperken tot computers of uitvoeradressen. U kunt bijvoorbeeld één affiniteit per land of subdomein gebruiken. Vervolgens kunt u één typologie per land maken en elke affiniteit koppelen aan de overeenkomstige typologie.

U kunt:

* Definieer de IP-affiniteiten in het configuratiebestand serverConf.xml. [Meer informatie](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Voor elk element IPAffinity, verklaar de IP adressen die kunnen worden gebruikt. [Meer informatie](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* In de [typologie](../../campaign/using/about-campaign-typologies.md) van uw keuze, gebruik het **[!UICONTROL Managing affinities with IP addresses]** gebied om leveringen aan de leveringsserver (MTA) te verbinden die bovengenoemde affiniteit beheert. [Meer informatie](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Zodra e-mail wordt verzonden, controleer de kopbal om te verifiëren welk IP adres de levering van werd verzonden. De e-mailbeheerder moet u helpen de koptekstgegevens op te halen.

>[!NOTE]
>
>De meeste van deze stappen kunnen slechts door een deskundige gebruiker worden uitgevoerd.

**Typologieën** gebruiken - U kunt typologische regels gebruiken om een deel van het doel uit te sluiten op basis van specifieke criteria. Dit garandeert dat de verzonden berichten het best aan de behoeften en de verwachtingen van klanten voldoen, in overeenstemming met het beleid van het bedrijfs communicatie. U kunt bijvoorbeeld de ontvangers die jonger zijn, filteren van het doel van de nieuwsbrief. Meer informatie [in dit voorbeeld](../../campaign/using/filtering-rules.md).

**Bijlagen** vermijden - Bijlagen blijven een van de meest voorkomende vectoren voor de proliferatie van malware, vooral wanneer ze in bulk worden verzonden. Neem een beveiligde koppeling naar het document op in plaats van deze te koppelen. Dit verzekert een extra laag van veiligheid om onbedoelde herdistributie te verhinderen, en vermindert enorm de kansen dat het bericht bij binnenkomende e-mailgateways voor berichtgrootte of veiligheidsredenen zal worden verworpen.

## Track en monitor {#track-and-monitor}

Hebt u op de knop Verzenden geklikt? Laten we eens kijken wat er gebeurt. Zodra de levering wordt verzonden, laat Adobe Campaign u toe om spoor van de verzonden berichten te houden en te ontdekken hoe uw ontvangers op uw levering reageren. Op deze manier kunt u uw volgende campagnes beter verzenden en optimaliseren.

### Bewaking van leveringen {#monitoring-deliveries}

Om uw campagnes te controleren, moet u ervoor zorgen dat het bericht inderdaad aan uw ontvangers is geleverd.

Van het dashboard van de levering van de Campagne, kunt u de verwerkte berichten en de logboeken van de leveringscontrole controleren.
U kunt de status van de berichten in de leveringslogboeken ook controleren. [Meer informatie](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

Wat gebeurt er als de leveringen niet worden verzonden en hun status **in behandeling** blijft?

* Het uitvoeringsproces wacht op de beschikbaarheid van sommige bronnen. De MTA is mogelijk niet gestart.
Controleer of uw modules mta@instance op uw servers MTA worden gelanceerd en begin indien nodig de module MTA. [Meer informatie](../../production/using/administration.md).

* De levering kan een affiniteit gebruiken die niet op de verzendende instantie is gevormd.
Tip: Controleer de configuratie van verkeersbeheer (IP affiniteit). Voor meer op dit, zie het uitgaande verkeer SMTP van de Controle.

>[!NOTE]
>
>Deze stappen kunnen slechts door een deskundige gebruiker worden uitgevoerd.

### Tracking {#tracking-deliveries}

Om het gedrag van uw ontvangers beter te kennen, kunt u volgen hoe zij op een levering reageren: ontvangen, openen, klikken op koppelingen, abonnementen enz. In Campaign Classic wordt deze informatie weergegeven op het tabblad Tracking van de ontvangers die de levering als doel heeft en op het tabblad Tracking van de levering. In Campaign Standard, wordt het getoond in het Volgen logboeken tabel van de levering.

**Tip**: Berichten bijhouden is standaard ingeschakeld. Als u URL&#39;s wilt configureren, selecteert u de optie URL&#39;s weergeven in de onderste sectie van de wizard voor levering. Voor elke URL van het bericht kunt u kiezen of u reeksspatiëring wilt activeren.

Voor meer op dit, verwijs naar de het [Vormen het volgen](../../delivery/using/how-to-configure-tracked-links.md) sectie en de beschrijving van de indicatoren [van het](../../reporting/using/delivery-reports.md#tracking-indicators) Volgen.

### Leveringsprestaties {#delivery-performances}

Om de snelheid te meten waarbij de berichten worden geleverd, kunt u de leveringsproductie controleren. De criteria zijn het aantal berichten die per uur worden verzonden en de grootte van de berichten (in beetjes per seconde). Voor meer op dit, zie de [productie](../../reporting/using/global-reports.md#delivery-throughput)van de Levering.

**Tips**:

* Bewaar de levering niet in mislukte staat op het geval, aangezien dit tijdelijke lijsten handhaaft en de prestaties beïnvloedt.

* Verwijder leveringen die niet meer nodig zijn en inactieve ontvangers uit de database om de adreskwaliteit te behouden.

* Probeer geen grote leveringen samen te plannen. Houd er rekening mee dat het 5 tot 10 minuten kan duren voordat de laadbewerking gelijkmatig over het systeem is verspreid.

## Problemen met levering oplossen {#delivery-troubleshooting}

Specifieke acties kunnen worden uitgevoerd wanneer problemen met leveringen optreden:

* [Leverbaarheidsproblemen](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemen met weergave van afbeeldingen](../../production/using/image-display-issues.md)

* [Leveringsprestaties](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Uitgave van tijdelijke bestanden](../../production/using/temporary-files.md) - alleen *klanten op locatie*
