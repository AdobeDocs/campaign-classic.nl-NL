---
solution: Campaign Classic
product: campaign
title: Samenvoegen
description: Meer informatie over de workflowactiviteiten van de Unie
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---


# Samenvoegen{#union}

Een vereniging groepeert het resultaat van verscheidene binnenkomende activiteiten in één enkel doel. Het doel wordt gemaakt met alle ontvangen resultaten: alle eerdere activiteiten moeten derhalve worden voltooid voordat de unie kan worden uitgevoerd .

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Raadpleeg [Verschillende doelen combineren (Union)](../../workflow/using/targeting-data.md#combining-several-targets--union-) voor meer informatie over het configureren en gebruiken van de samenvoegingsactiviteit.

## Voorbeeld van verenigen {#union-example}

In het volgende voorbeeld zijn de resultaten van twee query&#39;s gecombineerd om de lijst bij te werken. De twee vragen richten zich op de ontvangers. De resultaten zijn derhalve gebaseerd op dezelfde tabel.

1. Voeg een activiteit van het type **[!UICONTROL Union]** direct na de twee vragen en vóór een update-type activiteit van de lijst in dan open het.
1. U kunt een label invoeren.
1. Selecteer de verzoeningsmethode **[!UICONTROL Keys only]** aangezien, in dit voorbeeld, de populatie die uit vragen resulteert verenigbare gegevens bevat.
1. Als u aanvullende gegevens voor de query&#39;s hebt toegevoegd, kunt u alleen de gedeelde gegevens behouden.
1. Als u de grootte van de uiteindelijke populatie wilt beperken, schakelt u het selectievakje **[!UICONTROL Limit size of generated population]** in.

   Specificeer dit definitieve aantal door het maximumaantal ontvangers in te gaan en door de vraag te selecteren waarvan de bevolking prioriteit zal nemen.

1. Goedkeuren van de samenvoegingsactiviteit en configureren vervolgens de update-activiteit van de lijst (zie [Update van lijst](../../workflow/using/list-update.md)).
1. Start de workflow. Het aantal resultaten wordt weergegeven en de lijst die is gedefinieerd in de updateactiviteit van de lijst, wordt gemaakt of bijgewerkt. Deze lijst bevat de reeks ontvangers voor beide query&#39;s of, indien van toepassing, het nummer dat bij de vorige stap is gedefinieerd.

   ![](assets/union_example.png)

## Invoerparameters {#input-parameters}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert het doel dat uit de unie voortvloeit. **[!UICONTROL tableName]** is de naam van de lijst die de doelherkenningstekens registreert,  **[!UICONTROL schema]** is het schema van de bevolking (gewoonlijk nms:ontvanger) en  **[!UICONTROL recCount]** is het aantal elementen in de lijst.
