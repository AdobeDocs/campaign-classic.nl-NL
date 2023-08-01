---
product: campaign
title: Elementen en kenmerken - schema-element
description: Elementen en kenmerken
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# srcschema-element {#srcschema--element}

![](../../../assets/v7-only.svg)

## Inhoudsmodel {#content-model-14}

srcSchema:==(kenmerk | gemaaktDoor | Gegevens | element | Opsomming | Help | interface | Methode | gewijzigdDoor)

## Attributen {#attributes-14}

gemaakt (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string); namespace (tekenreeks), useRecycleBin (Boolean), view (boolean), xtkschema (tekenreeks)

## Ouders {#parents-14}

Geen

## Kinderen {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## Beschrijving {#description-14}

De `<srcschema>` is het hoofdelement van een schema. Dit is het invoerpunt voor de definitie van het schema.

## Gebruik en gebruikscontext {#use-and-context-of-use-9}

Schemapresentatie is beschikbaar in [Schema-verwijzing](../../../configuration/using/about-schema-reference.md) en [Schema-structuur](../../../configuration/using/schema-structure.md).

## Beschrijving van kenmerk {#attribute-description-14}

* **gemaakt (datetime)**: dit kenmerk biedt informatie over de datum en tijd waarop het schema wordt gemaakt. Het heeft een formulier Datum en tijd. De weergegeven waarden worden opgehaald van de server. De tijd wordt getoond in formaat UTC.
* **createdBy-id (long)**: is de id van de operator die het schema heeft gemaakt.
* **desc (tekenreeks)**: schemabeschrijving
* **entiteitSchema (tekenreeks)**: basisschema waarop syntaxis en goedkeuring zijn gebaseerd (standaard voor Adobe Campaign: xtk:srcSchema). Wanneer u het huidige schema opslaat, zal Adobe Campaign zijn grammatica met het schema goedkeuren dat in de @xtkschema attributen wordt verklaard.
* **extendedSchema (tekenreeks)**: ontvangt de naam van het out-of-the-box schema waarop de huidige schemauitbreiding is gebaseerd. Het formulier is &quot;namespace:name&quot;.
* **img (tekenreeks)**: pictogram dat is gekoppeld aan het schema (kan worden gedefinieerd in de wizard Schema maken).
* **label (tekenreeks)**: schema label.
* **labelSingular (string)**: label (enkelvoudig) voor weergave in de interface.
* **lastModified (datetime)**: dit kenmerk biedt informatie over de datum en het tijdstip van de laatste wijziging. Het heeft een formulier Datum en tijd. De weergegeven waarden worden opgehaald van de server. De tijd wordt getoond in formaat UTC.
* **bibliotheek (Boolean)**: gebruik van het schema als bibliotheek en niet als entiteit. Naar dit schema kan daarom door andere schema&#39;s worden verwezen dankzij de kenmerken &quot;@ref&quot; en &quot;@template&quot;.
* **mappingType (tekenreeks)**:

   * &quot;sql&quot;: databasetoewijzing
   * &quot;textFile&quot;: toewijzing van tekstbestand
   * &quot;xmlFile&quot;: tekstbestandstoewijzing in XML-indeling
   * &quot;binaryFile&quot;: binaire bestandstoewijzing

* **modifiedBy-id (long)**: komt overeen met de id van de operator die het schema heeft gewijzigd.
* **name (string)**: unieke schemanaam.
* **namespace (tekenreeks)**: naamruimte van het schema (standaard: nms, xtk, nl). Wanneer het creëren van een nieuw schema voor een project, adviseren wij dat u specifieke namespace gebruikt.
* **useRecycleBin (Boolean)**: activeert de prullenbak-functie in de toepassing. Verwijderde records worden in de prullenbak geplaatst voordat ze definitief worden verwijderd. Deze functie is alleen beschikbaar in de modus &quot;Aflevering&quot;.
* **weergave (Boolean)**: als het is geactiveerd (@view=&quot;true&quot;), wordt het schema gebruikt als weergave. De updatewizard voor de databasestructuur houdt geen rekening met het schema. Deze optie wordt vooral gebruikt voor het verwijzen naar externe tabellen.
* **xtkschema (tekenreeks)**: naam van het schema dat schema grammatica (xtk:srcSchema door gebrek) bepaalt.

## Voorbeelden {#examples-11}

`<srcschema>` element of the &quot;nms:delivery&quot; out of the box schema

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
