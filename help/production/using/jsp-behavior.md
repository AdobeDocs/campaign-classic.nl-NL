---
product: campaign
title: JSP-gedrag
description: JSP-gedrag
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# JSP-gedrag{#jsp-behavior}



Als bepaalde **jsp** taken worden niet uitgevoerd. U moet ze dwingen opnieuw te compileren.

Voer hiervoor de volgende opdrachten in:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

De **jsp** de taken worden opnieuw gegenereerd wanneer u de volgende keer verbinding maakt.
