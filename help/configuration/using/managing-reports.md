---
product: campaign
title: Rapporten beheren
description: Rapporten beheren
feature: Reporting, Configuration
role: Data Engineer, Developer
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# Rapporten beheren{#managing-reports}



Rapporten die zijn gebaseerd op een schema dat specifiek is voor de standaard Adobe Campaign-ontvangers (NM:ontvanger of gekoppeld schema) moeten opnieuw worden ontwikkeld om rekening te houden met de gegevens uit de aangepaste tabel en de tabellen die via de doeltoewijzing zijn gekoppeld (zie de [Doeltoewijzing](../../configuration/using/target-mapping.md) ).

Als u nieuwe rapporten wilt maken, raadpleegt u [deze sectie](../../reporting/using/about-reports-creation-in-campaign.md).

In sommige gevallen moet u ook nieuwe blokjes plaatsen die specifiek zijn voor deze tabellen. De kubussen worden gedetailleerd in [deze sectie](../../reporting/using/ac-cubes.md).

De volgende verslagen hebben betrekking op:

* **[!UICONTROL Recent proposition tracking]** (recentProposities): propositiebepaling in real time.
* **[!UICONTROL Breakdown of opens]** (openByUserAgent): opent uitgesplitst volgens gebruikerssoftware.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActiviteiten): analyse van gezamenlijke activiteiten, open en abonnementen per tijdsperiode.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): trackingsindicatoren voor een levering op een mobiele toepassing.
* **[!UICONTROL Offer analysis]** (offerteanalyse): aanbiedingsanalyse per datum en kanaal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): reactiviteitspercentage voor de meest recente leveringen.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): uitsplitsing van actieve abonnementen per mobiele toepassing.
