---
product: campaign
title: Een filter maken
description: Leer hoe u een filter maakt bij het uitvoeren van query's
feature: Query Editor, Workflows
hide: true
hidefromtoc: true
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# Een filter maken {#creating-a-filter}



De filters die beschikbaar zijn in Adobe Campaign worden gedefinieerd door filtervoorwaarden die worden gemaakt in dezelfde besturingsmodus als query&#39;s.

>[!NOTE]
>
>Voor meer bij het creëren van filters, verwijs naar [ deze sectie ](../../platform/using/filtering-options.md).

Het knooppunt **[!UICONTROL Administration > Configuration > Predefined filters]** bevat alle filters die worden gebruikt in de lijsten en overzichten.

De lijst met operatoren kan bijvoorbeeld worden gefilterd door **[!UICONTROL Active accounts]** :

![](assets/query_editor_filter_sample_1.png)

Het overeenkomende filter bevat de query op de **[!UICONTROL Account disabled]** -waarde van het **[!UICONTROL Operators]** -schema:

![](assets/query_editor_filter_sample_2.png)

Voor dezelfde lijst kunt u met het filter **[!UICONTROL By login or label]** de gegevens in de lijst filteren op basis van de waarde die u hebt ingevoerd in het filterveld:

![](assets/query_editor_filter_sample_3.png)

Het is als volgt samengesteld:

![](assets/query_editor_filter_sample_4.png)

Om de filtervoorwaarden aan te passen, moet de exploitantrekening één van de volgende voorwaarden controleren:

* Het label ervan bevat de tekens die in het invoerveld zijn ingevoerd.
* De operatornaam bevat de tekens die in het invoerveld zijn ingevoerd.
* De inhoud van het beschrijvingsgebied bevat de tekens die in het invoerveld worden ingevoerd.

>[!NOTE]
>
>Met de functie **[!UICONTROL Upper]** kunt u de hoofdlettergevoelige functie deactiveren.

In de kolom **[!UICONTROL Taken into account if]** kunt u de toepassingscriteria voor deze filtervoorwaarden definiëren. Hier vertegenwoordigen de tekens **$(/tmp/@text)** de inhoud van het invoerveld dat aan het filter is gekoppeld:

![](assets/query_editor_filter_sample_5.png)

Hier, **$(/tmp/@text)=&#39;office&#39;**

De **$(/tmp/@text)!=&#39;** uitdrukking past elke voorwaarde toe wanneer het inputgebied niet leeg is.
