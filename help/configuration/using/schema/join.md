---
product: campaign
title: Schemaelementen en -kenmerken - element join
description: join-element
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

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

* **dstFilterExpr (tekenreeks)**: met dit kenmerk kunt u het aantal waarden beperken dat in aanmerking komt in de externe tabel.
* **xpath-dst (tekenreeks)**: dit kenmerk ontvangt een Xpath (@name-kenmerk van de externe tabel).
* **xpath-src (tekenreeks)**: dit kenmerk ontvangt een Xpath (@name-kenmerk in het huidige schema).

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
