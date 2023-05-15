---
product: campaign
title: Problemen met het bijhouden van logboeken
description: Problemen met het bijhouden van logboeken
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# Problemen met het bijhouden van logboeken{#tracking-logs-issues}



Er kunnen veelvoudige redenen voor het volgen van logboeken zijn niet door:sturen. We raden u aan de volgende gegevens te controleren:

* **doet het** Tekstspatiëring **bevat de workflow fouten?**

   Zie [Technische workflows controleren](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **Is de module** trackinglogd **op de server wordt uitgevoerd?**

   Zie [Logbestanden](../../production/using/log-files.md).

* **Zijn er wijzigingen aangebracht?**

   Zij kunnen een verlies van verbinding aan de servers teweegbrengen gebruikend de volgende alias.
