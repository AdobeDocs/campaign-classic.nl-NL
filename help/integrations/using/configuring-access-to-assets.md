---
product: campaign
title: Toegang tot elementen configureren
description: Toegang tot elementen configureren
feature: Asset Sharing
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Toegang tot elementen configureren {#configuring-access-to-assets}

In deze sectie worden de benodigde configuratiestappen in Adobe Campaign beschreven voor het gebruik van de integratiefuncties met Assets of Adobe Experience Manager Assets (AEM Assets)-bibliotheek.

>[!CAUTION]
>
>Deze integraties zijn gelijktijdig. Lees de volgende informatie zorgvuldig door voordat u een configuratie maakt.

* Integratie met **Experience Cloud-elementen**: Dankzij deze integratie kunt u afbeeldingen uit uw Adobe Experience Cloud-bibliotheek invoegen. Deze integratie moet worden ingesteld door de installatie van de **[!UICONTROL Integration with the Adobe Experience Cloud]** ingebouwd pakket in Adobe Campaign.
* Integratie met **AEM Assets**: Dankzij deze integratie kunt u afbeeldingen uit uw Adobe Experience Manager Assets-bibliotheek invoegen. Deze integratie moet worden ingesteld door de installatie van de **[!UICONTROL AEM Integration]** ingebouwd pakket in Adobe Campaign. Deze integratie is vanaf Adobe Experience Manager 6.4 niet meer beschikbaar.

>[!NOTE]
>
>Indien de twee pakketten (**[!UICONTROL AEM Integration]** en **[!UICONTROL Integration with the Adobe Experience Cloud]** ) zijn geïnstalleerd, kunnen alleen de elementen die beschikbaar zijn in de Adobe Experience Cloud-bibliotheek worden gebruikt.

## Integreren met Experiencen Cloud {#integrating-with-experience-cloud-assets}

Als u de integratie tussen Adobe Campaign en Experience Cloud Assets wilt gebruiken, moet u beschikken over:

* Een Adobe Experience Cloud-organisatie
* De Adobe IMS-verificatiemodus ingeschakeld

Als u de verbinding tussen Adobe Campaign en Adobe Experience Cloud wilt inschakelen, configureert u de verbinding via IMS (Adobe ID-verbindingsservice). Deze configuratie wordt in het gedeelte [Verbinding maken via een Adobe ID](../../integrations/using/about-adobe-id.md) document. Het gaat om:

* De installatie van de **[!UICONTROL Integration with the Adobe Experience Cloud]** pakket.
* Een externe Adobe Experience Cloud-account configureren.

>[!NOTE]
>
>De functies die met deze integratie samenhangen, zijn alleen beschikbaar voor gebruikers die via IMS verbonden zijn met hun Adobe ID.

## Integreren met AEM Assets {#integrating-with-aem-assets}


>[!CAUTION]
>
>Deze mogelijkheid is uitgeschakeld, vanaf Adobe Experience Manager 6.4. [Meer informatie](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html#removed-features)

Als u AEM Assets wilt integreren met Adobe Campaign, moet u eerst de integratie tussen Adobe Experience Manager en Adobe Campaign configureren. Voor deze configuratie is voornamelijk het volgende vereist:

* De installatie van de **[!UICONTROL AEM Integration]** ingebouwd pakket
* Een externe account configureren die specifiek is voor Adobe Experience Manager

Leer hoe u Adobe Campaign en Adobe Experience Manager kunt integreren in de [gedetailleerde documentatie](../../integrations/using/about-adobe-experience-manager.md).

Zodra deze integratie is ingesteld, kunt u een nieuwe leveringssjabloon in Adobe Campaign configureren voor het gebruik van de AEM Assets-bibliotheek. Hiervoor voert u de volgende stappen uit:

1. Een nieuwe leveringssjabloon maken - of een bestaande sjabloon dupliceren. Voor meer informatie over leveringssjablonen raadpleegt u [deze pagina](../../delivery/using/about-templates.md).
1. Bewerk de **Eigenschappen** van deze template.
1. In de **[!UICONTROL Advanced]** tabblad, stelt u de **[!UICONTROL Content editing mode]** tot **DCE**.
1. Externe selecteren **[!UICONTROL AEM account]** die u moet gebruiken om toegang te krijgen tot uw AEM Assets-bibliotheek.

   ![](assets/dam_aem_assets1.png)

Wanneer u afbeeldingen invoegt in de inhoud van een levering die op deze sjabloon is gebaseerd, wordt de **[!UICONTROL Select a shared asset]** kunt u vervolgens door afbeeldingen bladeren in de AEM Assets-bibliotheek. Lees meer in [deze sectie](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Als de **[!UICONTROL Integration with the Adobe Experience Cloud]** -pakket is ook geïnstalleerd op uw Adobe Campaign-instantie. U kunt alleen de middelen gebruiken die beschikbaar zijn in de Adobe Experience Cloud-bibliotheek. Als u ook toegang wilt krijgen tot de elementen in uw AEM Assets-bibliotheek, moet u AEM Assets en Adobe Experience Cloud synchroniseren. De middelen in AEM Assets zijn dan ook beschikbaar in de Adobe Experience Cloud-bibliotheek. In dit geval hoeft u geen specifieke leveringssjabloon te maken.
