---
product: campaign
title: Schema-elementen en -kenmerken - opsommingselement
description: opsommingselement
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---

# opsommingselement {#enumeration--element}

![](../../../assets/v7-only.svg)

## Inhoudsmodel {#content-model-5}

opsomming:==(help| value)

## Attributen {#attributes-5}

* @basetype (tekenreeks)
* @default (tekenreeks)
* @desc (tekenreeks)
* @label (tekenreeks)
* @name (tekenreeks)
* @template (tekenreeks)

## Ouders {#parents-5}

`<srcschema>`

## Kinderen {#children-5}

* `<help>`
* `<value>`

## Beschrijving {#description-5}

Met dit element kunnen we een waardenopsomming definiëren. Een opsomming behoort tot het schema waarin het wordt bepaald, maar het is toegankelijk via een ander schema.

## Gebruik en gebruikscontext {#use-and-context-of-use-4}

Opsommingen worden gedefinieerd aan het begin van een schema (voordat het hoofdelement wordt gedefinieerd).

## Beschrijving van kenmerk {#attribute-description-5}

* **basetype (string)**: type van de waarden die in de opsomming zijn opgeslagen.

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

* **default (string)**: Standaardwaarde. De standaardwaarde kan ook een van de waarden zijn die in de opsomming worden gedefinieerd.
* **desc (tekenreeks)**: opsommingsbeschrijving.
* **label (tekenreeks)**: opsommingslabel.
* **name (string)**: interne naam van de opsomming.
* **sjabloon (tekenreeks)**: this attribute define a reference to an `<enumeration>` element dat door verscheidene schema&#39;s wordt gedeeld. De definitie wordt automatisch gekopieerd naar het huidige schema.

## Voorbeelden {#examples-4}

Voorbeeld van opsommingswaarden waarvan de waarden in de database worden opgeslagen:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Definitie van een opsomming met standaardwaarde:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
