---
product: campaign
title: Vereisten voor migratie naar Adobe Campaign 7
description: Vereisten voor migratie naar Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 747d8a2c-b13a-4852-a9b5-0d37b236a36f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---

# Vereisten voor migratie naar Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

![](../../assets/v7-only.svg)

Voordat u een migratie uitvoert, raadpleegt u de [Voordat u de migratie start](../../migration/using/before-starting-migration.md) en [Uw platform configureren](../../migration/using/configuring-your-platform.md) secties.

Bij het migreren van v6.02 naar Adobe Campaign v7 worden sommige bestanden die vooraf zijn geleverd, niet geleverd.

Als er een clientfout optreedt, moet u uw dashboards bijwerken met de nieuwe Adobe Campaign v7-code of de volgende bestanden handmatig kopiëren van de versie 6.02-instantie naar de v7-instantie:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
