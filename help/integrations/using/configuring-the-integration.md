---
title: Integratie configureren
seo-title: Integratie configureren
description: Integratie configureren
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Integratie configureren{#configuring-the-integration}

## Configureren in Adobe-campagne {#configuring-in-adobe-campaign}

Om deze twee oplossingen samen te gebruiken, moet u hen vormen om met elkaar te verbinden.

Voer de onderstaande stappen uit om de configuratie in Adobe Campaign te starten:

1. [Het AEM-integratiepakket installeren in Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [De externe account configureren](#configure-the-external-account)
1. [Filteren van AEM-bronnen configureren](#configure-aem-resources-filtering)

Voor geavanceerde configuraties zoals het beheren van verpersoonlijkingsgebieden en blokken. Raadpleeg de [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html)van Adobe Experience Manager.

### Het AEM-integratiepakket installeren in Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

U moet eerst het **[!UICONTROL AEM integration]** pakket installeren.

1. Kies een optie in de bovenste werkbalk van de Adobe Campagne-instantie. **[!UICONTROL Tools]**
1. Selecteer **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Selecteer **[!UICONTROL Install a standard package]**.
1. Schakel **[!UICONTROL AEM integration]** vervolgens in en klik op de **[!UICONTROL Next]** knop.

   ![](assets/aem_config_2.png)

1. Klik in het volgende venster op de **[!UICONTROL Start]** knop om de installatie van het pakket te starten. Sluit het venster als de installatie is voltooid.

### De beveiligingszone voor de AEM-operator configureren {#configure-the-security-zone-for-aem-operator}

Het **[!UICONTROL AEM integration]** pakket stelt de **[!UICONTROL aemserver]** operator in Campaign in. Deze operator wordt gebruikt om de Adobe Experience Manager-server te verbinden met Adobe Campaign.

U moet een beveiligingszone configureren voor deze operator om verbinding te maken met Adobe Campaign via Adobe Experience Manager.

>[!CAUTION]
>
>We raden u ten zeerste aan een beveiligingszone voor AEM te maken om beveiligingsproblemen te voorkomen. Raadpleeg voor meer informatie de [installatiegids](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Neem contact op met het ondersteuningsteam van Adobe als uw Campagne-instantie wordt gehost door Adobe. Voer de onderstaande stappen uit als u campagne op locatie gebruikt:

1. Open het configuratiebestand **serverConf.xml** .
1. Open het **allowUserPassword** -kenmerk van de geselecteerde beveiligingszone en stel dit in op **true**.

   Hierdoor kan Adobe Experience Manager verbinding maken met Adobe Campaign via aanmelden/wachtwoord.

### De externe account configureren {#configure-the-external-account}

Het **[!UICONTROL AEM integration]** pakket heeft de externe account voor Adobe Experience Cloud gemaakt. U moet deze nu configureren om verbinding te maken met uw Adobe Experience Manager-exemplaar.

Voer de volgende stappen uit om de externe AEM-account te configureren:

1. Klik op de **[!UICONTROL Explorer]** knop.

   ![](assets/aem_config_3.png)

1. Selecteer **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecteer in de **[!UICONTROL External account]** lijst de optie **[!UICONTROL AEM instance]**.
1. Voer de parameters in voor uw AEM-ontwerpinstantie:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**
   >[!NOTE]
   >
   >Zorg ervoor dat het **[!UICONTROL Server]** adres niet eindigt met een slash.

   ![](assets/aem_config_4.png)

1. Schakel het **[!UICONTROL Enabled]** selectievakje in.
1. Klik op de **[!UICONTROL Save]** knop.

### Filteren van AEM-bronnen configureren {#configure-aem-resources-filtering}

De optie **AEMResourceTypeFilter **wordt gebruikt om typen bronnen van de Manager van de Ervaring te filtreren die in de Campagne van Adobe kunnen worden gebruikt. Op deze manier kan Adobe Campaign Experience Manager-inhoud ophalen die speciaal is ontworpen om alleen in Adobe Campaign te worden gebruikt.

Controleren of de **[!UICONTROL AEMResourceTypeFilter]** optie is geconfigureerd:

1. Klik op de **[!UICONTROL Explorer]** knop.
1. Selecteer **[!UICONTROL Administration > Platform > Options]**.
1. Selecteer in de **[!UICONTROL Options]** lijst de optie **[!UICONTROL AEMResourceTypeFilter]**.
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

Voer de onderstaande stappen uit om de configuratie te starten in Adobe Experience Manager:

1. Configureer de **replicatie** om van de AEM-ontwerpinstantie naar de AEM-publicatieinstantie te repliceren.

   Raadpleeg de [documentatie](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/replication.html)van Adobe Experience Manager voor meer informatie over het configureren van replicatie.

1. Installeer de integratie **FeaturePack** op uw auteursinstantie dan repliceer de installatie op uw het publiceren instantie. (Alleen voor AEM-versies 5.6.1 en 6.0).

   Raadpleeg de [documentatie](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)van Adobe Experience Manager voor meer informatie over het installeren van FeaturePack.

1. Sluit Adobe Experience Manager aan op Adobe Campagne door een speciale **Cloud Service** te configureren.

   Raadpleeg de [documentatie](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) van Adobe Experience Manager voor informatie over het tot stand brengen van een verbinding tussen beide oplossingen via Cloud Services.

1. Configureer de **Externalzer-service**.

   Raadpleeg de [documentatie](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/externalizer.html)van Adobe Experience Manager voor meer informatie over het configureren ervan.

