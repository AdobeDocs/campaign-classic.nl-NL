---
title: Serviceniveau van Message Center
seo-title: Serviceniveau van Message Center
description: Serviceniveau van Message Center
seo-description: null
page-status-flag: never-activated
uuid: 8e363706-292b-40db-97bc-d41b41910556
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: e46a4e87-6c02-4b9c-bf6d-bb4e785e78fa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Serviceniveau van Message Center{#message-center-service-level}

Dit rapport geeft de leveringsstatistieken weer met betrekking tot transactieberichten en de uitsplitsing naar fouten. U kunt op een fouttype klikken om de details ervan weer te geven. Dit rapport, gericht op technische beheerders, kan ook via het **[!UICONTROL Monitoring]** universum in de controle instantie worden betreden.

![](assets/mc_reports_1.png)

In dit rapport kunt u de algemene statistieken of de statistieken ten opzichte van een bepaalde uitvoeringsinstantie weergeven. U kunt de gegevens ook filteren op kanaal en over een bepaalde periode. De indicatoren in de **[!UICONTROL Indicators over the period]** sectie worden berekend over de geselecteerde periode:

* **[!UICONTROL Incoming (throughput event/h)]** : gemiddeld aantal gebeurtenissen per uur dat is ingevoerd in de wachtrij van het Berichtencentrum.
* **[!UICONTROL Incoming (event vol)]** : Aantal gebeurtenissen ingegaan in de rij van het Centrum van het Bericht.
* **[!UICONTROL Outgoing (throughput msg/h)]** : gemiddeld uuraantal succesvolle uitgaande gebeurtenissen van het Centrum van het Bericht (verzonden door een levering).
* **[!UICONTROL Outgoing (msg vol)]** : Aantal succesvolle uitgaande gebeurtenissen van het Centrum van het Bericht (verzonden door een levering).
* **[!UICONTROL Average sending time (seconds)]** : gemiddelde tijd die in het Centrum van het Bericht voor met succes verwerkte gebeurtenissen wordt doorgebracht. De berekening neemt de verwerkingstijd in aanmerking en de tijd die de gegevens verzenden.
* **[!UICONTROL Error rate]** : Het aantal gebeurtenissen met fouten in vergelijking met het aantal gebeurtenissen dat de wachtrij van het Berichtencentrum is binnengekomen. Met de volgende fouten wordt rekening gehouden: het verpletteren van fout, verlopen gebeurtenis (gebeurtenis die in de rij te lang is geweest), leveringsfout, genegeerd door de levering (quarantaine, enz.).

>[!NOTE]
>
>De waarschuwings (oranje) en waakzame (rode) indicatordrempels kunnen in de plaatsingstovenaar worden gevormd. Zie [Controledrempels](../../message-center/using/monitoring-thresholds.md).

