---
solution: Campaign Classic
product: campaign
title: SQL-code en JavaScript-code
description: Meer informatie over workflowactiviteiten voor SQL- en JavaScript-codes
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 5%

---


# SQL-code en JavaScript-code{#sql-code-and-javascript-code}

## SQL-code {#sql-code}

Een **[!UICONTROL SQL code]** activiteit voert een SQL manuscript uit. Het script is een JST-sjabloon.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   Het centrale gebied van de editor bevat het script dat moet worden uitgevoerd. Dit script is een JST-sjabloon en kan daarom worden geconfigureerd volgens de workflowcontext.

* **[!UICONTROL Processing errors]**

   Raadpleeg [Verwerkingsfouten](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## JavaScript-code en geavanceerde JavaScript-code {#javascript-code}

**[!UICONTROL JavaScript code]** en **[!UICONTROL Advanced JavaScript code]** activiteiten voeren een JavaScript-script uit in de context van een workflow. Raadpleeg de sectie [JavaScript-scripts en -sjablonen](../../workflow/using/javascript-scripts-and-templates.md) voor meer informatie over scripts.

>[!NOTE]
>
>Standaard kan de uitvoeringsfase van **[!UICONTROL JavaScript code]** en de **[!UICONTROL Advanced JavaScript code]** activiteiten niet langer duren dan 1 uur. Na deze vertraging wordt het proces afgebroken met een foutbericht en mislukt de uitvoering van de activiteit.
>
>U kunt deze vertraging wijzigen in het **[!UICONTROL Stop execution after]** veld dat beschikbaar is in de eigenschappen van de activiteiten.

* **[!UICONTROL JavaScript code]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**: Het centrale gebied van de editor bevat het script dat moet worden uitgevoerd.
   * **[!UICONTROL Processing errors]**: Raadpleeg [Verwerkingsfouten](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**: De eerste streek van de redacteur bevat het manuscript om tijdens de eerste vraag uit te voeren.
   * **[!UICONTROL Next calls]**: De tweede streek van de redacteur bevat het manuscript om tijdens de volgende vraag uit te voeren.
   * **[!UICONTROL Transitions]**: U kunt verschillende uitvoerovergangen voor activiteiten definiëren.
   * **[!UICONTROL Schedule]**: Op het **[!UICONTROL Schedule]** tabblad kunt u plannen wanneer de activiteit moet worden geactiveerd.
