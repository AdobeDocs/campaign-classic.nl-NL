---
product: campaign
title: Samenvoeging bijwerken
description: Meer informatie over de workflowactiviteit voor het bijwerken van aggregaten
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 3%

---

# Samenvoeging bijwerken{#update-aggregate}



Voor rapportagedoeleinden worden aggregaten op kubueniveau gedefinieerd. A **[!UICONTROL Workflow]** is beschikbaar wanneer het vormen van een aggregaat.

Samengevoegde gegevens zijn handig wanneer u grote hoeveelheden gegevens bewerkt. Ze worden automatisch bijgewerkt op basis van de instellingen die in het specifieke werkstroomvak zijn gedefinieerd, zodat de gegevens die het laatst zijn verzameld, worden geïntegreerd in de indicatoren

De aggregaten worden bepaald in het relevante lusje van elke kubus.

![](assets/s_advuser_cube_agregate_01.png)


De **[!UICONTROL Update aggregate]** Met activiteit kunt u de updatemodus selecteren die u wilt toepassen: volledig of gedeeltelijk.

Standaard wordt bij elke berekening een volledige update uitgevoerd. Als u een gedeeltelijke update wilt inschakelen, selecteert u de desbetreffende optie en definieert u de updatevoorwaarden.

![](assets/s_advuser_cube_agregate_05.png)

**Goede praktijken**: a **[!UICONTROL Scheduler]** de activiteit kan worden gebruikt om de frequentie van de berekening - updates te specificeren.

![](assets/s_advuser_cube_agregate_04.png)
