---
solution: Campaign Classic
product: campaign
title: Query’s uitvoeren op de tabel met ontvangers
description: Leer hoe u een query uitvoert op de tabel met ontvangers
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
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

1. Klik **[!UICONTROL Tools > Generic query editor...]** en kies **Ontvangers** (**nms:ontvanger**) lijst. Klik vervolgens op **[!UICONTROL Next]**.
1. Kies: **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** en **[!UICONTROL Account number]**. Deze velden worden toegevoegd aan **[!UICONTROL Output columns]**. Klik vervolgens op **[!UICONTROL Next]**.

   ![](assets/query_editor_03.png)

1. Sorteer de kolommen om ze in de juiste volgorde weer te geven. Hier willen we rekeningnummers in aflopende volgorde en namen in alfabetische volgorde sorteren. Klik vervolgens op **[!UICONTROL Next]**.

   ![](assets/query_editor_04.png)

1. Verfijn uw zoekopdracht in het venster **[!UICONTROL Data filtering]**: Kies **[!UICONTROL Filtering conditions]** en klik **[!UICONTROL Next]**.
1. In het venster **[!UICONTROL Target element]** kunt u de filterinstellingen invoeren.

   Definieer de volgende filtervoorwaarde: ontvangers met een e-maildomein dat gelijk is aan &quot;orange.co.uk&quot;. Om dit te doen, verkies **E-maildomein (@email)** in **[!UICONTROL Expression]** kolom, kies **gelijk aan** in **[!UICONTROL Operator]** kolom en ga &quot;orange.co.uk&quot;in **[!UICONTROL Value]** kolom in.

   ![](assets/query_editor_05.png)

1. Klik zo nodig op de knop **[!UICONTROL Distribution of values]** om een distributie weer te geven op basis van het e-maildomein met vooruitzichten. Voor elk e-maildomein in de database is een percentage beschikbaar. Andere domeinen dan &quot;orange.co.uk&quot; worden weergegeven totdat het filter wordt toegepast.

   Een samenvatting van de vraag wordt getoond bij de bodem van het venster: **E-maildomein is gelijk aan &#39;orange.co.uk&#39;**.

1. Klik **[!UICONTROL Preview]** om een idee van het vraagresultaat te krijgen: alleen de e-maildomeinen &quot;orange.co.uk&quot; worden weergegeven.

   ![](assets/query_editor_nveau_17.png)

1. Wij zullen nu de vraag veranderen om contacten te vinden die niet in Londen wonen.

   Selecteer **[!UICONTROL City (location/@city)]** in **[!UICONTROL Expression]** kolom, **[!UICONTROL different from]** als exploitant en ga **[!UICONTROL London]** in **[!UICONTROL Value]** kolom in.

   ![](assets/query_editor_08.png)

1. Hiermee gaat u naar het venster **[!UICONTROL Data formatting]**. Controleer de kolomvolgorde. Verplaats de kolom &quot;Plaats&quot; omhoog onder de kolom &quot;Rekeningnummer&quot;.

   Schakel de kolom Voornaam uit om deze uit de lijst te verwijderen.

   ![](assets/query_editor_nveau_15.png)

1. Klik in het venster **[!UICONTROL Data preview]** op **[!UICONTROL Start the preview of the data]**. Deze functie berekent het resultaat van de query.

   Het **[!UICONTROL Column results]** lusje toont het vraagresultaat in kolommen.

   Het resultaat toont alle ontvangers met een &quot;orange.co.uk&quot;e-maildomein die niet in Londen wonen. De kolom Voornaam wordt niet weergegeven omdat deze tijdens het vorige werkgebied niet is ingeschakeld. Accountnummers worden in aflopende volgorde gesorteerd.

   ![](assets/query_editor_nveau_12.png)

   Op het tabblad **[!UICONTROL XML result]** wordt het resultaat weergegeven in XML-indeling.

   ![](assets/query_editor_nveau_13.png)

   Het **[!UICONTROL Generated QSL queries]** lusje toont het vraagresultaat in SQL formaat.

   ![](assets/query_editor_nveau_14.png)
