---
title: Ontbrekende afbeeldingen
seo-title: Ontbrekende afbeeldingen
description: Ontbrekende afbeeldingen
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
translation-type: tm+mt
source-git-commit: d509dc584cd4ae17c6dda85c09fceee8c6162dba
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 7%

---


# Ontbrekende afbeeldingen{#images-missing}

In de release 17.9 zijn verschillende bestanden (met name pictogrammen) verplaatst.

Voor gehoste klanten heeft dit geen gevolgen. Lees het volgende voor installaties op locatie.

**Apache-gebruikers:**

Er is geen effect voor Apache-gebruikers als ze de meegeleverde **apache_neolane.conf gebruiken**

**IIS-gebruikers:**

Voor gebruikers IIS (op Vensters), zullen verscheidene pictogrammen in de console na de bouwstijlupdate lijken te ontbreken. Er zijn aanvullende IIS-updatestappen vereist:

1. Na de bouwstijlupdate, klik op **is_neolane_setup.vbs** in de de installatiemap van de Campagne tweemaal. Het standaardpad is C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Start de IIS-site opnieuw die door de vorige stap is bijgewerkt.

