---
solution: Campaign Classic
product: campaign
title: Definiëren van de uiteindelijke levering
description: Leer hoe u een A/B-test uitvoert met een speciale praktijkcase.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Definiëren van de uiteindelijke levering {#step-6--defining-the-final-delivery}

Wanneer het script is gemaakt om de testwinnaar A/B te selecteren, kunt u de parameters van de uiteindelijke levering definiëren.

1. Sluit de **[!UICONTROL JavaScript code]** activiteit aan de resterende **[!UICONTROL Delivery]** activiteit aan.
1. Open de **[!UICONTROL Delivery]** activiteit.
1. Schakel de optie **[!UICONTROL Generate an outbound transition]** uit om de workflow met deze activiteit te voltooien.
1. Laat de standaardwaarden van de andere opties ongewijzigd.

   ![](assets/ab_test_final_delivery.png)

Door de levering voor te bereiden die is opgegeven in de overgang (gedefinieerd via de **[!UICONTROL Javascript Code]**-activiteit), kunt u deze goedkeuren en het verzenden starten, zoals beschreven in de volgende stap.

U kunt nu de workflow starten (zie [Stap 7: Start de workflow.](../../delivery/using/a-b-testing-uc-start-workflow.md)).
