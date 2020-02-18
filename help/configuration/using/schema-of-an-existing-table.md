---
title: Schema van een bestaande tabel
seo-title: Schema van een bestaande tabel
description: Schema van een bestaande tabel
seo-description: null
page-status-flag: never-activated
uuid: cb766259-8ed7-40a1-8df7-75a8a3f9986d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6877d94d-d6e5-4080-a537-ef1bb6e6f8cf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# Schema van een bestaande tabel{#schema-of-an-existing-table}

## Overzicht {#overview}

Wanneer de toepassing toegang moet krijgen tot de gegevens van een bestaande tabel, een SQL-weergave of gegevens uit een externe database, maakt u het schema in Adobe Campagne met de volgende gegevens:

* Naam van tabel: Voer de naam van de tabel (met de alias wanneer een koppeling wordt gebruikt) in met het kenmerk &quot;sqltable&quot;,
* schemasleutel: verwijzing naar het (de) afstemmingsveld(en);
* indexen: gebruikt om vragen te produceren,
* De velden en hun locatie in de XML-structuur: alleen de velden invullen die in de toepassing worden gebruikt;
* koppelingen: als er verbindingen met de andere lijsten van de basis zijn.

## Implementatie {#implementation}

Pas de volgende stappen toe om het bijbehorende schema te maken:

1. Bewerk het **[!UICONTROL Administration>Configuration>Data schemas]** knooppunt van de Adobe Campaign-structuur en klik **[!UICONTROL New]** .
1. Selecteer de **[!UICONTROL Access data from an existing table or an SQL view]** optie en klik **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Kies de tabel of de bestaande weergave:

   ![](assets/s_ncs_configuration_select_table.png)

1. Pas de schemainhoud aan uw behoeften aan.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Het schema moet worden gevuld met het kenmerk view=&quot;true&quot; op het `<srcSchema>` basiselement om geen SQL-script voor het maken van tabellen te genereren.

**Voorbeeld** :

```
<srcSchema name="recipient" namespace="cus" view="true">
  <element name="recipient" sqltable="dbsrv.recipient">
    <key name="email">
      <keyfield xpath="@email"/>
    </key>   
    <attribute name="email" type="string" length="80" sqlname="email"/>
  </element>
</srcSchema>
```

## Een externe database openen {#accessing-an-external-database}

Met de optie **Federated Data Access - FDA** hebt u toegang tot de gegevens die in een externe database zijn opgeslagen.

De configuratie die op de schema&#39;s moet worden gedragen om tot gegevens in een extern gegevensbestand toegang te hebben is gedetailleerd in [deze pagina](../../platform/using/creating-data-schema.md).
