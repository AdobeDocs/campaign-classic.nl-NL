---
product: campaign
title: Toegang tot Assets configureren
description: Toegang tot Assets configureren
feature: Asset Sharing
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 1%

---

# Toegang tot Assets configureren {#configuring-access-to-assets}

In deze sectie worden de benodigde configuratiestappen in Adobe Campaign beschreven voor het gebruik van de integratiefuncties in de Assets- of Adobe Experience Manager Assets-bibliotheek (AEM Assets).

>[!CAUTION]
>
>Deze integraties zijn gelijktijdig. Lees de volgende informatie zorgvuldig door voordat u een configuratie maakt.

* Integratie met **Experience Cloud Assets**: deze integratie staat u toe om beelden van uw bibliotheek van Adobe Experience Cloud op te nemen. Deze integratie moet worden ingesteld door het ingebouwde **[!UICONTROL Integration with the Adobe Experience Cloud]** -pakket in Adobe Campaign te installeren.
* Integratie met **AEM Assets**: deze integratie staat u toe om beelden van uw bibliotheek van Adobe Experience Manager Assets op te nemen. Deze integratie moet worden ingesteld door het ingebouwde **[!UICONTROL AEM Integration]** -pakket in Adobe Campaign te installeren. Deze integratie is vanaf Adobe Experience Manager 6.4 niet meer beschikbaar.

>[!NOTE]
>
>Als de twee pakketten ( **[!UICONTROL AEM Integration]** en **[!UICONTROL Integration with the Adobe Experience Cloud]** ) zijn geïnstalleerd, kunnen alleen de elementen die beschikbaar zijn in de Adobe Experience Cloud-bibliotheek worden gebruikt.

## Integreren met Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Om de integratie tussen Adobe Campaign en Experience Cloud Assets te kunnen gebruiken, moet u beschikken over:

* Een Adobe Experience Cloud-organisatie
* De Adobe IMS-verificatiemodus ingeschakeld

Als u de verbinding tussen Adobe Campaign en Adobe Experience Cloud wilt inschakelen, configureert u de verbinding via IMS (Adobe ID-verbindingsservice). Deze configuratie wordt gedetailleerd in [ het Verbinden via een Adobe ID ](../../integrations/using/about-adobe-id.md) document. Het gaat om:

* Het **[!UICONTROL Integration with the Adobe Experience Cloud]** -pakket installeren.
* Een externe Adobe Experience Cloud-account configureren.

>[!NOTE]
>
>De functies die met deze integratie samenhangen, zijn alleen beschikbaar voor gebruikers die via IMS verbonden zijn met hun Adobe ID.

## Integreren met AEM Assets {#integrating-with-aem-assets}


>[!CAUTION]
>
>Dit vermogen is ontmanteld, die van Adobe Experience Manager 6.4 beginnen. [ leer meer ](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html#removed-features)

Als u AEM Assets wilt integreren met Adobe Campaign, moet u eerst de integratie tussen Adobe Experience Manager en Adobe Campaign configureren. Voor deze configuratie is voornamelijk het volgende vereist:

* Het ingebouwde pakket **[!UICONTROL AEM Integration]** installeren
* Een externe account configureren die specifiek is voor Adobe Experience Manager

Leer hoe te om Adobe Campaign en Adobe Experience Manager in de [ gedetailleerde documentatie ](../../integrations/using/about-adobe-experience-manager.md) te integreren.

Zodra deze integratie is ingesteld, kunt u een nieuwe leveringssjabloon in Adobe Campaign configureren voor het gebruik van de AEM Assets-bibliotheek. Hiervoor voert u de volgende stappen uit:

1. Een nieuwe leveringssjabloon maken - of een bestaande sjabloon dupliceren. Verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html){target="_blank"}.
1. Bewerk de **Eigenschappen** van dit malplaatje.
1. In het **[!UICONTROL Advanced]** lusje, plaats **[!UICONTROL Content editing mode]** aan **DCE**.
1. Selecteer de externe **[!UICONTROL AEM account]** die u nodig hebt voor toegang tot uw AEM Assets-bibliotheek.

   ![](assets/dam_aem_assets1.png)

Wanneer u afbeeldingen invoegt in de inhoud van een levering die op deze sjabloon is gebaseerd, kunt u met de optie **[!UICONTROL Select a shared asset]** door afbeeldingen bladeren in de AEM Assets-bibliotheek. Lees meer in [deze sectie](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Als het **[!UICONTROL Integration with the Adobe Experience Cloud]** -pakket ook op uw Adobe Campaign-instantie is geïnstalleerd, kunt u alleen de elementen gebruiken die beschikbaar zijn in de Adobe Experience Cloud-bibliotheek. Als u ook toegang wilt krijgen tot de elementen in uw AEM Assets-bibliotheek, moet u AEM Assets en Adobe Experience Cloud synchroniseren. De middelen in AEM Assets zijn dan ook beschikbaar in de Adobe Experience Cloud-bibliotheek. In dit geval hoeft u geen specifieke leveringssjabloon te maken.
