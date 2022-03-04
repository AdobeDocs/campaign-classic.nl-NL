---
product: campaign
title: Vraag die een vele-aan-vele verhouding gebruikt
description: Leer hoe te om vragen uit te voeren gebruikend een vele-aan-vele verhouding
feature: Query Editor
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Vraag die een vele-aan-vele verhouding gebruikt {#querying-using-a-many-to-many-relationship}

![](../../assets/common.svg)

In dit voorbeeld willen we ontvangers herstellen die de afgelopen 7 dagen geen contact hebben gehad. Deze query heeft betrekking op alle leveringen.

Dit voorbeeld toont ook hoe te om een filter met betrekking tot de keus van een inzamelingselement (of oranje knoop) te vormen. De elementen van de inzameling zijn beschikbaar in **[!UICONTROL Field to select]** venster.

* Welke tabel moet worden geselecteerd?

   De tabel met ontvangers (**nms:ontvanger**)

* Velden die moeten worden geselecteerd voor de uitvoerkolom

   Primaire sleutel, Achternaam, Voornaam en E-mail

* Op basis van welke criteria wordt de gefilterde informatie

   Gebaseerd op de leveringslogboeken van ontvangers die 7 dagen voor vandaag teruggaan

Voer de volgende stappen uit:

1. Open de Algemene vraagredacteur en selecteer de Ontvangerlijst **[!UICONTROL (nms:recipient)]**.
1. In de **[!UICONTROL Data to extract]** venster, selecteert u **[!UICONTROL Primary key]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** en **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. Sorteer de namen in alfabetische volgorde in het sorteervenster.

   ![](assets/query_editor_nveau_34.png)

1. In de **[!UICONTROL Data filtering]** venster, selecteert u **[!UICONTROL Filtering conditions]**.
1. In de **[!UICONTROL Target element]** in het venster moeten twee stappen worden uitgevoerd voor het filteren van profielen zonder traceringslogbestand gedurende de laatste 7 dagen. Het element dat u moet selecteren, is een veel-op-veel-koppeling.

   * Begin door te selecteren **[!UICONTROL Recipient delivery logs (broadlog)]** verzamelingselement (oranje knooppunt) voor de eerste **[!UICONTROL Value]** kolom.

      ![](assets/query_editor_nveau_67.png)

      Kies de optie **[!UICONTROL do not exist as]** operator. U hoeft geen tweede waarde op deze regel te selecteren.

   * De inhoud van de tweede filtervoorwaarde is afhankelijk van de eerste. Hier, de **[!UICONTROL Event date]** het veld wordt rechtstreeks in het **[!UICONTROL Recipient delivery logs]** tabel omdat er een koppeling naar deze tabel is.

      ![](assets/query_editor_nveau_36.png)

      Selecteren **[!UICONTROL Event date]** met de **[!UICONTROL greater than or equal to]** operator. Selecteer **[!UICONTROL DaysAgo (7)]** waarde. Klik op **[!UICONTROL Edit expression]** in de **[!UICONTROL Value]** veld. In de **[!UICONTROL Formula type]** venster, selecteert u **[!UICONTROL Process on dates]** en **[!UICONTROL Current date minus n days]** en geeft &quot;7&quot; als een waarde.

      ![](assets/query_editor_nveau_37.png)

      De filtervoorwaarde wordt gevormd.

      ![](assets/query_editor_nveau_38.png)

1. In de **[!UICONTROL Data formatting]** venster, overschakelen van laatste namen naar hoofdletters. Klik op de knop **[!UICONTROL Last name]** in de **[!UICONTROL Transformation]** kolom en selecteer **[!UICONTROL Switch to upper case]** in het vervolgkeuzemenu.

   ![](assets/query_editor_nveau_39.png)

1. Gebruik de **[!UICONTROL Add a calculated field]** gebruiken om een kolom in te voegen in het venster met gegevensvoorvertoning.

   In dit voorbeeld voegt u een berekend veld met de eerste en laatste naam van de ontvangers toe in één kolom. Klik op de knop **[!UICONTROL Add a calculated field]** functie. In de **[!UICONTROL Export calculated field definition]** in, voert u een label en een interne naam in en kiest u de **[!UICONTROL JavaScript Expression]** type. Voer vervolgens de volgende expressie in:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Klik op **[!UICONTROL OK]**. De **[!UICONTROL Data formatting]** venster is geconfigureerd.

   Zie deze sectie voor meer informatie over het toevoegen van berekende velden.

1. Het resultaat wordt weergegeven in het dialoogvenster **[!UICONTROL Data preview]** venster. Ontvangers die de laatste 7 dagen geen contact hebben gehad, worden in alfabetische volgorde weergegeven. Namen worden in hoofdletters weergegeven en de kolom met de voor- en achternaam is gemaakt.

   ![](assets/query_editor_nveau_41.png)
