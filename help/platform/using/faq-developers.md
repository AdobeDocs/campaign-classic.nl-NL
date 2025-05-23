---
product: campaign
title: Veelgestelde vragen over ontwikkelaars
description: Veelgestelde vragen over ontwikkelaars
feature: Troubleshooting, Configuration
audience: platform
content-type: reference
level: Intermediate, Experienced
topic-tags: starting-with-adobe-campaign
exl-id: 20552812-5c58-4d48-9636-d5135197685d
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 84%

---

# Veelgestelde vragen over ontwikkelaars {#dev-faq}



Als open oplossing is Adobe Campaign klaar voor aanpassing en implementatie van geavanceerde applicaties.

## Wat is het gegevensmodel van de Campagne? {#what-is-the-campaign-data-model}

Het conceptuele datamodel van de Adobe Campaign-database bestaat uit een reeks ingebouwde tabellen en hun interactie. De fysieke en logische structuur van de data die in de applicatie worden overgedragen, wordt in XML beschreven. Het volgt een grammatica die specifiek is voor Adobe Campaign en een schema wordt genoemd. Raadpleeg [deze sectie](../../configuration/using/about-schema-edition.md) voor meer informatie over Adobe Campaign-schema’s.

[ klik hier om meer over het gegevensmodel van de Campagne ](https://helpx.adobe.com/nl/campaign/kb/acc-datamodel.html) te leren.

De best practices worden vermeld [in dit artikel](../../configuration/using/data-model-best-practices.md).

## Hoe te met de schema&#39;s van de Campagne werken? {#how-to-work-with-campaign-schemas-}

In Adobe Campaign worden dataschema’s gebruikt om het volgende te doen:

* Definiëren hoe dataobjecten in de applicatie worden gekoppeld aan onderliggende databasetabellen.
* Definiëren van koppelingen tussen de verschillende dataobjecten in de Campaign-applicatie.
* Definiëren en beschrijven van de afzonderlijke velden die in elk object zijn opgenomen.

Lees de [handleiding om aan de slag te gaan met tabellen en schema’s](../../configuration/using/about-schema-edition.md) om te begrijpen hoe u met een dataschema kunt werken en hoe u Campaign kunt uitbreiden en aanpassen om aan uw behoeften te voldoen.

## Hoe te om een douane ontvankelijke lijst te gebruiken? {#how-to-use-a-custom-recipient-table-}

U kunt een niet-ingebouwde ontvankelijke lijst in Campagne tot stand brengen en uitvoeren om uw berichten te verzenden.

[Klik hier voor meer informatie](../../configuration/using/about-custom-recipient-table.md)

## Wat zijn de beste praktijken om vragen in Campagne te bepalen? {#what-are-the-best-practices-to-define-queries-in-campaign-}

De query-editor van Adobe Campaign is een krachtige tool om data te onderzoeken en segmenten te bouwen.

U vindt de Adobe Campaign-querytool op meerdere niveaus van de software: om een doelpopulatie te maken, klanten te segmenteren, trackinglogboeken te extraheren en filteren, filters te bouwen, enzovoort.

U kunt query’s uitvoeren op de Campaign-database met behulp van de generieke query-editor. U kunt deze openen via het menu **Tools > Generic query editor...**. Hiermee kunt u gegevens ophalen die in een database zijn opgeslagen en deze gegevens ordenen, groeperen, sorteren, enzovoort. De gebruiker kan bijvoorbeeld ontvangers ophalen die gedurende een bepaalde periode meer dan ‘n’ keer op de koppeling van een nieuwsbrief hebben geklikt. Met deze tool kunt u resultaten verzamelen, sorteren en weergeven op basis van uw behoeften. Met deze tool combineert u alle querymogelijkheden van Adobe Campaign. Zo kunt u bijvoorbeeld beperkingsfilters maken en opslaan. Dit betekent dat een gebruikersfilter dat in de generieke query-editor is gemaakt, in het vakje Query van een targetingworkflow, enzovoort, kan worden gebruikt.

Query’s worden gemaakt met velden uit de geselecteerde tabel of met een formule. De belangrijkste principes om een query op de Campaign-database te maken, worden beschreven [op deze pagina](../../platform/using/about-queries-in-campaign.md).

[Klik hier](../../workflow/using/query.md) om meer te weten te komen over de query-editor van Campaign.

## Hoe kan ik een gegevenspakket importeren? {#how-can-i-import-a-data-package-}

Met Adobe Campaign kunt u de platformconfiguratie en data via een pakketsysteem exporteren of importeren. Met datapakketten kunnen entiteiten van de Adobe Campaign-database worden weergegeven via bestanden in XML-indeling. Elke entiteit in een pakket wordt met al zijn data vertegenwoordigd.

Het principe van datapakketten is een dataconfiguratie te exporteren en deze in een ander Adobe Campaign-systeem te integreren.

[Klik hier](../../platform/using/working-with-data-packages.md) om te leren hoe u met datapakketten kunt werken om Campaign-configuraties te importeren en exporteren.

## Waar vind ik de lijst met Campaign Classic API&#39;s? {#where-can-i-find-the-list-of-campaign-classic-apis}

Alle Campaign-API’s, inclusief de volledige beschrijving, zijn beschikbaar in deze [specifieke documentatie](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=nl).
