---
product: campaign
title: Kubussen
description: Aan de slag met kubussen
feature: Reporting, Monitoring
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
hide: true
hidefromtoc: true
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---

# Aan de slag met kubussen{#about-cubes}



## Terminologie {#terminology}

De specifieke termijnen wanneer het werken met kubussen worden hieronder vermeld.

* **Kubus** - Een kubus is een weergave van multidimensionale informatie: het biedt eindgebruikers structuren die ontworpen zijn voor interactieve gegevensanalyse.

* **Feitentabel/schema** - De tabel met feiten (of het feitelijke schema) bevat de onbewerkte of elementaire gegevens waarop analyses worden gebaseerd. Dit zijn hoofdzakelijk grote volumelijsten (misschien met verbonden lijsten) met potentieel lange berekeningen. Een tabel met feiten kan bijvoorbeeld de volgende zijn: de tabel voor het uitzenden, de tabel voor aankopen, enzovoort.

* **Dimension** - Met Dimensionen kunt u gegevens segmenteren in groepen: zodra ze zijn gemaakt, dienen ze als analysegassen. In de meeste gevallen zullen voor een bepaalde dimensie verschillende niveaus worden vastgesteld. Voor een tijdsdimensie zijn de niveaus bijvoorbeeld maanden, dagen, uren, minuten, enzovoort. Deze reeks niveaus vertegenwoordigt de dimensiehiërarchie en laat diverse niveaus van gegevensanalyse toe.

* **Binding** - Voor sommige velden kunt u binden aan groepswaarden definiëren en het gemakkelijker maken om informatie te lezen. Binding wordt toegepast op niveaus. Wij adviseren dat u het binden bepaalt wanneer er een mogelijkheid van vele verschillende waarden is.

* **Meetlat** - De meest voorkomende maatregelen zijn som, gemiddelde, maximum, minimum, standaardafwijking enz. De maatregelen kunnen worden berekend: het aanvaardingspercentage van een aanbieding is bijvoorbeeld de verhouding tussen het aantal ingediende aanbiedingen en het aantal aanvaarde inschrijvingen.

## De werkruimte Kubus {#cube-workspace}

De kubussen worden opgeslagen in de **[!UICONTROL Administration > Configuration > Cubes]** knooppunt.

![](assets/s_advuser_cube_node.png)

De belangrijkste gebruikscontext voor kubussen is als volgt:

* De uitvoer van gegevens kan rechtstreeks in een rapport worden uitgevoerd, dat in **[!UICONTROL Reports]** van het Adobe Campaign-platform.

  Hiertoe maakt u een nieuw rapport en selecteert u de kubus die u wilt gebruiken.

  ![](assets/cube_create_new.png)

  De kubussen verschijnen als malplaatjes die op welke rapporten worden gebaseerd worden gecreeerd. Als u een sjabloon hebt gekozen, klikt u op **[!UICONTROL Create]** om het passende rapport te vormen en te bekijken.

  U kunt maatregelen aanpassen, de vertoningswijze veranderen of de lijst vormen, dan het rapport tonen gebruikend de belangrijkste knoop.

  ![](assets/cube_display_new.png)

* U kunt ook naar een kubus verwijzen in het dialoogvenster **[!UICONTROL Query]** vak van een rapport waarin de indicatoren worden gebruikt, zoals hieronder aangegeven:

  ![](assets/s_advuser_query_using_a_cube.png)

* U kunt een spillijst ook opnemen die op een kubus wordt gebaseerd in om het even welke pagina van een rapport. Hiervoor verwijst u naar de kubus die moet worden gebruikt in het dialoogvenster **[!UICONTROL Data]** tabblad van de draaitabel op de desbetreffende pagina.

  ![](assets/s_advuser_cube_in_report.png)

  Raadpleeg voor meer informatie hierover [De gegevens in een rapport verkennen](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
