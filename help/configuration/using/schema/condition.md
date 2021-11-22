---
product: campaign
title: Elementen en kenmerken
description: Elementen en kenmerken
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 8%

---

# voorwaarde-element {#condition--element}

![](../../../assets/v7-only.svg)

## Inhoudsmodel {#content-model-2}

condition:==EMPTY

## Attributen {#attributes-2}

* @boolOperator (tekenreeks)
* @enabledIf (string)
* @expr (tekenreeks)

## Ouders {#parents-2}

`<sysfilter>`

## Kinderen {#children-2}

Geen

## Beschrijving {#description-2}

Met dit element kunt u een filtervoorwaarde definiëren.

## Gebruik en gebruikscontext {#use-and-context-of-use-2}

Eén `<sysfiler>`  element kan verschillende filtervoorwaarden bevatten.

## Beschrijving van kenmerk {#attribute-description-2}

* **boolOperator (tekenreeks)**: indien meerdere `<conditions>` worden gedefinieerd binnen dezelfde  `<sysfilter>` -element, kunt u deze kenmerken combineren. Standaard is de logische koppeling tussen `<condition>` elementen is &quot;AND&quot;. Met het kenmerk &quot;@boolOperator&quot; kunt u koppelingen van het type &quot;OR&quot; en &quot;AND&quot; combineren.
* **enabledIf (string)**: activeringstest voorwaarde.
* **expr (tekenreeks)**: een XTK-expressie.

## Voorbeelden {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
