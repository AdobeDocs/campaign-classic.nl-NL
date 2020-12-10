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
source-wordcount: '453'
ht-degree: 1%

---


# `<srcschema>` element  {#srcschema--element}

## Inhoudsmodel {#content-model-14}

srcSchema:==(kenmerk | gemaaktDoor | Gegevens | element | opsomming | Help | interface | Methode | gewijzigdDoor)

## Kenmerken {#attributes-14}

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

`<srcschema>` is het wortelelement van een schema. Dit is het invoerpunt voor de definitie van het schema.

## Gebruik en gebruikscontext {#use-and-context-of-use-9}

Schemapresentatie is beschikbaar in [Schemenverwijzing](../../configuration/using/about-schema-reference.md) en [Schemastructuur](../../configuration/using/schema-structure.md).

## Kenmerkbeschrijving {#attribute-description-14}

* **gemaakt (datetime)**: this attribute provided information on the date and time of schema creation. Het heeft een formulier &#39;Datum en tijd&#39;. De weergegeven waarden worden opgehaald van de server. De tijd wordt getoond in formaat UTC.
* **createdBy-id (long)**: is het herkenningsteken van de exploitant die het schema creeerde.
* **desc (tekenreeks)**: schemabeschrijving
* **entiteitSchema (tekenreeks)**: basisschema waarop syntaxis en goedkeuring zijn gebaseerd (standaard voor Adobe Campaign: xtk:srcSchema). Wanneer u het huidige schema opslaat, zal Adobe Campaign zijn grammatica met het schema goedkeuren dat in de @xtkschema attributen wordt verklaard.
* **extendedSchema (tekenreeks)**: ontvangt de naam van het out-of-the-box schema waarop de huidige schemauitbreiding gebaseerd is. Het formulier is &quot;namespace:name&quot;.
* **img (tekenreeks)**: pictogram gekoppeld aan het schema (kan worden gedefinieerd in de wizard Schema maken).
* **label (tekenreeks)**: schemalabel.
* **labelSingular (string)**: label (enkelvoudig) voor weergave in de interface.
* **lastModified (datetime)**: this attribute provided information on the date and time of the last modification. Het heeft een formulier &#39;Datum en tijd&#39;. De weergegeven waarden worden opgehaald van de server. De tijd wordt getoond in formaat UTC.
* **bibliotheek (Booleaans)**: gebruik van het schema als bibliotheek en niet als entiteit. Naar dit schema kan daarom door andere schema&#39;s worden verwezen dankzij de kenmerken &quot;@ref&quot; en &quot;@template&quot;.
* **mappingType (tekenreeks)**:

   * &quot;sql&quot;: databasetoewijzing
   * &quot;textFile&quot;: tekstbestandstoewijzing
   * &quot;xmlFile&quot;: XML-bestandstoewijzing
   * &quot;binaryFile&quot;: binaire bestandstoewijzing

* **modifiedBy-id (long)**: komt overeen met de id van de operator die het schema heeft gewijzigd.
* **name (string)**: unieke schemanaam.
* **naamruimte (tekenreeks)**: naamruimte van het schema (standaard: nms, xtk, nl). Wanneer het creëren van een nieuw schema voor een project, adviseren wij dat u specifieke namespace gebruikt.
* **useRecycleBin (Boolean)**: Hiermee activeert u de prullenbak-functie in de toepassing. Verwijderde records worden in de prullenbak geplaatst voordat ze definitief worden verwijderd. Deze functie is alleen beschikbaar in de modus &quot;Aflevering&quot;.
* **weergave (Booleaans)**: als het wordt geactiveerd (@view=&quot;waar&quot;), zal het schema als mening worden gebruikt. De updatewizard voor de databasestructuur houdt geen rekening met het schema. Deze optie wordt vooral gebruikt voor het verwijzen naar externe tabellen.
* **xtkschema (tekenreeks)**: naam van het schema dat schema grammatica bepaalt (xtk:srcSchema door gebrek).

## Voorbeelden {#examples-11}

`<srcschema>` element of the &quot;nms:delivery&quot; out of the box schema

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
