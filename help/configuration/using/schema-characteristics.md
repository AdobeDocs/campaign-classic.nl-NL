---
solution: Campaign Classic
product: campaign
title: Schema-eigenschappen
description: Schema-eigenschappen
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---


# Schema-eigenschappen{#schema-characteristics}

De kenmerken van een schema dat verwijzingen een bestaande lijst zijn als volgt:

* Adobe Campaign mag SQL-objecten niet wijzigen ten opzichte van bestaande tabellen.
* De namen van tabellen en kolommen moeten expliciet worden vermeld.
* Indexen moeten worden gedeclareerd.

>[!IMPORTANT]
>
>Verwijder geen velden uit de standaardtabel voor ontvangers, zelfs niet als deze geen nut hebben. Dit kan gedragsfouten in de Adobe Campaign-database veroorzaken.

## Het weergavekenmerk {#the-view-attribute}

De bronschema&#39;s keuren de **meningsattributen** voor het **srcSchema** wortelelement goed. Deze moet worden gebruikt wanneer Adobe Campaign wordt gemanipuleerd in aangepaste tabellen. Het **kenmerk view=&quot;true&quot;** vertelt de updatetovenaar van de databasestructuur om dit schema te negeren. Het is daarom niet toegestaan dat de toepassing de tabel, de kolommen en de indexen synchroniseert met het corresponderende schema.

Wanneer dit kenmerk is ingesteld op **true**, wordt het schema alleen gebruikt om SQL-query&#39;s te genereren voor toegang tot de gegevens van deze tabel.

## Namen van tabellen en kolommen {#names-of-tables-and-columns}

Wanneer tabellen worden gemaakt door de wizard voor tabelupdates, worden de namen van tabellen en kolommen automatisch gegenereerd op basis van de namen van de respectievelijke schema&#39;s en kenmerken. Het is echter mogelijk om de SQL-namen te forceren die moeten worden gebruikt door de volgende kenmerken in te voeren:

* **sqltable** binnen het belangrijkste element van het schema, om de lijst te specificeren,
* **sqlname** binnen elk attribuut, om de kolommen te specificeren.

**Voorbeeld**:

```
<element label="Individual" name="individual" sqltable="individual">
    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key> 
    <attribute name="id" type="long" length="32" />
    <attribute name="lastName" type="string" length="100" sqlname="Last_Name"/>
    <attribute name="firstName" type="string" length="100" sqlname="First_Name"/>
    <attribute name="email" type="string" length="100"/>
    <attribute name="mobile" type="string" length="100"/>
</element>
```

In dit voorbeeld, als de namen van de lijsten en de kolommen niet uitdrukkelijk waren gespecificeerd, zou de toepassing **CusIndividual** voor de lijst, **lastName** en **firstName** voor de kolommen hebben gebruikt.

In een schema, is het mogelijk om slechts een deel van de kolommen van een bestaande lijst te bevolken. Niet-gevulde kolommen zijn niet toegankelijk voor de gebruiker.

## Geïndexeerde velden {#indexed-fields}

Wanneer u de records van een lijst sorteert op de clientconsole, krijgt u betere prestaties door te sorteren op geïndexeerde velden. Door een index in een schema te declareren, geeft de console de geïndexeerde velden weer met een rode lijn onder de sorteervolgordepijl links van het kolomlabel, zoals hieronder wordt getoond:

![](assets/s_ncs_integration_mapping_index.png)

In een schema wordt een index als volgt gedefinieerd:

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

Daarom is het belangrijk om bestaande indexen van de douanetabel in het passende schema te verklaren.

Een index wordt impliciet gedeclareerd voor elke sleutel- en koppelingsdeclaratie van het bronschema. Indexdeclaratie kan worden voorkomen door het kenmerk **noDbIndex=&quot;true&quot;** op te geven:

**Voorbeeld**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```

