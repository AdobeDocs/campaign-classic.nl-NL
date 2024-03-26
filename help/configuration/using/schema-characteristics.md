---
product: campaign
title: Schema-eigenschappen
description: Schema-eigenschappen
feature: Custom Resources
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '392'
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

Bronschema&#39;s accepteren de **weergave** kenmerk voor de **srcSchema** hoofdelement. Deze moet worden gebruikt wanneer Adobe Campaign wordt gemanipuleerd in aangepaste tabellen. De **view=&quot;true&quot;** dit kenmerk vertelt de updatewizard voor de databasestructuur om dit schema te negeren. Het is daarom niet toegestaan dat de toepassing de tabel, de kolommen en de indexen synchroniseert met het corresponderende schema.

Wanneer dit kenmerk is ingesteld op **true**, wordt het schema gebruikt slechts om SQL vragen te produceren om tot de gegevens van deze lijst toegang te hebben.

## Namen van tabellen en kolommen {#names-of-tables-and-columns}

Wanneer tabellen worden gemaakt door de wizard voor tabelupdates, worden de namen van tabellen en kolommen automatisch gegenereerd op basis van de namen van de respectievelijke schema&#39;s en kenmerken. Het is echter mogelijk om de SQL-namen te forceren die moeten worden gebruikt door de volgende kenmerken in te voeren:

* **sqltable** binnen het hoofdelement van het schema om de tabel op te geven;
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

Als in dit voorbeeld de namen van de tabellen en kolommen niet expliciet waren opgegeven, zou de toepassing zijn gebruikt **CusIndividual** voor de tabel, **lastName** en **firstName** voor de kolommen.

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

Een index wordt impliciet gedeclareerd voor elke sleutel- en koppelingsdeclaratie van het bronschema. Indexdeclaratie kan worden voorkomen door de **noDbIndex=&quot;true&quot;** kenmerk:

**Voorbeeld**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
