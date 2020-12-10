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
source-wordcount: '92'
ht-degree: 8%

---


# `<condition>` element  {#condition--element}

## Inhoudsmodel {#content-model-2}

condition:==EMPTY

## Kenmerken {#attributes-2}

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

Één `<sysfiler>` element kan verscheidene het filtreren voorwaarden bevatten.

## Kenmerkbeschrijving {#attribute-description-2}

* **boolOperator (tekenreeks)**: als er meerdere  `<conditions>` zijn gedefinieerd binnen hetzelfde   `<sysfilter>` element, kunt u deze combineren met dit kenmerk. Door gebrek, is de logische verbinding tussen `<condition>` elementen &quot;EN&quot;. Met het kenmerk &quot;@boolOperator&quot; kunt u koppelingen van het type &quot;OR&quot; en &quot;AND&quot; combineren.
* **enabledIf (string)**: activeringstest voorwaarde.
* **expr (tekenreeks)**: een XTK-expressie.

## Voorbeelden {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
