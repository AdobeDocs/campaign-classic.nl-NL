---
title: JSP-gedrag
seo-title: JSP-gedrag
description: JSP-gedrag
seo-description: null
page-status-flag: never-activated
uuid: b9e9f348-968c-46e0-8340-df1f1fcaf3a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 5dcc4090-effe-479e-8d5c-67e6a6542fbb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# JSP-gedrag{#jsp-behavior}

Als bepaalde **jsp** -taken niet met succes worden uitgevoerd, moet u ze dwingen opnieuw te compileren.

Voer hiervoor de volgende opdrachten in:

```
nlserver stop web
cd nl6/tomcat-7
rm -r work/
nlserver start web
```

De **jsp** -taken worden opnieuw gegenereerd wanneer u de volgende keer verbinding maakt.
