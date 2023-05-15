---
product: campaign
title: Serviceniveau van het Berichtencentrum
description: Meer informatie over het serviceniveau van Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 3%

---

# Serviceniveau van het Berichtencentrum {#message-center-service-level}



Dit rapport geeft de leveringsstatistieken weer met betrekking tot transactieberichten en de uitsplitsing naar fouten. U kunt op een fouttype klikken om de details ervan weer te geven.

Dit rapport, dat gericht is op technische beheerders, is ook toegankelijk via **[!UICONTROL Monitoring]** op de besturingsinstantie.

![](assets/mc_reports_1.png)

In dit rapport kunt u de algemene statistieken of de statistieken ten opzichte van een bepaalde uitvoeringsinstantie weergeven. U kunt de gegevens ook filteren op kanaal en over een bepaalde periode.

De indicatoren die worden weergegeven in het **[!UICONTROL Indicators over the period]** de sectie wordt berekend over de geselecteerde periode:

* **[!UICONTROL Incoming (throughput event/h)]** : gemiddeld aantal gebeurtenissen per uur dat is ingevoerd in de wachtrij van het Berichtencentrum.
* **[!UICONTROL Incoming (event vol)]** : Aantal gebeurtenissen ingegaan in de rij van het Centrum van het Bericht.
* **[!UICONTROL Outgoing (throughput msg/h)]** : gemiddeld uuraantal succesvolle uitgaande gebeurtenissen van het Centrum van het Bericht (verzonden door een levering).
* **[!UICONTROL Outgoing (msg vol)]** : Aantal succesvolle uitgaande gebeurtenissen van het Centrum van het Bericht (verzonden door een levering).
* **[!UICONTROL Average sending time (seconds)]** : gemiddelde tijd die in het Centrum van het Bericht voor met succes verwerkte gebeurtenissen wordt doorgebracht. De berekening neemt de verwerkingstijd in aanmerking en de tijd die de gegevens verzenden.
* **[!UICONTROL Error rate]** : Het aantal gebeurtenissen met fouten in vergelijking met het aantal gebeurtenissen dat de wachtrij van het Berichtencentrum is binnengekomen. Met de volgende fouten wordt rekening gehouden: het verpletteren van fout, verlopen gebeurtenis (gebeurtenis die in de rij te lang is geweest), leveringsfout, genegeerd door de levering (quarantaine, enz.).

>[!NOTE]
>
>De waarschuwings (oranje) en waakzame (rode) indicatordrempels kunnen in de plaatsingstovenaar worden gevormd. Zie [Monitordrempels](../../message-center/using/additional-configurations.md#monitoring-thresholds).
