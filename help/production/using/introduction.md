---
title: Inleiding
seo-title: Inleiding
description: Inleiding
seo-description: null
page-status-flag: never-activated
uuid: 4192a74e-1d4f-4784-80e3-53aaefa9141e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 772992bf-588f-42bd-a72a-986a88815264
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 2%

---


# Inleiding{#introduction}

In deze sectie wordt de procedure beschreven die moet worden toegepast om Adobe Campaign, client en server bij te werken, en wordt de overschakeling naar Unicode van een bestaande instantie beschreven.

>[!NOTE]
>
>Voor gehoste instanties, moet u met uw Beheerder van Adobe coördineren.\
>Voor on-premise gevallen, kunt u hulp van Adobe Consultants krijgen.

De upgrade moet worden toegepast op alle servers waarop Adobe Campaign is geïnstalleerd.

1. Migreer de omleiding en het volgen servers (Apache/IIS).
1. Migreer de Power Booster/Cluster-servers.
1. Migreer de marketingserver.

Adobe Campaign is gebaseerd op verschillende processen die aan de serverzijde worden uitgevoerd en die u tijdens updates moet manipuleren, met name:

* Toepassingsserver (extern web)
* Leveringsserver (nlserver mta)
* Redirection-server (webmdl)

>[!NOTE]
>
>Raadpleeg [deze sectie](../../installation/using/general-architecture.md#logical-application-layer)voor meer informatie over de verschillende Adobe Campaign-processen.\
>Wanneer u de architectuur van het type Power Booster of Power Cluster gebruikt, moet u dit proces toepassen op alle Power Booster-/Cluster-servers.

Als de nieuwe versie een wijziging van de gegevensbestandstructuur impliceert, adviseren wij opnieuw beginnend de servers in de volgende orde:

1. Toepassingsserver (internet op de server),
1. Redirection server (webmdl),
1. Leveringsserver (nlserver mta).

