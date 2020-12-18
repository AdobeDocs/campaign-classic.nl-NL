---
solution: Campaign Classic
product: campaign
title: Integratie van gedeelde soorten publiek configureren in Adobe Campaign
description: Leer hoe u integratie met gedeelde soorten publiek configureert
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 2%

---


# Integratie van gedeelde soorten publiek configureren in Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

Zodra u dit verzoek hebt voorgelegd, zal Adobe aan de levering van de integratie voor u te werk gaan en u contacteren om details en informatie te verstrekken die u de configuratie moet voltooien:

1. [Stap 1: Externe accounts in Adobe Campaign configureren of controleren](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Stap 2: De gegevensbron configureren](#step-2--configure-the-data-source)
1. [Stap 3: Campagne bijhouden-server configureren](#step-3--configure-campaign-tracking-server)
1. [Stap 4: De service voor de bezoekersidentiteitskaart configureren](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>Als u het demdex-domein gebruikt en de syntaxis **ftp-out.demdex.com** voor de externe account van de import en **ftp-in.demdex.com** voor de externe account van de export volgt, moet u uw implementatie dienovereenkomstig aanpassen en overschakelen naar de connector van de Amazon Simple Storage Service (S3) om gegevens te importeren of exporteren. Voor meer informatie over hoe te om uw externe rekeningen met Amazon S3 te vormen, verwijs naar dit [sectie](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign).

## Stap 1: Externe accounts in Adobe Campaign configureren of controleren{#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Ten eerste moeten we de externe accounts in Adobe Campaign als volgt configureren of controleren:

1. Klik op het pictogram **[!UICONTROL Explorer]**.
1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**. De vermelde SFTP-rekeningen hadden door Adobe moeten zijn geconfigureerd en de benodigde informatie had aan u moeten worden meegedeeld.

   * **[!UICONTROL importSharedAudience]**: account voor het importeren van publiek.
   * **[!UICONTROL exportSharedAudience]**: account gewijd aan het exportpubliek.

   ![](assets/aam_config_1.png)

1. Selecteer de externe account **[!UICONTROL Export audiences to the Adobe Marketing Cloud]**.

1. Selecteer **[!UICONTROL AWS S3]** in de vervolgkeuzelijst **[!UICONTROL Type]**.

1. Geef de volgende gegevens op:

   * **[!UICONTROL AWS S3 Account Server]**
URL van uw server, zou het als volgt moeten worden gevuld:

      ```
      <S3bucket name>.s3.amazonaws.com/<s3object path>
      ```

   * **[!UICONTROL AWS access key ID]**
Raadpleeg deze  [pagina](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)  om te weten waar u uw AWS-toegangstoets-id kunt vinden.

   * **[!UICONTROL Secret access key to AWS]**
Raadpleeg deze  [pagina](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/) om te weten waar u uw geheime toegangssleutel voor AWS vindt.

   * **[!UICONTROL AWS Region]**
Raadpleeg deze  [pagina](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/) voor meer informatie over het AWS-gebied.
   ![](assets/aam_config_2.png)

1. Klik op **[!UICONTROL Save]** en configureer de externe account **[!UICONTROL Import audiences from the Adobe Marketing Cloud]** zoals in de vorige stappen wordt beschreven.

Uw externe accounts zijn nu geconfigureerd.

## Stap 2: De gegevensbron {#step-2--configure-the-data-source} configureren

De **Ontvanger - Bezoeker ID** wordt binnen de Audience Manager gemaakt. Dit is een uit-van-de-doos gegevensbron die door gebrek voor identiteitskaart van de Bezoeker wordt gevormd. Segmenten die zijn gemaakt op basis van campagne maken deel uit van deze gegevensbron.

De **[!UICONTROL Recipient - Visitor ID]**-gegevensbron configureren:

1. Selecteer **[!UICONTROL Administration > Platform > AMC Data sources]** in het knooppunt **[!UICONTROL Explorer]**.
1. Selecteer **[!UICONTROL Recipient - Visitor ID]**.
1. Voer de **[!UICONTROL Data Source ID]** en **[!UICONTROL AAM Destination ID]** in die door Adobe worden opgegeven.

   ![](assets/aam_config_3.png)

## Stap 3: Campagne bijhouden-server {#step-3--configure-campaign-tracking-server} configureren

Voor de configuratie van de integratie met de dienst van de Kern van Mensen of de manager van het Publiek, moeten wij ook de server van het Volgen van de Campagne vormen.

U moet ervoor zorgen de het Volgen van de Campagne Server op het domein (CNAME) wordt geregistreerd. Meer informatie over domeinnaamdelegatie vindt u in [dit artikel](https://helpx.adobe.com/nl/campaign/kb/domain-name-delegation.html).

## Stap 4: De Bezoeker-id-service {#step-4--configure-the-visitor-id-service} configureren

Als uw bezoeker-id-service nog nooit is geconfigureerd op uw wegeigenschappen of websites, raadpleegt u het volgende [document](https://docs.adobe.com/content/help/en/id-service/using/implementation/setup-aam-analytics.html) om te leren hoe u uw service of de volgende [video](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two) kunt configureren.

Uw configuratie en levering worden voltooid, kan de integratie nu worden gebruikt om publiek of segmenten in te voeren en uit te voeren.
