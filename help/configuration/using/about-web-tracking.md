---
solution: Campaign Classic
product: campaign
title: Webtracering
description: Webtracering
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---


# Webtracering{#about-web-tracking}

Naast de standaardtracering die het gedrag van een internetgebruiker die op een koppeling in een e-mailbericht klikt, toont, kunt u met het Adobe Campaign-platform informatie verzamelen over hoe internetgebruikers door uw website bladeren. Deze gegevensverzameling wordt uitgevoerd door de module Webtracering.

Wanneer een internetgebruiker op een bijgehouden koppeling in een e-mail van een bepaalde levering klikt, slaat de omleidingsserver contact op met een sessiecookie die de identificatie voor de uitzending (broadlogId) en de identificatie voor de levering (deliveryId) bevat.

De webclient verzendt dit cookie vervolgens naar de server wanneer de gebruiker een pagina bezoekt met een tag voor webtracering. Dit gaat tijdens de hele sessie door, dus totdat de webclient wordt gesloten.

De omleidingsserver verzamelt op deze manier de volgende gegevens:

* URL van de weergegeven pagina via een id die als parameter is verzonden,
* de levering vanaf welke de webpagina is bezocht, via het sessiecookie;
* id van de internetgebruiker die via het sessiecookie heeft geklikt;
* aanvullende informatie zoals het gegenereerde bedrijfsvolume.

Het volgende diagram toont de stadia van de dialoog tussen de cliënt en de diverse servers.

![](assets/d_ncs_integration_webtracking_structure1.png)

