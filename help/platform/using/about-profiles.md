---
product: campaign
title: Aan de slag met profielen
description: Werken met profielen in Adobe Campaign
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: d42389add06db74c54cb3a21813e9a832a2a288a
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 14%

---

# Aan de slag met profielen{#about-profiles}

![](../../assets/v7-only.svg)

Profielen worden gecentraliseerd in de Adobe Campaign-database. Er zijn vele mogelijke mechanismen om profielen te verwerven en deze database op te bouwen: online verzameling via webformulieren, handmatig of automatisch importeren van tekstbestanden, replicatie met bedrijfsdatabases of andere informatiesystemen. Met Adobe Campaign kunt u de marketinggeschiedenis, aankoopgegevens, voorkeuren, CRM-gegevens en alle relevante PI-gegevens in een geconsolideerde weergave opnemen om te analyseren en actie te ondernemen.

&quot;**Profiel**&quot;: een informatiedossier (bv.: een record in de nmsRecipient-tabel of een externe tabel met een cookie-id, de klant-id, de mobiele id of andere informatie die relevant is voor een bepaald kanaal) die een eindklant, perspectief of lead vertegenwoordigt.

In Adobe Campaign zijn ontvangers de standaardprofielen voor het verzenden van leveringen (e-mails, sms’en, enzovoort). De ontvangende gegevens die in het gegevensbestand worden opgeslagen laten u toe om het doel te filtreren dat om het even welke bepaalde levering zal ontvangen en verpersoonlijkingsgegevens in uw leveringsinhoud toe te voegen. De database bevat andere typen profielen. Ze zijn ontworpen voor verschillende applicaties. Seed-profielen worden bijvoorbeeld gemaakt om de leveringen te testen voordat ze naar het uiteindelijke doel worden verzonden.

![](assets/do-not-localize/how-to-video.png) [Werken met het concept profielen in video](#create-profiles-video)

## Profieltypen {#profile-types}

Met Adobe Campaign kunt u profielen gedurende de volledige levenscyclus beheren: maken, importeren, aanwijzen, handelingen bijhouden, bijwerken, enz.

Elk profiel komt overeen met een database-item. Zij bevatten alle informatie die vereist is voor het richten, kwalificeren en volgen van personen.

Profielen kunnen worden geïdentificeerd op basis van opslagruimte. Dit betekent dat een profiel kan overeenkomen met: een ontvanger, een bezoeker, een exploitant, een abonnee, een vooruitzicht, enz.

## Ontvangerprofielen {#recipient-profiles}

Ontvangers van de levering worden in de database opgeslagen als profielen die de aan hen gekoppelde informatie bevatten: achternaam, voornaam, adres, abonnementen, leveringen, enz. Wanneer u campagnes creeert, kunt u het doel van de leveringen aan een selectie van de profielen in de basis volgens eenvoudige of geavanceerde criteria bepalen.

U kunt ook campagnes maken voor ontvangers waarvan de profielen niet in de database maar in bestanden worden opgeslagen. Deze worden &quot;externe&quot; leveringen genoemd. Voor meer informatie over dit type levering raadpleegt u [deze pagina](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

De belangrijkste methoden voor het maken van profielen voor ontvangers zijn:

* directe invoer in de grafische interfaceschermen,
* lijsten met ontvangers importeren,
* online verzameling via webformulieren.

>[!NOTE]
>
>Als u wilt weten hoe bestanden en webformulieren worden geïmporteerd, raadpleegt u [Algemene invoer en uitvoer](../../platform/using/get-started-data-import-export.md).

## Profielen en doelen {#profiles-and-targets}

De **[!UICONTROL Profiles and targets]** Met deze koppeling kunt u ontvangers weergeven die zijn opgeslagen in de Adobe Campaign-database. U kunt een nieuwe ontvanger maken, een bestaande ontvanger bewerken en het bijbehorende profiel openen. Raadpleeg [deze pagina](../../platform/using/editing-a-profile.md) voor meer informatie.

![](assets/d_ncs_user_interface_target_link.png)

Het geeft u ook toegang tot:

* lijsten - [Meer informatie](../../platform/using/creating-and-managing-lists.md)
* abonnementsservices - [Meer informatie](../../delivery/using/managing-subscriptions.md)
* webtoepassingen - [Meer informatie](../../web/using/about-web-applications.md)
* invoer en uitvoer ( werkgelegenheid ) - [Meer informatie](../../platform/using/about-generic-imports-exports.md)
* doelgerichte workflows - [Meer informatie](../../workflow/using/building-a-workflow.md#implementation-steps-)

Op de pagina met ontvangers kunt u veelvuldige bewerkingen uitvoeren op profielen: bewerkingen, updates, toevoegingen, verwijderingen, sorteren.

Voor geavanceerdere profielmanipulaties moet u de Adobe Campaign-structuur bewerken. Om dit te doen, klik **[!UICONTROL Explorer]** koppeling op de startpagina van Adobe Campaign.

Ontvangers worden standaard opgeslagen in de **[!UICONTROL Profiles and Targets > Recipients]** knooppunt van de structuur. U kunt ontvangers maken vanuit deze weergave en ook:

* de profielen van de database sorteren en filteren - [Meer informatie](../../platform/using/filtering-options.md)
* profielen verplaatsen, kopiëren of verwijderen uit de database - [Meer informatie](../../platform/using/managing-profiles.md),
* updateprofielen - [Meer informatie](../../platform/using/updating-data.md)
* exportontvangers - [Meer informatie](../../platform/using/exporting-and-importing-profiles.md)
* groepen ontvangers maken - [Meer informatie](../../platform/using/creating-and-managing-lists.md)

Voor toegang tot geavanceerde functies en configuraties moet u op de knop **[!UICONTROL Explorer]** pictogram.

![](assets/d_ncs_user_interface01.png)

De algemene lay-out van de Adobe Campaign-verkenner wordt weergegeven in [deze pagina](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>U kunt een geavanceerde weergave van deze lijst ook weergeven vanuit de Adobe Campaign-structuur door te klikken op de knop **[!UICONTROL Profiles and targets > Recipients]** koppeling. De lijstvertoning kan aan uw behoeften worden gevormd. U kunt kolommen toevoegen of verwijderen, de kolomvolgorde, de sorteergegevens enzovoort definiëren. De weergaveconfiguratie van de lijst wordt beschreven in [deze pagina](../../platform/using/adobe-campaign-ui-lists.md).
>
>U kunt ook de weergave voor ontvangers definiëren. Voor meer informatie over deze functionaliteit raadpleegt u [deze sectie](../../platform/using/access-management-folders.md).

## Actieve profielen {#active-profiles}

Actieve profielen zijn de profielen die voor factureringsdoeleinden worden geteld.

Facturering heeft alleen betrekking op profielen die **actief**. Een profiel wordt als actief beschouwd als het profiel de afgelopen twaalf maanden via een kanaal als doel is aangewezen of met het profiel is gecommuniceerd.

Een profiel dat voor meerdere leveringen is bedoeld, wordt slechts eenmaal geteld.

>[!NOTE]
>
>Er wordt geen rekening gehouden met de kanalen Facebook en Twitter.

Aantal actieve profielen is beschikbaar voor **Marketinginstanties** alleen. Het is niet beschikbaar voor instanties van de Uitvoering, betekenend MID (midsourcing) en RT (het Centrum van het Bericht / Real-time overseinen) instanties.

>[!NOTE]
>
>U kunt het aantal actieve profielen op uw instantie ook controleren direct van het Controlebord van de Campagne. Raadpleeg voor meer informatie de [Documentatie van het regelpaneel](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html).

## Video over zelfstudie {#create-profiles-video}

Leer hoe u toegang krijgt tot profielgegevens, profielen kunt sorteren en filteren en profielen handmatig kunt maken en beheren.

In deze video wordt ook uitgelegd of Adobe Campaign Classic voldoet aan de algemene gegevensbeschermingsregels.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

Er zijn aanvullende Campaign Classic-hoe-kan-video&#39;s beschikbaar [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).

**Zie ook**

* [Privacybeheer in campagne](https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html)

* [Doelpopulatie definiëren](../../delivery/using/define-the-right-audience.md)

* [Vragen en segmentgegevens maken in workflows](../../workflow/using/targeting-data.md)

* [Doeltoewijzing selecteren](../../delivery/using/selecting-a-target-mapping.md)

* [Het publiek definiëren - aanbevolen procedures](../../delivery/using/define-the-right-audience.md)
