---
product: campaign
title: Nieuwste release
description: De nieuwste aanvullende informatie voor Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 631188b5974eaa4cd1bf667c5df9f2ff0f983cf0
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 24%

---

# Nieuwste release {#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van Campaign Classic v7**. Elke nieuwe build heeft een status die wordt aangegeven door een kleur. Meer informatie over de build-statussen van Campaign Classic v7 vindt u op [deze pagina](rn-overview.md).

## Release 7.4.2 - build 9390 {#release-7-4-2}

[!BADGE Beperkte beschikbaarheid]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Beperkte beschikbaarheid"}

_zaterdag 21 maart 2025_

>[!AVAILABILITY]
>
>Deze versie is in **Beperkte Beschikbaarheid** (LA). Het is beperkt tot Gehoste/Beheerde de dienstengebruikers slechts. Deze release is binnenkort beschikbaar voor klanten met hybride en on-premise.

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Beveiligingsverbeteringen {#security-7-4-2}

Deze release wordt geleverd met verschillende beveiligingsoplossingen.

De verbinding met Adobe-oplossingen en -toepassingen via de externe account van **[!UICONTROL Adobe Experience Cloud]** is bijgewerkt om de beveiliging te verbeteren.

### Oplossingen {#release-7-4-2-fixes}

Deze release bevat de volgende hoofdoplossingen:

* TLS-/SMPP-verbinding - Vaste problemen met SMPP-stabiliteit

* Google BigQuery corrigeert:

   * Vaste regressies op BOOLEAN-gegevenstypen
   * Vaste proxyinstellingen
   * Vaste regressies op gegevenstypen DATETIME
   * Vaste stabiliteit van bulklading
   * Verbeterde interne tests op ODBC-versies
   * Probleem verholpen met speciale tekens in verbindingstekenreeks
   * Standaardtime-out (5 minuten) voor Google BigQuery-query-query verwijderd

* Mail Transfer Agent (MTA) - Fixed orphan MTA child to be plakt on **[!UICONTROL Start pending]** status.

De volgende problemen zijn ook opgelost in deze release:

NEO-47269, NEO-59059, NEO-62455, NEO-65774, NEO-66462, NEO-66989, NEO-77898, NEO-788 43, NEO-79373, NEO-79598, NEO-80145, NEO-80245, NEO-80434, NEO-80683, NEO-8122, NEO-8 1433, NEO-81864, NEO-82351, NEO-82781, NEO-82838, NEO-82923, NEO-83252, NEO-83809, O-83826, NEO-84024, NEO-84553, NEO-85150

