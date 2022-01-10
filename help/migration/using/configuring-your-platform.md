---
product: campaign
title: Pas uw configuratie aan
description: Leer hoe u uw configuratie aanpast voor en na een migratie naar Campagne v7
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 327f220d6700242308ef3738a38cc95b970e3f46
workflow-type: tm+mt
source-wordcount: '1980'
ht-degree: 3%

---

# Pas uw configuratie aan{#configuring-your-platform}

![](../../assets/v7-only.svg)

Bepaalde belangrijke wijzigingen in Adobe Campaign v7 vereisen een specifieke configuratie. Deze configuraties kunnen nodig zijn voor of na het migreren.

Gedetailleerde configuratie die moet worden uitgevoerd in Adobe Campaign v7 wanneer wordt gemigreerd vanuit Campagne v5 of v6 is beschikbaar in [deze pagina](general-configurations.md).


Tijdens de migratie **NmsRecipient** tabel wordt opnieuw samengesteld op basis van de schemadefinitie. Eventuele wijzigingen die buiten Adobe Campaign in de SQL-structuur van deze tabel zijn aangebracht, gaan verloren.

Voorbeeld van te controleren elementen:

* Als u een kolom (of een index) hebt toegevoegd aan de **NmsRecipient** tabel maar u hebt deze niet in het schema gedetailleerd, deze wordt niet opgeslagen.
* De **tabelruimte** Het attribuut neemt zijn waarden door gebrek terug, met andere woorden die die in de plaatsingstovenaar worden bepaald.
* Als u een verwijzingsweergave hebt toegevoegd aan de **NmsRecipient** voor het migreren.


## Voor de migratie {#before-the-migration}

Bij het migreren naar Adobe Campaign v7 moeten de volgende elementen worden geconfigureerd. Deze elementen moeten worden aangepakt voordat met de **postupgrade**.

* Tijdzones

   Tijdens een migratie vanaf een v5.11-platform moet u opgeven welke tijdzone u tijdens de postupgrade wilt gebruiken.

   Als u de modus &quot;multi timezone&quot; wilt gebruiken, raadpleegt u [deze sectie](../../migration/using/general-configurations.md#time-zones).

   Als u Oracle als gegevensbestand gebruikt, controleer dat de dossiers van de Oracle timezone behoorlijk tussen de toepassingsserver en de gegevensbestandserver zijn gesynchroniseerd. [Meer informatie](../../migration/using/general-configurations.md#oracle)

* Beveiligingszones

   Om veiligheidsredenen is het Adobe Campaign-platform niet meer standaard toegankelijk: u moet de veiligheidsstreken vormen, die het verzamelen van de gebruikersIP adressen vóór de migratie vereist. [Meer informatie](../../migration/using/general-configurations.md#security)

* Syntaxis

   Sommige Javascript-code wordt mogelijk niet meer geaccepteerd in de versie v7 vanwege het gebruik van een nieuwe interpreter. [Meer informatie](../../migration/using/general-configurations.md#javascript).

   Op dezelfde manier wordt in Adobe Campaign v7 een nieuwe syntaxis geïntroduceerd die de op SQLData gebaseerde syntaxis vervangt. Als u code-elementen met deze syntaxis gebruikt, moet u deze aanpassen. [Meer informatie](../../migration/using/general-configurations.md#sqldata)

* Wachtwoorden

   U moet de **Beheer** en **Intern** wachtwoorden. [Meer informatie](../../migration/using/before-starting-migration.md#user-passwords)

* Boomstructuur

   Als u migreert vanaf een v5.11-platform, moet u de structuurmappen opnieuw ordenen volgens de Adobe Campaign v6-normen. [Meer informatie](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).

* Interaction

   Als u migreert op basis van Campagne v6.02 en de  **Interactie** moet u alle 6.02 schemaverwijzingen verwijderen die niet meer in v7 bestaan. [Meer informatie](../../migration/using/general-configurations.md#interaction)

## Na de migratie {#after-the-migration}

Na uitvoering **postupgrade**, de volgende elementen controleren en configureren:

* Pagina&#39;s spiegelen

   Het aanpassingsblok van de pagina Mirror is gewijzigd met v6.x. Deze nieuwe versie verbetert de beveiliging bij het openen van deze pagina&#39;s.

   Als u het v5-verpersoonlijkingsblok in uw berichten hebt gebruikt, mislukt de weergave van de spiegelpagina. Adobe adviseert hoogst om het nieuwe verpersoonlijkingsblok te gebruiken wanneer het opnemen van spiegelpagina in uw berichten.

   Als tijdelijke oplossing (en aangezien de spiegelpagina&#39;s nog steeds actief zijn) kunt u echter terugkeren naar het oude aanpassingsblok om dit probleem te voorkomen door de optie te wijzigen **[!UICONTROL XtkAcceptOldPasswords]** en stel deze in op **[!UICONTROL 1]**. Dit heeft geen invloed op het gebruik van het nieuwe personalisatieblok v6.x.

* Syntaxis

   Als er fouten optreden met betrekking tot de syntaxis, moet u de functie **allowSQLInjection** in de **serverConf.xml** bestand, omdat u dan tijd hebt om de code te herschrijven. Nadat de code is aangepast, moet u de beveiliging opnieuw activeren. [Meer informatie](../../migration/using/general-configurations.md#sqldata)

* Conflicten

   De migratie wordt uitgevoerd via een postupgrade en conflicten kunnen optreden in rapporten, formulieren of webtoepassingen. Deze conflicten kunnen vanaf de console worden opgelost. [Meer informatie](../../migration/using/general-configurations.md#conflicts)

* Tomcat

   Als u de installatiemap hebt aangepast, moet u controleren of deze na de migratie correct is bijgewerkt. [Meer informatie](../../migration/using/general-configurations.md#tomcat)

* Rapporten

   Alle out-of-box-rapporten gebruiken momenteel de v6.x-renderingengine. Als u JavaScript-code aan de rapporten hebt toegevoegd, kan dit invloed hebben op bepaalde elementen. [Meer informatie](../../migration/using/general-configurations.md#reports)

* Webtoepassingen

   Na postupgrade, als u om het even welke problemen hebt die met uw geïdentificeerde toepassingen van het Web verbinden, moet u activeren **allowUserPassword** en **sessionTokenOnly** opties in het dialoogvenster **serverConf.xml** bestand. Om veiligheidskwesties te vermijden, moeten deze twee opties opnieuw geactiveerd worden nadat het probleem is opgelost. [Meer informatie](../../migration/using/general-configurations.md#identified-web-applications)

   Afhankelijk van het type van de toepassingen van het Web en hun configuratie, moet u extra manipulaties uitvoeren om ervoor te zorgen zij correct werken. [Meer informatie](../../migration/using/general-configurations.md#web-applications)

   Als u van een v5.11-platform migreert, moeten er aanvullende configuraties worden uitgevoerd. [Meer informatie](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* Beveiligingszones

   Voordat u de server start, moet u de beveiligingszones configureren. [Meer informatie](../../installation/using/security-zones.md) en [hier zien](../../migration/using/general-configurations.md#security)

* Workflows

   Als u migreert vanaf een v5.11-platform, moet u de map workflows controleren. [Meer informatie](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Tracking

   Als u migreert vanaf een v5.11-platform, moet u de modus Tekstspatiëring configureren. [Meer informatie](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Interactie

   Als u **Interactie**, moet u parameters aanpassen na de migratie. [Meer informatie](../../migration/using/general-configurations.md#interaction)

* Dashboards

   Als er een clientfout optreedt, moet u uw dashboards bijwerken met de nieuwe Adobe Campaign v7-code of de volgende bestanden handmatig kopiëren van de versie 6.02-instantie naar de v7-instantie:

   ```
   v6.02 files and spaces:
   /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
   /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
   v6.1 files and spaces:
   /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
   /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
   ```


## Specifieke configuraties van v5.11 tot en met v7{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

In deze sectie wordt beschreven welke aanvullende configuratie is vereist voor het migreren van versie 5.11. U zou ook de montages moeten vormen die in [Algemene configuraties](../../migration/using/general-configurations.md) sectie.

### Webapplicaties {#web-applications-v5}

De volgende waarschuwing wordt automatisch weergegeven tijdens de migratie:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Sommige componenten van webtoepassingen, bijvoorbeeld de verschillende formulevelden, hebben @id-kenmerken. Deze worden gebruikt in de XML-code van webtoepassingen en worden niet meer op dezelfde manier gegenereerd. Ze zijn niet zichtbaar in de interface en u moet ze normaal niet gebruiken. In sommige gevallen kunnen @id-kenmerken echter zijn gebruikt om de weergave van webtoepassingen aan te passen, bijvoorbeeld via een stijlpagina of met JavaScript-code.

Tijdens de migratie **moet** Controleer het pad naar het logbestand dat in de waarschuwing is opgegeven:

* **Het bestand is niet leeg**: het bevat waarschuwingen die betrekking hebben op inconsistenties die vóór de migratie zijn geconstateerd en die nog steeds bestaan . Dit kan JavaScript-code zijn in een webtoepassing die naar een niet-bestaande id verwijst. Elke fout moet worden gecontroleerd en gecorrigeerd.
* **Het bestand is leeg**: dit betekent dat Adobe Campaign geen problemen heeft ontdekt.

Of het dossier of niet leeg is, moet u controleren dat deze IDs niet voor configuratie elders (en aanpassingsconfiguratie als dit het geval is) wordt gebruikt.

### Workflows {#workflows}

Aangezien de naam van de Adobe Campaign-installatiemap is gewijzigd, werken sommige workflows mogelijk niet meer na de migratie. Als een workflow naar de map nl5 in een van de activiteiten ervan verwijst, treedt er een fout op. Deze verwijzing vervangen door **build**. U kunt een SQL-query uitvoeren om deze workflows te identificeren (voorbeeld PostSQL):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>MySQL wordt alleen ondersteund in v7 als de hoofddatabase-engine bij het migreren van versie 6.02 of 5.11 met deze engine.

MySQL beheert tijdzones standaard niet. Voer de volgende opdracht uit om tijdzonebeheer in te schakelen:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Raadpleeg voor meer informatie de [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) pagina.

Als de databasestructuur bijvoorbeeld tijdens de configuratie is gewijzigd (specifieke indexen maken, SQL-weergaven maken, enz.), moeten er bepaalde voorzorgsmaatregelen worden getroffen bij het migreren. Bepaalde wijzigingen kunnen immers worden veroorzaakt door onverenigbaarheden met de migratieprocedure. Zo maakt u SQL-weergaven die **Tijdstempel** velden zijn niet compatibel met de **usetimestamptz** optie. Daarom raden wij u aan onderstaande aanbevelingen op te volgen:

1. Maak een back-up van de database voordat u de migratie start.
1. SQL-wijzigingen verwijderen.
1. Naupgrade uitvoeren
   >[!NOTE]
   >
   >U dient de volgende migratiestappen te volgen: [deze sectie](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. SQL-wijzigingen opnieuw integreren.

In dit voorbeeld wordt een **NmcTrackingLogMessages** mening was gecreeerd en dit heeft **Tijdstempel** veldnaam **tslog**. In dit geval mislukt de migratieprocedure en verschijnt het volgende foutbericht:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Om ervoor te zorgen dat de postupgrade werkt, moet u de weergave vóór de migratie verwijderen en na de migratie opnieuw maken en deze aanpassen aan de TIMESTAMP-modus MET TIMEZONE.

### Tekstspatiëring {#tracking}

De volgende formule is gewijzigd. Bij het migreren wordt de oude formule (v5) vervangen door de nieuwe (v7). Als u een gepersonaliseerde formule in Adobe Campaign v5 gebruikt, moet deze configuratie worden aangepast in Adobe Campaign v7 (**NmsTracking_ClickFormula** en **NmsTracking_OpenFormula** opties).

Het beheer voor webtracering is ook gewijzigd. Nadat de migratie naar v7 is uitgevoerd, moet u de implementatietovenaar starten om de webtracering te voltooien.

![](assets/migration_web_tracking.png)

Er zijn drie modi beschikbaar:

* **Webreeksspatiëring**: Als de **[!UICONTROL Leads]** is niet geïnstalleerd, is deze optie standaard geselecteerd. Deze optie is het ideale in termen van prestaties en staat u toe om de grootte van het volgen logboeken te beperken.
* **Permanente webtracering**
* **Anonieme webtracering**: Als de **[!UICONTROL Leads]** is geïnstalleerd, is deze optie standaard geselecteerd. Het is de meest hulpbronnenverbruikende optie. Als hierboven, **sSourceId** de kolom moet worden geïndexeerd (in de volgende tabel en de **CrmIncomingLead** tabel).

>[!NOTE]
>
>Raadpleeg voor meer informatie over deze drie modi [deze sectie](../../configuration/using/about-web-tracking.md).

### Adobe Campaign v7-boomstructuur {#campaign-vseven-tree-structure}

Tijdens de migratie wordt de boomstructuur automatisch gereorganiseerd op basis van de v7-standaarden. De nieuwe mappen worden toegevoegd, de verouderde mappen worden verwijderd en de inhoud ervan wordt in de map &quot;To move&quot; geplaatst. Alle items in deze map moeten na de migratie worden gecontroleerd en de consultant moet besluiten of de map behouden blijft of dat ze worden verwijderd. Items die vervolgens moeten worden bewaard, moeten naar de juiste plaats worden verplaatst.

Er is een optie toegevoegd voor het uitschakelen van de automatische migratie van de boomstructuur. Deze bewerking is nu handmatig. Verouderde mappen worden niet verwijderd en er worden geen nieuwe mappen toegevoegd. Deze optie mag alleen worden gebruikt als de v5-navigatiestructuur buiten het vak te veel is gewijzigd. Voeg de optie vóór de migratie toe aan de console in het dialoogvenster **[!UICONTROL Administration > Options]** knooppunt:

* Interne naam: NlMigration_KeepFolderStructure
* Gegevenstype: Geheel
* Waarde (tekst): 1

Als u deze optie gebruikt, moet u na de migratie verouderde mappen verwijderen, de nieuwe mappen toevoegen en alle vereiste controles uitvoeren.

**Lijst met nieuwe mappen**:

De volgende mappen moeten na de migratie worden toegevoegd:

| Interne naam | Label | Voorwaarde |
|---|---|---|
| nmsAutoObjects | Automatisch gemaakte objecten | - |
| nmsCampaignAdmin | Campagnebeheer | - |
| nmsCampaignMgt | Campagnebeheer | - |
| nmsCampaignRes | Campagnebeheer | - |
| nmsModels | Sjablonen | - |
| nmsOnlineRes | Online | - |
| nmsProduction | Productie | - |
| nmsProfileProcess | Processen | - |
| xtkDashboard | Dashboards | - |
| xtkPlatformAdmin | Platform | - |
| nmsLocalOrgUnit | Organisatorische eenheden | - |
| nmsMRM | MRM | MRM geïnstalleerd |
| nmsOperations | Campagnes | Campagne geïnstalleerd |

**Lijst met verouderde mappen**:

De verouderde mappen die na de migratie moeten worden verwijderd, zijn als volgt:

>[!NOTE]
>
>De volledige inhoud van de verouderde mappen moet worden gecontroleerd en voor elk onderdeel beslist de consultant of de map moet worden bewaard of verwijderd. De te bewaren voorwerpen moeten naar de juiste plaats worden verplaatst.

| Interne naam | Label | Voorwaarde |
|---|---|---|
| nmsAdministration | Beheer | - |
| nmsDeliveryMgt | Campagne uitvoeren | - |
| ncmContent | Inhoudsbeheer | Inhoudsbeheer geïnstalleerd |
| ncmForm | Invoerformulier | Inhoudsbeheer geïnstalleerd |
| ncmImage | Afbeeldingen | Inhoudsbeheer geïnstalleerd |
| ncmJavascript | JavaScript-codes | Inhoudsbeheer geïnstalleerd |
| ncmJst | JavaScript-sjablonen | Inhoudsbeheer geïnstalleerd |
| ncmParameters | Configuratie | Inhoudsbeheer geïnstalleerd |
| ncmSrcSchema | Gegevensschema’s | Inhoudsbeheer geïnstalleerd |
| ncmStylesheet | XSL-stijlbestanden | Inhoudsbeheer geïnstalleerd |
| nmsAdminPlan | Beheer | Campagne geïnstalleerd |
| nmsResourcePlan | Bronnen | Campagne geïnstalleerd |
| nmsResourcesModels | Sjablonen | Campagne geïnstalleerd |
| nmsRootPlan | Campagnebeheer | Campagne geïnstalleerd |
| nmsOperator | Marketing operators | MRM geïnstalleerd |


## Specifieke configuraties van v6.02 tot v7{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

In de volgende sectie wordt beschreven welke aanvullende configuratie is vereist voor het migreren van versie 6.02. U moet ook de instellingen configureren die in [deze pagina](../../migration/using/general-configurations.md).

### Webapplicaties {#web-applications-v6}

Als u migreert op basis van versie 6.02, worden mogelijk foutlogboeken weergegeven met betrekking tot webtoepassingen van het overzichtstype. Voorbeelden van foutberichten:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Deze webtoepassingen maakten gebruik van SQLData en zijn niet compatibel met versie 7 vanwege de verhoogde beveiliging. Deze fouten leiden tot een migratiefout.

Als u deze webtoepassingen niet hebt gebruikt, voert u het volgende opschoonscript uit en voert u de postupgrade opnieuw uit:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Als u deze webtoepassingen hebt gewijzigd en u wilt deze blijven gebruiken in v7, moet u het dialoogvenster **allowSQLInjection** in uw verschillende beveiligingszones en start de naupgrade opnieuw. Zie de [SQLData](../../migration/using/general-configurations.md#sqldata) voor meer informatie hierover.

### Berichtencentrum {#message-center}

Na een migratie van de controleinstantie van het Centrum van het Bericht, moet u de transactionele berichtmalplaatjes voor hen opnieuw publiceren om te werken.

In v7 zijn de namen van transactionele berichtsjablonen op uitvoeringsinstanties gewijzigd. Ze worden momenteel voorafgegaan door de naam van de operator die correspondeert met de besturingsinstantie waarop ze zijn gemaakt, bijvoorbeeld **control1_template1_rt** waarbij **control1** is de naam van de operator). Als u een significant volume van malplaatjes hebt, adviseren wij schrappend oude malplaatjes op controleinstanties.