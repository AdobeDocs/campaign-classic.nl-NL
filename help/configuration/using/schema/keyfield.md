---
solution: Campaign Classic
product: campaign
title: Elementen en kenmerken
description: Elementen en kenmerken
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 8%

---


# `<keyfield>` element  {#keyfield--element}

## Inhoudsmodel {#content-model-9}

keyfield:==EMPTY

## Kenmerken {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Ouders {#parents-9}

`<key>`  ,  `<dbindex />`

## Kinderen {#children-9}

Geen

## Beschrijving {#description-9}

Dit element definieert de velden die moeten worden geïntegreerd in een index of een sleutel.

## Kenmerkbeschrijving {#attribute-description-9}

* **xlink (MNTOKEN)**: Hiermee kunt u automatisch verwijzen naar externe sleutels die zijn gedefinieerd in de samenvoeging voor een relatietabel (N-N koppeling).
* **xpath (MNTOKEN)**: definitie van een index of een sleutel op een  `<attribute>`  element. Dit kenmerk ontvangt een Xpath dat het pad naar het schemakenmerk definieert dat de sleutel of de index definieert.

## Voorbeelden {#examples-}

Selectie van het veld &#39;sName&#39; in een index met een Xpath-element op &#39;@name&#39;:

```
<keyfield xpath="@name"/>
```
