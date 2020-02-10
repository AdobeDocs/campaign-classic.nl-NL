---
title: Algemene vragen
seo-title: Algemene vragen
description: Klassieke veelgestelde vragen over campagne
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
translation-type: tm+mt
source-git-commit: 994ec35e37a1c26e83a8dd2ae31f6594cadd4c45

---


# Veelgestelde vragen over ontwikkelaars {#dev-faq}

Als open oplossing is Adobe Campaign gereed voor aanpassing en ontwikkeling van geavanceerde toepassingen.

## Wat is het gegevensmodel van de Campagne? {#what-is-the-campaign-data-model}

Het conceptuele gegevensmodel van de Adobe Campagne-database bestaat uit een set ingebouwde tabellen en hun interactie. De fysieke en logische structuur van de gegevens die in de toepassing worden overgedragen, wordt in XML beschreven. Het voert een grammatica specifiek voor de Campagne van Adobe uit, genoemd een schema. Raadpleeg [deze sectie](../../configuration/using/about-schema-edition.md)voor meer informatie over Adobe Campagne-schema&#39;s.

[Klik hier voor meer informatie over het datamodel](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)Campagne.

De beste praktijken worden vermeld [in dit artikel](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).

## Hoe te met de schema&#39;s van de Campagne werken? {#how-to-work-with-campaign-schemas-}

In de Campagne van Adobe, worden de gegevensschema&#39;s gebruikt om:

* Definieer hoe gegevensobjecten in de toepassing worden gekoppeld aan onderliggende databasetabellen.
* Definieer koppelingen tussen de verschillende gegevensobjecten in de Campagne-toepassing.
* Definieer en beschrijf de afzonderlijke velden die in elk object zijn opgenomen.

Lees uit de [Lijsten en schema&#39;s die beginnen](../../configuration/using/about-schema-edition.md) te begrijpen hoe te met gegevensschema werken, Campagne uitbreiden en aanpassen om aan uw behoeften te voldoen.

## Hoe te om een douane ontvankelijke lijst te gebruiken? {#how-to-use-a-custom-recipient-table-}

U kunt een niet-standaard ontvankelijke lijst in Campagne tot stand brengen en uitvoeren om uw berichten te verzenden.

[Klik hier voor meer informatie](../../configuration/using/about-custom-recipient-table.md)

## Wat zijn de beste praktijken om vragen in Campagne te bepalen? {#what-are-the-best-practices-to-define-queries-in-campaign-}

De de vraagredacteur van de Campagne van Adobe is een krachtig hulpmiddel om gegevens te onderzoeken en segmenten te bouwen.

U vindt het zoekprogramma voor Adobe Campagne op meerdere niveaus van de software: om een doelbevolking, segmentklanten, extract en filter het volgen logboeken te creëren, filters, enz. te bouwen.

U kunt het gegevensbestand van de Campagne vragen gebruikend de generische vraagredacteur. **U kunt deze openen via de query-editor** Gereedschappen > Algemeen... menu. Hiermee kunt u gegevens ophalen die in een database zijn opgeslagen, ordenen, groeperen, sorteren, enzovoort. De gebruiker kan bijvoorbeeld ontvangers herstellen die gedurende een bepaalde periode meer dan &#39;n keer op de koppeling van een nieuwsbrief hebben geklikt. Met dit gereedschap kunt u resultaten verzamelen, sorteren en weergeven op basis van uw behoeften. Met dit gereedschap kunt u alle mogelijkheden van Adobe Campagne onderzoeken. Zo kunt u bijvoorbeeld restrictiefilters maken en opslaan. Dit betekent dat een gebruikersfilter dat in de Algemene vraagredacteur wordt gecreeerd in het vakje van de Vraag van een het richten werkschema, enz. kan worden gebruikt.

Vragen worden gemaakt met velden uit de geselecteerde tabel of met een formule. De belangrijkste principes om een vraag op het gegevensbestand van de Campagne tot stand te brengen worden beschreven [in deze pagina](../../platform/using/about-queries-in-campaign.md).

[Klik hier](../../workflow/using/query.md) om de vraagredacteur van de Campagne te ontdekken.

## Hoe kan ik een gegevenspakket importeren? {#how-can-i-import-a-data-package-}

Met Adobe Campaign kunt u de platformconfiguratie en gegevens via een pakketsysteem exporteren of importeren. Met gegevenspakketten kunnen entiteiten van de Adobe Campagne-database worden weergegeven via bestanden in XML-indeling. Elke entiteit in een pakket wordt met al zijn gegevens vertegenwoordigd.

Gegevenspakketten bestaan uit het exporteren van een gegevensconfiguratie en het integreren van deze configuratie in een ander Adobe Campagne-systeem.

[Klik hier](../../platform/using/working-with-data-packages.md) om te leren hoe u met gegevenspakketten kunt werken om campagneconfiguraties te importeren en exporteren.

## Waar vind ik de lijst van Klassieke API&#39;s van de Campagne? {#where-can-i-find-the-list-of-campaign-classic-apis}

Alle campagne-API&#39;s, inclusief de volledige beschrijving, zijn beschikbaar in deze [specifieke documentatie](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).
