---
product: campaign
title: Kubussen
description: Aan de slag met kubussen
feature: Reporting
hide: true
hidefromtoc: true
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 2665ea2ba67a0ca2a4beb0b076543b3245acbebb
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 2%

---

# Aan de slag met kubussen{#about-cubes}

![](../../assets/common.svg)

## Terminologie {#terminology}

De specifieke termijnen wanneer het werken met kubussen worden hieronder vermeld.

* **Kubus** - Een kubus is een weergave van multidimensionale informatie: het biedt eindgebruikers structuren die ontworpen zijn voor interactieve gegevensanalyse .

* **Feitentabel/schema** - De tabel met feiten (of het feitelijke schema) bevat de onbewerkte of elementaire gegevens waarop analyses worden gebaseerd. Dit zijn hoofdzakelijk grote volumelijsten (misschien met verbonden lijsten) met potentieel lange berekeningen. Een feitentabel kan bijvoorbeeld: de omroeptabel, de aankooptabel, enz.

* **Dimension** - Met Dimension kunt u gegevens segmenteren in groepen: zodra zij zijn gecreëerd , dienen de afmetingen als analysecentra . In de meeste gevallen zullen voor een bepaalde dimensie verschillende niveaus worden vastgesteld. Voor een tijdsdimensie zijn de niveaus bijvoorbeeld maanden, dagen, uren, minuten, enzovoort. Deze reeks niveaus vertegenwoordigt de dimensiehiërarchie en laat diverse niveaus van gegevensanalyse toe.

* **Binding** - Voor sommige velden kunt u binden aan groepswaarden definiëren en het gemakkelijker maken om informatie te lezen. Binding wordt toegepast op niveaus. Wij adviseren dat u het binden bepaalt wanneer er een mogelijkheid van vele verschillende waarden is.

* **Meetlat** - De meest voorkomende maatregelen zijn som, gemiddelde, maximum, minimum, standaardafwijking enz. De maatregelen kunnen worden berekend: zo is het aanvaardingspercentage van een aanbieding bijvoorbeeld de verhouding tussen het aantal ingediende aanbiedingen en het aantal aanvaarde inschrijvingen .

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
