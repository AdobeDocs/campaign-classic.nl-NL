---
solution: Campaign Classic
product: campaign
title: Elementen en kenmerken
description: Elementen en kenmerken
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 8%

---


# compute-string element {#compute-string--element}

## Inhoudsmodel {#content-model-1}

compute-string:==EMPTY

## Kenmerken {#attributes-1}

@expr

## Ouders {#parents-1}

`<element>`

## Kinderen {#children-1}

Geen

## Beschrijving {#description-1}

Met het element `<compute-string>` kunt u een tekenreeks genereren op basis van een XTK-expressie om een &quot;gebouwd&quot; label weer te geven in de interface op basis van verschillende waarden.

## Gebruik en gebruikscontext {#use-and-context-of-use-1}

Wanneer geen `<compute-string>` wordt bepaald, is een `<compute-string>` element ingegaan door gebrek met de waarden van de primaire sleutel in het schema.

## Kenmerkbeschrijving {#attribute-description-1}

* **expr (tekenreeks)**: XTK en/of Xpath-expressie

## Voorbeelden {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Resultaat van de tekenreeks berekend op een ontvanger: &quot;Jan Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
