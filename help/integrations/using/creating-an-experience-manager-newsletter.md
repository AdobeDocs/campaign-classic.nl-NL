---
product: campaign
title: Een nieuwsbrief voor Experience Managers maken
description: Een nieuwsbrief voor Experience Managers maken
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 1%

---

# Een nieuwsbrief voor Experience Managers maken{#creating-an-experience-manager-newsletter}

![](../../assets/common.svg)

Deze integratie kan bijvoorbeeld worden gebruikt voor het maken van een nieuwsbrief in Adobe Experience Manager die vervolgens in Adobe Campaign wordt gebruikt als onderdeel van een e-mailcampagne.

Raadpleeg dit voor een meer gedetailleerd voorbeeld van het gebruik van deze integratie [stapsgewijze handleiding](https://helpx.adobe.com/campaign/kb/acc-aem.html).

**Uit Adobe Experience Manager:**

1. Klik in de AEM instantie van de auteur op de knop **Adobe Experience** logo in de linkerbovenhoek van de pagina en selecteer **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Selecteer **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**.
1. Klik op de knop **[!UICONTROL Create]** in de rechterbovenhoek van de pagina en selecteer vervolgens **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Selecteer **[!UICONTROL Adobe Campaign Email (AC 6.1)]** sjabloon en naam van nieuwsbrief.
1. Als uw pagina is gemaakt, opent u de **[!UICONTROL Page information]** menu en klik op **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. In de **[!UICONTROL Cloud Services]** tab, selecteert u **[!UICONTROL Adobe Campaign]** als **[!UICONTROL Cloud service configuration]** en uw Adobe Campaign-exemplaar in de tweede vervolgkeuzelijst.

   ![](assets/aem_uc_4.png)

1. Bewerk uw e-mailinhoud door onderdelen toe te voegen, zoals personalisatievelden uit Adobe Campaign.
1. Als uw e-mail gereed is, opent u de **[!UICONTROL Page information]** menu en klik op **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. Selecteer in de eerste vervolgkeuzelijst de optie **[!UICONTROL Publish to Adobe Campaign]** als workflowmodel en klik op **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Start vervolgens, als de vorige stap, de **[!UICONTROL Approve for Campaign]** workflow.
1. Boven op de pagina wordt een disclaimer weergegeven. Klikken **[!UICONTROL Complete]** om de revisie te bevestigen en klik op **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Klik nogmaals **[!UICONTROL Complete]** en selecteert u **[!UICONTROL Newsletter approval]** in de **[!UICONTROL Next Step]** vervolgkeuzelijst.

   ![](assets/aem_uc_8.png)

Uw nieuwsbrief is nu klaar en gesynchroniseerd in Adobe Campaign.

**Uit Adobe Campaign:**

1. Van de **[!UICONTROL Campaigns]** tabblad, klikt u op **[!UICONTROL Deliveries]** dan **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. In de **[!UICONTROL Delivery template]** vervolgkeuzelijst, selecteert u de **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** sjabloon.

   ![](assets/aem_uc_10.png)

1. Voeg een **[!UICONTROL Label]** aan uw levering en klik op **[!UICONTROL Continue]**.
1. Klik op de knop **[!UICONTROL Synchronize]**.

   Als deze knop niet in uw interface wordt weergegeven, klikt u op de knop **[!UICONTROL Properties]** en selecteert u de **[!UICONTROL Advanced]** tab. De **[!UICONTROL Content editing mode]** veld moet worden ingesteld op **[!UICONTROL AEM]** met uw AEM in de **[!UICONTROL AEM account]** veld.

   ![](assets/aem_uc_11.png)

1. Selecteer de levering die eerder in Adobe Experience Manager is gemaakt en klik op **[!UICONTROL Ok]**.
1. Klik op de knop **[!UICONTROL Refresh content]** zodra er wijzigingen in de AEM zijn aangebracht.

   ![](assets/aem_uc_12.png)

Uw e-mail kan nu naar uw publiek worden verzonden.
