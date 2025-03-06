---
product: campaign
title: Gegevensextractie (bestand)
description: Meer informatie over de activiteit van de gegevensextractie-workflow (bestand)
feature: Workflows, Data Management Activity
hide: true
hidefromtoc: true
exl-id: 06eafedd-6386-498f-a80d-7f57ddcccad6
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---

# Gegevensextractie (bestand){#extraction-file}



U kunt gegevens uit een workflowtabel in een extern bestand extraheren met de activiteit **[!UICONTROL Data extraction (file)]** .

>[!CAUTION]
>
>Deze activiteit moet altijd een binnenkomende overgang hebben die de te halen gegevens bevat.

Voer de volgende stappen uit om gegevensextractie te configureren:

1. Geef de naam van het uitvoerbestand op: deze naam kan variabelen bevatten die met de aanpassingsknop rechts van het veld worden ingevoegd.
1. Klik op **[!UICONTROL Edit the file format...]** om de gegevens te selecteren die u wilt extraheren.

   ![](assets/s_advuser_extract_file_param.png)

   Met de optie **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** voegt u een extra stap toe om het uiteindelijke resultaat van het aggregaat te filteren, bijvoorbeeld op een bepaald type inkooporder, klanten die meer dan tien keer hebben besteld, enz.

1. Indien nodig kunt u nieuwe kolommen aan het uitvoerbestand toevoegen, zoals bijvoorbeeld berekeningen of verwerkingsresultaten. Klik hiertoe op het pictogram **[!UICONTROL Add]** .

   ![](assets/s_advuser_extract_file_add_col.png)

   Klik op de extra regel op het pictogram **[!UICONTROL Edit expression]** om de inhoud van de nieuwe kolom te definiëren.

   ![](assets/s_advuser_extract_file_add_exp.png)

   Vervolgens opent u het selectievenster. Klik op **[!UICONTROL Advanced selection]** om het proces te kiezen dat op de gegevens moet worden toegepast.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Kies de gewenste formule in de lijst.

   ![](assets/s_advuser_extract_file_agregate_values.png)

U kunt een postproces bepalen dat tijdens de gegevensextractie wordt uitgevoerd, toestaand u om de dossiers te zip of te coderen. Hiervoor moet de gewenste opdracht worden toegevoegd op het tabblad **[!UICONTROL Script]** van de activiteit.

Voor meer op dit, verwijs naar deze sectie: [ het Zippen of het coderen van een dossier ](../../platform/using/zip-encrypt.md)

![](assets/postprocessing_dataextraction.png)

## Lijst van geaggregeerde functies {#list-of-aggregate-functions}

Hieronder volgt een lijst met beschikbare statistische functies:

* **[!UICONTROL Count]** alle waarden te tellen die niet gelijk zijn aan null van het veld dat moet worden samengevoegd, inclusief dubbele waarden (van het geaggregeerde veld);

  **[!UICONTROL Distinct]** om het totale aantal verschillende en niet-null waarden van het veld te tellen dat moet worden geaggregeerd (dubbele waarden worden vóór de berekening uitgesloten),

* **[!UICONTROL Sum]** om de som van waarden van een numeriek veld te berekenen,
* **[!UICONTROL Minimum value]** voor het berekenen van de minimumwaarden van een veld (numeriek of anderszins);
* **[!UICONTROL Maximum value]** voor het berekenen van de maximumwaarden van een veld (numeriek of anderszins);
* **[!UICONTROL Average]** om het gemiddelde van de waarden van een numeriek veld te berekenen.
