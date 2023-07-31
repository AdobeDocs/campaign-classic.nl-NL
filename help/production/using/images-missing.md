---
product: campaign
title: Ontbrekende afbeeldingen
description: Ontbrekende afbeeldingen
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 5%

---

# Ontbrekende afbeeldingen{#images-missing}



In de release 17.9 zijn verschillende bestanden (met name pictogrammen) verplaatst.

Voor gehoste klanten heeft dit geen gevolgen. Lees het volgende voor installaties op locatie.

**Apache-gebruikers:**

Er is geen effect voor Apache-gebruikers als zij de meegeleverde **apache_neolane.conf**.

**IIS-gebruikers:**

Voor gebruikers IIS (op Vensters), zullen verscheidene pictogrammen in de console na de bouwstijlupdate lijken te ontbreken. Er zijn aanvullende IIS-updatestappen vereist:

1. Dubbelklik na de update van de build **iis_neolane_setup.vbs** bevindt zich in de installatiemap van Campagne. Het standaardpad is C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Start de IIS-site opnieuw die door de vorige stap is bijgewerkt.
