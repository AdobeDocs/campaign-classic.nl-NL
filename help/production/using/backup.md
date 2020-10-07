---
title: Back-up
seo-title: Back-up
description: Back-up
seo-description: null
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---


# Back-up{#backup}

Back-up is van essentieel belang om gegevensverlies te voorkomen in geval van een fysiek of systeemgerelateerd probleem op een computer.

Gegevens worden op twee verschillende locaties opgeslagen:

* fysieke bestanden worden opgeslagen in de mappen van Adobe Campaign;
* andere gegevens worden in de database opgeslagen.

De meeste gegevens bevinden zich in de database. Dit is 99% van de informatie waarvan een back-up moet worden gemaakt.

## Fysieke bestanden {#physical-files}

Bestanden zijn verdeeld in verschillende categorieën:

* Configuratiebestanden in **nl6/conf**

   Hiermee kunt u Adobe Campaign zeer snel opnieuw configureren.

* Bestanden omleiden ** nl6/var/`<instancename>`/redir**

   Dit zijn op het volgen (vaak &quot;frontal&quot;genoemd) servers, en omvat alle vorige campagneomleiding. Ze worden nog steeds gebruikt door vorige campagnes.

* Logbestanden: **nl6/var/`<instancename>`/log**

   Deze kunnen worden gebruikt om problemen te traceren.

De mappen waarvan een back-up moet worden gemaakt, zijn daarom:

* nl6/conf

* nl6/var/`<instanceName>`/redir (voor elke instantie)

* nl6/var/`<instanceName>`/log (optioneel)

* nl6/var/`<instanceName>`/relais (facultatief)

>[!CAUTION]
>
>Het is van essentieel belang een back-up van de database te maken.

## Database {#database}

Het gegevensbestand bevat alle informatie die in de rijke cliëntconsole van Adobe Campaign wordt getoond, evenals alle lijn-van-bedrijfsgegevens.

Uw hostingbedrijf en met name de databasebeheerders zijn verantwoordelijk voor deze bewerking.
