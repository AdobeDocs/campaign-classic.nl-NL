---
product: campaign
title: A/B-tests configureren
description: Leer hoe u A/B-tests configureert in Campagne
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 4%

---

# A/B-tests configureren {#configuring-a-b-testing}

In deze sectie wordt beschreven hoe u een workflow bouwt om A/B-tests uit te voeren.

1. Maak een nieuwe workflow en configureer vervolgens een [Query](../../workflow/using/query.md) activiteit om de gewenste bevolking te bereiken.

1. Voeg een [Splitsen](../../workflow/using/split.md) activiteit om de doelpopulatie in meerdere subgroepen te verdelen.

1. Open de activiteit, dan vorm elke ondergroep volgens uw behoeften. Voor meer op hoe te om een te vormen **[!UICONTROL Split]** activiteit, zie [deze sectie](../../workflow/using/split.md).

   In dit voorbeeld willen we twee nieuwe onderwerpen testen voor een nieuwsbrief door ze allemaal te presenteren aan 10 procent van de doelgroep.

   ![](assets/ab-testing-split.png)

1. Voeg een overgang toe om de nieuwsbrief met het huidige onderwerp naar de resterende bevolking te sturen. Activeer de **[!UICONTROL Generate complement]** van de **[!UICONTROL General]** tab.

   ![](assets/ab-testing-complement.png)

1. Voeg voor elke subset de versie van de levering toe die u wilt testen.

   ![](assets/ab-testing-delivery.png)

U kunt de workflow nu starten. Zodra de leveringen zijn verzonden, zult u het gedrag van de drie ondergroepen in de leveringslogboeken kunnen volgen, om te zien welk onderwerp het meest succesvol is geweest.

Met workflows kunt u ook uw processen automatiseren door automatisch de variant te identificeren die beter presteerde en deze vervolgens naar de resterende populatie te verzenden. Raadpleeg voor meer informatie deze [use case](a-b-testing-use-case.md).
