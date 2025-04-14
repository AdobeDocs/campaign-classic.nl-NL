---
product: campaign
title: Nieuwste release
description: De nieuwste aanvullende informatie voor Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 86bc3bdfe628cc694e47a4670e99225e05b3df1b
workflow-type: ht
source-wordcount: '224'
ht-degree: 100%

---

# Nieuwste release {#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van Campaign Classic v7**. Elke nieuwe build heeft een status die wordt aangegeven door een kleur. Meer informatie over de build-statussen van Campaign Classic v7 vindt u op [deze pagina](rn-overview.md).

## Release 7.4.2 - build 9390 {#release-7-4-2}

[!BADGE Algemene beschikbaarheid]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Algemene beschikbaarheid"}

_2 april 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Beveiligingsverbeteringen {#security-7-4-2}

Deze release bevat verschillende beveiligingsoplossingen.

De verbinding met Adobe-oplossingen en -toepassingen via het **[!UICONTROL Adobe Experience Cloud]** externe account is bijgewerkt om de beveiliging te verbeteren.

### Oplossingen {#release-7-4-2-fixes}

Deze release bevat de volgende belangrijkste oplossingen:

* TLS-/SMPP-verbinding - Problemen opgelost met SMPP-stabiliteit

* Oplossingen voor Google BigQuery:

   * Problemen met regressies van BOOLEAN-gegevenstypen opgelost
   * Problemen met proxy-instellingen opgelost
   * Problemen met regressies van het gegevenstype DATETIME opgelost
   * Problemen met de stabiliteit van bulksgewijs laden opgelost
   * Verbeterde interne tests op ODBC-versies
   * Probleem verholpen met speciale tekens in verbindingstekenreeks
   * Standaardtime-out (5 minuten) voor Google BigQuery-query&#39;s verwijderd

* Mail Transfer Agent (MTA) - Probleem opgelost met een verweesde onderliggende MTA die vast bleef zitten op de status **[!UICONTROL Start pending]**.

De volgende problemen zijn ook opgelost in deze release:

NEO-47269, NEO-59059, NEO-62455, NEO-65774, NEO-66462, NEO-66989, NEO-77898, NEO-78843, NEO-79373, NEO-79598, NEO-80145, NEO-80245, NEO-80434, NEO-80683, NEO-81222, NEO-81433, NEO-81864, NEO-82351, NEO-82781, NEO-82838, NEO-82923, NEO-83252, NEO-83809, NEO-83826, NEO-84024, NEO-84553, NEO-85150

