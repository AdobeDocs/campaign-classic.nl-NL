---
product: campaign
title: Adobe Experience Manager-integratie configureren
description: Leer hoe te om campagne-AEM integratie te vormen
audience: integrations
content-type: reference
exl-id: 54ee88b2-e646-4fb9-abec-957f0096f15f
source-git-commit: 6c23dadb5b6523e17e242de43a908ca86ed7cc23
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 3%

---

# Integratie van campagne-AEM configureren{#configuring-the-integration}

![](../../assets/common.svg)

## Configuratiestappen in Adobe Campaign {#configuring-in-adobe-campaign}

Om deze twee oplossingen samen te gebruiken, moet u hen vormen om met elkaar te verbinden.

Voer de onderstaande stappen uit om de configuratie in Adobe Campaign te starten:

1. [Installeer het AEM integratiepakket in Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [De externe account configureren](#configure-the-external-account)
1. [Filteren van AEM configureren](#configure-aem-resources-filtering)

Voor geavanceerde configuraties zoals het beheren van verpersoonlijkingsgebieden en blokken. Zie Adobe Experience Manager [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html).

### Installeer het AEM integratiepakket in Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

U moet eerst de **[!UICONTROL AEM integration]** pakket.

1. Selecteer in uw Adobe Campaign-exemplaar de optie **[!UICONTROL Tools]** in de bovenste werkbalk.
1. Selecteer **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Selecteer **[!UICONTROL Install a standard package]**.
1. Controleren **[!UICONTROL AEM integration]** Klik vervolgens op de knop **[!UICONTROL Next]** knop.

   ![](assets/aem_config_2.png)

1. Klik in het volgende venster op de knop **[!UICONTROL Start]** om de installatie van het pakket te starten. Sluit het venster als de installatie is voltooid.

### De beveiligingszone voor AEM operator configureren {#configure-the-security-zone-for-aem-operator}

De **[!UICONTROL AEM integration]** pakket stelt de **[!UICONTROL aemserver]** in Campaign. Deze operator wordt gebruikt om de Adobe Experience Manager-server te verbinden met Adobe Campaign.

U moet een beveiligingszone configureren voor deze operator om verbinding te maken met Adobe Campaign via Adobe Experience Manager.

>[!CAUTION]
>
>We raden u ten zeerste aan een beveiligingszone in te stellen die is gewijd aan AEM om beveiligingsproblemen te voorkomen. Raadpleeg de installatie voor meer informatie [hulplijn](../../installation/using/security-zones.md).

Als uw instantie Campagne door Adobe wordt ontvangen, contacteer [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team. Voer de onderstaande stappen uit als u campagne op locatie gebruikt:

1. Open de **serverConf.xml** configuratiebestand.
1. Toegang krijgen tot **allowUserPassword** kenmerk van de geselecteerde beveiligingszone en stel deze in op **true**.

   Hierdoor kan Adobe Experience Manager verbinding maken met Adobe Campaign via aanmelding/wachtwoord.

### De externe account configureren {#configure-the-external-account}

De **[!UICONTROL AEM integration]** -pakket is gemaakt voor de externe account voor Adobe Experience Cloud. U moet het nu configureren om verbinding te maken met uw Adobe Experience Manager-instantie.

Volg onderstaande stappen om de AEM externe account te configureren:

1. Klik op de knop **[!UICONTROL Explorer]**.

   ![](assets/aem_config_3.png)

1. Selecteer **[!UICONTROL Administration > Platform > External accounts]**.
1. Van de **[!UICONTROL External account]** list, selecteer **[!UICONTROL AEM instance]**.
1. Voer de parameters in voor de AEM ontwerpinstantie:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >Zorg ervoor dat uw **[!UICONTROL Server]** Het adres eindigt niet met een slash.

   ![](assets/aem_config_4.png)

1. Controleer de **[!UICONTROL Enabled]** doos.
1. Klik op de knop **[!UICONTROL Save]**.

### Filteren van AEM configureren {#configure-aem-resources-filtering}

De **AEMResourceTypeFilter** wordt gebruikt om types van Experience Manager middelen te filtreren die in Adobe Campaign kunnen worden gebruikt. Op deze manier kan Adobe Campaign inhoud van Experience Managers ophalen die specifiek is ontworpen voor gebruik in alleen Adobe Campaign.

Om te controleren of de **[!UICONTROL AEMResourceTypeFilter]** Deze optie is geconfigureerd:

1. Klik op de knop **[!UICONTROL Explorer]**.
1. Selecteer **[!UICONTROL Administration > Platform > Options]**.
1. Van de **[!UICONTROL Options]** list, selecteer **[!UICONTROL AEMResourceTypeFilter]**.
1. In de **[!UICONTROL Value (text)]** in het veld moet het pad als volgt zijn:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   In sommige gevallen:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Configuratiestappen in Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Voer de onderstaande stappen uit om de configuratie in Adobe Experience Manager te starten:

1. Configureer de **replicatie** om van de AEM authoring instantie te herhalen naar de AEM publishing-instantie.

   Raadpleeg Adobe Experience Manager voor meer informatie over het configureren van replicatie [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html).

1. De integratie installeren **FeaturePack** op uw ontwerpinstantie dan repliceer de installatie op uw het publiceren instantie. (Alleen voor AEM versies 5.6.1 en 6.0).

   Raadpleeg Adobe Experience Manager voor meer informatie over het installeren van FeaturePack [documentatie](https://helpx.adobe.com/experience-manager/aem-previous-versions.html).

1. Adobe Experience Manager verbinden met Adobe Campaign door een speciale toepassing te configureren **Cloud Service**.

   Raadpleeg Adobe Experience Manager voor meer informatie over het verbinden van beide oplossingen via Cloud Services [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) .

1. Configureer de **ExternalAlizer-service**.

   Raadpleeg Adobe Experience Manager voor meer informatie over het configureren ervan [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html).
