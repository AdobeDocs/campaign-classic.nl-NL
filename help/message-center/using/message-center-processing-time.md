---
product: campaign
title: Verwerkingstijd van het Berichtencentrum
description: Meer informatie over de verwerkingstijd van Message Center
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# Verwerkingstijd van het Berichtencentrum {#message-center-processing-time}



Dit rapport geeft de belangrijkste indicatoren weer die betrekking hebben op de real-time wachtrij.

Dit rapport, dat op technische beheerders is gericht, kan ook via het **[!UICONTROL Monitoring]** lusje op de controleinstantie worden betreden.

![](assets/mc_reports_2.png)

Net als voor het **[!UICONTROL Message Center service level]** -rapport kunt u desgewenst de algemene statistieken of de statistieken ten opzichte van een bepaalde uitvoeringsinstantie weergeven. U kunt de gegevens ook filteren op kanaal en over een bepaalde periode.

De indicatoren die in de sectie **[!UICONTROL Indicators over the period]** worden weergegeven, worden berekend over de geselecteerde periode:

* **[!UICONTROL Average queuing time]** : de gemiddelde tijd die met succes in het Centrum van het Bericht doorgebrachte gebeurtenissen verwerkte. Alleen de verwerkingstijd wordt in aanmerking genomen.
* **[!UICONTROL Average message sending time (s)]** : de gemiddelde tijd die met succes in het Centrum van het Bericht doorgebrachte gebeurtenissen verwerkte. Alleen de levertijd van de mta wordt in aanmerking genomen.
* **[!UICONTROL Average processing time (s)]** : de gemiddelde tijd die met succes in het Centrum van het Bericht doorgebrachte gebeurtenissen verwerkte. De berekening neemt de verwerkingstijd in aanmerking en de tijd die de gegevens verzenden.
* **[!UICONTROL Maximum number of queued events]** : maximumaantal gebeurtenissen aanwezig in de wachtrij van het Berichtencentrum op een bepaald moment.
* **[!UICONTROL Minimum number of queued events]** : minimumaantal gebeurtenissen dat zich op een bepaald moment in de wachtrij van het Message Center bevindt.
* **[!UICONTROL Average number of queued events]** : het gemiddelde aantal gebeurtenissen dat op een bepaald moment in de wachtrij van het Berichtencentrum aanwezig is.

>[!NOTE]
>
>De drempelwaarden voor de waarschuwings- (oranje) en waarschuwingsindicator (rood) kunnen worden geconfigureerd in de implementatiewizard van Adobe Campaign. Verwijs naar [ drempels van de Monitor ](../../message-center/using/additional-configurations.md#monitoring-thresholds).
