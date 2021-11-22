---
product: campaign
title: Samenvoegen
description: Meer informatie over de workflowactiviteiten van de Unie
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 1cda3146-c333-4743-a871-c44583b6e5b2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# Samenvoegen{#union}

![](../../assets/common.svg)

Een vereniging groepeert het resultaat van verscheidene binnenkomende activiteiten in één enkel doel. Het doel wordt gemaakt met alle ontvangen resultaten: alle eerdere activiteiten moeten derhalve worden voltooid voordat de unie kan worden uitgevoerd .

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Voor meer bij het vormen van en het gebruiken van de vakbondsactiviteit, verwijs naar [Combinatie van verschillende doelen (Unie)](targeting-data.md#combining-several-targets--union-).

## Voorbeeld van Vereniging {#union-example}

In het volgende voorbeeld zijn de resultaten van twee query&#39;s gecombineerd om de lijst bij te werken. De twee vragen richten zich op de ontvangers. De resultaten zijn derhalve gebaseerd op dezelfde tabel.

1. Een **[!UICONTROL Union]** -type activiteit direct na de twee vragen en vóór een update-type activiteit van de lijst dan open het.
1. U kunt een label invoeren.
1. Selecteer **[!UICONTROL Keys only]** afstemmingsmethode, aangezien in dit voorbeeld de populatie die het resultaat is van query’s consistente gegevens bevat.
1. Als u aanvullende gegevens voor de query&#39;s hebt toegevoegd, kunt u alleen de gedeelde gegevens behouden.
1. Als u de omvang van de uiteindelijke populatie wilt beperken, controleert u de **[!UICONTROL Limit size of generated population]** doos.

   Specificeer dit definitieve aantal door het maximumaantal ontvangers in te gaan en door de vraag te selecteren waarvan de bevolking prioriteit zal nemen.

1. Goedkeuren van de vakbondsactiviteit en configureren van de update-activiteit van de lijst (zie [Lijstupdate](list-update.md)).
1. De workflow starten. Het aantal resultaten wordt weergegeven en de lijst die is gedefinieerd in de updateactiviteit van de lijst, wordt gemaakt of bijgewerkt. Deze lijst bevat de reeks ontvangers voor beide query&#39;s of, indien van toepassing, het nummer dat bij de vorige stap is gedefinieerd.

   ![](assets/union_example.png)

## Invoerparameters {#input-parameters}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert het doel dat uit de unie voortvloeit. **[!UICONTROL tableName]** is de naam van de lijst die de doelherkenningstekens registreert, **[!UICONTROL schema]** is het schema van de populatie (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de tabel.
