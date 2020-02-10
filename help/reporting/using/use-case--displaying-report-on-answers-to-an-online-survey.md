---
title: '"Hoofdlettergebruik: rapport weergeven over antwoorden op een online enquête"'
seo-title: '"Hoofdlettergebruik: rapport weergeven over antwoorden op een online enquête"'
description: '"Hoofdlettergebruik: rapport weergeven over antwoorden op een online enquête"'
seo-description: null
page-status-flag: never-activated
uuid: 2c0a5b7d-c606-4bcb-9600-8f89e6fce32a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: 5404a227-6cfb-463b-9a56-af46a022eb38
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Hoofdlettergebruik: rapport weergeven over antwoorden op een online enquête{#use-case-displaying-report-on-answers-to-an-online-survey}

Antwoorden op Adobe Campagne-enquêtes kunnen worden verzameld en geanalyseerd met behulp van speciale rapporten.

In het volgende voorbeeld willen we antwoorden verzamelen op een online enquête en deze weergeven in een draaientabel

Voer de volgende stappen uit:

1. Een workflow maken om antwoorden op de enquête te herstellen en deze op te slaan in een lijst.
1. Een kubus maken met de gegevens in de lijst.
1. Een rapport maken met de draaitabel en de indeling van de antwoorden weergeven.

Voordat u met dit gebruiksgeval begint, hebt u toegang nodig tot een enquête en een reeks antwoorden die u kunt analyseren.

>[!NOTE]
>
>Dit gebruiksgeval mag alleen worden geïmplementeerd als u de optie **Beoordelingsmanager** hebt verkregen. Controleer uw licentieovereenkomst.

## Stap 1 - Het creëren van de gegevensinzameling en de opslagwerkschema {#step-1---creating-the-data-collection-and-storage-workflow}

Voer de volgende stappen uit om de antwoorden op de enquête te verzamelen:

1. Maak een workflow en plaats een **[!UICONTROL Answers to a survey]** activiteit. Raadpleeg [deze sectie](../../web/using/publish--track-and-use-collected-data.md#using-the-collected-data)voor meer informatie over het gebruik van deze activiteit.
1. Bewerk de activiteit en selecteer de enquête waarvan u de antwoorden wilt analyseren.
1. Schakel de **[!UICONTROL Select all the answer data]** optie in om alle informatie te verzamelen.

   ![](assets/reporting_usecase_1_01.png)

1. Selecteer de kolommen die u wilt extraheren (in dit geval: selecteren: alle gearchiveerde velden. Dit zijn de velden die de antwoorden bevatten.

   ![](assets/reporting_usecase_1_02.png)

1. Zodra het vakje van de antwoordinzameling wordt gevormd, plaats een **[!UICONTROL List update]** typeactiviteit om de gegevens te bewaren.

   ![](assets/reporting_usecase_1_04.png)

   Geef in deze activiteit de lijst op die moet worden bijgewerkt en schakel de **[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]** optie uit: antwoorden worden toegevoegd aan de bestaande tabel. Met deze optie kunt u verwijzen naar de lijst in een kubus. Het schema dat aan de lijst wordt gekoppeld, wordt niet opnieuw gegenereerd voor elke update. Dit garandeert de integriteit van de kubus die deze lijst gebruikt.

   ![](assets/reporting_usecase_1_03.png)

1. Start de workflow om de configuratie ervan te bevestigen.

   ![](assets/reporting_usecase_1_05.png)

   De gespecificeerde lijst wordt gecreeerd en omvat het schema van de antwoorden aan het onderzoek.

1. Voeg een planner toe om de dagelijkse inzameling van antwoorden en de lijstupdate te automatiseren.

   De **[!UICONTROL List update]** en de **[!UICONTROL Scheduler]** activiteiten worden nader toegelicht in .

## Stap 2 - De kubus, de maatregelen en de indicatoren ervan maken {#step-2---creating-the-cube--its-measures-and-its-indicators}

U kunt dan de kubus tot stand brengen en zijn maatregelen vormen: zij zullen worden gebruikt om de indicatoren te creëren die in het verslag zullen worden getoond . Voor meer bij het creëren van en het vormen van kubussen, verwijs naar [Ongeveer kubussen](../../reporting/using/about-cubes.md).

In dit voorbeeld is de kubus gebaseerd op de gegevens in de lijst die worden gevoed door de eerder gemaakte workflow.

![](assets/reporting_usecase_2_01.png)

Definieer de afmetingen en de maatregelen die in het rapport moeten worden weergegeven. Hier willen we de contractdatum en het land van de geënquêteerde weergeven.

![](assets/reporting_usecase_2_02.png)

Op het **[!UICONTROL Preview]** tabblad kunt u de rendering van het rapport bepalen.

## Stap 3 - het creëren van het rapport en het vormen van de gegevenslay-out binnen de lijst {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

U kunt dan een rapport creëren dat op deze kubus wordt gebaseerd en de gegevens en de informatie verwerken.

![](assets/reporting_usecase_3_01.png)

Pas de informatie aan om weer te geven op basis van uw behoeften.

![](assets/reporting_usecase_3_02.png)

