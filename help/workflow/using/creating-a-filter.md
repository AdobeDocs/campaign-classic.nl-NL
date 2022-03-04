---
product: campaign
title: Een filter maken
description: Leer hoe u een filter maakt bij het uitvoeren van query's
feature: Workflows
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---

# Een filter maken {#creating-a-filter}

![](../../assets/common.svg)

De filters die beschikbaar zijn in Adobe Campaign worden gedefinieerd door filtervoorwaarden die worden gemaakt in dezelfde besturingsmodus als query&#39;s.

>[!NOTE]
>
>Raadpleeg voor meer informatie over het maken van filters [deze sectie](../../platform/using/filtering-options.md).

De **[!UICONTROL Administration > Configuration > Predefined filters]** bevat alle filters die in de lijsten en overzichten worden gebruikt.

De lijst met operatoren kan bijvoorbeeld worden gefilterd door **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

Het overeenkomende filter bevat de query voor het **[!UICONTROL Account disabled]** waarde van de **[!UICONTROL Operators]** schema:

![](assets/query_editor_filter_sample_2.png)

Voor dezelfde lijst **[!UICONTROL By login or label]** Hiermee kunt u de gegevens in de lijst filteren op basis van de waarde die u hebt ingevoerd in het filterveld:

![](assets/query_editor_filter_sample_3.png)

Het is als volgt samengesteld:

![](assets/query_editor_filter_sample_4.png)

Om de filtervoorwaarden aan te passen, moet de exploitantrekening één van de volgende voorwaarden controleren:

* Het label ervan bevat de tekens die in het invoerveld zijn ingevoerd.
* De operatornaam bevat de tekens die in het invoerveld zijn ingevoerd.
* De inhoud van het beschrijvingsgebied bevat de tekens die in het invoerveld worden ingevoerd.

>[!NOTE]
>
>De **[!UICONTROL Upper]** kunt u de hoofdlettergevoelige functie deactiveren.

De **[!UICONTROL Taken into account if]** in de kolom kunt u de toepassingscriteria voor deze filtervoorwaarden definiëren. Hier, de **$(/tmp/@text)** De tekens vertegenwoordigen de inhoud van het invoerveld dat aan het filter is gekoppeld:

![](assets/query_editor_filter_sample_5.png)

Hier, **$(/tmp/@text)=&#39;office&#39;**

De **$(/tmp/@text)!=&#39;&#39;** expressie past elke voorwaarde toe wanneer het invoerveld niet leeg is.
