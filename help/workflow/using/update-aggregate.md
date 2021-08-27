---
product: campaign
title: Samenvoeging bijwerken
description: Meer informatie over de activiteit van de geaggregeerde workflow bijwerken
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 4%

---

# Samenvoeging bijwerken{#update-aggregate}

![](../../assets/common.svg)

Voor rapportagedoeleinden worden aggregaten op kubueniveau gedefinieerd. Een **[!UICONTROL Workflow]** lusje is beschikbaar wanneer het vormen van een aggregaat.

Raadpleeg de specifieke [sectie](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates) voor meer informatie over kubussen en het gebruik van aggregaten in Adobe Campaign.

Met de activiteit **[!UICONTROL Update aggregate]** kunt u de updatemodus selecteren die u wilt toepassen: volledig of gedeeltelijk.

Standaard wordt bij elke berekening een volledige update uitgevoerd. Als u een gedeeltelijke update wilt inschakelen, selecteert u de desbetreffende optie en definieert u de updatevoorwaarden.

![](assets/s_advuser_cube_agregate_05.png)

**Goede praktijken**: een  **[!UICONTROL Scheduler]** activiteit kan worden gebruikt om de frequentie van de actualiseringen van de berekeningen te specificeren .

![](assets/s_advuser_cube_agregate_04.png)
