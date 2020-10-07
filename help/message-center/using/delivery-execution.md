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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 9%

---


# Uitvoering van levering{#delivery-execution}

>[!NOTE]
>
>MTA geeft voorrang aan verwerking van de transactionele berichten over om het even welke andere levering.

Op de uitvoeringsinstantie wordt de levering verzonden zodra het verrijkingsstadium is voltooid en een leveringssjabloon aan de gebeurtenis is gekoppeld. Alle leveringen worden gegroepeerd in de **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** map.

![](assets/messagecenter_deliveries_execinstances_001.png)

Standaard worden ze in submappen gesorteerd op leveringsmaand.

Deze soort kan in de eigenschappen van het berichtmalplaatje worden veranderd zoals hieronder getoond.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Voor ontvangen of hybride installaties, als u aan Verbeterde MTA hebt bevorderd, kunnen alle transactionele berichten ook met Adobe Campaign Verbeterde MTA voor betere leverability, productie, en stuitbehandeling worden verzonden. Alle effecten zijn gelijk aan die voor standaardmarketingberichten en worden beschreven in het document [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/nl/campaign/kb/acc-campaign-enhanced-mta.html) .