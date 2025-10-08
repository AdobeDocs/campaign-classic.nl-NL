---
product: campaign
title: Aan de slag met profielen
description: Werken met profielen in Adobe Campaign
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: 4d8c4ba846148d3df00a76ecc29375b9047c2b20
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 22%

---

# Aan de slag met profielen{#about-profiles}



Profielen worden gecentraliseerd in de Adobe Campaign-database. Er zijn vele mogelijke mechanismen om profielen te verwerven en deze database op te bouwen: online verzameling via webformulieren, handmatig of automatisch importeren van tekstbestanden, replicatie met bedrijfsdatabases of andere informatiesystemen. Met Adobe Campaign kunt u de marketinggeschiedenis, aankoopgegevens, voorkeuren, CRM-gegevens en alle relevante PI-gegevens in een geconsolideerde weergave opnemen om te analyseren en actie te ondernemen.

&quot;**Profiel**&quot;betekent een verslag van informatie (b.v.: een verslag in de nmsRecipient lijst of een externe lijst die een koekjesidentiteitskaart, identiteitskaart van de Klant, mobiele herkenningsteken of andere informatie relevant voor een bepaald kanaal bevatten) die een eindklant, een vooruitzicht, of een lood vertegenwoordigen.

In Adobe Campaign zijn ontvangers de standaardprofielen voor het verzenden van leveringen (e-mails, sms’en, enzovoort). De ontvangende gegevens die in het gegevensbestand worden opgeslagen laten u toe om het doel te filtreren dat om het even welke bepaalde levering zal ontvangen en verpersoonlijkingsgegevens in uw leveringsinhoud toe te voegen. De database bevat andere typen profielen. Ze zijn ontworpen voor verschillende applicaties. Seed-profielen worden bijvoorbeeld gemaakt om de leveringen te testen voordat ze naar het uiteindelijke doel worden verzonden.

![&#x200B; Video die toont welke profielen zijn en hoe zij &#x200B;](assets/do-not-localize/how-to-video.png) [&#x200B; werken begrijpt het concept profielen in video &#x200B;](#create-profiles-video)

>[!NOTE]
>
>Meer over profiel leren, om hen tot stand te brengen en uit te geven, gelieve te verwijzen naar de gedetailleerde documentatie over de [&#x200B; Campagne v8 documentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/audience/gs-audiences){target=_blank}.

>[!BEGINTABS]

>[!TAB  documentatie van Profielen ]

Meer over profiel leren, om hen tot stand te brengen en uit te geven, gelieve te verwijzen naar de gedetailleerde documentatie over de **[Campagne v8 documentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/audience/gs-audiences){target=_blank}**.

[![afbeelding](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/audience/gs-audiences){target=_blank}

>[!TAB creeer en geef profielen  uit]

Leer om profielen in de **documentatie van de Campagne v8** uit te geven, te beheren en toe te voegen:

* [&#x200B; voegt profielen &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign-classic/using/getting-started/profile-management/adding-profiles){target=_blank} toe: Leer de belangrijkste stappen om nieuwe profielen toe te voegen en tot stand te brengen.
* [&#x200B; geef profielen &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/audience/view-profiles?lang=en#_blank){target=_blank} uit: Bekijk en geef bestaande profielen uit.
* [&#x200B; beheer profielen &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/folders-and-views?lang=en#_blank){target=_blank}: Heb toegang tot en beheer uw bestaande profielen gebruikend het hulpmiddel van het omslagbeheer.

>[!TAB  de Invoer/de uitvoerprofielen ]

Leer hoe te om profielen en gegevens in de **Campagne v8 documentatie** in te voeren en uit te voeren:

* [&#x200B; de Profielen van de Invoer &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/audience/add-profiles/import-profiles){target=_blank}: U kunt profielen invoeren gebruikend werkschema&#39;s.
* [&#x200B; de Invoer/de uitvoergegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/data/import){target=_blank}: Leer hoe te om gegevens en profielen in te voeren of uit te voeren gebruikend generische invoer/uitvoer.

>[!ENDTABS]

<!--
## Profile types {#profile-types}

Adobe Campaign lets you manage profiles throughout their entire lifecycle: creation, import, targeting, action tracking, updates, etc.

Each profile matches a database entry. They contain all the information required for targeting, qualifying and tracking individuals.

Profiles can be identified based on storage space. This means that a profile can match: a recipient, a visitor, an operator, a subscriber, a prospect, etc.

## Recipient profiles {#recipient-profiles}

Delivery recipients are stored in the database as profiles containing the information linked to them: last name, first name, address, subscriptions, deliveries, etc. When you create campaigns, you can define the target of the deliveries to a selection of the profiles in the base according to simple or advanced criteria.

You can also create campaigns aimed at recipients whose profiles are stored not in the database, but in files. These are known as "external" deliveries. For more information about this type of delivery, refer to [this page](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

The main methods for creating recipient profiles are as follows:

* direct input in the graphical interface screens,
* importing recipient lists,
* on-line collection via web forms.

>[!NOTE]
>
>To find out how files and web forms are imported, refer to [Generic imports and exports](../../platform/using/get-started-data-import-export.md).

## Profiles and targets {#profiles-and-targets}

The **[!UICONTROL Profiles and targets]** link lets you display recipients stored in Adobe Campaign database. You can create new recipient, edit an existing recipient and access its profile. For more on this, refer to [this page](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

It also gives you access to:

* lists - [Learn more](../../platform/using/creating-and-managing-lists.md)
* subscription services - [Learn more](../../delivery/using/managing-subscriptions.md)
* web applications - [Learn more](../../web/using/about-web-applications.md)
* imports and exports (jobs) - [Learn more](../../platform/using/about-generic-imports-exports.md)
* targeting workflows - [Learn more](../../workflow/using/building-a-workflow.md#implementation-steps-)

The recipients page lets you perform frequent operations on profiles: edits, updates, adds, deletions, sorts.

For more advanced profile manipulations, you need to edit the Adobe Campaign tree. To do this, click the **[!UICONTROL Explorer]** link on the Adobe Campaign home page.

By default, recipients are stored in the **[!UICONTROL Profiles and Targets > Recipients]** node of the tree. You can create recipients from this view, as well as:

* sort and filter the profiles of the database - [Learn more](../../platform/using/filtering-options.md)
* move, copy or delete profiles from the database - [Learn more](../../platform/using/managing-profiles.md),
* update profiles - [Learn more](../../platform/using/updating-data.md)
* export recipients - [Learn more](../../platform/using/exporting-and-importing-profiles.md)
* create recipient groups - [Learn more](../../platform/using/creating-and-managing-lists.md)

To access advanced functionalities and configurations, you need to click the **[!UICONTROL Explorer]** icon. 

![](assets/d_ncs_user_interface01.png)

The general layout of the Adobe Campaign explorer is presented in [this page](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>You can also display an advanced view of this list from the Adobe Campaign tree by clicking the **[!UICONTROL Profiles and targets > Recipients]** link. The list display can be configured to suit your needs. You can add or delete columns, define column order, sort data, etc. List display configuration is described in [this page](../../platform/using/adobe-campaign-ui-lists.md).  
>
>You can also define recipient views. For further information about this functionality, refer to [this section](../../platform/using/access-management-folders.md).

## Active profiles {#active-profiles}

An active profile is a profile that customer has attempted to communicate with during the past 12 months via any channel.

According to your contract, each of your Campaign instances is provisioned with a specific amount of active profiles that are counted for billing purposes. Please refer to your latest contract for reference on number of purchased active profiles. Learn more in [Adobe Campaign product description](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

You can monitor the number of active profiles on your instance directly from Campaign Control Panel. For more on this, refer to the [Control Panel documentation](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html?lang=nl-NL){target="_blank"}.

The following guardrails and limitations apply:

* A profile that has been targeted by several deliveries is counted only once. 
* Profiles targeted in the context of Social marketing on X (Twitter) or Facebook are not taken into account as active profiles.
* The count of active profiles is available for **Marketing instances** only. It is not available for Execution instances, meaning MID (mid sourcing) and RT (Message Center / Real-time messaging) instances.
* The count is based on the recipient primary key. As a consequence, if a profile is present in two different recipient tables, it can be counted twice as an active profile.


## Tutorial video {#create-profiles-video}

Learn how to access profile data, sort and filter profiles and manually create and manage profiles.

This video also explains the compliance of Adobe Campaign Classic with General Data Protection Regulations. 

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

Additional Campaign Classic how-to videos are available [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl-NL).

**See also**

* [Privacy management in Campaign](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

* [Create queries and segment data in workflows](../../workflow/using/targeting-data.md)

* [Select target mapping](../../delivery/using/steps-defining-the-target-population.md#select-a-target-mapping)

-->