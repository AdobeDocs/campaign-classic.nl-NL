---
product: campaign
title: Schemaelementen en -kenmerken - hoofdelement
description: sleutelelement
feature: Schema Extension
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# sleutelelement {#key--element}


## Inhoudsmodel {#content-model-8}

key:==keyfield

## Attributen {#attributes-8}

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

Een sleutel wordt een samengestelde sleutel genoemd als deze meerdere velden bevat (bijvoorbeeld meerdere `<keyfield>` onderliggende items). Gebruik geen samengestelde sleutel om een primaire sleutel te definiëren.

Als het hoofdelement van het schema het kenmerk &quot;@autopk=true&quot; bevat, is de primaire sleutel uniek. We kunnen slechts één primaire sleutel per schema hebben.

De eerste 1000 id&#39;s zijn gereserveerd, dus als een reeks waarden moet worden gedefinieerd voor toetsen, begint u bij 1000.

## Beschrijving van kenmerk {#attribute-description-8}

* **allowEmptyPart (boolean)**: in het geval van een samengestelde sleutel, als dit attribuut wordt geactiveerd, wordt zij als geldig beschouwd als minstens één van zijn sleutels niet leeg is. Als dit het geval is, is de lege nodewaarde &quot;0&quot;(boolean of voor alle soorten numerieke gegevens). Standaard moeten alle toetsen waaruit een samengestelde sleutel bestaat, worden ingevoerd.
* **applyIf (koord)**: dit attribuut laat u de sleutel facultatief maken. In deze code wordt de voorwaarde gedefinieerd op basis waarvan de sleuteldefinitie wordt toegepast. Dit kenmerk ontvangt een XTK-expressie.
* **intern (boolean)**: als het wordt geactiveerd, laat dit attribuut Adobe Campaign weten dat de sleutel primair is.
* **etiket (koord)**: etiket van de sleutel.
* **naam (MNTOKEN)**: interne naam van de sleutel.
* **noDbIndex (boolean)**: als het wordt geactiveerd (noDbIndex= &quot;waar&quot;), zal het gebied dat de sleutel aanpast niet worden geïndexeerd.

## Voorbeelden {#examples-------}

Verklaring van een samengestelde sleutel die het veld &quot;@expr&quot; of &quot;alias&quot; leeg maakt:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Declaratie van een primaire sleutel in het veld Naam van het type STRING in een `<srcschema>` en de bijbehorende SQL-query:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
