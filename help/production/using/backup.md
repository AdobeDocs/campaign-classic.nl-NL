---
product: campaign
title: Back-up
description: Back-up
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 4b13e310fcee9ba24e83b697fca57bc494505642
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

* Configuratiebestanden, opgeslagen in **nl6/conf** kunt u Adobe Campaign zeer snel opnieuw configureren.

* Bestanden omleiden, opgeslagen in  **nl6/var/`<instance-name>`/redir**, op de trackingservers (vaak &quot;frontal&quot; genoemd) staan en alle eerdere instructies voor de campagne bevatten. Ze worden nog steeds gebruikt door vorige campagnes.

* Logbestanden, opgeslagen in **nl6/var/`<instance-name>`/log** kan worden gebruikt om problemen op te sporen.

De mappen waarvan een back-up moet worden gemaakt, zijn daarom:

* nl6/conf

* nl6/var/`<instance-name>`/redir (voor elke instantie)

* nl6/var/`<instance-name>`/log (optioneel)

* nl6/var/`<instance-name>`/relay (facultatief)


## Database {#database}

>[!IMPORTANT]
>
>Het is noodzakelijk om een back-up van de database te maken.


Het gegevensbestand bevat alle informatie die in de rijke cliëntconsole van Adobe Campaign wordt getoond, evenals alle lijn-van-bedrijfsgegevens.

Uw hostingbedrijf en met name de databasebeheerders zijn verantwoordelijk voor deze bewerking.
