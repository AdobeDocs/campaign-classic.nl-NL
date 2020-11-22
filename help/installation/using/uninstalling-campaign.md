---
solution: Campaign Classic
product: campaign
title: Installatie van Campaign verwijderen
description: Leer hoe u campagne kunt verwijderen
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 13%

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

Refer to this [page](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Vergeet niet de installatiemap van de Campagne te verwijderen.
