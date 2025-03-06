---
product: campaign
title: Vraag die een vele-aan-vele verhouding gebruikt
description: Leer hoe te om vragen uit te voeren gebruikend een vele-aan-vele verhouding
feature: Query Editor, Workflows
hide: true
hidefromtoc: true
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Vraag die een vele-aan-vele verhouding gebruikt {#querying-using-a-many-to-many-relationship}



In dit voorbeeld willen we ontvangers herstellen die de afgelopen 7 dagen geen contact hebben gehad. Deze query heeft betrekking op alle leveringen.

Dit voorbeeld toont ook hoe te om een filter met betrekking tot de keus van een inzamelingselement (of oranje knoop) te vormen. Verzamelingselementen zijn beschikbaar in het **[!UICONTROL Field to select]** -venster.

* Welke tabel moet worden geselecteerd?

  De ontvankelijke lijst (**nms:ontvanger**)

* Velden die moeten worden geselecteerd voor de uitvoerkolom

  Primaire sleutel, Achternaam, Voornaam en E-mail

* Op basis van welke criteria wordt de gefilterde informatie

  Gebaseerd op de leveringslogboeken van ontvangers die 7 dagen voor vandaag teruggaan

Voer de volgende stappen uit:

1. Open de Algemene vraagredacteur en selecteer de Ontvangerlijst **[!UICONTROL (nms:recipient)]**.
1. Selecteer **[!UICONTROL Primary key]** , **[!UICONTROL First name]** , **[!UICONTROL Last name]** en **[!UICONTROL Email]** in het **[!UICONTROL Data to extract]** -venster.

   ![](assets/query_editor_nveau_33.png)

1. Sorteer de namen alfabetisch in het sorteervenster.

   ![](assets/query_editor_nveau_34.png)

1. Selecteer **[!UICONTROL Filtering conditions]** in het **[!UICONTROL Data filtering]** -venster.
1. In het **[!UICONTROL Target element]** -venster bestaat de filtervoorwaarde voor het extraheren van profielen zonder trackinglogbestand gedurende de laatste 7 dagen uit twee stappen. Het element dat u moet selecteren, is een veel-op-veel-koppeling.

   * Selecteer eerst het verzamelingselement **[!UICONTROL Recipient delivery logs (broadlog)]** (oranje knooppunt) voor de eerste **[!UICONTROL Value]** -kolom.

     ![](assets/query_editor_nveau_67.png)

     Kies de operator **[!UICONTROL do not exist as]** . U hoeft geen tweede waarde op deze regel te selecteren.

   * De inhoud van de tweede filtervoorwaarde is afhankelijk van de eerste. Hier wordt het veld **[!UICONTROL Event date]** direct in de tabel **[!UICONTROL Recipient delivery logs]** aangeboden omdat er een koppeling naar deze tabel is.

     ![](assets/query_editor_nveau_36.png)

     Selecteer **[!UICONTROL Event date]** met de operator **[!UICONTROL greater than or equal to]** . Selecteer de waarde **[!UICONTROL DaysAgo (7)]** . Klik hiertoe op **[!UICONTROL Edit expression]** in het veld **[!UICONTROL Value]** . Selecteer **[!UICONTROL Process on dates]** en **[!UICONTROL Current date minus n days]** in het **[!UICONTROL Formula type]** -venster en geef &quot;7&quot; als een waarde.

     ![](assets/query_editor_nveau_37.png)

     De filtervoorwaarde wordt gevormd.

     ![](assets/query_editor_nveau_38.png)

1. Schakel in het **[!UICONTROL Data formatting]** -venster de achternaam in hoofdletters. Klik op de regel **[!UICONTROL Last name]** in de kolom **[!UICONTROL Transformation]** en selecteer **[!UICONTROL Switch to upper case]** in de vervolgkeuzelijst.

   ![](assets/query_editor_nveau_39.png)

1. Gebruik de functie **[!UICONTROL Add a calculated field]** om een kolom in te voegen in het venster van de gegevensvoorvertoning.

   In dit voorbeeld voegt u een berekend veld met de eerste en laatste naam van de ontvangers toe in één kolom. Klik op de functie **[!UICONTROL Add a calculated field]** . Voer in het **[!UICONTROL Export calculated field definition]** -venster een label en een interne naam in en kies het **[!UICONTROL JavaScript Expression]** -type. Voer vervolgens de volgende expressie in:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Klik op **[!UICONTROL OK]**. Het venster **[!UICONTROL Data formatting]** is geconfigureerd.

   Zie deze sectie voor meer informatie over het toevoegen van berekende velden.

1. Het resultaat wordt weergegeven in het venster **[!UICONTROL Data preview]** . Ontvangers die de laatste 7 dagen geen contact hebben gehad, worden in alfabetische volgorde weergegeven. Namen worden in hoofdletters weergegeven en de kolom met de voor- en achternaam is gemaakt.

   ![](assets/query_editor_nveau_41.png)
