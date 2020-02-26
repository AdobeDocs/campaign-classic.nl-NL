---
title: Specifieke configuraties in v5.11
seo-title: Specifieke configuraties in v5.11
description: Specifieke configuraties in v5.11
seo-description: null
page-status-flag: never-activated
uuid: d6920beb-a766-4aec-8a8e-d32e47b545a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: fc280640-528d-44de-87d8-52f443772abd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# Specifieke configuraties in v5.11{#specific-configurations-in-v5-11}

In deze sectie wordt beschreven welke aanvullende configuratie is vereist voor het migreren van versie 5.11. U zou ook de montages moeten vormen die in de [Algemene configuratiesectie](../../migration/using/general-configurations.md) worden gedetailleerd.

## Webtoepassingen {#web-applications}

De volgende waarschuwing wordt automatisch weergegeven tijdens de migratie:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Sommige componenten van webtoepassingen, bijvoorbeeld de verschillende formulevelden, hebben @id-kenmerken. Deze worden gebruikt in de XML-code van webtoepassingen en worden niet meer op dezelfde manier gegenereerd. Ze zijn niet zichtbaar in de interface en u moet ze normaal niet gebruiken. In sommige gevallen kunnen @id-kenmerken echter zijn gebruikt om de weergave van webtoepassingen aan te passen, bijvoorbeeld via een stijlpagina of met JavaScript-code.

Tijdens de migratie **moet** u het pad van het logbestand controleren dat in de waarschuwing is opgegeven:

* **Het bestand is niet leeg**: het bevat waarschuwingen die betrekking hebben op inconsistenties die vóór de migratie zijn geconstateerd en die nog steeds bestaan . Dit kan JavaScript-code zijn in een webtoepassing die naar een niet-bestaande id verwijst. Elke fout moet worden gecontroleerd en gecorrigeerd.
* **Het bestand is leeg**: Dit betekent dat er in Adobe Campaign geen problemen zijn aangetroffen.

Of het dossier of niet leeg is, moet u controleren dat deze IDs niet voor configuratie elders (en aanpassingsconfiguratie als dit het geval is) wordt gebruikt.

## Workflows {#workflows}

Aangezien de naam van de installatiemap van Adobe Campagne is gewijzigd, werken sommige workflows mogelijk niet meer na de migratie. Als een workflow naar de map nl5 in een van de activiteiten ervan verwijst, treedt er een fout op. Vervang deze referentie door **build**. U kunt een SQL-query uitvoeren om deze workflows te identificeren (voorbeeld PostSQL):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## Gebruikersvriendelijkheid {#user-friendliness}

De startpagina van Adobe Campaign v5.11 is niet meer beschikbaar.

Hoewel het niet wordt aangeraden, zijn er bepaalde oplossingen als u specifieke interfaces wilt behouden van Adobe Campaign v5.11. Neem contact met ons op voor meer informatie.

## MySQL {#mysql}

>[!IMPORTANT]
>
>MySQL wordt alleen ondersteund in v7 als de hoofddatabase-engine bij het migreren van versie 6.02 of 5.11 met deze engine.

MySQL beheert tijdzones standaard niet. Voer de volgende opdracht uit om tijdzonebeheer in te schakelen:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Raadpleeg de pagina [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) voor meer informatie.

Als de databasestructuur bijvoorbeeld tijdens de configuratie is gewijzigd (specifieke indexen maken, SQL-weergaven maken, enz.), moeten er bepaalde voorzorgsmaatregelen worden getroffen bij het migreren. Bepaalde wijzigingen kunnen immers worden veroorzaakt door onverenigbaarheden met de migratieprocedure. Het maken van SQL-weergaven met **tijdstempelvelden** is bijvoorbeeld niet compatibel met de optie **usetimestamptz** . Daarom raden wij u aan onderstaande aanbevelingen op te volgen:

1. Maak een back-up van de database voordat u de migratie start.
1. SQL-wijzigingen verwijderen.
1. Voer de postupgrade uit volgens de procedure die is beschreven in de sectie [Voorwaarden voor migratie naar Adobe Campagne 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .
   >[!NOTE]
   >
   >U moet de migratiestappen volgen die worden beschreven in de sectie [Voorwaarden voor migratie naar Adobe Campagne 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .
1. SQL-wijzigingen opnieuw integreren.

In dit voorbeeld is een **weergave NmcTrackingLogMessages** gemaakt en heeft dit veld een **tijdstempelveld** met de naam **tslog**. In dit geval mislukt de migratieprocedure en verschijnt het volgende foutbericht:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Om ervoor te zorgen dat de postupgrade werkt, moet u de weergave vóór de migratie verwijderen en na de migratie opnieuw maken en deze aanpassen aan de TIMESTAMP-modus MET TIMEZONE.

## Tekstspatiëring {#tracking}

De volgende formule is gewijzigd. Bij het migreren wordt de oude formule (v5) vervangen door de nieuwe (v7). Als u een gepersonaliseerde formule in de Campagne van Adobe v5 gebruikt, moet deze configuratie in de Campagne van Adobe v7 (**NmsTracking_ClickFormula** en **NmsTracking_OpenFormula** opties) worden aangepast.

Het beheer voor webtracering is ook gewijzigd. Nadat de migratie naar v7 is uitgevoerd, moet u de implementatietovenaar starten om de webtracering te voltooien.

![](assets/migration_web_tracking.png)

Er zijn drie modi beschikbaar:

* **Webtracering** sessie: Als het **[!UICONTROL Leads]** pakket niet is geïnstalleerd, is deze optie standaard geselecteerd. Deze optie is het ideale in termen van prestaties en staat u toe om de grootte van het volgen logboeken te beperken.
* **Permanente webtracering**
* **Anonieme webtracering**: Als het **[!UICONTROL Leads]** pakket is geïnstalleerd, is deze optie standaard geselecteerd. Het is de meest hulpbronnenverbruikende optie. Zoals hierboven, moet de **sSourceId** kolom (in de volgende lijst en de **CrmIncomingLead** lijst) worden geïndexeerd.

>[!NOTE]
>
>Raadpleeg [deze sectie](../../configuration/using/about-web-tracking.md)voor meer informatie over deze drie modi.

## Adobe Campagne v7-boomstructuur {#campaign-vseven-tree-structure}

Tijdens de migratie wordt de boomstructuur automatisch gereorganiseerd op basis van de v7-standaarden. De nieuwe mappen worden toegevoegd, de verouderde mappen worden verwijderd en de inhoud ervan wordt in de map &quot;To move&quot; geplaatst. Alle items in deze map moeten na de migratie worden gecontroleerd en de consultant moet besluiten of de map behouden blijft of dat ze worden verwijderd. Items die vervolgens moeten worden bewaard, moeten naar de juiste plaats worden verplaatst.

Er is een optie toegevoegd voor het uitschakelen van de automatische migratie van de boomstructuur. Deze bewerking is nu handmatig. Verouderde mappen worden niet verwijderd en er worden geen nieuwe mappen toegevoegd. Deze optie mag alleen worden gebruikt als de v5-navigatiestructuur buiten het vak te veel is gewijzigd. Voeg de optie aan de console toe, alvorens, in de **[!UICONTROL Administration > Options]** knoop te migreren:

* Interne naam: NlMigration_KeepFolderStructure
* Gegevenstype:Geheel
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
| ncmSrcSchema | Gegevensschema&#39;s | Inhoudsbeheer geïnstalleerd |
| ncmStylesheet | XSL-stijlbestanden | Inhoudsbeheer geïnstalleerd |
| nmsAdminPlan | Beheer | Campagne geïnstalleerd |
| nmsResourcePlan | Bronnen | Campagne geïnstalleerd |
| nmsResourcesModels | Sjablonen | Campagne geïnstalleerd |
| nmsRootPlan | Campagnebeheer | Campagne geïnstalleerd |
| nmsOperator | Marketing operators | MRM geïnstalleerd |

