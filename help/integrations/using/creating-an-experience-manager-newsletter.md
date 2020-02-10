---
title: Een nieuwsbrief voor Experience Manager maken
seo-title: Een nieuwsbrief voor Experience Manager maken
description: Een nieuwsbrief voor Experience Manager maken
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Een nieuwsbrief voor Experience Manager maken{#creating-an-experience-manager-newsletter}

Deze integratie kan bijvoorbeeld worden gebruikt om een nieuwsbrief te maken in Adobe Experience Manager die vervolgens in Adobe Campaign wordt gebruikt als onderdeel van een e-mailcampagne.

Raadpleeg deze [stapsgewijze handleiding](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/aem.html)voor een meer gedetailleerd voorbeeld van het gebruik van deze integratie.

**Vanuit Adobe Experience Manager:**

1. Klik in uw exemplaar van de AEM-auteur op het **Adobe Experience** -logo linksboven op de pagina en selecteer **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Selecteer **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Master Area > Email campaigns]**.
1. Klik op de **[!UICONTROL Create]** knop rechtsboven op de pagina en selecteer **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Selecteer de **[!UICONTROL Adobe Campaign Email (AC 6.1)]** sjabloon en geef de nieuwsbrief een naam.
1. Nadat de pagina is gemaakt, opent u het **[!UICONTROL Page information]** menu en klikt u **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. Selecteer op het **[!UICONTROL Cloud Services]** tabblad de optie **[!UICONTROL Adobe Campaign]** Als **[!UICONTROL Cloud service configuration]** en uw Adobe Campagne-instantie in de tweede vervolgkeuzelijst.

   ![](assets/aem_uc_4.png)

1. Bewerk uw e-mailinhoud door onderdelen toe te voegen, zoals personalisatievelden uit Adobe Campagne.
1. Als uw e-mail gereed is, opent u het **[!UICONTROL Page information]** menu en klikt u **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. Selecteer in de eerste keuzelijst het workflowmodel en klik op **[!UICONTROL Publish to Adobe Campaign]** **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Start vervolgens de **[!UICONTROL Approve for Campaign]** workflow als de vorige stap.
1. Boven op de pagina wordt een disclaimer weergegeven. Klik **[!UICONTROL Complete]** om de revisie te bevestigen en klik op **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Klik nogmaals **[!UICONTROL Complete]** en selecteer **[!UICONTROL Newsletter approval]** in de **[!UICONTROL Next Step]** vervolgkeuzelijst.

   ![](assets/aem_uc_8.png)

Uw nieuwsbrief is nu klaar en gesynchroniseerd in de Campagne van Adobe.

**Van Adobe-campagne:**

1. Klik op het **[!UICONTROL Campaigns]** tabblad **[!UICONTROL Deliveries]** vervolgens **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. Selecteer de **[!UICONTROL Delivery template]** sjabloon in de **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** vervolgkeuzelijst.

   ![](assets/aem_uc_10.png)

1. Voeg een **[!UICONTROL Label]** object toe aan uw levering en klik op **[!UICONTROL Continue]**.
1. Klik op de **[!UICONTROL Synchronize]** knop.

   Als deze knoop niet in uw interface verschijnt, klik de **[!UICONTROL Properties]** knoop en selecteer het **[!UICONTROL Advanced]** lusje. Het **[!UICONTROL Content editing mode]** veld moet worden ingesteld op **[!UICONTROL AEM]** uw AEM-instantie in het **[!UICONTROL AEM account]** veld.

   ![](assets/aem_uc_11.png)

1. Selecteer de levering die u eerder hebt gemaakt in Adobe Experience Manager en klik op **[!UICONTROL Ok]**.
1. Klik op de **[!UICONTROL Refresh content]** knop zodra er wijzigingen zijn aangebracht in uw AEM-levering.

   ![](assets/aem_uc_12.png)

Uw e-mail kan nu naar uw publiek worden verzonden.
