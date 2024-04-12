---
product: campaign
title: De uiteindelijke levering definiëren
description: Leer hoe u A/B-tests kunt uitvoeren met een speciale praktijkcase
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 5%

---

# AB-tests: de uiteindelijke levering definiëren {#step-6--defining-the-final-delivery}

Wanneer het script is gemaakt om de testwinnaar A/B te selecteren, kunt u de parameters van de uiteindelijke levering definiëren.

1. Verbind de **[!UICONTROL JavaScript code]** activiteit aan de resterende **[!UICONTROL Delivery]** activiteit.
1. Open de **[!UICONTROL Delivery]** activiteit.
1. Schakel het selectievakje **[!UICONTROL Generate an outbound transition]** om de workflow met deze activiteit te voltooien.
1. Laat de standaardwaarden van de andere opties ongewijzigd.

   ![](assets/ab_test_final_delivery.png)

Door de levering voor te bereiden die is opgegeven in de overgang (gedefinieerd via de **[!UICONTROL Javascript Code]** activiteit), kunt u het dan goedkeuren en het verzenden beginnen, zoals die in de volgende stap wordt beschreven.

U kunt de workflow nu starten. [Meer informatie](a-b-testing-uc-start-workflow.md).
