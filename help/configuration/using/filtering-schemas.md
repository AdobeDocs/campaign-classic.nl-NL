---
product: campaign
title: Schema’s filteren
description: Schema’s filteren
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Filterschema&#39;s{#filtering-schemas}

![](../../assets/v7-only.svg)

## Systeemfilters {#system-filters}

U kunt de schematoegang tot specifieke gebruikers, afhankelijk van hun toestemmingen filtreren. Met systeemfilters kunt u de lees- en schrijfmachtigingen beheren van entiteiten die in schema&#39;s zijn beschreven, met **readAccess** en **writeAccess** parameters.

>[!NOTE]
>
>Deze beperking geldt alleen voor niet-technische gebruikers: een technische gebruiker met verwante machtigingen of met behulp van een workflow kan gegevens ophalen en bijwerken .

* **readAccess**: biedt alleen-lezen toegang tot schemagegevens.

   **Waarschuwing** - Alle gekoppelde tabellen moeten met dezelfde beperking worden ingesteld. Deze configuratie kan van invloed zijn op prestaties.

* **writeAccess**: biedt schrijftoegang tot schemagegevens.

Deze filters worden ingevoerd bij de hoofdmap **element** niveau van de regelingen en, zoals in de volgende voorbeelden wordt getoond, kan worden gevormd om toegang te beperken.

* SCHRIJFmachtigingen beperken

   Hier, wordt de filter gebruikt om SCHRIJVEN toestemmingen op het schema voor exploitanten zonder de toestemming van het BEHEER toe te staan. Dit betekent dat alleen beheerders schrijfmachtigingen hebben voor entiteiten die in dit schema worden beschreven.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Rechten voor LEZEN EN SCHRIJVEN beperken:

   Hier, wordt de filter gebruikt om zowel LEZEN als SCHRIJVEN toestemmingen op het schema voor alle exploitanten toe te staan. Alleen de **internal** account, weergegeven door de expressie &quot;$(loginId)!=0&quot;, heeft deze toestemmingen.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   Mogelijk **expr** de kenmerkwaarden die worden gebruikt om de voorwaarde te definiëren, zijn TRUE of FALSE.

>[!NOTE]
>
>Als er geen filter is opgegeven, hebben alle operatoren lees- en schrijfmachtigingen voor het schema.

## Protect ingebouwde schema&#39;s {#protecting-built-in-schemas}

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
>Rechten voor LEZEN en SCHRIJVEN voor de **xtk:sessionInfo** schema&#39;s zijn alleen toegankelijk via de interne account van een Adobe Campaign-exemplaar.

## Systeemfilters van ingebouwde schema&#39;s wijzigen {#modifying-system-filters-of-built-in-schemas}

U kunt nog steeds de systeemfilters wijzigen van de out-of-the-box schema&#39;s die standaard beveiligd zijn vanwege compatibiliteitsproblemen met oudere versies.

>[!NOTE]
>
>Adobe raadt u echter aan de standaardparameters niet te wijzigen om optimale beveiliging te garanderen.

1. Maak een extensie voor het desbetreffende schema of open een bestaande extensie.
1. Een onderliggend element toevoegen **`<sysfilter name="<filter name>" _operation="delete"/>`** in het hoofdelement om toepassing van het filter onder het zelfde in het oorsprongschema te schrappen.
1. U kunt desgewenst een nieuw filter toevoegen, zoals wordt beschreven in [Systeemfilters](#system-filters).
