---
product: campaign
title: Integratie met Adobe Target configureren
description: Integratie met Adobe Target configureren
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 94e609f3df94c553e2ec84ee427887a767b9af21
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Integratie met Adobe Target configureren{#configuring-the-integration-with-adobe-target}

## Vereisten {#prerequisites}

Om de integratie tussen Adobe Campaign en Adobe Target te kunnen gebruiken, moet u beschikken over:

* Adobe Experience Cloud- en Adobe Target-organisaties
* Een Adobe Target-vak opgegeven voor het tot stand brengen van de verbinding met Adobe Campaign

## Adobe Campaign configureren {#configuring-adobe-campaign}

Adobe Campaign configureren:

1. Installeer het standaardpakket **[!UICONTROL Integration with the Adobe Experience Cloud]**. Het installeren van een integratiepakket is hetzelfde als het installeren van een standaardpakket. Dit wordt beschreven in de sectie [Pakket importeren](../../platform/using/working-with-data-packages.md#importing-packages). Zo hebt u via Digital Asset Manager toegang tot de gedeelde elementen.
1. Schakel verbinding via IMS (Adobe ID-verbindingsservice) in om afbeeldingen te gebruiken die via Adobe Experience Cloud worden gedeeld in uw e-mails. Raadpleeg de sectie over [IMS](../../integrations/using/about-adobe-id.md).
1. Configureer in **[!UICONTROL Administration > Platform > Options]** de server- en organisatie (Tenant)-opties voor Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]** : Adobe Target-server gebruikt voor integratie. Deze optie is standaard al geselecteerd. Deze waarde komt overeen met de Adobe Target **[!UICONTROL Domain Server]**, gevolgd door de waarde **/m2**. Bijvoorbeeld: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Naam van Adobe Target-organisatie. Deze waarde komt overeen met de naam van de Adobe Target **[!UICONTROL Client]**.

   ![](assets/tar_options.png)

>[!CAUTION]
>
>Voor hybride en gehoste architecturen moeten deze opties op alle servers worden ingesteld, inclusief de [mid-sourcing server](../../installation/using/mid-sourcing-server.md) en de [uitvoeringsinstantie](../../message-center/using/configuring-instances.md#execution-instance).