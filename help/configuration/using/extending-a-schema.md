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
>**dataSource=&quot;file&quot;** en  **mappingType=&quot;xmlFile&quot;**.\
>De volgende schema&#39;s mogen niet worden uitgebreid: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, &lt;a1 0/>ncm:publishing **,** nl:monitoring **,** nms:agenda **,** nms:remoteTracking **,** nms:userAgentRules 19/>, **xtk:builder**, **xtk:connections**, **xtk:dbInit**, **xtk:funcList&lt;a22 7/>,** xtk:fusion **,** xtk: jst **,** xtk:navtree **,** xtk:queryDef **,** xtk:resourceMenu **,** xtk:schema 39/>, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.********
>Deze lijst is niet limitatief.

Er zijn twee methoden om een bestaand schema uit te breiden:

1. Het bronschema rechtstreeks wijzigen.
1. Een ander schema maken met dezelfde naam, maar met een andere naamruimte. Het voordeel is dat u een tabel kunt uitbreiden zonder het oorspronkelijke schema te hoeven wijzigen.

   Het wortelelement van het schema moet **extendedSchema** attributen met de naam van het uit te breiden schema als zijn waarde bevatten.

   Een extensieschema heeft geen eigen schema: het schema dat met het bronschema wordt gegenereerd, wordt ingevuld met de velden van het extensieschema.

   >[!IMPORTANT]
   >
   >U kunt de ingebouwde schema&#39;s van de toepassing niet wijzigen, maar eerder het mechanisme van de schemauitbreiding. Anders worden gewijzigde schema&#39;s niet bijgewerkt op het moment van toekomstige upgrades van de toepassing. Dit kan leiden tot storingen in het gebruik van Adobe Campaign.

   **Voorbeeld**: extensie van de  **nms:** ontvanentschema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Het uitgebreide schema **nms:ontvanger** is ingevuld met het veld dat is ingevuld in het extensieschema:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   Het **AfhankelijkSchemas** attribuut op het wortelelement van het schema verwijzingen de gebiedsdelen op de uitbreidingsschema&#39;s.

   Het **behoortTo** attribuut op het gebied vult in het schema waar het wordt verklaard.

>[!IMPORTANT]
>
>Voor de wijzigingen die in aanmerking moeten worden genomen, moet u schema&#39;s opnieuw genereren. Raadpleeg voor meer informatie de sectie [Regenererende schema&#39;s](../../configuration/using/regenerating-schemas.md).\
>Als de wijzigingen van invloed zijn op de structuur van de database, moet u een update uitvoeren. Raadpleeg de sectie [De databasestructuur bijwerken](../../configuration/using/updating-the-database-structure.md) voor meer informatie.

