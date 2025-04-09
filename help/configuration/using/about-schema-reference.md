---
product: campaign
title: Aan de slag met schema's in Adobe Campaign
description: Leer hoe u met schema's werkt en breid het conceptuele gegevensmodel van de Adobe Campaign-database uit
feature: Schema Extension
role: Data Engineer, Developer
level: Intermediate, Experienced
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 1%

---

# Aan de slag met schema&#39;s {#about-schema-reference}

## Wat is een schema {#what-is-a-schema}

In dit hoofdstuk wordt beschreven hoe u extensieschema&#39;s configureert om het conceptuele gegevensmodel van de Adobe Campaign-database uit te breiden.

Voor een beter inzicht in de ingebouwde lijsten van de Campagne en hun interactie, verwijs naar het [ de gegevensmodel van Campaign Classic ](about-data-model.md).

In Adobe Campaign wordt de fysieke en logische structuur van de gegevens die in de toepassing worden overgedragen, in XML beschreven. A **schema** is een document van XML verbonden aan een gegevensbestandlijst. De code definieert de gegevensstructuur en beschrijft de SQL-definitie van de tabel:

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

Het hoofdelement van het schema is **`<srcschema>`** . Het bevat de subelementen **`<element>`** en **`<attribute>`** .

Het eerste subelement **`<element>`** valt samen met de hoofdmap van de entiteit.

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

Met de tags **`<element>`** worden de namen van entiteitelementen gedefinieerd. **`<attribute>`** -tags van het schema definiëren de namen van de kenmerken in de **`<element>`** -tags waaraan ze zijn gekoppeld.

## Identificatie van een schema {#identification-of-a-schema}

Een gegevensschema wordt geïdentificeerd door zijn naam en zijn namespace.

Met een naamruimte kunt u een set schema&#39;s groeperen op interessegebied. Bijvoorbeeld, wordt **focus** namespace gebruikt voor klant-specifieke configuratie (**klanten**).

De identificatiesleutel van een schema is een koord dat wordt gebouwd gebruikend namespace en de naam die door een dubbelpunt wordt gescheiden; bijvoorbeeld: **concentreert:ontvanger**.

>[!IMPORTANT]
>
>* De naam van de naamruimte moet beknopt zijn en mag alleen toegestane tekens bevatten in overeenstemming met de XML-naamgevingsregels.
>
>* Id&#39;s mogen niet beginnen met numerieke tekens.
>
>* De volgende namespaces zijn gereserveerd voor beschrijvingen van de systeementiteiten die voor de verrichting van de toepassing van Adobe Campaign worden vereist en moeten niet worden gebruikt: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.
>
