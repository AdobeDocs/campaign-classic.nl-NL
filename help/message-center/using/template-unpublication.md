---
title: Sjabloonpublicatie
seo-title: Sjabloonpublicatie
description: Sjabloonpublicatie
seo-description: null
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 71aeeda3edafc64dbe696ce6f344b8b0ccdc43d1
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# Onpublicatie sjabloon{#template-unpublication}

Zodra een berichtmalplaatje op de uitvoeringsinstanties wordt gepubliceerd, kan het unpublished.

Een gepubliceerde sjabloon kan zelfs nog steeds worden aangeroepen. Daarom als u niet meer een berichtmalplaatje gebruikt, wordt het geadviseerd om het unpublish. Dit om te voorkomen dat er per ongeluk een ongewenste transactiemelding wordt verzonden. U hebt bijvoorbeeld een berichtsjabloon gepubliceerd die u alleen gebruikt voor kerstcampagnes. Misschien wilt u de publicatie ongedaan maken nadat de kerstperiode is afgelopen en deze volgend jaar opnieuw publiceren.

U kunt ook geen transactiemalplaatje verwijderen dat de **[!UICONTROL Published]** status heeft. U moet eerst de publicatie ongedaan maken.

Volg onderstaande stappen om de publicatie van een transactiemalplaatje ongedaan te maken.

1. Ga in de besturingsinstantie naar de **[!UICONTROL Message Center > Transactional message templates]** map van de boomstructuur.
1. Selecteer de sjabloon die u wilt verwijderen.
1. Klik op **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Klik op **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

De status van de transactiemeldsjabloon verandert van **[!UICONTROL Published]** naar **[!UICONTROL Being edited]**.

Zodra de publicatie is voltooid:

* Beide berichtmalplaatjes (die op partij en real-time typegebeurtenissen worden toegepast) worden geschrapt van elke uitvoeringsinstantie. Ze worden niet meer in de **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** map weergegeven.

* Zodra een malplaatje unpublished is, kunt u het van de controleinstantie indien nodig schrappen. U doet dit door het in de lijst te selecteren en op de **[!UICONTROL Delete]** knop rechtsboven in het scherm te klikken.