---
title: Query’s uitvoeren op de tabel met ontvangers
description: Leer hoe u een query uitvoert op de tabel met ontvangers
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
source-wordcount: '392'
ht-degree: 3%

---


# Query’s uitvoeren op de tabel met ontvangers {#querying-recipient-table}

In dit voorbeeld willen we de namen en e-mails herstellen van ontvangers wier e-maildomein &quot;orange.co.uk&quot; is en die niet in Londen wonen.

* Welke tabel moeten we kiezen?

   De tabel met ontvangers (nms:ontvanger)

* Velden die moeten worden geselecteerd als uitvoerkolommen

   E-mail, naam, plaats en rekeningnummer

* Wat zijn de filtervoorwaarden van de ontvangers?

   Plaats en e-maildomein

* Is een soort gevormd?

   Ja, gebaseerd op **[!UICONTROL Account number]** en **[!UICONTROL Last name]**

U kunt dit voorbeeld maken door de volgende stappen toe te passen:

1. Klik **[!UICONTROL Tools > Generic query editor...]** en kies de **Ontvangers** (**nms:ontvanger**) lijst. Klik vervolgens op **[!UICONTROL Next]**.
1. Kies: **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** en **[!UICONTROL Account number]**. Deze velden worden toegevoegd aan **[!UICONTROL Output columns]**. Klik vervolgens op **[!UICONTROL Next]**.

   ![](assets/query_editor_03.png)

1. Sorteer de kolommen om ze in de juiste volgorde weer te geven. Hier willen we rekeningnummers in aflopende volgorde en namen in alfabetische volgorde sorteren. Klik vervolgens op **[!UICONTROL Next]**.

   ![](assets/query_editor_04.png)

1. Verfijn de zoekopdracht in het **[!UICONTROL Data filtering]** venster: kiest **[!UICONTROL Filtering conditions]** en klikt **[!UICONTROL Next]**.
1. In het **[!UICONTROL Target element]** venster kunt u de filterinstellingen invoeren.

   Definieer de volgende filtervoorwaarde: ontvangers met een e-maildomein dat gelijk is aan &quot;orange.co.uk&quot;. Kies hiervoor **E-maildomein (@email)** in de **[!UICONTROL Expression]** kolom, kies **gelijk aan** in de **[!UICONTROL Operator]** kolom en voer &quot;orange.co.uk&quot; in de **[!UICONTROL Value]** kolom in.

   ![](assets/query_editor_05.png)

1. Klik zo nodig op de **[!UICONTROL Distribution of values]** knop om een distributie weer te geven op basis van het e-maildomein van vooruitzichten. Voor elk e-maildomein in de database is een percentage beschikbaar. Andere domeinen dan &quot;orange.co.uk&quot; worden weergegeven totdat het filter wordt toegepast.

   Een samenvatting van de vraag wordt getoond bij de bodem van het venster: **E-maildomein is gelijk aan &#39;orange.co.uk&#39;**.

1. Klik op de **[!UICONTROL Preview]** koppeling om een idee te krijgen van het zoekresultaat: alleen de e-maildomeinen &quot;orange.co.uk&quot; worden weergegeven.

   ![](assets/query_editor_nveau_17.png)

1. Wij zullen nu de vraag veranderen om contacten te vinden die niet in Londen wonen.

   Selecteer **[!UICONTROL City (location/@city)]** in de **[!UICONTROL Expression]** kolom, **[!UICONTROL different from]** als exploitant en ga **[!UICONTROL London]** in de **[!UICONTROL Value]** kolom in.

   ![](assets/query_editor_08.png)

1. Hiermee gaat u naar het **[!UICONTROL Data formatting]** venster. Controleer de kolomvolgorde. Verplaats de kolom &quot;Plaats&quot; omhoog onder de kolom &quot;Rekeningnummer&quot;.

   Schakel de kolom Voornaam uit om deze uit de lijst te verwijderen.

   ![](assets/query_editor_nveau_15.png)

1. In the **[!UICONTROL Data preview]** window, click **[!UICONTROL Start the preview of the data]**. Deze functie berekent het resultaat van de query.

   Het **[!UICONTROL Column results]** lusje toont het vraagresultaat in kolommen.

   Het resultaat toont alle ontvangers met een &quot;orange.co.uk&quot;e-maildomein die niet in Londen wonen. De kolom Voornaam wordt niet weergegeven omdat deze tijdens het vorige werkgebied niet is ingeschakeld. Accountnummers worden in aflopende volgorde gesorteerd.

   ![](assets/query_editor_nveau_12.png)

   Op het **[!UICONTROL XML result]** tabblad wordt het resultaat weergegeven in XML-indeling.

   ![](assets/query_editor_nveau_13.png)

   Het **[!UICONTROL Generated QSL queries]** lusje toont het vraagresultaat in SQL formaat.

   ![](assets/query_editor_nveau_14.png)
