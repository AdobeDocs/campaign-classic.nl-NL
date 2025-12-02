---
product: campaign
title: Gegevensschema's gebruiken in campagne
description: Leer hoe u gegevensschema's kunt gebruiken in Campagne
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Data Model
role: User, Developer
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 1%

---

# Gegevensschema&#39;s gebruiken in campagne{#data-schemas}

Hieronder volgen enkele algemene beginselen betreffende het gebruik van gegevensschema&#39;s in Adobe Campaign.

Voor meer bij het creëren van en het vormen van gegevensschema&#39;s in Adobe Campaign, verwijs naar [ deze sectie ](../../configuration/using/about-schema-edition.md).

## Schemastructuur {#schema-structure}

Het document van XML van een gegevensschema moet het **`<srcschema>`** wortelelement met de **naam** en **namespace** attributen bevatten om de schemanaam en zijn namespace te bevolken.

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

Het **malplaatje** attribuut ingegaan in het belangrijkste element laat u het schema met generische eigenschappen tot alle inhoudsdefinities zoals naam, creatieve datum, auteur, geassocieerd koord, enz. uitbreiden.

Deze eigenschappen worden beschreven in het **ncm:content** schema.

>[!NOTE]
>
>De aanwezigheid van het **xmlChildren** attribuut wijst erop dat de gegevensstructuur die via het belangrijkste element wordt ingegaan in een document van XML van de inhoudsinstantie wordt opgeslagen.

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

U kunt verschillende eigenschappen gebruiken om de elementen **`<element>`** en **`<attribute>`** van het gegevensschema te verrijken.

De belangrijkste eigenschappen die in inhoudsbeheer worden gebruikt zijn als volgt:

* **etiket**: korte beschrijving,
* **desc**: lange beschrijving,
* **gebrek**: uitdrukking die een standaardwaarde op inhoudsverwezenlijking terugkeren,
* **userEnum**: vrije opsomming om de waarden op te slaan en te tonen ingegaan via dit gebied,
* **enum**: vaste opsomming die wordt gebruikt wanneer de lijst van mogelijke waarden vooraf gekend is.

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

In ons voorbeeld zijn de elementen **`<chapter>`** en **`<page>`** verzamelingselementen. Het **ongebonden** attribuut moet daarom aan de definitie van deze elementen worden toegevoegd:

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>De aanwezigheid van **ordered= &quot;waar&quot;** attributen laat u tot de opgenomen inzamelingselementen opdracht geven.

## Element verwijzen {#element-referencing}

Element dat verwijst wordt veel gebruikt in inhoudsschema&#39;s. Hiermee kunt u de definitie van een **`<element>`** -element factoriseren, zodat er naar kan worden verwezen op andere elementen met dezelfde structuur.

Het **ref** attribuut op het element dat moet worden van verwijzingen voorzien moet met de weg (XPath) van het verwijzingselement worden voltooid.

**Voorbeeld**: het toevoegen van een **bijlage** sectie met de zelfde structuur zoals het **`<chapter>`** element van ons voorbeeldschema.

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

## Compute string {#compute-string}

A **verwerkt koord** is een uitdrukking van XPath die wordt gebruikt om een koord te construeren dat een inhoudsinstantie vertegenwoordigt.

Hier is ons voorbeeldschema met zijn **verwerkt koord**:

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
>De **Naam** geeft controle uit laat u de sleutel van het schema ingaan, die uit de naam en namespace bestaat. De **naam** en **namespace** attributen van het element van de schemawortel worden automatisch bijgewerkt in XML geeft gebied van het schema uit.
