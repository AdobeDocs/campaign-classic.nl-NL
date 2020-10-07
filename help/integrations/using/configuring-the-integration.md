---
title: De integratie configureren
seo-title: De integratie configureren
description: De integratie configureren
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 4%

---


# De integratie configureren{#configuring-the-integration}

## Configuring in Adobe Campaign {#configuring-in-adobe-campaign}

Om deze twee oplossingen samen te gebruiken, moet u hen vormen om met elkaar te verbinden.

Voer de onderstaande stappen uit om de configuratie in Adobe Campaign te starten:

1. [Installeer het AEM integratiepakket in Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [De externe account configureren](#configure-the-external-account)
1. [Filteren van AEM configureren](#configure-aem-resources-filtering)

Voor geavanceerde configuraties zoals het beheren van verpersoonlijkingsgebieden en blokken. Raadpleeg de Adobe Experience Manager- [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html).

### Installeer het AEM integratiepakket in Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

U moet eerst het **[!UICONTROL AEM integration]** pakket installeren.

1. Selecteer in uw Adobe Campaign-exemplaar **[!UICONTROL Tools]** op de bovenste werkbalk.
1. Selecteer **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Selecteer **[!UICONTROL Install a standard package]**.
1. Schakel **[!UICONTROL AEM integration]** vervolgens in en klik op de **[!UICONTROL Next]** knop.

   ![](assets/aem_config_2.png)

1. Klik in het volgende venster op de **[!UICONTROL Start]** knop om de installatie van het pakket te starten. Sluit het venster als de installatie is voltooid.

### De beveiligingszone voor AEM operator configureren {#configure-the-security-zone-for-aem-operator}

Het **[!UICONTROL AEM integration]** pakket stelt de **[!UICONTROL aemserver]** operator in Campaign in. Deze operator wordt gebruikt om de Adobe Experience Manager-server te verbinden met Adobe Campaign.

U moet een beveiligingszone configureren voor deze operator om verbinding te maken met Adobe Campaign via Adobe Experience Manager.

>[!CAUTION]
>
>We raden u ten zeerste aan een beveiligingszone in te stellen die is gewijd aan AEM om beveiligingsproblemen te voorkomen. For more on this, refer to the Installation [guide](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Als uw instantie van de Campagne door Adobe wordt ontvangen, contacteer het team van de Steun van de Adobe. Voer de onderstaande stappen uit als u campagne op locatie gebruikt:

1. Open het configuratiebestand **serverConf.xml** .
1. Open het **allowUserPassword** -kenmerk van de geselecteerde beveiligingszone en stel dit in op **true**.

   Hierdoor kan Adobe Experience Manager verbinding maken met Adobe Campaign via aanmelding/wachtwoord.

### De externe account configureren {#configure-the-external-account}

Het **[!UICONTROL AEM integration]** pakket heeft de externe account voor Adobe Experience Cloud gemaakt. U moet het nu configureren om verbinding te maken met uw Adobe Experience Manager-instantie.

Voer de volgende stappen uit om de AEM externe account te configureren:

1. Klik op de knop **[!UICONTROL Explorer]**.

   ![](assets/aem_config_3.png)

1. Selecteer **[!UICONTROL Administration > Platform > External accounts]**.
1. From the **[!UICONTROL External account]** list, select **[!UICONTROL AEM instance]**.
1. Voer de parameters in voor de AEM ontwerpinstantie:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >Zorg ervoor dat het **[!UICONTROL Server]** adres niet eindigt met een slash.

   ![](assets/aem_config_4.png)

1. Schakel het **[!UICONTROL Enabled]** selectievakje in.
1. Klik op de knop **[!UICONTROL Save]**.

### Filteren van AEM configureren {#configure-aem-resources-filtering}

De **optie AEMResourceTypeFilter** wordt gebruikt om types van Experience Manager middelen te filtreren die in Adobe Campaign kunnen worden gebruikt. Op deze manier kan Adobe Campaign inhoud van Experience Managers ophalen die specifiek is ontworpen voor gebruik in alleen Adobe Campaign.

Controleren of de **[!UICONTROL AEMResourceTypeFilter]** optie is geconfigureerd:

1. Klik op de knop **[!UICONTROL Explorer]**.
1. Selecteer **[!UICONTROL Administration > Platform > Options]**.
1. From the **[!UICONTROL Options]** list, select **[!UICONTROL AEMResourceTypeFilter]**.
1. In het **[!UICONTROL Value (text)]** veld moet het pad als volgt zijn:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   In sommige gevallen:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Configureren in Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Voer de onderstaande stappen uit om de configuratie in Adobe Experience Manager te starten:

1. Vorm de **replicatie** om van de AEM auteursinstantie aan de AEM het publiceren instantie te herhalen.

   Raadpleeg de Adobe Experience Manager- [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html)voor meer informatie over het configureren van replicatie.

1. Installeer de integratie **FeaturePack** op uw auteursinstantie dan repliceer de installatie op uw het publiceren instantie. (Alleen voor AEM versies 5.6.1 en 6.0).

   Raadpleeg de Adobe Experience Manager- [documentatie](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)voor meer informatie over het installeren van FeaturePack.

1. Verbind Adobe Experience Manager met Adobe Campaign door een specifieke **Cloud Service** te vormen.

   Raadpleeg de Adobe Experience Manager- [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) voor informatie over het tot stand brengen van een verbinding tussen beide oplossingen via Cloud Services.

1. Configureer de **Externalzer-service**.

   Raadpleeg de Adobe Experience Manager- [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)voor meer informatie over het configureren ervan.

