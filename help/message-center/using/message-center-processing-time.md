---
title: Verwerkingstijd van het Berichtencentrum
seo-title: Verwerkingstijd van het Berichtencentrum
description: Verwerkingstijd van het Berichtencentrum
seo-description: null
page-status-flag: never-activated
uuid: 06aca2c2-33c0-4839-bee4-fd838c49ce76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: d1f591d2-95e8-4d99-bc60-955c96b532eb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 7%

---


# Verwerkingstijd van het Berichtencentrum{#message-center-processing-time}

Dit rapport geeft de belangrijkste indicatoren weer die betrekking hebben op de real-time wachtrij. Dit rapport, gericht op technische beheerders, kan ook via het **[!UICONTROL Monitoring]** universum in de controle instantie worden betreden.

![](assets/mc_reports_2.png)

Enkel zoals voor het **[!UICONTROL Message Center service level]** rapport, kunt u verkiezen om de algemene statistieken of die met betrekking tot een bepaalde uitvoeringsinstantie te tonen. U kunt de gegevens ook filteren op kanaal en over een bepaalde periode. De indicatoren in de **[!UICONTROL Indicators over the period]** sectie worden berekend over de geselecteerde periode:

* **[!UICONTROL Average queuing time]** : de gemiddelde tijd die met succes gebeurtenissen gebruikte in het Centrum van het Bericht verwerkte. Alleen de verwerkingstijd wordt in aanmerking genomen.
* **[!UICONTROL Average message sending time (s)]** : de gemiddelde tijd die met succes gebeurtenissen gebruikte in het Centrum van het Bericht verwerkte. Alleen de levertijd van de mta wordt in aanmerking genomen.
* **[!UICONTROL Average processing time (s)]** : de gemiddelde tijd die met succes gebeurtenissen gebruikte in het Centrum van het Bericht verwerkte. De berekening neemt de verwerkingstijd in aanmerking en de tijd die de gegevens verzenden.
* **[!UICONTROL Maximum number of queued events]** : maximumaantal gebeurtenissen aanwezig in de rij van het Centrum van het Bericht op om het even welk bepaald ogenblik.
* **[!UICONTROL Minimum number of queued events]** : minimumaantal gebeurtenissen aanwezig in de rij van het Centrum van het Bericht op om het even welk bepaald ogenblik.
* **[!UICONTROL Average number of queued events]** : gemiddeld aantal gebeurtenissen aanwezig in de rij van het Centrum van het Bericht op om het even welk bepaald ogenblik.

>[!NOTE]
>
>De drempelwaarden voor de waarschuwings- (oranje) en waarschuwingsindicator (rood) kunnen worden geconfigureerd in de implementatiewizard van Adobe Campaign. Zie [Controledrempels](../../message-center/using/monitoring-thresholds.md).

