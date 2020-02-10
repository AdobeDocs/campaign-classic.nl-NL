---
title: Inhoudsbeheer
seo-title: Inhoudsbeheer
description: Inhoudsbeheer
seo-description: null
page-status-flag: never-activated
uuid: 8d1bf84b-96e5-4d3d-9d77-42d2027a74db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 13b72aa1-de40-4548-835b-97e765e04e95
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Inhoudsbeheer{#content-management}

Met een **inhoudsbeheeractiviteit** kunt u inhoud maken en manipuleren en bestanden genereren op basis van deze inhoud. Deze inhoud kan vervolgens worden geleverd via een &#39;leveringsactiviteit&#39;.

>[!CAUTION]
>
>Inhoudsbeheer is een optionele Adobe Campagne-module. Controleer uw licentieovereenkomst.

De eigenschappen van de activiteit zijn verdeeld in drie stappen:

* **Selectie** van inhoud: de inhoud kan eerder zijn gemaakt of via de activiteit zijn gemaakt.
* **Inhoud bijwerken**: de taak kan het onderwerp van de inhoud wijzigen of alle inhoud van XML invoeren.
* **Actie**: de resulterende inhoud kan worden opgeslagen of gegenereerd.

   ![](assets/content_mgmt_edit.png)

   Raadpleeg deze [sectie](../../delivery/using/about-content-management.md)voor meer informatie over het configureren en gebruiken van inhoudsbeheer in Adobe Campaign.

1. **Inhoud**

   * **[!UICONTROL Specified in the transition]**

      Met deze optie kunt u de inhoud gebruiken die is opgegeven in de overgang, dat wil zeggen de gebeurtenis die inhoudsbeheer activeert, moet een **[!UICONTROL contentId]** variabele bevatten. Deze variabele kan door een vorig inhoudsbeheer of door om het even welk manuscript zijn geplaatst.

   * **[!UICONTROL Explicit]**

      Met deze optie kunt u inhoud selecteren die al is gemaakt via het **[!UICONTROL Content]** veld. Dit veld is alleen zichtbaar wanneer de **[!UICONTROL Explicit]** optie is geselecteerd.

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      De inhoud-id wordt berekend door een script. In het **[!UICONTROL Script]** veld kunt u een JavaScript-sjabloon definiëren waarmee de id (primaire sleutel) van de inhoud wordt geëvalueerd. Dit veld is alleen zichtbaar wanneer de **[!UICONTROL Calculated by a script]** optie is geselecteerd.

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      Hiermee maakt u nieuwe inhoud op basis van een publicatiesjabloon. Deze nieuwe inhoud wordt opgeslagen in het bestand dat in het **[!UICONTROL String]** veld is opgegeven. In het **[!UICONTROL Template]** veld wordt de publicatiesjabloon opgegeven die moet worden gebruikt om de inhoud te maken.

      ![](assets/content_mgmt_new.png)

1. **Inhoud bijwerken**

   * **[!UICONTROL Subject]**

      In dit veld kunt u het onderwerp van de inhoud wijzigen.

   * **[!UICONTROL Access to data from an XML feed]**

      Met deze optie kunt u de inhoud samenstellen op basis van een XML-document dat via een XSL-stijlpagina is gedownload. Wanneer deze optie is geselecteerd, geeft het **[!UICONTROL URL]** veld de URL op voor het downloaden van XML-inhoud. Met **[!UICONTROL XSL stylesheet]** deze optie kunt u de stijlpagina opgeven die moet worden gebruikt om het gedownloade XML-document te transformeren. Deze eigenschap is optioneel.

      ![](assets/content_mgmt_xmlcontent.png)

1. **Uit te voeren handeling**

   * **[!UICONTROL Save]**

      Met deze optie slaat u de gemaakte of gewijzigde inhoud op.

      De uitgaande overgang wordt slechts eenmaal geactiveerd, waarbij de inhoud als parameter in de **[!UICONTROL contentId]** variabele wordt opgeslagen.

   * **[!UICONTROL Generate]**

      Met deze optie slaat u de inhoud op en genereert u vervolgens de uitvoerbestanden voor elke transformatiesjabloon met een publicatie van het type &#39;Bestand&#39;.

      ![](assets/content_mgmt_generate.png)

      De uitgaande overgang wordt geactiveerd voor elk bestand dat wordt gegenereerd met de id van de inhoud die als parameter in de **[!UICONTROL contentId]** variabele wordt opgeslagen en de bestandsnaam in de **[!UICONTROL filename]** variabele.

## Invoerparameters {#input-parameters}

* contentId

Identifier van de inhoud die moet worden gebruikt als de **[!UICONTROL Specified in the transition]** optie is ingeschakeld.

## Uitvoerparameters {#output-parameters}

* contentId

   Inhoud-id.

* filename

   Volledige naam van het gegenereerde bestand als de geselecteerde actie **[!UICONTROL Generate]** is.

## Voorbeelden {#examples}

In deze [sectie](../../delivery/using/automating-via-workflows.md#examples)worden voorbeelden gegeven.
