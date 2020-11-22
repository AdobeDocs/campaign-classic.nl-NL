---
solution: Campaign Classic
product: campaign
title: Schema-verwijzing in Adobe Campaign Classic
description: Leer hoe te om uitbreidingsschema's te vormen om het conceptuele gegevensmodel van het gegevensbestand van Adobe Campaign Classic uit te breiden.
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 7%

---


# Schemaverwijzing{#about-schema-reference}

In dit hoofdstuk wordt beschreven hoe u extensieschema&#39;s configureert om het conceptuele gegevensmodel van de Adobe Campaign-database uit te breiden.

Raadpleeg het gegevensmodel [](https://helpx.adobe.com/nl/campaign/kb/acc-datamodel.html)Campaign Classic voor een beter begrip van ingebouwde tabellen en hun interactie.

De fysieke en logische structuur van de data die in de applicatie worden overgedragen, wordt in XML beschreven. It obeys a grammar specific to Adobe Campaign, called a **schema**.

Een schema is een XML-document dat is gekoppeld aan een databasetabel. De code definieert de gegevensstructuur en beschrijft de SQL-definitie van de tabel:

* De naam van de tabel
* Velden
* Indexen
* Koppelingen met andere tabellen

Hierin wordt ook de XML-structuur beschreven die wordt gebruikt om gegevens op te slaan:

* Elementen en kenmerken
* Hiërarchie van elementen
* Element- en kenmerktypen
* Standaardwaarden
* Labels, beschrijvingen en andere eigenschappen.

Met schema&#39;s kunt u een entiteit in de database definiëren. Er is een schema voor elke entiteit.

In de volgende afbeelding ziet u de locatie van schema&#39;s in het Adobe Campaign-gegevenssysteem:

![](assets/reference_schema_intro.png)

## Syntaxis van schema&#39;s {#syntax-of-schemas}

Het hoofdelement van het schema is **`<srcschema>`**. Het bevat de **`<element>`** en **`<attribute>`** subelementen.

Het eerste **`<element>`** subelement valt samen met de hoofdmap van de entiteit.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Het hoofdelement van de entiteit heeft dezelfde naam als het schema.

![](assets/s_ncs_configuration_schema_and_entity.png)

De **`<element>`** tags definiëren de namen van entiteitselementen. **`<attribute>`** tags in het schema de namen definiëren van de kenmerken in de **`<element>`** tags waaraan ze zijn gekoppeld.

## Identificatie van een schema {#identification-of-a-schema}

Een gegevensschema wordt geïdentificeerd door zijn naam en zijn namespace.

Met een naamruimte kunt u een set schema&#39;s groeperen op interessegebied. Bijvoorbeeld, wordt **concentraat** namespace gebruikt voor klant-specifieke configuratie (**klanten**).

>[!IMPORTANT]
>
>Standaard moet de naam van de naamruimte beknopt zijn en alleen toegestane tekens bevatten, in overeenstemming met XML-naamgevingsregels.
>
>Id&#39;s mogen niet beginnen met numerieke tekens.

Bepaalde naamruimten zijn gereserveerd voor beschrijvingen van de systeementiteiten die vereist zijn voor de werking van de Adobe Campaign-toepassing:

* **xtk**: met betrekking tot platformsysteemgegevens,
* **nl**: betreffende het algemene gebruik van de aanvraag,
* **nms**: wat de levering betreft (ontvanger, levering, tracking, enz.),
* **ncm**: met betrekking tot inhoudsbeheer,
* **temp**: gereserveerd voor tijdelijke regelingen.

De identificatiesleutel van een schema is een tekenreeks die is opgebouwd met behulp van de naamruimte en de naam gescheiden door een dubbele punt. bijvoorbeeld: **focus:ontvanger**.
