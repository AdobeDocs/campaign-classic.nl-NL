---
product: campaign
title: SQL Data Management
description: Meer informatie over de workflowactiviteit van SQL Data Management
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: cada78cb-658f-4b9e-8136-31c17cb1d82f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 4%

---

# SQL-gegevensbeheer{#sql-data-management}

![](../../assets/common.svg)

Met de activiteit **SQL-gegevensbeheer** kunt u uw eigen SQL-scripts schrijven om werktabellen te maken en te vullen.

## Vereisten {#prerequisites}

Voordat u de activiteit configureert, moet u controleren of aan de volgende voorwaarden is voldaan:

* De activiteit is beschikbaar voor verre slechts gegevensbronnen. Het **[!UICONTROL FDA]** (Federated Data Access)-pakket moet daarom op uw instantie worden geïnstalleerd. [Meer info](../../installation/using/about-fda.md).

   Raadpleeg de volgende secties voor meer informatie, afhankelijk van uw campagneversie:

   ![](assets/do-not-localize/v7.jpeg)[  Documentatie voor Campaign v7](../../installation/using/about-fda.md)

   ![](assets/do-not-localize/v8.png)[  Documentatie voor Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html)

* Het uitgaande schema moet in het gegevensbestand bestaan en met een gegevensbestand FDA worden verbonden.
* De exploitant die het werkschema uitvoert moet **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** genoemd hebben recht. [Meer info](../../platform/using/access-management-named-rights.md).

## De SQL-gegevensbeheeractiviteit configureren {#configuring-the-sql-data-management-activity}

1. Geef de activiteit **[!UICONTROL Label]** op.
1. Selecteer **[!UICONTROL External account]** aan gebruik, dan selecteren **[!UICONTROL Outbound schema]** verbonden aan deze externe rekening.

   >[!CAUTION]
   >
   >Het uitgaande schema is vast en kan niet worden bewerkt.

1. Voeg het SQL-script toe.

   >[!CAUTION]
   >
   >Het is de verantwoordelijkheid van de SQL-scripteigenaar om ervoor te zorgen dat het SQL-script functioneel is en dat de referenties ervan (veldnamen, enz.) zijn in overeenstemming met het Uitgaande schema.

   Als u een bestaande SQL-code wilt laden, selecteert u de optie **[!UICONTROL The SQL script is contained in an entity stored in the database]**. SQL-scripts moeten worden gemaakt en opgeslagen in het menu **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]**.

   Anders typt of kopieert u het SQL-script in het daarvoor bestemde gebied.

   ![](assets/sql_datamanagement.png)

   Met deze activiteit kunt u de volgende variabelen in het script gebruiken:

   * **activity.tableName**: SQL-naam van de uitgaande werktabel.
   * **task.innerTransitionByName(&quot;name&quot;).tableName**: SQL naam van de het werklijst die door de inkomende overgang wordt gedragen te gebruiken (de overgang wordt geïdentificeerd door zijn naam).

      >[!NOTE]
      >
      >De waarde (&#39;name&#39;) komt overeen met het veld **[!UICONTROL Name]** van de overgangseigenschappen.

1. Als het SQL manuscript reeds bevelen bevat om een uitgaande het werklijst tot stand te brengen, unselect de **[!UICONTROL Automatically create work table]** optie. Anders wordt automatisch een werktabel gemaakt zodra de workflow wordt uitgevoerd.
1. Klik **[!UICONTROL Ok]** om de activiteitenconfiguratie te bevestigen.

De activiteit wordt nu gevormd. Het is klaar om in het werkschema te worden uitgevoerd.

>[!CAUTION]
>
>Zodra de uitgevoerde activiteit, is de uitgaande telling van overgangsverslagen slechts indicatief. Deze kan variëren afhankelijk van het complexiteitsniveau van het SQL-script.
>  
>Als de activiteit opnieuw is begonnen, wordt het volledige manuscript uitgevoerd vanaf zijn begin, ongeacht het uitvoerstatus.

## SQL-scriptvoorbeelden {#sql-script-samples}

>[!NOTE]
>
>De manuscriptsteekproeven in deze sectie moeten onder PostgreSQL worden uitgevoerd.

Met het onderstaande script kunt u een werktabel maken en gegevens in dezelfde werktabel invoegen:

```
CREATE UNLOGGED TABLE <%= activity.tableName %> (
  iRecipientId INTEGER DEFAULT 0,
  sFirstName VARCHAR(100),
  sMiddleName VARCHAR(100),
  sLastName VARCHAR(100),
  sEmail VARCHAR(100)
);

INSERT INTO <%= activity.tableName %>
SELECT iRecipientId, sFirstName, sMiddleName, sLastName, sEmail
FROM nmsRecipient
GROUP BY iRecipientId, sFirstName, sMiddleName, sLastName, sEmail;
```

Met het onderstaande script kunt u een CTAS-bewerking (CREATE TABLE AS SELECT) uitvoeren en een werktabelindex maken:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

Met het onderstaande script kunt u twee werktabellen samenvoegen:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```
