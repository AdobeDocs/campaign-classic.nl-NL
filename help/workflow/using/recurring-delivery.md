---
product: campaign
title: Terugkerende levering
description: Meer informatie over de activiteit van de workflow Terugkerende levering
feature: Workflows
hide: true
hidefromtoc: true
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 8%

---

# Terugkerende levering{#recurring-delivery}

Met een **[!UICONTROL Recurring delivery]** -activiteit kunt u een exemplaar van een leveringssjabloon configureren dat specifiek is voor een campagne.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#recurring-delivery-video)

Deze activiteit is alleen beschikbaar op het tabblad **[!UICONTROL Targeting and workflows]** dat in een campagne wordt gevonden.

Dit doet u als volgt:

1. Selecteer de leveringssjabloon waarop de activiteit wordt gebaseerd.

   ![](assets/recurring_delivery_001.png)

1. Vorm het leveringsmalplaatje.

Het configuratieproces voor deze activiteit is gelijkaardig aan dat van het creëren van een leveringsmalplaatje in termen van de beschikbare opties. Raadpleeg deze [sectie](../../delivery/using/about-templates.md) voor meer informatie.

>[!CAUTION]
>
>Het terugkeren van leveringen steunt het voorvertonen van inhoud of het verzenden van proeven met inbegrip van [ doelgegevens ](../../workflow/using/data-life-cycle.md#target-data) verpersoonlijkingselementen niet.

Voor een voorbeeld van deze activiteit die wordt gebruikt, verwijs naar deze [ sectie ](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Hoe te opstelling terugkomende levering {#set-up-recurring-delivery}

A **terugkomende levering** zal tot een nieuwe leveringsinstantie leiden telkens als het uitvoert. Als de workflow bijvoorbeeld eenmaal per week wordt uitgevoerd, levert dat na één jaar 52 leveringen op. Dit betekent ook dat het brede logboek en het volgen logboeken door elke leveringsinstantie zullen worden gescheiden.

![Terugkerende levering](assets/delivery_recurring.jpg)

Als u een terugkerende levering wilt tegenhouden van het lopen, zou u de campagne volledig moeten annuleren of de werkschema ophouden uitvoerend het. Als de levering vanaf het campagnemdashboard wordt gestopt, wordt de levering alleen gestopt: de volgende exemplaren van de terugkerende levering blijven bij elke workflowuitvoering worden gemaakt.

>[!NOTE]
>
>Het is niet mogelijk een proef van een **[!UICONTROL Recurring delivery]** type activiteit te verzenden.
> 
>Als u rechtstreeks een levering wilt maken via een campagneworkflow, gebruikt u de kanaalspecifieke activiteiten die vooraf zijn geconfigureerd (bijvoorbeeld **[!UICONTROL Recurring delivery]** ).

## Video over zelfstudie {#recurring-delivery-video}

Deze video verklaart hoe te om een terugkomende levering en een planneractiviteit te vormen.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

De extra hoe te video&#39;s van Campaign Classic zijn beschikbaar [ hier ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
