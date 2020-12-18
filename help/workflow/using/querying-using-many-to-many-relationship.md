---
solution: Campaign Classic
product: campaign
title: Het vragen gebruikend een vele-aan-vele verhouding
description: Leer hoe te om vragen uit te voeren gebruikend een vele-aan-vele verhouding
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# Het vragen gebruikend een vele-aan-vele verhouding {#querying-using-a-many-to-many-relationship}

In dit voorbeeld willen we ontvangers herstellen die de afgelopen 7 dagen geen contact hebben gehad. Deze query heeft betrekking op alle leveringen.

Dit voorbeeld toont ook hoe te om een filter met betrekking tot de keus van een inzamelingselement (of oranje knoop) te vormen. De elementen van de inzameling zijn beschikbaar in **[!UICONTROL Field to select]** venster.

* Welke tabel moet worden geselecteerd?

   De ontvankelijke lijst (**nms:ontvanger**)

* Velden die moeten worden geselecteerd voor de uitvoerkolom

   Primaire sleutel, Achternaam, Voornaam en E-mail

* Op basis van welke criteria wordt de gefilterde informatie

   Gebaseerd op de leveringslogboeken van ontvangers die 7 dagen voor vandaag teruggaan

Voer de volgende stappen uit:

1. Open de Algemene vraagredacteur en selecteer de Ontvangende lijst **[!UICONTROL (nms:recipient)]**.
1. Selecteer **[!UICONTROL Data to extract]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** en **[!UICONTROL Email]** in het venster &lt;a0/>.**[!UICONTROL Primary key]**

   ![](assets/query_editor_nveau_33.png)

1. Sorteer de namen in alfabetische volgorde in het sorteervenster.

   ![](assets/query_editor_nveau_34.png)

1. Selecteer **[!UICONTROL Filtering conditions]** in het venster **[!UICONTROL Data filtering]**.
1. In het **[!UICONTROL Target element]** venster, impliceert de het filtreren voorwaarde voor het halen van profielen zonder het volgen logboek voor de laatste 7 dagen twee stappen. Het element dat u moet selecteren, is een veel-op-veel-koppeling.

   * Begin door het **[!UICONTROL Recipient delivery logs (broadlog)]** inzamelingselement (oranje knoop) voor de eerste **[!UICONTROL Value]** kolom te selecteren.

      ![](assets/query_editor_nveau_67.png)

      Kies de operator **[!UICONTROL do not exist as]**. U hoeft geen tweede waarde op deze regel te selecteren.

   * De inhoud van de tweede filtervoorwaarde is afhankelijk van de eerste. Hier wordt het veld **[!UICONTROL Event date]** direct in de tabel **[!UICONTROL Recipient delivery logs]** aangeboden omdat er een koppeling naar deze tabel is.

      ![](assets/query_editor_nveau_36.png)

      Selecteer **[!UICONTROL Event date]** met de **[!UICONTROL greater than or equal to]** exploitant. Selecteer de waarde **[!UICONTROL DaysAgo (7)]**. Klik hiertoe op **[!UICONTROL Edit expression]** in het veld **[!UICONTROL Value]**. Selecteer **[!UICONTROL Formula type]** en **[!UICONTROL Current date minus n days]** in het venster &lt;a0/> en geef &quot;7&quot; als een waarde.**[!UICONTROL Process on dates]**

      ![](assets/query_editor_nveau_37.png)

      De filtervoorwaarde wordt gevormd.

      ![](assets/query_editor_nveau_38.png)

1. Schakel in het venster **[!UICONTROL Data formatting]** de achternaam in hoofdletters. Klik op de regel **[!UICONTROL Last name]** in de kolom **[!UICONTROL Transformation]** en selecteer **[!UICONTROL Switch to upper case]** in het vervolgkeuzemenu.

   ![](assets/query_editor_nveau_39.png)

1. Gebruik de functie **[!UICONTROL Add a calculated field]** om een kolom in te voegen in het venster van de gegevensvoorproef.

   In dit voorbeeld voegt u een berekend veld met de eerste en laatste naam van de ontvangers toe in één kolom. Klik op de functie **[!UICONTROL Add a calculated field]**. Voer in het venster **[!UICONTROL Export calculated field definition]** een label en een interne naam in en kies het type **[!UICONTROL JavaScript Expression]**. Voer vervolgens de volgende expressie in:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Klik op **[!UICONTROL OK]**. Het **[!UICONTROL Data formatting]** venster wordt gevormd.

   Zie deze sectie voor meer informatie over het toevoegen van berekende velden.

1. Het resultaat wordt weergegeven in het venster **[!UICONTROL Data preview]**. Ontvangers die de laatste 7 dagen geen contact hebben gehad, worden in alfabetische volgorde weergegeven. Namen worden in hoofdletters weergegeven en de kolom met de voor- en achternaam is gemaakt.

   ![](assets/query_editor_nveau_41.png)
