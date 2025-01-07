---
product: campaign
title: Schemaelementen en -kenmerken - paramelement
description: param, element
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 2%

---

# param, element {#param--element}


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

Met dit element kunt u een parameter definiëren voor het aanroepen van een SOAP.

## Beschrijving van kenmerk {#attribute-description-12}

* **desc (koord)**: beschrijving die het `<param>` element aangaat.
* **inout (koord)**: dit attribuut bepaalt al dan niet de parameter bij de input (in) of output (uit) van de SOAP vraag is. Als dit kenmerk niet wordt opgegeven, wordt de standaardparameter invoer (&quot;@inout=in&quot;).
* **etiket (koord)**: `<param>` etiket
* **localizable (koord)**: als het wordt geactiveerd, vertelt dit attribuut het inzamelingshulpmiddel om de waarde van het &quot;@label&quot;attribuut voor vertaling (intern gebruik) terug te krijgen.
* **naam (MNTOKEN)**: interne naam van `<param>`
* **type (koord)**: dit attribuut bepaalt het type van `<param>` element

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
