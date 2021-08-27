---
product: campaign
title: JSP-gedrag
description: JSP-gedrag
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# JSP-gedrag{#jsp-behavior}

![](../../assets/v7-only.svg)

Als bepaalde **jsp** taken niet met succes worden uitgevoerd, moet u hen dwingen opnieuw te compileren.

Voer hiervoor de volgende opdrachten in:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

De **jsp** banen worden opnieuw geproduceerd de volgende tijd u verbindt.
