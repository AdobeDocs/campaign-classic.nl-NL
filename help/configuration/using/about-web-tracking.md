---
product: campaign
title: Webtracking
feature: Configuration, Instance Settings
description: Webtracking
role: User, Data Engineer, Developer
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# Webtracking{#about-web-tracking}

Naast de standaardtracering die het gedrag van een internetgebruiker die op een koppeling in een e-mailbericht klikt, toont, kunt u met het Adobe Campaign-platform informatie verzamelen over hoe internetgebruikers door uw website bladeren. Deze gegevensverzameling wordt uitgevoerd door de module voor webtracering.

Wanneer een internetgebruiker op een bijgehouden koppeling in een e-mailbericht van een bepaalde levering klikt, slaat de omleidingsserver contact op met een sessiecookie met de identificatie voor de uitzending (broadlogId) en de identificatie voor de levering (deliveryId).

De webclient verzendt dit cookie vervolgens naar de server wanneer de gebruiker een pagina bezoekt met een tag voor webtracering. Dit gaat tijdens de hele sessie door, dus totdat de webclient wordt gesloten.

De omleidingsserver verzamelt op deze manier de volgende gegevens:

* URL van de weergegeven pagina via een id die als parameter is verzonden,
* de levering vanaf welke de webpagina is bezocht, via het sessiecookie;
* id van de internetgebruiker die via het sessiecookie heeft geklikt;
* aanvullende informatie zoals het gegenereerde bedrijfsvolume.

Het volgende diagram toont de stadia van de dialoog tussen de cliënt en de diverse servers.

![](assets/d_ncs_integration_webtracking_structure1.png)
