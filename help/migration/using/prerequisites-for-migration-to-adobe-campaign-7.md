---
title: Vereisten voor migratie naar Adobe-campagne 7
seo-title: Vereisten voor migratie naar Adobe-campagne 7
description: Vereisten voor migratie naar Adobe-campagne 7
seo-description: null
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f460c79a763c6a207656c54351a4c685f2a78a03

---


# Vereisten voor migratie naar Adobe-campagne 7{#prerequisites-for-migration-to-adobe-campaign}

Voordat u een migratie uitvoert, raadpleegt u de secties [Voordat u de migratie](../../migration/using/before-starting-migration.md) start en uw platform [](../../migration/using/configuring-your-platform.md) configureert.

Bij het migreren van v6.02 naar Adobe Campagne v7 worden sommige bestanden die vooraf zijn geleverd, niet geleverd.

Als er een clientfout optreedt, moet u de dashboards bijwerken met de nieuwe Adobe Campagne v7-code of de volgende bestanden handmatig kopiëren van de versie6.02-instantie naar de v7-instantie:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
