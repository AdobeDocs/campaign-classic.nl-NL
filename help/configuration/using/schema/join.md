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
source-wordcount: '210'
ht-degree: 3%

---


# `<join>` element  {#join--element}

## Inhoudsmodel {#content-model-7}

join:==EMPTY

## Kenmerken {#attributes-7}

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

Een element `<join>` kan alleen worden gebruikt als het bovenliggende element `<element>` van het type &#39;link&#39; is. Dit betekent dat het bovenliggende element het kenmerk &quot;@type=link&quot; moet hebben gedeclareerd.

Het is niet noodzakelijk om de naam en namespace van de verre lijst in het `<join>` element te specificeren. Zij moeten in de ouder `<element>` worden gespecificeerd.

Door overeenkomst, worden de verbindingen bepaald aan het eind van het schema.

Als het `<join>` element niet wordt gespecificeerd wanneer het element van het verbindingstype wordt bepaald, zal de verbinding automatisch op de primaire sleutels van beide lijsten worden geplaatst.

## Kenmerkbeschrijving {#attribute-description-7}

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
