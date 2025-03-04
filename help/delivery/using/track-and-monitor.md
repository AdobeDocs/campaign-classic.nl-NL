---
product: campaign
title: Berichten bijhouden en controleren
description: Leer hoe u berichten kunt bijhouden en controleren
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Monitoring, Reporting
role: User
hide: true
hidefromtoc: true
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 2%

---

# Track en monitor {#track-and-monitor}

U klikte **verzendt** knoop? Laten we eens kijken wat er gebeurt. Zodra de levering wordt verzonden, laat Adobe Campaign u toe om spoor van de verzonden berichten te houden en te ontdekken hoe uw ontvangers op uw levering reageren. Op deze manier kunt u uw volgende campagnes beter verzenden en optimaliseren.

## Leveringen controleren {#monitoring-deliveries}

Om uw campagnes te controleren, moet u ervoor zorgen dat het bericht inderdaad aan uw ontvangers is geleverd.

Van het dashboard van de levering van de Campagne, kunt u de verwerkte berichten en de logboeken van de leveringscontrole controleren.
U kunt de status van de berichten in de leveringslogboeken ook controleren. [Meer informatie](about-delivery-monitoring.md).

Wat als de leveringen niet worden verzonden en hun status blijft **Hangende**?

* Het uitvoeringsproces wacht op de beschikbaarheid van sommige bronnen. De MTA is mogelijk niet gestart.
Controleer of uw modules mta@instance op uw servers MTA worden gelanceerd en begin indien nodig de module MTA. [Meer informatie](../../production/using/administration.md).

* De levering kan een affiniteit gebruiken die niet op de verzendende instantie is gevormd.
Tip: controleer de configuratie van verkeersbeheer (IP affiniteit). Voor meer op dit, zie het uitgaande verkeer SMTP van de Controle.

>[!NOTE]
>
>Deze stappen kunnen slechts door een deskundige gebruiker worden uitgevoerd.

## Traceergedrag {#track-behaviour}

Als u het gedrag van de ontvangers beter wilt weten, kunt u bijhouden hoe zij op een levering reageren: ontvangst, openen, klikken op koppelingen, abonnementen, enz. In Campaign Classic, wordt deze informatie getoond in het Volgen lusje van de ontvangers die door de levering en in het Volgen lusje van de levering worden gericht.

**Uiteinde**: Het volgen van het bericht wordt toegelaten door gebrek. Om URLs te vormen, selecteer de optie van de Vertoning URLs in de lagere sectie van de leveringsmedewerker. Voor elke URL van het bericht kunt u kiezen of u reeksspatiëring wilt activeren.

Voor meer op dit, verwijs naar [ het volgen ](how-to-configure-tracked-links.md) sectie en [ het Volgen indicatoren ](../../reporting/using/delivery-reports.md#tracking-indicators) beschrijving vormen.

## Leveringsprestaties {#delivery-performances}

Om de snelheid te meten waarbij de berichten worden geleverd, kunt u de leveringsproductie controleren. De criteria zijn het aantal berichten die per uur worden verzonden en de grootte van de berichten (in beetjes per seconde). Voor meer op dit, zie [ productie van de Levering ](../../reporting/using/global-reports.md#delivery-throughput).

**Uiteinden**:

* Bewaar de levering niet in mislukte staat, aangezien dit tijdelijke lijsten handhaaft en de prestaties beïnvloedt.

* Verwijder leveringen die niet meer nodig zijn en inactieve ontvangers uit de database om de adreskwaliteit te behouden.

* Probeer geen grote leveringen samen te plannen. Houd er rekening mee dat het 5 tot 10 minuten kan duren voordat de laadbewerking gelijkmatig over het systeem is verspreid.

## Problemen met een levering oplossen {#delivery-troubleshooting}

Specifieke acties kunnen worden uitgevoerd wanneer problemen met leveringen optreden:

* [Leverbaarheidsproblemen](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemen met weergave van afbeeldingen](../../production/using/image-display-issues.md)

* [Leveringsprestaties](delivery-performances.md)

* [ Tijdelijke dossiers kwesties ](../../production/using/temporary-files.md) - *op-gebouw slechts klanten*
