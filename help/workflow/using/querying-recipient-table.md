---
product: campaign
title: Een query uitvoeren op de tabel met ontvangers
description: Leer hoe u een query uitvoert op de tabel met ontvangers
feature: Query Editor
exl-id: 5b037798-b092-4c98-9f6a-4af7fc7941c6
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---

# Een query uitvoeren op de tabel met ontvangers {#querying-recipient-table}

![](../../assets/v7-only.svg)

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

1. Klikken **[!UICONTROL Tools > Generic query editor...]** en kiest u **Ontvangers** (**nms:ontvanger**) tabel. Klik vervolgens op **[!UICONTROL Next]**.
1. Kies: **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** en **[!UICONTROL Account number]**. Deze velden worden toegevoegd aan **[!UICONTROL Output columns]**. Klik vervolgens op **[!UICONTROL Next]**.

   ![](assets/query_editor_03.png)

1. Sorteer de kolommen om ze in de juiste volgorde weer te geven. Hier willen we rekeningnummers in aflopende volgorde en namen in alfabetische volgorde sorteren. Klik vervolgens op **[!UICONTROL Next]**.

   ![](assets/query_editor_04.png)

1. In de **[!UICONTROL Data filtering]** venster, verfijnen uw zoekopdracht: kiezen **[!UICONTROL Filtering conditions]** en klik op **[!UICONTROL Next]**.
1. De **[!UICONTROL Target element]** kunt u de filterinstellingen invoeren.

   Definieer de volgende filtervoorwaarde: ontvangers met een e-maildomein dat gelijk is aan &quot;orange.co.uk&quot;. Kies **E-maildomein (@email)** in de **[!UICONTROL Expression]** kolom, kies **gelijk aan** in de **[!UICONTROL Operator]** kolom en voer &quot;orange.co.uk&quot; in in het dialoogvenster **[!UICONTROL Value]** kolom.

   ![](assets/query_editor_05.png)

1. Klik indien nodig op de knop **[!UICONTROL Distribution of values]** om een distributie te bekijken die op het e-maildomein van vooruitzichten wordt gebaseerd. Voor elk e-maildomein in de database is een percentage beschikbaar. Andere domeinen dan &quot;orange.co.uk&quot; worden weergegeven totdat het filter wordt toegepast.

   Een samenvatting van de vraag wordt getoond bij de bodem van het venster: **E-maildomein is gelijk aan &#39;orange.co.uk&#39;**.

1. Klik op de knop **[!UICONTROL Preview]** om een idee van het vraagresultaat te krijgen: alleen de e-maildomeinen &quot;orange.co.uk&quot; worden weergegeven.

   ![](assets/query_editor_nveau_17.png)

1. Wij zullen nu de vraag veranderen om contacten te vinden die niet in Londen wonen.

   Selecteren **[!UICONTROL City (location/@city)]** in de **[!UICONTROL Expression]** kolom, **[!UICONTROL different from]** als een operator en **[!UICONTROL London]** in de **[!UICONTROL Value]** kolom.

   ![](assets/query_editor_08.png)

1. Hiermee gaat u naar de **[!UICONTROL Data formatting]** venster. Controleer de kolomvolgorde. Verplaats de kolom &quot;Plaats&quot; omhoog onder de kolom &quot;Rekeningnummer&quot;.

   Schakel de kolom Voornaam uit om deze uit de lijst te verwijderen.

   ![](assets/query_editor_nveau_15.png)

1. In de **[!UICONTROL Data preview]** venster, klikt u op **[!UICONTROL Start the preview of the data]**. Deze functie berekent het resultaat van de query.

   De **[!UICONTROL Column results]** toont het vraagresultaat in kolommen.

   Het resultaat toont alle ontvangers met een &quot;orange.co.uk&quot;e-maildomein die niet in Londen wonen. De kolom Voornaam wordt niet weergegeven omdat deze tijdens het vorige werkgebied niet is ingeschakeld. Accountnummers worden in aflopende volgorde gesorteerd.

   ![](assets/query_editor_nveau_12.png)

   De **[!UICONTROL XML result]** geeft het resultaat weer in XML-indeling.

   ![](assets/query_editor_nveau_13.png)

   De **[!UICONTROL Generated QSL queries]** toont het vraagresultaat in SQL formaat.

   ![](assets/query_editor_nveau_14.png)
