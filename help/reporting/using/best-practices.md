---
title: Aanbevolen werkwijzen voor rapportage
seo-title: Aanbevolen werkwijzen voor rapportage
description: Aanbevolen werkwijzen voor rapportage
seo-description: null
page-status-flag: never-activated
uuid: 09de6a17-b3a7-4543-b672-b0a21653aa75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: 904961e0-7dff-4350-8d5d-e4bdd368b3ff
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c41cf2f35495a1514642e47f0b7146d8dd50946

---


# Aanbevolen werkwijzen voor rapportage{#best-practices-reporting}

## De behoeften analyseren{#analyzing-needs}

Het gebruik van een rapportagegereedschap hangt af van het te manipuleren gegevensvolume, de complexiteit ervan en het type rapportage dat moet worden ingesteld.

Om de creatie, het gebruik en de duurzaamheid van een rapport te optimaliseren, moet u de behoeften zorgvuldig bekijken waaraan u wilt voldoen. Deze eerste analyse zal u toelaten om het type van te creëren rapport en de beste aanmaakwijze te identificeren. Voer de volgende stappen uit om het rapport te maken:

1. Identificeer de behoefte

   De eerste stap bestaat erin duidelijk aan te geven wat de noodzaak is: wat u in uw rapport wilt tonen en wat zijn doel is (controle, analyse, gegevensexport, enz.).

   Adobe Campaign biedt een groot aantal verschillende rapportagemogelijkheden. Het is belangrijk dat u analyseert wat u nodig hebt om de meest geschikte functionaliteit te identificeren.

   U kunt bijvoorbeeld:

   * De gegevens in de database verkennen en metingen definiëren (via [deze sectie](../../reporting/using/about-cubes.md)).
   * Voeg indicatoren toe aan een bestaand rapport (zie [deze paragraaf](../../reporting/using/about-reports-creation-in-campaign.md)),
   * De gegevens in de database bekijken (via [deze sectie](../../reporting/using/about-descriptive-analysis.md)),
   * Maak een nieuw leveringsrapport (zie [deze sectie](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Gegevens exporteren uit de Adobe Campagne-database (via een workflow, zie [deze sectie](../../workflow/using/about-workflows.md)),
   * Een draaitabel maken (zie [deze sectie](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)),
   * Geaggregeerde gegevens verkennen (via [deze sectie](../../reporting/using/about-cubes.md)),
   * Gebruik een wizard om gegevens te analyseren (via [deze sectie](../../reporting/using/about-descriptive-analysis.md)),
   * Analyseer grote hoeveelheden gegevens (zie [deze sectie](../../reporting/using/about-reports-creation-in-campaign.md)), enz.

1. Doelpopulatie identificeren

   Dan moet u weten wie het rapport u wilt tot stand brengen zal richten, het type van publiek kent wie het en de wijze van de rapportvertoning (in browser, in de Campagne van Adobe, voor een specifiek voorwerp, voor het volledige platform, enz.) zal bekijken.

   U kunt ook rapporten maken voor:

   * Alle Adobe Campaign-operatoren
   * marktdeelnemers die uitsluitend toegang hebben tot een marketingcampagne,
   * één enkele exploitant voor tijdelijk gebruik,
   * Alle operatoren in webtoegang, enz.
   Bij deze overwegingen moet ook rekening worden gehouden met kwesties die verband houden met toegangsrechten en veiligheid.

1. De inhoud definiëren

   Vervolgens moet u weten welk type gegevens u wilt weergeven: leveringsindicatoren, verslagen over de databaseprofielen, enz.

   U moet ook de aard van deze gegevens (eenvoudig, resulterend uit een berekening, significant, enz.), zijn plaats (in de Campagne van Adobe, in een derdesysteem), zijn updatefrequentie kennen om de berekeningsfrequentie (dagelijks, wekelijks, op-de-weg), en zijn volume te bepalen.

   De kwesties die verband houden met gegevensvolumes en updates moeten zorgvuldig worden bestudeerd om weergaveproblemen, met name in termen van tijd, te vermijden. Daarom raden we u aan aggregaten te maken om bepaalde gegevens buiten het rapport vooraf te berekenen. Tabellen die de tracerings- en leveringslogboeken bevatten, kunnen miljoenen records bevatten: dit betekent dat de gegevens moeten worden samengevoegd via een werkstroom die in een rapport moet worden gebruikt .

## Rapport maken optimaliseren{#optimizing-report-creation}

### Gegevensvolume {#data-volume}

Om optimale prestaties te garanderen, moet het volume van gemanipuleerde gegevens niet te groot zijn.

Namelijk:

* De berekeningstijd voor een rapport mag nooit meer dan 5 minuten bedragen.

   Op dezelfde manier, tijdens de ontwerpfase, met een klein volume van gegevens, als de rapportberekening 60 seconden overschrijdt, moeten de berekeningsmethodes worden veranderd.

* Wanneer het gebruiken van de Analyse van de Marketing, moeten de gemanipuleerde gegevens 10 miljoen lijnen niet overschrijden.

We raden ook aan &#39;s nachts aggregaten te berekenen en deze geaggregeerde gegevens rechtstreeks in de rapporten te gebruiken. Deze aggregaten moeten worden gemaakt via speciale gegevensbeheerworkflows (SQL-query&#39;s).

U kunt ook &#39;s nachts rapporten berekenen en automatisch een geschiedenis maken die op elk moment kan worden weergegeven zonder de database te overladen.

### Zoekopdrachten {#queries}

We raden u aan om waar mogelijk SQL-query&#39;s te gebruiken en JavaScript-naverwerking te vermijden. Gebruik indien nodig een scriptactiviteit in een workflow en verwijder de gegevens die voor de berekening worden gebruikt. U kunt gearchiveerde gegevens ook gebruiken om de verwerkingstijd te versnellen.

In dit geval moet de volgende syntaxis worden gebruikt:

```
if(string(ctx@_historyId)!==""))
```

Zoekopdrachten die u in staat stellen de gegevens te verzamelen die in de rapporten worden weergegeven, mogen niet te complex zijn, met name niet wanneer deze worden toegepast op alle gegevens in de database. Om de prestaties te verbeteren, kan het nuttig zijn om de gegevens te filteren alvorens deze vragen uit te voeren: dit betekent dat de berekening slechts betrekking heeft op een deel van de gegevens .

### Prestaties {#performances}

Met de bovenstaande aanbevelingen kunt u de berekening van rapporten optimaliseren.

Daarnaast worden in Adobe Campaign de volgende verbeteringen aanbevolen:

* Onderzoek het datamodel: de geïndexeerde velden moeten vooral worden gebruikt om de berekeningsformules te verbeteren .

   Als u snel een geïndexeerd veld wilt zoeken, bekijkt u de naam van de kolom in de Adobe Campagne-interface: de sorteerpijl wordt rood onderstreept als het veld wordt geïndexeerd.

* Zorg ervoor dat het rapport op lange termijn geldig is: het gegevensvolume kan in de loop der tijd aanzienlijk toenemen.

   Evenzo kan het tijdens de testfasen gemanipuleerde gegevensvolume afwijken van het werkelijke productievolume. Daarom zijn testfasen belangrijk.

   Tot slot moeten vertragingen bij het wissen van gegevens bekend zijn en waar nodig worden aangepast voor een gemakkelijke gegevensmanipulatie.

### Rapporten exporteren {#exporting-reports}

De aanbevelingen specifiek voor het uitvoeren van rapporten worden gedetailleerd in [deze sectie](../../reporting/using/actions-on-reports.md#exporting-a-report).
