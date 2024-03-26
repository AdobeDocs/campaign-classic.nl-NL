---
product: campaign
title: Schema van een bestaande tabel
description: Schema van een bestaande tabel
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 10%

---

# Schema van een bestaande tabel{#schema-of-an-existing-table}

## Overzicht {#overview}

Wanneer de toepassing toegang moet krijgen tot de gegevens van een bestaande tabel, een SQL-weergave of gegevens uit een externe database, maakt u het schema in Adobe Campaign met de volgende gegevens:

* Naam van tabel: voer de naam in van de tabel (met de alias wanneer een koppeling wordt gebruikt) met het kenmerk &quot;sqltable&quot;.
* schemasleutel: verwijzing naar het (de) afstemmingsveld(en);
* indexen: gebruikt om query&#39;s te genereren;
* De velden en hun locatie in de XML-structuur: vul alleen de velden in die in de toepassing worden gebruikt.
* koppelingen: als er verbindingen zijn met de andere tabellen in de basis.

## Implementatie {#implementation}

Pas de volgende stappen toe om het bijbehorende schema te maken:

1. Bewerk de **[!UICONTROL Administration>Configuration>Data schemas]** knoop van de boom van Adobe Campaign en klik **[!UICONTROL New]** .
1. Selecteer de **[!UICONTROL Access data from an existing table or an SQL view]** en klik op **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Kies de tabel of de bestaande weergave:

   ![](assets/s_ncs_configuration_select_table.png)

1. Pas de schemainhoud aan uw behoeften aan.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Het schema moet worden gevuld met het kenmerk view=&quot;true&quot; op het tabblad `<srcSchema>` basiselement om geen SQL-script voor het maken van tabellen te genereren.

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

De **Federale gegevenstoegang - FDA** hebt u toegang tot de gegevens die in een externe database zijn opgeslagen.

De configuratie die op de schema&#39;s moet worden gedragen om tot gegevens in een externe gegevensbestand toegang te hebben is gedetailleerd in [deze pagina](../../installation/using/creating-data-schema.md).
