---
solution: Campaign Classic
product: campaign
title: Back-up
description: Back-up
audience: production
content-type: reference
topic-tags: data-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '197'
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

* nl6/var/`<instanceName>`/relais (optioneel)

>[!IMPORTANT]
>
>Het is van essentieel belang een back-up van de database te maken.

## Database {#database}

Het gegevensbestand bevat alle informatie die in de rijke cliëntconsole van Adobe Campaign wordt getoond, evenals alle lijn-van-bedrijfsgegevens.

Uw hostingbedrijf en met name de databasebeheerders zijn verantwoordelijk voor deze bewerking.
