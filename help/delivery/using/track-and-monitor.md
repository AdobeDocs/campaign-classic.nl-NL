---
title: Berichten bijhouden en controleren
seo-title: Berichten bijhouden en controleren
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 2%

---


# Track en monitor {#track-and-monitor}

Hebt u op de knop Verzenden geklikt? Laten we eens kijken wat er gebeurt. Zodra de levering wordt verzonden, laat Adobe Campaign u toe om spoor van de verzonden berichten te houden en te ontdekken hoe uw ontvangers op uw levering reageren. Op deze manier kunt u uw volgende campagnes beter verzenden en optimaliseren.

## Leveringen controleren{#monitoring-deliveries}

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

## Tracking {#tracking-deliveries}

Om het gedrag van uw ontvangers beter te kennen, kunt u volgen hoe zij op een levering reageren: ontvangen, openen, klikken op koppelingen, abonnementen enz. In Campaign Classic wordt deze informatie weergegeven op het tabblad Tracking van de ontvangers die de levering als doel heeft en op het tabblad Tracking van de levering. In Campaign Standard, wordt het getoond in het Volgen logboeken tabel van de levering.

**Tip**: Berichten bijhouden is standaard ingeschakeld. Als u URL&#39;s wilt configureren, selecteert u de optie URL&#39;s weergeven in de onderste sectie van de wizard voor levering. Voor elke URL van het bericht kunt u kiezen of u reeksspatiëring wilt activeren.

Voor meer op dit, verwijs naar de het [Vormen het volgen](../../delivery/using/how-to-configure-tracked-links.md) sectie en de beschrijving van de indicatoren [van het](../../reporting/using/delivery-reports.md#tracking-indicators) Volgen.

## Leveringsprestaties {#delivery-performances}

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
