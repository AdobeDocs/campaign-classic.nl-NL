---
product: campaign
title: Best practices voor rapportage
description: Campagne die beste praktijken meldt
feature: Reporting, Monitoring
badge: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 1%

---

# Beste werkwijzen rapporteren{#best-practices-reporting}



## Analyseer uw behoeften{#analyzing-needs}

Het gebruik van een rapportagegereedschap hangt af van het te manipuleren gegevensvolume, de complexiteit ervan en het type rapportage dat moet worden ingesteld.

Om de creatie, het gebruik en de duurzaamheid van een rapport te optimaliseren, moet u de behoeften zorgvuldig bekijken waaraan u wilt voldoen. Deze eerste analyse zal u toelaten om het type van te creëren rapport en de beste aanmaakwijze te identificeren. Voer de volgende stappen uit om het rapport te maken:

1. Identificeer de behoefte

   De eerste stap bestaat uit het duidelijk identificeren van de noodzaak: wat u in uw verslag wilt laten zien en wat het doel ervan is (controle, analyse, gegevensexport, enz.).

   Adobe Campaign biedt een breed scala aan rapportagemogelijkheden. Het is belangrijk dat u analyseert wat u nodig hebt om de meest geschikte functionaliteit te identificeren.

   U kunt bijvoorbeeld:

   * Onderzoek de gegevens in het gegevensbestand en bepaal metingen. Leer meer [ in deze sectie ](../../reporting/using/ac-cubes.md)
   * Voeg indicatoren aan een bestaand rapport toe. Leer meer [ in deze sectie ](../../reporting/using/about-reports-creation-in-campaign.md)
   * Bekijk de gegevens in de database. Leer meer [ in deze sectie ](../../reporting/using/about-descriptive-analysis.md)
   * Maak een nieuw leveringsrapport. Leer meer [ in deze sectie ](../../reporting/using/about-reports-creation-in-campaign.md)),
   * De gegevens van de uitvoer van het gegevensbestand van Adobe Campaign (via een werkschema, verwijs naar [ deze sectie ](../../workflow/using/about-workflows.md)
   * Maak een draaitabel. Leer meer [ in deze sectie ](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * Geaggregeerde gegevens verkennen. Leer meer [ in deze sectie ](../../reporting/using/ac-cubes.md)
   * Gebruik een medewerker om gegevens te analyseren. Leer meer [ in deze sectie ](../../reporting/using/about-descriptive-analysis.md)
   * Analyseer grote hoeveelheden gegevens. Leer meer [ in deze sectie ](../../reporting/using/about-reports-creation-in-campaign.md)

1. Doelpopulatie identificeren

   Dan moet u weten wie het rapport u wilt tot stand brengen zal richten, het type van publiek kent wie het en de wijze van de rapportvertoning (in browser, in Adobe Campaign, voor een specifiek voorwerp, voor het volledige platform, enz.) zal bekijken.

   U kunt ook rapporten maken voor:

   * Alle Adobe Campaign-operatoren
   * marktdeelnemers die uitsluitend toegang hebben tot een marketingcampagne,
   * één enkele exploitant voor tijdelijk gebruik,
   * Alle operatoren in webtoegang, enz.

   Bij deze overwegingen moet ook rekening worden gehouden met kwesties die verband houden met toegangsrechten en veiligheid.

1. De inhoud definiëren

   Vervolgens moet u weten welk type gegevens u wilt weergeven: leveringsindicatoren, rapporten over de databaseprofielen, enzovoort.

   U moet ook weten wat de aard van deze gegevens is (eenvoudig, resulterend uit een berekening, significant, enz.), waar deze zich bevinden (in Adobe Campaign, in een systeem van derden), hoe vaak ze worden bijgewerkt om de berekeningsfrequentie (dagelijks, wekelijks, ter plekke) en het volume ervan te bepalen.

   De kwesties die verband houden met gegevensvolumes en updates moeten zorgvuldig worden bestudeerd om weergaveproblemen, met name in termen van tijd, te vermijden. Daarom raden we u aan aggregaten te maken om bepaalde gegevens buiten het rapport vooraf te berekenen. Tabellen die de tracerings- en leveringslogboeken bevatten, kunnen miljoenen records bevatten: dit betekent dat de gegevens moeten worden samengevoegd via een workflow die in een rapport moet worden gebruikt.

## Rapportontwerp optimaliseren{#optimizing-report-creation}

### Gegevensvolume {#data-volume}

Om optimale prestaties te garanderen, moet het volume van gemanipuleerde gegevens niet te groot zijn.

Namelijk:

* De berekeningstijd voor een rapport mag nooit meer dan 5 minuten bedragen.

  Op dezelfde manier, tijdens de ontwerpfase, met een klein volume van gegevens, als de rapportberekening 60 seconden overschrijdt, moeten de berekeningsmethodes worden veranderd.

* Wanneer het gebruiken van de module van de Analyse van de Marketing, moeten de rapportgegevens 10 miljoen lijnen niet overschrijden.

We raden ook aan &#39;s nachts aggregaten te berekenen en deze geaggregeerde gegevens rechtstreeks in de rapporten te gebruiken. Deze aggregaten moeten worden gemaakt via speciale gegevensbeheerworkflows (SQL-query&#39;s).

U kunt ook &#39;s nachts rapporten berekenen en automatisch een geschiedenis maken die op elk moment kan worden weergegeven zonder de database te overladen.

### Zoekopdrachten {#queries}

We raden u aan om waar mogelijk SQL-query&#39;s te gebruiken en JavaScript-naverwerking te vermijden. Gebruik indien nodig een scriptactiviteit in een workflow en verwijder de gegevens die voor de berekening worden gebruikt. U kunt gearchiveerde gegevens ook gebruiken om de verwerkingstijd te versnellen.

In dit geval moet de volgende syntaxis worden gebruikt:

```
if(string(ctx@_historyId)!==""))
```

Zoekopdrachten die u in staat stellen de gegevens te verzamelen die in de rapporten worden weergegeven, mogen niet te complex zijn, met name niet wanneer deze worden toegepast op alle gegevens in de database. Om de prestaties te verbeteren, kan het nuttig zijn om de gegevens te filteren alvorens deze vragen uit te voeren: dit betekent dat de berekening slechts een deel van de gegevens zal betreffen.

### Prestaties {#performances}

Met de bovenstaande aanbevelingen kunt u de berekening van rapporten optimaliseren.

Daarnaast beveelt Adobe Campaign de volgende verbeteringen aan:

* Werk aan uw datamodel: de geïndexeerde gebieden moeten hoofdzakelijk worden gebruikt om berekeningsformules te verbeteren.

  Als u snel een geïndexeerd veld wilt zoeken, bekijkt u de naam van de kolom in de Adobe Campaign-interface: de sorteerpijl wordt rood onderstreept als het veld wordt geïndexeerd.

  Voor meer op indexen, verwijs naar [ deze sectie ](../../configuration/using/data-model-best-practices.md#indexes).

* Zorg ervoor het rapport scalable is: het gegevensvolume kan in tijd beduidend stijgen.

  Evenzo kan het tijdens de testfasen gemanipuleerde gegevensvolume afwijken van het werkelijke productievolume. Daarom zijn testfasen belangrijk.

  Tot slot moeten vertragingen bij het wissen van gegevens bekend zijn en waar nodig worden aangepast voor een gemakkelijke gegevensmanipulatie.

  Voor meer op schoonmaak en gegevensbehoud, verwijs naar [ deze sectie ](../../configuration/using/data-model-best-practices.md#data-retention).

### Uw rapporten exporteren {#exporting-reports}

Recommendations specifiek voor het uitvoeren van rapporten wordt gedetailleerd in [ deze sectie ](../../reporting/using/actions-on-reports.md#exporting-a-report).
