---
product: campaign
title: Schema-eigenschappen
description: Schema-eigenschappen
feature: Custom Resources
role: Data Engineer, Developer
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 1%

---

# Schema-eigenschappen{#schema-characteristics}



De kenmerken van een schema dat verwijzingen een bestaande lijst zijn als volgt:

* Adobe Campaign mag SQL-objecten niet wijzigen ten opzichte van bestaande tabellen.
* De namen van tabellen en kolommen moeten expliciet worden vermeld.
* Indexen moeten worden gedeclareerd.

>[!IMPORTANT]
>
>Verwijder geen velden in de ingebouwde tabel voor ontvangers, zelfs niet als deze geen nut hebben. Dit kan gedragsfouten in de Adobe Campaign-database veroorzaken.

## Het weergavekenmerk {#the-view-attribute}

De schema&#39;s van Source keuren het **mening** attribuut voor het **srcSchema** wortelelement goed. Deze moet worden gebruikt wanneer Adobe Campaign wordt gemanipuleerd in aangepaste tabellen. Het **view= &quot;waar&quot;** attribuut vertelt de updateassistent van de gegevensbestandstructuur om dit schema te negeren. Het is daarom niet toegestaan dat de toepassing de tabel, de kolommen en de indexen synchroniseert met het corresponderende schema.

Wanneer dit attribuut aan **waar** wordt geplaatst, wordt het schema gebruikt slechts om SQL vragen te produceren om tot de gegevens van deze lijst toegang te hebben.

## Namen van tabellen en kolommen {#names-of-tables-and-columns}

Wanneer de lijsten door de hulp van de lijstupdate worden gecreeerd, worden de namen van lijsten en kolommen automatisch geproduceerd gebaseerd op de namen van de respectieve schema&#39;s en de attributen. Het is echter mogelijk om de SQL-namen te forceren die moeten worden gebruikt door de volgende kenmerken in te voeren:

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

In een schema is het mogelijk slechts een deel van de kolommen van een bestaande tabel te vullen. Niet-gevulde kolommen zijn niet toegankelijk voor de gebruiker.

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

Een index wordt impliciet gedeclareerd voor elke sleutel- en koppelingsdeclaratie van het bronschema. De verklaring van de index kan worden verhinderd door **te specificeren noDbIndex= &quot;waar&quot;** attributen:

**Voorbeeld**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
