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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Integratie met Adobe Target configureren{#configuring-the-integration-with-adobe-target}

## Vereisten {#prerequisites}

Als u de integratie tussen Adobe Campaign en Adobe Target wilt gebruiken, moet u beschikken over:

* Adobe Experience Cloud- en Adobe Target-organisaties
* Een Adobe Target-rawbox die is opgegeven om de verbinding met Adobe Campagne tot stand te brengen

## Adobe-campagne configureren {#configuring-adobe-campaign}

Adobe-campagne configureren:

1. Installeer het **[!UICONTROL Integration with the Adobe Experience Cloud]** standaardpakket. Het installeren van een integratiepakket is hetzelfde als het installeren van een standaardpakket, dat wordt beschreven in de sectie [Pakket importeren](../../platform/using/working-with-data-packages.md#importing-packages) . Zo hebt u via Digital Asset Manager toegang tot de gedeelde elementen.
1. Schakel verbinding via IMS (Adobe-id-verbindingsservice) in om afbeeldingen te gebruiken die via Adobe Experience Cloud worden gedeeld in uw e-mails. Raadpleeg de sectie over [IMS](../../integrations/using/about-adobe-id.md).
1. Configureer in **[!UICONTROL Administration > Platform > Options]** Adobe Target de server- en organisatieopties (Tenant):

   * **[!UICONTROL TNT_EdgeServer]** : Adobe Target-server gebruikt voor de integratie. Deze optie is standaard al geselecteerd. Deze waarde komt overeen met Adobe Target **[!UICONTROL Domain Server]**, gevolgd door de waarde **/m2**. Bijvoorbeeld: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Naam van Adobe Target-organisatie. Deze waarde komt overeen met de naam van Adobe Target **[!UICONTROL Client]**.
   ![](assets/tar_options.png)

