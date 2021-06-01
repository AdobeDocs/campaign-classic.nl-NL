---
product: campaign
title: Contentmanagement
description: Contentmanagement
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: eb92a7c7-edfa-4062-b473-6d8b50d35e5f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 2%

---

# Contentmanagement{#content-management}

Met een activiteit **Inhoudsbeheer** kunt u inhoud maken en manipuleren en bestanden genereren op basis van deze inhoud. Deze inhoud kan vervolgens worden geleverd via een &#39;leveringsactiviteit&#39;.

>[!CAUTION]
>
>Inhoudsbeheer is een optionele Adobe Campaign-module. Controleer hiervoor uw licentieovereenkomst.

De eigenschappen van de activiteit zijn verdeeld in drie stappen:

* **Selectie** van inhoud: de inhoud kan eerder zijn gemaakt of via de activiteit zijn gemaakt.
* **Inhoud bijwerken**: de taak kan het onderwerp van de inhoud wijzigen of alle inhoud van XML invoeren.
* **Actie**: de resulterende inhoud kan worden opgeslagen of gegenereerd.

   ![](assets/content_mgmt_edit.png)

   Raadpleeg deze [sectie](../../delivery/using/about-content-management.md) voor meer informatie over het configureren en gebruiken van contentbeheer in Adobe Campaign.

1. **Inhoud**

   * **[!UICONTROL Specified in the transition]**

      Met deze optie kunt u de inhoud gebruiken die is opgegeven in de overgang, dat wil zeggen de gebeurtenis die inhoudsbeheer activeert, moet een **[!UICONTROL contentId]**-variabele bevatten. Deze variabele kan door een vorig inhoudsbeheer of door om het even welk manuscript zijn geplaatst.

   * **[!UICONTROL Explicit]**

      Met deze optie kunt u reeds gemaakte inhoud selecteren via het veld **[!UICONTROL Content]**. Dit veld is alleen zichtbaar wanneer de optie **[!UICONTROL Explicit]** is geselecteerd.

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      De inhoud-id wordt berekend door een script. In het veld **[!UICONTROL Script]** kunt u een JavaScript-sjabloon definiëren waarmee de id (primaire sleutel) van de inhoud wordt geëvalueerd. Dit veld is alleen zichtbaar wanneer de optie **[!UICONTROL Calculated by a script]** is geselecteerd.

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      Hiermee maakt u nieuwe inhoud op basis van een publicatiesjabloon. Deze nieuwe inhoud wordt opgeslagen in het bestand dat is opgegeven in het veld **[!UICONTROL String]**. In het veld **[!UICONTROL Template]** wordt de publicatiesjabloon opgegeven die moet worden gebruikt om de inhoud te maken.

      ![](assets/content_mgmt_new.png)

1. **Inhoud bijwerken**

   * **[!UICONTROL Subject]**

      In dit veld kunt u het onderwerp van de inhoud wijzigen.

   * **[!UICONTROL Access to data from an XML feed]**

      Met deze optie kunt u de inhoud samenstellen op basis van een XML-document dat via een XSL-stijlpagina is gedownload. Wanneer deze optie is geselecteerd, geeft het veld **[!UICONTROL URL]** de URL voor het downloaden van XML-inhoud op. Met **[!UICONTROL XSL stylesheet]** kunt u de stijlpagina opgeven die moet worden gebruikt om het gedownloade XML-document te transformeren. Deze eigenschap is optioneel.

      ![](assets/content_mgmt_xmlcontent.png)

1. **Uit te voeren handeling**

   * **[!UICONTROL Save]**

      Met deze optie slaat u de gemaakte of gewijzigde inhoud op.

      De uitgaande overgang wordt slechts eenmaal geactiveerd, met de inhoud die in de **[!UICONTROL contentId]** variabele als parameter wordt opgeslagen.

   * **[!UICONTROL Generate]**

      Met deze optie slaat u de inhoud op en genereert u vervolgens de uitvoerbestanden voor elke transformatiesjabloon met een publicatie van het type &#39;Bestand&#39;.

      ![](assets/content_mgmt_generate.png)

      De uitgaande overgang wordt geactiveerd voor elk bestand dat wordt gegenereerd met de id van de inhoud die als parameter in de variabele **[!UICONTROL contentId]** is opgeslagen en de bestandsnaam in de variabele **[!UICONTROL filename]**.

## Invoerparameters {#input-parameters}

* contentId

Identifier van de inhoud die moet worden gebruikt als de optie **[!UICONTROL Specified in the transition]** is ingeschakeld.

## Uitvoerparameters {#output-parameters}

* contentId

   Inhoud-id.

* filename

   Volledige naam van het gegenereerde bestand als de geselecteerde actie **[!UICONTROL Generate]** is.

## Voorbeelden {#examples}

Voorbeelden worden gegeven in deze [sectie](../../delivery/using/automating-via-workflows.md#examples).
