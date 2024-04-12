---
product: campaign
title: JSP-gedrag
description: JSP-gedrag
feature: Monitoring
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 14%

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
