---
solution: Campaign Classic
product: campaign
title: Sjabloonpublicatie
description: Sjabloonpublicatie
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 3%

---


# Publicatie van sjabloon ongedaan maken{#template-unpublication}

Zodra een berichtmalplaatje op de uitvoeringsinstanties wordt gepubliceerd, kan het unpublished. Zie [deze sectie](../../message-center/using/template-publication.md) voor meer informatie over het publicatieproces van sjablonen.

* Een gepubliceerde sjabloon kan zelfs nog steeds worden opgeroepen als de overeenkomstige gebeurtenis wordt geactiveerd: Als u geen berichtmalplaatje meer gebruikt, wordt het geadviseerd om het unpublish. Dit om te voorkomen dat er per ongeluk een ongewenste transactiemelding wordt verzonden.

   U hebt bijvoorbeeld een berichtsjabloon gepubliceerd die u alleen gebruikt voor kerstcampagnes. Misschien wilt u de publicatie ongedaan maken nadat de kerstperiode is afgelopen en deze volgend jaar opnieuw publiceren.

* U kunt ook geen transactiemalplaatje verwijderen dat de status **[!UICONTROL Published]** heeft. U moet eerst de publicatie ongedaan maken.

>[!NOTE]
>
>Deze mogelijkheid is beschikbaar vanaf de release van Campagne 20.2.

Volg onderstaande stappen om de publicatie van een transactiemalplaatje ongedaan te maken.

1. Ga voor de besturingsinstantie naar de map **[!UICONTROL Message Center > Transactional message templates]** van de boomstructuur.
1. Selecteer de sjabloon die u wilt verwijderen.
1. Klik op **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Klik op **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

De status van de transactioneleberichtsjabloon verandert weer van **[!UICONTROL Published]** in **[!UICONTROL Being edited]**.

Zodra de publicatie is voltooid:

* Beide berichtmalplaatjes (die op partij en real-time typegebeurtenissen worden toegepast) worden geschrapt van elke uitvoeringsinstantie.

   Zij verschijnen niet meer in **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** omslag (zie [deze sectie](../../message-center/using/template-publication.md)).

* Zodra een malplaatje unpublished is, kunt u het van de controleinstantie schrappen.

   Selecteer dit in de lijst en klik op de knop **[!UICONTROL Delete]** rechtsboven in het scherm.