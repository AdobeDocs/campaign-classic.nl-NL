---
product: campaign
title: Schemaelementen en -kenmerken - paramelement
description: param, element
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 2%

---

# param, element {#param--element}

![](../../../assets/v7-only.svg)

## Inhoudsmodel {#content-model-12}

param:==help

## Attributen {#attributes-12}

* @_operation (tekenreeks)
* @desc (tekenreeks)
* @enum (tekenreeks)
* @inout (tekenreeks)
* @label (tekenreeks)
* @localizable (tekenreeks)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (tekenreeks)

## Ouders {#parents-12}

`<parameters>`

## Kinderen {#children-12}

`<help>`

## Beschrijving {#description-12}

Met dit element kunt u een parameter definiëren voor het aanroepen van een SOAP-methode.

## Beschrijving van kenmerk {#attribute-description-12}

* **desc (tekenreeks)**: beschrijving die betrekking heeft op de `<param>` element.
* **inout (tekenreeks)**: dit kenmerk definieert of de parameter zich bij de invoer (in) of uitvoer (uit) van de SOAP-aanroep bevindt. Als dit kenmerk niet wordt opgegeven, wordt de standaardparameter invoer (&quot;@inout=in&quot;).
* **label (tekenreeks)**: `<param>` label
* **localizable (tekenreeks)**: als dit kenmerk is geactiveerd, geeft dit kenmerk het gereedschap Verzameling de waarde van het kenmerk &quot;@label&quot; voor vertaling (intern gebruik) weer.
* **naam (MNTOKEN)**: interne naam van de `<param>`
* **type (tekenreeks)**: dit kenmerk definieert het type van `<param>` element

  Lijst met beschikbare typen:

   * ALLE
   * bin
   * opblazen
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * double
   * enum
   * zweven
   * html
   * int64
   * link
   * lang
   * memo
   * MNTOKEN
   * procent
   * primaire sleutel
   * kort
   * string
   * tijd
   * timespan
   * uuid

## Voorbeelden {#examples-9}

Definitie van de inkomende instelling &quot;serviceName&quot; van het tekenreekstype:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
