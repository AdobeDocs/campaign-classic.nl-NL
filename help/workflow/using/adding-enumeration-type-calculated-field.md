---
title: Een berekend veld van het type Opsomming toevoegen
description: Leer hoe u een berekend veld voor het type opsomming toevoegt
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


# Een berekend veld van het type Opsomming toevoegen {#adding-an-enumeration-type-calculated-field}

Hier willen wij een vraag met een **[!UICONTROL Enumerations]** type berekend gebied tot stand brengen. Met dit veld wordt een extra kolom gegenereerd in het venster met de gegevensvoorvertoning. Deze kolom zal de numerieke waarden specificeren die als resultaat voor elke ontvanger (0, 1 en 2) zijn teruggekeerd. Aan elke waarde in de nieuwe kolom wordt een geslacht toegewezen: &quot;Mannelijk&quot; voor &quot;1&quot;, &quot;Vrouwelijk&quot; voor &quot;2&quot; of &quot;Niet aangegeven&quot; als de waarde gelijk is aan &quot;0&quot;.

* Welke tabel moet worden geselecteerd?

   De tabel met ontvangers (nms:ontvanger)

* Te selecteren velden in de uitvoerkolom?

   Achternaam, voornaam, geslacht

* Aan welke criteria wordt de informatie gefilterd?

   De taal van de ontvanger

Voer de volgende stappen uit:

1. Open de Algemene vraagredacteur en selecteer de Ontvangerlijst (**[!UICONTROL nms:recipient]**).
1. Selecteer in het **[!UICONTROL Data to extract]** venster **[!UICONTROL Last name]** de optie **[!UICONTROL First name]** en **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_73.png)

1. Klik in het **[!UICONTROL Sorting]** venster op **[!UICONTROL Next]**: voor dit voorbeeld is geen sortering nodig .
1. Selecteer **[!UICONTROL Data filtering]** in **[!UICONTROL Filtering conditions]**.
1. In het **[!UICONTROL Target element]** venster, plaats een filtervoorwaarde om ontvangers te verzamelen die Engels spreken.

   ![](assets/query_editor_nveau_74.png)

1. Klik in het **[!UICONTROL Data formatting]** venster op **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. Ga naar het **[!UICONTROL Type]** venster van het **[!UICONTROL Export calculated field definition]** venster en selecteer **[!UICONTROL Enumerations]**.

   Definieer de kolom waarnaar het nieuwe berekende veld moet verwijzen. Selecteer hiertoe de **[!UICONTROL Gender]** kolom in het keuzemenu van het **[!UICONTROL Source column]** veld: de doelwaarden komen overeen met de **[!UICONTROL Gender]** kolom.

   ![](assets/query_editor_nveau_76.png)

   Definieer de waarden voor **Bron** en **Doel** : de bestemmingswaarde maakt het vraagresultaat gemakkelijker te lezen. Deze vraag zou ontvankelijk geslacht moeten terugkeren en het resultaat zal of 0, 1, of 2 zijn.

   Voor elke &quot;bron-bestemming&quot;lijn die moet worden ingegaan, klik **[!UICONTROL Add]** in **[!UICONTROL List of enumeration values]**:

   * Voer in de **[!UICONTROL Source]** kolom de bronwaarde voor elk geslacht (0,1,2) in een nieuwe regel in.
   * Voer in de **[!UICONTROL Destination]** kolom de waarden in: &quot;Niet aangegeven&quot; voor regel &quot;0&quot;, &quot;Mannelijk&quot; voor regel &quot;1&quot; en &quot;Vrouwelijk&quot; voor regel &quot;2&quot;.
   Selecteer de **[!UICONTROL Keep the source value]** functie.

   Klik **[!UICONTROL OK]** om het berekende veld goed te keuren.

   ![](assets/query_editor_nveau_77.png)

1. Klik in het **[!UICONTROL Data formatting]** venster op **[!UICONTROL Next]**.
1. In het voorvertoningsvenster **[!UICONTROL start the preview of the data]**.

   De aanvullende kolom definieert het geslacht van 0, 1 en 2:

   * 0 voor &quot;Niet aangegeven&quot;
   * 1 voor &quot;Mannelijk&quot;
   * 2 voor &quot;Vrouwelijk&quot;
   ![](assets/query_editor_nveau_78.png)

   Als u bijvoorbeeld geen geslacht &quot;2&quot; opgeeft in het veld **[!UICONTROL List of enumeration values]** en de **[!UICONTROL Generate a warning and continue]** functie van het **[!UICONTROL In other cases]** veld is geselecteerd, wordt een waarschuwingslogboek weergegeven. Dit logbestand geeft aan dat geslacht &quot;2&quot; (vrouwelijk) niet is ingevoerd. Deze wordt weergegeven in het **[!UICONTROL Logs generated during export]** veld van het venster met gegevensvoorvertoning.

   ![](assets/query_editor_nveau_79.png)

   Neem een ander voorbeeld en zeg dat de opsommingswaarde &quot;2&quot;niet is ingegaan. Selecteer de **[!UICONTROL Generate an error and reject the line]** functie: alle geslachten die onder &quot; 2 &quot; vallen , zullen anomalieën veroorzaken en de overige informatie op de regel ( voornaam en achternaam , enz . ) wordt niet geëxporteerd. Een foutenlogboek wordt getoond op het **[!UICONTROL Logs generated during export]** gebied van het venster van de gegevensvoorproef. Dit logboek wijst erop dat de opsommingswaarde &quot;2&quot;niet ingegaan is.

   ![](assets/query_editor_nveau_80.png)
