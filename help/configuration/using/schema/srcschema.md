---
product: campaign
title: Elementen en kenmerken - schema-element
description: Elementen en kenmerken
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# srcschema-element {#srcschema--element}

![](../../../assets/v7-only.svg)

## Inhoudsmodel {#content-model-14}

srcSchema:==(kenmerk | createdBy | data | element | opsomming | help | interface | methoden | modifiedBy)

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

`<srcschema>` is het hoofdelement van een schema. Dit is het invoerpunt voor de definitie van het schema.

## Gebruik en gebruikscontext {#use-and-context-of-use-9}

De presentatie van het schema is beschikbaar in [ Ongeveer schemaverwijzing ](../../../configuration/using/about-schema-reference.md) en [ structuur van het Schema ](../../../configuration/using/schema-structure.md).

## Beschrijving van kenmerk {#attribute-description-14}

* **gecreeerd (datetime)**: dit attribuut verstrekt informatie over de datum en de tijd van schemaverwezenlijking. Het heeft een formulier Datum en tijd. De weergegeven waarden worden opgehaald van de server. De tijd wordt getoond in formaat UTC.
* **createdBy-id (lang)**: is het herkenningsteken van de exploitant die het schema creeerde.
* **desc (koord)**: schemabeschrijving
* **entitySchema (koord)**: basisschema dat de syntaxis en de goedkeuring op (door gebrek voor Adobe Campaign: xtk:srcSchema) gebaseerd zijn. Wanneer u het huidige schema opslaat, zal Adobe Campaign zijn grammatica met het schema goedkeuren dat in de @xtkschema attributen wordt verklaard.
* **extendedSchema (koord)**: ontvangt de naam van het out-of-the-box schema dat de huidige schemaversie op gebaseerd is. Het formulier is &quot;namespace:name&quot;.
* **img (koord)**: pictogram verbonden aan het schema (kan in de medewerker van de schemaverwezenlijking worden bepaald).
* **etiket (koord)**: schemalabel.
* **labelSingular (koord)**: etiket (enkelvoudig) voor vertoning in de interface.
* **lastModified (datetime)**: dit attribuut verstrekt informatie over de datum en de tijd van de laatste wijziging. Het heeft een formulier Datum en tijd. De weergegeven waarden worden opgehaald van de server. De tijd wordt getoond in formaat UTC.
* **bibliotheek (boolean)**: gebruik van het schema als bibliotheek en niet een entiteit. Naar dit schema kan daarom door andere schema&#39;s worden verwezen dankzij de kenmerken &quot;@ref&quot; en &quot;@template&quot;.
* **mappingType (koord)**:

   * &quot;sql&quot;: databasetoewijzing
   * &quot;textFile&quot;: toewijzing van tekstbestand
   * &quot;xmlFile&quot;: tekstbestandstoewijzing in XML-indeling
   * &quot;binaryFile&quot;: binaire bestandstoewijzing

* **modifiedBy-id (long)**: past het herkenningsteken van de exploitant aan die het schema veranderde.
* **naam (koord)**: unieke schemanaam.
* **namespace (koord)**: namespace van het schema (gebrek: nms, xtk, nl). Wanneer het creëren van een nieuw schema voor een project, adviseren wij dat u specifieke namespace gebruikt.
* **useRecycleBin (boolean)**: activeert de vuileigenschap in de toepassing. Verwijderde records worden in de prullenbak geplaatst voordat ze definitief worden verwijderd. Deze functie is alleen beschikbaar in de modus &quot;Aflevering&quot;.
* **mening (boolean)**: als het (@view= &quot;waar&quot;) wordt geactiveerd, zal het schema als mening worden gebruikt. De update-assistent voor de databasestructuur houdt geen rekening met het schema. Deze optie wordt vooral gebruikt voor het verwijzen naar externe tabellen.
* **xtkschema (koord)**: naam van het schema dat schema grammatica (xtk bepaalt:srcSchema door gebrek).

## Voorbeelden {#examples-11}

`<srcschema>` -element van het &quot;nms:delivery&quot;-element uit het kaderschema

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
