---
solution: Campaign Classic
product: campaign
title: Een schema uitbreiden
description: Leer hoe u een schema kunt uitbreiden
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---


# Een schema uitbreiden{#extending-a-schema}

>[!IMPORTANT]
>
>Sommige ingebouwde schema&#39;s mogen niet worden uitgebreid: voornamelijk die waarvoor de volgende instellingen zijn gedefinieerd:\
>**dataSource=&quot;file&quot;** en **mappingType=&quot;xmlFile&quot;**.\
>De volgende schema&#39;s mogen niet worden uitgebreid: **xtk:entiteitBackupNew**, **xtk:entiteitBackupOriginal**, **xtk:entiteitOriginal**, **xtk:form**, **xtk:srcSchema**, ******************************************ncm:publishing, nl:controle,nms:agendaonderRingNms:remoteTracking,nms:userAgentRules, xtk:builder, xtk:connections, xtk:dbInit, xtk:funcList,xtk:fusionxtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, ****************xtk:scriptContext, xtk:sessionxtk:sqlSchemaxtk:strings.
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
>Voor de wijzigingen die in aanmerking moeten worden genomen, moet u schema&#39;s opnieuw genereren. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.\
>Als de wijzigingen van invloed zijn op de structuur van de database, moet u een update uitvoeren. Raadpleeg de sectie [De databasestructuur bijwerken](../../configuration/using/updating-the-database-structure.md) voor meer informatie.

