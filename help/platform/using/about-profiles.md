---
product: campaign
title: Aan de slag met profielen
description: Werken met profielen in Adobe Campaign
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 14%

---

# Aan de slag met profielen{#about-profiles}



Profielen worden gecentraliseerd in de Adobe Campaign-database. Er zijn vele mogelijke mechanismen om profielen te verwerven en deze database op te bouwen: online verzameling via webformulieren, handmatig of automatisch importeren van tekstbestanden, replicatie met bedrijfsdatabases of andere informatiesystemen. Met Adobe Campaign kunt u de marketinggeschiedenis, aankoopgegevens, voorkeuren, CRM-gegevens en alle relevante PI-gegevens in een geconsolideerde weergave opnemen om te analyseren en actie te ondernemen.

&quot;**Profiel**&quot;betekent een verslag van informatie (b.v.: een verslag in de nmsRecipient lijst of een externe lijst die een koekjesidentiteitskaart, identiteitskaart van de Klant, mobiele herkenningsteken of andere informatie relevant voor een bepaald kanaal bevatten) die een eindklant, een vooruitzicht, of een lood vertegenwoordigen.

In Adobe Campaign zijn ontvangers de standaardprofielen voor het verzenden van leveringen (e-mails, sms’en, enzovoort). De ontvangende gegevens die in het gegevensbestand worden opgeslagen laten u toe om het doel te filtreren dat om het even welke bepaalde levering zal ontvangen en verpersoonlijkingsgegevens in uw leveringsinhoud toe te voegen. De database bevat andere typen profielen. Ze zijn ontworpen voor verschillende applicaties. Seed-profielen worden bijvoorbeeld gemaakt om de leveringen te testen voordat ze naar het uiteindelijke doel worden verzonden.

![](assets/do-not-localize/how-to-video.png) [ Begrijp het concept profielen in video ](#create-profiles-video)

## Profieltypen {#profile-types}

Met Adobe Campaign kunt u profielen gedurende de volledige levenscyclus beheren: maken, importeren, aanwijzen, handelingen bijhouden, updates, enzovoort.

Elk profiel komt overeen met een database-item. Zij bevatten alle informatie die vereist is voor het richten, kwalificeren en volgen van personen.

Profielen kunnen worden geïdentificeerd op basis van opslagruimte. Dit betekent dat een profiel kan overeenkomen: een ontvanger, een bezoeker, een exploitant, een abonnee, een vooruitzicht, enz.

## Ontvangerprofielen {#recipient-profiles}

Ontvangers van leveringen worden in de database opgeslagen als profielen die de hun gekoppelde informatie bevatten: achternaam, voornaam, adres, abonnementen, leveringen, enz. Wanneer u campagnes creeert, kunt u het doel van de leveringen aan een selectie van de profielen in de basis volgens eenvoudige of geavanceerde criteria bepalen.

U kunt ook campagnes maken voor ontvangers waarvan de profielen niet in de database maar in bestanden worden opgeslagen. Deze worden &quot;externe&quot; leveringen genoemd. Voor meer informatie over dit type van levering, verwijs naar [ deze pagina ](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

De belangrijkste methoden voor het maken van profielen voor ontvangers zijn:

* directe invoer in de grafische interfaceschermen,
* lijsten met ontvangers importeren,
* online verzameling via webformulieren.

>[!NOTE]
>
>Om te weten te komen hoe de dossiers en de Webvormen worden ingevoerd, verwijs naar [ Algemene invoer en de uitvoer ](../../platform/using/get-started-data-import-export.md).

## Profielen en doelen {#profiles-and-targets}

Met de koppeling **[!UICONTROL Profiles and targets]** kunt u ontvangers weergeven die zijn opgeslagen in de Adobe Campaign-database. U kunt een nieuwe ontvanger maken, een bestaande ontvanger bewerken en het bijbehorende profiel openen. Raadpleeg [deze pagina](../../platform/using/editing-a-profile.md) voor meer informatie.

![](assets/d_ncs_user_interface_target_link.png)

Het geeft u ook toegang tot:

* lijsten - [ Leer meer ](../../platform/using/creating-and-managing-lists.md)
* De diensten van het abonnement - [ leren meer ](../../delivery/using/managing-subscriptions.md)
* Webtoepassingen - [ leren meer ](../../web/using/about-web-applications.md)
* de invoer en de uitvoer (banen) - [ leren meer ](../../platform/using/about-generic-imports-exports.md)
* het richten werkschema&#39;s - [ leer meer ](../../workflow/using/building-a-workflow.md#implementation-steps-)

Op de pagina met ontvangers kunt u veelvuldige bewerkingen uitvoeren op profielen: bewerken, bijwerken, toevoegen, verwijderen en sorteren.

Voor geavanceerdere profielmanipulaties moet u de Adobe Campaign-structuur bewerken. Klik hiertoe op de koppeling **[!UICONTROL Explorer]** op de startpagina van Adobe Campaign.

Ontvangers worden standaard opgeslagen in het knooppunt **[!UICONTROL Profiles and Targets > Recipients]** van de boomstructuur. U kunt ontvangers maken vanuit deze weergave en ook:

* soort en filter de profielen van het gegevensbestand - [ Leer meer ](../../platform/using/filtering-options.md)
* Beweeg, kopieer of schrap profielen van het gegevensbestand - [ leer meer ](../../platform/using/managing-profiles.md),
* updateprofielen - [ leer meer ](../../platform/using/updating-data.md)
* de uitvoerontvangers - [ leren meer ](../../platform/using/exporting-and-importing-profiles.md)
* creeer ontvankelijke groepen - [ leer meer ](../../platform/using/creating-and-managing-lists.md)

Voor toegang tot geavanceerde functies en configuraties moet u op het pictogram **[!UICONTROL Explorer]** klikken.

![](assets/d_ncs_user_interface01.png)

De algemene lay-out van de ontdekkingsreiziger van Adobe Campaign wordt voorgesteld in [ deze pagina ](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>U kunt een geavanceerde weergave van deze lijst ook weergeven vanuit de Adobe Campaign-structuur door op de koppeling **[!UICONTROL Profiles and targets > Recipients]** te klikken. De lijstvertoning kan aan uw behoeften worden gevormd. U kunt kolommen toevoegen of verwijderen, de kolomvolgorde, de sorteergegevens enzovoort definiëren. De vertoningsconfiguratie van de lijst wordt beschreven in [ deze pagina ](../../platform/using/adobe-campaign-ui-lists.md).
>
>U kunt ook de weergave voor ontvangers definiëren. Voor verdere informatie over deze functionaliteit, verwijs naar [ deze sectie ](../../platform/using/access-management-folders.md).

## Actieve profielen {#active-profiles}

Een actief profiel is een profiel waarmee de klant de afgelopen twaalf maanden via een willekeurig kanaal heeft geprobeerd te communiceren.

Volgens uw contract worden al uw Campaign-instanties ingericht met een specifieke hoeveelheid actieve profielen die voor factureringsdoeleinden worden geteld. Raadpleeg het meest recente contract voor informatie over het aantal aangeschafte actieve profielen. Leer meer in [ het productbeschrijving van Adobe Campaign ](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-campaign-managed-cloud-services.html) {target="_blank"}.

U kunt het aantal actieve profielen op uw instantie direct van het Controlebord van de Campagne controleren. Voor meer op dit, verwijs naar de [ documentatie van het Controlebord ](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html) {target="_blank"}.

De volgende instructies en beperkingen zijn van toepassing:

* Een profiel dat voor meerdere leveringen is bedoeld, wordt slechts eenmaal geteld.
* Profielen die zijn gericht in het kader van sociale marketing op X (Twitter) of Facebook, worden niet in aanmerking genomen als actieve profielen.
* De telling van actieve profielen is beschikbaar voor **Marketing instanties** slechts. Het is niet beschikbaar voor instanties van de Uitvoering, betekenend MID (midsourcing) en RT (het Centrum van het Bericht / Real-time overseinen) instanties.
* De telling is gebaseerd op de ontvankelijke primaire sleutel. Als een profiel aanwezig is in twee verschillende tabellen voor ontvangers, kan het daarom twee keer worden geteld als een actief profiel.


## Video over zelfstudie {#create-profiles-video}

Leer hoe u toegang krijgt tot profielgegevens, profielen kunt sorteren en filteren en profielen handmatig kunt maken en beheren.

In deze video wordt ook uitgelegd of Adobe Campaign Classic voldoet aan de algemene gegevensbeschermingsregels.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

De extra Campaign Classic hoe te video&#39;s zijn beschikbaar [ hier ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).

**zie ook**

* [ het beheer van de Privacy in Campagne ](https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html)

* [Vragen en segmentgegevens maken in workflows](../../workflow/using/targeting-data.md)

* [Doeltoewijzing selecteren](../../delivery/using/selecting-a-target-mapping.md)
