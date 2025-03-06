---
product: campaign
title: Samenvoeging bijwerken
description: Meer informatie over de workflowactiviteit voor het bijwerken van aggregaten
feature: Workflows
hide: true
hidefromtoc: true
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 3%

---

# Samenvoeging bijwerken{#update-aggregate}



Voor rapportagedoeleinden worden aggregaten op kubueniveau gedefinieerd. Er is een tabblad **[!UICONTROL Workflow]** beschikbaar wanneer u een aggregaat configureert.

Samengevoegde gegevens zijn handig wanneer u grote hoeveelheden gegevens bewerkt. Ze worden automatisch bijgewerkt op basis van de instellingen die in het specifieke werkstroomvak zijn gedefinieerd, zodat de gegevens die het laatst zijn verzameld, worden geïntegreerd in de indicatoren

De aggregaten worden bepaald in het relevante lusje van elke kubus.

![](assets/s_advuser_cube_agregate_01.png)


Met de **[!UICONTROL Update aggregate]** -activiteit kunt u de updatemodus selecteren die u wilt toepassen: volledig of gedeeltelijk.

Standaard wordt bij elke berekening een volledige update uitgevoerd. Als u een gedeeltelijke update wilt inschakelen, selecteert u de desbetreffende optie en definieert u de updatevoorwaarden.

![](assets/s_advuser_cube_agregate_05.png)

**Goede praktijken**: a **[!UICONTROL Scheduler]** activiteit kan worden gebruikt om de frequentie van berekeningsupdates te specificeren.

![](assets/s_advuser_cube_agregate_04.png)
