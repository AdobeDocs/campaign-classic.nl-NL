---
solution: Campaign Classic
product: campaign
title: Ontbrekende afbeeldingen
description: Ontbrekende afbeeldingen
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---


# Ontbrekende afbeeldingen{#images-missing}

In de release 17.9 zijn verschillende bestanden (met name pictogrammen) verplaatst.

Voor gehoste klanten heeft dit geen gevolgen. Lees het volgende voor installaties op locatie.

**Apache-gebruikers:**

Er is geen effect voor Apache-gebruikers als ze de meegeleverde **apache_neolane.conf** gebruiken.

**IIS-gebruikers:**

Voor gebruikers IIS (op Vensters), zullen verscheidene pictogrammen in de console na de bouwstijlupdate lijken te ontbreken. Er zijn aanvullende IIS-updatestappen vereist:

1. Na de bouwstijlupdate, klik **is_neolane_setup.vbs** in de de installatiemap van de Campagne tweemaal. Het standaardpad is C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Start de IIS-site opnieuw die door de vorige stap is bijgewerkt.
