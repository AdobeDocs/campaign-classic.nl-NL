---
title: Architectuur
description: Workflows worden afgehandeld door een specifieke module, die op meerdere servers kan worden gestart om de verwerkingsbelasting te delen.
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3a932bc440853151704f1ba1e188fa0af9d4c5cb
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# Architectuur {#architecture}

Workflows worden afgehandeld door een specifieke module. Deze module kan op meerdere servers worden gestart om de verwerkingsbelasting te delen.

![](assets/architecture.png)

* Het runwf-proces (Workflow Instance Runner) voert alle taken van een bepaalde workflowinstantie uit. Wanneer er geen uit te voeren taken voorlopig zijn, wordt het &quot;passief&quot;, d.w.z. het bewaart zijn status in het gegevensbestand, dan houdt op.
* De wfserver-module (Workflow Server) bewaakt de huidige workflowinstanties. Als er een taak moet worden uitgevoerd, maakt deze module een proces om de bijbehorende instantie te activeren (of opnieuw te activeren).

