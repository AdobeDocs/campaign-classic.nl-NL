---
product: campaign
title: Schema’s filteren
description: Schema’s filteren
feature: Custom Resources
role: Developer
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 1%

---

# Filterschema&#39;s{#filtering-schemas}

## Systeemfilters {#system-filters}

U kunt de schematoegang tot specifieke gebruikers, afhankelijk van hun toestemmingen filtreren. De filters van het systeem laten u lezen beheren en schrijven toestemmingen van entiteiten die in schema&#39;s worden gedetailleerd, gebruikend **readAccess** en **writeAccess** parameters.

>[!NOTE]
>
>Deze beperking geldt alleen voor niet-technische gebruikers: een technische gebruiker met gerelateerde machtigingen of met behulp van een workflow kan gegevens ophalen en bijwerken.

* **readAccess**: verleent read slechts toegang tot schemagegevens.

  **Waarschuwing** - Alle verbonden lijsten moeten met de zelfde beperking worden geplaatst. Deze configuratie kan van invloed zijn op prestaties.

* **writeAccess**: verleent schrijftoegang tot schemagegevens.

Deze filters zijn ingegaan op het belangrijkste **element** niveau van de schema&#39;s en, zoals aangetoond in de volgende voorbeelden, kunnen worden gevormd om toegang te beperken.

* SCHRIJFmachtigingen beperken

  Hier, wordt de filter gebruikt om SCHRIJVEN toestemmingen op het schema voor exploitanten zonder de toestemming van het BEHEER toe te staan. Dit betekent dat alleen beheerders schrijfmachtigingen hebben voor entiteiten die in dit schema worden beschreven.

  ```
  <sysFilter name="writeAccess">      
   <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
  </sysFilter>
  ```

* Rechten voor LEZEN EN SCHRIJVEN beperken:

  Hier, wordt de filter gebruikt om zowel LEZEN als SCHRIJVEN toestemmingen op het schema voor alle exploitanten toe te staan. Slechts de **interne** rekening, die door de uitdrukking &quot;$ (loginId) wordt vertegenwoordigd!=0&quot;, heeft deze toestemmingen.

  ```
  <sysFilter name="readAccess"> 
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  
  <sysFilter name="writeAccess">  
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  ```

  Mogelijke **expr** kenmerkwaarden die worden gebruikt om de voorwaarde te bepalen zijn WAAR of VALS.

>[!NOTE]
>
>Als er geen filter is opgegeven, hebben alle operatoren lees- en schrijfmachtigingen voor het schema.

## Ingebouwde schema&#39;s beschermen {#protecting-built-in-schemas}

Door gebrek, zijn de ingebouwde schema&#39;s slechts toegankelijk met SCHRIJVEN toestemmingen voor exploitanten met de rechten van het BEHEER:

* ncm:publishing
* nl:monitoring
* nms:calendar
* xtk:builder
* xtk:connections
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk:image
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
* xtk:strings
* xtk:xslt

>[!IMPORTANT]
>
>LEES en SCHRIJF toestemmingen voor het **xtk:sessionInfo** schema zijn slechts toegankelijk door de interne rekening van een instantie van Adobe Campaign.

## Systeemfilters van ingebouwde schema&#39;s wijzigen {#modifying-system-filters-of-built-in-schemas}

U kunt nog steeds de systeemfilters wijzigen van de out-of-the-box schema&#39;s die standaard beveiligd zijn vanwege compatibiliteitsproblemen met oudere versies.

>[!NOTE]
>
>Adobe raadt u echter aan de standaardparameters niet te wijzigen om optimale beveiliging te garanderen.

1. Maak een extensie voor het desbetreffende schema of open een bestaande extensie.
1. Voeg een onderliggend element **`<sysfilter name="<filter name>" _operation="delete"/>`** toe aan het hoofdelement om de toepassing van het filter onder hetzelfde filter in het oorspronkelijke schema te verwijderen.
1. Als u houdt van, kunt u een nieuw filter toevoegen, zoals die in [ worden gedetailleerd de filters van het Systeem ](#system-filters).
