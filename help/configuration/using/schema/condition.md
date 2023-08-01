---
product: campaign
title: Schemaelementen en -kenmerken - voorwaardelement
description: voorwaarde-element
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 2%

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

Eén `<sysfiler>`  Het element kan verschillende filtervoorwaarden bevatten.

## Beschrijving van kenmerk {#attribute-description-2}

* **boolOperator (tekenreeks)**: als er meerdere `<conditions>` worden gedefinieerd binnen dezelfde  `<sysfilter>` -element, kunt u deze kenmerken combineren. Standaard is de logische koppeling tussen `<condition>` elementen is &quot;AND&quot;. Met het kenmerk &quot;@boolOperator&quot; kunt u koppelingen van het type &quot;OR&quot; en &quot;AND&quot; combineren.
* **enabledIf (string)**: activeringstest voorwaarde.
* **expr (tekenreeks)**: een XTK-expressie.

## Voorbeelden {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
