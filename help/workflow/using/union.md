---
title: Unie
seo-title: Unie
description: Unie
seo-description: null
page-status-flag: never-activated
uuid: 987e106e-c414-4db4-a93e-96e43dc04370
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 573021ad-1efb-4156-af6d-417737ce745a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Unie{#union}

Een vereniging groepeert het resultaat van verscheidene binnenkomende activiteiten in één enkel doel. Het doel wordt gemaakt met alle ontvangen resultaten: alle eerdere activiteiten moeten derhalve worden voltooid voordat de unie kan worden uitgevoerd .

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Voor meer bij het vormen van en het gebruiken van de vakbondsactiviteit, verwijs naar het [Combineren van verscheidene doelstellingen (Unie)](../../workflow/using/targeting-data.md#combining-several-targets--union-).

## Voorbeeld van Vereniging {#union-example}

In het volgende voorbeeld zijn de resultaten van twee query&#39;s gecombineerd om de lijst bij te werken. De twee vragen richten zich op de ontvangers. De resultaten zijn derhalve gebaseerd op dezelfde tabel.

1. Voeg direct na de twee query&#39;s en vóór een update-type activiteit van de lijst een activiteit van het **[!UICONTROL Union]** -type in en open deze vervolgens.
1. U kunt een label invoeren.
1. Selecteer de **[!UICONTROL Keys only]** afstemmingsmethode omdat in dit voorbeeld de populatie die het resultaat is van query&#39;s consistente gegevens bevat.
1. Als u aanvullende gegevens voor de query&#39;s hebt toegevoegd, kunt u alleen de gedeelde gegevens behouden.
1. Als u de grootte van de uiteindelijke populatie wilt beperken, schakelt u het **[!UICONTROL Limit size of generated population]** selectievakje in.

   Specificeer dit definitieve aantal door het maximumaantal ontvangers in te gaan en door de vraag te selecteren waarvan de bevolking prioriteit zal nemen.

1. Goedkeuren van de vakbondsactiviteit en configureren vervolgens de update-activiteit van de lijst (zie [Lijstupdate](../../workflow/using/list-update.md)).
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

Deze reeks van drie waarden identificeert het doel dat uit de unie voortvloeit. **[!UICONTROL tableName]** is de naam van de lijst die de doelherkenningstekens registreert, **[!UICONTROL schema]** is het schema van de bevolking (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de lijst.
