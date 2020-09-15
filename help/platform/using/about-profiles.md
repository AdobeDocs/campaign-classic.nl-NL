---
title: Informatie over profielen
seo-title: Informatie over profielen
description: Informatie over profielen
seo-description: null
page-status-flag: never-activated
uuid: 9a3fcb58-a356-4eee-bc26-c64825de5f99
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 5addada8-0185-488f-9825-83f60981c139
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 762a6ba3fdad9c30407bf807f2cd8076796f98c2
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 15%

---


# Informatie over profielen{#about-profiles}

Profielen (klanten, prospects, leden van nieuwsbrieven, enzovoort) zijn gecentraliseerd in de Adobe Campaign-database. Er zijn vele mogelijke mechanismen om profielen te verwerven en deze database op te bouwen: online verzameling via webformulieren, handmatig of automatisch importeren van tekstbestanden, replicatie met bedrijfsdatabases of andere informatiesystemen. Met Adobe Campaign kunt u de marketinggeschiedenis, aankoopgegevens, voorkeuren, CRM-gegevens en alle relevante PI-gegevens in een geconsolideerde weergave opnemen om te analyseren en actie te ondernemen.

In Adobe Campaign zijn ontvangers de standaardprofielen voor het verzenden van leveringen (e-mails, sms’en, enzovoort). Dankzij de ontvangerdata die in de database worden opgeslagen, kunt u het doel filteren dat een bepaalde levering zal ontvangen en personalisatiedata in uw leveringscontent toevoegen. De database bevat andere typen profielen. Ze zijn ontworpen voor verschillende applicaties. Seed-profielen worden bijvoorbeeld gemaakt om de leveringen te testen voordat ze naar het uiteindelijke doel worden verzonden.

![](assets/do-not-localize/how-to-video.png) [Werken met het concept profielen in video](#create-profiles-video)

## Profieltypen {#profile-types}

Met Adobe Campaign kunt u profielen gedurende de volledige levenscyclus beheren: maken, importeren, aanwijzen, handelingen bijhouden, bijwerken, enz.

Elk profiel komt overeen met een database-item. Zij bevatten alle informatie die vereist is voor het richten, kwalificeren en volgen van personen.

Profielen kunnen worden geïdentificeerd op basis van opslagruimte. Dit betekent dat een profiel kan overeenkomen met: een ontvanger, een bezoeker, een exploitant, een abonnee, een vooruitzicht, enz.

## Ontvangerprofielen {#recipient-profiles}

Ontvangers van de levering worden in de database opgeslagen als profielen die de aan hen gekoppelde informatie bevatten: achternaam, voornaam, adres, abonnementen, leveringen, enz. Wanneer u campagnes creeert, kunt u het doel van de leveringen aan een selectie van de profielen in de basis volgens eenvoudige of geavanceerde criteria bepalen.

U kunt ook campagnes maken voor ontvangers waarvan de profielen niet in de database maar in bestanden worden opgeslagen. Deze worden &quot;externe&quot; leveringen genoemd. Raadpleeg [deze pagina](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)voor meer informatie over dit type levering.

De belangrijkste methoden voor het maken van profielen voor ontvangers zijn:

* directe invoer in de grafische interfaceschermen,
* lijsten met ontvangers importeren,
* online verzameling via webformulieren.

>[!NOTE]
>
>Als u wilt weten hoe bestanden en webformulieren worden geïmporteerd, raadpleegt u [Algemene import en export](../../platform/using/generic-imports-and-exports.md).

## Profielen en doelen {#profiles-and-targets}

Met de **[!UICONTROL Profiles and targets]** koppeling kunt u ontvangers weergeven die zijn opgeslagen in de Adobe Campaign-database. U kunt een nieuwe ontvanger maken, een bestaande ontvanger bewerken en het bijbehorende profiel openen. For more on this, refer to [this page](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Het geeft u ook toegang tot:

* lijsten; zie [Lijsten](../../platform/using/creating-and-managing-lists.md)maken en beheren,
* abonnementsdiensten; verwijzen naar [deze pagina](../../delivery/using/managing-subscriptions.md),
* webtoepassingen; verwijzen naar [deze pagina](../../web/using/about-web-applications.md),
* invoer en uitvoer ( werkgelegenheid ) ; verwijzen naar [algemene invoer en uitvoer](../../platform/using/generic-imports-and-exports.md);
* doelgerichte werkstromen; verwijst naar [deze pagina](../../workflow/using/building-a-workflow.md#implementation-steps-).

Op de pagina met ontvangers kunt u veelvuldige bewerkingen uitvoeren op profielen: bewerkingen, updates, toevoegingen, verwijderingen, sorteren.

Voor geavanceerdere profielmanipulaties moet u de Adobe Campaign-structuur bewerken. Klik hiertoe op de **[!UICONTROL Explorer]** koppeling op de startpagina van Adobe Campaign.

Door gebrek, worden de ontvangers opgeslagen in de **[!UICONTROL Profiles and Targets > Recipients]** knoop van de boom. U kunt ontvangers maken vanuit deze weergave en ook:

* de profielen van de database sorteren en filteren; zie [Filteropties](../../platform/using/filtering-options.md);
* profielen uit de database verplaatsen, kopiëren of verwijderen; zie [Profielen](../../platform/using/managing-profiles.md)beheren;
* updateprofielen; zie Gegevens [bijwerken](../../platform/using/updating-data.md),
* ontvangers van uitvoer; zie Profielen [](../../platform/using/exporting-and-importing-profiles.md)exporteren en importeren;
* groepen ontvangers creëren; zie Lijsten [maken en beheren](../../platform/using/creating-and-managing-lists.md).

Voor toegang tot geavanceerde functies en configuraties moet u op het **[!UICONTROL Explorer]** pictogram klikken.

![](assets/d_ncs_user_interface01.png)

De algemene indeling van de Adobe Campaign-verkenner wordt weergegeven in de [Adobe Campaign-verkenner](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer)gebruiken.

>[!NOTE]
>
>U kunt een geavanceerde weergave van deze lijst ook weergeven vanuit de Adobe Campaign-structuur door op de **[!UICONTROL Profiles and targets > Recipients]** koppeling te klikken. De lijstvertoning kan aan uw behoeften worden gevormd. U kunt kolommen toevoegen of verwijderen, de kolomvolgorde, de sorteergegevens enzovoort definiëren. De de vertoningsconfiguratie van de lijst wordt beschreven in het [Gebruiken van de ontdekkingsreiziger](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer)van Adobe Campaign.
>
>U kunt ook de weergave voor ontvangers definiëren. Zie [Mappen en weergaven](../../platform/using/access-management.md#folders-and-views)voor meer informatie over deze functionaliteit.

## Actieve profielen {#active-profiles}

Actieve profielen zijn de profielen die voor factureringsdoeleinden worden geteld.

>[!NOTE]
>
>Als u op AWS wordt gehost en Campaign Classic uit build 8931 gebruikt, kunt u het aantal actieve profielen dat op uw instanties wordt gebruikt, ook rechtstreeks via het Configuratiescherm controleren. For more on this, refer to the [Control Panel documentation](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/active-profiles-monitoring.html).
>
>Het aantal actieve profielen is alleen beschikbaar voor **marketinginstanties** . Het is niet beschikbaar voor instanties van de Uitvoering, betekenend MID (midsourcing) en RT (het Centrum van het Bericht / Real-time overseinen) instanties.

“**Profile**” means a record of information (e.g.: a record in the nmsRecipient table or an external table containing a cookie ID, Customer ID, mobile identifier or other information relevant to a particular channel) representing an end-customer, prospect, or lead.

Facturering heeft alleen betrekking op profielen die **actief** zijn. Een profiel wordt als actief beschouwd als het profiel de afgelopen twaalf maanden via een kanaal als doel is aangewezen of met het profiel is gecommuniceerd.

Er wordt geen rekening gehouden met de profielen die tijdens de voorbereiding van de levering zijn uitgesloten (typologische regels, quarantaine). Een profiel dat voor meerdere leveringen is bestemd, wordt slechts eenmaal meegeteld.

>[!NOTE]
>
>Er wordt geen rekening gehouden met de kanalen Facebook en Twitter.

U kunt een overzicht van het **[!UICONTROL Number of active profiles]** van het menu van de Campaign Standard **[!UICONTROL Administration > Campaign Management > Customer metrics]** hebben. Het daadwerkelijke aantal wordt uitgevoerd door het **[!UICONTROL Number of active billing profiles]** (**[!UICONTROL billingActiveContactCount]**) [technische werkschema](../../workflow/using/deliveries.md), dat elke dag loopt en de nieuwe gegevens aan het bestaande rapport voor de huidige periode in het **[!UICONTROL Customer metrics]** menu toevoegt. Elke periode duurt 12 maanden.

## Profielen maken en beheren {#create-profiles-video}

Leer hoe u toegang krijgt tot profielgegevens, profielen kunt sorteren en filteren en profielen handmatig kunt maken en beheren.

In deze video wordt ook uitgelegd of Adobe Campaign Classic voldoet aan de algemene gegevensbeschermingsregels.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

**Zie ook**

* [Privacy mamanagement in Campaign](https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html)

* [Doelpopulatie definiëren](../../delivery/using/define-the-right-audience.md)

* [Vragen en segmentgegevens maken in workflows](../../workflow/using/targeting-data.md)

* [Doeltoewijzing selecteren](../../delivery/using/selecting-a-target-mapping.md)

* [Het publiek definiëren - aanbevolen procedures](../../delivery/using/define-the-right-audience.md)
