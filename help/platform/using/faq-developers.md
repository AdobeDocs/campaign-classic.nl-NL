---
title: Algemene vragen
seo-title: Algemene vragen
description: Veelgestelde vragen over Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 994ec35e37a1c26e83a8dd2ae31f6594cadd4c45
workflow-type: ht
source-wordcount: '528'
ht-degree: 100%

---


# Veelgestelde vragen voor ontwikkelaars {#dev-faq}

Als open oplossing is Adobe Campaign klaar voor aanpassing en implementatie van geavanceerde applicaties.

## Wat is het Campaign-datamodel? {#what-is-the-campaign-data-model}

Het conceptuele datamodel van de Adobe Campaign-database bestaat uit een reeks ingebouwde tabellen en hun interactie. De fysieke en logische structuur van de data die in de applicatie worden overgedragen, wordt in XML beschreven. Het volgt een grammatica die specifiek is voor Adobe Campaign en een schema wordt genoemd. Raadpleeg [deze sectie](../../configuration/using/about-schema-edition.md) voor meer informatie over Adobe Campaign-schema’s.

[Klik hier voor meer informatie over het Campaign-datamodel](https://helpx.adobe.com/nl/campaign/kb/acc-datamodel.html).

De best practices worden vermeld [in dit artikel](https://helpx.adobe.com/nl/campaign/kb/acc-data-model-best-practices.html).

## Hoe kan ik werken met Campaign-schema’s? {#how-to-work-with-campaign-schemas-}

In Adobe Campaign worden dataschema’s gebruikt om het volgende te doen:

* Definiëren hoe dataobjecten in de applicatie worden gekoppeld aan onderliggende databasetabellen.
* Definiëren van koppelingen tussen de verschillende dataobjecten in de Campaign-applicatie.
* Definiëren en beschrijven van de afzonderlijke velden die in elk object zijn opgenomen.

Lees de [handleiding om aan de slag te gaan met tabellen en schema’s](../../configuration/using/about-schema-edition.md) om te begrijpen hoe u met een dataschema kunt werken en hoe u Campaign kunt uitbreiden en aanpassen om aan uw behoeften te voldoen.

## Hoe kan ik een aangepaste ontvangerstabel gebruiken? {#how-to-use-a-custom-recipient-table-}

U kunt een niet-standaard ontvangerstabel in Campaign maken en implementeren om uw berichten te verzenden.

[Klik hier voor meer informatie](../../configuration/using/about-custom-recipient-table.md)

## Wat zijn de best practices om query’s in Campaign te definiëren? {#what-are-the-best-practices-to-define-queries-in-campaign-}

De query-editor van Adobe Campaign is een krachtige tool om data te onderzoeken en segmenten te bouwen.

U vindt de Adobe Campaign-querytool op meerdere niveaus van de software: om een doelpopulatie te maken, klanten te segmenteren, trackinglogboeken te extraheren en filteren, filters te bouwen, enzovoort.

U kunt query’s uitvoeren op de Campaign-database met behulp van de generieke query-editor. U kunt deze openen via het menu **Tools > Generic query editor...**. Hiermee kunt u gegevens ophalen die in een database zijn opgeslagen en deze gegevens ordenen, groeperen, sorteren, enzovoort. De gebruiker kan bijvoorbeeld ontvangers ophalen die gedurende een bepaalde periode meer dan ‘n’ keer op de koppeling van een nieuwsbrief hebben geklikt. Met deze tool kunt u resultaten verzamelen, sorteren en weergeven op basis van uw behoeften. Met deze tool combineert u alle querymogelijkheden van Adobe Campaign. Zo kunt u bijvoorbeeld beperkingsfilters maken en opslaan. Dit betekent dat een gebruikersfilter dat in de generieke query-editor is gemaakt, in het vakje Query van een targetingworkflow, enzovoort, kan worden gebruikt.

Query’s worden gemaakt met velden uit de geselecteerde tabel of met een formule. De belangrijkste principes om een query op de Campaign-database te maken, worden beschreven [op deze pagina](../../platform/using/about-queries-in-campaign.md).

[Klik hier](../../workflow/using/query.md) om meer te weten te komen over de query-editor van Campaign.

## Hoe kan ik een datapakket importeren? {#how-can-i-import-a-data-package-}

Met Adobe Campaign kunt u de platformconfiguratie en data via een pakketsysteem exporteren of importeren. Met datapakketten kunnen entiteiten van de Adobe Campaign-database worden weergegeven via bestanden in XML-indeling. Elke entiteit in een pakket wordt met al zijn data vertegenwoordigd.

Het principe van datapakketten is een dataconfiguratie te exporteren en deze in een ander Adobe Campaign-systeem te integreren.

[Klik hier](../../platform/using/working-with-data-packages.md) om te leren hoe u met datapakketten kunt werken om Campaign-configuraties te importeren en exporteren.

## Waar vind ik de lijst met Campaign Classic-API’s? {#where-can-i-find-the-list-of-campaign-classic-apis}

Alle Campaign-API’s, inclusief de volledige beschrijving, zijn beschikbaar in deze [specifieke documentatie](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).
