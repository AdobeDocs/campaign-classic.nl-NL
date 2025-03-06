---
product: campaign
title: Samenvoegen
description: Meer informatie over de workflowactiviteiten van de Unie
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: 1cda3146-c333-4743-a871-c44583b6e5b2
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Samenvoegen{#union}



Een vereniging groepeert het resultaat van verscheidene binnenkomende activiteiten in één enkel doel. Het doel wordt gecreëerd met alle ontvangen resultaten: alle eerdere activiteiten moeten dus worden afgerond voordat de unie kan worden uitgevoerd.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Voor meer bij het vormen van en het gebruiken van de vakbondsactiviteit, verwijs naar [ het Combineren van verscheidene doelstellingen (Unie) ](targeting-data.md#combining-several-targets--union-).

## Voorbeeld van Vereniging {#union-example}

In het volgende voorbeeld zijn de resultaten van twee query&#39;s gecombineerd om de lijst bij te werken. De twee vragen richten zich op de ontvangers. De resultaten zijn derhalve gebaseerd op dezelfde tabel.

1. Voeg een **[!UICONTROL Union]** -type activiteit in vlak na de twee vragen en vóór een update-type activiteit van de lijst en open het dan.
1. U kunt een label invoeren.
1. Selecteer de **[!UICONTROL Keys only]** afstemmingsmethode omdat in dit voorbeeld de populatie die het resultaat is van query&#39;s consistente gegevens bevat.
1. Als u aanvullende gegevens voor de query&#39;s hebt toegevoegd, kunt u alleen de gedeelde gegevens behouden.
1. Als u de grootte van de uiteindelijke populatie wilt beperken, schakelt u het selectievakje **[!UICONTROL Limit size of generated population]** in.

   Specificeer dit definitieve aantal door het maximumaantal ontvangers in te gaan en door de vraag te selecteren waarvan de bevolking prioriteit zal nemen.

1. Stem de vakbondsactiviteit dan vormen de activiteit van de lijstupdate (zie [ update van de Lijst ](list-update.md)).
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

Deze reeks van drie waarden identificeert het doel dat uit de unie voortvloeit. **[!UICONTROL tableName]** is de naam van de tabel waarin de doel-id&#39;s worden vastgelegd. **[!UICONTROL schema]** is het schema van de populatie (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de tabel.
