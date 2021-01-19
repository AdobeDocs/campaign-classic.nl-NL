---
solution: Campaign Classic
product: campaign
title: Informatie over profielen
description: Informatie over profielen
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 17%

---


# Informatie over profielen{#about-profiles}

Profielen (klanten, prospects, leden van nieuwsbrieven, enzovoort) zijn gecentraliseerd in de Adobe Campaign-database. Er zijn vele mogelijke mechanismen om profielen te verwerven en deze database op te bouwen: online verzameling via webformulieren, handmatig of automatisch importeren van tekstbestanden, replicatie met bedrijfsdatabases of andere informatiesystemen. Met Adobe Campaign kunt u de marketinggeschiedenis, aankoopgegevens, voorkeuren, CRM-gegevens en alle relevante PI-gegevens in een geconsolideerde weergave opnemen om te analyseren en actie te ondernemen.

In Adobe Campaign zijn ontvangers de standaardprofielen voor het verzenden van leveringen (e-mails, sms’en, enzovoort). Dankzij de ontvangerdata die in de database worden opgeslagen, kunt u het doel filteren dat een bepaalde levering zal ontvangen en personalisatiedata in uw leveringscontent toevoegen. De database bevat andere typen profielen. Ze zijn ontworpen voor verschillende applicaties. Seed-profielen worden bijvoorbeeld gemaakt om de leveringen te testen voordat ze naar het uiteindelijke doel worden verzonden.

![](assets/do-not-localize/how-to-video.png) [Werken met het concept profielen in video](#create-profiles-video)

## Profieltypen {#profile-types}

Met Adobe Campaign kunt u profielen gedurende de volledige levenscyclus beheren: maken, importeren, aanwijzen, handelingen bijhouden, bijwerken, enz.

Elk profiel komt overeen met een database-item. Zij bevatten alle informatie die vereist is voor het richten, kwalificeren en volgen van personen.

Profielen kunnen worden geïdentificeerd op basis van opslagruimte. Dit betekent dat een profiel kan overeenkomen met: een ontvanger, een bezoeker, een exploitant, een abonnee, een vooruitzicht, enz.

## Ontvangersprofielen {#recipient-profiles}

Ontvangers van de levering worden in de database opgeslagen als profielen die de aan hen gekoppelde informatie bevatten: achternaam, voornaam, adres, abonnementen, leveringen, enz. Wanneer u campagnes creeert, kunt u het doel van de leveringen aan een selectie van de profielen in de basis volgens eenvoudige of geavanceerde criteria bepalen.

U kunt ook campagnes maken voor ontvangers waarvan de profielen niet in de database maar in bestanden worden opgeslagen. Deze worden &quot;externe&quot; leveringen genoemd. Voor meer informatie over dit type van levering, verwijs naar [deze pagina](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

De belangrijkste methoden voor het maken van profielen voor ontvangers zijn:

* directe invoer in de grafische interfaceschermen,
* lijsten met ontvangers importeren,
* online verzameling via webformulieren.

>[!NOTE]
>
>Als u wilt weten hoe bestanden en webformulieren worden geïmporteerd, raadpleegt u [Algemene import en export](../../platform/using/get-started-data-import-export.md).

## Profielen en doelen {#profiles-and-targets}

Met de koppeling **[!UICONTROL Profiles and targets]** kunt u ontvangers weergeven die zijn opgeslagen in de Adobe Campaign-database. U kunt een nieuwe ontvanger maken, een bestaande ontvanger bewerken en het bijbehorende profiel openen. Raadpleeg [deze pagina](../../platform/using/editing-a-profile.md) voor meer informatie.

![](assets/d_ncs_user_interface_target_link.png)

Het geeft u ook toegang tot:

* lijsten; zie [Lijsten maken en beheren](../../platform/using/creating-and-managing-lists.md),
* abonnementsdiensten; verwijzen naar [deze pagina](../../delivery/using/managing-subscriptions.md),
* webtoepassingen; verwijzen naar [deze pagina](../../web/using/about-web-applications.md),
* invoer en uitvoer ( werkgelegenheid ) ; zie [Algemene invoer en uitvoer](../../platform/using/about-generic-imports-exports.md);
* doelgerichte werkstromen; verwijst naar [deze pagina](../../workflow/using/building-a-workflow.md#implementation-steps-).

Op de pagina met ontvangers kunt u veelvuldige bewerkingen uitvoeren op profielen: bewerkingen, updates, toevoegingen, verwijderingen, sorteren.

Voor geavanceerdere profielmanipulaties moet u de Adobe Campaign-structuur bewerken. Klik hiertoe op de koppeling **[!UICONTROL Explorer]** op de startpagina van Adobe Campaign.

Door gebrek, worden de ontvangers opgeslagen in de **[!UICONTROL Profiles and Targets > Recipients]** knoop van de boom. U kunt ontvangers maken vanuit deze weergave en ook:

* de profielen van de database sorteren en filteren; zie [Filteropties](../../platform/using/filtering-options.md),
* profielen uit de database verplaatsen, kopiëren of verwijderen; zie [Profielen beheren](../../platform/using/managing-profiles.md),
* updateprofielen; zie [Gegevens bijwerken](../../platform/using/updating-data.md),
* ontvangers van uitvoer; zie [Profielen exporteren en importeren](../../platform/using/exporting-and-importing-profiles.md),
* groepen ontvangers creëren; zie [Lijsten maken en beheren](../../platform/using/creating-and-managing-lists.md).

Voor toegang tot geavanceerde functies en configuraties moet u op het pictogram **[!UICONTROL Explorer]** klikken.

![](assets/d_ncs_user_interface01.png)

De algemene indeling van de Adobe Campaign-verkenner wordt weergegeven in [Adobe Campaign-verkenner gebruiken](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).

>[!NOTE]
>
>U kunt een geavanceerde weergave van deze lijst ook weergeven vanuit de Adobe Campaign-structuur door op de koppeling **[!UICONTROL Profiles and targets > Recipients]** te klikken. De lijstvertoning kan aan uw behoeften worden gevormd. U kunt kolommen toevoegen of verwijderen, de kolomvolgorde, de sorteergegevens enzovoort definiëren. De de vertoningsconfiguratie van de lijst wordt beschreven in [Gebruikend de ontdekkingsreiziger van Adobe Campaign](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).
>
>U kunt ook de weergave voor ontvangers definiëren. Raadpleeg [Mappen en weergaven](../../platform/using/access-management.md#folders-and-views) voor meer informatie over deze functionaliteit.

## Actieve profielen {#active-profiles}

Actieve profielen zijn de profielen die voor factureringsdoeleinden worden geteld.

>[!NOTE]
>
>Als u op AWS wordt gehost en Campaign Classic uit build 8931 gebruikt, kunt u het aantal actieve profielen dat op uw instanties wordt gebruikt, ook rechtstreeks via het Configuratiescherm controleren. Raadpleeg de [documentatie van het Configuratiescherm](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/active-profiles-monitoring.html) voor meer informatie.
>
>Het aantal actieve profielen is alleen beschikbaar voor **Marketingsinstanties**. Het is niet beschikbaar voor instanties van de Uitvoering, betekenend MID (midsourcing) en RT (het Centrum van het Bericht / Real-time overseinen) instanties.

&quot;**Profiel**&quot; betekent een record met informatie (bijvoorbeeld: een record in de nmsRecipient-tabel of een externe tabel met een cookie-id, de klant-id, de mobiele id of andere informatie die relevant is voor een bepaald kanaal) die een eindklant, perspectief of lead vertegenwoordigt.

Facturering heeft alleen betrekking op profielen die **actief** zijn. Een profiel wordt als actief beschouwd als het profiel de afgelopen twaalf maanden via een kanaal als doel is aangewezen of met het profiel is gecommuniceerd.

Er wordt geen rekening gehouden met de profielen die tijdens de voorbereiding van de levering zijn uitgesloten (typologische regels, quarantaine). Een profiel dat voor meerdere leveringen is bestemd, wordt slechts eenmaal meegeteld.

>[!NOTE]
>
>Er wordt geen rekening gehouden met de kanalen Facebook en Twitter.

U kunt een overzicht van **[!UICONTROL Number of active profiles]** van het menu van Campaign Standard hebben **[!UICONTROL Administration > Campaign Management > Customer metrics]**. Het daadwerkelijke aantal wordt uitgevoerd door **[!UICONTROL Number of active billing profiles]** (**[!UICONTROL billingActiveContactCount]**) [technische werkschema](../../workflow/using/about-technical-workflows.md), die elke dag loopt en de nieuwe gegevens aan het bestaande rapport voor de huidige periode in **[!UICONTROL Customer metrics]** menu toevoegt. Elke periode duurt 12 maanden.

## Video over zelfstudie {#create-profiles-video}

Leer hoe u toegang krijgt tot profielgegevens, profielen kunt sorteren en filteren en profielen handmatig kunt maken en beheren.

In deze video wordt ook uitgelegd of Adobe Campaign Classic voldoet aan de algemene gegevensbeschermingsregels.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl) extra Campaign Classic hoe kan ik-video&#39;s beschikbaar.

**Zie ook**

* [Privacybeheer in campagne](https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html)

* [Doelpopulatie definiëren](../../delivery/using/define-the-right-audience.md)

* [Vragen en segmentgegevens maken in workflows](../../workflow/using/targeting-data.md)

* [Doeltoewijzing selecteren](../../delivery/using/selecting-a-target-mapping.md)

* [Het publiek definiëren - aanbevolen procedures](../../delivery/using/define-the-right-audience.md)
