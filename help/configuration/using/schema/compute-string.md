---
product: campaign
title: Elementen en kenmerken - element compute-string
description: compute-string element
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 2%

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

De `<compute-string>` het element laat u toe om een koord te produceren dat op een uitdrukking XTK wordt gebaseerd om een &quot;gebouwd&quot;etiket in de interface te tonen die op verscheidene waarden wordt gebaseerd.

## Gebruik en gebruikscontext {#use-and-context-of-use-1}

Wanneer `<compute-string>` wordt gedefinieerd, a `<compute-string>` het element is door gebrek ingegaan met de waarden van de primaire sleutel in het schema.

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
