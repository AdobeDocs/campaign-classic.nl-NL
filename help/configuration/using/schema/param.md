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
source-wordcount: '174'
ht-degree: 6%

---


# `<param>` element  {#param--element}

## Inhoudsmodel {#content-model-12}

param:==help

## Kenmerken {#attributes-12}

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

## Kenmerkbeschrijving {#attribute-description-12}

* **desc (tekenreeks)**: beschrijving die betrekking heeft op het  `<param>` element.
* **inout (tekenreeks)**: this attribute define whether or not the parameter is at the input (in) or output (out) of the SOAP call. Als dit kenmerk niet wordt opgegeven, wordt de standaardparameter invoer (&quot;@inout=in&quot;).
* **label (tekenreeks)**:  `<param>` label
* **localizable (tekenreeks)**: Als dit kenmerk is geactiveerd, geeft dit het gereedschap Verzameling de opdracht om de waarde van het kenmerk &quot;@label&quot; te herstellen voor vertaling (intern gebruik).
* **naam (MNTOKEN)**: interne naam van de  `<param>`
* **type (tekenreeks)**: this attribute define the type of  `<param>` element

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
   * primarykey
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
