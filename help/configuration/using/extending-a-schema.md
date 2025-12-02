---
product: campaign
title: Een schema uitbreiden
description: Leer hoe u een schema kunt uitbreiden
role: Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 5%

---

# Een schema uitbreiden{#extending-a-schema}

>[!IMPORTANT]
>
>Sommige ingebouwde schema&#39;s mogen niet worden uitgebreid, met name die waarvoor de volgende instellingen zijn gedefinieerd:\
>**dataSource= &quot;dossier&quot;** en **mappingType=&quot;xmlFile&quot;**.\
>De volgende schema&#39;s moeten niet worden uitgebreid: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, 6&rbrace; nms **,:remoteTracking** nms **,:userAgentRules** xtk **,:builder** xtk **,:connections** xtk **,:dbInit** xtk **,:funcList** xtk **,:fusion** xtk tk: jst **,** xtk **,:navtree** xtk **,:queryDef** xtk **,:resourceMenu** xtk **,:schema** xtk **,:scriptContext** xtk **,:session** xtk **,:sqlSchema** xtk **.:strings**
>Deze lijst is niet limitatief.

Er zijn twee methoden om een bestaand schema uit te breiden:

1. Het bronschema rechtstreeks wijzigen.
1. Een ander schema maken met dezelfde naam, maar met een andere naamruimte. Het voordeel is dat u een tabel kunt uitbreiden zonder het oorspronkelijke schema te hoeven wijzigen.

   Het wortelelement van het schema moet het **extendedSchema** attribuut met de naam van het uit te breiden schema als zijn waarde bevatten.

   Een extensieschema heeft geen eigen schema: het schema dat met het bronschema wordt gegenereerd, wordt ingevuld met de velden van het extensieschema.

   >[!IMPORTANT]
   >
   >U kunt de ingebouwde schema&#39;s van de toepassing niet wijzigen, maar eerder het mechanisme van de schemauitbreiding. Anders worden gewijzigde schema&#39;s niet bijgewerkt op het moment van toekomstige upgrades van de toepassing. Dit kan leiden tot storingen in het gebruik van Adobe Campaign.

   **Voorbeeld**: uitbreiding van het **nms:recipient** schema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Het **nms:recipient** uitgebreide schema wordt gevuld in met het gebied dat in het uitbreidingsschema wordt bevolkt:

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
>Voor de wijzigingen die in aanmerking moeten worden genomen, moet u schema&#39;s opnieuw genereren. Raadpleeg [deze pagina](../../configuration/using/regenerating-schemas.md) voor meer informatie.\
>Als de wijzigingen van invloed zijn op de structuur van de database, moet u een update uitvoeren. Raadpleeg [deze pagina](../../configuration/using/updating-the-database-structure.md) voor meer informatie.
