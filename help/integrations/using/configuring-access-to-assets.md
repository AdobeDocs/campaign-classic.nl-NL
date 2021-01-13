---
solution: Campaign Classic
product: campaign
title: Toegang tot elementen configureren
description: Toegang tot elementen configureren
audience: integrations
content-type: reference
topic-tags: asset-sharing
translation-type: tm+mt
source-git-commit: 5d5d4b87bae44ce0a93458f79179434a5bf315c3
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 1%

---


# Toegang tot elementen configureren{#configuring-access-to-assets}

In deze sectie worden de benodigde configuratiestappen in Adobe Campaign beschreven voor het gebruik van de integratiefuncties met de Assets Core-service of de Adobe Experience Manager Assets-bibliotheek.

>[!CAUTION]
>
>Deze integraties zijn gelijktijdig. Lees de volgende informatie zorgvuldig door alvorens om het even welke configuratie te maken.

* Integratie met **Experience Cloud Assets**: Dankzij deze integratie kunt u afbeeldingen uit uw Adobe Experience Cloud-bibliotheek invoegen. Afhankelijk van uw configuratie en licentiemodel kan deze bibliotheek de kernservice Middelen of Middelen op aanvraag zijn. Deze integratie moet worden ingesteld door het ingebouwde **[!UICONTROL Integration with the Adobe Experience Cloud]**-pakket in Adobe Campaign te installeren.
* Integratie met **AEM Assets**: Dankzij deze integratie kunt u afbeeldingen uit uw Adobe Experience Manager-middelenbibliotheek invoegen. Deze integratie moet worden ingesteld door het ingebouwde **[!UICONTROL AEM Integration]**-pakket in Adobe Campaign te installeren.

>[!NOTE]
>
>Als de twee pakketten (**[!UICONTROL AEM Integration]** en **[!UICONTROL Integration with the Adobe Experience Cloud]**) zijn geïnstalleerd, kunnen alleen de elementen worden gebruikt die beschikbaar zijn in de Adobe Experience Cloud-bibliotheek. Als u ook toegang wilt tot de elementen in uw AEM Assets-bibliotheek, moet u AEM Assets en Adobe Experience Cloud synchroniseren. De middelen in AEM Assets zijn dan ook beschikbaar in de Adobe Experience Cloud-bibliotheek. Raadpleeg de [gedetailleerde documentatie](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html) voor meer informatie over het synchroniseren van AEM Assets en Adobe Experience Cloud.

## Integreren met Experience Cloud-elementen {#integrating-with-experience-cloud-assets}

Als u de integratie tussen Adobe Campaign en Experience Cloud Assets wilt gebruiken, moet u beschikken over:

* Een Adobe Experience Cloud-organisatie
* De verificatiemodus Adobe IMS ingeschakeld

Als u de verbinding tussen Adobe Campaign en Adobe Experience Cloud wilt inschakelen, configureert u de verbinding via IMS (Adobe ID-verbindingsservice). Deze configuratie wordt gedetailleerd beschreven in [Verbinding maken via een Adobe ID](../../integrations/using/about-adobe-id.md)-document. Het gaat om:

* Het **[!UICONTROL Integration with the Adobe Experience Cloud]**-pakket installeren.
* Een externe Adobe Experience Cloud-account configureren.

>[!NOTE]
>
>De functies die met deze integratie samenhangen, zijn alleen beschikbaar voor gebruikers die via IMS verbonden zijn met hun Adobe ID.

## Integreren met AEM Assets {#integrating-with-aem-assets}

Als u AEM Assets wilt integreren met Adobe Campaign, moet u eerst de integratie tussen Adobe Experience Manager en Adobe Campaign configureren. Voor deze configuratie is voornamelijk het volgende vereist:

* Het ingebouwde **[!UICONTROL AEM Integration]**-pakket installeren
* Een externe account configureren die specifiek is voor Adobe Experience Manager

Leer hoe u Adobe Campaign en Adobe Experience Manager kunt integreren in de [gedetailleerde documentatie](../../integrations/using/about-adobe-experience-manager.md).

Zodra deze integratie is ingesteld, kunt u een nieuwe leveringssjabloon in Adobe Campaign configureren voor het gebruik van de AEM Assets-bibliotheek. Volg de onderstaande stappen om dit te doen:

1. Een nieuwe leveringssjabloon maken - of een bestaande sjabloon dupliceren. Raadpleeg [deze pagina](../../delivery/using/about-templates.md) voor meer informatie over leveringssjablonen.
1. Bewerk de **Eigenschappen** van deze sjabloon.
1. Stel op het tabblad **[!UICONTROL Advanced]** de **[!UICONTROL Content editing mode]** in op **DCE**.
1. Selecteer de externe **[!UICONTROL AEM account]** die u moet gebruiken om uw AEM Assets-bibliotheek te openen.

   ![](assets/dam_aem_assets1.png)

Wanneer u afbeeldingen invoegt in de inhoud van een levering die op deze sjabloon is gebaseerd, kunt u met de optie **[!UICONTROL Select a shared asset]** bladeren in afbeeldingen in de AEM Assets-bibliotheek. Meer informatie vindt u in [deze sectie](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Als het **[!UICONTROL Integration with the Adobe Experience Cloud]**-pakket ook op uw Adobe Campaign-instantie is geïnstalleerd, kunt u alleen de elementen gebruiken die beschikbaar zijn in de Adobe Experience Cloud-bibliotheek. Als u ook toegang wilt tot de elementen in uw AEM Assets-bibliotheek, moet u AEM Assets en Adobe Experience Cloud synchroniseren. De middelen in AEM Assets zijn dan ook beschikbaar in de Adobe Experience Cloud-bibliotheek. In dit geval hoeft u geen specifieke leveringssjabloon te maken. Raadpleeg de [gedetailleerde documentatie](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/configure-assets-cc-integration.html#integration) voor meer informatie over het synchroniseren tussen AEM Assets en Adobe Experience Cloud.


