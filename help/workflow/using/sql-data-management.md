---
product: campaign
title: SQL Data Management
description: Meer informatie over de workflowactiviteit van SQL Data Management
feature: Workflows
exl-id: cada78cb-658f-4b9e-8136-31c17cb1d82f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 2%

---

# SQL Data Management{#sql-data-management}



De **SQL-gegevensbeheer** Met activiteit kunt u uw eigen SQL-scripts schrijven om werktabellen te maken en te vullen.

## Vereisten {#prerequisites}

Voordat u de activiteit configureert, moet u controleren of aan de volgende voorwaarden is voldaan:

* De activiteit is beschikbaar voor verre slechts gegevensbronnen. De **[!UICONTROL FDA]** (Federated Data Access) moet daarom op uw exemplaar worden geïnstalleerd. [Meer informatie](../../installation/using/about-fda.md).

  Raadpleeg de volgende secties voor meer informatie, afhankelijk van uw campagneversie:

  ![](assets/do-not-localize/v7.jpeg)[Campagne v7-documentatie](../../installation/using/about-fda.md)

  ![](assets/do-not-localize/v8.png)[Campagne v8-documentatie](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html)

* Het uitgaande schema moet in het gegevensbestand bestaan en met een gegevensbestand FDA worden verbonden.
* De exploitant die het werkschema uitvoert moet hebben **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** genoemd recht. [Meer informatie](../../platform/using/access-management-named-rights.md).

## De SQL-gegevensbeheeractiviteit configureren {#configuring-the-sql-data-management-activity}

1. De activiteit opgeven **[!UICONTROL Label]**.
1. Selecteer de **[!UICONTROL External account]** om te gebruiken, dan selecteren **[!UICONTROL Outbound schema]** aan deze externe rekening gekoppeld.

   >[!CAUTION]
   >
   >Het uitgaande schema is vast en kan niet worden bewerkt.

1. Voeg het SQL-script toe.

   >[!CAUTION]
   >
   >Het is de verantwoordelijkheid van de SQL-scripteigenaar om ervoor te zorgen dat het SQL-script functioneel is en dat de referenties ervan (veldnamen, enz.) zijn in overeenstemming met het Uitgaande schema.

   Als u een bestaande SQL-code wilt laden, selecteert u de **[!UICONTROL The SQL script is contained in an entity stored in the database]** -optie. SQL-scripts moeten worden gemaakt en opgeslagen in de **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** -menu.

   Anders typt of kopieert u het SQL-script in het daarvoor bestemde gebied.

   ![](assets/sql_datamanagement.png)

   Met deze activiteit kunt u de volgende variabelen in het script gebruiken:

   * **activity.tableName**: SQL-naam van de uitgaande werktabel.
   * **task.innerTransitionByName(&quot;name&quot;).tableName**: SQL-naam van de werktabel die wordt gedragen door de inkomende overgang die moet worden gebruikt (de overgang wordt aangeduid met de naam ervan).

     >[!NOTE]
     >
     >De waarde (&#39;name&#39;) komt overeen met de **[!UICONTROL Name]** van de overgangseigenschappen.

1. Als het SQL-script al opdrachten bevat om een uitgaande werktabel te maken, schakelt u de optie **[!UICONTROL Automatically create work table]** -optie. Anders wordt automatisch een werktabel gemaakt zodra de workflow wordt uitgevoerd.
1. Klikken **[!UICONTROL Ok]** om de activiteitenconfiguratie te bevestigen.

De activiteit wordt nu gevormd. Het kan worden uitgevoerd in de workflow.

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
