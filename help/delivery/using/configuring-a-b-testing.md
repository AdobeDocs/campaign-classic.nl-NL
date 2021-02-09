---
solution: Campaign Classic
product: campaign
title: A/B-tests configureren
description: Leer hoe u A/B-tests configureert in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 1330d4658d039f27a98535bf9885bffbfa0be3c9
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---


# A/B-tests configureren {#configuring-a-b-testing}

In deze sectie wordt beschreven hoe u een workflow bouwt om A/B-tests uit te voeren.

1. Creeer een nieuw werkschema dan vormen een [Vraag](../../workflow/using/query.md) activiteit om de gewenste bevolking te richten.

1. Voeg een [Gesplitste ](../../workflow/using/split.md) activiteit toe om de doelpopulatie in veelvoudige ondergroepen te verdelen.

1. Open de activiteit, dan vorm elke ondergroep volgens uw behoeften. Voor meer op hoe te om een **[!UICONTROL Split]** activiteit te vormen, verwijs naar deze sectie.

   In dit voorbeeld willen we twee nieuwe onderwerpen testen voor een nieuwsbrief door ze allemaal te presenteren aan 10 procent van de doelgroep.

   ![](assets/ab-testing-split.png)

1. Voeg een overgang toe om de nieuwsbrief met het huidige onderwerp naar de resterende bevolking te sturen. Hiervoor activeert u de optie **[!UICONTROL Generate complement]** op het tabblad **[!UICONTROL General]**.

   ![](assets/ab-testing-complement.png)

1. Voeg voor elke subset de versie van de levering toe die u wilt testen.

   ![](assets/ab-testing-delivery.png)

U kunt de workflow nu starten. Zodra de leveringen zijn verzonden, zult u het gedrag van de drie ondergroepen in de leveringslogboeken kunnen volgen, om te zien welk onderwerp het meest succesvol is geweest.

Met workflows kunt u ook uw processen automatiseren door automatisch de variant te identificeren die beter presteerde en deze vervolgens naar de resterende populatie te verzenden. Raadpleeg voor meer informatie deze [use case](../../delivery/using/a-b-testing-use-case.md).
