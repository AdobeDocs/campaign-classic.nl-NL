---
product: campaign
title: Back-up
description: Back-up
feature: Monitoring
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 1%

---

# Back-up{#backup}

Back-up is van essentieel belang om gegevensverlies te voorkomen in geval van een fysiek of systeemgerelateerd probleem op een computer.

Gegevens worden op twee verschillende locaties opgeslagen:

* fysieke bestanden worden opgeslagen in de directory&#39;s van Adobe Campaign;
* andere gegevens worden in de database opgeslagen.

De meeste gegevens bevinden zich in de database. Dit is 99% van de informatie waarvan een back-up moet worden gemaakt.

## Fysieke bestanden {#physical-files}

Bestanden zijn verdeeld in verschillende categorieën:

* De dossiers van de configuratie, die in **nl6/conf** worden opgeslagen, laten u toe om Adobe Campaign zeer snel aan te passen.

* De dossiers van de omleiding, die in **worden opgeslagen nl6/var/`<instance-name>`/redir**, zijn op het volgen (vaak genoemd &quot;frontal&quot;) servers, en omvatten alle vorige campagneomleiding. Ze worden nog steeds gebruikt door vorige campagnes.

* De dossiers van het logboek, die in **worden opgeslagen nl6/var/`<instance-name>`/log**, kunnen worden gebruikt om problemen te vinden.

De mappen waarvan een back-up moet worden gemaakt, zijn daarom:

* nl6/conf

* nl6/var/`<instance-name>`/redir (voor elke instantie)

* nl6/var/`<instance-name>`/log (optioneel)

* nl6/var/`<instance-name>`/relais (optioneel)


## Database {#database}

>[!IMPORTANT]
>
>Het is absoluut noodzakelijk om een back-up van de database te maken.


Het gegevensbestand bevat alle informatie die in de rijke cliëntconsole van Adobe Campaign wordt getoond, evenals alle lijn-van-bedrijfsgegevens.

Uw hostingbedrijf en met name de databasebeheerders zijn verantwoordelijk voor deze bewerking.
