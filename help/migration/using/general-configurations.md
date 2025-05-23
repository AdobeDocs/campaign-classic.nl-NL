---
product: campaign
title: Algemene configuraties
description: Algemene configuraties
feature: Upgrade
audience: migration
content-type: reference
topic-tags: configuration
hide: true
hidefromtoc: true
exl-id: 7aad0e49-8d9c-40c7-9d6a-42fee0ae5870
source-git-commit: 349c3dfd936527e50d7d3e03aa3408b395502da0
workflow-type: tm+mt
source-wordcount: '2558'
ht-degree: 0%

---

# Algemene configuraties{#general-configurations}

In dit gedeelte wordt de configuratie beschreven die in Adobe Campaign v7 moet worden uitgevoerd wanneer wordt gemigreerd van versie 5.11 of v6.02.

Daarnaast:

* Als u van v5.11 migreert, moet u ook de configuratie voltooien die in [ wordt gedetailleerd deze sectie ](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).
* Als u van v6.02 migreert, moet u ook de configuratie voltooien die in [ wordt gedetailleerd deze sectie ](../../migration/using/configuring-your-platform.md#specific-configurations-in-v6-02).

## Tijdzones {#time-zones}

### Modus voor meerdere tijdzones {#multi-time-zone-mode}

In v6.02 was de modus &quot;multi-time zone&quot; alleen beschikbaar voor PostgreSQL-databasemotoren. Er wordt nu aangeboden welk type database-engine wordt gebruikt. Wij adviseren sterk dat u uw basis in een &quot;multi timezone&quot;basis omzet.

Om TIMESTAMP MET wijze TIMEZONE te gebruiken, moet u ook **- userTimestamptz:1** optie aan de post-verbeteringsbevellijn toevoegen.

>[!IMPORTANT]
>
>Als de parameter **-usetimestamptz:1** met een incompatibele gegevensbestandmotor wordt gebruikt, zal uw gegevensbestand worden bedorven en u zult een steun van uw gegevensbestand moeten herstellen en het bevel hierboven opnieuw uitvoeren.

>[!NOTE]
>
>Het is mogelijk om timezone na migratie via de console (**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** knoop) te veranderen.
>
>Voor meer op tijdzonebeheer, verwijs naar [ deze sectie ](../../installation/using/time-zone-management.md).

### Oracle {#oracle}

Als u een **ORA 01805** fout tijdens postupgrade krijgt, betekent dit dat de dossiers van de Oracle timezone tussen de toepassingsserver en de gegevensbestandserver uit synchronisatie zijn. Voer de volgende stappen uit om ze opnieuw te synchroniseren:

1. Voer de volgende opdracht uit om het gebruikte tijdzonebestand te identificeren:

   ```
   select * from v$timezone_file
   ```

   De dossiers van de tijdzone worden gewoonlijk gevonden in **ORACLE_HOME/oracore/zoneinfo/** omslag.

1. Zorg ervoor dat de tijdzonebestanden op beide servers identiek zijn.

Voor meer informatie, bezoek: [ https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004 ](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

Een onjuiste uitlijning van de tijdzone tussen client en server kan ook enige vertraging veroorzaken. Daarom adviseren wij het gebruiken van de zelfde versie van de bibliotheek van het Oracle op de cliënt en serverkanten, moeten beide tijdstreken het zelfde zijn.

Controleren of beide zijden zich in dezelfde tijdzone bevinden:

1. Controleer de versie van het dossier van de tijdzone op de cliëntkant door het volgende bevel in werking te stellen:

   ```
   genezi -v
   ```

   genezi is een binair die in **$ORACLE_HOME/bin** bewaarplaats wordt gevonden.

1. Controleer de versie van het dossier van de tijdzone op de server door het volgende bevel in werking te stellen:

   ```
   select * from v$timezone_file
   ```

1. Om het dossier van de tijdzone op de cliëntkant te veranderen, gebruik **ORA_TZFILE** milieuvariabele.

## Beveiliging {#security}

### Beveiligingszones {#security-zones}

>[!IMPORTANT]
>
>Om veiligheidsredenen, is het platform van Adobe Campaign niet meer toegankelijk door gebrek: u moet de veiligheidsstreken vormen, en daarom exploitant IP adressen verzamelen.

Adobe Campaign v7 impliceert het concept **veiligheidsstreken**. Elke gebruiker moet met een streek worden geassocieerd om aan login aan een instantie en het IP van de gebruiker adres moet in de adressen of adreswaaiers worden omvat die in de veiligheidsstreek worden bepaald. U kunt de beveiligingszones configureren in het configuratiebestand van de Adobe Campaign-server. De veiligheidsstreek waaraan een gebruiker wordt geassocieerd moet in de console (**[!UICONTROL Administration > Access management > Operators]**) worden bepaald.

**vóór de migratie**, vraag uw netwerkbeheerder om u te helpen de veiligheidsstreken bepalen die na de migratie moeten worden geactiveerd.

**na postupgrade** (vóór het servernieuwe begin), moet u de veiligheidsstreken vormen.

De configuratie van de veiligheidsstreek wordt gevonden in [ deze sectie ](../../installation/using/security-zones.md).

### Gebruikerswachtwoorden {#user-passwords}

In v7, **interne** en **admin** de exploitantverbinding moet door een wachtwoord worden beveiligd. Wij adviseren sterk toewijzend wachtwoorden aan deze rekeningen en alle exploitantrekeningen, **vóór migratie**. Als u geen wachtwoord voor **intern** hebt gespecificeerd, zult u niet kunnen verbinden. Om een wachtwoord aan **intern** toe te wijzen, ga het volgende bevel in:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>Het **interne** wachtwoord moet voor alle volgende servers identiek zijn. Voor meer informatie, verwijs naar [ deze sectie ](../../installation/using/configuring-campaign-server.md#internal-identifier) en [ deze sectie ](../../platform/using/access-management.md).

### Nieuwe functies in v7 {#new-features-in-v7}

* Gebruikers zonder machtigingen kunnen niet langer verbinding maken met Adobe Campaign. Hun toestemmingen moeten manueel worden toegevoegd, bijvoorbeeld, door een toestemming te creëren genoemd **verbind**.

  De gebruikers die door deze wijziging worden beïnvloed worden geïdentificeerd en worden vermeld tijdens postupgrade.

* Tekstspatiëring werkt niet meer als het wachtwoord leeg is. Als dit het geval is, zal een foutenmelding u op de hoogte brengen en u vragen om het aan te passen.
* De wachtwoorden van de gebruiker worden niet meer opgeslagen in **xtk:sessionInfo** schema.
* Beheermachtigingen zijn nu nodig om de functies **`xtk:builder:EvaluateJavaScript`** en **`xtk:builder:EvaluateJavaScriptTemplate`** te kunnen gebruiken.

Bepaalde out-of-box schema&#39;s zijn gewijzigd en zijn nu door gebrek slechts toegankelijk met schrijftoegang voor exploitanten met **admin** toestemming:

* ncm:publiceren
* nl:controleren
* nms:kalender
* xtk:builder
* xtk:verbindingen
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusie
* xtk:afbeelding
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:tekenreeksen
* xtk:xslt

### Sessiontoken, parameter {#sessiontoken-parameter}

In v5, werkte de **zittingsontoken** parameter aan beide cliëntkant (lijst van overzichtstype schermen, verbindingsredacteur, enz.) en server (webtoepassingen, rapporten, jsp, jssp, enz.). In versie 7 werkt deze alleen aan de serverzijde. Als u wilt terugkeren naar de volledige functionaliteit zoals in versie 5, moet u de koppelingen wijzigen met deze parameter en via de verbindingspagina doorgeven:

Voorbeeld van koppeling:

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

Nieuwe koppeling met de verbindingspagina:

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!IMPORTANT]
>
>Als u een exploitant gebruikt met een vertrouwd op IP masker wordt verbonden, controleer dat het de minimumrechten heeft en dat het in een veiligheidsstreek op **sessionTokenOnly** wijze is.

### SQL-functies {#sql-functions}

Onbekende SQL-functieaanroepen worden niet meer automatisch naar de server verzonden. Momenteel, moeten alle SQL functies aan **xtk worden toegevoegd:funcList** schema (voor meer op dit, verwijs naar [ deze sectie ](../../configuration/using/adding-additional-sql-functions.md)). Tijdens het migreren wordt tijdens de postupgrade een optie toegevoegd waarmee u compatibiliteit met oude niet-gedeclareerde SQL-functies kunt behouden. Als u deze functies zou willen blijven gebruiken, controleer dat **XtkPassUnknownSQLFunctionsToRDBMS** optie inderdaad op het **[!UICONTROL Administration > Platform > Options]** knooppuntniveau wordt bepaald.

>[!IMPORTANT]
>
>We raden u ten zeerste aan deze optie niet te gebruiken vanwege de beveiligingsrisico&#39;s die erin worden geïntroduceerd.

### JSSP {#jssp}

Als u toegang tot bepaalde pagina&#39;s via het protocol van HTTP (niet HTTPS), in uw Web zou willen toestaan apps bijvoorbeeld, ongeacht de configuratie die in de veiligheidsstreken wordt uitgevoerd, moet u **httpAllowed= &quot; waar&quot;** parameter in de overeenkomstige relaisregel specificeren.

Als u anonieme JSSPs gebruikt, moet u **httpAllowed= &quot;waar&quot;** parameter in een relaisregel voor uw JSSP (**[!UICONTROL serverConf.xml]** dossier) toevoegen:

Bijvoorbeeld:

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## Syntaxis {#syntax}

### JavaScript {#javascript}

Adobe Campaign v7 integreert een recentere tolk van JavaScript. Deze update kan echter tot een storing van bepaalde scripts leiden. Aangezien de vorige motor machtiger was, zou bepaalde syntaxis werken wat niet langer het geval is met de nieuwe versie van de motor.

De syntaxis van **[!UICONTROL myObject.@attribute]** is nu alleen geldig voor XML-objecten. Deze syntaxis kan worden gebruikt voor het aanpassen van leveringen en inhoudsbeheer. Als u dit type syntaxis gebruikt voor een niet-XML-object, werken de verpersoonlijkingsfuncties niet meer.

Voor alle andere objecten types, is de syntaxis nu **[!UICONTROL myObject`[`&quot;attribuut&quot;`]`]**. Bijvoorbeeld, moet een niet-voorwerp van XML dat de volgende syntaxis gebruikte: **[!UICONTROL employee.@sn]**, nu de volgende syntaxis gebruiken: **[!UICONTROL employee`[`&quot;sn&quot;`]`]**.

* Voormalige syntaxis:

  ```
  employee.@sn
  ```

* Nieuwe syntaxis:

  ```
  employee["sn"]
  ```

Als u een waarde in een XML-object wilt wijzigen, moet u nu beginnen met het bijwerken van de waarde voordat u het XML-knooppunt toevoegt:

* Oude JavaScript-code:

  ```
  var cellStyle = node.style.copy();
  this.styles.appendChild(cellStyle);
  cellStyle.@width = column.@width;
  ```

* Nieuwe JavaScript-code:

  ```
  var cellStyle = node.style.copy();
  cellStyle.@width = column.@width;
  this.styles.appendChild(cellStyle);
  ```

U kunt een XML-kenmerk niet meer gebruiken als een tabelsleutel.

* Voormalige syntaxis:

  ```
  if(serverForm.activities[ctx.activityHistory.activity[0].@name].type !="end")
  ```

* Nieuwe syntaxis:

  ```
  if(serverForm.activities[String(ctx.activityHistory.activity[0].@name)].type !="end"
  ```

### SQLData {#sqldata}

Om de instantieveiligheid te versterken, is een nieuwe syntaxis geïntroduceerd in Adobe Campaign v7 om de syntaxis te vervangen die op SQLData wordt gebaseerd. Als u deze code-elementen met deze syntaxis gebruikt, moet u deze wijzigen. De belangrijkste elementen zijn:

* Filteren op subquery: de nieuwe syntaxis is gebaseerd op het element `<subQuery>` om een subquery te definiëren
* Samengevoegde gegevens: de nieuwe syntaxis is &quot;statistische functie(verzameling)&quot;
* Filteren op samenvoeging: de nieuwe syntaxis is `[schemaName:alias:xPath]`

Het schema queryDef (xtk:queryDef) is gewijzigd:

* er is een nieuw `<subQuery>` -element beschikbaar om de SELECT in SQLData te vervangen
* Er zijn twee nieuwe waarden &quot;IN&quot; en &quot;NOT IN&quot; geïntroduceerd voor het @setOperator-kenmerk
* een nieuw `<where>` -element, dat een onderliggend element is van het `<node>` -element: hiermee kunt u subselecties maken in SELECT

Wanneer een &quot;@expr&quot;attribuut wordt gebruikt, kan SQLData aanwezig zijn. U kunt de volgende termen zoeken: &quot;SQLData&quot;, &quot;aliasSqlTable&quot;, &quot;sql&quot;.

Adobe Campaign v7-instanties zijn standaard beveiligd. De veiligheid komt in termen van definities van veiligheidsstreken in het **[!UICONTROL serverConf.xml]** dossier: het **allowSQLInjection** attribuut beheert de SQL syntaxisveiligheid.

Als een SQLData-fout optreedt tijdens de uitvoering na de upgrade, moet u dit kenmerk wijzigen om het gebruik van op SQLData gebaseerde syntaxis tijdelijk toe te staan, zodat u de code kunt herschrijven. Om dit te doen, moet de volgende optie in het **serverConf.xml** dossier worden veranderd:

```
allowSQLInjection="true"
```

Daarom lanceer de postupgrade met het volgende bevel:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

U moet de veiligheidsstreken vormen (verwijs naar [ Veiligheid ](#security)), dan de veiligheid opnieuw activeren door de optie te veranderen:

```
allowSQLInjection="false"
```

Hieronder vindt u vergelijkende voorbeelden tussen de oude en de nieuwe syntaxis.

**Filtrerend door sub-query&#39;s**

* Voormalige syntaxis:

  ```
  <condition expr="@id NOT IN ([SQLDATA[SELECT iOperatorId FROM XtkOperatorGroup WHERE iGroupId = $(../@owner-id)]])" enabledIf="$(/ignored/@ownerType)=1"/>
  ```

* Nieuwe syntaxis:

  ```
  <condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
    <subQuery schema="xtk:operatorGroup">
       <select>
         <node expr="[@operator-id]" />
       </select>
       <where>
         <condition expr="[@group-id]=$long(../@owner-id)"/>
       </where>
     </subQuery>
  </condition>
  ```

* Voormalige syntaxis:

  ```
  <queryFilter name="dupEmail" label="Emails duplicated in the folder" schema="nms:recipient">
      <where>
        <condition sql="sEmail in (select sEmail from nmsRecipient where iFolderId=$(folderId) group by sEmail having count(sEmail)>1)" internalId="1"/>
      </where>
      <folder _operation="none" name="nmsSegment"/>
    </queryFilter>
  ```

* Nieuwe syntaxis:

  ```
  <queryFilter name="dupEmail" label=" Emails duplicated in the folder " schema="nms:recipient">
      <where>
        <condition expr="@email" setOperator="IN" internalId="1">
          <subQuery schema="nms:recipient">
            <select><node expr="@email"/></select>
            <where><condition expr="[@folder-id]=$(folderId)"/></where>
            <groupBy><node expr="@email"/></groupBy>
            <having><condition expr="count(@email)>1"/></having>
          </subQuery>
        </condition>
      </where>
      <folder _operation="none" name="nmsSegment"/>
    </queryFilter>
  ```

**het aggregaat**

Samengevoegde functie (verzameling)

* Voormalige syntaxis:

  ```
  <node sql="(select count(*) from NmsNewsgroup WHERE O0.iOperationId=iOperationId)" alias="@nbMessages"/>
  ```

* Nieuwe syntaxis:

  ```
  <node expr="count([newsgroup/@id])" alias="../@nbMessages"/>
  ```

  >[!NOTE]
  >
  >De verbindingen worden automatisch uitgevoerd voor de gezamenlijke functies. Het is niet meer noodzakelijk om de voorwaarde WHERE O0.iOperationId=iOperationId te specificeren.
  >
  >Het is niet meer mogelijk om de functie &quot;count(&#42;)&quot; te gebruiken. Je moet &quot;countall()&quot; gebruiken.

* Voormalige syntaxis:

  ```
  <node sql="(select Sum(iToDeliver) from NmsDelivery WHERE O0.iOperationId=iOperationId AND iSandboxMode=0 AND iState>=45)" alias="@nbMessages"/>
  ```

* Nieuwe syntaxis:

  ```
  <node expr="Sum([delivery-linkedDelivery/properties/@toDeliver])" alias= "../@sumToDeliver">
                    <where><condition expr="[validation/@sandboxMode]=0 AND @state>=45" /></where></node>
  ```

**Filters door zich** aansluit

`[schemaName:alias:xPath]`

De alias is optioneel

* Voormalige syntaxis:

  ```
  <condition expr={"[" + joinPart.destination.nodePath + "] = [SQLDATA[W." + joinPart.source.SQLName + "]]"}
                                           aliasSqlTable={nodeSchemaRoot.SQLTable + " W"}/>
  ```

* Nieuwe syntaxis:

  ```
  <condition expr={"[" + joinPart.destination.nodePath + "] = [" + nodeSchema.id + ":" + joinPart.source.nodePath + "]]"}/>
  ```

**Uiteinden en trucs**

In een element `<subQuery>` verwijst u naar een veld &quot;veld&quot; van het hoofdveld `<queryDef>`   -element, gebruikt u de volgende syntaxis: `[../@field]`

Voorbeeld:

```
<queryDef operation="select" schema="xtk:jobLog" startPath="/" xtkschema="xtk:queryDef">
  <select>
    <node expr="[job/@pid]" alias="@pid"/>
    <node expr="@id" ordered="true"/>
    <node expr="@logType"/>
  </select>
  <where>
    <condition expr="[@job-id]=99"/>
    <condition expr="@logType" setOperator="IN">
      <subQuery schema="xtk:jobLog">
        <select><node expr="@logType"/></select>
        <where><condition expr="[@job-id]=[../job/@id]"/></where>
        <groupBy><node expr="@logType"/></groupBy>
        <having><condition expr="count(@logType)>1"/></having>
      </subQuery>
    </condition>
  </where>
</queryDef>
```

## Conflicten {#conflicts}

De migratie wordt uitgevoerd via een postupgrade en conflicten kunnen optreden in rapporten, formulieren of webtoepassingen. Deze conflicten kunnen vanaf de console worden opgelost.

Na de middelsynchronisatie, laat het **postupgrade** bevel u ontdekken als de synchronisatie fouten of waarschuwingen produceert.

### Het synchronisatieresultaat weergeven {#view-the-synchronization-result}

Het synchronisatieresultaat kan op twee manieren worden weergegeven:

* In de bevel-lijn interface, worden de fouten materialized door een drievoudig chevron **>>>** en de synchronisatie wordt automatisch tegengehouden. De waarschuwingen worden materialized door een dubbel chevron **>>** en moeten worden opgelost zodra de synchronisatie volledig is. Aan het eind van postupgrade, wordt een samenvatting getoond in de bevelherinnering. Bijvoorbeeld:

  ```
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     info    log     =========Summary of the update==========
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Als de waarschuwing een conflict van middelen betreft, wordt de aandacht van de exploitant vereist om het op te lossen.

* Het **postupgrade_ `<server version number>`_time van postupgrade `>` .log** dossier bevat het synchronisatieresultaat. Het is beschikbaar door gebrek in de volgende folder: **installatiemap/var/`<instance>` postupgrade**. De fouten en de waarschuwingen worden vermeld door de **fout** en **waarschuwings** attributen.

### Een conflict oplossen {#resolve-a-conflict}

Conflicten oplossen moet alleen worden uitgevoerd door gevorderde operatoren en gebruikers aan wie beheerdersrechten zijn verleend.

U lost een conflict op door het volgende proces toe te passen:

1. Plaats de cursor in de Adobe Campaign-boomstructuur boven **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Selecteer in de lijst het conflict dat u wilt oplossen.

Er zijn drie manieren om een conflict op te lossen:

* **[!UICONTROL Declared as resolved]**: vereist vooraf ingrijpen door de operator.
* **[!UICONTROL Accept the new version]**: aanbevolen als de bronnen die bij Adobe Campaign worden geleverd, niet door de gebruiker zijn gewijzigd.
* **[!UICONTROL Keep the current version]** : betekent dat de update wordt afgewezen.

  >[!IMPORTANT]
  >
  >Als u deze resolutiemodus selecteert, loopt u het risico dat de patches in de nieuwe versie verloren gaan. Daarom wordt ten zeerste aanbevolen deze optie niet te gebruiken of alleen voor professionele marktdeelnemers te reserveren.

Ga als volgt te werk als u het conflict handmatig wilt oplossen:

1. Zoek in de onderste sectie van het venster naar de **`_conflict_ string`** om de entiteiten met conflicten te zoeken. De entiteit die met de nieuwe versie wordt geïnstalleerd bevat het **nieuwe** argument, de entiteit die de vorige versie aanpast bevat het **focus** argument.

   ![](assets/s_ncs_production_conflict002.png)

1. Verwijder de versie die u niet wilt behouden. Verwijder **`_conflict_argument_ string`** van de entiteit die u bewaart.

   ![](assets/s_ncs_production_conflict003.png)

1. Ga naar het conflict dat u had opgelost. Klik op het pictogram **[!UICONTROL Actions]** en selecteer **[!UICONTROL Declare as resolved]** .
1. Sla uw wijzigingen op: het conflict is nu opgelost.

<!--
## Tomcat {#tomcat}

The integrated Tomcat server in Adobe Campaign v7 has changed version. Its installation folder (tomcat-6) has therefore also changed (tomcat 7). After the postupgrade, make sure to check that the paths do link to the updated folder (in the **[!UICONTROL serverConf.xml]** file):

```
$(XTK_INSTALL_DIR)/tomcat-X/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-X/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/el-api.jar
```
-->

## Interactie {#interaction}

### Vereisten {#prerequisites}

**vóór postupgrade**, moet u alle schemaverwijzingen van 6.02 schrappen die niet meer in v7 zullen bestaan.

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### Inhoud aanbieden {#offer-content}

In v7 is de inhoud van het aanbod verplaatst. In v6.02 was de inhoud in elk vertegenwoordigingsschema (**nms:emailOfferView**). In v7 bevindt de inhoud zich nu in het aanbiedingsschema. Na de postupgrade is de inhoud daarom niet zichtbaar in de interface. Na postupgrade moet u de aanbiedingsinhoud opnieuw maken of een script ontwikkelen dat de inhoud automatisch van het presentatieschema naar het aanbiedingsschema verplaatst.

>[!IMPORTANT]
>
>Als sommige leveringen die geconfigureerde aanbiedingen gebruiken na de migratie moeten worden verzonden, moet u al deze leveringen in v7 verwijderen en opnieuw maken. Als u dat niet kunt, wordt een &quot;verenigbaarheidswijze&quot;aangeboden. Deze modus wordt niet aanbevolen omdat u niet van alle nieuwe functies in Interaction v7 kunt profiteren. Dit is een overgangsmodus waarmee u lopende campagnes kunt voltooien vóór de daadwerkelijke 6.1-migratie. Neem contact met ons op voor meer informatie over deze modus.

Een voorbeeld van een bewegingsmanuscript (**interactionTo610_full_XX.js**) is beschikbaar in de **omslag van de Migratie** binnen de omslag van Adobe Campaign v7. In dit bestand ziet u een voorbeeld van een script voor een client dat gebruikmaakt van één e-mailrepresentatie per aanbieding (de velden **[!UICONTROL htmlSource]** en **[!UICONTROL textSource]** ). De inhoud die in de **NmsEmailOfferView** lijst was is verplaatst naar de aanbiedingslijst.

>[!NOTE]
>
>Met dit script kunt u niet profiteren van de opties voor inhoudsbeheer en renderfuncties. Om van deze functies te profiteren, moet u de catalogusaanbiedingen, in het bijzonder de aanbiedingsinhoud en configuratieruimten heroverwegen.

```
loadLibrary("/nl/core/shared/nl.js");

NL.require("/nl/core/shared/xtk.js");

// 1. Restore old emailOfferView schema
logInfo("Restoring old emailOfferView schema");
var oldOfferViewSchemas = <entities schema="xtk:srcSchema"/>;

oldOfferViewSchemas.appendChild(
  <srcSchema img="nms:offerView.png"
             label="Email offer representations"
             labelSingular="Email offer representation"
             name="emailOfferView" namespace="nlmig"
             genAccessors="false" implements="xtk:persist">
    <element name="emailOfferView" template="nms:offerView" sqltable="NmsEmailOfferView">
      <element name="offer" revLabel="Email representation" revIntegrity="owncopy"/>
      <element   name="htmlSource"      type="html" label="HTML content"  xml="true"/>
      <element   name="textSource"      type="CDATA" label="Text content" xml="true"/>
      <element   name="htmlSource_jst"  type="CDATA" label="HTML script"  desc="HTML content calculation script."  xml="true" advanced="true"/>
      <element   name="textSource_jst"  type="CDATA" label="Text script" desc="Text content calculation script." xml="true" advanced="true"/>
    </element>
  </srcSchema>);

var oldOfferViewsPkg = <builder><package buildNumber="*">{oldOfferViewSchemas}</package></builder>;
xtk.builder.InstallPackage(oldOfferViewsPkg);

// 2. Migrate data from old emailOfferView table to nms:offer
logInfo("Moving data from old EmailOfferView table to NmsOffer");
var OFFER_STATUS_VALIDATED = 3;

var queryDef = xtk.queryDef.create(
  <queryDef operation="select" schema="nlmig:emailOfferView">
    <select>
      <node expr="[@offer-id]"/>
      <node expr="[@space-id]"/>
      <node expr="htmlSource_jst"/>
      <node expr="textSource_jst"/>
    </select>
  </queryDef>);
var res = queryDef.ExecuteQuery();

var processedOffers = {};
for each( var emailOfferView in res.emailOfferView )
{
  if( processedOffers[String(emailOfferView.@["offer-id"])] != undefined )
  {
    logWarning("Found 2 or more eff fffffmail representations for offer " + String(emailOfferView.@["offer-id"]) + ". Only keep the first one here.");
    continue;
  }
  xtk.session.Write(
    <offer id={emailOfferView.@["offer-id"]} status={OFFER_STATUS_VALIDATED} xtkschema="nms:offer">
      <view>
        {emailOfferView.mdSource_jst}
        {emailOfferView.textSource_jst}
      </view>
    </offer>
  );
  processedOffers[String(emailOfferView.@["offer-id"])] = 1;
}

// 3. Get rid of emailOfferView schema now that data has been moved.
logInfo("Deleting EmailOfferView schema");
xtk.session.Write(<srcSchema xtkschema="xtk:srcSchema" name="emailOfferView" namespace="nlmig" _operation="delete"/>);

logInfo("Done");
```

### Tests en configuratie {#tests-and-configuration}

Hier volgt de procedure nadat u de inhoud van het aanbod hebt verplaatst als u slechts één omgeving hebt. Laten we in dit geval &quot;ENV&quot; als voorbeeld nemen.

1. Werk in alle &quot;ENV&quot;-omgevingen de lijst met gebruikte velden bij. Voor een aanbiedingsruimte die alleen de **[!UICONTROL htmlSource]** gebruikt, moet u bijvoorbeeld de lus **[!UICONTROL view/htmlSource]** toevoegen.

   ![](assets/migration_interaction_2.png)

1. Selecteer **[!UICONTROL Live]** in het veld **[!UICONTROL Type of Environment]** op de tab **[!UICONTROL General]** .

   ![](assets/migration_interaction_3.png)

1. Maak een ontwerpomgeving (bijvoorbeeld &quot;ENV_DESIGN&quot;) en sluit deze aan op de online ENV-omgeving.

   ![](assets/migration_interaction_4.png)

1. Implementeer alle &quot;ENV&quot;-omgeving met spaties (klik met de rechtermuisknop > **[!UICONTROL Actions > Deploy]** ) en selecteer de omgeving &quot;ENV_DESIGN&quot;.

   ![](assets/migration_interaction_5.png)

1. Doe hetzelfde voor alle &quot;ENV&quot;-omgevingsfuncties.
1. Activeer alle omgevingsfuncties &quot;ENV_DESIGN&quot; op de relevante kanalen.
1. Test of een aanbieding live gaat. Als u geen problemen ondervindt, voert u lopende taken uit op de meest recente workflowtaak **[!UICONTROL Offer notification]** (offerMgt) om alle aanbiedingen live te laten gaan.

   ![](assets/migration_interaction_6.png)

1. Voer uitgebreide tests uit.

   >[!NOTE]
   >
   >De namen van categorieën en aanbiedingen online worden gewijzigd nadat u live bent gegaan. Werk op het binnenkomende kanaal alle verwijzingen naar aanbiedingen en categorieën bij.

## Rapporten {#reports}

### Standaardrapporten {#standard-reports}

Alle standaardrapporten gebruiken momenteel de renderingengine v6.x. Als u JavaScript in deze rapporten had toegevoegd, werken bepaalde elementen mogelijk niet meer. De oude versie van JavaScript is namelijk niet compatibel met de v6.x-renderingengine. U moet daarom de JavaScript-code controleren en deze later aanpassen. U moet elk rapport testen, met name de exportfunctie.

### Persoonlijke rapporten {#personalized-reports}

<!--If you want to have the blue banner from v7 (allowing you access to the tabs), you must republish reports. If you encounter problems, you can force the v6.0 rendering engine. To do this, go to **[!UICONTROL Properties]** within the report, click **[!UICONTROL Rendering]** and choose the **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** rendering engine.

![](assets/migration_reports_1.png)
-->
Als u van de nieuwe rapportfuncties wilt profiteren, moet u rapporten opnieuw publiceren. Controleer in dit geval al uw scripts en wijzig deze zo nodig. Wat de uitvoer van PDF betreft, als u specifiek manuscript voor Open Office had toegevoegd, zal dit niet meer met de nieuwe de uitvoermotor van de PDF (PhantomJS) werken.

## Webtoepassingen {#web-applications}

Er zijn twee families voor webtoepassingen:

* geïdentificeerde webtoepassingen (samen gezien, goedkeuringsformulieren, interne extranetontwikkelingen);
* anonieme webtoepassingen (web- of vragenformulieren).

### Geïdentificeerde webtoepassingen {#identified-web-applications}

Enkel zoals voor rapporten ([ leert meer ](#reports)), als u JavaScript had toegevoegd, moet u controleren en aanpassen indien nodig. Als u wilt profiteren van de blauwe banner v7 (met de blauwe tabbladen), moet u de webtoepassing opnieuw publiceren.

Verbindingsmethoden voor webtoepassingen zijn gewijzigd in v7. Als u om het even welke verbindingsproblemen in uw geïdentificeerde Webtoepassingen ontmoet, moet u **allowUserPassword** en **sessionTokenOnly** opties in het **serverConf.xml** dossier tijdelijk activeren. Na de postupgrade wijzigt u de volgende waarden voor opties:

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

Daarom lanceer de postupgrade met het volgende bevel:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Test uw webtoepassingen in de v6.x-renderingengine voordat u ze publiceert. Vervolgens deactiveert u deze twee opties.

```
allowUserPassword="false"
```

```
sessionTokenOnly="false"
```

### Anonieme webtoepassingen {#anonymous-web-applications}

Als u problemen ondervindt, publiceert u de webtoepassing opnieuw.
