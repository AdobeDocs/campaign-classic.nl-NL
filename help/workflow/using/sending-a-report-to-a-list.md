---
solution: Campaign Classic
product: campaign
title: Een rapport naar een lijst verzenden
description: Leer hoe u een rapport naar een lijst met een workflow kunt verzenden
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---


# Een rapport naar een lijst verzenden{#sending-a-report-to-a-list}

In dit geval wordt beschreven hoe u een maandelijks rapport in PDF-indeling buiten het vak kunt genereren en hoe u het rapport naar een lijst met ontvangers kunt verzenden.**[!UICONTROL Tracking indicators]**

![](assets/use_case_report_intro.png)

De belangrijkste implementatiestappen voor dit gebruiksgeval zijn:

* Een lijst maken van ontvangers die de levering zullen ontvangen (zie: [Stap 1: Het creëren van de ontvankelijke lijst](#step-1--creating-the-recipient-list)).
* Creërend een leveringsmalplaatje dat u een nieuwe levering zal laten produceren telkens als het werkschema wordt uitgevoerd (verwijs naar: [Stap 2: Het creëren van het leveringsmalplaatje](#step-2--creating-the-delivery-template)).
* Een werkstroom maken waarmee u het rapport in PDF-indeling kunt genereren en naar de lijst met ontvangers kunt verzenden (zie: [Stap 3: Het maken van de workflow (](#step-3--creating-the-workflow)).

## Stap 1: De lijst met ontvangers maken {#step-1--creating-the-recipient-list}

Ga naar **[!UICONTROL Profiles and targets]** universum, klik **[!UICONTROL Lists]** verbinding, dan **[!UICONTROL Create]** knoop. Selecteer **[!UICONTROL New list]** en creeer een nieuwe ontvankelijke lijst voor het rapport dat moet worden verzonden naar.

![](assets/use_case_report_1.png)

Voor meer bij het creëren van lijsten, verwijs naar dit [sectie](../../platform/using/creating-and-managing-lists.md).

## Stap 2: Het creëren van het leveringsmalplaatje {#step-2--creating-the-delivery-template}

1. Ga naar de **[!UICONTROL Resources > Templates > Delivery templates]** knoop van de ontdekkingsreiziger van Adobe Campaign en dupliceer **[!UICONTROL Email delivery]** out-of-the-box malplaatje.

   ![](assets/use_case_report_2.png)

   Voor meer bij het creëren van een leveringsmalplaatje, verwijs naar dit [sectie](../../delivery/using/about-templates.md).

1. Voer de verschillende sjabloonparameters in: label, doel (de lijst met eerder gemaakte ontvangers), onderwerp en inhoud.

   ![](assets/use_case_report_3.png)

1. Telkens wanneer de workflow wordt uitgevoerd, wordt het **[!UICONTROL Tracking indicators]**-rapport bijgewerkt (zie [Stap 3: Het maken van de workflow (a2/>). ](#step-3--creating-the-workflow) Om de recentste versie van het rapport in de levering te omvatten, moet u **[!UICONTROL Calculated attachment]** toevoegen:

   Voor meer bij het creëren van een berekende gehechtheid, verwijs naar dit [sectie](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

   * Klik op de koppeling **[!UICONTROL Attachments]** en klik op **[!UICONTROL Add]** en selecteer **[!UICONTROL Calculated attachment]**.

      ![](assets/use_case_report_4.png)

   * Ga naar het **[!UICONTROL Type]** gebied en selecteer de vierde optie: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

      ![](assets/use_case_report_5.png)

      De waarde die in het veld **[!UICONTROL Label]** wordt ingevoerd, wordt niet weergegeven in de uiteindelijke levering.

   * Ga naar de bewerkingszone en voer het toegangspad en de naam van het bestand in.

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >Het bestand moet aanwezig zijn op de server. Het pad en de naam moeten identiek zijn aan de waarden die worden ingevoerd in de **[!UICONTROL JavaScript code]**-tekstactiviteit van de workflow (zie: [Stap 3: Het maken van de workflow (a2/>).](#step-3--creating-the-workflow)

   * Selecteer de tab **[!UICONTROL Advanced]** en controleer **[!UICONTROL Script the name of the file name displayed in the mails sent]**. Ga naar de uitgeeft streek en ga de naam in u de gehechtheid in de definitieve levering wilt geven.

      ![](assets/use_case_report_6bis.png)

## Stap 3: De workflow {#step-3--creating-the-workflow} maken

De volgende workflow is gemaakt voor dit gebruik. Het heeft drie activiteiten:

* Eén **[!UICONTROL Scheduler]** typt activiteit waarmee u de workflow eenmaal per maand kunt uitvoeren.
* Eén **[!UICONTROL JavaScript code]**-type-activiteit waarmee u het rapport in PDF-indeling kunt genereren.
* één **[!UICONTROL Delivery]** type activiteit die het eerder gecreeerde leveringsmalplaatje gebruikt.

![](assets/use_case_report_8.png)

1. Ga nu naar **[!UICONTROL Administration > Production > Technical workflows]** knoop en creeer een nieuwe werkschema.

   ![](assets/use_case_report_7.png)

1. Begin door een **[!UICONTROL Scheduler]** type activiteit toe te voegen en vorm het zodat het werkschema op de eerste Maandag van de maand uitvoert.

   ![](assets/use_case_report_9.png)

   Voor meer bij het vormen van de planner, verwijs naar [Planner](../../workflow/using/scheduler.md).

1. Voeg vervolgens een **[!UICONTROL JavaScript code]**-tekstactiviteit toe.

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

   * **var reportName**: Voer de interne naam van het rapport tussen dubbele aanhalingstekens in. In dit geval is de interne naam van het **Trackingindicator**-rapport &quot;deliveryFeedback&quot;.
   * **var pad**: Voer het opslagpad in van het bestand (&quot;tmp/files/&quot;), de naam die u aan het bestand wilt geven (&quot;deliveryFeedback&quot;) en de bestandsextensie (&quot;.pdf&quot;). In dit geval hebben we de interne naam gebruikt als bestandsnaam. Waarden moeten tussen dubbele aanhalingstekens liggen en door het plusteken (+) worden gescheiden.

      >[!CAUTION]
      >
      >Het bestand moet op de server worden opgeslagen. U moet hetzelfde pad en dezelfde naam invoeren op het tabblad **[!UICONTROL General]** van het bewerkvenster voor de berekende bijlage (verwijs naar: [Stap 2: Het creëren van het leveringsmalplaatje](#step-2--creating-the-delivery-template)).

   * **var exportFormat**: Voer de exportindeling van het bestand (&quot;PDF&quot;) in.
   * **var_ctx** (context): in dit geval gebruiken wij het  **[!UICONTROL Tracking indicators]** verslag in zijn mondiale context .

1. Voltooi door een **[!UICONTROL Delivery]** type activiteit met de volgende opties toe te voegen:

   * **[!UICONTROL Delivery]**: Selecteer  **[!UICONTROL New, created from a template]** en selecteer de eerder gemaakte leveringssjabloon.
   * Selecteer **[!UICONTROL Specified in the delivery]** voor de velden **[!UICONTROL Recipients]** en **[!UICONTROL Content]**.
   * **[!UICONTROL Action to execute]**: selecteren  **[!UICONTROL Prepare and start]**.
   * **[!UICONTROL Generate an outbound transition]** en **[!UICONTROL Process errors]** niet controleren.

   ![](assets/use_case_report_11.png)

