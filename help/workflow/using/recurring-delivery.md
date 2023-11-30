---
product: campaign
title: Terugkerende levering
description: Meer informatie over de activiteit van de workflow Terugkerende levering
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Workflows
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: 198921813ff097db0d4ba0a8203fef65bb591af7
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 12%

---

# Terugkerende levering{#recurring-delivery}

A **[!UICONTROL Recurring delivery]** De activiteit laat u een voorkomen van het leveringsmalplaatje vormen die voor een campagne specifiek is.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#recurring-delivery-video)

Deze activiteit is alleen beschikbaar via de **[!UICONTROL Targeting and workflows]** wordt gevonden in een campagne.

Dit doet u als volgt:

1. Selecteer de leveringssjabloon waarop de activiteit wordt gebaseerd.

   ![](assets/recurring_delivery_001.png)

1. Vorm het leveringsmalplaatje.

Het configuratieproces voor deze activiteit is gelijkaardig aan dat van het creëren van een leveringsmalplaatje in termen van de beschikbare opties. Raadpleeg deze [sectie](../../delivery/using/about-templates.md) voor meer informatie.

>[!CAUTION]
>
>Terugkerende leveringen ondersteunen het verzenden van proefdrukken, waaronder [doelgegevens](../../workflow/using/data-life-cycle.md#target-data) personalisatie-elementen.

Raadpleeg dit voor een voorbeeld van deze activiteit die wordt gebruikt [sectie](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Hoe te opstelling terugkomende levering {#set-up-recurring-delivery}

A **terugkerende levering** wordt elke keer dat het wordt uitgevoerd, een nieuwe leveringsinstantie gemaakt. Als de workflow bijvoorbeeld eenmaal per week wordt uitgevoerd, levert dat na één jaar 52 leveringen op. Dit betekent ook dat het brede logboek en het volgen logboeken door elke leveringsinstantie zullen worden gescheiden.

![Terugkerende levering](assets/delivery_recurring.jpg)

Als u een terugkerende levering wilt tegenhouden van het lopen, zou u de campagne volledig moeten annuleren of de werkschema ophouden uitvoerend het. Als de levering vanaf het campagnemdashboard wordt gestopt, wordt de levering alleen gestopt: de volgende exemplaren van de terugkerende levering blijven bij elke workflowuitvoering worden gemaakt.

>[!NOTE]
>
>Het is niet mogelijk een bewijs van een **[!UICONTROL Recurring delivery]** type activiteit.
> 
>Om een levering via een campagnewerkschema direct tot stand te brengen, gebruik de kanaal specifieke activiteiten die (b.v. **[!UICONTROL Recurring delivery]**).

## Video over zelfstudie {#recurring-delivery-video}

Deze video verklaart hoe te om een terugkomende levering en een planneractiviteit te vormen.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

Er zijn aanvullende Campaign Classic-to-video&#39;s beschikbaar [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
