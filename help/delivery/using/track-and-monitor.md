---
product: campaign
title: Berichten bijhouden en controleren
description: Leer hoe u berichten kunt bijhouden en controleren
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---

# Bijhouden en bewaken {#track-and-monitor}



U hebt op de knop **Verzenden** knop? Laten we eens kijken wat er gebeurt. Zodra de levering wordt verzonden, laat Adobe Campaign u toe om spoor van de verzonden berichten te houden en te ontdekken hoe uw ontvangers op uw levering reageren. Op deze manier kunt u uw volgende campagnes beter verzenden en optimaliseren.

## Verzendingen controleren {#monitoring-deliveries}

Om uw campagnes te controleren, moet u ervoor zorgen dat het bericht inderdaad aan uw ontvangers is geleverd.

Van het dashboard van de levering van de Campagne, kunt u de verwerkte berichten en de logboeken van de leveringscontrole controleren.
U kunt de status van de berichten in de leveringslogboeken ook controleren. [Meer informatie](about-delivery-monitoring.md).

Wat als de leveringen niet worden verzonden en hun status blijft **In behandeling**?

* Het uitvoeringsproces wacht op de beschikbaarheid van sommige bronnen. De MTA is mogelijk niet gestart.
Controleer of uw modules mta@instance op uw servers MTA worden gelanceerd en begin indien nodig de module MTA. [Meer informatie](../../production/using/administration.md).

* De levering kan een affiniteit gebruiken die niet op de verzendende instantie is gevormd.
Tip: Controleer de configuratie van verkeersbeheer (IP affiniteit). Voor meer op dit, zie het uitgaande verkeer SMTP van de Controle.

>[!NOTE]
>
>Deze stappen kunnen slechts door een deskundige gebruiker worden uitgevoerd.

## Traceergedrag {#track-behaviour}

Om het gedrag van uw ontvangers beter te kennen, kunt u volgen hoe zij op een levering reageren: ontvangen, openen, klikken op koppelingen, abonnementen enz. In Campaign Classic wordt deze informatie weergegeven op het tabblad Tracking van de ontvangers die de levering als doel heeft en op het tabblad Tracking van de levering.

**Tip**: Berichten bijhouden is standaard ingeschakeld. Als u URL&#39;s wilt configureren, selecteert u de optie URL&#39;s weergeven in de onderste sectie van de wizard voor levering. Voor elke URL van het bericht kunt u kiezen of u reeksspatiëring wilt activeren.

Raadpleeg voor meer informatie de [Tracking configureren](how-to-configure-tracked-links.md) en de [Traceringsindicatoren](../../reporting/using/delivery-reports.md#tracking-indicators) beschrijving.

## Leveringsprestaties {#delivery-performances}

Om de snelheid te meten waarbij de berichten worden geleverd, kunt u de leveringsproductie controleren. De criteria zijn het aantal berichten die per uur worden verzonden en de grootte van de berichten (in beetjes per seconde). Zie voor meer informatie [Leveringsdoorvoer](../../reporting/using/global-reports.md#delivery-throughput).

**Tips**:

* Bewaar de levering niet in mislukte staat op het geval, aangezien dit tijdelijke lijsten handhaaft en de prestaties beïnvloedt.

* Verwijder leveringen die niet meer nodig zijn en inactieve ontvangers uit de database om de adreskwaliteit te behouden.

* Probeer geen grote leveringen samen te plannen. Houd er rekening mee dat het 5 tot 10 minuten kan duren voordat de laadbewerking gelijkmatig over het systeem is verspreid.

## Problemen met een levering oplossen {#delivery-troubleshooting}

Specifieke acties kunnen worden uitgevoerd wanneer problemen met leveringen optreden:

* [Leverbaarheidsproblemen](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemen met weergave van afbeeldingen](../../production/using/image-display-issues.md)

* [Leveringsprestaties](delivery-performances.md)

* [Problemen met tijdelijke bestanden](../../production/using/temporary-files.md) - *alleen on-premise klanten*
