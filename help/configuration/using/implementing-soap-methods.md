---
product: campaign
title: SOAP-methoden implementeren
description: SOAP-methoden implementeren
feature: Configuration
role: Data Engineer, Developer
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 2%

---

# SOAP implementeren{#implementing-soap-methods}



## Inleiding {#introduction}

Het is mogelijk SOAP methoden te maken in JavaScript. Deze functie laat eenvoudig toepassingsprocessen toe, kan het het ontwikkelen van JSPs en hun het roepen in de vormen vermijden.

Deze SOAP werken op dezelfde manier als de methoden die native in de toepassing worden gedefinieerd. Dezelfde kenmerken worden ondersteund: statisch, alleen-toets en const.

## Een methodebibliotheek definiëren {#defining-a-method-library}

Het maken van een methodebibliotheek bestaat uit twee fasen:

* de declaratie van de SOAP methode;
* Definitie (of implementatie) in JavaScript.

### Verklaring {#declaration}

Begin door de methodes in de schema&#39;s (voor meer op te verklaren om schema&#39;s tot stand te brengen en uit te geven, verwijs naar [ deze sectie ](../../configuration/using/about-schema-edition.md)).

Hun verklaring is gelijkaardig aan die van inheemse methodes, behalve dat moet u het attribuut &quot;bibliotheek&quot;toevoegen die de naam van de methodebibliotheek specificeren waar de definitie wordt gevestigd.

Deze naam valt samen met de naam (met de naamruimte) van het type &#39;JavaScript Code&#39;.

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

SOAP methoden worden geïmplementeerd in de vorm van een JavaScript-functie gegroepeerd in een script dat een bibliotheek vertegenwoordigt.

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

De volgende JavaScript-functie is de implementatie van de hierboven beschreven methode. Zij wordt in de entiteit van het type &quot;JavaScript Code&quot; gedefinieerd met de naam &quot;cus:test&quot;.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Handtekening**

De handtekening van de functie moet een argument bevatten voor elke parameter &#39;in&#39; of &#39;inout&#39; van de declaratie.

Specifieke gevallen:

* **niet-statische methodes**: de functie moet een extra argument eerst omvatten, samenvallend met de entiteit van XML die in de vorm van een &quot;xml&quot;(E4X) typevoorwerp wordt overgegaan.
* **&quot;sleutel slechts&quot;typemethodes**: de functie moet een extra argument eerst omvatten, die met de sleutel samenvalt die in de vorm van karakterkoorden wordt overgegaan.

**3. Geretourneerde waarden**

De functie moet een waarde retourneren voor elke parameter van het type &#39;out&#39; of &#39;inout&#39;. Specifiek geval: als de methode wordt gedeclareerd zonder de kenmerken &#39;static&#39;, &#39;key only&#39; of &#39;const&#39;, moet de eerste geretourneerde waarde overeenkomen met de gewijzigde entiteit. Het is mogelijk om een nieuw object te retourneren of de eerste gewijzigde parameter te retourneren.

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
