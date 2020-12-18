---
solution: Campaign Classic
product: campaign
title: Dataschema’s
description: Dataschema’s
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---


# Dataschema’s{#data-schemas}

Hieronder volgen enkele algemene beginselen betreffende het gebruik van gegevensschema&#39;s in Adobe Campaign.

Raadpleeg [deze sectie](../../configuration/using/about-schema-edition.md) voor meer informatie over het maken en configureren van gegevensschema&#39;s in Adobe Campaign.

## Schemastructuur {#schema-structure}

Het document van XML van een gegevensschema moet **`<srcschema>`** wortelelement met **name** en **namespace** attributen bevatten om de schemanaam en zijn namespace te bevolken.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Het punt van ingang van het schema is zijn belangrijkste element. Het is gemakkelijk te identificeren omdat het de zelfde naam zoals het schema heeft, en het zou het kind van het wortelelement moeten zijn. De beschrijving van de inhoud begint met dit element.

In een inhoudsbeheerschema, wordt het belangrijkste element vertegenwoordigd door de volgende lijn:

```
<element name="book" template="ncm:content" xmlChildren="true">
```

Met het **template**-kenmerk dat u in het hoofdelement hebt ingevoerd, kunt u het schema met algemene eigenschappen uitbreiden naar alle inhoudsdefinities, zoals naam, aanmaakdatum, auteur, gekoppelde tekenreeks, enz.

Deze eigenschappen worden beschreven in het schema **ncm:content**.

>[!NOTE]
>
>De aanwezigheid van het **xmlChildren**-kenmerk geeft aan dat de gegevensstructuur die via het hoofdelement wordt ingevoerd, wordt opgeslagen in een XML-document van de inhoudsinstantie.

>[!CAUTION]
>
>Wanneer het creëren van een nieuw schema of tijdens een schemauitbreiding, moet u de zelfde primaire zeer belangrijke opeenvolgingswaarde (@pkSequence) voor het volledige schema houden.

## Datatypen {#data-types}

Hier volgt een voorbeeld van een inhoudsbeheerschema met de ingevulde typen:

```
<srcSchema name="book" namespace="cus">
  <element name="book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string"/>
    <attribute name="date" type="date"/>
    <attribute name="language" type="string"/>
    <element name="chapter">
      <attribute name="name" type="string"/>
      <element name="page" type="string>
        <attribute name="number" type="short"/>
      </element>
    </element>
  </element>
</element>
```

## Properties {#properties}

Verschillende eigenschappen kunnen worden gebruikt om de elementen **`<element>`** en **`<attribute>`** van het gegevensschema te verrijken.

De belangrijkste eigenschappen die in inhoudsbeheer worden gebruikt zijn als volgt:

* **label**: korte beschrijving,
* **desc**: lange beschrijving,
* **standaard**: expressie die een standaardwaarde retourneert bij het maken van inhoud,
* **userEnum**: gratis opsomming voor het opslaan en weergeven van de waarden die via dit veld worden ingevoerd;
* **opsomming**: vaste opsomming die wordt gebruikt wanneer de lijst van mogelijke waarden vooraf bekend is.

Hier volgt ons voorbeeldschema met de eigenschappen die zijn ingevuld:

```
<srcSchema name="book" namespace="cus">
  <enumeration name="language" basetype="string" default="eng">    
    <value name="fra" label="French"/>    
    <value name="eng" label="English"/>   
  </enumeration>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter">
      <attribute name="name" type="string" label="Name" desc="Name of chapter"/>
      <element name="page" type="string" label="Page" desc="Page content">
        <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
      </element>
    </element>
  </element>
</srcSchema>
```

## Verzamelelementen {#collection-elements}

Een verzameling is een lijst met elementen met dezelfde naam en hetzelfde hiërarchische niveau.

In ons voorbeeld zijn de elementen **`<chapter>`** en **`<page>`** verzamelingselementen. Het **unbound** attribuut moet daarom aan de definitie van deze elementen worden toegevoegd:

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>Met de aanwezigheid van het **ordered=&quot;true&quot;**-kenmerk kunt u de ingevoegde verzamelingselementen ordenen.

## Element dat verwijst naar {#element-referencing}

Element dat verwijst wordt veel gebruikt in inhoudsschema&#39;s. Het laat u toe om de definitie van een **`<element>`** element te factoriseren zodat het op andere elementen met de zelfde structuur kan worden van verwijzingen voorzien.

Het **ref** attribuut op het element waarnaar moet worden verwezen moet met de weg (XPath) van het verwijzingselement worden voltooid.

**Voorbeeld**: toevoegen van een  **** bijlage met de zelfde structuur zoals het  **`<chapter>`** element van ons voorbeeldschema.

```
<srcSchema name="book" namespace="cus">
  <element name="section">
    <attribute name="name" type="string" label="Name" desc="Name"/>
    <element name="page" type="string" label="Page" desc="Content of page">
      <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
    </element>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter" ref="section"/>
    <element name="appendix" label="Appendix" ref="section"/>
  </element>
</srcSchema>
```

De hoofdstukstructuur wordt verplaatst naar het element met de naam &quot;sectie&quot; buiten het hoofdelement. Het hoofdstuk en de sectie verwijzen naar het element &quot;section&quot;.

## Tekenreeks {#compute-string} berekenen

Een **Berekende tekenreeks** is een XPath-expressie die wordt gebruikt om een tekenreeks samen te stellen die een inhoudsinstantie vertegenwoordigt.

Hier is ons voorbeeldschema met zijn **Berekende koord**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## Schema’s bewerken {#editing-schemas}

In het bewerkingsveld kunt u de XML-inhoud van het bronschema invoeren:

![](assets/d_ncs_integration_schema_edition.png)

Wanneer het bronschema wordt opgeslagen, wordt het uitgebreide schema automatisch opgestart.

>[!NOTE]
>
>Met het besturingselement **Naam** kunt u de sleutel van het schema invoeren, bestaande uit de naam en naamruimte. De **name** en **namespace** attributen van het schema wortelelement worden automatisch bijgewerkt op XML uitgeeft gebied van het schema.
