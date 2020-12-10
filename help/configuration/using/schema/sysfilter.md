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
source-wordcount: '42'
ht-degree: 19%

---


# `<sysfilter>` element  {#sysfilter--element}

## Inhoudsmodel {#content-model-15}

sysFilter:==condition

## Kenmerken {#attributes-15}

Geen

## Ouders {#parents-15}

`<element>`

## Kinderen {#children-15}

`<condition>`

## Beschrijving {#description-15}

Met dit element kunt u een filter definiëren.

## Kenmerkbeschrijving {#attribute-description-15}

Dit element heeft geen kenmerken.

## Voorbeelden {#examples-12}

Definitie van een filter met een voorwaarde voor het kenmerk @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
