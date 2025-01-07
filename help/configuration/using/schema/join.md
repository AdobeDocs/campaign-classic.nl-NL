---
product: campaign
title: Schemaelementen en -kenmerken - element join
description: join-element
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# join-element {#join--element}


## Inhoudsmodel {#content-model-7}

join:==EMPTY

## Attributen {#attributes-7}

* @dstFilterExpr (tekenreeks)
* @xpath-dst (tekenreeks)
* @xpath-src (tekenreeks)

## Ouders {#parents-7}

`<element>`

## Kinderen {#children-7}

Geen

## Beschrijving {#description-7}

Hiermee kunt u de velden definiëren waarmee een samenvoeging tussen SQL-tabellen wordt gemaakt.

## Gebruik en gebruikscontext {#use-and-context-of-use-5}

Een `<join>` -element kan alleen worden gebruikt als het bovenliggende `<element>` -element van het type &#39;link&#39; is. Dit betekent dat het bovenliggende element het kenmerk &quot;@type=link&quot; moet hebben gedeclareerd.

Het is niet nodig de naam en naamruimte van de externe tabel in het element `<join>` op te geven. Deze moeten in het bovenliggende element `<element>` worden opgegeven.

Door overeenkomst, worden de verbindingen bepaald aan het eind van het schema.

Als het element `<join>` niet wordt opgegeven wanneer het element voor het koppelingstype wordt gedefinieerd, wordt de koppeling automatisch op de primaire sleutels van beide tabellen geplaatst.

## Beschrijving van kenmerk {#attribute-description-7}

* **dstFilterExpr (koord)**: dit attribuut laat u het aantal in aanmerking komende waarden in de verre lijst beperken.
* **xpath-dst (koord)**: dit attribuut ontvangt een Xpath (@name attributen van de verre lijst).
* **xpath-src (koord)**: dit attribuut ontvangt een Xpath (@name attribuut in het huidige schema).

## Voorbeelden {#examples-6}

Koppeling tussen het veld E-mail van de huidige tabel en het veld @compagny-id van de externe tabel:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Gefilterde koppeling naar de tabel &quot;cus:Country&quot;, gebaseerd op de inhoud van het veld &quot;@country&quot;, die de waarde &quot;EN&quot; moet bevatten:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
