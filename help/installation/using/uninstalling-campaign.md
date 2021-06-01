---
product: campaign
title: Installatie van Campaign verwijderen
description: Leer hoe u campagne kunt verwijderen
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 19%

---

# Installatie van Campaign verwijderen{#uninstalling-campaign}

>[!CAUTION]
>
>Deze procedures verwijderen Adobe Campaign permanent. Alle gegevens gaan verloren.

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows:**

Zie deze [pagina](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Vergeet niet de installatiemap van de Campagne te verwijderen.
