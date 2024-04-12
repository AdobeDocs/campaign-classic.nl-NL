---
product: campaign
title: Integratie met Adobe Target configureren
description: Leer hoe u de integratie met Adobe Target kunt configureren
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 2%

---

# Integratie met Adobe Target configureren{#configuring-the-integration-with-adobe-target}




>[!CAUTION]
>
> Neem als gehoste of hybride klant contact op met uw Adobe om deze integratie te configureren. De onderstaande stappen zijn alleen van toepassing op on-premise klanten.

Deze integratie vereist:

* Adobe Experience Cloud- en Adobe Target-organisaties
* Een Adobe Target-vak opgegeven voor het tot stand brengen van de verbinding met Adobe Campaign

Volg onderstaande stappen om deze integratie in Adobe Campaign te configureren:

1. Installeer de **[!UICONTROL Integration with the Adobe Experience Cloud]** ingebouwd pakket. [Meer informatie](../../platform/using/working-with-data-packages.md#importing-packages)

   Met dit pakket hebt u via Digital Asset Manager toegang tot de gedeelde elementen.

1. Schakel verbinding via IMS (Adobe ID-verbindingsservice) in om afbeeldingen te gebruiken die via Adobe Experience Cloud worden gedeeld in uw e-mails. [Meer informatie](../../integrations/using/about-adobe-id.md)
1. Bladeren naar **[!UICONTROL Administration > Platform > Options]** om de server- en organisatie-opties (Tenant) voor Adobe Target te configureren:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : Adobe Target-server gebruikt voor integratie. Deze optie is standaard al geselecteerd. Deze waarde komt overeen met de Adobe Target **[!UICONTROL Domain Server]**, gevolgd door de waarde **/m2**. Bijvoorbeeld: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : naam van Adobe Target-organisatie. Deze waarde komt overeen met de naam van de Adobe Target **[!UICONTROL Client]**.


>[!CAUTION]
>
>Voor hybride en gehoste architecturen moeten deze opties op alle servers worden ingesteld, inclusief de [server voor midsourcing](../../installation/using/mid-sourcing-server.md) en de [uitvoeringsinstantie](../../message-center/using/configuring-instances.md#execution-instance).