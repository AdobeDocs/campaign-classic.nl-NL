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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Inleiding{#introduction}

In deze sectie wordt de procedure beschreven die moet worden toegepast om Adobe Campagne, client- en serverzijde bij te werken en wordt de overstap van een bestaande instantie naar Unicode beschreven.

>[!NOTE]
>
>Voor gehoste instanties moet u coördineren met uw Adobe-beheerder.\
>Voor on-premise gevallen, kunt u hulp van de Adviseurs van Adobe krijgen.

De upgrade moet worden toegepast op alle servers waarop Adobe Campaign is geïnstalleerd.

1. Migreer de omleiding en het volgen servers (Apache/IIS).
1. Migreer de Power Booster/Cluster-servers.
1. Migreer de marketingserver.

De campagne van Adobe is gebaseerd op verscheidene processen die op de server worden uitgevoerd die u tijdens updates zult moeten manipuleren, in het bijzonder:

* Toepassingsserver (extern web)
* Leveringsserver (nlserver mta)
* Redirection-server (webmdl)

>[!NOTE]
>
>Raadpleeg [deze sectie](../../installation/using/general-architecture.md#logical-application-layer)voor meer informatie over de verschillende Adobe-campagneprocessen.\
>Wanneer u de architectuur van het type Power Booster of Power Cluster gebruikt, moet u dit proces toepassen op alle Power Booster-/Cluster-servers.

Als de nieuwe versie een wijziging van de gegevensbestandstructuur impliceert, adviseren wij opnieuw beginnend de servers in de volgende orde:

1. Toepassingsserver (internet op de server),
1. Redirection server (webmdl),
1. Leveringsserver (nlserver mta).

