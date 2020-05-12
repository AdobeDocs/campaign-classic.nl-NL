---
title: Belangrijkste punten bij het beheren van de prestaties in Adobe Campagne Classic
description: Wat zijn de belangrijkste punten om te controleren bij het beheren van de prestaties in Adobe Campaign Classic?
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 15581517df8d2f397285bbadebd83b7f4539dfd7
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 0%

---


# Probleemoplossing voor levering{#deliverability-faq}

Ondervindt u een probleem met de leesbaarheid? U kunt hier de oplossing vinden.

## MX-regelfout {#mx-rule-error}

**Wat betekent het foutbericht &#39;quota gehaald&#39;?**

Dit bericht geeft aan dat u de quota voor een specifieke MX hebt bereikt en dat u moet wachten om nog een e-mail naar deze provider te kunnen verzenden.

In de Campagne van Adobe, is er een configuratie betreffende het aantal e-mails per uur dat kan worden verzonden. Deze configuratie moet met waakzaamheid worden gebruikt, aangezien het aantal in het geval wordt bepaald het aantal verbindingen die met ISP worden uitgevoerd en niet het aantal werkelijk verzonden e-mails betreft.

Dit betekent dat een verbinding een MX-regel kan gebruiken zonder dat een e-mail is verzonden. In dit geval, zal een configuratie met IP of een domein met een lage reputatie verscheidene verbindingen moeten proberen alvorens een e-mail te verzenden. Voor elke poging, zal een berichten per uurkrediet worden gebruikt. Als gevolg hiervan zullen de prestaties van de marketingcampagne aanzienlijk worden beïnvloed.

Daarom is &#39;met quota&#39;s tegemoet gekomen&#39; niet alleen een configuratieprobleem, maar kan het ook worden gekoppeld aan reputatie. Het is belangrijk om foutenmeldingen in het logboek [te analyseren](../../production/using/monitoring-processes.md#smtp-errors-per-domain)SMTP.

Voor meer op MX configuratie, zie [deze sectie](../../installation/using/email-deliverability.md#mx-configuration).

## Hetzelfde foutbericht voor een ISP {#same-error-for-an-isp}

**Waarom krijg ik altijd het zelfde foutenbericht voor bepaalde ISP?**

Als u altijd het zelfde foutenbericht voor ISP krijgt, kan uw e-mail of IP als gebrek door ISP worden ontdekt. Voer de volgende aanbevelingen uit:
* Controleer of u een groot percentage mislukkingen ontvangt die zijn gekoppeld aan onbestaande e-mailadressen (**Onbekende** fouten van gebruiker).
* Werk uw abonnementsformulieren bij om fouten in de ingevoerde domeinnamen op te sporen (bijvoorbeeld: gmaul.com of yaho.com).
* Als u fouten opmerkt die verklaren dat uw berichten als spam worden verklaard, of dat uw berichten constant worden geblokkeerd, probeer exclusief de ontvangers die niet in één van uw berichten in de laatste 12 maanden van het doel hebben geopend of geklikt.

Als het probleem zich blijft voordoen, neemt u contact op met de commerciële services of de services voor de levering, de Adobe Campagne Client Care of de Adobe Campagne-ondersteuning.

## Zwarte lijst versus quarantaine {#blacklisting-versus-quarantine}

* **Wat is het verschil tussen een e-mailadres dat op de zwarte lijst staat en een e-mailadres dat in quarantaine is geplaatst?**

   * De status **[!UICONTROL Blacklisted]** is een resultaat van een feedbacklus (wanneer een persoon een bericht rapporteert als spam).

   * De status **[!UICONTROL Quarantined]** is het resultaat van een zachte of harde stuit.
   Zie [deze sectie](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-blacklisting)voor meer informatie.

* **Wat betekenen de verschillende redenen voor quarantainefouten?**

   Hier volgen tien mogelijke redenen: niet gedefinieerd, gebruiker onbekend, ongeldig domein, adres op de zwarte lijst, geweigerd, fout genegeerd, onbereikbaar, account uitgeschakeld, postvak vol, niet verbonden.

   Voor meer op dit, zie het [Begrip van quarantainebeheer](../../delivery/using/understanding-quarantine-management.md).

## Uitschakelen {#unblacklisting}

* **Een van mijn ontvangers was per ongeluk op de zwarte lijst gezet. Hoe maak ik de zwarte lijst ongedaan zodat ik ze opnieuw kan versturen?**

   * Ga naar **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * Stel in de details van de corresponderende record de waarde van het **[!UICONTROL Status]** veld in op **[!UICONTROL Valid]**.
   * Sla de record op.

* **Hoe kan ik weten of één van mijn IPs zwarte lijst is? Hoe maak ik mijn IP(s) niet op de zwarte lijst?**

   Om te controleren of uw IP adres zwarte lijst is, kunt u diverse websites gebruiken om het te verifiëren:
   * [https://mxtoolbox.com/](https://mxtoolbox.com/)
   * [https://whatismyipaddress.com/blacklist-check](https://whatismyipaddress.com/blacklist-check)
   * [https://www.blacklistalert.org/](https://www.blacklistalert.org/)
   Over het algemeen, zal het resultaat van de IP adrescontrole een lijst terugkeren die details van de zwarte lijst en ook de naam van de website bevat die het IP adres zwarte lijst maakt.

   Als u op de desbetreffende koppeling klikt, hebt u toegang tot de gegevens van de website. Vervolgens kunt u vragen dat uw website wordt verwijderd van de website die het IP-adres op een zwarte lijst zet.

   >[!NOTE]
   >
   >Het verwijderingsproces kan afhankelijk van de website variëren. Sommige plaatsen vereisen u om een rekening tot stand te brengen, terwijl anderen enkel u nodig hebben om het IP adres te verstrekken.

## Aanbevolen procedures {#best-practices}

Hieronder vindt u een aantal tips en trucs die u kunnen helpen om problemen met betrekking tot de prestaties op te sporen en aan te pakken.

### Identificeer een leveringsprobleem {#identify-deliverability-issue}

De volgende elementen kunnen uw aandacht vestigen:

* Meting van mailadres of campagne: afmelden, klachten over misbruik en/of stuitpercentages zijn hoger dan normaal.
* Abonnementsactiviteiten: openen, klikken en/of transacties zijn lager dan normaal.
* Zaadaccounts geven gefilterde of niet-geleverde mails weer.

### Mogelijke hypothetische oorzaken {#potential-causes}

Stel uzelf de volgende vragen om de mogelijke oorzaken van het probleem van de leverbaarheid te achterhalen:

* Was er een recente wijziging in de segmentatie van lijsten?
* Heb ik nieuwe gegevensbronnen verkregen?
* Heb ik per ongeluk een quarantainebestand gepost?
* Kan het probleem worden veroorzaakt door mijn berichtinhoud?
* Verzend ik vaak genoeg om warme IPs te handhaven?
* segmenteer ik mijn berichten op activiteit/betrokkenheid, of verzend volledig-dossiers?
* Wat is het &#39;veilige&#39; segment in mijn bestand wat betreft recentie?
* Beschikt ik over strategieën voor reactivering en herbevestiging voor segmenten die niet als veilig worden gedefinieerd?

### Het probleem verhelpen {#address-issue}

**Klachten**

Klachten worden gedefinieerd door abonnees die e-mail **rapporteren als spam** door op de bijbehorende knop te drukken vanuit hun inbox.

Als uw bezorgingsprobleem is veroorzaakt door klachten:
* U moet proberen te bepalen waarom de ontvangers klagen.
* Je kunt ook overwegen om je afmeldingskoppeling naar de bovenkant van je e-mail te verplaatsen. Dit zal abonnees aanmoedigen om zich af te melden in plaats van met de spamknoop te klagen.

Afzenders kunnen een schat aan informatie uit hun [feedback loop](../../delivery/using/technical-recommendations.md#feedback-loop) klachten genereren:
* Het is belangrijk om de gegevens op te nemen en te zoeken naar patronen in zaken als opt-in-bron, hoe lang het adres is ingetekend, of zelfs bepaalde gedrags-demografie.
* Klachten kunnen vaak een riskante gegevensbron of segment in het bestand identificeren. Risky wordt gedefinieerd als het meest waarschijnlijk om te klagen, wat reputatie, en beurtelings, inbox tarieven kan beschadigen.

De klachten zijn ook afkomstig van abonnees die gewoon geen e-mail meer willen ontvangen:
* Dit kan vaak toe te schrijven zijn aan overseinen, de perceptie van uw abonnees van het bericht, dat zij niet het bericht verwachtten, of zich niet het kiezen binnen herinneren.
* Het is ook belangrijk om een controle in werking te stellen om ervoor te zorgen dat alle punten van inzameling duidelijk zijn, en dat er geen vooraf gecontroleerde dozen in uw punten van verwerving zijn.
* U moet ook een welkomstbericht sturen wanneer abonnees zich aanmelden om de toon te bepalen en uit te leggen hoe vaak ze e-mails van u kunnen ontvangen.

**Geldigheid van gegevens**

**De harde stuitingen** komen voor wanneer u naar een **niet te leveren adres** bij ISP verzendt. Een adres kan om vele redenen zoals:
* Onjuist gespeld adres. Dit kan worden opgelost met een realtime service voor gegevensvalidatie, of door een bevestigde aanmeldingsprocedure te vereisen voordat marketinge-mails naar dat adres worden verzonden.
* Onjuiste lijst of gegevensbron. Als het uit een nieuwe bron komt, herzie hoe de adressen werden verzameld en zorg ervoor dat er toestemming was.
* Verzenden naar een adres dat op een bepaald moment actief was, maar na een periode van inactiviteit is gesloten of beëindigd.

**Betrokkenheid**

Naast klachten en gegevensgeldigheid concentreren ISPs zich meer dan ooit op **positieve betrokkenheid** om leveringsbesluiten te nemen. Ze kijken of je abonnees je e-mails openen of ze verwijderen zonder ze te lezen. Omdat deze gegevens niet worden gedeeld met afzenders, moeten we de beschikbare informatie gebruiken en de taken voor het openen, klikken en uitvoeren als betrokkenheid vertalen.

Als deel van aan de gang zijnde reputatie, is het belangrijk om te begrijpen hoe betrokken abonnees op uw lijst zijn en een **recency risicopiërarchie** voor de abonnees op elk dossier te ontwikkelen. Recentie wordt gedefinieerd als laatste open-/klikdatum, -datum of -datum. Dit tijdkader kan verticaal verschillen. Dit doet u als volgt:

1. Bepaal actieve (&quot;veilige&quot;) segmenten voor elke verticaal. Dit zijn typisch abonnees die binnen de laatste 3-6 maanden actief zijn geweest.
1. Verminder de frequentie tot inactieven.
1. Maak een [herbetrokkenheidsreeks](../../delivery/using/re-engagement-best-practices.md) voor inactieven met matige risico&#39;s. Dit is doorgaans 6 tot 9 maanden zonder betrokkenheid.
1. Ontwikkelen van een herbevestigingscampagne voor inactieven met een hoger risico. Dit zijn doorgaans abonnees die in 9 tot 12 maanden geen e-mailberichten hebben ontvangen.
1. Stel ten slotte een keuzeregel in en verwijder abonnees die uw e-mails niet hebben geopend in &#39;x&#39; maanden. We raden doorgaans 12+ maanden aan, maar dit kan verschillen afhankelijk van de verkoop- en aankoopcyclus.
