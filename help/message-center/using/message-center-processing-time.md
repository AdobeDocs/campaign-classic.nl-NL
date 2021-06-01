---
product: campaign
title: Verwerkingstijd van het Berichtencentrum
description: Meer weten over het rapport Verwerkingstijd van Message Center?
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: e86350cf12db37e3f2c227563057b97922601729
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# Verwerkingstijd van het Berichtencentrum {#message-center-processing-time}

Dit rapport geeft de belangrijkste indicatoren weer die betrekking hebben op de real-time wachtrij.

Dit rapport, gericht op technische beheerders, kan ook via het **[!UICONTROL Monitoring]** lusje op de controleinstantie worden betreden.

![](assets/mc_reports_2.png)

Enkel zoals voor het **[!UICONTROL Message Center service level]** rapport, kunt u verkiezen om de algemene statistieken of die met betrekking tot een bepaalde uitvoeringsinstantie te tonen. U kunt de gegevens ook filteren op kanaal en over een bepaalde periode.

De indicatoren die in de **[!UICONTROL Indicators over the period]** sectie worden getoond worden berekend over de geselecteerde periode:

* **[!UICONTROL Average queuing time]** : de gemiddelde tijd die met succes gebeurtenissen gebruikte in het Centrum van het Bericht verwerkte. Alleen de verwerkingstijd wordt in aanmerking genomen.
* **[!UICONTROL Average message sending time (s)]** : de gemiddelde tijd die met succes gebeurtenissen gebruikte in het Centrum van het Bericht verwerkte. Alleen de levertijd van de mta wordt in aanmerking genomen.
* **[!UICONTROL Average processing time (s)]** : de gemiddelde tijd die met succes gebeurtenissen gebruikte in het Centrum van het Bericht verwerkte. De berekening neemt de verwerkingstijd in aanmerking en de tijd die de gegevens verzenden.
* **[!UICONTROL Maximum number of queued events]** : maximumaantal gebeurtenissen aanwezig in de rij van het Centrum van het Bericht op om het even welk bepaald ogenblik.
* **[!UICONTROL Minimum number of queued events]** : minimumaantal gebeurtenissen aanwezig in de rij van het Centrum van het Bericht op om het even welk bepaald ogenblik.
* **[!UICONTROL Average number of queued events]** : gemiddeld aantal gebeurtenissen aanwezig in de rij van het Centrum van het Bericht op om het even welk bepaald ogenblik.

>[!NOTE]
>
>De drempelwaarden voor de waarschuwings- (oranje) en waarschuwingsindicator (rood) kunnen worden geconfigureerd in de implementatiewizard van Adobe Campaign. Raadpleeg [Monitordrempels](../../message-center/using/additional-configurations.md#monitoring-thresholds).
