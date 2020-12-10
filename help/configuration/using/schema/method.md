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
source-wordcount: '204'
ht-degree: 3%

---


# `<method>` element  {#method--element}

## Inhoudsmodel {#content-model-10}

methode:==( help: | Parameters)

## Kenmerken {#attributes-10}

* @_operation (tekenreeks)
* @access (tekenreeks)
* @const (Boolean)
* @hidden (boolean)
* @label (tekenreeks)
* @library (tekenreeks)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolean)

## Ouders {#parents-10}

`<methods>`  ,  `<interface />`

## Kinderen {#children-10}

* `<help>`
* `<parameters>`

## Beschrijving {#description-10}

Met dit element kunt u een SOAP-methode definiëren.

## Gebruik en gebruikscontext {#use-and-context-of-use-7}

SOAP-methoden maken toepassingsprocessen mogelijk.

De &quot;@bibliotheek&quot; is nodig voor het declareren van een nieuwe methode (niet-native): de naamruimte en de naam die voor de bibliotheek worden gebruikt, zijn onafhankelijk van de naamruimte en naam van het schema waarin de declaratie zich bevindt.

## Kenmerkbeschrijving {#attribute-description-10}

* **toegang (tekenreeks)**: this attribute define access control for using the method. Als dit kenmerk ontbreekt, is identificatie verplicht. Beschikbare waarden zijn: &#39;anoniem&#39;, &#39;admin&#39; en &#39;sql&#39;.
* **const (Boolean)**: als deze eigenschap is geactiveerd, betekent dit dat de gedeclareerde methode de entiteit wijzigt
* **label (tekenreeks)**: label van de methode.
* **bibliotheek (tekenreeks)**: deze methode is niet native voor de toepassing. Dit kenmerk neemt de waarde van de methodebibliotheek waar de methodedefinitie is gevonden (nms:mylibrary.js).
* **naam (MNTOKEN)**: unieke methodenaam.
* **static (boolean)**: als dit attribuut wordt geactiveerd, wordt de methode beschouwd als autonoom, moeten alle parameters aan de methode worden gespecificeerd wanneer het omhoog wordt geroepen.

## Voorbeelden {#examples-7}

Definitie van de methode &quot;Abonneren&quot; in het tekstvak:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```
