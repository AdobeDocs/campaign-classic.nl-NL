---
solution: Campaign Classic
product: campaign
title: Gebeurtenissen leegmaken
description: Gebeurtenissen leegmaken
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 6%

---


# Gebeurtenissen leegmaken{#purging-events}

Met de [implementatiewizard](../../production/using/database-cleanup-workflow.md#deployment-wizard) kunt u configureren hoe lang de gegevens in de database moeten worden opgeslagen.

Gebeurtenissen worden automatisch gewist door de [workflow voor het opschonen van databases](../../production/using/database-cleanup-workflow.md). Dit werkschema zuiveert de gebeurtenissen die op de uitvoeringsinstanties en de gebeurtenissen worden ontvangen en worden opgeslagen die op een controleinstantie worden gearchiveerd.

Gebruik de pijlen naar wens om de instellingen voor leegmaken te wijzigen.

Instellingen voor het opschonen van gebeurtenissen op een besturingsinstantie:

![](assets/messagecenter_delete_events_001.png)

Instellingen voor het opschonen van gebeurtenissen op een uitvoeringsinstantie:

![](assets/messagecenter_delete_events_002.png)

Raadpleeg [deze sectie](../../production/using/database-cleanup-workflow.md) voor meer informatie over de workflow voor het opschonen van databases.
