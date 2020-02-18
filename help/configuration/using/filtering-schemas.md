---
title: Filterschema's
seo-title: Filterschema's
description: Filterschema's
seo-description: null
page-status-flag: never-activated
uuid: 04a90785-3084-42fd-85af-77bc28687579
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 64d4c5b8-db0b-4287-8d30-4bf09878a401
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Filterschema&#39;s{#filtering-schemas}

## Systeemfilters {#system-filters}

U kunt de schematoegang tot specifieke gebruikers, afhankelijk van hun toestemmingen filtreren. Met systeemfilters kunt u de lees- en schrijfmachtigingen beheren van entiteiten die in schema&#39;s worden beschreven, met behulp van **parameters readAccess** en **writeAccess** .

>[!NOTE]
>
>Deze beperking geldt alleen voor niet-technische gebruikers: een technische gebruiker met verwante machtigingen of met behulp van een workflow kan gegevens ophalen en bijwerken .

* **readAccess**: biedt alleen-lezen toegang tot schemagegevens.

   **Waarschuwing** - Alle gekoppelde tabellen moeten met dezelfde beperking zijn ingesteld. Deze configuratie kan van invloed zijn op prestaties.

* **writeAccess**: biedt schrijftoegang tot schemagegevens.

Deze filters zijn ingegaan op het belangrijkste **elementniveau** van de schema&#39;s en, zoals aangetoond in de volgende voorbeelden, kunnen worden gevormd om toegang te beperken.

* SCHRIJFmachtigingen beperken

   Hier, wordt de filter gebruikt om SCHRIJVEN toestemmingen op het schema voor exploitanten zonder de toestemming van het BEHEER toe te staan. Dit betekent dat alleen beheerders schrijfmachtigingen hebben voor entiteiten die in dit schema worden beschreven.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Lezen- en schrijfmachtigingen beperken:

   Hier, wordt de filter gebruikt om zowel LEZEN als SCHRIJVEN toestemmingen op het schema voor alle exploitanten toe te staan. Alleen de **interne** account, vertegenwoordigd door de expressie &quot;$(loginId)!=0&quot;, heeft deze toestemmingen.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   Mogelijke **expr** -kenmerkwaarden die worden gebruikt om de voorwaarde te definiëren, zijn TRUE of FALSE.

>[!NOTE]
>
>Als er geen filter is opgegeven, hebben alle operatoren lees- en schrijfmachtigingen voor het schema.

## Ingebouwde schema&#39;s beschermen {#protecting-built-in-schemas}

Door gebrek, zijn de ingebouwde schema&#39;s slechts toegankelijk met SCHRIJVEN toestemmingen voor exploitanten met de rechten van het BEHEER:

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

>[!IMPORTANT]
>
>LEES- en SCHRIJFmachtigingen voor het schema **xtk:sessionInfo** zijn alleen toegankelijk voor de interne account van een Adobe Campagne-instantie.

## Systeemfilters van ingebouwde schema&#39;s wijzigen {#modifying-system-filters-of-built-in-schemas}

U kunt nog steeds de systeemfilters wijzigen van de out-of-the-box schema&#39;s die standaard beveiligd zijn vanwege compatibiliteitsproblemen met oudere versies.

>[!NOTE]
>
>Adobe raadt u echter aan de standaardparameters niet te wijzigen om optimale beveiliging te garanderen.

1. Maak een extensie voor het desbetreffende schema of open een bestaande extensie.
1. Voeg een onderliggend element **`<sysfilter name="<filter name>" _operation="delete"/>`** in het hoofdelement toe om toepassing van het filter onder het zelfde in het oorsprongschema te schrappen.
1. U kunt desgewenst een nieuw filter toevoegen, zoals wordt beschreven in [Systeemfilters](#system-filters).

