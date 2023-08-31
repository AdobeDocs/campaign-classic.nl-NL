---
product: campaign
title: Bronnen en beginselen voor contentmanagement
description: Middelen en beginselen voor inhoudsbeheer
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Templates
role: User, Developer, Data Engineer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 4%

---

# Bronnen en beginselen voor contentmanagement{#content-manager-resources-and-principles}


U moet een publicatiesjabloon definiëren dat transformatiesjablonen voor elke inhoud bevat.

Een inhoudsblok is gestructureerd in een XML-document voor gegevensopslag. Er wordt een bewerkingsinterface gebruikt om de inhoud in te voeren vanaf de Adobe Campaign-clientconsole of via een webbrowser. De inhoud kan ook automatisch worden ingevoerd via het vastleggen van XML-flow of gegevens die in een database zijn samengevoegd.

Wanneer u het XML-document en de XSL- of JavaScript-sjabloonopmaakmodellen combineert, wordt automatisch de projectie van de publicatiesjabloon in de verschillende indelingen (HTML, tekst) gegenereerd.

![](assets/d_ncs_content_process.png)

De volgende middelen worden vereist voor inhoudsconfiguratie:

* Gegevensschema&#39;s: beschrijving van de XML-inhoudsstructuur. Raadpleeg voor meer informatie hierover [Gegevensschema&#39;s](data-schemas.md).
* Formulieren voor gegevensinvoer: constructie van gegevensinvoerschermen. Raadpleeg voor meer informatie hierover [Invoerformulieren](input-forms.md).
* Afbeeldingen: afbeeldingen die worden gebruikt in formulieren voor gegevensinvoer. Raadpleeg voor meer informatie hierover [Afbeeldingsbeheer](formatting.md#image-management).
* Stylesheets: opmaak van uitvoerdocumenten met XSLT-taal. Raadpleeg voor meer informatie hierover [Opmaak](formatting.md).
* JavaScript-sjablonen: opmaak van uitvoerdocumenten met JavaScript. Raadpleeg voor meer informatie hierover [Publicatiesjablonen](publication-templates.md).
* JavaScript-codes: JavaScript-codes voor gegevensaggregatie. Raadpleeg voor meer informatie hierover [aggregator](publication-templates.md#aggregator).
* Publicatiesjablonen: definitie van publicatiesjablonen. Raadpleeg voor meer informatie hierover [Publicatiesjablonen](publication-templates.md).
* Inhoud: instanties van inhoud die moeten worden gemaakt en gepubliceerd. Raadpleeg voor meer informatie hierover [Een inhoudssjabloon gebruiken](using-a-content-template.md).
