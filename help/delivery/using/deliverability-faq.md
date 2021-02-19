---
solution: Campaign Classic
product: campaign
title: Belangrijkste punten bij het beheren van de leverbaarbaarheid in Adobe Campaign Classic
description: Wat zijn de belangrijkste punten om te controleren wanneer het beheren van leverbaarheid in Adobe Campaign Classic?
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '1343'
ht-degree: 1%

---


# Probleemoplossing voor levering{#deliverability-faq}

Ondervindt u een probleem met de leesbaarheid? U kunt hier de oplossing vinden.

## MX-regelfout {#mx-rule-error}

**Wat betekent het foutbericht &#39;quota gehaald&#39;?**

Dit bericht geeft aan dat u de quota voor een specifieke MX hebt bereikt en dat u moet wachten om nog een e-mail naar deze provider te kunnen verzenden.

In Adobe Campaign is er een configuratie voor het aantal e-mails per uur dat kan worden verzonden. Deze configuratie moet met waakzaamheid worden gebruikt, aangezien het aantal in het geval wordt bepaald het aantal verbindingen die met ISP worden uitgevoerd en niet het aantal daadwerkelijk verzonden e-mails betreft.

Dit betekent dat een verbinding een MX-regel kan gebruiken zonder dat een e-mail is verzonden. In dit geval, zal een configuratie met IP of een domein met een lage reputatie verscheidene verbindingen moeten proberen alvorens een e-mail te verzenden. Voor elke poging, zal een berichten per uurkrediet worden gebruikt. Als gevolg hiervan zullen de prestaties van de marketingcampagne aanzienlijk worden beïnvloed.

Daarom is &#39;met quota&#39;s tegemoet gekomen&#39; niet alleen een configuratieprobleem, maar kan het ook worden gekoppeld aan reputatie. Het is belangrijk om foutenmeldingen in [SMTP logboek](../../production/using/monitoring-processes.md#smtp-errors-per-domain) te analyseren.

Zie [deze sectie](../../installation/using/email-deliverability.md#mx-configuration) voor meer informatie over MX-configuratie.

## Hetzelfde foutbericht voor een ISP {#same-error-for-an-isp}

**Waarom krijg ik altijd het zelfde foutenbericht voor bepaalde ISP?**

Als u altijd het zelfde foutenbericht voor ISP krijgt, kan uw e-mail of IP als gebrek door ISP worden ontdekt. Voer de volgende aanbevelingen uit:
* Controleer of u een groot percentage fouten ontvangt die zijn gekoppeld aan onbestaande e-mailadressen (**Onbekende gebruiker** fouten).
* Werk uw abonnementsformulieren bij om fouten in de ingevoerde domeinnamen op te sporen (bijvoorbeeld: gmaul.com of yaho.com).
* Als u fouten opmerkt die verklaren dat uw berichten als spam worden verklaard, of dat uw berichten constant worden geblokkeerd, probeer exclusief de ontvangers die niet in één van uw berichten in de laatste 12 maanden van het doel hebben geopend of geklikt.

Als het probleem aanhoudt, neemt u contact op met de service voor commercieel gebruik of voor levering, [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Lijst van gewezen personen versus quarantaine {#denylist-versus-quarantine}

* **Wat is het verschil tussen een e-mailadres op lijst van gewezen personen en een quarantined e-mailadres?**

   * De status **[!UICONTROL Denylisted]** is een resultaat van een feedbacklus (wanneer een persoon een bericht rapporteert als spam).

   * De status **[!UICONTROL Quarantined]** is het resultaat van een zachte of harde stuit.
   Zie [deze sectie](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)voor meer informatie.

* **Wat betekenen de verschillende redenen voor quarantainefouten?**

   Hier volgen tien mogelijke redenen: niet bepaald, gebruiker onbekend, ongeldig domein, op lijst van gewezen personen, geweigerd, fout genegeerd, onbereikbaar, rekening gehandicapt, brievenbus volledig, niet verbonden.

   Voor meer op dit, zie [Het begrip quarantainebeheer](../../delivery/using/understanding-quarantine-management.md).

## Verwijderen uit lijst van gewezen personen {#remove-from-denylist}

* **Een van mijn ontvangers is per ongeluk aan de lijst van gewezen personen toegevoegd. Hoe verwijder ik hen uit ontkenner zodat ik kan beginnen hen berichten opnieuw te verzenden?**

   * Ga naar **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * Stel in de details van de corresponderende record de waarde van het veld **[!UICONTROL Status]** in op **[!UICONTROL Valid]**.
   * Sla de record op.

* **Hoe kan ik te weten komen of één van mijn IPs op een lijst van gewezen personen is? Hoe verwijder ik mijn IP(s) uit een lijst van gewezen personen?**

   Om te controleren of uw IP adres op een lijst van gewezen personen is, kunt u diverse websites gebruiken om het te verifiëren, zoals:
   * [MX-gereedschapset](https://mxtoolbox.com/)
   * [Wat is mijn IP adres](https://whatismyipaddress.com)

   Over het algemeen, zal het resultaat van de IP adrescontrole een lijst terugkeren die details van de lijst van gewezen personen en ook de naam van de website bevat die het IP adres ontkende.

   Als u op de desbetreffende koppeling klikt, hebt u toegang tot de gegevens van de website. Vervolgens kunt u vragen dat uw website wordt verwijderd van de website die het IP-adres aan de lijst van gewezen personen heeft toegevoegd.

   >[!NOTE]
   >
   >Het verwijderingsproces kan afhankelijk van de website variëren. Sommige plaatsen vereisen u om een rekening tot stand te brengen, terwijl anderen enkel u nodig hebben om het IP adres te verstrekken.

## Aanbevolen procedures {#best-practices}

Hieronder vindt u een aantal tips en trucs die u kunnen helpen om problemen met betrekking tot de prestaties op te sporen en aan te pakken.

### Identificeer een probleem van de leverbaarheid {#identify-deliverability-issue}

De volgende elementen kunnen uw aandacht vestigen:

* Meting van mailadres of campagne: afmelden, klachten over misbruik en/of stuitpercentages zijn hoger dan normaal.
* Abonnementsactiviteiten: openen, klikken en/of transacties zijn lager dan normaal.
* Zaadaccounts geven gefilterde of niet-geleverde mails weer.

### Mogelijke oorzaken voor hypothetisch formaat{#potential-causes}

Stel uzelf de volgende vragen om de mogelijke oorzaken van het probleem van de leverbaarheid te achterhalen:

* Was er een recente wijziging in de segmentatie van lijsten?
* Heb ik nieuwe gegevensbronnen verkregen?
* Heb ik per ongeluk een quarantainebestand gepost?
* Kan het probleem worden veroorzaakt door mijn berichtinhoud?
* Verzend ik vaak genoeg om warme IPs te handhaven?
* segmenteer ik mijn berichten op activiteit/betrokkenheid, of verzend volledig-dossiers?
* Wat is het &#39;veilige&#39; segment in mijn bestand wat betreft recentie?
* Beschikt ik over strategieën voor reactivering en herbevestiging voor segmenten die niet als veilig worden gedefinieerd?

### Het probleem {#address-issue} aanpakken

**Klachten**

Klachten worden gedefinieerd door abonnees die **e-mail rapporteren als spam** door de bijbehorende knop vanuit hun Postvak IN te drukken.

Als uw bezorgingsprobleem is veroorzaakt door klachten:
* U moet proberen te bepalen waarom de ontvangers klagen.
* Je kunt ook overwegen om je afmeldingskoppeling naar de bovenkant van je e-mail te verplaatsen. Dit zal abonnees aanmoedigen om zich af te melden in plaats van met de spamknoop te klagen.

Afzenders kunnen een schat aan informatie uit hun [terugkoppelingslus](../../delivery/using/technical-recommendations.md#feedback-loop) klachten genereren:
* Het is belangrijk om de gegevens op te nemen en te zoeken naar patronen in zaken als opt-in-bron, hoe lang het adres is ingetekend, of zelfs bepaalde gedrags-demografie.
* Klachten kunnen vaak een riskante gegevensbron of segment in het bestand identificeren. Risky wordt gedefinieerd als het meest waarschijnlijk om te klagen, wat reputatie, en beurtelings, inbox tarieven kan beschadigen.

De klachten zijn ook afkomstig van abonnees die gewoon geen e-mail meer willen ontvangen:
* Dit kan vaak toe te schrijven zijn aan overseinen, de perceptie van uw abonnees van het bericht, dat zij niet het bericht verwachtten, of zich niet het kiezen binnen herinneren.
* Het is ook belangrijk om een controle in werking te stellen om ervoor te zorgen dat alle punten van inzameling duidelijk zijn, en dat er geen vooraf gecontroleerde dozen in uw punten van verwerving zijn.
* U moet ook een welkomstbericht sturen wanneer abonnees zich aanmelden om de toon te bepalen en uit te leggen hoe vaak ze e-mails van u kunnen ontvangen.

**Geldigheid van gegevens**

**De harde** grenzen komen voor wanneer u naar een  **niet te leveren** adres ISP verzendt. Een adres kan om vele redenen zoals:
* Onjuist gespeld adres. Dit kan worden opgelost met een realtime service voor gegevensvalidatie, of door een bevestigde aanmeldingsprocedure te vereisen voordat marketinge-mails naar dat adres worden verzonden.
* Onjuiste lijst of gegevensbron. Als het uit een nieuwe bron komt, herzie hoe de adressen werden verzameld en zorg ervoor dat er toestemming was.
* Verzenden naar een adres dat op een bepaald moment actief was, maar na een periode van inactiviteit is gesloten of beëindigd.

**Betrokkenheid**

Naast klachten en gegevensgeldigheid concentreren ISPs zich meer dan ooit op **positieve overeenkomst** om leveringsbesluiten te nemen. Ze kijken of je abonnees je e-mails openen of ze verwijderen zonder ze te lezen. Omdat deze gegevens niet worden gedeeld met afzenders, moeten we de beschikbare informatie gebruiken en de taken voor het openen, klikken en uitvoeren als betrokkenheid vertalen.

Als deel van aan de gang zijnde reputatie het onderhoud, is het belangrijk om te begrijpen hoe betrokken abonnees op uw lijst zijn en een **recency risicopiërarchie** voor de abonnees op elk dossier ontwikkelen. Recentie wordt gedefinieerd als laatste open-/klikdatum, -datum of -datum. Dit tijdkader kan verticaal verschillen. Dit doet u als volgt:

1. Bepaal actieve (&quot;veilige&quot;) segmenten voor elke verticaal. Dit zijn typisch abonnees die binnen de laatste 3-6 maanden actief zijn geweest.
1. Verminder de frequentie tot inactieven.
1. Maak een [re-engagement](../../delivery/using/re-engagement-best-practices.md) reeks voor matige risico-inactieven. Dit is doorgaans 6 tot 9 maanden zonder betrokkenheid.
1. Ontwikkelen van een herbevestigingscampagne voor inactieven met een hoger risico. Dit zijn doorgaans abonnees die in 9 tot 12 maanden geen e-mailberichten hebben ontvangen.
1. Stel ten slotte een keuzeregel in en verwijder abonnees die uw e-mails niet hebben geopend in &#39;x&#39; maanden. We raden doorgaans 12+ maanden aan, maar dit kan verschillen afhankelijk van de verkoop- en aankoopcyclus.
