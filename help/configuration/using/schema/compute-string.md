---
product: campaign
title: Elementen en kenmerken - element compute-string
description: compute-string element
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 2%

---

# compute-string element {#compute-string--element}


## Inhoudsmodel {#content-model-1}

compute-string:==EMPTY

## Attributen {#attributes-1}

@expr

## Ouders {#parents-1}

`<element>`

## Kinderen {#children-1}

Geen

## Beschrijving {#description-1}

Met het element `<compute-string>` kunt u een tekenreeks genereren op basis van een XTK-expressie en zo een &#39;gebouwd&#39; label weergeven in de interface op basis van verschillende waarden.

## Gebruik en gebruikscontext {#use-and-context-of-use-1}

Wanneer er geen `<compute-string>` is gedefinieerd, wordt standaard een `<compute-string>` -element ingevoerd met de waarden van de primaire sleutel in het schema.

## Beschrijving van kenmerk {#attribute-description-1}

* **expr (koord)**: XTK en/of de uitdrukking van Xpath

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
