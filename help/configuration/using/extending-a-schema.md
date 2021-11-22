---
product: campaign
title: Een schema uitbreiden
description: Leer hoe u een schema kunt uitbreiden
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---

# Een schema uitbreiden{#extending-a-schema}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
>Sommige ingebouwde schema&#39;s mogen niet worden uitgebreid: voornamelijk die waarvoor de volgende instellingen zijn gedefinieerd:\
>**dataSource=&quot;file&quot;** en **mappingType=&quot;xmlFile&quot;**.\
>De volgende schema&#39;s mogen niet worden uitgebreid: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publiceren**, **nl:controleren**, **nms:kalender**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk:verbindingen**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusie**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:sessie**, **xtk:sqlSchema**, **xtk:tekenreeksen**.
>Deze lijst is niet limitatief.

Er zijn twee methoden om een bestaand schema uit te breiden:

1. Het bronschema rechtstreeks wijzigen.
1. Een ander schema maken met dezelfde naam, maar met een andere naamruimte. Het voordeel is dat u een tabel kunt uitbreiden zonder het oorspronkelijke schema te hoeven wijzigen.

   Het hoofdelement van het schema moet het volgende bevatten: **extendedSchema** kenmerk met de naam van het schema dat als waarde moet worden uitgebreid.

   Een extensieschema heeft geen eigen schema: het schema dat met het bronschema wordt gegenereerd, wordt ingevuld met de velden van het extensieschema.

   >[!IMPORTANT]
   >
   >U kunt de ingebouwde schema&#39;s van de toepassing niet wijzigen, maar eerder het mechanisme van de schemauitbreiding. Anders worden gewijzigde schema&#39;s niet bijgewerkt op het moment van toekomstige upgrades van de toepassing. Dit kan leiden tot storingen in het gebruik van Adobe Campaign.

   **Voorbeeld**: verlenging van de **nms:ontvanger** schema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   De **nms:ontvanger** Het uitgebreide schema wordt ingevuld met het veld dat is ingevuld in het extensieschema:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   De **afhankelijkSchemas** kenmerk op het hoofdelement van het schema verwijst naar de afhankelijkheden van de extensieschema&#39;s.

   De **behoortTo** kenmerk op het veld vult het schema in waarin het wordt gedeclareerd.

>[!IMPORTANT]
>
>Voor de wijzigingen die in aanmerking moeten worden genomen, moet u schema&#39;s opnieuw genereren. Raadpleeg voor meer informatie de [Regeneratieschema&#39;s](../../configuration/using/regenerating-schemas.md) sectie.\
>Als de wijzigingen van invloed zijn op de structuur van de database, moet u een update uitvoeren. Raadpleeg de sectie [De databasestructuur bijwerken](../../configuration/using/updating-the-database-structure.md) voor meer informatie.
