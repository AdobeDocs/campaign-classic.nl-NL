---
title: Algemene configuraties
seo-title: Algemene configuraties
description: Algemene configuraties
seo-description: null
page-status-flag: never-activated
uuid: 317a145d-36b0-40fe-a272-ad5e35b0b190
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: f4b1c108-7f71-4aa1-8394-a7f660834c9c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Algemene configuraties{#general-configurations}

In deze sectie wordt de configuratie beschreven die in Adobe Campagne v7 moet worden uitgevoerd als u van versie 5.11 of v6.02 migreert.

Daarnaast:

* Als u migreert vanaf v5.11, moet u ook de configuratie voltooien die in de sectie [Specifieke configuraties in v5.11](../../migration/using/specific-configurations-in-v5-11.md) wordt beschreven.
* Als u migreert vanaf v6.02, moet u ook de configuratie voltooien die in de sectie [Specifieke configuraties in v6.02](../../migration/using/specific-configurations-in-v6-02.md) wordt beschreven.

## Tijdzones {#time-zones}

### Modus voor meerdere tijdzones {#multi-time-zone-mode}

In v6.02 was de modus &quot;multi-time zone&quot; alleen beschikbaar voor PostgreSQL-databasemotoren. Er wordt nu aangeboden welk type database-engine wordt gebruikt. Wij adviseren sterk dat u uw basis in een &quot;multi timezone&quot;basis omzet.

Als u de TIMESTAMP-modus met TIMEZONE wilt gebruiken, moet u ook de optie **-userTimestamptz:1** toevoegen aan de opdrachtregel na de upgrade.

>[!CAUTION]
>
>Als de parameter **-usetimestamptz:1** wordt gebruikt met een incompatibele gegevensbestandmotor, zal uw gegevensbestand worden bedorven en u zult een steun van uw gegevensbestand moeten herstellen en het bevel hierboven opnieuw uitvoeren.

>[!NOTE]
>
>Het is mogelijk om de tijdzone na migratie via de console (**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** knoop) te veranderen.
>
>Raadpleeg [deze sectie](../../installation/using/time-zone-management.md)voor meer informatie over tijdzonebeheer.

### Oracle {#oracle}

Als u een **ORA 01805** -fout krijgt tijdens de postupgrade, betekent dit dat de Oracle-tijdzonebestanden tussen de toepassingsserver en de databaseserver niet gesynchroniseerd zijn. Voer de volgende stappen uit om ze opnieuw te synchroniseren:

1. Voer de volgende opdracht uit om het gebruikte tijdzonebestand te identificeren:

   ```
   select * from v$timezone_file
   ```

   Tijdzonebestanden bevinden zich gewoonlijk in de map **ORACLE_HOME/oracore/zoneinfo/** .

1. Zorg ervoor dat de tijdzonebestanden op beide servers identiek zijn.

Ga voor meer informatie naar: [https://download.oracle.com/docs/cd/E11882_01/server.112/e10729/ch4datetime.htm](http://download.oracle.com/docs/cd/E11882_01/server.112/e10729/ch4datetime.htm).

Een onjuiste uitlijning van de tijdzone tussen client en server kan ook enige vertraging veroorzaken. Daarom raden we aan om dezelfde versie van Oracle-bibliotheek aan client- en serverzijde te gebruiken. Beide tijdzones moeten hetzelfde zijn.

Controleren of beide zijden zich in dezelfde tijdzone bevinden:

1. Controleer de versie van het dossier van de tijdzone op de cliëntkant door het volgende bevel in werking te stellen:

   ```
   genezi -v
   ```

   genezi is een binair getal gevonden in **$ORACLE_HOME/bin** repository.

1. Controleer de versie van het dossier van de tijdzone op de server door het volgende bevel in werking te stellen:

   ```
   select * from v$timezone_file
   ```

1. Als u het bestand met de tijdzone aan de clientzijde wilt wijzigen, gebruikt u de omgevingsvariabele **ORA_TZFILE** .

## Beveiliging {#security}

### Beveiligingszones {#security-zones}

>[!CAUTION]
>
>Om veiligheidsredenen is het Adobe Campagne-platform niet meer standaard toegankelijk: u moet de veiligheidsstreken vormen, en daarom exploitantIP adressen verzamelen.

Adobe Campaign v7 heeft betrekking op het concept van **beveiligingszones**. Elke gebruiker moet met een streek worden geassocieerd om aan login aan een instantie en het IP van de gebruiker adres moet in de adressen of adreswaaiers worden omvat die in de veiligheidsstreek worden bepaald. U kunt de beveiligingszones configureren in het configuratiebestand van de Adobe Campagne-server. De veiligheidsstreek waaraan een gebruiker wordt geassocieerd moet in de console (**[!UICONTROL Administration > Access management > Operators]**) worden bepaald.

**Vraag uw netwerkbeheerder vóór de migratie** om u te helpen de beveiligingszones definiëren die na de migratie moeten worden geactiveerd.

**Na de postupgrade** (vóór het opnieuw opstarten van de server), moet u de veiligheidsstreken vormen.

De configuratie van de veiligheidszone wordt gevonden in [deze sectie](../../installation/using/configuring-campaign-server.md#defining-security-zones).

### Gebruikerswachtwoorden {#user-passwords}

In v7 moet de **interne** en **beheerder** operatorverbinding met een wachtwoord worden beveiligd. We raden u ten zeerste aan wachtwoorden toe te wijzen aan deze accounts en alle exploitantaccounts, **voordat u gaat migreren**. Als u geen wachtwoord voor **intern** hebt opgegeven, kunt u geen verbinding maken. Voer de volgende opdracht in om een wachtwoord aan **internal** toe te wijzen:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>Het **interne** wachtwoord moet voor alle volgende servers identiek zijn. Zie [deze sectie](../../installation/using/campaign-server-configuration.md#internal-identifier) en [deze sectie](../../platform/using/access-management.md#about-permissions)voor meer informatie.

### Nieuwe functies in v7 {#new-features-in-v7}

* Gebruikers zonder machtigingen kunnen geen verbinding meer maken met Adobe Campaign. Hun toestemmingen moeten manueel worden toegevoegd, bijvoorbeeld, door een toestemming te creëren genoemd **verbind**.

   De gebruikers die door deze wijziging worden beïnvloed worden geïdentificeerd en worden vermeld tijdens postupgrade.

* Tekstspatiëring werkt niet meer als het wachtwoord leeg is. Als dit het geval is, zal een foutenmelding u op de hoogte brengen en u vragen om het aan te passen.
* Gebruikerswachtwoorden worden niet meer opgeslagen in het schema **xtk:sessionInfo** .
* Beheermachtigingen zijn nu nodig om de functies **xtk:builder:EvaluateJavaScript** en **xtk:builder:EvaluateJavaScriptTemplate** te gebruiken.

Bepaalde out-of-the-box schema&#39;s zijn gewijzigd en zijn nu standaard alleen toegankelijk met schrijftoegang voor operatoren met de **beheerdersbevoegdheid** :

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

In v5 werkte de **sessiontoken** -parameter aan beide clientzijde (lijst met overzichtstypeschermen, koppelingseditor, enz.) en server (webtoepassingen, rapporten, jsp, jssp, enz.). In versie 7 werkt deze alleen aan de serverzijde. Als u wilt terugkeren naar de volledige functionaliteit zoals in versie 5, moet u de koppelingen wijzigen met deze parameter en via de verbindingspagina doorgeven:

Voorbeeld van koppeling:

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

Nieuwe koppeling met de verbindingspagina:

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!CAUTION]
>
>Als u een exploitant gebruikt verbonden aan een vertrouwd op IP masker, controleer dat het de minimumrechten heeft en dat het in een veiligheidsstreek op **sessionTokenOnly** wijze is.

### SQL-functies {#sql-functions}

Onbekende SQL-functieaanroepen worden niet meer automatisch naar de server verzonden. Momenteel, moeten alle SQL functies aan het schema **xtk:funcList** worden toegevoegd (voor meer op dit, verwijs naar [deze sectie](../../configuration/using/adding-additional-sql-functions.md)). Tijdens het migreren wordt tijdens de postupgrade een optie toegevoegd waarmee u compatibiliteit met oude niet-gedeclareerde SQL-functies kunt behouden. Als u deze functies wilt blijven gebruiken, controleert u of de optie **XtkPassUnknownSQLFunctionsToRDBMS** op het niveau van de **[!UICONTROL Administration > Platform > Options]** node is gedefinieerd.

>[!CAUTION]
>
>We raden u ten zeerste aan deze optie niet te gebruiken vanwege de beveiligingsrisico&#39;s die erin worden geïntroduceerd.

### JSSP {#jssp}

Als u toegang tot bepaalde pagina&#39;s via het HTTP-protocol (niet HTTPS) wilt toestaan, bijvoorbeeld in uw Web-apps, ongeacht de configuratie die in de beveiligingszones wordt uitgevoerd, moet u de parameter **httpAllowed=&quot;true&quot;** in de corresponderende relaisregel opgeven.

Als u anonieme JSSPs gebruikt, moet u de parameter **httpAllowed=&quot;waar&quot;** in een relaisregel voor uw JSSP (**[!UICONTROL serverConf.xml]** dossier) toevoegen:

Bijvoorbeeld:

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## Syntaxis {#syntax}

### JavaScript {#javascript}

In Adobe Campaign v7 is een recentere JavaScript-interpreter geïntegreerd. Deze update kan echter tot een storing van bepaalde scripts leiden. Aangezien de vorige motor machtiger was, zou bepaalde syntaxis werken wat niet langer het geval is met de nieuwe versie van de motor.

De **[!UICONTROL myObject.@attribute]** syntaxis is nu alleen geldig voor XML-objecten. Deze syntaxis kan worden gebruikt voor het aanpassen van leveringen en inhoudsbeheer. Als u dit type syntaxis op een niet voorwerp van XML gebruikte, zullen de verpersoonlijkingseigenschappen niet meer werken.

Voor alle andere objecttypen is de syntaxis nu **[!UICONTROL myObject`[`&quot;kenmerk&quot;`]`]**. Bijvoorbeeld een niet-XML-object dat de volgende syntaxis heeft gebruikt:**[!UICONTROL employee.@sn]**, moet nu de volgende syntaxis gebruiken:**[!UICONTROL employee`[`&quot;sn&quot;`]`]**.

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

Om de beveiliging van de instantie te versterken, is een nieuwe syntaxis geïntroduceerd in Adobe Campagne v7 om de syntaxis te vervangen die op SQLData wordt gebaseerd. Als u deze code-elementen met deze syntaxis gebruikt, moet u deze wijzigen. De belangrijkste elementen zijn:

* Filteren op subquery: de nieuwe syntaxis is gebaseerd op het `<subQuery>` element om een subquery te bepalen
* Aggregaten: de nieuwe syntaxis is &quot;statistische functie(verzameling)&quot;
* Filteren met samenvoeging: de nieuwe syntaxis is `[schemaName:alias:xPath]`

Het schema queryDef (xtk:queryDef) is gewijzigd:

* er is een nieuw `<subQuery>` element beschikbaar om de SELECT in SQLData te vervangen
* Er zijn twee nieuwe waarden &quot;IN&quot; en &quot;NOT IN&quot; geïntroduceerd voor het @setOperator-kenmerk
* een nieuw `<where>` element, dat een onderliggend element van het `<node>` element is: hiermee kunt u &quot;subselecties&quot; maken in SELECT

Wanneer een &quot;@expr&quot;attribuut wordt gebruikt, kan SQLData aanwezig zijn. U kunt de volgende termen zoeken: &quot;SQLData&quot;, &quot;aliasSqlTable&quot;, &quot;sql&quot;.

Adobe Campagne v7-instanties zijn standaard beveiligd. De veiligheid komt in termen van definities van veiligheidsstreken in het **[!UICONTROL serverConf.xml]** dossier: het **allowSQLInjection** -kenmerk beheert de SQL-syntaxisbeveiliging.

Als een SQLData-fout optreedt tijdens de uitvoering na de upgrade, moet u dit kenmerk wijzigen om het gebruik van op SQLData gebaseerde syntaxis tijdelijk toe te staan, zodat u de code kunt herschrijven. Hiervoor moet u de volgende optie wijzigen in het bestand **serverConf.xml** :

```
allowSQLInjection="true"
```

Daarom lanceer de postupgrade met het volgende bevel:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

U moet de veiligheidsstreken vormen (verwijs naar [Veiligheid](#security)), dan reactivate de veiligheid door de optie te veranderen:

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
   >Het is niet meer mogelijk om de functie &quot;count(*)&quot; te gebruiken. Je moet &quot;countall()&quot; gebruiken.

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

Gebruik in een `<subQuery>` `<queryDef>` element de volgende syntaxis om naar een veld van het hoofdelement te verwijzen: `[../@field]`

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

* In de opdrachtregelinterface worden fouten geconcretiseerd door een drievoudig chevron **>>** en wordt de synchronisatie automatisch gestopt. Waarschuwingen worden geconcretiseerd door een dubbel chevron **>>** en moeten worden opgelost zodra de synchronisatie is voltooid. Aan het eind van postupgrade, wordt een samenvatting getoond in de bevelherinnering. Bijvoorbeeld:

   ```
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Als de waarschuwing een conflict van middelen betreft, wordt de aandacht van de exploitant vereist om het op te lossen.

* Het **postupgrade_`<server version number>`_time van het bestand postupgrade`>`.log** bevat het synchronisatieresultaat. Deze is standaard beschikbaar in de volgende map: **installatiemap/var/`<instance>`postupgrade**. Fouten en waarschuwingen worden aangegeven door de **fout** - en **waarschuwingskenmerken** .

### Een conflict oplossen {#resolve-a-conflict}

Conflicten oplossen moet alleen worden uitgevoerd door gevorderde operatoren en gebruikers aan wie beheerdersrechten zijn verleend.

U lost een conflict op door het volgende proces toe te passen:

1. Plaats de cursor in de structuur van de Adobe Campagne. **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**
1. Selecteer in de lijst het conflict dat u wilt oplossen.

Er zijn drie manieren om een conflict op te lossen:

* **[!UICONTROL Declared as resolved]**: van tevoren ingrijpen van de exploitant vereist.
* **[!UICONTROL Accept the new version]**: wordt aangeraden als de bronnen van Adobe Campaign niet door de gebruiker zijn gewijzigd.
* **[!UICONTROL Keep the current version]**: betekent dat de bijwerking wordt afgewezen.

   >[!CAUTION]
   Als u deze resolutiemodus selecteert, loopt u het risico dat de patches in de nieuwe versie verloren gaan. Daarom wordt ten zeerste aanbevolen deze optie niet te gebruiken of alleen voor professionele marktdeelnemers te reserveren.

Ga als volgt te werk als u het conflict handmatig wilt oplossen:

1. Zoek in de onderste sectie van het venster naar de entiteiten met **`_conflict_ string`** conflicten. De entiteit die met de nieuwe versie is geïnstalleerd, bevat het **nieuwe** argument. De entiteit die met de vorige versie overeenkomt, bevat het **focusargument** .

   ![](assets/s_ncs_production_conflict002.png)

1. Verwijder de versie die u niet wilt behouden. Verwijder de entiteit **`_conflict_argument_ string`** die u bijhoudt.

   ![](assets/s_ncs_production_conflict003.png)

1. Ga naar het conflict dat u had opgelost. Klik op het **[!UICONTROL Actions]** pictogram en selecteer **[!UICONTROL Declare as resolved]**.
1. Sla uw wijzigingen op: het conflict is nu opgelost .

## Tomcat {#tomcat}

De geïntegreerde Tomcat-server in Adobe Campaign v7 is van versie veranderd (Tomcat 7). De installatiemap (tomcat-6) is daarom ook gewijzigd (tomcat 7). Controleer na de upgrade of de paden wel zijn gekoppeld aan de bijgewerkte map (in het **[!UICONTROL serverConf.xml]** bestand):

```
$(XTK_INSTALL_DIR)/tomcat-7/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-7/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/el-api.jar
```

## Interactie {#interaction}

### Vereisten {#prerequisites}

**Vóór postupgrade**, moet u alle schemaverwijzingen van 6.02 schrappen die niet meer in v7 zullen bestaan.

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### Inhoud aanbieden {#offer-content}

In v7 is de inhoud van het aanbod verplaatst. In v6.02 bevond de inhoud zich in elk weergaveschema (**nms:emailOfferView**). In v7 bevindt de inhoud zich nu in het aanbiedingsschema. Na de postupgrade is de inhoud daarom niet zichtbaar in de interface. Na postupgrade moet u de aanbiedingsinhoud opnieuw maken of een script ontwikkelen dat de inhoud automatisch van het presentatieschema naar het aanbiedingsschema verplaatst.

>[!CAUTION]
Als sommige leveringen die geconfigureerde aanbiedingen gebruiken na de migratie moeten worden verzonden, moet u al deze leveringen in v7 verwijderen en opnieuw maken. Als u dat niet kunt, wordt een &quot;verenigbaarheidswijze&quot;aangeboden. Deze modus wordt niet aanbevolen omdat u niet van alle nieuwe functies in Interaction v7 kunt profiteren. Dit is een overgangsmodus waarmee u lopende campagnes kunt voltooien vóór de daadwerkelijke 6.1-migratie. Neem contact met ons op voor meer informatie over deze modus.

Een voorbeeld van een bewegingsscript (**interactionTo610_full_XX.js**) is beschikbaar in de map **Migration** in de map Adobe Campagne v7. In dit bestand ziet u een voorbeeld van een script voor een client dat gebruikmaakt van één e-mailrepresentatie per aanbieding (de **[!UICONTROL htmlSource]** velden en **[!UICONTROL textSource]** velden). De inhoud in de tabel **NmsEmailOfferView** is verplaatst naar de tabel met aanbiedingen.

>[!NOTE]
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

1. Werk in alle &quot;ENV&quot;-omgevingen de lijst met gebruikte velden bij. Als u bijvoorbeeld een aanbiedingsruimte wilt gebruiken waarin alleen de inhoud wordt gebruikt, moet u de inhoud toevoegen **[!UICONTROL htmlSource]****[!UICONTROL view/htmlSource]**.

   ![](assets/migration_interaction_2.png)

1. Selecteer in het **[!UICONTROL Type of Environment]** veld op het **[!UICONTROL General]** tabblad de optie **[!UICONTROL Live]**.

   ![](assets/migration_interaction_3.png)

1. Maak een ontwerpomgeving (bijvoorbeeld &quot;ENV_DESIGN&quot;) en sluit deze aan op de online ENV-omgeving.

   ![](assets/migration_interaction_4.png)

1. Implementeer alle &quot;ENV&quot;-omgeving met spaties (klik met de rechtermuisknop > **[!UICONTROL Actions > Deploy]**) en selecteer de omgeving &quot;ENV_DESIGN&quot;.

   ![](assets/migration_interaction_5.png)

1. Doe hetzelfde voor alle &quot;ENV&quot;-omgevingsfuncties.
1. Activeer alle omgevingsfuncties &quot;ENV_DESIGN&quot; op de relevante kanalen.
1. Test of een aanbieding live gaat. Als u geen problemen tegenkomt, voert u lopende taken uit op de meest recente workflowtaak **[!UICONTROL Offer notification]** (offerMgt) om alle aanbiedingen live te laten gaan.

   ![](assets/migration_interaction_6.png)

1. Voer uitgebreide tests uit.

   >[!NOTE]
   De namen van categorieën en aanbiedingen online worden gewijzigd nadat u live bent gegaan. Werk op het binnenkomende kanaal alle verwijzingen naar aanbiedingen en categorieën bij.

## Rapporten {#reports}

### Standaardrapporten {#standard-reports}

Alle standaardrapporten maken momenteel gebruik van de renderingengine v6.x. Als u JavaScript in deze rapporten had toegevoegd, zouden bepaalde elementen niet meer kunnen werken. De oude versie van JavaScript is namelijk niet compatibel met de v6.x-renderingengine. U moet daarom de JavaScript-code controleren en deze later aanpassen. U moet elk rapport testen, met name de exportfunctie.

### Persoonlijke rapporten {#personalized-reports}

Als u de blauwe banner vanaf v7 wilt hebben (zodat u toegang hebt tot de universa), moet u rapporten opnieuw publiceren. Als u problemen ondervindt, kunt u de v6.0-renderingengine forceren. Om dit te doen, ga naar **[!UICONTROL Properties]** binnen het rapport, klik **[!UICONTROL Rendering]** en kies de **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** teruggevende motor.

![](assets/migration_reports_1.png)

Als u wilt profiteren van de nieuwe rapportfuncties, moet u de v.6.x-renderingengine selecteren. Controleer in dit geval al uw scripts en wijzig deze zo nodig. Als u een specifiek script voor OpenOffice hebt toegevoegd voor het exporteren van PDF-bestanden, werkt dit niet meer met de nieuwe PDF-exportengine (PhantomJS).

## Webtoepassingen {#web-applications}

Er zijn twee families voor webtoepassingen:

* geïdentificeerde webtoepassingen (samen gezien, goedkeuringsformulieren, interne extranetontwikkelingen);
* anonieme webtoepassingen (web- of vragenformulieren).

### Geïdentificeerde webtoepassingen {#identified-web-applications}

Net als voor rapporten (zie [Rapporten](#reports)), als u JavaScript hebt toegevoegd, moet u controleren en aanpassen indien nodig. Als u wilt profiteren van de blauwe banner v7 (die de universen bevat), moet u de webtoepassing opnieuw publiceren. Als uw JavaScript-code werkt, kunt u de v6.x-renderingengine selecteren. Als dit niet het geval is, kunt u de v6.0-renderingengine gebruiken terwijl u uw code aanpast en vervolgens de v6.x-renderingengine gebruiken.

>[!NOTE]
De stappen voor het selecteren van de renderingengine zijn gelijk aan die voor het selecteren van rapporten. Zie [Gepersonaliseerde rapporten](#personalized-reports).

Verbindingsmethoden voor webtoepassingen zijn gewijzigd in v7. Als u verbindingsproblemen tegenkomt in uw geïdentificeerde webtoepassingen, moet u tijdelijk de opties **allowUserPassword** en **sessionTokenOnly** activeren in het bestand **serverConf.xml** . Na de postupgrade wijzigt u de volgende waarden voor opties:

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

Als u problemen ondervindt, publiceert u de webtoepassing opnieuw. Als het probleem zich blijft voordoen, kunt u de v6.0-renderingengine selecteren. Als u JavaScript niet hebt toegevoegd, kunt u de v6.x-renderingengine selecteren en profiteren van de nieuwe functies.

>[!NOTE]
De stappen voor het selecteren van de renderingengine zijn gelijk aan die voor het selecteren van rapporten. Zie [Gepersonaliseerde rapporten](#personalized-reports).

## Rood-Hoed {#red-hat}

Als de out-of-the-box schema&#39;s in v6.02 of v5.11 zijn geschrapt, kunt u uw schema&#39;s na de postupgrade misschien niet meer uitgeven. Als dit gebeurt, voert u de opdracht uit:

```
su - neolane
nlserver config -postupgrade -instance:<instance name> -force
```
