---
product: campaign
title: Elementen en kenmerken - element SystemFilter
description: Elementen en kenmerken
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 4%

---

# sysfilter, element {#sysfilter--element}


## Inhoudsmodel {#content-model-15}

sysFilter:==condition

## Attributen {#attributes-15}

Geen

## Ouders {#parents-15}

`<element>`

## Kinderen {#children-15}

`<condition>`

## Beschrijving {#description-15}

Met dit element kunt u een filter definiëren.

## Beschrijving van kenmerk {#attribute-description-15}

Dit element heeft geen kenmerken.

## Voorbeelden {#examples-12}

Definitie van een filter met een voorwaarde voor het kenmerk @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
