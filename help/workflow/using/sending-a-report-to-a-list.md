---
product: campaign
title: Een rapport naar een lijst verzenden
description: Leer hoe u een rapport naar een lijst met een workflow kunt verzenden
feature: Workflows
hide: true
hidefromtoc: true
exl-id: cb24aea5-f3c7-4b17-8899-1792ea18c235
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 1%

---

# Een rapport naar een lijst verzenden{#sending-a-report-to-a-list}



In dit geval wordt beschreven hoe u een maandelijks out-of-the-box **[!UICONTROL Tracking indicators]** -rapport in PDF-indeling kunt genereren en hoe u dit rapport naar een lijst met ontvangers kunt verzenden.

![](assets/use_case_report_intro.png)

De belangrijkste implementatiestappen voor dit gebruiksgeval zijn:

* Creërend een lijst van ontvangers die de levering zullen ontvangen (verwijs naar: [ Stap 1: Creërend de ontvankelijke lijst ](#step-1--creating-the-recipient-list)).
* Creërend een leveringsmalplaatje dat u een nieuwe levering zal laten produceren telkens als het werkschema wordt uitgevoerd (verwijs naar: [ Stap 2: Creërend het leveringsmalplaatje ](#step-2--creating-the-delivery-template)).
* Creërend een werkschema dat u het rapport in het formaat van PDF zal produceren en het naar de lijst van ontvangers zal verzenden (verwijs naar: [ Stap 3: Creërend het werkschema ](#step-3--creating-the-workflow)).

## Stap 1: De lijst met ontvangers maken {#step-1--creating-the-recipient-list}

Ga naar het tabblad **[!UICONTROL Profiles and targets]** en klik op de koppeling **[!UICONTROL Lists]** en vervolgens op de knop **[!UICONTROL Create]** . Selecteer **[!UICONTROL New list]** en maak een nieuwe lijst met ontvangers waarnaar het rapport moet worden verzonden.

![](assets/use_case_report_1.png)

Voor meer bij het creëren van lijsten, verwijs naar deze [ sectie ](../../platform/using/creating-and-managing-lists.md).

## Stap 2: Het creëren van het leveringsmalplaatje {#step-2--creating-the-delivery-template}

1. Ga naar het knooppunt **[!UICONTROL Resources > Templates > Delivery templates]** van de Adobe Campaign-verkenner en dupliceer de **[!UICONTROL Email delivery]** out-of-the-box sjabloon.

   ![](assets/use_case_report_2.png)

   Voor meer bij het creëren van een leveringsmalplaatje, verwijs naar deze [ sectie ](../../delivery/using/about-templates.md).

1. Voer de verschillende sjabloonparameters in: label, doel (de lijst met eerder gemaakte ontvangers), onderwerp en inhoud.

   ![](assets/use_case_report_3.png)

1. Telkens als het werkschema wordt uitgevoerd, wordt het **[!UICONTROL Tracking indicators]** rapport bijgewerkt (verwijs naar [ Stap 3: Creërend het werkschema ](#step-3--creating-the-workflow)). Als u de meest recente versie van het rapport in de levering wilt opnemen, moet u een **[!UICONTROL Calculated attachment]** toevoegen:

   Voor meer bij het creëren van een berekende gehechtheid, verwijs naar deze [ sectie ](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

   * Klik op de koppeling **[!UICONTROL Attachments]** , klik op **[!UICONTROL Add]** en selecteer vervolgens **[!UICONTROL Calculated attachment]** .

     ![](assets/use_case_report_4.png)

   * Ga naar het veld **[!UICONTROL Type]** en selecteer de vierde optie: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]** .

     ![](assets/use_case_report_5.png)

     De waarde die in het veld **[!UICONTROL Label]** wordt ingevoerd, wordt niet weergegeven in de uiteindelijke aflevering.

   * Ga naar de bewerkingszone en voer het toegangspad en de naam van het bestand in.

     ![](assets/use_case_report_6.png)

     >[!CAUTION]
     >
     >Het bestand moet aanwezig zijn op de server. Zijn weg en naam moeten aan die ingegaan in de **[!UICONTROL JavaScript code]** typeactiviteit van het werkschema (verwijs naar: [ Stap 3: Creërend het werkschema ](#step-3--creating-the-workflow)) identiek zijn.

   * Selecteer de tab **[!UICONTROL Advanced]** en controleer **[!UICONTROL Script the name of the file name displayed in the mails sent]** . Ga naar de uitgeeft streek en ga de naam in u de gehechtheid in de definitieve levering wilt geven.

     ![](assets/use_case_report_6bis.png)

## Stap 3: De workflow maken {#step-3--creating-the-workflow}

De volgende workflow is gemaakt voor dit gebruik. Het heeft drie activiteiten:

* Een **[!UICONTROL Scheduler]** type activiteit waarmee u de workflow één keer per maand kunt uitvoeren.
* Een **[!UICONTROL JavaScript code]** type-activiteit waarmee u het rapport kunt genereren in PDF-indeling.
* één **[!UICONTROL Delivery]** type activiteit die het eerder gecreeerde leveringsmalplaatje gebruikt.

![](assets/use_case_report_8.png)

1. Ga nu naar het knooppunt **[!UICONTROL Administration > Production > Technical workflows]** en maak een nieuwe workflow.

   ![](assets/use_case_report_7.png)

1. Begin door een **[!UICONTROL Scheduler]** type activiteit toe te voegen en vorm het zodat het werkschema op de eerste Maandag van de maand uitvoert.

   ![](assets/use_case_report_9.png)

   Voor meer bij het vormen van de planner, verwijs naar [ Planner ](scheduler.md).

1. Voeg vervolgens een **[!UICONTROL JavaScript code]** type-activiteit toe.

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

   * **var reportName**: ga de interne naam van het rapport in dubbele citaten in. In dit geval, is de interne naam van het **het Volgen indicator** rapport &quot;deliveryFeedback&quot;.
   * **var weg**: ga sparen weg van het dossier (&quot;tmp/files/&quot;), de naam in u het dossier (&quot;deliveryFeedback&quot;) en de dossieruitbreiding (&quot;.pdf&quot;) wilt geven. In dit geval hebben we de interne naam gebruikt als bestandsnaam. Waarden moeten tussen dubbele aanhalingstekens liggen en door het plusteken (+) worden gescheiden.

     >[!CAUTION]
     >
     >Het bestand moet op de server worden opgeslagen. U moet de zelfde weg en de zelfde naam in het **[!UICONTROL General]** lusje van uitgeven venster voor de berekende gehechtheid ingaan (verwijs naar: [ Stap 2: Creërend het leveringsmalplaatje ](#step-2--creating-the-delivery-template)).

   * **var exportFormat**: ga het uitvoerformaat van het dossier (&quot;PDF&quot;) in.
   * **var _ctx** (context): in dit geval, gebruiken wij het **[!UICONTROL Tracking indicators]** rapport in zijn globale context.

1. Voltooi de bewerking door een tekstactiviteit **[!UICONTROL Delivery]** toe te voegen met de volgende opties:

   * **[!UICONTROL Delivery]**: selecteer **[!UICONTROL New, created from a template]** en selecteer de eerder gemaakte leveringssjabloon.
   * Selecteer **[!UICONTROL Specified in the delivery]** voor de velden **[!UICONTROL Recipients]** en **[!UICONTROL Content]** .
   * **[!UICONTROL Action to execute]**: select **[!UICONTROL Prepare and start]** .
   * U kunt **[!UICONTROL Generate an outbound transition]** en **[!UICONTROL Process errors]** niet controleren.

   ![](assets/use_case_report_11.png)
