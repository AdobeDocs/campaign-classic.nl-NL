---
product: campaign
title: RDBMS - Specifieke aanbevelingen
description: RDBMS - Specifieke aanbevelingen
feature: Monitoring
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 1%

---

# RDBMS - Specifieke aanbevelingen{#rdbms-specific-recommendations}



Om u te helpen bij het instellen van onderhoudsplannen, geeft deze sectie een overzicht van een aantal aanbevelingen en aanbevolen procedures die zijn aangepast aan de verschillende RDBMS-engines die Adobe Campaign ondersteunt. Dit zijn echter slechts aanbevelingen. Het is aan u om deze aan uw behoeften aan te passen, in overeenstemming met uw interne procedure en beperkingen. Uw gegevensbestandbeheerder heeft de verantwoordelijkheid om deze plannen te bouwen en uit te voeren.

## PostgreSQL {#postgresql}

### Grote tabellen detecteren {#detecting-large-tables}

1. U kunt de volgende weergave aan uw database toevoegen:

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8  / 1024 AS size_mbytes, c2.relfilenode AS filename, cast(0 AS bigint) AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8  /1024  AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as bigint) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. U kunt deze query uitvoeren om grote tabellen en indexen te zoeken:

   ```
   SELECT * FROM uvSpace;
   ```

   Alternatief, kunt u deze vraag in werking stellen, bijvoorbeeld om alle indexgrootte collectief te zien:

   ```
   SELECT
      tablename,
      sum(size_mbytes) AS "sizeMB_all",
      (
         SELECT sum(size_mbytes)
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_data",
      (
         SELECT sum(size_mbytes)
         FROM uvspace 
         AS uv2 
         WHERE
            INDEXNAME IS NOT NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_index",
      (
         SELECT ROW_COUNT
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS ROWS FROM uvspace AS uv1
      GROUP BY tablename
      ORDER BY 2 DESC
   ```

### Eenvoudig onderhoud {#simple-maintenance}

>[!IMPORTANT]
>
>De Adobe adviseert sterk om VACUUM niet VOLLEDIG op de Adobe-ontvangen gegevensbestandmontages van de Campagne in werking te stellen.Het voorgestelde onderhoud is een gids voor slechts installaties ON-PREMISE. Voor de implementaties en de schema&#39;s van de douanetabel, gebruik VACUUM VOLLEDIG bij uw eigen risico aangezien VACUUM - zonder controle - lijsten exclusief kan sluiten die gestagelde vragen veroorzaken - en in sommige gevallen, omhoog het volledige gegevensbestand blokkeren.

In PostgreSQL, kunt u deze typische sleutelwoorden gebruiken:

* VACUUM (VOLLEDIG, ANALYSEREN, VERBODEN)

Als u de VACUUM-bewerking wilt uitvoeren en analyseren en uitvoeren, kunt u deze syntaxis gebruiken:

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

We raden u aan de ANALYZE-instructie niet weg te laten. Anders wordt de vacuümtabel zonder statistieken weergegeven. De reden is dat er een nieuwe tabel wordt gemaakt en dat de oude tabel wordt verwijderd. Het resultaat is dat de object-id (OID) van de tabel verandert, maar dat er geen statistieken worden berekend. Dit betekent dat u meteen prestatieproblemen zult ondervinden.

Hier volgt een typisch voorbeeld van een SQL-onderhoudsplan dat regelmatig moet worden uitgevoerd:

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdelivery;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverystat;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflow;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowevent;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowlog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowtask;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjoblog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsaddress;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverypart;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe beveelt aan om te beginnen met kleinere tabellen: als het proces op grote tabellen mislukt (waar het risico op mislukking het grootst is), is ten minste een deel van het onderhoud voltooid.
>* Adobe raadt u aan de tabellen toe te voegen die specifiek zijn voor uw gegevensmodel en die kunnen worden bijgewerkt. Dit kan het geval voor **NmsRecipient** zijn als u grote dagelijkse stromen van de gegevensreplicatie hebt.
>* De instructie VACUUM vergrendelt de tabel, die sommige processen onderbreekt terwijl onderhoud wordt uitgevoerd.
>* Voor zeer grote tabellen (doorgaans boven 5 GB) kan de VACUUM FULL-instructie tamelijk inefficiënt worden en erg lang duren. De Adobe adviseert niet gebruikend het voor **YyyNmsBroadLogXxx** lijst.
>* Deze onderhoudsbewerking kan worden geïmplementeerd door een Adobe Campaign-workflow met behulp van een **[!UICONTROL SQL]** -activiteit. Voor meer op dit, verwijs naar [ deze sectie ](../../workflow/using/architecture.md). Zorg ervoor dat u onderhoud plant voor een lage activiteitstijd die niet in strijd is met uw back-upvenster.
>

### Database opnieuw samenstellen {#rebuilding-a-database}

PostgreSQL biedt geen eenvoudige manier om een online tabel opnieuw samen te stellen, aangezien de VACUUM FULL-instructie de tabel vergrendelt, waardoor normale productie wordt voorkomen. Dit betekent dat onderhoud moet worden uitgevoerd wanneer de tabel niet wordt gebruikt. U kunt:

* onderhoud uitvoeren wanneer het Adobe Campaign-platform wordt gestopt;
* einde diverse subservices van Adobe Campaign die waarschijnlijk in de lijst zullen schrijven die wordt herbouwd (**nlserver stop wfserver instance_name** om het werkschemaproces tegen te houden).

Hier is een voorbeeld van lijstdefragmentatie gebruikend specifieke functies om noodzakelijke DDL te produceren. De volgende SQL laat u twee nieuwe functies creëren: **GenRebuildTablePart1** en **GenRebuildTablePart2**, die kunnen worden gebruikt om noodzakelijke DDL te produceren om een lijst te ontspannen.

* Met de eerste functie kunt u (**&#x200B; _tmp** hier) een werktabel maken die een kopie is van de oorspronkelijke tabel.
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

Het volgende voorbeeld kan in een werkschema worden gebruikt om de vereiste lijsten te herbouwen eerder dan het gebruiken van het **vacuum/rebuild** bevel:

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

Neem contact op met de databasebeheerder voor meer informatie over de procedures die het meest geschikt zijn voor uw versie van Oracle.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Voor de Server van Microsoft SQL, kunt u het onderhoudsplan gebruiken dat op [ wordt gedetailleerd deze pagina ](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

Het onderstaande voorbeeld betreft Microsoft SQL Server 2005. Als u een andere versie gebruikt, neemt u contact op met uw databasebeheerder voor informatie over onderhoudsprocedures.

1. Eerst, verbind met de Studio van het Beheer van de Server van Microsoft SQL, met login met beheerderrechten.
1. Ga naar de map **[!UICONTROL Management > Maintenance Plans]** , klik er met de rechtermuisknop op en kies **[!UICONTROL Maintenance Plan Assistant]** .
1. Klik op **[!UICONTROL Next]** wanneer de eerste pagina naar boven komt.
1. Selecteer het type onderhoudsplan dat u wilt maken (afzonderlijke schema&#39;s voor elke taak of één schema voor het hele abonnement) en klik op de knop **[!UICONTROL Change...]** .
1. Selecteer in het **[!UICONTROL Job schedule properties]** -venster de gewenste uitvoeringsinstellingen en klik op **[!UICONTROL OK]** en klik vervolgens op **[!UICONTROL Next]** .
1. Selecteer de onderhoudstaken die u wilt uitvoeren en klik op **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >We raden u aan ten minste de hieronder weergegeven onderhoudstaken uit te voeren. U kunt ook de statistische updatetaak selecteren, hoewel deze al wordt uitgevoerd door de workflow voor het opschonen van de database.

1. Selecteer in de vervolgkeuzelijst de database waarop u de **[!UICONTROL Database Check Integrity]** -taak wilt uitvoeren.
1. Selecteer de database en klik op **[!UICONTROL OK]** en klik vervolgens op **[!UICONTROL Next]** .
1. Configureer de maximale grootte die aan uw database is toegewezen en klik op **[!UICONTROL Next]** .

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

     Selecteer de opties die u wilt toepassen op de indexherbouwingstaak en klik vervolgens op **[!UICONTROL Next]** .

     >[!NOTE]
     >
     >Het rebuild-indexproces is beperkter in termen van processorgebruik en vergrendelt de databasebronnen. Selecteer de optie **[!UICONTROL Keep index online while reindexing]** als u wilt dat de index beschikbaar is tijdens het opnieuw samenstellen.

1. Selecteer de opties die u in het activiteitenrapport wilt weergeven en klik op **[!UICONTROL Next]** .
1. Controleer de lijst met taken die voor het onderhoudsplan zijn geconfigureerd en klik op **[!UICONTROL Finish]** .

   Er wordt een samenvatting van het onderhoudsplan en de status van de verschillende stappen weergegeven.

1. Klik op **[!UICONTROL Close]** als het onderhoudsplan is voltooid.
1. Dubbelklik in de Microsoft SQL Server-verkenner op de map **[!UICONTROL Management > Maintenance Plans]** .
1. Selecteer het Adobe Campaign-onderhoudsplan: de verschillende stappen worden beschreven in een workflow.

   Een object is gemaakt in de map **[!UICONTROL SQL Server Agent > Jobs]** . Met dit object kunt u het onderhoudsplan starten. In ons voorbeeld is er slechts één object omdat alle onderhoudstaken deel uitmaken van hetzelfde plan.

   >[!IMPORTANT]
   >
   >Dit object kan alleen worden uitgevoerd als de Microsoft SQL Server-agent is ingeschakeld.

**Vormend een afzonderlijk gegevensbestand voor het werken van lijsten**

>[!NOTE]
>
>Deze configuratie is optioneel.

**WdbcOptions_TempDbName** optie staat u toe om een afzonderlijk gegevensbestand voor het werken van lijsten op de Server van Microsoft te vormen SQL. Hierdoor worden back-ups en replicatie geoptimaliseerd.

Deze optie kan worden gebruikt als u de het werk lijsten (bijvoorbeeld, de lijsten die tijdens de uitvoering van een werkschema worden gecreeerd) op een andere gegevensbestand wilt worden gecreeerd.

Wanneer u de optie op &quot;tempdb.dbo.&quot;plaatst, worden de het werk lijsten gecreeerd op het gebrek tijdelijke gegevensbestand van de Server van Microsoft SQL. De gegevensbestandbeheerder moet schrijftoegang tot het tempdb- gegevensbestand toestaan.

Als de optie wordt geplaatst, wordt het gebruikt op alle gegevensbestanden van de Server van Microsoft SQL die in Adobe Campaign (belangrijkste gegevensbestand en externe rekeningen) worden gevormd. Let op: als twee externe accounts dezelfde server delen, kunnen er conflicten optreden (omdat tempdb uniek is). Op dezelfde manier, als twee instanties van de Campagne de zelfde server MSSQL gebruiken, kunnen er conflicten zijn als zij de zelfde tempdb gebruiken.
