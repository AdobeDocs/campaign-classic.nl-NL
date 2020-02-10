---
title: Gegevens uitnemen (bestand)
description: Meer informatie over de activiteit van de gegevensextractie-workflow (bestand).
page-status-flag: never-activated
uuid: c1e3fde3-183c-4602-9cef-760e4648fcf7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: fe4e6f64-eb0a-44bc-8221-6c9bfb99871f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5eb82bb5dae589cb18d42695565b25dad36006bd

---


# Gegevens uitnemen (bestand){#extraction-file}

U kunt gegevens uit een werkstroomtabel in een extern bestand extraheren met behulp van de **[!UICONTROL Data extraction (file)]** activiteit.

>[!CAUTION]
>
>Deze activiteit moet altijd een binnenkomende overgang hebben die de te halen gegevens bevat.

Voer de volgende stappen uit om gegevensextractie te configureren:

1. Geef de naam van het uitvoerbestand op: deze naam kan variabelen bevatten die via de verpersoonlijkingsknoop rechts van het gebied worden opgenomen.
1. Klik **[!UICONTROL Edit the file format...]** om de gegevens te selecteren die u wilt extraheren.

   ![](assets/s_advuser_extract_file_param.png)

   De **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** optie voegt een extra stap toe om het uiteindelijke resultaat van het aggregaat te filteren, bijvoorbeeld op een bepaald type inkooporder, klanten die meer dan tien keer hebben besteld, enz.

1. Indien nodig kunt u nieuwe kolommen aan het uitvoerbestand toevoegen, zoals bijvoorbeeld berekeningen of verwerkingsresultaten. Klik hiertoe op het **[!UICONTROL Add]** pictogram

   ![](assets/s_advuser_extract_file_add_col.png)

   Klik op de extra regel op het **[!UICONTROL Edit expression]** pictogram om de inhoud van de nieuwe kolom te definiëren.

   ![](assets/s_advuser_extract_file_add_exp.png)

   Vervolgens opent u het selectievenster. Klik **[!UICONTROL Advanced selection]** om het proces te kiezen dat op de gegevens moet worden toegepast.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Kies de gewenste formule in de lijst.

   ![](assets/s_advuser_extract_file_agregate_values.png)

## Lijst van geaggregeerde functies {#list-of-aggregate-functions}

Hieronder volgt een lijst met beschikbare statistische functies:

* **[!UICONTROL Count]** alle niet-null-waarden van het veld te tellen, met inbegrip van dubbele waarden (van het geaggregeerde veld);

   **[!UICONTROL Distinct]** het totale aantal verschillende en niet-nulwaarden van het veld dat moet worden geaggregeerd (dubbele waarden worden vóór de berekening buiten beschouwing gelaten);

* **[!UICONTROL Sum]** de som van de waarden van een numeriek veld te berekenen;
* **[!UICONTROL Minimum value]** de minimumwaarden van een veld (numeriek of anderszins) te berekenen;
* **[!UICONTROL Maximum value]** de maximumwaarden van een veld (numeriek of anderszins) te berekenen;
* **[!UICONTROL Average]** het gemiddelde van de waarden van een numeriek veld te berekenen.

