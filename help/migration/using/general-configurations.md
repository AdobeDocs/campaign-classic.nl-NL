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
source-git-commit: afbec7b3df810c8c1818a4fb93c5f7e30f7a753b
workflow-type: tm+mt
source-wordcount: '2558'
ht-degree: 0%

---

# Algemene configuraties{#general-configurations}



In dit gedeelte wordt de configuratie beschreven die in Adobe Campaign v7 moet worden uitgevoerd wanneer wordt gemigreerd van versie 5.11 of v6.02.

Daarnaast:

* Als u migreert vanaf v5.11, moet u ook de configuratie voltooien die in [deze sectie](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).
* Als u migreert vanaf v6.02, moet u ook de configuratie voltooien die in [deze sectie](../../migration/using/configuring-your-platform.md#specific-configurations-in-v6-02).

## Tijdzones {#time-zones}

### Modus voor meerdere tijdzones {#multi-time-zone-mode}

In v6.02 was de modus &quot;multi-time zone&quot; alleen beschikbaar voor PostgreSQL-databasemotoren. Er wordt nu aangeboden welk type database-engine wordt gebruikt. Wij adviseren sterk dat u uw basis in een &quot;multi timezone&quot;basis omzet.

Als u de TIMESTAMP met de modus TIMEZONE wilt gebruiken, moet u ook de opdracht **-userTimestamptz:1** optie aan de postupgrade bevellijn.

>[!IMPORTANT]
>
>Als de **-usetimestamptz:1** wordt gebruikt met een incompatibele database-engine, is uw database beschadigd en moet u een back-up van uw database herstellen en de bovenstaande opdracht opnieuw uitvoeren.

>[!NOTE]
>
>Het is mogelijk de tijdzone na migratie via de console te wijzigen (**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** knooppunt).
>
>Raadpleeg voor meer informatie over tijdzonebeheer [deze sectie](../../installation/using/time-zone-management.md).

### Oracle {#oracle}

Als u een **ORA 01805** fout tijdens postupgrade, betekent dit dat de tijdzonebestanden van het Oracle tussen de toepassingsserver en de databaseserver niet gesynchroniseerd zijn. Voer de volgende stappen uit om ze opnieuw te synchroniseren:

1. Voer de volgende opdracht uit om het gebruikte tijdzonebestand te identificeren:

   ```
   select * from v$timezone_file
   ```

   Tijdzonebestanden worden meestal gevonden in het dialoogvenster **ORACLE_HOME/oracore/zoneinfo/** map.

1. Zorg ervoor dat de tijdzonebestanden op beide servers identiek zijn.

Ga voor meer informatie naar: [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

Een onjuiste uitlijning van de tijdzone tussen client en server kan ook enige vertraging veroorzaken. Daarom adviseren wij het gebruiken van de zelfde versie van de bibliotheek van het Oracle op de cliënt en serverkanten, moeten beide tijdstreken het zelfde zijn.

Controleren of beide zijden zich in dezelfde tijdzone bevinden:

1. Controleer de versie van het dossier van de tijdzone op de cliëntkant door het volgende bevel in werking te stellen:

   ```
   genezi -v
   ```

   genezi is binair aangetroffen in **$ORACLE_HOME/bin** opslagplaats.

1. Controleer de versie van het dossier van de tijdzone op de server door het volgende bevel in werking te stellen:

   ```
   select * from v$timezone_file
   ```

1. Als u het bestand met de tijdzone aan de clientzijde wilt wijzigen, gebruikt u de optie **ORA_TZFILE** omgevingsvariabele.

## Beveiliging {#security}

### Beveiligingszones {#security-zones}

>[!IMPORTANT]
>
>Om veiligheidsredenen, is het platform van Adobe Campaign niet meer toegankelijk door gebrek: u moet de veiligheidsstreken vormen, en daarom exploitant IP adressen verzamelen.

In Adobe Campaign v7 wordt het concept van **beveiligingszones**. Elke gebruiker moet met een streek worden geassocieerd om aan login aan een instantie en het IP van de gebruiker adres moet in de adressen of adreswaaiers worden omvat die in de veiligheidsstreek worden bepaald. U kunt de beveiligingszones configureren in het configuratiebestand van de Adobe Campaign-server. De veiligheidsstreek waaraan een gebruiker wordt geassocieerd moet in de console worden bepaald (**[!UICONTROL Administration > Access management > Operators]**).

**Voor de migratie**, vraag uw netwerkbeheerder om u te helpen de veiligheidsstreken bepalen die na de migratie moeten worden geactiveerd.

**Na de postupgrade** (voordat de server opnieuw wordt opgestart), moet u de beveiligingszones configureren.

Configuratie van beveiligingszone is gevonden in [deze sectie](../../installation/using/security-zones.md).

### Gebruikerswachtwoorden {#user-passwords}

In v7: **internal** en **admin** De verbinding van de exploitant moet door een wachtwoord worden beveiligd. Wij adviseren sterk wachtwoorden aan deze rekeningen en alle exploitantrekeningen toe te wijzen, **voor migratie**. Als u geen wachtwoord hebt opgegeven voor **internal**, kunt u geen verbinding maken. Een wachtwoord toewijzen aan **internal** voert u de volgende opdracht in:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>De **internal** wachtwoord moet identiek zijn voor alle volgende servers. Raadpleeg voor meer informatie [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) en [deze sectie](../../platform/using/access-management.md).

### Nieuwe functies in v7 {#new-features-in-v7}

* Gebruikers zonder machtigingen kunnen niet langer verbinding maken met Adobe Campaign. Hun toestemmingen moeten manueel worden toegevoegd, bijvoorbeeld door een toestemming te creëren genoemd **verbinden**.

  De gebruikers die door deze wijziging worden beïnvloed worden geïdentificeerd en worden vermeld tijdens postupgrade.

* Tekstspatiëring werkt niet meer als het wachtwoord leeg is. Als dit het geval is, zal een foutenmelding u op de hoogte brengen en u vragen om het aan te passen.
* Gebruikerswachtwoorden worden niet meer opgeslagen in het dialoogvenster **xtk:sessionInfo** schema.
* Beheerdersmachtigingen zijn nu nodig om de **`xtk:builder:EvaluateJavaScript`** en **`xtk:builder:EvaluateJavaScriptTemplate`** functies.

Bepaalde out-of-the-box schema&#39;s zijn gewijzigd en zijn nu standaard alleen toegankelijk met schrijftoegang voor operatoren met de **admin** machtiging:

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

In v5 **sessiontoken** parameter werkte aan beide cliëntkant (lijst van overzichtstypesschermen, verbindingsredacteur, enz.) en server (webtoepassingen, rapporten, jsp, jssp, enz.). In versie 7 werkt deze alleen aan de serverzijde. Als u wilt terugkeren naar de volledige functionaliteit zoals in versie 5, moet u de koppelingen wijzigen met deze parameter en via de verbindingspagina doorgeven:

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
>Als u een exploitant gebruikt verbonden aan een vertrouwd op IP masker, controleer dat het de minimumrechten heeft en dat het in een veiligheidsstreek binnen is **sessionTokenOnly** -modus.

### SQL-functies {#sql-functions}

Onbekende SQL-functieaanroepen worden niet meer automatisch naar de server verzonden. Momenteel moeten alle SQL-functies worden toegevoegd aan de **xtk:funcList** schema (voor meer informatie hierover raadpleegt u [deze sectie](../../configuration/using/adding-additional-sql-functions.md)). Tijdens het migreren wordt tijdens de postupgrade een optie toegevoegd waarmee u compatibiliteit met oude niet-gedeclareerde SQL-functies kunt behouden. Als u deze functies wilt blijven gebruiken, controleert u of de functie **XtkPassUnknownSQLFunctionsToRDBMS** de optie is inderdaad gedefinieerd in de **[!UICONTROL Administration > Platform > Options]** knooppuntniveau.

>[!IMPORTANT]
>
>We raden u ten zeerste aan deze optie niet te gebruiken vanwege de beveiligingsrisico&#39;s die erin worden geïntroduceerd.

### JSSP {#jssp}

Als u toegang tot bepaalde pagina&#39;s via het HTTP-protocol (niet HTTPS) wilt toestaan, bijvoorbeeld in uw Web-apps, ongeacht de configuratie die in de beveiligingszones wordt uitgevoerd, moet u de **httpAllowed=&quot;true&quot;** parameter in de overeenkomstige relaisregel.

Als u anonieme JSSPs gebruikt, moet u toevoegen **httpAllowed=&quot;true&quot;** parameter in een relaisregel voor uw JSSP (**[!UICONTROL serverConf.xml]** bestand):

Bijvoorbeeld:

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## Syntaxis {#syntax}

### JavaScript {#javascript}

Adobe Campaign v7 integreert een recentere tolk JavaScript. Deze update kan echter tot een storing van bepaalde scripts leiden. Aangezien de vorige motor machtiger was, zou bepaalde syntaxis werken wat niet langer het geval is met de nieuwe versie van de motor.

De **[!UICONTROL myObject.@attribute]** is nu alleen geldig voor XML-objecten. Deze syntaxis kan worden gebruikt voor het aanpassen van leveringen en inhoudsbeheer. Als u dit type syntaxis gebruikt voor een niet-XML-object, werken de verpersoonlijkingsfuncties niet meer.

Voor alle andere objecttypen is de syntaxis nu **[!UICONTROL myObject`[`&quot;attribute&quot;`]`]**. Bijvoorbeeld een niet-XML-object dat de volgende syntaxis heeft gebruikt: **[!UICONTROL employee.@sn]** moet nu de volgende syntaxis gebruiken: **[!UICONTROL employee`[`&quot;sn&quot;`]`]**.

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

* Filteren op subquery: de nieuwe syntaxis is gebaseerd op de `<subQuery>`  element om een subquery te definiëren
* Samengevoegde gegevens: de nieuwe syntaxis is &quot;statistische functie(verzameling)&quot;
* Filteren op samenvoeging: de nieuwe syntaxis is `[schemaName:alias:xPath]`

Het schema queryDef (xtk:queryDef) is gewijzigd:

* een nieuwe `<subQuery>`  -element is beschikbaar om de SELECT in SQLData te vervangen
* Er zijn twee nieuwe waarden &quot;IN&quot; en &quot;NOT IN&quot; geïntroduceerd voor het @setOperator-kenmerk
* een nieuwe `<where>`  element, dat een onderliggend element is van het `<node>` element: hiermee kunt u subselecties maken in SELECT

Wanneer een &quot;@expr&quot;attribuut wordt gebruikt, kan SQLData aanwezig zijn. U kunt de volgende termen zoeken: &quot;SQLData&quot;, &quot;aliasSqlTable&quot;, &quot;sql&quot;.

Adobe Campaign v7-instanties zijn standaard beveiligd. De veiligheid komt in termen van definities van veiligheidsgebieden in **[!UICONTROL serverConf.xml]** bestand: het **allowSQLInjection** beheert de SQL-syntaxisbeveiliging.

Als een SQLData-fout optreedt tijdens de uitvoering na de upgrade, moet u dit kenmerk wijzigen om het gebruik van op SQLData gebaseerde syntaxis tijdelijk toe te staan, zodat u de code kunt herschrijven. Hiervoor moet u de volgende optie wijzigen in het dialoogvenster **serverConf.xml** bestand:

```
allowSQLInjection="true"
```

Daarom lanceer de postupgrade met het volgende bevel:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

U moet de veiligheidsstreken vormen (verwijs naar [Beveiliging](#security)) en activeer vervolgens de beveiliging door de optie te wijzigen:

```
allowSQLInjection="false"
```

Hieronder vindt u vergelijkende voorbeelden tussen de oude en de nieuwe syntaxis.

**Filteren op subquery&#39;s**

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

**Het aggregaat**

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
  >Het is niet meer mogelijk om &quot;count()&#42;)&quot;. Je moet &quot;countall()&quot; gebruiken.

* Voormalige syntaxis:

  ```
  <node sql="(select Sum(iToDeliver) from NmsDelivery WHERE O0.iOperationId=iOperationId AND iSandboxMode=0 AND iState>=45)" alias="@nbMessages"/>
  ```

* Nieuwe syntaxis:

  ```
  <node expr="Sum([delivery-linkedDelivery/properties/@toDeliver])" alias= "../@sumToDeliver">
                    <where><condition expr="[validation/@sandboxMode]=0 AND @state>=45" /></where></node>
  ```

**Filters op verbindingen**

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

**Tips en trucs**

In een `<subQuery>` -element, naar een veld &quot;veld&quot; in het hoofdveld verwijzen `<queryDef>`   -element, gebruikt u de volgende syntaxis: `[../@field]`

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

Na de resourcesynchronisatie **postupgrade** kunt u nagaan of de synchronisatie fouten of waarschuwingen genereert.

### Het synchronisatieresultaat weergeven {#view-the-synchronization-result}

Het synchronisatieresultaat kan op twee manieren worden weergegeven:

* In de bevel-lijn interface, worden de fouten geconcretiseerd door een drievoudig chevron **>>>** en synchronisatie wordt automatisch gestopt. Waarschuwingen worden geconcretiseerd door een dubbele chevron **>>** en moet worden opgelost zodra de synchronisatie is voltooid. Aan het eind van postupgrade, wordt een samenvatting getoond in de bevelherinnering. Bijvoorbeeld:

  ```
  2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
  2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
  2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Als de waarschuwing een conflict van middelen betreft, wordt de aandacht van de exploitant vereist om het op te lossen.

* De **postupgrade_`<server version number>`_tijd na upgrade`>`.log** bevat het synchronisatieresultaat. Deze is standaard beschikbaar in de volgende map: **installatiemap/var/`<instance>`postupgrade**. Fouten en waarschuwingen worden aangegeven door de **fout** en **waarschuwing** kenmerken.

### Een conflict oplossen {#resolve-a-conflict}

Conflicten oplossen moet alleen worden uitgevoerd door gevorderde operatoren en gebruikers aan wie beheerdersrechten zijn verleend.

U lost een conflict op door het volgende proces toe te passen:

1. Plaats de cursor in de Adobe Campaign-boomstructuur boven **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**.
1. Selecteer in de lijst het conflict dat u wilt oplossen.

Er zijn drie manieren om een conflict op te lossen:

* **[!UICONTROL Declared as resolved]**: vereist vooraf ingrijpen van de exploitant.
* **[!UICONTROL Accept the new version]**: aanbevolen als de bronnen die bij Adobe Campaign worden geleverd, niet door de gebruiker zijn gewijzigd.
* **[!UICONTROL Keep the current version]**: betekent dat de bijwerking wordt afgewezen.

  >[!IMPORTANT]
  >
  Als u deze resolutiemodus selecteert, loopt u het risico dat de patches in de nieuwe versie verloren gaan. Daarom wordt ten zeerste aanbevolen deze optie niet te gebruiken of alleen voor professionele marktdeelnemers te reserveren.

Ga als volgt te werk als u het conflict handmatig wilt oplossen:

1. Zoek in de onderste sectie van het venster naar de **`_conflict_ string`** om de entiteiten met conflicten te zoeken. De entiteit die met de nieuwe versie is geïnstalleerd, bevat de **new** argument, de entiteit die overeenkomt met de vorige versie bevat de **cus** argument.

   ![](assets/s_ncs_production_conflict002.png)

1. Verwijder de versie die u niet wilt behouden. Verwijder de **`_conflict_argument_ string`** van de entiteit die u bijhoudt.

   ![](assets/s_ncs_production_conflict003.png)

1. Ga naar het conflict dat u had opgelost. Klik op de knop **[!UICONTROL Actions]** pictogram en selecteer **[!UICONTROL Declare as resolved]**.
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

**Voor de postupgrade**, moet u alle schemaverwijzingen van 6.02 schrappen die niet meer in v7 zullen bestaan.

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### Inhoud aanbieden {#offer-content}

In v7 is de inhoud van het aanbod verplaatst. In v6.02 bevond de inhoud zich in elk representatieschema (**nms:emailOfferView**). In v7 bevindt de inhoud zich nu in het aanbiedingsschema. Na de postupgrade is de inhoud daarom niet zichtbaar in de interface. Na postupgrade moet u de aanbiedingsinhoud opnieuw maken of een script ontwikkelen dat de inhoud automatisch van het presentatieschema naar het aanbiedingsschema verplaatst.

>[!IMPORTANT]
>
Als sommige leveringen die geconfigureerde aanbiedingen gebruiken na de migratie moeten worden verzonden, moet u al deze leveringen in v7 verwijderen en opnieuw maken. Als u dat niet kunt, wordt een &quot;verenigbaarheidswijze&quot;aangeboden. Deze modus wordt niet aanbevolen omdat u niet van alle nieuwe functies in Interaction v7 kunt profiteren. Dit is een overgangsmodus waarmee u lopende campagnes kunt voltooien vóór de daadwerkelijke 6.1-migratie. Neem contact met ons op voor meer informatie over deze modus.

Een voorbeeld van een bewegingsscript (**interactionTo610_full_XX.js**) is beschikbaar in het dialoogvenster **Migratie** in de map Adobe Campaign v7. In dit bestand ziet u een voorbeeld van een script voor een client dat gebruikmaakt van één e-mailrepresentatie per aanbieding (de **[!UICONTROL htmlSource]** en **[!UICONTROL textSource]** velden). De inhoud in het dialoogvenster **NmsEmailOfferView** tabel is verplaatst naar de aanbiedingstabel.

>[!NOTE]
>
Met dit script kunt u niet profiteren van de opties voor inhoudsbeheer en renderfuncties. Om van deze functies te profiteren, moet u de catalogusaanbiedingen, in het bijzonder de aanbiedingsinhoud en configuratieruimten heroverwegen.

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

1. Werk in alle &quot;ENV&quot;-omgevingen de lijst met gebruikte velden bij. Bijvoorbeeld voor een aanbiedingsruimte die alleen de **[!UICONTROL htmlSource]**, moet u de opdracht **[!UICONTROL view/htmlSource]**.

   ![](assets/migration_interaction_2.png)

1. In de **[!UICONTROL Type of Environment]** in het veld **[!UICONTROL General]** tab, selecteert u **[!UICONTROL Live]**.

   ![](assets/migration_interaction_3.png)

1. Maak een ontwerpomgeving (bijvoorbeeld &quot;ENV_DESIGN&quot;) en sluit deze aan op de online ENV-omgeving.

   ![](assets/migration_interaction_4.png)

1. Alle &quot;ENV&quot;-omgevingen implementeren biedt spaties (klik met de rechtermuisknop > **[!UICONTROL Actions > Deploy]**) en selecteert u de omgeving ENV_DESIGN.

   ![](assets/migration_interaction_5.png)

1. Doe hetzelfde voor alle &quot;ENV&quot;-omgevingsfuncties.
1. Activeer alle omgevingsfuncties &quot;ENV_DESIGN&quot; op de relevante kanalen.
1. Test of een aanbieding live gaat. Als u geen problemen ondervindt, voert u lopende taken uit op de meest recente workflowtaak **[!UICONTROL Offer notification]** (biedGgt) om alle aanbiedingen live te laten gaan.

   ![](assets/migration_interaction_6.png)

1. Voer uitgebreide tests uit.

   >[!NOTE]
   >
   De namen van categorieën en aanbiedingen online worden gewijzigd nadat u live bent gegaan. Werk op het binnenkomende kanaal alle verwijzingen naar aanbiedingen en categorieën bij.

## Rapporten {#reports}

### Standaardrapporten {#standard-reports}

Alle standaardrapporten gebruiken momenteel de renderingengine v6.x. Als u JavaScript in deze rapporten had toegevoegd, zouden bepaalde elementen niet meer kunnen werken. De oude versie van JavaScript is namelijk niet compatibel met de v6.x-renderingengine. U moet daarom de JavaScript-code controleren en deze later aanpassen. U moet elk rapport testen, met name de exportfunctie.

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

Net als voor rapporten ([Meer informatie](#reports)), als u JavaScript hebt toegevoegd, moet u controleren en indien nodig aanpassen. Als u wilt profiteren van de blauwe banner v7 (met de blauwe tabbladen), moet u de webtoepassing opnieuw publiceren.

Verbindingsmethoden voor webtoepassingen zijn gewijzigd in v7. Als u verbindingsproblemen ondervindt in uw geïdentificeerde webtoepassingen, moet u tijdelijk het dialoogvenster **allowUserPassword** en **sessionTokenOnly** in de **serverConf.xml** bestand. Na de postupgrade wijzigt u de volgende waarden voor opties:

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
