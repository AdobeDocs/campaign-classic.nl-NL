---
solution: Campaign Classic
product: campaign
title: Recycling van gebeurtenissen
description: Recycling van gebeurtenissen
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Recycling van gebeurtenissen{#event-recycling}

Als de levering van een bericht op een specifiek kanaal mislukt, kan Adobe Campaign het bericht opnieuw verzenden via een ander kanaal. Als een levering op het SMS-kanaal bijvoorbeeld mislukt, wordt het bericht opnieuw verzonden via het e-mailkanaal.

Hiervoor moet u een workflow configureren die alle gebeurtenissen opnieuw maakt met de status **Leveringsfout** en er een ander kanaal aan toewijst.

>[!CAUTION]
>
>Deze stap kan alleen worden uitgevoerd met behulp van een workflow en is daarom voorbehouden aan professionele gebruikers. Neem voor meer informatie contact op met het accountmanager van Adobe.

