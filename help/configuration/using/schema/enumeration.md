---
product: campaign
title: Schema-elementen en -kenmerken - opsommingselement
description: opsommingselement
feature: Schema Extension
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---

# opsommingselement {#enumeration--element}


## Inhoudsmodel {#content-model-5}

opsomming:==(help| waarde)

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

* **basetype (koord)**: type van de waarden die in de opsomming worden opgeslagen.

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

* **gebrek (koord)**: Standaardwaarde. De standaardwaarde kan ook een van de waarden zijn die in de opsomming worden gedefinieerd.
* **desc (koord)**: opsommingsbeschrijving.
* **etiket (koord)**: opsommingsetiket.
* **naam (koord)**: interne naam van de opsomming.
* **malplaatje (koord)**: dit attribuut bepaalt een verwijzing naar een `<enumeration>` element dat door verscheidene schema&#39;s wordt gedeeld. De definitie wordt automatisch gekopieerd naar het huidige schema.

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
