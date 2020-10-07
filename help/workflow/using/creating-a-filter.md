---
title: Een filter maken
description: Leer hoe u een filter maakt bij het uitvoeren van query's
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---


# Een filter maken {#creating-a-filter}

De filters die beschikbaar zijn in Adobe Campaign worden gedefinieerd door filtervoorwaarden die worden gemaakt in dezelfde besturingsmodus als query&#39;s.

>[!NOTE]
>
>For more on creating filters, refer to [this section](../../platform/using/filtering-options.md).

Het **[!UICONTROL Administration > Configuration > Predefined filters]** knooppunt bevat alle filters die worden gebruikt in de lijsten en overzichten.

De lijst met operatoren kan bijvoorbeeld worden gefilterd met **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

Het passende filter bevat de vraag over de **[!UICONTROL Account disabled]** waarde van het **[!UICONTROL Operators]** schema:

![](assets/query_editor_filter_sample_2.png)

Voor dezelfde lijst kunt u met het **[!UICONTROL By login or label]** filter de gegevens in de lijst filteren op basis van de waarde die u in het filterveld hebt ingevoerd:

![](assets/query_editor_filter_sample_3.png)

Het is als volgt samengesteld:

![](assets/query_editor_filter_sample_4.png)

Om de filtervoorwaarden aan te passen, moet de exploitantrekening één van de volgende voorwaarden controleren:

* Het label ervan bevat de tekens die in het invoerveld zijn ingevoerd.
* De operatornaam bevat de tekens die in het invoerveld zijn ingevoerd.
* De inhoud van het beschrijvingsgebied bevat de tekens die in het invoerveld worden ingevoerd.

>[!NOTE]
>
>Met de **[!UICONTROL Upper]** functie kunt u de hoofdlettergevoelige functie deactiveren.

In de **[!UICONTROL Taken into account if]** kolom kunt u de toepassingscriteria voor deze filtervoorwaarden definiëren. Hier geven de tekens **$(/tmp/@text)** de inhoud weer van het invoerveld dat aan het filter is gekoppeld:

![](assets/query_editor_filter_sample_5.png)

Hier, **$(/tmp/@text)=&#39;office&#39;**

De **$(/tmp/@text)!=&#39;&#39;** expressie past elke voorwaarde toe wanneer het invoerveld niet leeg is.
