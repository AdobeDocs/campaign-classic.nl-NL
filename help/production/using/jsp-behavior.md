---
solution: Campaign Classic
product: campaign
title: JSP-gedrag
description: JSP-gedrag
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---


# JSP-gedrag{#jsp-behavior}

Als bepaalde **jsp** taken niet met succes worden uitgevoerd, moet u hen dwingen opnieuw te compileren.

Voer hiervoor de volgende opdrachten in:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

De **jsp** banen worden opnieuw geproduceerd de volgende tijd u verbindt.
