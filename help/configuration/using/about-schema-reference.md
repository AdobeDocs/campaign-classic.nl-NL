---
product: campaign
title: Aan de slag met schema's in Adobe Campaign
description: Leer hoe u met schema's werkt en breid het conceptuele gegevensmodel van de Adobe Campaign-database uit
feature: Schema Extension
role: Data Engineer, Developer
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 1%

---

# Aan de slag met schema&#39;s {#about-schema-reference}

## Wat is een schema {#what-is-a-schema}

In dit hoofdstuk wordt beschreven hoe u extensieschema&#39;s configureert om het conceptuele gegevensmodel van de Adobe Campaign-database uit te breiden.

Voor een beter inzicht in de ingebouwde lijsten van de Campagne en hun interactie, verwijs naar [Gegevensmodel Campaign Classic](about-data-model.md).

In Adobe Campaign wordt de fysieke en logische structuur van de gegevens die in de toepassing worden overgedragen, in XML beschreven. A **schema** is een XML-document dat is gekoppeld aan een databasetabel. De code definieert de gegevensstructuur en beschrijft de SQL-definitie van de tabel:

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

De eerste **`<element>`** het subelement samenvalt met de hoofdmap van de entiteit.

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

De **`<element>`** -tags definiëren de namen van entiteitselementen. **`<attribute>`** de labels van het schema definiëren de namen van de kenmerken in het **`<element>`** tags waaraan zij zijn gekoppeld.

## Identificatie van een schema {#identification-of-a-schema}

Een gegevensschema wordt geïdentificeerd door zijn naam en zijn namespace.

Met een naamruimte kunt u een set schema&#39;s groeperen op interessegebied. Bijvoorbeeld de **cus** namespace wordt gebruikt voor klant-specifieke configuratie (**klanten**).

De identificatiesleutel van een schema is een tekenreeks die is samengesteld met behulp van de naamruimte en de naam gescheiden door een dubbele punt, bijvoorbeeld: **focus:ontvanger**.

>[!IMPORTANT]
>
>De naam van de naamruimte moet beknopt zijn en mag alleen toegestane tekens bevatten in overeenstemming met de XML-naamgevingsregels.
>
>Id&#39;s mogen niet beginnen met numerieke tekens.
>
>De volgende naamruimten zijn gereserveerd voor beschrijvingen van de systeementiteiten die vereist zijn voor de werking van de Adobe Campaign-toepassing en mogen niet worden gebruikt: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.

