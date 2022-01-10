---
product: campaign
title: Instellingen voor uitvoering
description: Instellingen voor uitvoering
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: 7728826eea199d2367fcbf556c01ec9d6cae466f
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---

# Instellingen voor uitvoering{#execution-settings}

![](../../assets/common.svg)

Wanneer u een simulatie maakt, kunt u indien nodig uitvoeringsinstellingen opgeven. Deze montages laten u de simulatie tijdens een tijd van lage activiteit afhankelijk van zijn prioriteit uitvoeren, of SQL vragen in het logboek registreren. Dit werkgebied is optioneel.

Deze instellingen kunt u later wijzigen in het dialoogvenster **[!UICONTROL General]** van het simulatievenster.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** : Hiermee kunt u de simulatie plannen op basis van de gekozen prioriteit (Laag, Gemiddeld of Hoog) om de Adobe Campaign-prestaties te optimaliseren.
* **[!UICONTROL Priority]** : dit is het niveau dat op de simulatie wordt toegepast om het te plannen. Wanneer de **[!UICONTROL Schedule execution for a time of low activity]** is ingeschakeld, wordt in de workflow voor het verwerken van de campagne een tijd met een lage activiteit geselecteerd om de campagne te starten.
* **[!UICONTROL Log SQL queries in the journal]** : deze functionaliteit is alleen voor ervaren gebruikers. Het laat u een lusje aan het logboek toevoegen die SQL vragen toont om mogelijke storingen te ontdekken als de simulatie met fouten eindigt.
