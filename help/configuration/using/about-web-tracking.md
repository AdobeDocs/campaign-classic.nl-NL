---
title: Webtracering
seo-title: Webtracering
description: Webtracering
seo-description: null
page-status-flag: never-activated
uuid: 59d18ffb-c26e-4571-8364-5e85ec587349
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 38ba9be9-dabc-41d4-878c-d772955301fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Webtracering{#about-web-tracking}

Naast de standaardtracering die het gedrag van een internetgebruiker die op een koppeling in een e-mailbericht klikt, toont, kunt u met het Adobe Campagne-platform informatie verzamelen over hoe internetgebruikers door uw website bladeren. Deze gegevensverzameling wordt uitgevoerd door de module Webtracering.

Wanneer een internetgebruiker op een bijgehouden koppeling in een e-mail van een bepaalde levering klikt, slaat de omleidingsserver contact op met een sessiecookie die de identificatie voor de uitzending (broadlogId) en de identificatie voor de levering (deliveryId) bevat.

De webclient verzendt dit cookie vervolgens naar de server wanneer de gebruiker een pagina bezoekt met een tag voor webtracering. Dit gaat tijdens de hele sessie door, dus totdat de webclient wordt gesloten.

De omleidingsserver verzamelt op deze manier de volgende gegevens:

* URL van de weergegeven pagina via een id die als parameter is verzonden,
* de levering vanaf welke de webpagina is bezocht, via het sessiecookie;
* id van de internetgebruiker die via het sessiecookie heeft geklikt;
* aanvullende informatie zoals het gegenereerde bedrijfsvolume.

Het volgende diagram toont de stadia van de dialoog tussen de cliënt en de diverse servers.

![](assets/d_ncs_integration_webtracking_structure1.png)

