---
product: campaign
title: Een gedeelde asset invoegen
description: Een gedeelde asset invoegen
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# Een gedeelde asset invoegen{#inserting-a-shared-asset}

Middelen die door Adobe Experience Cloud worden gedeeld, kunnen als volgt op uw e-mails en landingspagina&#39;s worden gebruikt:

1. Maak een nieuwe e-mail of een nieuwe bestemmingspagina.

   Als u elementen uit de Adobe Experience Manager-elementenbibliotheek gebruikt, gebruikt u een leveringssjabloon die is gemaakt bij [configureren van integratie](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Als u dit specifieke malplaatje niet hebt, zorg ervoor dat in de levering **Eigenschappen** de **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** tab) is ingesteld op **DCE** en dat de AEM externe account die u wilt gebruiken voor toegang tot uw AEM Assets-bronbibliotheek is opgegeven.

1. Selecteer in het bewerkingsvenster de optie om een afbeelding toe te voegen:

   * Als u het [standaardbewerkingsmodus](../../delivery/using/defining-the-email-content.md#adding-images), selecteert u **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_standard.png)

   * Als u het [geavanceerde bewerkingsmodus](../../web/using/about-campaign-html-editor.md) (DCE), ga naar een afbeeldingsblok en selecteer vervolgens via het contextmenu **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >U kunt geen gedeelde afbeeldingen vanuit Adobe Campaign invoegen in [webtoegang](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) bij gebruik van de DCE.

1. Selecteer in het selectievenster dat wordt geopend een afbeelding en bevestig deze vervolgens.

   De beschikbare afbeeldingen zijn afkomstig uit uw Adobe Experience Cloud-bibliotheek of uw AEM Assets-bibliotheek, afhankelijk van de configuratie van uw Adobe Campaign-instantie. Zie de [Toegang tot elementen configureren](../../integrations/using/configuring-access-to-assets.md) sectie.

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Als u de integratie met Adobe Target gebruikt, kunt u een gedeelde afbeelding als standaardafbeelding gebruiken. Zie [deze pagina](../../integrations/using/integrating-with-adobe-target.md).
