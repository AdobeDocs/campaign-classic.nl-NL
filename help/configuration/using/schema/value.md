---
product: campaign
title: Elementen en kenmerken - waardeelement
description: Elementen en kenmerken
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%

---

# value, element {#value--element}


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

* **applyIf (koord)**: dit attribuut laat u een opsommingswaarde facultatief maken. Er wordt een XTK-expressie ontvangen.
* **desc (koord)**: beschrijving van de opsommingswaarde.
* **enabledIf (koord)**: voorwaarde voor het activeren van de opsommingswaarde.
* **img (koord)**: beeld verbonden aan de opsomming in de &quot;namespace:image_name&quot;vorm. De afbeelding moet op de toepassingsserver worden geïmporteerd.
* **etiket (koord)**: etiket van de opsommingswaarde.
* **naam (koord)**: interne naam van de opsommingswaarde.
* **waarde (koord)**: waarde van de opsommingswaarde. Het type waarde wordt gedefinieerd op basis van het type opsomming. Wanneer de opsomming van het type tekenreeks is, mag deze alleen tekenreekstype waarden bevatten.

## Voorbeelden {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
