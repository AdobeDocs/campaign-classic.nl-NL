---
title: SOAP-methoden implementeren
seo-title: SOAP-methoden implementeren
description: SOAP-methoden implementeren
seo-description: null
page-status-flag: never-activated
uuid: c9366f4e-460d-4087-88f7-9cc6d0de597a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 76984d9d-7759-4e0f-a275-09cca27589fa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# SOAP-methoden implementeren{#implementing-soap-methods}

## Inleiding {#introduction}

Het is mogelijk om SOAP-methoden te maken in JavaScript. Deze functie laat eenvoudig toepassingsprocessen toe, kan het het ontwikkelen van JSPs en hun het roepen in de vormen vermijden.

Deze SOAP-methoden gedragen zich op dezelfde manier als de methoden die native in de toepassing worden gedefinieerd. Dezelfde kenmerken worden ondersteund: statisch, alleen sleutel en const.

## Een methodebibliotheek definiëren {#defining-a-method-library}

Het maken van een methodebibliotheek bestaat uit twee fasen:

* de SOAP-methodedeclaratie,
* Definitie (of implementatie) in JavaScript.

### Verklaring {#declaration}

Begin door de methodes in de schema&#39;s te verklaren (voor meer op om schema&#39;s tot stand te brengen en uit te geven, verwijs naar [deze sectie](../../configuration/using/about-schema-edition.md)).

Hun verklaring is gelijkaardig aan die van inheemse methodes, behalve dat moet u het attribuut &quot;bibliotheek&quot;toevoegen die de naam van de methodebibliotheek specificeren waar de definitie wordt gevestigd.

Deze naam valt samen met de naam (met de naamruimte) van de entiteit van het type &#39;JavaScript Code&#39;.

Voorbeeld:

De methode testLog(msg) wordt gedeclareerd in een extensie nms:ontvanger

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>De naamruimte en de naam die voor de bibliotheek worden gebruikt, zijn onafhankelijk van de naamruimte en het schema waarin de declaratie zich bevindt.

### Definitie {#definition}

SOAP-methoden worden geïmplementeerd in de vorm van een JavaScript-functie gegroepeerd in een script dat een bibliotheek vertegenwoordigt.

>[!NOTE]
>
>Een methodebibliotheek kan functies voor diverse schema&#39;s groeperen of vice versa, kunnen de functies van één schema in afzonderlijke bibliotheken worden bepaald.

Het script kan code bevatten die moet worden uitgevoerd tijdens het laden van de eerste bibliotheek.

**1. Naam**

De naam van de functie moet de volgende indeling hebben:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Voorbeeld:

De volgende JavaScript-functie is de implementatie van de hierboven beschreven methode. Deze wordt gedefinieerd in de entiteit van het type JavaScript Code met de naam &#39;cus:test&#39;.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Handtekening**

De handtekening van de functie moet een argument bevatten voor elke parameter &#39;in&#39; of &#39;inout&#39; van de declaratie.

Specifieke gevallen:

* **niet-statische methoden**: de functie moet eerst een aanvullend argument bevatten, dat samenvalt met de XML-entiteit die wordt doorgegeven in de vorm van een object van het type &#39;xml&#39; (E4X).
* **Methoden** van het type &quot;key only&quot;: de functie moet eerst een extra argument bevatten, dat samenvalt met de sleutel die wordt doorgegeven in de vorm van tekenreeksen.

**3. Geretourneerde waarden**

De functie moet een waarde retourneren voor elke parameter van het type &#39;out&#39; of &#39;inout&#39;. Specifiek geval: Als de methode wordt gedeclareerd zonder de kenmerken &#39;static&#39;, &#39;key only&#39; of &#39;const&#39;, moet de eerste geretourneerde waarde overeenkomen met de gewijzigde entiteit. Het is mogelijk om een nieuw object te retourneren of de eerste gewijzigde parameter te retourneren.

Bijvoorbeeld:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

Wanneer meerdere waarden moeten worden geretourneerd, moeten deze in een tabel worden weergegeven.

Voorbeeld:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

