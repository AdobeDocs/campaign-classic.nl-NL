---
product: campaign
title: Serviceniveau van het Berichtencentrum
description: Meer informatie over het serviceniveau van Message Center
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 3%

---

# Serviceniveau van het Berichtencentrum {#message-center-service-level}



Dit rapport geeft de leveringsstatistieken weer met betrekking tot transactieberichten en de uitsplitsing naar fouten. U kunt op een fouttype klikken om de details ervan weer te geven.

Dit rapport, dat op technische beheerders is gericht, kan ook via het **[!UICONTROL Monitoring]** lusje op de controleinstantie worden betreden.

![](assets/mc_reports_1.png)

In dit rapport kunt u desgewenst de algemene statistieken of de statistieken ten opzichte van een bepaalde uitvoeringsinstantie weergeven. U kunt de gegevens ook filteren op kanaal en over een bepaalde periode.

De indicatoren die in de sectie **[!UICONTROL Indicators over the period]** worden weergegeven, worden berekend over de geselecteerde periode:

* **[!UICONTROL Incoming (throughput event/h)]** : gemiddeld aantal gebeurtenissen per uur dat is ingevoerd in de wachtrij voor Bericht centreren.
* **[!UICONTROL Incoming (event vol)]** : aantal gebeurtenissen dat is ingevoerd in de wachtrij van het Berichtencentrum.
* **[!UICONTROL Outgoing (throughput msg/h)]** : gemiddeld uuraantal geslaagde uitgaande gebeurtenissen van het Centrum van het Bericht (verzonden door een levering).
* **[!UICONTROL Outgoing (msg vol)]** : aantal geslaagde uitgaande gebeurtenissen van het Message Center (verzonden door een levering).
* **[!UICONTROL Average sending time (seconds)]** : gemiddelde tijd die in het Centrum van het Bericht voor met succes verwerkte gebeurtenissen wordt doorgebracht. De berekening neemt de verwerkingstijd in aanmerking en de tijd die de gegevens verzenden.
* **[!UICONTROL Error rate]** : aantal gebeurtenissen met fouten in vergelijking met het aantal gebeurtenissen dat de wachtrij van het Message Center is binnengekomen. Met de volgende fouten wordt rekening gehouden: het verpletteren van fout, verlopen gebeurtenis (gebeurtenis die in de rij te lang is geweest), leveringsfout, die door de levering (quarantaine, enz.) wordt genegeerd.

>[!NOTE]
>
>De waarschuwings (oranje) en waakzame (rode) indicatordrempels kunnen in de plaatsingstovenaar worden gevormd. Verwijs naar [ drempels van de Monitor ](../../message-center/using/additional-configurations.md#monitoring-thresholds).
