---
product: campaign
title: Elementen en kenmerken
description: Elementen en kenmerken
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 8%

---

# compute-string element {#compute-string--element}

![](../../../assets/v7-only.svg)

## Inhoudsmodel {#content-model-1}

compute-string:==EMPTY

## Attributen {#attributes-1}

@expr

## Ouders {#parents-1}

`<element>`

## Kinderen {#children-1}

Geen

## Beschrijving {#description-1}

Met het element `<compute-string>` kunt u een tekenreeks genereren op basis van een XTK-expressie om een &quot;gebouwd&quot; label weer te geven in de interface op basis van verschillende waarden.

## Gebruik en gebruikscontext {#use-and-context-of-use-1}

Wanneer geen `<compute-string>` wordt bepaald, is een `<compute-string>` element ingegaan door gebrek met de waarden van de primaire sleutel in het schema.

## Beschrijving van kenmerk {#attribute-description-1}

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
