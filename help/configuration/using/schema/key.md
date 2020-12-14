---
solution: Campaign Classic
product: campaign
title: Elementen en kenmerken
description: Elementen en kenmerken
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 2%

---


# hoofdelement {#key--element}

## Inhoudsmodel {#content-model-8}

key:==keyfield

## Kenmerken {#attributes-8}

* @allowEmptyPart (boolean)
* @applicableIf (tekenreeks)
* @internal (boolean)
* @label (tekenreeks)
* @name (MNTOKEN)
* @noDbIndex (boolean)

## Ouders {#parents-8}

`<element>`

## Kinderen {#children-8}

`<keyfield>`

## Beschrijving {#description-8}

Met dit element kunt u een sleutel definiëren voor het identificeren van een record in de tabel.

Een tabel moet minstens één sleutel hebben.

## Gebruik en gebruikscontext {#use-and-context-of-use-6}

Normaliter worden toetsen gedeclareerd na het hoofdelement van het schema en de indexen.

Een sleutel wordt bekend als een samengestelde sleutel als deze verschillende velden bevat (d.w.z. verschillende `<keyfield>` onderliggende items). Gebruik geen samengestelde sleutel om een primaire sleutel te definiëren.

Als het hoofdelement van het schema het kenmerk &quot;@autopk=true&quot; bevat, is de primaire sleutel uniek. We kunnen slechts één primaire sleutel per schema hebben.

De eerste 1000 id&#39;s zijn gereserveerd, dus als een reeks waarden moet worden gedefinieerd voor toetsen, begint u bij 1000.

## Kenmerkbeschrijving {#attribute-description-8}

* **allowEmptyPart (boolean)**: in het geval van een samengestelde sleutel, als dit attribuut wordt geactiveerd, wordt zij als geldig beschouwd als minstens één van zijn sleutels niet leeg is. Als dit het geval is, is de lege nodewaarde &quot;0&quot;(boolean of voor alle soorten numerieke gegevens). Standaard moeten alle toetsen waaruit een samengestelde sleutel bestaat, worden ingevoerd.
* **applyIf (string)**: Met dit kenmerk kunt u de sleutel optioneel maken. In deze code wordt de voorwaarde gedefinieerd op basis waarvan de sleuteldefinitie wordt toegepast. Dit kenmerk ontvangt een XTK-expressie.
* **internal (boolean)**: als het wordt geactiveerd, laat dit kenmerk Adobe Campaign weten dat de sleutel primair is.
* **label (tekenreeks)**: label van de toets.
* **naam (MNTOKEN)**: interne naam van de sleutel.
* **noDbIndex (boolean)**: als deze is geactiveerd (noDbIndex=&quot;true&quot;), wordt het veld dat overeenkomt met de sleutel niet geïndexeerd.

## Voorbeelden {#examples-------}

Verklaring van een samengestelde sleutel die het veld &quot;@expr&quot; of &quot;alias&quot; leeg maakt:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Verklaring van een primaire sleutel op het gebied van de &quot;Naam&quot;van type STRING in een `<srcschema>` en de passende SQL vraag:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
