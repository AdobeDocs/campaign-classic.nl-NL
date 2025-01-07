---
product: campaign
title: Schemaelementen en -kenmerken - sleutelveldelement
description: sleutelveldelement
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 1%

---

# sleutelveldelement {#keyfield--element}


## Inhoudsmodel {#content-model-9}

keyfield:==EMPTY

## Attributen {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Ouders {#parents-9}

`<key>` , `<dbindex />`

## Kinderen {#children-9}

Geen

## Beschrijving {#description-9}

Dit element definieert de velden die moeten worden geïntegreerd in een index of een sleutel.

## Beschrijving van kenmerk {#attribute-description-9}

* **xlink (MNTOKEN)**: laat u automatisch buitenlandse sleutels van verwijzingen voorzien die in toetreden voor een relatietabel (N-N verbinding) worden bepaald.
* **xpath (MNTOKEN)**: definitie van een index of een sleutel op een `<attribute>` element. Dit kenmerk ontvangt een Xpath dat het pad naar het schemakenmerk definieert dat de sleutel of de index definieert.

## Voorbeelden {#examples-}

Selectie van het veld &#39;sName&#39; in een index met een Xpath-bewerking voor &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
