---
solution: Campaign Classic
product: campaign
title: Terugkerende levering
description: Meer informatie over de activiteit van de workflow Terugkerende levering
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 7%

---


# Terugkerende levering{#recurring-delivery}

Een **[!UICONTROL Recurring delivery]** activiteit laat u een voorkomen van het leveringsmalplaatje vormen die voor een campagne specifiek is.

Deze activiteit is slechts beschikbaar van het **[!UICONTROL Targeting and workflows]** lusje dat in een campagne wordt gevonden.

Dit doet u als volgt:

1. Selecteer de leveringssjabloon waarop de activiteit wordt gebaseerd.

   ![](assets/recurring_delivery_001.png)

1. Vorm het leveringsmalplaatje.

Het configuratieproces voor deze activiteit is gelijkaardig aan dat van het creëren van een leveringsmalplaatje in termen van de beschikbare opties. Raadpleeg deze [sectie](../../delivery/using/about-templates.md) voor meer informatie.

Zie deze [sectie](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)voor een voorbeeld van deze activiteit die wordt gebruikt.

## Hoe te opstelling terugkomende levering

Elke keer dat een **terugkerende levering** wordt uitgevoerd, wordt een nieuwe leveringsinstantie gemaakt. Als de workflow bijvoorbeeld eenmaal per week wordt uitgevoerd, levert dat na één jaar 52 leveringen op. Dit betekent ook dat het brede logboek en het volgen logboeken door elke leveringsinstantie zullen worden gescheiden.

![Terugkerende aflevering](assets/delivery_recurring.jpg)

Deze video verklaart hoe te om een terugkomende levering en een planneractiviteit te vormen.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

>[!NOTE]
>
>Het is niet mogelijk een bewijs van een **[!UICONTROL Recurring delivery]** type activiteit te verzenden.\
>Om een levering via een campagnewerkschema direct tot stand te brengen, gebruik de kanaal specifieke activiteiten die (b.v. **[!UICONTROL Email delivery]**).
