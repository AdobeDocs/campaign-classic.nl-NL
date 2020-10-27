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
source-git-commit: d567cb7dbc55d9c124d1cc83b7a5a9e2dfb5ab61
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 2%

---


# Configuring shared audiences integration in Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

Zodra u dit verzoek hebt voorgelegd, zal Adobe aan de levering van de integratie voor u te werk gaan en u contacteren om details en informatie te verstrekken die u de configuratie moet voltooien:

1. [Stap 1: Externe accounts in Adobe Campaign configureren of controleren](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Stap 2: De gegevensbron configureren](#step-2--configure-the-data-source)
1. [Stap 3: Campagne bijhouden-server configureren](#step-3--configure-campaign-tracking-server)
1. [Stap 4: De service voor de bezoekersidentiteitskaart configureren](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>Als u het demdex-domein gebruikt en de syntaxis **ftp-out.demdex.com** voor de externe account van de import en **ftp-in.demdex.com** voor de externe account van de export volgt, moet u uw implementatie dienovereenkomstig aanpassen en overschakelen naar de connector Amazon Simple Storage Service (S3) voor het importeren of exporteren van gegevens. Raadpleeg deze [sectie](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)voor meer informatie over het configureren van externe accounts met Amazon S3.

## Stap 1: Externe accounts in Adobe Campaign configureren of controleren {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Ten eerste moeten we de externe accounts in Adobe Campaign als volgt configureren of controleren:

1. Klik op het **[!UICONTROL Explorer]** pictogram.
1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**. De vermelde SFTP-rekeningen hadden door Adobe moeten zijn geconfigureerd en de benodigde informatie had aan u moeten worden meegedeeld.

   * **[!UICONTROL importSharedAudience]**: account voor het importeren van publiek.
   * **[!UICONTROL exportSharedAudience]**: account gewijd aan het exportpubliek.

   ![](assets/aam_config_1.png)

1. Select the **[!UICONTROL Export audiences to the Adobe Marketing Cloud]** external account.

1. From the **[!UICONTROL Type]** drop-down, select **[!UICONTROL AWS S3]**.

1. Geef de volgende gegevens op:

   * **[!UICONTROL AWS S3 Account Server]**
URL van uw server, zou het als volgt moeten worden gevuld:

      ```
      <S3bucket name>.s3.amazonaws.com/<s3object path>
      ```

   * **[!UICONTROL AWS access key ID]**
Raadpleeg deze [pagina](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) om te weten waar u uw AWS-toegangstoets-id kunt vinden.

   * **[!UICONTROL Secret access key to AWS]**
Raadpleeg deze [pagina](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/)om te weten waar u uw geheime toegangssleutel voor AWS vindt.

   * **[!UICONTROL AWS Region]**
Raadpleeg deze [pagina](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)voor meer informatie over het AWS-gebied.
   ![](assets/aam_config_2.png)

1. Klik op **[!UICONTROL Save]** en configureer de **[!UICONTROL Import audiences from the Adobe Marketing Cloud]** externe account zoals in de vorige stappen wordt beschreven.

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
