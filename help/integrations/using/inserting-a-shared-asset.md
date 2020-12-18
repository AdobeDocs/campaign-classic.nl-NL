---
solution: Campaign Classic
product: campaign
title: Een gedeelde asset invoegen
description: Een gedeelde asset invoegen
audience: integrations
content-type: reference
topic-tags: asset-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---


# Een gedeelde asset invoegen{#inserting-a-shared-asset}

Middelen die door Adobe Experience Cloud worden gedeeld, kunnen als volgt op uw e-mails en landingspagina&#39;s worden gebruikt:

1. Maak een nieuwe e-mail of een nieuwe bestemmingspagina.

   Als u elementen uit de Adobe Experience Manager-elementenbibliotheek gebruikt, gebruikt u een leveringssjabloon die wordt gemaakt bij [het configureren van de integratie](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Als u dit specifieke malplaatje niet hebt, zorg ervoor dat in levering **Eigenschappen**, **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** lusje) aan **DCE** wordt geplaatst en dat de AEM externe rekening die u voor de toegang tot van uw het middelbibliotheek van AEM Assets wilt gebruiken wordt verstrekt.

1. Selecteer in het bewerkingsvenster de optie om een afbeelding toe te voegen:

   * Als u de [standaardbewerkingsmodus](../../delivery/using/defining-the-email-content.md#adding-images) gebruikt, selecteert u **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_standard.png)

   * Als u de [geavanceerde bewerkingsmodus](../../web/using/about-campaign-html-editor.md) (DCE) gebruikt, gaat u naar een afbeeldingsblok en selecteert u **[!UICONTROL Select a shared asset]** via het contextmenu.

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >U kunt geen gedeelde beelden van Adobe Campaign in [Webtoegang ](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) opnemen wanneer het gebruiken van DCE.

1. Selecteer in het selectievenster dat wordt geopend een afbeelding en bevestig deze vervolgens.

   De beschikbare afbeeldingen zijn afkomstig uit uw Adobe Experience Cloud-bibliotheek of uw AEM Assets-bibliotheek, afhankelijk van de configuratie van uw Adobe Campaign-instantie. Raadpleeg de sectie [Toegang tot middelen configureren](../../integrations/using/configuring-access-to-assets.md).

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Als u de integratie met Adobe Target gebruikt, kunt u een gedeelde afbeelding als standaardafbeelding gebruiken. Zie [deze pagina](../../integrations/using/integrating-with-adobe-target.md).

