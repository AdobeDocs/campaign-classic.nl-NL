---
title: Een rapport naar een lijst verzenden
seo-title: Een rapport naar een lijst verzenden
description: Een rapport naar een lijst verzenden
seo-description: null
page-status-flag: never-activated
uuid: 29759fd8-47f3-47cc-9f7e-263e305fd6fb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 41b8a8a8-efac-4e8e-8aea-d4fd06c46e74
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Een rapport naar een lijst verzenden{#sending-a-report-to-a-list}

In dit geval wordt beschreven hoe u een maandelijks rapport buiten de doos in PDF-indeling kunt genereren en hoe u dit rapport naar een lijst met ontvangers kunt verzenden. **[!UICONTROL Tracking indicators]**

![](assets/use_case_report_intro.png)

De belangrijkste implementatiestappen voor dit gebruiksgeval zijn:

* Een lijst maken van ontvangers die de levering zullen ontvangen (zie: [Stap 1: De lijst met](#step-1--creating-the-recipient-list)ontvangers maken).
* Creërend een leveringsmalplaatje dat u een nieuwe levering zal laten produceren telkens als het werkschema wordt uitgevoerd (verwijs naar: [Stap 2: Het creëren van het leveringsmalplaatje](#step-2--creating-the-delivery-template)).
* Een werkstroom maken waarmee u het rapport in PDF-indeling kunt genereren en naar de lijst met ontvangers kunt verzenden (zie: [Stap 3: De workflow](#step-3--creating-the-workflow)maken).

## Stap 1: De lijst met ontvangers maken {#step-1--creating-the-recipient-list}

Ga naar het **[!UICONTROL Profiles and targets]** universum, klik op de **[!UICONTROL Lists]** link, dan op de **[!UICONTROL Create]** knop. Selecteer **[!UICONTROL New list]** en maak een nieuwe lijst met ontvangers voor het rapport waarnaar u wilt verzenden.

![](assets/use_case_report_1.png)

Raadpleeg deze [sectie](../../platform/using/creating-and-managing-lists.md)voor meer informatie over het maken van lijsten.

## Stap 2: De leveringssjabloon maken {#step-2--creating-the-delivery-template}

1. Ga naar het **[!UICONTROL Resources > Templates > Delivery templates]** knooppunt van de Adobe Campagne-verkenner en dupliceer de **[!UICONTROL Email delivery]** out-of-the-box sjabloon.

   ![](assets/use_case_report_2.png)

   Raadpleeg deze [sectie](../../delivery/using/about-templates.md)voor meer informatie over het maken van een leveringssjabloon.

1. Voer de verschillende sjabloonparameters in: label, doel (de lijst met eerder gemaakte ontvangers), onderwerp en inhoud.

   ![](assets/use_case_report_3.png)

1. Telkens wanneer het werkschema wordt uitgevoerd, wordt het **[!UICONTROL Tracking indicators]** rapport bijgewerkt (verwijs naar [Stap 3: De workflow](#step-3--creating-the-workflow)maken). Om de recentste versie van het rapport in de levering te omvatten, moet u toevoegen: **[!UICONTROL Calculated attachment]**:

   Raadpleeg deze [sectie](../../delivery/using/attaching-files.md#creating-a-calculated-attachment)voor meer informatie over het maken van een berekende bijlage.

   * Klik op de **[!UICONTROL Attachments]** koppeling en klik **[!UICONTROL Add]** op de koppeling en selecteer **[!UICONTROL Calculated attachment]**.

      ![](assets/use_case_report_4.png)

   * Ga naar het **[!UICONTROL Type]** veld en selecteer de vierde optie: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

      ![](assets/use_case_report_5.png)

      De waarde die in het **[!UICONTROL Label]** veld wordt ingevoerd, wordt niet weergegeven in de uiteindelijke aflevering.

   * Ga naar de bewerkingszone en voer het toegangspad en de naam van het bestand in.

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >Het bestand moet aanwezig zijn op de server. Het pad en de naam moeten identiek zijn aan de waarden die worden ingevoerd in de **[!UICONTROL JavaScript code]** tekstactiviteit van de workflow (zie: [Stap 3: De workflow](#step-3--creating-the-workflow)maken).

   * Selecteer het **[!UICONTROL Advanced]** tabblad en controleer **[!UICONTROL Script the name of the file name displayed in the mails sent]**. Ga naar de uitgeeft streek en ga de naam in u de gehechtheid in de definitieve levering wilt geven.

      ![](assets/use_case_report_6bis.png)

## Stap 3: De workflow maken {#step-3--creating-the-workflow}

De volgende workflow is gemaakt voor dit gebruik. Het heeft drie activiteiten:

* Eén **[!UICONTROL Scheduler]** type activiteit waarmee u de workflow één keer per maand kunt uitvoeren.
* Een **[!UICONTROL JavaScript code]** type activiteit waarmee u het rapport in PDF-indeling kunt genereren.
* één **[!UICONTROL Delivery]** typeactiviteit die het eerder gecreeerde leveringsmalplaatje gebruikt.

![](assets/use_case_report_8.png)

1. Ga nu naar het **[!UICONTROL Administration > Production > Technical workflows]** knooppunt en maak een nieuwe workflow.

   ![](assets/use_case_report_7.png)

1. Begin door een **[!UICONTROL Scheduler]** typeactiviteit toe te voegen en het te vormen zodat het werkschema op de eerste Maandag van de maand uitvoert.

   ![](assets/use_case_report_9.png)

   Voor meer bij het vormen van de planner, verwijs naar [Planner](../../workflow/using/scheduler.md).

1. Voeg vervolgens een **[!UICONTROL JavaScript code]** tekstactiviteit toe.

   ![](assets/use_case_report_10.png)

   Voer de volgende code in de bewerkingszone in:

   ```
   var reportName = "deliveryFeedback";
   var path = "/tmp/deliveryFeedback.pdf";
   var exportFormat = "PDF";
   var reportURL = "<PUT THE URL OF THE REPORT HERE>";
   var _ctx = <ctx _context="global" _reportContext="deliveryFeedback" />
   var isAdhoc = 0;
   
   xtk.report.export(reportName, _ctx, exportFormat, path, isAdhoc);
   ```

   De volgende variabelen worden gebruikt:

   * **var reportName**: Voer de interne naam van het rapport tussen dubbele aanhalingstekens in. In dit geval is de interne naam van het **trackingindicatorrapport** &quot;deliveryFeedback&quot;.
   * **var pad**: Voer het opslagpad in van het bestand (&quot;tmp/files/&quot;), de naam die u aan het bestand wilt geven (&quot;deliveryFeedback&quot;) en de bestandsextensie (&quot;.pdf&quot;). In dit geval hebben we de interne naam gebruikt als bestandsnaam. Waarden moeten tussen dubbele aanhalingstekens liggen en door het plusteken (+) worden gescheiden.

      >[!CAUTION]
      >
      >Het bestand moet op de server worden opgeslagen. U moet hetzelfde pad en dezelfde naam invoeren op het **[!UICONTROL General]** tabblad van het bewerkvenster voor de berekende bijlage (zie: [Stap 2: Het creëren van het leveringsmalplaatje](#step-2--creating-the-delivery-template)).

   * **var exportFormat**: Voer de exportindeling van het bestand (&quot;PDF&quot;) in.
   * **var_ctx** (context): in dit geval gebruiken wij het **[!UICONTROL Tracking indicators]** verslag in zijn mondiale context .

1. Voltooi door een **[!UICONTROL Delivery]** tekstactiviteit met de volgende opties toe te voegen:

   * **[!UICONTROL Delivery]**: Selecteer **[!UICONTROL New, created from a template]** en selecteer de eerder gemaakte leveringssjabloon.
   * Selecteer voor de velden **[!UICONTROL Recipients]** en **[!UICONTROL Content]** velden **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to execute]**: selecteren **[!UICONTROL Prepare and start]**.
   * Niet controleren **[!UICONTROL Generate an outbound transition]** en **[!UICONTROL Process errors]**.
   ![](assets/use_case_report_11.png)

