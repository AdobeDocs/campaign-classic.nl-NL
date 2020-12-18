---
solution: Campaign Classic
product: campaign
title: Een nieuwsbrief voor Experience Managers maken
description: Een nieuwsbrief voor Experience Managers maken
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 1%

---


# Een nieuwsbrief voor Experience Managers maken{#creating-an-experience-manager-newsletter}

Deze integratie kan bijvoorbeeld worden gebruikt voor het maken van een nieuwsbrief in Adobe Experience Manager die vervolgens in Adobe Campaign wordt gebruikt als onderdeel van een e-mailcampagne.

Voor een meer gedetailleerd voorbeeld over hoe te om deze integratie te gebruiken, verwijs naar deze [geleidelijke gids](https://helpx.adobe.com/campaign/kb/acc-aem.html).

**Uit Adobe Experience Manager:**

1. Klik in de AEM auteur op het **Adobe Experience**-logo linksboven op de pagina en selecteer **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Selecteer **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**.
1. Klik op de knop **[!UICONTROL Create]** rechtsboven op de pagina en selecteer **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Selecteer de sjabloon **[!UICONTROL Adobe Campaign Email (AC 6.1)]** en geef de nieuwsbrief een naam.
1. Nadat de pagina is gemaakt, opent u het menu **[!UICONTROL Page information]** en klikt u op **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. Selecteer **[!UICONTROL Cloud Services]** op het tabblad &lt;a0/> als **[!UICONTROL Cloud service configuration]** en uw Adobe Campaign-instantie in de tweede vervolgkeuzelijst.**[!UICONTROL Adobe Campaign]**

   ![](assets/aem_uc_4.png)

1. Bewerk uw e-mailinhoud door onderdelen toe te voegen, zoals personalisatievelden uit Adobe Campaign.
1. Als uw e-mail gereed is, opent u het menu **[!UICONTROL Page information]** en klikt u op **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. Selecteer **[!UICONTROL Publish to Adobe Campaign]** als workflowmodel in de eerste vervolgkeuzelijst en klik op **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Start vervolgens de **[!UICONTROL Approve for Campaign]**-workflow als de vorige stap.
1. Boven op de pagina wordt een disclaimer weergegeven. Klik **[!UICONTROL Complete]** om de revisie te bevestigen en **[!UICONTROL Ok]** te klikken.

   ![](assets/aem_uc_7.png)

1. Klik nogmaals **[!UICONTROL Complete]** en selecteer **[!UICONTROL Newsletter approval]** in **[!UICONTROL Next Step]** drop-down.

   ![](assets/aem_uc_8.png)

Uw nieuwsbrief is nu klaar en gesynchroniseerd in Adobe Campaign.

**Uit Adobe Campaign:**

1. Klik op het tabblad **[!UICONTROL Campaigns]** en vervolgens **[!UICONTROL Create]**.**[!UICONTROL Deliveries]**

   ![](assets/aem_uc_9.png)

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Delivery template]** de sjabloon **[!UICONTROL Email delivery with AEM content (mailAEMContent)]**.

   ![](assets/aem_uc_10.png)

1. Voeg een **[!UICONTROL Label]** aan uw levering toe en klik **[!UICONTROL Continue]**.
1. Klik op de knop **[!UICONTROL Synchronize]**.

   Als deze knoop niet in uw interface verschijnt, klik **[!UICONTROL Properties]** knoop en selecteer **[!UICONTROL Advanced]** tabel. Het veld **[!UICONTROL Content editing mode]** moet worden ingesteld op **[!UICONTROL AEM]** met uw AEM-instantie in het veld **[!UICONTROL AEM account]**.

   ![](assets/aem_uc_11.png)

1. Selecteer de levering die eerder in Adobe Experience Manager is gemaakt en klik op **[!UICONTROL Ok]**.
1. Klik op de knop **[!UICONTROL Refresh content]** zodra er wijzigingen in de AEM zijn aangebracht.

   ![](assets/aem_uc_12.png)

Uw e-mail kan nu naar uw publiek worden verzonden.
