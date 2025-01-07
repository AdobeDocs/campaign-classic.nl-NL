---
product: campaign
title: Schema-elementen en -kenmerken - methode-element
description: methode-element
feature: Schema Extension
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# methode-element {#method--element}


## Inhoudsmodel {#content-model-10}

methode:==( help: | parameters)

## Attributen {#attributes-10}

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

`<methods>` , `<interface />`

## Kinderen {#children-10}

* `<help>`
* `<parameters>`

## Beschrijving {#description-10}

Met dit element kunt u een SOAP-methode definiëren.

## Gebruik en gebruikscontext {#use-and-context-of-use-7}

SOAP methoden maken toepassingsprocessen mogelijk.

De &quot;@bibliotheek&quot; is nodig voor het declareren van een nieuwe methode (niet-native): de naamruimte en de naam die voor de bibliotheek worden gebruikt, zijn onafhankelijk van de naamruimte en naam van het schema waarin de declaratie zich bevindt.

## Beschrijving van kenmerk {#attribute-description-10}

* **toegang (koord)**: dit attribuut bepaalt toegangsbeheer voor het gebruiken van de methode. Als dit kenmerk ontbreekt, is identificatie verplicht. Beschikbare waarden zijn: &#39;anoniem&#39;, &#39;admin&#39; en &#39;sql&#39;.
* **const (boolean)**: als het wordt geactiveerd, betekent dit attribuut dat de gedeclareerde methode de entiteit zal veranderen
* **etiket (koord)**: etiket van de methode.
* **bibliotheek (koord)**: deze methode is niet inheems aan de toepassing. Dit kenmerk neemt de waarde van de methodebibliotheek waar de methodedefinitie is gevonden (nms:mylibrary.js).
* **naam (MNTOKEN)**: unieke methodenaam.
* **statisch (boolean)**: als dit attribuut wordt geactiveerd, wordt de methode beschouwd als autonoom, moeten alle parameters aan de methode worden gespecificeerd wanneer het omhoog wordt geroepen.

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
