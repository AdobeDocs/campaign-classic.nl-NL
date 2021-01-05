---
solution: Campaign Classic
product: campaign
title: Uitvoering van levering
description: Uitvoering van levering
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 1788346f7dfe2c18c490363c90358fcb737f1646
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 4%

---


# Uitvoering van levering{#delivery-execution}

## Transactiebericht {#transactional-message-send} verzenden

Op de uitvoeringsinstantie wordt de levering verzonden zodra het verrijkingsstadium is voltooid en een leveringssjabloon aan de gebeurtenis is gekoppeld.

>[!NOTE]
>
>MTA geeft voorrang aan verwerking van de transactionele berichten over om het even welke andere levering.

Alle leveringen worden gegroepeerd in de map **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**.

![](assets/messagecenter_deliveries_execinstances_001.png)

Standaard worden ze in submappen gesorteerd op leveringsmaand. Deze soort kan in de eigenschappen van het berichtmalplaatje worden veranderd zoals hieronder getoond.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Voor ontvangen of hybride installaties, als u aan Verbeterde MTA hebt bevorderd, kunnen alle transactionele berichten ook met Adobe Campaign Verbeterde MTA voor betere leverability, productie, en stuitbehandeling worden verzonden. Alle effecten zijn gelijk aan die voor standaardmarketingberichten en worden beschreven in het document [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/nl/campaign/kb/acc-campaign-enhanced-mta.html).

## Controle van het transactiebericht {#transactional-message-monitoring}

Controleer de leveringslogboeken om de transactiemeldingen te controleren. De toegang tot de leveringslogboeken wordt voorgesteld in [deze sectie](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

De transactionele leveringen die van de uitvoeringsinstantie worden verzonden worden gesynchroniseerd terug naar de controleinstantie door een technisch werkschema (**[!UICONTROL Message Center execution instance]**) dat elk uur in werking stelt.

>[!NOTE]
>
>De leveringenwekelijkse accumulatie van de gebeurtenissen op basis van de meest recente update van de gebeurtenis en niet op de aanmaakdatum van de gebeurtenis. Daarom wanneer het halen van transactioneel overseinenleveringslogboeken van de controleinstantie, levert identiteitskaart verbonden aan elke identiteitskaart van het leveringslogboek kan in tijd veranderen aangezien het logboek wordt bijgewerkt (bijvoorbeeld, wanneer een binnenkomende stuit voor de gebeurtenis wordt ontvangen).

<!--The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

Let's take a [delivery template](../../message-center/using/introduction.md) labelled *Template_1*.

1. An event corresponding to *Template_1* is received on the execution instance.
1. The **Processing real time events** (rtEventsProcessing) workflow processes the event and searches for an existing delivery for the current month.

    >[!NOTE]
    >
    >If not found, a new delivery is created and the event is assigned to the new delivery.

1. The transactional email is sent and the delivery status changes to **[!UICONTROL Sent]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and updates the delivery logs on the control instance.
1. The control instance searches for an existing delivery for week 40 (2020-09-28_Template_1).

    >[!NOTE]
    >
    >If not found, a new delivery is created.

1. The week after, an inbound bounce is received for the event.
1. The status of the event changes to **[!UICONTROL Delivery failed]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and searches for a delivery for week 41 (2020-10-05_Template_1) to update the delivery logs. The delivery logs are then linked to a new delivery for the current week.

To summarize, the deliveries weekly accumulate the events based on the latest event update, and not on the event creation date.

Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID changes every week.-->