---
title: Uitvoering van levering
seo-title: Uitvoering van levering
description: Uitvoering van levering
seo-description: null
page-status-flag: never-activated
uuid: d4f4cea7-783b-45d3-b004-297104f0a906
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: afb375de-2de3-47ad-8b37-664cc04864e8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# Uitvoering van levering{#delivery-execution}

>[!NOTE]
>
>MTA geeft voorrang aan verwerking van de transactionele berichten over om het even welke andere levering.

Voor de uitvoeringsinstantie, zodra de verrijkingsstadia volledig zijn en een leveringsmalplaatje met de gebeurtenis verbonden is, wordt de levering verzonden. Alle leveringen worden gegroepeerd in de **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** map.

![](assets/messagecenter_deliveries_execinstances_001.png)

Standaard worden ze in submappen gesorteerd op leveringsmaand.

Deze soort kan in de eigenschappen van het berichtmalplaatje worden veranderd zoals hieronder getoond.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Voor gehoste of hybride installaties, als u tot Verbeterde MTA hebt bevorderd, kunnen alle transactionele berichten ook met de Verbeterde MTA van de Campagne van Adobe voor betere leverability, productie, en stuitbehandeling worden verzonden. Alle effecten zijn gelijk aan die voor standaardmarketingberichten en worden beschreven in het document [Adobe Campagne Enhanced MTA](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) .