---
product: campaign
title: Architectuur
description: Workflows worden afgehandeld door een specifieke module, die kan worden gestart op meerdere servers om de belasting van de verwerking te delen
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---

# Architectuur {#architecture}



Workflows worden afgehandeld door een specifieke module. Deze module kan op meerdere servers worden gestart om de verwerkingsbelasting te delen.

![](assets/architecture.png)

* Het runwf-proces (Workflow Instance Runner) voert alle taken van een bepaalde workflowinstantie uit. Wanneer er geen uit te voeren taken voorlopig zijn, wordt het &quot;passief&quot;, dat wil zeggen het bewaart zijn status in het gegevensbestand, dan houdt op.
* De wfserver-module (Workflow Server) bewaakt de huidige workflowinstanties. Als er een taak moet worden uitgevoerd, maakt deze module een proces om de bijbehorende instantie te activeren (of opnieuw te activeren).
