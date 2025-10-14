---
product: campaign
title: Gedeeld element invoegen
description: Gedeeld element invoegen
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 1%

---

# Gedeeld element invoegen{#inserting-a-shared-asset}

Assets dat door Adobe Experience Cloud wordt gedeeld, kan als volgt op uw e-mails en landingspagina&#39;s worden gebruikt:

1. Maak een nieuwe e-mail of een nieuwe bestemmingspagina.

   Als u activa van de activa van Adobe Experience Manager bibliotheek gebruikt, gebruik een levermalplaatje dat wanneer [&#x200B; wordt gecreeerd vormend de integratie &#x200B;](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Als u dit specifieke malplaatje niet hebt, zorg ervoor dat in de levering **Eigenschappen**, **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** lusje) aan **DCE** wordt geplaatst en dat de externe rekening van AEM die u voor de toegang tot van uw het middelbibliotheek van AEM Assets wilt gebruiken wordt verstrekt.

1. Selecteer in het bewerkingsvenster de optie om een afbeelding toe te voegen:

   * Als u de [&#x200B; standaard het uitgeven wijze &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html#adding-images){target="_blank"} gebruikt, uitgezocht **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_standard.png)

   * Als u [&#x200B; geavanceerde het uitgeven wijze &#x200B;](../../web/using/about-campaign-html-editor.md) (DCE) gebruikt, ga naar een beeldblok, dan via het contextafhankelijke menu, uitgezocht **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >U kunt geen gedeelde beelden van Adobe Campaign in [&#x200B; Webtoegang &#x200B;](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) opnemen wanneer het gebruiken van DCE.

1. Selecteer in het selectievenster dat wordt geopend een afbeelding en bevestig deze vervolgens.

   De beschikbare afbeeldingen zijn afkomstig uit uw Adobe Experience Cloud-bibliotheek of uw AEM Assets-bibliotheek, afhankelijk van de configuratie van uw Adobe Campaign-instantie. Verwijs naar [&#x200B; het Vormen toegang tot de sectie van Assets &#x200B;](../../integrations/using/configuring-access-to-assets.md).

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Als u de integratie met Adobe Target gebruikt, kunt u een gedeelde afbeelding als standaardafbeelding gebruiken. Zie [deze pagina](../../integrations/using/integrating-with-adobe-target.md).
