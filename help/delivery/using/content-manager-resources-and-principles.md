---
product: campaign
title: Bronnen en beginselen voor contentmanagement
description: Middelen en beginselen voor inhoudsbeheer
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Templates
role: User, Developer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 4%

---

# Bronnen en beginselen voor contentmanagement{#content-manager-resources-and-principles}


U moet een publicatiesjabloon definiëren dat transformatiesjablonen voor elke inhoud bevat.

Een inhoudsblok is gestructureerd in een XML-document voor gegevensopslag. Er wordt een bewerkingsinterface gebruikt om de inhoud in te voeren vanaf de Adobe Campaign-clientconsole of via een webbrowser. De inhoud kan ook automatisch worden ingevoerd via het vastleggen van XML-flow of gegevens die in een database zijn samengevoegd.

Wanneer u het XML-document en de XSL- of JavaScript-sjabloonopmaakmodellen combineert, wordt automatisch de projectie van de publicatiesjabloon in de verschillende indelingen (HTML, tekst) gegenereerd.

![](assets/d_ncs_content_process.png)

De volgende middelen worden vereist voor inhoudsconfiguratie:

* Gegevensschema&#39;s: beschrijving van de XML-inhoudsstructuur. Voor meer op dit, verwijs naar [ schema&#39;s van Gegevens ](data-schemas.md).
* Formulieren voor gegevensinvoer: constructie van gegevensinvoerschermen. Voor meer op dit, verwijs naar [ vormen van de Input ](input-forms.md).
* Afbeeldingen: afbeeldingen die worden gebruikt in formulieren voor gegevensinvoer. Voor meer op dit, verwijs naar [ beheer van het Beeld ](formatting.md#image-management).
* Stylesheets: opmaak van uitvoerdocumenten met XSLT-taal. Voor meer op dit, verwijs naar [ Formatterend ](formatting.md).
* JavaScript-sjablonen: opmaken van uitvoerdocumenten met de JavaScript-taal. Voor meer op dit, verwijs naar [ malplaatjes van de Publicatie ](publication-templates.md).
* JavaScript-codes: JavaScript-codes voor gegevensaggregatie. Voor meer op dit, verwijs naar [ Agregator ](publication-templates.md#aggregator).
* Publicatiesjablonen: definitie van publicatiesjablonen. Voor meer op dit, verwijs naar [ malplaatjes van de Publicatie ](publication-templates.md).
* Inhoud: instanties van inhoud die moeten worden gemaakt en gepubliceerd. Voor meer op dit, verwijs naar [ Gebruikend een inhoudsmalplaatje ](using-a-content-template.md).
