---
product: campaign
title: Architectuur
description: Workflows worden afgehandeld door een specifieke module, die kan worden gestart op meerdere servers om de belasting van de verwerking te delen
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Workflows
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 7%

---

# Architectuur {#architecture}



Workflows worden afgehandeld door een specifieke module. Deze module kan op meerdere servers worden gestart om de verwerkingsbelasting te delen.

![](assets/architecture.png)

* Het runwf-proces (Workflow Instance Runner) voert alle taken van een bepaalde workflowinstantie uit. Wanneer er geen uit te voeren taken voorlopig zijn, wordt het &quot;passief&quot;, dat wil zeggen het bewaart zijn status in het gegevensbestand, dan houdt op.
* De wfserver-module (Workflow Server) bewaakt de huidige workflowinstanties. Als er een taak moet worden uitgevoerd, maakt deze module een proces om de bijbehorende instantie te activeren (of opnieuw te activeren).
