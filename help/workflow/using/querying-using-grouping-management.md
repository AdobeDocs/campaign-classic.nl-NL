---
title: Vragen met behulp van groeperingsbeheer
description: Leer hoe u query's uitvoert met behulp van groeperingsbeheer
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Vragen met behulp van groeperingsbeheer {#querying-using-grouping-management}

In dit voorbeeld willen we een query uitvoeren om alle e-maildomeinen te zoeken die meer dan 30 keer zijn aangewezen tijdens eerdere leveringen.

* Welke tabel moet worden geselecteerd?

   De tabel met ontvangers (nms:ontvanger)

* Velden die moeten worden geselecteerd in uitvoerkolommen?

   E-maildomein en primaire sleutel (met aantal)

* Gegevensgroepering?

   Gebaseerd op e-maildomein met een aantal primaire sleutels boven 30. Deze bewerking wordt uitgevoerd met de **[!UICONTROL Group by + Having]** optie. **[!UICONTROL Group by + Having]** Hiermee kunt u gegevens groeperen (&quot;groeperen door&quot;) en een selectie maken van gegroepeerde objecten (&quot;hebben&quot;).

U kunt dit voorbeeld maken door de volgende stappen toe te passen:

1. Open de tabel **[!UICONTROL Generic query editor]** en kies de tabel Ontvanger (**nms:ontvanger**).

   ![](assets/query_editor_02.png)

1. Selecteer in het **[!UICONTROL Data to extract]** venster de velden **[!UICONTROL Email domain]** en **[!UICONTROL Primary key]** velden. Een telling uitvoeren op het **[!UICONTROL Primary key]** veld.

   Raadpleeg [deze sectie](../../platform/using/defining-filter-conditions.md#building-expressions)voor meer informatie over primaire sleutels.

1. Schakel het **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** selectievakje in.

   ![](assets/query_editor_nveau_29.png)

1. Sorteer de e-maildomeinen in aflopende volgorde in het **[!UICONTROL Sorting]** venster. Controleer **[!UICONTROL Yes]** de **[!UICONTROL Descending sort]** kolom om dit te doen. Klik **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. Selecteer **[!UICONTROL Data filtering]** in **[!UICONTROL Filtering conditions]**. Ga naar het **[!UICONTROL Target elements]** venster en klik **[!UICONTROL Next]**.
1. Selecteer in het **[!UICONTROL Data grouping]** venster de **[!UICONTROL Email domain]** knop door te klikken **[!UICONTROL Add]**.

   Dit venster voor gegevensgroepering wordt alleen weergegeven als het vak **[!UICONTROL Handle groupings (GROUP BY + HAVING]**) is ingeschakeld.

   ![](assets/query_editor_blacklist_04.png)

1. Geef in het **[!UICONTROL Grouping condition]** venster een aantal primaire sleutels op dat groter is dan 30, omdat we alleen willen dat e-maildomeinen die meer dan 30 keer zijn bedoeld, als resultaten worden geretourneerd.

   Dit venster wordt weergegeven wanneer het **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** selectievakje is ingeschakeld: Hier wordt het groeperingsresultaat gefilterd (HAVING).

   ![](assets/query_editor_blacklist_05.png)

1. Klik in het **[!UICONTROL Data formatting]** venster op **[!UICONTROL Next]**: hier is geen opmaak nodig .
1. Klik in het venster met de gegevensvoorvertoning op **[!UICONTROL Launch data preview]**: hier worden drie verschillende e-maildomeinen geretourneerd die meer dan 30 keer als doel hebben.

   ![](assets/query_editor_blacklist_06.png)
