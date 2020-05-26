---
title: RDBMS - Specifieke aanbevelingen
seo-title: RDBMS - Specifieke aanbevelingen
description: RDBMS - Specifieke aanbevelingen
seo-description: null
page-status-flag: never-activated
uuid: 637c1b5a-0484-4734-a012-eb4ba8036263
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: b2219912-5570-45d2-8b52-52486e29d008
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 0%

---


# RDBMS - Specifieke aanbevelingen{#rdbms-specific-recommendations}

In deze sectie worden enkele aanbevelingen/aanbevolen procedures beschreven die zijn aangepast aan de verschillende RDBMS-engines die door Adobe Campaign worden ondersteund, zodat u onderhoudsplannen kunt instellen. Dit zijn echter slechts aanbevelingen. Het is aan u om deze aan uw behoeften aan te passen, overeenkomstig uw interne procedure en beperkingen. Uw gegevensbestandbeheerder heeft de verantwoordelijkheid om deze plannen te bouwen en uit te voeren.

## PostgreSQL {#postgresql}

### Grote tabellen detecteren {#detecting-large-tables}

1. U kunt de volgende weergave aan uw database toevoegen:

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8 / 1024 AS size_mbytes, c2.relfilenode AS filename, 0 AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION 
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8 / 1024 AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as integer) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. Als u de volgende opdracht uitvoert, kunt u grote tabellen en indexen tekenen:

   ```
   select * from uvSpace;
   ```

### Eenvoudig onderhoud {#simple-maintenance}

Onder PostgreSQL, zijn de typische bevelen u **vacuüm volledig** en **herdex** kunt gebruiken.

Hier volgt een typisch voorbeeld van een SQL-onderhoudsplan dat regelmatig moet worden uitgevoerd met behulp van deze twee opdrachten:

```
vacuum full nmsdelivery;
 reindex table nmsdelivery;
 
 vacuum full nmsdeliverystat;
 reindex table nmsdeliverystat;
 
 vacuum full xtkworkflow;
 reindex table xtkworkflow;
 
 vacuum full xtkworkflowevent;
 reindex table xtkworkflowevent;
 
 vacuum full xtkworkflowjob;
 reindex table xtkworkflowjob;
 
 vacuum full xtkworkflowlog;
 reindex table xtkworkflowlog;
 
 vacuum full xtkworkflowtask;
 reindex table xtkworkflowtask;
 
 vacuum full xtkjoblog;
 reindex table xtkjoblog;
 
 vacuum full xtkjob;
 reindex table xtkjob;
 
 vacuum full nmsaddress;
 reindex table nmsaddress;

 vacuum full nmsdeliverypart;
 reindex table nmsdeliverypart;
 
 vacuum full nmsmirrorpageinfo;
 reindex table nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe raadt u aan om kleinere tabellen te gebruiken: als het proces op grote tabellen mislukt ( waarbij het risico van mislukking het grootst is ) , is ten minste een deel van het onderhoud voltooid .
>* Adobe raadt u aan de tabellen toe te voegen die specifiek zijn voor uw gegevensmodel en die kunnen worden bijgewerkt. Dit kan het geval voor **NmsRecipient** zijn als u grote dagelijkse gegevensreplicatiestromen hebt.
>* De **vacuüm** en **re-index** bevelen zullen de lijst sluiten, die sommige processen onderbreekt terwijl het onderhoud wordt uitgevoerd.
>* Voor zeer grote tabellen (meestal boven 5 GB) kan **vacuüm vol** tamelijk inefficiënt worden en erg lang duren. Adobe raadt u niet aan deze methode te gebruiken voor de **tabel YyyNmsBroadLogXxx** .
>* Deze onderhoudsbewerking kan worden geïmplementeerd door een Adobe Campagne-workflow met een **[!UICONTROL SQL]** activiteit (zie [deze sectie](../../workflow/using/architecture.md)voor meer informatie). Zorg ervoor dat u onderhoud plant voor een lage activiteitstijd die niet in strijd is met uw back-upvenster.
>



### Database opnieuw samenstellen {#rebuilding-a-database}

PostgreSQL biedt geen eenvoudige manier om een online tabel opnieuw samen te stellen, aangezien **vacuüm de tabel volledig** vergrendelt en zo een normale productie voorkomt. Dit betekent dat onderhoud moet worden uitgevoerd wanneer de tabel niet wordt gebruikt. U kunt:

* onderhoud uitvoeren wanneer het Adobe Campagne-platform wordt gestopt,
* Stop de diverse subservices van Adobe Campagne die waarschijnlijk in de tabel zullen schrijven die opnieuw wordt samengesteld (**nlserver stop wfserver instance_name** om het werkstroomproces te stoppen).

Hier is een voorbeeld van lijstdefragmentatie gebruikend specifieke functies om noodzakelijke DDL te produceren. Met de volgende SQL kunt u twee nieuwe functies maken: **GenRebuildTablePart1** en **GenRebuildTablePart2**, die kunnen worden gebruikt om de noodzakelijke DDL te produceren om een lijst te ontspannen.

* Met de eerste functie kunt u (** _tmp** hier) een werktabel maken die een kopie is van de oorspronkelijke tabel.
* De tweede functie verwijdert vervolgens de oorspronkelijke tabel en wijzigt de naam van de werktabel en de bijbehorende indexen.
* Het gebruik van twee functies in plaats van één betekent dat als de eerste functie mislukt, u niet het risico loopt de oorspronkelijke tabel te verwijderen.

```
 -- --------------------------------------------------------------------------
 -- Generate the CREATE TABLE DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenTableDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecFld RECORD;
 vstrDDL text;
 vstrFields text;
 vstrNsTable text;
 vstrTableSpace text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 SELECT
 pg_catalog.quote_ident(n.nspname) || '.' || pg_catalog.quote_ident(c.relname),
 pg_catalog.quote_ident(t.spcname)
 INTO
 vstrNsTable, vstrTableSpace
 FROM
 pg_namespace n, pg_class c left outer join pg_tablespace t on c.reltablespace = t.oid
 WHERE
 n.oid = c.relnamespace AND
 c.relname = vstrTable;
 
 vstrDDL = 'CREATE TABLE ' || vstrNsTable || '_tmp(';
 
 vstrFields = ;
 FOR vrecFld IN
 SELECT
 pg_catalog.quote_ident(a.attname) ||
 ' ' || t.typname ||
 case when t.typname='varchar' then '(' || cast(a.atttypmod-4 as text) || ')'
 when t.typname='numeric' then '(' || cast((a.atttypmod-4)/65536 as text) || ',' || cast((a.atttypmod-4)%65536 as text) || ')'
 else end ||
 case when a.attnotnull then ' not null' else end ||
 case when a.atthasdef then ' default '|| d.adsrc else end as DDL
 FROM
 pg_type t, pg_class c, pg_attribute a LEFT OUTER JOIN pg_attrdef d ON d.adrelid=a.attrelid and d.adnum=a.attnum
 WHERE 
 a.attnum > 0 AND
 a.attrelid = c.oid AND
 t.oid = a.atttypid AND
 c.relname = vstrTable
 ORDER BY
 a.attnum
 LOOP
 IF vstrFields <> THEN
 vstrFields = vstrFields || ',' || chr(10) || ' ';
 ELSE
 vstrFields = vstrFields || chr(10) || ' ';
 END IF;
 vstrFields = vstrFields || vrecFld.DDL;
 END LOOP;
 
 vstrDDL = vstrDDL || vstrFields || chr(10) || ')';
 if vstrTableSpace <> then
 vstrDDL = vstrDDL || ' TABLESPACE ' || vstrTableSpace;
 end if;
 vstrDDL = vstrDDL || ';' || chr(10);
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the CREATE INDEX DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 viFld integer;
 vstrFld text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
 SELECT
 i.indkey, i.indisunique,
 pg_catalog.quote_ident(c.relname) as tablename,
 pg_catalog.quote_ident(ic.relname) as indexname,
 pg_catalog.quote_ident(t.spcname) as tablespace
 FROM
 pg_class c, pg_index i, pg_class ic left outer join pg_tablespace t on ic.reltablespace = t.oid
 WHERE
 i.indexrelid = ic.oid AND
 i.indrelid = c.oid AND
 c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'CREATE ';
  if vrecIndex.indisunique then
  vstrDDL = vstrDDL || 'UNIQUE ';
  end if;
  vstrDDL = vstrDDL ||
   'INDEX ' ||vrecIndex.indexname || '_tmp ON ' ||
   vrecIndex.tablename || '_tmp(';
 
  FOR viFld IN array_lower(vrecIndex.indkey, 1) .. array_upper(vrecIndex.indkey, 1) LOOP
  SELECT pg_catalog.quote_ident(a.attname) INTO vstrFld 
  FROM 
   pg_attribute a, pg_class c
  WHERE 
   a.attnum = vrecIndex.indkey[viFld] AND
   a.attrelid = c.oid AND c.relname=vstrTable;
  
  vstrDDL = vstrDDL || vstrFld;
  if viFld <> array_upper(vrecIndex.indkey, 1) then
   vstrDDL = vstrDDL || ', ';
  end if;
  END LOOP;
  vstrDDL = vstrDDL || ')';
 
  if vrecIndex.tablespace <> then
  vstrDDL = vstrDDL || 'TABLESPACE ' || vrecIndex.tablespace;
  end if;
  vstrDDL = vstrDDL || ';' || chr(10);
 
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the ALTER INDEX RENAME for a table
 -- --------------------------------------------------------------------------
 create or replace function GenRenameIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
  SELECT
  pg_catalog.quote_ident(n.nspname) as namespace,
  pg_catalog.quote_ident(ic.relname) as indexname
  FROM
  pg_namespace n, pg_class c, pg_index i, pg_class ic
  WHERE
  i.indexrelid = ic.oid AND
  n.oid = ic.relnamespace AND
  i.indrelid = c.oid AND
  c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'ALTER INDEX ' || vrecIndex.namespace || '.' || vrecIndex.indexname ||
    '_tmp RENAME TO ' || vrecIndex.indexname ||
    ';' || chr(10);
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Build a copy of a table, with index
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart1(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = ;
 
 SELECT GenTableDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 vstrDDL = vstrDDL|| 'INSERT INTO ' || vstrTable || '_tmp SELECT * FROM ' || vstrTable || ';'||chr(10);
 SELECT GenIndexDDL(vstrTable) INTO vstrTmp;
 
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 vstrDDL = vstrDDL|| 'VACUUM ANALYSE '|| vstrTable || '_tmp;' ||chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
 
 -- --------------------------------------------------------------------------
 -- Drop the original table and rename the copy
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart2(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = 'DROP TABLE ' || vstrTable||';'|| chr(10);
 vstrDDL = vstrDDL|| 'ALTER TABLE ' || vstrTable || '_tmp RENAME TO ' || vstrTable ||';'|| chr(10);
 
 SELECT GenRenameIndexDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
```

Het volgende voorbeeld kan in een werkschema worden gebruikt om de vereiste lijsten te herbouwen eerder dan het gebruiken van het **vacuüm/rebuild** bevel:

```
function sqlGetMemo(strSql)
 {
 var res = sqlSelect("s, m:memo", strSql);
 return res.s.m.toString();
 }

 function RebuildTable(strTable)
 {
 // Rebuild a table_tmp
 var strSql = sqlGetMemo("select GenRebuildTablePart1('"+strTable+"')");
 logInfo("Rebuilding table '"+strTable+"'...");
 // logInfo(strSql);
 sqlExec(strSql);
 
 // If fails, there is an exception thrown and so we do not delete the original table
 strSql = sqlGetMemo("select GenRebuildTablePart2('"+strTable+"')");
 logInfo("Swapping table '"+strTable+"'...");
 //logInfo(strSql);
 sqlExec(strSql);
 }
 
 RebuildTable('nmsrecipient');
 RebuildTable('nmsrcpgrlrel');
 // ... other tables here
```

## Oracle {#oracle}

Neem contact op met uw databasebeheerder voor informatie over de procedures die het meest geschikt zijn voor uw versie van Oracle.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Voor de Server van Microsoft SQL, kunt u het onderhoudsplan gebruiken dat [in deze pagina](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html)wordt gedetailleerd.

Het onderstaande voorbeeld heeft betrekking op Microsoft SQL Server 2005. Als u een andere versie gebruikt, neemt u contact op met uw databasebeheerder voor informatie over onderhoudsprocedures.

1. Eerst, verbind met de Studio van het Beheer van de Server van Microsoft SQL, met login met beheerderrechten.
1. Ga naar de **[!UICONTROL Management > Maintenance Plans]** map, klik er met de rechtermuisknop op en kies **[!UICONTROL Maintenance Plan Wizard]**
1. Klik **[!UICONTROL Next]** wanneer de eerste pagina omhoog komt.
1. Selecteer het type onderhoudsplan u (afzonderlijke programma&#39;s voor elke taak of één enkel programma voor het volledige plan) wilt creëren, dan klik de **[!UICONTROL Change...]** knoop.
1. Selecteer in het **[!UICONTROL Job schedule properties]** venster de gewenste instellingen voor de uitvoering en klik **[!UICONTROL OK]** op **[!UICONTROL Next]** .
1. Selecteer de onderhoudstaken die u wilt uitvoeren en klik op **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >We raden u aan ten minste de hieronder weergegeven onderhoudstaken uit te voeren. U kunt ook de statistische updatetaak selecteren, hoewel deze al wordt uitgevoerd door de workflow voor het opschonen van databases.

1. Selecteer in de vervolgkeuzelijst de database waarop u de **[!UICONTROL Database Check Integrity]** taak wilt uitvoeren.
1. Selecteer de database en klik **[!UICONTROL OK]** op **[!UICONTROL Next]** .
1. Vorm de maximumgrootte die aan uw gegevensbestand wordt toegewezen, dan klik **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >Als de grootte van de database deze drempel overschrijdt, probeert het onderhoudsplan ongebruikte gegevens te verwijderen om ruimte vrij te maken.

1. De index opnieuw ordenen of opnieuw genereren:

   * Als het indexfragmentatietempo tussen 10% en 40% ligt, wordt een reorganisatie aanbevolen.

      Kies welke databases en objecten (tabellen of weergaven) u wilt reorganiseren en klik op **[!UICONTROL Next]** .

      >[!NOTE]
      >
      >Afhankelijk van uw configuratie kunt u de eerder geselecteerde tabellen of alle tabellen in uw database kiezen.

   * Als het indexfragmentatietempo hoger is dan 40%, wordt een heropbouw aanbevolen.

      Selecteer de opties die u op de indexherbouwingstaak wilt toepassen en klik op **[!UICONTROL Next]** .

      >[!NOTE]
      >
      >Het rebuild-indexproces is beperkter in termen van processorgebruik en vergrendelt de databasebronnen. Tik op de **[!UICONTROL Keep index online while reindexing]** optie als u de index tijdens het opnieuw samenstellen beschikbaar wilt maken.

1. Selecteer de opties die u in het activiteitenrapport wilt weergeven en klik op **[!UICONTROL Next]** .
1. Controleer de lijst van taken die voor het onderhoudsplan worden gevormd, dan klik **[!UICONTROL Finish]** .

   Er wordt een samenvatting van het onderhoudsplan en de status van de verschillende stappen weergegeven.

1. Klik op **[!UICONTROL Close]** .
1. Dubbelklik in de Microsoft SQL Server-verkenner op de **[!UICONTROL Management > Maintenance Plans]** map.
1. Selecteer het onderhoudsplan van de Campagne van Adobe: de verschillende stappen worden beschreven in een workflow .

   Er is een object gemaakt in de **[!UICONTROL SQL Server Agent > Jobs]** map. Met dit object kunt u het onderhoudsplan starten. In ons voorbeeld is er slechts één object omdat alle onderhoudstaken deel uitmaken van hetzelfde plan.

   >[!CAUTION]
   >
   >Voor dit voorwerp om te lopen, moet de agent van de Server van Microsoft SQL worden toegelaten.

**Een afzonderlijke database voor het werken met tabellen configureren**

>[!NOTE]
>
>Deze configuratie is optioneel.

Met de optie **WdbcOptions_TempDbName** kunt u een afzonderlijke database configureren voor het werken van tabellen op Microsoft SQL Server. Hierdoor worden back-ups en replicatie geoptimaliseerd.

Deze optie kan worden gebruikt als u wilt dat werktabellen (bijvoorbeeld de tabellen die tijdens de uitvoering van een workflow worden gemaakt) op een andere database worden gemaakt.

Wanneer u de optie op &quot;tempdb.dbo.&quot;plaatst, zullen de werkende lijsten op het gebrek tijdelijke gegevensbestand van de Server van Microsoft worden gecreeerd SQL. De gegevensbestandbeheerder moet schrijftoegang tot het tempdb- gegevensbestand toestaan.

Als de optie is ingesteld, wordt deze gebruikt voor alle Microsoft SQL Server-databases die zijn geconfigureerd in Adobe Campagne (hoofddatabase en externe accounts). Als twee externe accounts dezelfde server delen, kunnen er conflicten optreden (omdat tempdb uniek is). Op dezelfde manier, als twee instanties van de Campagne de zelfde server MSSQL gebruiken, zouden er conflicten kunnen zijn als zij de zelfde tempdb gebruiken.
