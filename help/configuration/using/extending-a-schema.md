---
title: Een schema uitbreiden
seo-title: Een schema uitbreiden
description: Een schema uitbreiden
seo-description: null
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Een schema uitbreiden{#extending-a-schema}

>[!IMPORTANT]
>
>Sommige ingebouwde schema&#39;s mogen niet worden uitgebreid: voornamelijk die waarvoor de volgende instellingen zijn gedefinieerd:\
>**dataSource=&quot;file&quot;** en **mappingType=&quot;xmlFile&quot;**.\
>De volgende schema&#39;s mogen niet worden uitgebreid: **xtk:entiteitBackupNew**, **xtk:entiteitBackupOriginal**, **xtk:entiteitOriginal**, **xtk:form**, **xtk:srcSchema********************************************, ncm:publishing, nl:monitoring, nms:agendaRookschemanms:remoteTracms king, nms:userAgentRules, xtk:builder, xtk:connectionsxtk:dbInit,xtk:funcList,xtk:fusion,xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, ****************xtk:scriptContext, xtk:sessionxtk:sqlSchemaxtk:strings.
>Deze lijst is niet limitatief.

Er zijn twee methoden om een bestaand schema uit te breiden:

1. Het bronschema rechtstreeks wijzigen.
1. Een ander schema maken met dezelfde naam, maar met een andere naamruimte. Het voordeel is dat u een tabel kunt uitbreiden zonder het oorspronkelijke schema te hoeven wijzigen.

   Het wortelelement van het schema moet de **extendedSchema** attributen met de naam van het uit te breiden schema als zijn waarde bevatten.

   Een extensieschema heeft geen eigen schema: het schema dat met het bronschema wordt gegenereerd, wordt ingevuld met de velden van het extensieschema.

   >[!IMPORTANT]
   >
   >U kunt de ingebouwde schema&#39;s van de toepassing niet wijzigen, maar eerder het mechanisme van de schemauitbreiding. Anders worden gewijzigde schema&#39;s niet bijgewerkt op het moment van toekomstige upgrades van de toepassing. Dit kan leiden tot storingen in het gebruik van Adobe Campaign.

   **Voorbeeld**: extensie van het **nms:ontvangerschema** .

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   De **nms:ontvanger** uitgebreid schema wordt ingevuld met het gebied dat in het uitbreidingsschema wordt bevolkt:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   Het **attribuut AfhankelijkSchemas** op het wortelelement van het schema verwijzingen de gebiedsdelen op de uitbreidingsschema&#39;s.

   Het **kenmerk** memberToop het veld vult het schema in waarin het wordt gedeclareerd.

>[!IMPORTANT]
>
>Voor de wijzigingen die in aanmerking moeten worden genomen, moet u schema&#39;s opnieuw genereren. Raadpleeg voor meer informatie de sectie [Regenererende schema&#39;s](../../configuration/using/regenerating-schemas.md) .\
>Als de wijzigingen van invloed zijn op de structuur van de database, moet u een update uitvoeren. Raadpleeg voor meer informatie de sectie [De databasestructuur](../../configuration/using/updating-the-database-structure.md) bijwerken.

