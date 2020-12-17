---
solution: Campaign Classic
product: campaign
title: Inleiding
description: Inleiding
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 5b35d2ffdd0f591e2fe31dc98a54be9ea0c0c18d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 1%

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

>[!CAUTION]
>
>De cliëntconsole zou op de zelfde bouwstijl moeten zijn zoals de serverinstantie.

>[!NOTE]
>
>Raadpleeg [deze sectie](../../installation/using/general-architecture.md#logical-application-layer) voor meer informatie over de verschillende Adobe Campaign-processen.\
>Wanneer u de architectuur van het type Power Booster of Power Cluster gebruikt, moet u dit proces toepassen op alle Power Booster-/Cluster-servers.

Als de nieuwe versie een wijziging van de gegevensbestandstructuur impliceert, adviseren wij opnieuw beginnend de servers in de volgende orde:

1. Toepassingsserver (internet op de server),
1. Redirection server (webmdl),
1. Leveringsserver (nlserver mta).

