---
product: campaign
title: Elementen en kenmerken
description: Elementen en kenmerken
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 18%

---

# sysfilter, element {#sysfilter--element}

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
