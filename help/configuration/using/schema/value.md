---
product: campaign
title: Elementen en kenmerken - waardeelement
description: Elementen en kenmerken
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%

---

# value, element {#value--element}

![](../../../assets/v7-only.svg)

## Inhoudsmodel {#content-model-16}

waarde:==help

## Attributen {#attributes-16}

* @applicableIf (tekenreeks)
* @desc (tekenreeks)
* @enabledIf (string)
* @img (tekenreeks)
* @label (tekenreeks)
* @name (tekenreeks)
* @value (tekenreeks)

## Ouders {#parents-16}

`<enumeration>`

## Kinderen {#children-16}

`<help>`

## Beschrijving {#description-16}

Met dit element kunt u de waarden definiëren die in een opsomming zijn opgeslagen.

## Beschrijving van kenmerk {#attribute-description-16}

* **applyIf (string)**: met dit kenmerk kunt u een opsommingswaarde optioneel maken. Er wordt een XTK-expressie ontvangen.
* **desc (tekenreeks)**: beschrijving van de opsommingswaarde.
* **enabledIf (string)**: voorwaarde voor het activeren van de opsommingswaarde.
* **img (tekenreeks)**: afbeelding die is gekoppeld aan de opsomming in het formulier &quot;namespace:image_name&quot;. De afbeelding moet op de toepassingsserver worden geïmporteerd.
* **label (tekenreeks)**: label van de opsommingswaarde.
* **name (string)**: interne naam van de opsommingswaarde.
* **value (string)**: waarde van de opsommingswaarde. Het type waarde wordt gedefinieerd op basis van het type opsomming. Wanneer de opsomming van het type tekenreeks is, mag deze alleen tekenreekstype waarden bevatten.

## Voorbeelden {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
