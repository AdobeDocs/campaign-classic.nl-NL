---
product: campaign
title: Elementen en kenmerken
description: Elementen en kenmerken
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 3%

---

# join-element {#join--element}

![](../../../assets/v7-only.svg)

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

A `<join>`  -element kan alleen worden gebruikt als het bovenliggende element  `<element>`  element is van het type &#39;link&#39;. Dit betekent dat het bovenliggende element het kenmerk &quot;@type=link&quot; moet hebben gedeclareerd.

U hoeft de naam en naamruimte van de externe tabel niet op te geven in het dialoogvenster `<join>`  element. Zij moeten in de ouder worden gespecificeerd  `<element>`.

Door overeenkomst, worden de verbindingen bepaald aan het eind van het schema.

Als de `<join>` het element wordt niet gespecificeerd wanneer het element van het verbindingstype wordt bepaald, zal de verbinding automatisch op de primaire sleutels van beide lijsten worden geplaatst.

## Beschrijving van kenmerk {#attribute-description-7}

* **dstFilterExpr (tekenreeks)**: Met dit kenmerk kunt u het aantal waarden in de externe tabel beperken.
* **xpath-dst (tekenreeks)**: this attribute receive an Xpath (@name attribute of the remote table).
* **xpath-src (tekenreeks)**: this attribute receive an Xpath (@name attribute in the current schema).

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
