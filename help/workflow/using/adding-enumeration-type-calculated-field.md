---
product: campaign
title: Een berekend veld voor het type opsomming toevoegen
description: Leer hoe u een berekend veld voor het type opsomming toevoegt
audience: workflow
content-type: reference
topic-tags: use-cases
feature: Workflows, Data Management
exl-id: 3f606d3a-0af5-4315-bb08-1b21a71f1721
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Een berekend veld voor het type opsomming toevoegen {#adding-an-enumeration-type-calculated-field}



Hier willen wij een vraag met tot stand brengen **[!UICONTROL Enumerations]** berekend veld. Met dit veld wordt een extra kolom gegenereerd in het venster met de gegevensvoorvertoning. Deze kolom zal de numerieke waarden specificeren die als resultaat voor elke ontvanger (0, 1 en 2) zijn teruggekeerd. Aan elke waarde in de nieuwe kolom wordt een geslacht toegewezen: &quot;Mannelijk&quot; voor &quot;1&quot;, &quot;Vrouwelijk&quot; voor &quot;2&quot; of &quot;Niet aangegeven&quot; als de waarde gelijk is aan &quot;0&quot;.

* Welke tabel moet worden geselecteerd?

  De tabel met ontvangers (nms:ontvanger)

* Te selecteren velden in de uitvoerkolom?

  Achternaam, voornaam, geslacht

* Aan welke criteria wordt de informatie gefilterd?

  De taal van de ontvanger

Voer de volgende stappen uit:

1. Open de Algemene vraagredacteur en selecteer de Ontvangerlijst (**[!UICONTROL nms:recipient]**).
1. In de **[!UICONTROL Data to extract]** venster, selecteert u **[!UICONTROL Last name]**, **[!UICONTROL First name]** en **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_73.png)

1. In de **[!UICONTROL Sorting]** venster, klikt u op **[!UICONTROL Next]**: voor dit voorbeeld is geen sortering nodig.
1. In **[!UICONTROL Data filtering]** selecteert u **[!UICONTROL Filtering conditions]**.
1. In de **[!UICONTROL Target element]** , stelt u een filtervoorwaarde in om ontvangers die Engels spreken, te verzamelen.

   ![](assets/query_editor_nveau_74.png)

1. In de **[!UICONTROL Data formatting]** venster, klikt u op **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. Ga naar de **[!UICONTROL Type]** van het **[!UICONTROL Export calculated field definition]** venster en selecteer **[!UICONTROL Enumerations]**.

   Definieer de kolom waarnaar het nieuwe berekende veld moet verwijzen. Selecteer de optie **[!UICONTROL Gender]** in het vervolgkeuzemenu van het dialoogvenster **[!UICONTROL Source column]** veld: de doelwaarden vallen samen met de **[!UICONTROL Gender]** kolom.

   ![](assets/query_editor_nveau_76.png)

   Definieer de **Bron** en **Doel** waarden: de doelwaarde maakt het queryresultaat beter leesbaar. Deze vraag zou ontvankelijk geslacht moeten terugkeren en het resultaat zal of 0, 1, of 2 zijn.

   Voor elke &quot;bron-bestemming&quot;lijn die moet worden ingegaan, klik **[!UICONTROL Add]** in de **[!UICONTROL List of enumeration values]**:

   * In de **[!UICONTROL Source]** Voer in een nieuwe regel de bronwaarde voor elk geslacht (0,1,2) in.
   * In de **[!UICONTROL Destination]** Voer de waarden in: &quot;Niet aangegeven&quot; voor regel &quot;0&quot;, &quot;Mannelijk&quot; voor regel &quot;1&quot; en &quot;Vrouwelijk&quot; voor regel &quot;2&quot;.

   Selecteer de **[!UICONTROL Keep the source value]** functie.

   Klikken **[!UICONTROL OK]** om het berekende veld goed te keuren.

   ![](assets/query_editor_nveau_77.png)

1. In de **[!UICONTROL Data formatting]** venster, klikt u op **[!UICONTROL Next]**.
1. In het voorvertoningsvenster: **[!UICONTROL start the preview of the data]**.

   De aanvullende kolom definieert het geslacht van 0, 1 en 2:

   * 0 voor &quot;Niet aangegeven&quot;
   * 1 voor &quot;Mannelijk&quot;
   * 2 voor &quot;Vrouwelijk&quot;

   ![](assets/query_editor_nveau_78.png)

   Als u bijvoorbeeld geen geslacht &quot;2&quot; opgeeft in het dialoogvenster **[!UICONTROL List of enumeration values]** en de **[!UICONTROL Generate a warning and continue]** de functie van de **[!UICONTROL In other cases]** wordt geselecteerd, krijgt u een waarschuwingslogboek. Dit logbestand geeft aan dat geslacht &quot;2&quot; (vrouwelijk) niet is ingevoerd. Het wordt weergegeven in het dialoogvenster **[!UICONTROL Logs generated during export]** in het venster met gegevensvoorvertoning.

   ![](assets/query_editor_nveau_79.png)

   Neem een ander voorbeeld en zeg dat de opsommingswaarde &quot;2&quot;niet is ingegaan. Selecteer de **[!UICONTROL Generate an error and reject the line]** functie: alle geslachten die &quot;2&quot; ontvangen, zullen anomalieën veroorzaken en de andere informatie op de regel (voornaam en achternaam, enz.) wordt niet geëxporteerd. In het dialoogvenster **[!UICONTROL Logs generated during export]** in het venster met gegevensvoorvertoning. Dit logboek wijst erop dat de opsommingswaarde &quot;2&quot;niet ingegaan is.

   ![](assets/query_editor_nveau_80.png)
