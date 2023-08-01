---
product: campaign
title: Schemaelementen en -kenmerken - sleutelveldelement
description: sleutelveldelement
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 1%

---

# sleutelveldelement {#keyfield--element}

![](../../../assets/v7-only.svg)

## Inhoudsmodel {#content-model-9}

keyfield:==EMPTY

## Attributen {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Ouders {#parents-9}

`<key>`  ,  `<dbindex />`

## Kinderen {#children-9}

Geen

## Beschrijving {#description-9}

Dit element definieert de velden die moeten worden geïntegreerd in een index of een sleutel.

## Beschrijving van kenmerk {#attribute-description-9}

* **xlink (MNTOKEN)**: Hiermee kunt u automatisch verwijzen naar externe sleutels die in de samenvoeging zijn gedefinieerd voor een relatietabel (N-N koppeling).
* **xpath (MNTOKEN)**: definitie van een index of een toets op een `<attribute>`  element. Dit kenmerk ontvangt een Xpath dat het pad naar het schemakenmerk definieert dat de sleutel of de index definieert.

## Voorbeelden {#examples-}

Selectie van het veld &#39;sName&#39; in een index met een Xpath-element op &#39;@name&#39;:

```
<keyfield xpath="@name"/>
```
