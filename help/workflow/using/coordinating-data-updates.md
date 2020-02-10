---
title: Gegevensupdates coördineren
seo-title: Gegevensupdates coördineren
description: Gegevensupdates coördineren
seo-description: null
page-status-flag: never-activated
uuid: 003d63f8-3169-4190-882e-e360a83ccafb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: efe09c66-b74b-48f0-9042-5da4342e014e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Gegevensupdates coördineren{#coordinating-data-updates}

In dit geval wordt beschreven hoe u een workflow maakt waarmee u gelijktijdige updates kunt beheren wanneer u verschillende uitvoeringen van een workflow gebruikt.

Het doel is te controleren of het updateproces is beëindigd voordat een andere updatebewerking wordt uitgevoerd. Hiervoor wordt een instantievariabele ingesteld en wordt in de workflow getest of de instantie wordt uitgevoerd om te bepalen of de workflow moet worden voortgezet en of de update moet worden uitgevoerd.

![](assets/uc_dataupdate_wkf.png)

Deze workflow bestaat uit:

* een activiteit van de **Planner** , die het werkschema op een specifieke frequentie uitvoert.
* een **testactiviteit** die controleert of de workflow al wordt uitgevoerd.
* **De activiteiten van de vraag** en van de **Update gegevens** voor het geval de werkschema niet reeds uitvoert, gevolgd door een activiteit van het **Eind** die de veranderlijke van de werkschemainstantie aan vals herinitialiseert.
* Een activiteit van het **Eind** als het werkschema reeds uitvoert.

Volg onderstaande stappen om de workflow te maken:

1. Voeg een activiteit van de **Planner** toe, dan vorm zijn frequentie volgens uw behoeften.
1. Voeg een activiteit van de **Test** toe om te controleren of het werkschema reeds uitvoert, dan vorm het zoals hieronder.

   >[!NOTE]
   >
   >&quot;isRunning&quot; is de naam van de instantievariabele die we voor dit voorbeeld hebben gekozen. Dit is geen ingebouwde variabele.

   ![](assets/uc_dataupdate_test.png)

1. Voeg een activiteit van het **Eind** aan **Geen** vork toe. Op deze manier wordt niets uitgevoerd als de workflow al wordt uitgevoerd.
1. Voeg de gewenste activiteiten toe aan de **Ja** -vork. In ons geval, **vraag** en **werk de activiteiten van Gegevens** bij.
1. Open de eerste activiteit, dan voeg **instance.vars.isRunning = ware** bevel op het **[!UICONTROL Advanced]** lusje toe. Op deze manier wordt de instantievariabele ingesteld als actief.

   ![](assets/uc_dataupdate_query.png)

1. Voeg een activiteit van het **Eind** aan het eind van de **[!UICONTROL Yes]** vork toe, dan voeg **instance.vars.isRunning = vals** bevel op het **[!UICONTROL Advanced]** lusje toe.

   Op deze manier wordt geen actie uitgevoerd zolang de workflow wordt uitgevoerd.

   ![](assets/uc_dataupdate_end.png)

**Verwante onderwerpen:**

* [Meerdere uitvoeringen voorkomen](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [Gegevensactiviteit bijwerken](../../workflow/using/update-data.md)

