---
title: Gedeeld element invoegen
seo-title: Gedeeld element invoegen
description: Gedeeld element invoegen
seo-description: null
page-status-flag: never-activated
uuid: ab661bfd-d0a3-4b5c-ba52-4c76c834d584
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: 3d01cc7e-5685-4101-bf4b-ef5f6e52b3c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Gedeeld element invoegen{#inserting-a-shared-asset}

Middelen die worden gedeeld via Adobe Experience Cloud kunnen als volgt worden gebruikt in uw e-mails en landingspagina&#39;s:

1. Maak een nieuwe e-mail of een nieuwe bestemmingspagina.

   Als u middelen uit de bibliotheek met Adobe Experience Manager gebruikt, gebruikt u een leveringssjabloon die bij het [configureren van de integratie](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets)is gemaakt.

   Als u dit specifieke malplaatje niet hebt, zorg ervoor dat in de levering **Eigenschappen**, **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** lusje) aan **DCE** wordt geplaatst en dat de externe rekening AEM die u voor de toegang tot van uw AEM middelbibliotheek van Middelen wilt gebruiken wordt verstrekt.

1. Selecteer in het bewerkingsvenster de optie om een afbeelding toe te voegen:

   * Als u de [standaardbewerkingsmodus](../../delivery/using/defining-the-email-content.md#adding-images)gebruikt, selecteert u **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_standard.png)

   * Als u de [geavanceerde bewerkingsmodus](../../web/using/about-campaign-html-editor.md) (DCE) gebruikt, gaat u naar een afbeeldingsblok en selecteert u vervolgens via het contextmenu **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >U kunt geen gedeelde afbeeldingen vanuit Adobe Campagne invoegen in [webtoegang](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) wanneer u de DCE gebruikt.

1. Selecteer in het selectievenster dat wordt geopend een afbeelding en bevestig deze vervolgens.

   De beschikbare afbeeldingen zijn afkomstig uit uw Adobe Experience Cloud-bibliotheek of de AEM Assets-bibliotheek, afhankelijk van de configuratie van uw Adobe Campagne-instantie. Raadpleeg de sectie Toegang [tot middelen](../../integrations/using/configuring-access-to-assets.md) configureren.

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Als u de integratie met Adobe Target gebruikt, kunt u een gedeelde afbeelding als standaardafbeelding gebruiken. Zie [deze pagina](../../integrations/using/integrating-with-adobe-target.md).

