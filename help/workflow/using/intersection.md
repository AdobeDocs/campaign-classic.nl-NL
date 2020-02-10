---
title: Intersectie
seo-title: Intersectie
description: Intersectie
seo-description: null
page-status-flag: never-activated
uuid: a8ff7a66-6c12-4e3c-ad45-d11b34ca64ff
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: d0dd9c74-aad5-452e-a11d-c231dacd2aec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Intersectie{#intersection}

Een **doorsnede**-type activiteit leidt tot een doel van de doorsnede van de ontvangen doelstellingen.

Met een doorsnede kunt u alleen de populatie extraheren die algemeen geldt voor alle resultaten van de binnenkomende activiteit. Het doel wordt gemaakt met alle ontvangen resultaten: alle eerdere activiteiten moeten daarom worden beëindigd voordat de doorsnede kan worden uitgevoerd. Om deze activiteit te vormen, moet u een etiket voor het evenals de opties betreffende het resultaat ingaan.

![](assets/s_user_segmentation_inter.png)

Voor meer bij het vormen van en het gebruiken van de intersectieactiviteit, verwijs naar het [Uithalen van gezamenlijke gegevens (Doorsnede)](../../workflow/using/targeting-data.md#extracting-joint-data--intersection-).

Controleer de **[!UICONTROL Generate complement]** optie als u de resterende populatie wilt verwerken. Het complement zal de samenvoeging bevatten van de resultaten van alle binnenkomende activiteiten min de doorsnede. Een extra uitgaande overgang zal dan aan de activiteit worden toegevoegd, als volgt:

![](assets/s_user_segmentation_inter_compl.png)

## Voorbeeld van intersectie {#intersection-example}

In het volgende voorbeeld is het doel van de doorsnede het berekenen van de ontvangers gemeenschappelijk aan drie eenvoudige vragen om een lijst te creëren.

1. Na drie eenvoudige vragen, neem een **[!UICONTROL Intersection]** - type activiteit op.

   In dit voorbeeld; de vragen betreffen respectievelijk mannen, ontvangers die in Parijs wonen en ontvangers tussen 18 en 30 jaar oud.

1. Configureer de doorsnede. Selecteer hiertoe de **[!UICONTROL Keys only]** afstemmingsmethode omdat de populaties die uit de query&#39;s voortvloeien, consistente gegevens bevatten.
1. Als u aanvullende gegevens voor de query&#39;s hebt ingevoerd, kunt u ervoor kiezen alleen die gegevens te behouden die door ontvangers worden gedeeld door het desbetreffende vakje in te schakelen.
1. Als u de rest van de gegevens wilt gebruiken (met betrekking tot de vragen maar niet hun kruising), controleer het **[!UICONTROL Generate complement]** vakje.
1. Voeg een activiteit van de lijstupdate na het intersectieresultaat toe. U kunt ook een update van de lijst toevoegen aan het complement als u dit wilt gebruiken.
1. Voer de workflow uit. Hier, zijn twee ontvangers op alle drie inputted vragen tezelfdertijd van toepassing. De aanvulling bestaat uit vijf ontvangers die slechts op één of twee van de drie vragen van toepassing zijn.

   Het resultaat van de doorsnede wordt naar de eerste update van de lijst verzonden. Als u ervoor hebt gekozen om het complement te gebruiken, wordt het ook verzonden naar de tweede lijstupdate.

   ![](assets/intersection_example.png)

## Invoerparameters {#input-parameters}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert het doel resulterend uit de doorsnede. **[!UICONTROL tableName]** is de naam van de lijst die de doelherkenningstekens registreert, **[!UICONTROL schema]** is het schema van de bevolking (gewoonlijk **[!UICONTROL nms:recipient]**) en **[!UICONTROL recCount]** is het aantal elementen in de lijst.
