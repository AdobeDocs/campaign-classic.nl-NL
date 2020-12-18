---
solution: Campaign Classic
product: campaign
title: Vereisten voor migratie naar Adobe Campaign 7
description: Vereisten voor migratie naar Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---


# Vereisten voor migratie naar Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Voordat u een migratie uitvoert, raadpleegt u de secties [Voordat u de migratie start](../../migration/using/before-starting-migration.md) en [Uw platform configureren](../../migration/using/configuring-your-platform.md).

Bij het migreren van v6.02 naar Adobe Campaign v7 worden sommige bestanden die vooraf zijn geleverd, niet geleverd.

Als er een clientfout optreedt, moet u de dashboards bijwerken met de nieuwe Adobe Campaign v7-code of de volgende bestanden handmatig kopiëren van de versie 6.02-instantie naar de v7-instantie:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
