---
product: campaign
title: Integratie van gedeelde soorten publiek configureren in Adobe Campaign
description: Leer hoe u integratie met gedeelde soorten publiek configureert
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: a3e26cff-9609-4d91-8976-9213a30c3fd2
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 3%

---

# Integratie van gedeelde soorten publiek configureren in Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}



Zodra u dit verzoek hebt voorgelegd, zal Adobe aan de levering van de integratie voor u te werk gaan en u contacteren om details en informatie te verstrekken die u de configuratie moet voltooien:

1. [Stap 1: Externe accounts in Adobe Campaign configureren of controleren](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Stap 2: De gegevensbron configureren](#step-2--configure-the-data-source)
1. [Stap 3: Campagne bijhouden-server configureren](#step-3--configure-campaign-tracking-server)
1. [Stap 4: De service voor de bezoekersidentiteitskaart configureren](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>Als u het demdex-domein gebruikt en de syntaxis volgt **ftp-out.demdex.com** voor de externe rekening van de invoer en **ftp-in.demdex.com** voor de externe exportaccount moet u uw implementatie dienovereenkomstig aanpassen en overschakelen naar de Amazon Simple Storage Service (S3)-connector om gegevens te importeren of te exporteren. Raadpleeg voor meer informatie over het configureren van externe accounts met Amazon S3 [sectie](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign).

## Stap 1: Externe accounts in Adobe Campaign configureren of controleren {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Ten eerste moeten we de externe accounts in Adobe Campaign als volgt configureren of controleren:

1. Klik op de knop **[!UICONTROL Explorer]** pictogram.
1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**. De vermelde SFTP-rekeningen hadden door Adobe moeten zijn geconfigureerd en de benodigde informatie had aan u moeten worden meegedeeld.

   * **[!UICONTROL importSharedAudience]**: account voor het importeren van publiek.
   * **[!UICONTROL exportSharedAudience]**: account gewijd aan het exportpubliek.

   ![](assets/aam_config_1.png)

1. Selecteer **[!UICONTROL Export audiences to the Adobe Marketing Cloud]** externe rekening.

1. Van de **[!UICONTROL Type]** vervolgkeuzelijst, selecteert u **[!UICONTROL AWS S3]**.

1. Geef de volgende gegevens op:

   * **[!UICONTROL AWS S3 Account Server]**
URL van uw server, zou het als volgt moeten worden gevuld:

      ```
      <S3bucket name>.s3.amazonaws.com/<s3object path>
      ```

   * **[!UICONTROL AWS access key ID]**
Als u wilt weten waar je AWS-toegangs sleutel-id moet worden gevonden, raadpleegt u deze [page](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

   * **[!UICONTROL Secret access key to AWS]**
Als je wilt weten waar je je geheime toegangssleutel voor AWS vindt, raadpleeg dan deze [page](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

   * **[!UICONTROL AWS Region]**
Raadpleeg de volgende secties voor meer informatie over AWS-regio [page](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).
   ![](assets/aam_config_2.png)

1. Klikken **[!UICONTROL Save]** en configureert u de **[!UICONTROL Import audiences from the Adobe Marketing Cloud]** externe rekening zoals in de vorige stappen beschreven.

Uw externe accounts zijn nu geconfigureerd.

## Stap 2: De gegevensbron configureren {#step-2--configure-the-data-source}

De **Ontvanger - Bezoeker-id** wordt gemaakt in Audience Manager. Dit is een uit-van-de-doos gegevensbron die door gebrek voor identiteitskaart van de Bezoeker wordt gevormd. Segmenten die zijn gemaakt op basis van campagne maken deel uit van deze gegevensbron.

Om het **[!UICONTROL Recipient - Visitor ID]** gegevensbron:

1. Van de **[!UICONTROL Explorer]** knooppunt, selecteren **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. Selecteer **[!UICONTROL Recipient - Visitor ID]**.
1. Voer de **[!UICONTROL Data Source ID]** en **[!UICONTROL AAM Destination ID]** verstrekt door Adobe.

   ![](assets/aam_config_3.png)

## Stap 3: Campagne bijhouden-server configureren {#step-3--configure-campaign-tracking-server}

Voor de configuratie van de integratie met de dienst van de Kern van Mensen of de manager van het Publiek, moeten wij ook de server van het Volgen van de Campagne vormen.

U moet ervoor zorgen de het Volgen van de Campagne Server op het domein (CNAME) wordt geregistreerd. Meer informatie over domeinnaamdelegatie vindt u in [dit artikel](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=nl).

## Stap 4: De service voor de bezoekersidentiteitskaart configureren {#step-4--configure-the-visitor-id-service}

Raadpleeg het volgende als uw bezoekersidentiteitsservice nog nooit is geconfigureerd op uw wegeigenschappen of websites [document](https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-aam-analytics.html) leren hoe te om uw dienst of het volgende te vormen [video](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two).

Uw configuratie en levering worden voltooid, kan de integratie nu worden gebruikt om publiek of segmenten in te voeren en uit te voeren.
