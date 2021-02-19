---
solution: Campaign Classic
product: campaign
title: Berichten bijhouden en controleren
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 3%

---


# Bijhouden en bewaken {#track-and-monitor}

Hebt u op de knop Verzenden geklikt? Laten we eens kijken wat er gebeurt. Zodra de levering wordt verzonden, laat Adobe Campaign u toe om spoor van de verzonden berichten te houden en te ontdekken hoe uw ontvangers op uw levering reageren. Op deze manier kunt u uw volgende campagnes beter verzenden en optimaliseren.

## Leveringen controleren{#monitoring-deliveries}

Om uw campagnes te controleren, moet u ervoor zorgen dat het bericht inderdaad aan uw ontvangers is geleverd.

Van het dashboard van de levering van de Campagne, kunt u de verwerkte berichten en de logboeken van de leveringscontrole controleren.
U kunt de status van de berichten in de leveringslogboeken ook controleren. [Meer informatie](../../delivery/using/about-delivery-monitoring.md).

Wat als de leveringen niet worden verzonden en hun status **Pending** blijft?

* Het uitvoeringsproces wacht op de beschikbaarheid van sommige bronnen. De MTA is mogelijk niet gestart.
Controleer of uw modules mta@instance op uw servers MTA worden gelanceerd en begin indien nodig de module MTA. [Meer informatie](../../production/using/administration.md).

* De levering kan een affiniteit gebruiken die niet op de verzendende instantie is gevormd.
Tip: Controleer de configuratie van verkeersbeheer (IP affiniteit). Voor meer op dit, zie het uitgaande verkeer SMTP van de Controle.

>[!NOTE]
>
>Deze stappen kunnen slechts door een deskundige gebruiker worden uitgevoerd.

## Tracking {#tracking-deliveries}

Om het gedrag van uw ontvangers beter te kennen, kunt u volgen hoe zij op een levering reageren: ontvangen, openen, klikken op koppelingen, abonnementen enz. In Campaign Classic wordt deze informatie weergegeven op het tabblad Tracking van de ontvangers die de levering als doel heeft en op het tabblad Tracking van de levering. In Campaign Standard, wordt het getoond in het Volgen logboeken tabel van de levering.

**Tip**: Berichten bijhouden is standaard ingeschakeld. Als u URL&#39;s wilt configureren, selecteert u de optie URL&#39;s weergeven in de onderste sectie van de wizard voor levering. Voor elke URL van het bericht kunt u kiezen of u reeksspatiëring wilt activeren.

Raadpleeg voor meer informatie de sectie [Tracking](../../delivery/using/how-to-configure-tracked-links.md) configureren en de beschrijving [Tracking-indicatoren](../../reporting/using/delivery-reports.md#tracking-indicators).

## Leveringsprestaties {#delivery-performances}

Om de snelheid te meten waarbij de berichten worden geleverd, kunt u de leveringsproductie controleren. De criteria zijn het aantal berichten die per uur worden verzonden en de grootte van de berichten (in beetjes per seconde). Zie [Productie-doorvoer](../../reporting/using/global-reports.md#delivery-throughput) voor meer informatie.

**Tips**:

* Bewaar de levering niet in mislukte staat op het geval, aangezien dit tijdelijke lijsten handhaaft en de prestaties beïnvloedt.

* Verwijder leveringen die niet meer nodig zijn en inactieve ontvangers uit de database om de adreskwaliteit te behouden.

* Probeer geen grote leveringen samen te plannen. Houd er rekening mee dat het 5 tot 10 minuten kan duren voordat de laadbewerking gelijkmatig over het systeem is verspreid.

## Problemen met levering oplossen {#delivery-troubleshooting}

Specifieke acties kunnen worden uitgevoerd wanneer problemen met leveringen optreden:

* [Leverbaarheidsproblemen](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemen met weergave van afbeeldingen](../../production/using/image-display-issues.md)

* [Leveringsprestaties](../../delivery/using/delivery-performances.md)

* [Uitgave van tijdelijke bestanden](../../production/using/temporary-files.md)  - alleen  *klanten op locatie*
