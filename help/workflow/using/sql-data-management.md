---
title: SQL-gegevensbeheer
seo-title: SQL-gegevensbeheer
description: SQL-gegevensbeheer
seo-description: null
page-status-flag: never-activated
uuid: b6057496-2dd5-4289-96df-98378e4f0ae7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 18d6f5e1-308f-4080-b7c4-ebf836f74842
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# SQL-gegevensbeheer{#sql-data-management}

Met de activiteit **SQL-gegevensbeheer** kunt u uw eigen SQL-scripts schrijven om werktabellen te maken en te vullen.

## Vereisten {#prerequisites}

Voordat u de activiteit configureert, moet u controleren of aan de volgende voorwaarden is voldaan:

* De activiteit is beschikbaar voor verre slechts gegevensbronnen. Het pakket **[!UICONTROL FDA]** (Federated Data Access) moet daarom op uw exemplaar worden geïnstalleerd (zie [deze sectie](../../platform/using/accessing-an-external-database.md)).
* Het uitgaande schema moet in het gegevensbestand bestaan en met een gegevensbestand FDA (voor meer op gegevensschema&#39;s, verwijs naar [deze sectie](../../configuration/using/about-schema-reference.md)) worden verbonden.
* De exploitant die het werkschema uitvoert moet het **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** genoemde recht hebben. Raadpleeg [deze sectie](../../platform/using/access-management.md#named-rights)voor meer informatie over benoemde rechten.

## De SQL-gegevensbeheeractiviteit configureren {#configuring-the-sql-data-management-activity}

1. Geef de activiteit op **[!UICONTROL Label]**.
1. Selecteer de **[!UICONTROL External account]** te gebruiken account en selecteer de **[!UICONTROL Outbound schema]** gekoppelde account.

   >[!CAUTION]
   >
   >Het uitgaande schema is vast en kan niet worden bewerkt.

1. Voeg het SQL-script toe.

   >[!CAUTION]
   >
   >Het is de verantwoordelijkheid van de SQL-scripteigenaar om ervoor te zorgen dat het SQL-script functioneel is en dat de referenties ervan (veldnamen, enz.) zijn in overeenstemming met het Uitgaande schema.

   Als u een bestaande SQL-code wilt laden, selecteert u de **[!UICONTROL The SQL script is contained in an entity stored in the database]** optie. SQL-scripts moeten worden gemaakt en opgeslagen in het menu **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** .

   Anders typt of kopieert u het SQL-script in het daarvoor bestemde gebied.

   ![](assets/sql_datamanagement.png)

   Met deze activiteit kunt u de volgende variabelen in het script gebruiken:

   * **activity.tableName**: SQL-naam van de uitgaande werktabel.
   * **task.innerTransitionByName(&quot;name&quot;).tableName**: SQL naam van de het werklijst die door de inkomende overgang wordt gedragen te gebruiken (de overgang wordt geïdentificeerd door zijn naam).

      >[!NOTE]
      >
      >De waarde (&#39;name&#39;) komt overeen met het **[!UICONTROL Name]** veld van de overgangseigenschappen.

1. Als het SQL-script al opdrachten bevat om een uitgaande werktabel te maken, schakelt u de **[!UICONTROL Automatically create work table]** optie uit. Anders wordt automatisch een werktabel gemaakt zodra de workflow wordt uitgevoerd.
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

