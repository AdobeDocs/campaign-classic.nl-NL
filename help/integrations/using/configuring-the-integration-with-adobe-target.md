---
title: Integratie met Adobe Target configureren
seo-title: Integratie met Adobe Target configureren
description: Integratie met Adobe Target configureren
seo-description: null
page-status-flag: never-activated
uuid: b9337e92-e4e5-4cba-a559-75db7460d5c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 378d5ff9-88c0-43f1-beb8-454701e9f1d1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Configuring the integration with Adobe Target{#configuring-the-integration-with-adobe-target}

## Vereisten {#prerequisites}

Om de integratie tussen Adobe Campaign en Adobe Target te kunnen gebruiken, moet u beschikken over:

* Adobe Experience Cloud- en Adobe Target-organisaties
* Een Adobe Target-vak opgegeven voor het tot stand brengen van de verbinding met Adobe Campaign

## Adobe Campaign configureren {#configuring-adobe-campaign}

Adobe Campaign configureren:

1. Installeer het **[!UICONTROL Integration with the Adobe Experience Cloud]** standaardpakket. Het installeren van een integratiepakket is hetzelfde als het installeren van een standaardpakket, dat wordt beschreven in de sectie [Pakket importeren](../../platform/using/working-with-data-packages.md#importing-packages) . Zo hebt u via Digital Asset Manager toegang tot de gedeelde elementen.
1. Schakel verbinding via IMS (Adobe ID-verbindingsservice) in om afbeeldingen te gebruiken die via Adobe Experience Cloud worden gedeeld in uw e-mails. Raadpleeg de sectie over [IMS](../../integrations/using/about-adobe-id.md).
1. In **[!UICONTROL Administration > Platform > Options]**, vorm de server en organisatie (HTENT) opties voor Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]** : Adobe Target-server gebruikt voor integratie. Deze optie is standaard al geselecteerd. Deze waarde komt overeen met de Adobe Target **[!UICONTROL Domain Server]**, gevolgd door de waarde **/m2**. Bijvoorbeeld: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Naam van Adobe Target-organisatie. Deze waarde komt overeen met de naam van de Adobe Target **[!UICONTROL Client]**.

   ![](assets/tar_options.png)

