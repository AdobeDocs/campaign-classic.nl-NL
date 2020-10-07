---
title: Resources en beginselen voor contentmanagement
seo-title: Resources en beginselen voor contentmanagement
description: Resources en beginselen voor contentmanagement
seo-description: null
page-status-flag: never-activated
uuid: 3560e392-129a-471d-a211-05481cdda224
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: b22b3abb-6fe5-4f4d-93fc-0d00d426edb6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 8%

---


# Resources en beginselen voor contentmanagement{#content-manager-resources-and-principles}

U moet een publicatiesjabloon definiëren dat transformatiesjablonen voor elke inhoud bevat.

Een inhoudsblok is gestructureerd in een XML-document voor gegevensopslag. Er wordt een bewerkingsinterface gebruikt om de inhoud in te voeren vanaf de Adobe Campaign-clientconsole of via een webbrowser. De inhoud kan ook automatisch worden ingevoerd via het vastleggen van XML-flow of gegevens die in een database zijn samengevoegd.

Wanneer u het XML-document en de XSL- of JavaScript-sjabloonopmaakmodellen combineert, wordt automatisch de projectie van de publicatiesjabloon in de verschillende indelingen (HTML, tekst) gegenereerd.

![](assets/d_ncs_content_process.png)

De volgende middelen worden vereist voor inhoudsconfiguratie:

* Gegevensschema&#39;s: beschrijving van de XML-inhoudsstructuur. For more on this, refer to [Data schemas](../../delivery/using/data-schemas.md).
* Formulieren voor gegevensinvoer: bouw van gegevensinvoerschermen. For more on this, refer to [Input forms](../../delivery/using/input-forms.md).
* Afbeeldingen: afbeeldingen die worden gebruikt in formulieren voor gegevensinvoer. For more on this, refer to [Image management](../../delivery/using/formatting.md#image-management).
* Stylesheets: opmaak van uitvoerdocumenten met XSLT-taal. For more on this, refer to [Formatting](../../delivery/using/formatting.md).
* JavaScript-sjablonen: opmaak van uitvoerdocumenten met gebruik van JavaScript-taal. For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* JavaScript-codes: JavaScript-codes voor gegevensaggregatie. For more on this, refer to [Aggregator](../../delivery/using/publication-templates.md#aggregator).
* Publicatiesjablonen: definitie van publicatiesjablonen. For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* Inhoud: te maken en te publiceren inhoudsinstanties. Raadpleeg [Een inhoudssjabloon](../../delivery/using/using-a-content-template.md)gebruiken voor meer informatie.
