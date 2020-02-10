---
title: Samenvoegen bijwerken
seo-title: Samenvoegen bijwerken
description: Samenvoegen bijwerken
seo-description: null
page-status-flag: never-activated
uuid: 34ae42e1-da34-43be-b219-0b3b872177b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 031f8d5d-940c-4a4c-97e7-ad4ef61983c1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Samenvoegen bijwerken{#update-aggregate}

Voor rapportagedoeleinden worden aggregaten op kubueniveau gedefinieerd. Er is een **[!UICONTROL Workflow]** tabblad beschikbaar wanneer u een aggregaat configureert.

Raadpleeg de desbetreffende [sectie](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates)voor meer informatie over kubussen en het gebruik van aggregaten in Adobe Campagne.

Met de **[!UICONTROL Update aggregate]** activiteit kunt u de updatemodus selecteren die u wilt toepassen: volledig of gedeeltelijk.

Standaard wordt bij elke berekening een volledige update uitgevoerd. Als u een gedeeltelijke update wilt inschakelen, selecteert u de desbetreffende optie en definieert u de updatevoorwaarden.

![](assets/s_advuser_cube_agregate_05.png)

**Goede praktijken**: een **[!UICONTROL Scheduler]** activiteit kan worden gebruikt om de frequentie van de actualiseringen van de berekeningen te specificeren.

![](assets/s_advuser_cube_agregate_04.png)

