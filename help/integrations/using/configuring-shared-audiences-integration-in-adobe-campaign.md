---
title: Integratie van gedeelde soorten publiek configureren in Adobe Campaign
seo-title: Integratie van gedeelde soorten publiek configureren in Adobe Campaign
description: Integratie van gedeelde soorten publiek configureren in Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: 6ed137e4-027f-4eb0-a0b5-4beb7deef51f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 4443b0ca-80c6-467d-a4df-50864aae8496
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 2%

---


# Configuring shared audiences integration in Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

Zodra u dit verzoek hebt voorgelegd, zal Adobe aan de levering van de integratie voor u te werk gaan en u contacteren om details en informatie te verstrekken die u de configuratie moet voltooien:

1. [Stap 1: Externe accounts in Adobe Campaign configureren of controleren](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Stap 2: De gegevensbron configureren](#step-2--configure-the-data-source)
1. [Stap 3: Campagne bijhouden-server configureren](#step-3--configure-campaign-tracking-server)
1. [Stap 4: De service voor de bezoekersidentiteitskaart configureren](#step-4--configure-the-visitor-id-service)

## Stap 1: Externe accounts in Adobe Campaign configureren of controleren {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Ten eerste moeten we de externe accounts in Adobe Campaign als volgt configureren of controleren:

1. Klik op het **[!UICONTROL Explorer]** pictogram.
1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**. De vermelde SFTP-rekeningen hadden door Adobe moeten zijn geconfigureerd en de benodigde informatie had aan u moeten worden meegedeeld.

   * **[!UICONTROL importSharedAudience]** : SFTP-account voor het importeren van soorten publiek.
   * **[!UICONTROL exportSharedAudience]** : SFTP-account voor het exporteren van soorten publiek.

   ![](assets/aam_config_1.png)

1. Vul het **[!UICONTROL Server]** veld in: **ftp-out.demdex.com** domein voor de invoer externe rekening en **ftp-in.demdex.com** domein voor de uitvoer externe rekening.

   Herinner dat de uitvoer van Campagne de invoer voor de de kerndienst van de Audience Manager of van de Mensen is.

   >[!NOTE]
   >
   >Als u S3 gebruikt, ga uw **[!UICONTROL AWS S3 Account Server]** volgende syntaxis in:
   >
   >`<S3bucket name>.s3.amazonaws.com/<s3object path>`
   >
   >Voor meer informatie over hoe te om uw S3 rekening te vormen, verwijs naar deze [pagina](../../platform/using/external-accounts.md#amazon-simple-storage-service--s3--external-account).

   ![](assets/aam_config_2.png)

1. Voeg de tekst **[!UICONTROL Account]** en **[!UICONTROL Password]** informatie van Adobe toe.

Uw externe accounts zijn nu geconfigureerd.

## Step 2: Configure the Data Source {#step-2--configure-the-data-source}

De **ontvanger - Bezoeker-id** wordt gemaakt in de Audience Manager. Dit is een uit-van-de-doos gegevensbron die door gebrek voor identiteitskaart van de Bezoeker wordt gevormd. Segmenten die zijn gemaakt op basis van campagne maken deel uit van deze gegevensbron.

De **[!UICONTROL Recipient - Visitor ID]** gegevensbron configureren:

1. From the **[!UICONTROL Explorer]** node, select **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. Selecteer **[!UICONTROL Recipient - Visitor ID]**.
1. Voer de tekst in **[!UICONTROL Data Source ID]** en **[!UICONTROL AAM Destination ID]** geef deze op door Adobe.

   ![](assets/aam_config_3.png)

## Stap 3: Campagne bijhouden-server configureren {#step-3--configure-campaign-tracking-server}

Voor de configuratie van de integratie met de dienst van de Kern van Mensen of de manager van het Publiek, moeten wij ook de server van het Volgen van de Campagne vormen.

U moet ervoor zorgen de het Volgen van de Campagne Server op het domein (CNAME) wordt geregistreerd. Meer informatie over domeinnaamdelegatie vindt u in [dit artikel](https://helpx.adobe.com/nl/campaign/kb/domain-name-delegation.html).

## Stap 4: De service voor de bezoekersidentiteitskaart configureren {#step-4--configure-the-visitor-id-service}

Raadpleeg het volgende [document](https://docs.adobe.com/content/help/en/id-service/using/implementation/setup-aam-analytics.html) voor informatie over het configureren van uw service of de volgende [video](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two) als uw bezoeker-id nog nooit is geconfigureerd op uw webeigenschappen of websites.

Uw configuratie en levering worden voltooid, kan de integratie nu worden gebruikt om publiek of segmenten in te voeren en uit te voeren.
