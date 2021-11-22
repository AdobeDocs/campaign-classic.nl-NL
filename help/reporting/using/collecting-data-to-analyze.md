---
product: campaign
title: Data verzamelen om te analyseren
description: Data verzamelen om te analyseren
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: cf621374-88f9-4def-8bea-87e0ea69ecd3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 3%

---

# Data verzamelen om te analyseren{#collecting-data-to-analyze}

![](../../assets/common.svg)

De gegevens die voor de bouw van het rapport moeten worden gebruikt kunnen direct in de rapportpagina worden geselecteerd (voor meer op dit, verwijs naar [De context gebruiken](../../reporting/using/using-the-context.md)) of via een of meer query&#39;s worden verzameld.

Deze activiteit biedt drie verschillende methodes aan:

1. Een query maken met de gegevens in de database.
1. De gegevens in een lijst verwerken.
1. Gegevens in een bestaande kubus gebruiken.

De keuze van de methode hangt af van het type berekening, het gegevensvolume en de duurzaamheid ervan, enz. Al deze parameters moeten zorgvuldig worden onderzocht om overbelasting van de Adobe Campaign-database te voorkomen en om het genereren en manipuleren van de gemaakte rapporten te optimaliseren. Raadpleeg [deze pagina](../../reporting/using/best-practices.md#optimizing-report-creation) voor meer informatie.

In alle gevallen worden gegevens verzameld via een **[!UICONTROL Query]** type activiteit.

![](assets/reporting_query_edit.png)

Deze wijze van de gegevensselectie is relevant wanneer de gegevens in het rapport moeten worden verzameld of worden gebouwd gebruikend gegevens in het gegevensbestand. In sommige gevallen kunt u de gegevens ook rechtstreeks selecteren uit de elementen die in het rapport worden gebruikt. Als u bijvoorbeeld een grafiek invoegt, kunt u de brongegevens rechtstreeks selecteren. Raadpleeg voor meer informatie hierover [De context gebruiken](../../reporting/using/using-the-context.md).

## De gegevens van een schema gebruiken {#using-the-data-from-a-schema}

Om gegevens te gebruiken verbonden aan een gegevensbestandschema, selecteer de aangewezen optie in de vraagredacteur en vorm de vraag die moet worden toegepast.

In het volgende voorbeeld kunt u het aantal ontvangers voor elk land verzamelen, onder de profielen in de database. Ze kunnen vervolgens in een rapport in de vorm van een tabel worden weergegeven.

![](assets/reporting_query_from_schema.png)

## Een geïmporteerde lijst gebruiken {#using-an-imported-list}

Als u een rapport wilt maken, kunt u gegevens uit een lijst met geïmporteerde gegevens gebruiken.

Selecteer hiervoor de optie **[!UICONTROL Use an imported list]** in het vraagvakje en selecteer de betrokken lijst.

![](assets/reporting_query_from_list.png)

Klik op de knop **[!UICONTROL Edit query...]** koppeling om de gegevens te definiëren die moeten worden verzameld onder de elementen in deze lijst voor het samenstellen van het rapport.

## Een kubus gebruiken {#using-a-cube}

Het is mogelijk om een kubus voor het bepalen van de vraag te selecteren.

![](assets/reporting_query_from_cube.png)

Met behulp van kubussen kunt u de exploratie- en analysemogelijkheden van de database uitbreiden en tegelijkertijd de configuratie van rapporten en tabellen voor eindgebruikers vereenvoudigen: Selecteer eenvoudig een bestaande, volledig gevormde kubus en gebruik zijn berekeningen, maatregelen en statistieken. Voor meer informatie over het maken van kubussen raadpleegt u [deze sectie](../../reporting/using/about-cubes.md).

Klik op de knop **[!UICONTROL Edit query...]** en selecteer de indicatoren die u in uw rapport wilt tonen of gebruiken.

![](assets/reporting_query_from_cube_edit_query.png)

## Filteropties in de query&#39;s {#filtering-options-in-the-queries}

Om het runnen van vragen over het volledige gegevensbestand te vermijden, moeten de gegevens worden gefiltreerd.

### Vereenvoudigd filter {#simplified-filter}

U kunt de **[!UICONTROL Filter automatically with the context]** optie om het rapport toegankelijk te maken via een specifiek knooppunt van de boomstructuur, zoals een lijst, een ontvanger of een levering.

De **[!UICONTROL Filter with the folder]** Met deze optie kunt u een map opgeven en alleen de inhoud ervan in aanmerking nemen. Hiermee kunt u de rapportgegevens filteren, zodat alleen de gegevens uit een van de mappen in de structuur worden weergegeven, zoals hieronder wordt getoond:

![](assets/reporting_control_folder.png)

### De hoeveelheid verzamelde gegevens beperken {#limiting-the-amount-of-data-collected}

Vorm het aantal verslagen dat via de vraag moet worden gehaald gebruikend de resultaat beperkende opties:

* **[!UICONTROL Limit to first record]** om één resultaat te extraheren,
* **[!UICONTROL Size]** om een ingesteld aantal records te extraheren.
