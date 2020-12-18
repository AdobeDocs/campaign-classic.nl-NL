---
solution: Campaign Classic
product: campaign
title: Kubussen
description: Kubussen
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 10%

---


# Kubussen{#about-cubes}

De exploratie van gegevens in het gegevensbestand wordt aangeboden via **de Analytics van de Marketing** module. Het laat u toe om gegevens te analyseren en te meten, statistieken te berekenen, en rapportverwezenlijking en berekening te vereenvoudigen en te optimaliseren. Daarnaast kunt u met Marketing Analytics rapporten maken en doelpopulaties maken. Zodra deze worden geïdentificeerd, worden zij opgeslagen in lijsten die in Adobe Campaign (gericht, segmentatie, enz.) kunnen worden gebruikt.

De kubussen worden gebruikt voor het produceren van bepaalde ingebouwde rapporten, met inbegrip van leveringsrapporten (levering het volgen, klikt, opent, enz.). Rapporten op basis van kubussen mogen alleen worden gebruikt als standaard voor gegevensvolumes onder 5 miljoen feitenlijnen.

U kunt de mogelijkheden van databaseverkenning en -analyse uitbreiden terwijl het voor eindgebruikers gemakkelijker wordt om rapporten en tabellen te configureren. Alles wat gebruikers moeten doen is een bestaande (volledig geconfigureerde) kubus selecteren bij het maken van hun rapport of tabel om berekeningen, metingen en statistieken te verwerken.

Zodra kubussen zijn gemaakt en geconfigureerd, worden ze gebruikt in vakken voor rapportquery’s en webapplicaties. Ze kunnen worden gebruikt en bewerkt binnen draaitabellen.

>[!CAUTION]
>
>**Marketing** Analytics en Adobe Campaign module. Het moet op uw instantie worden geïnstalleerd zodat u de hieronder beschreven mogelijkheden kunt gebruiken.

Met de module van de Analyse van de Marketing, laat de Campagne u toe:

1. Kubussen maken met het oog op:

   * gegevens samenvoegen en opslaan in een werktabel om indicatoren vooraf te berekenen op basis van gebruikersbehoeften;
   * vermindering van de hoeveelheid gegevens die betrokken is bij de verschillende berekeningen die voor rapporten en vragen worden gebruikt, waardoor de berekeningstijden van de indicatoren aanzienlijk worden geoptimaliseerd;
   * het vereenvoudigen van de toegang tot gegevens, waardoor gebruikers gegevens (al dan niet vooraf geaggregeerd) kunnen manipuleren, afhankelijk van verschillende dimensies.

   Raadpleeg [Indicatoren maken](../../reporting/using/creating-indicators.md) voor meer informatie.

1. Draai-tabellen maken met de volgende weergave:

   * het verkennen van berekende gegevens, geconfigureerde maatregelen;
   * selecteren van de gegevens die moeten worden weergegeven en de weergavemodus;
   * aanpassing van de gebruikte maatregelen en indicatoren;
   * het aanbieden van interactieve analysehulpmiddelen aan gebruikers met een niet-technische achtergrond.

   Voor meer op dit, verwijs naar [Gebruikend kubussen om gegevens](../../reporting/using/using-cubes-to-explore-data.md) te onderzoeken.

1. Bouw een vraag gebruikend gegevens die in een kubus worden berekend en worden samengevoegd.
1. Identificeer populaties en verwijs hen in lijsten.

## Terminologie {#terminology}

Wanneer het werken met kubussen, moeten de volgende concepten gekend zijn:

* Kubus

   Een kubus is een weergave van multidimensionale informatie: het biedt eindgebruikers structuren die ontworpen zijn voor interactieve gegevensanalyse .

* Feitentabel/schema

   De tabel met feiten (of het feitelijke schema) bevat de onbewerkte of elementaire gegevens waarop analyses worden gebaseerd. Dit zijn hoofdzakelijk grote volumelijsten (misschien met verbonden lijsten) met potentieel lange berekeningen.

   Een feitentabel kan bijvoorbeeld: de omroeptabel, de aankooptabel, enz.

* Dimension

   Met Dimension kunt u gegevens segmenteren in groepen: zodra zij zijn gecreëerd , dienen de afmetingen als analysecentra . In de meeste gevallen zullen voor een bepaalde dimensie verschillende niveaus worden vastgesteld. Voor een tijdsdimensie zijn de niveaus bijvoorbeeld maanden, dagen, uren, minuten, enzovoort. Deze reeks niveaus vertegenwoordigt de dimensiehiërarchie en laat diverse niveaus van gegevensanalyse toe.

* Binding

   Voor sommige velden kunt u binding met groepswaarden definiëren en het gemakkelijker maken om informatie te lezen. Binding wordt toegepast op niveaus

   Wij adviseren dat u het binden bepaalt wanneer er een mogelijkheid van vele verschillende waarden is.

* Meetlat

   De meest voorkomende maatregelen zijn som, gemiddelde, maximum, minimum, standaardafwijking enz.

   De maatregelen kunnen worden berekend: zo is het aanvaardingspercentage van een aanbieding bijvoorbeeld de verhouding tussen het aantal ingediende aanbiedingen en het aantal aanvaarde inschrijvingen .

## Kubus-werkruimte {#cube-workspace}

De kubussen worden opgeslagen in de **[!UICONTROL Administration > Configuration > Cubes]** knoop.

![](assets/s_advuser_cube_node.png)

De belangrijkste gebruikscontext voor kubussen is als volgt:

* De uitvoer van gegevens kan direct in een rapport worden uitgevoerd, dat in het **[!UICONTROL Reports]** universum van het platform van Adobe Campaign wordt ontworpen.

   Hiertoe maakt u een nieuw rapport en selecteert u de kubus die u wilt gebruiken.

   ![](assets/cube_create_new.png)

   De kubussen verschijnen als malplaatjes die op welke rapporten worden gebaseerd worden gecreeerd. Nadat u een sjabloon hebt gekozen, klikt u op **[!UICONTROL Create]** om het bijbehorende rapport te configureren en weer te geven.

   U kunt maatregelen aanpassen, de vertoningswijze veranderen of de lijst vormen, dan het rapport tonen gebruikend de belangrijkste knoop.

   ![](assets/cube_display_new.png)

* U kunt ook naar een kubus in de doos **[!UICONTROL Query]** van een rapport verwijzen om zijn indicatoren, zoals hieronder getoond te gebruiken:

   ![](assets/s_advuser_query_using_a_cube.png)

* U kunt een spillijst ook opnemen die op een kubus wordt gebaseerd in om het even welke pagina van een rapport. Hiervoor verwijst u naar de kubus die u wilt gebruiken op het tabblad **[!UICONTROL Data]** van de draaitabel op de betreffende pagina.

   ![](assets/s_advuser_cube_in_report.png)

   Voor meer op dit, verwijs naar [Verkennend de gegevens in een rapport](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).

