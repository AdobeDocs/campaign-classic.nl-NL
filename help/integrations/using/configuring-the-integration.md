---
solution: Campaign Classic
product: campaign
title: Adobe Experience Manager-integratie configureren
description: Leer hoe te om campagne-AEM integratie te vormen
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 2%

---


# De integratie configureren{#configuring-the-integration}

## Configureren in Adobe Campaign {#configuring-in-adobe-campaign}

Om deze twee oplossingen samen te gebruiken, moet u hen vormen om met elkaar te verbinden.

Voer de onderstaande stappen uit om de configuratie in Adobe Campaign te starten:

1. [Installeer het AEM integratiepakket in Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [De externe account configureren](#configure-the-external-account)
1. [Filteren van AEM configureren](#configure-aem-resources-filtering)

Voor geavanceerde configuraties zoals het beheren van verpersoonlijkingsgebieden en blokken. Raadpleeg de [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html) van Adobe Experience Manager.

### Installeer het AEM integratiepakket in Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

U moet eerst het **[!UICONTROL AEM integration]** pakket installeren.

1. Selecteer **[!UICONTROL Tools]** in uw Adobe Campaign-exemplaar op de bovenste werkbalk.
1. Selecteer **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Selecteer **[!UICONTROL Install a standard package]**.
1. Schakel **[!UICONTROL AEM integration]** in en klik op de knop **[!UICONTROL Next]**.

   ![](assets/aem_config_2.png)

1. Klik in het volgende venster op de knop **[!UICONTROL Start]** om de installatie van het pakket te starten. Sluit het venster als de installatie is voltooid.

### De beveiligingszone voor AEM operator {#configure-the-security-zone-for-aem-operator} configureren

Met het pakket **[!UICONTROL AEM integration]** wordt de operator **[!UICONTROL aemserver]** in Campagne ingesteld. Deze operator wordt gebruikt om de Adobe Experience Manager-server te verbinden met Adobe Campaign.

U moet een beveiligingszone configureren voor deze operator om verbinding te maken met Adobe Campaign via Adobe Experience Manager.

>[!CAUTION]
>
>We raden u ten zeerste aan een beveiligingszone in te stellen die is gewijd aan AEM om beveiligingsproblemen te voorkomen. Raadpleeg de Installatiehandleiding [a1/> voor meer informatie.](../../installation/using/configuring-campaign-server.md#defining-security-zones)

Als uw instantie van de Campagne door Adobe wordt ontvangen, contacteer [Adobe klantenZorg](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team. Voer de onderstaande stappen uit als u campagne op locatie gebruikt:

1. Open het configuratiebestand **serverConf.xml**.
1. Open het **allowUserPassword** attribuut van de geselecteerde veiligheidsstreek en plaats het aan **true**.

   Hierdoor kan Adobe Experience Manager verbinding maken met Adobe Campaign via aanmelding/wachtwoord.

### De externe account {#configure-the-external-account} configureren

Met het **[!UICONTROL AEM integration]**-pakket is de externe account voor Adobe Experience Cloud gemaakt. U moet het nu configureren om verbinding te maken met uw Adobe Experience Manager-instantie.

Voer de volgende stappen uit om de AEM externe account te configureren:

1. Klik op de knop **[!UICONTROL Explorer]**.

   ![](assets/aem_config_3.png)

1. Selecteer **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecteer **[!UICONTROL AEM instance]** in de lijst **[!UICONTROL External account]**.
1. Voer de parameters in voor de AEM ontwerpinstantie:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >Zorg ervoor dat uw **[!UICONTROL Server]** adres niet met een het slepen schuine streep beëindigt.

   ![](assets/aem_config_4.png)

1. Schakel het selectievakje **[!UICONTROL Enabled]** in.
1. Klik op de knop **[!UICONTROL Save]**.

### Filteren van AEM bronnen {#configure-aem-resources-filtering} configureren

De optie **AEMResourceTypeFilter** wordt gebruikt om typen bronnen van de Experience Manager te filteren die in Adobe Campaign kunnen worden gebruikt. Op deze manier kan Adobe Campaign inhoud van Experience Managers ophalen die specifiek is ontworpen voor gebruik in alleen Adobe Campaign.

Om te controleren of wordt de optie **[!UICONTROL AEMResourceTypeFilter]** gevormd:

1. Klik op de knop **[!UICONTROL Explorer]**.
1. Selecteer **[!UICONTROL Administration > Platform > Options]**.
1. Selecteer **[!UICONTROL AEMResourceTypeFilter]** in de lijst **[!UICONTROL Options]**.
1. In het veld **[!UICONTROL Value (text)]** moet het pad als volgt zijn:

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

1. Configureer de **replicatie** om van de AEM ontwerpinstantie naar de AEM publicatieinstantie te repliceren.

   Meer informatie over het configureren van replicatie vindt u in Adobe Experience Manager [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html).

1. Installeer de integratie **FeaturePack** op uw auteursinstantie dan repliceer de installatie op uw het publiceren instantie. (Alleen voor AEM versies 5.6.1 en 6.0).

   Raadpleeg de documentatie bij Adobe Experience Manager [voor meer informatie over het installeren van FeaturePack.](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)

1. Verbind Adobe Experience Manager met Adobe Campaign door een specifieke **Cloud Service** te vormen.

   Raadpleeg de Adobe Experience Manager [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) voor informatie over het verbinden van beide oplossingen via Cloud Services.

1. Configureer de **Externalzer-service**.

   Raadpleeg de documentatie [van Adobe Experience Manager voor meer informatie over het configureren van de documentatie.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)

