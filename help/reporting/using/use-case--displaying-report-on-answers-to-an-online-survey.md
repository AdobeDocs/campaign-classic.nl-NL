---
product: campaign
title: '"Gebruiksscenario: een rapport weergeven over antwoorden op een online enquête"'
description: '"Gebruiksscenario: een rapport weergeven over antwoorden op een online enquête"'
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
exl-id: 6be12518-86d1-4a13-bbc2-b2ec5141b505
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 5%

---

# Hoofdlettergebruik: een rapport weergeven over antwoorden op een online enquête{#use-case-displaying-report-on-answers-to-an-online-survey}

Antwoorden op Adobe Campaign-enquêtes kunnen worden verzameld en geanalyseerd met behulp van speciale rapporten.

In het volgende voorbeeld willen we antwoorden verzamelen op een online enquête en deze weergeven in een draaientabel

Voer de volgende stappen uit:

1. Een workflow maken om antwoorden op de enquête te herstellen en deze op te slaan in een lijst.
1. Een kubus maken met de gegevens in de lijst.
1. Een rapport maken met de draaitabel en de indeling van de antwoorden weergeven.

Voordat u met dit gebruiksgeval begint, hebt u toegang nodig tot een enquête en een reeks antwoorden die u kunt analyseren.

>[!NOTE]
>
>Dit gebruiksgeval kan slechts worden uitgevoerd als u **de optie van de Manager van het Onderzoek** hebt verworven. Controleer hiervoor uw licentieovereenkomst.

## Stap 1 - Het creëren van de gegevensinzameling en de opslagwerkschema {#step-1---creating-the-data-collection-and-storage-workflow}

Voer de volgende stappen uit om de antwoorden op de enquête te verzamelen:

1. Maak een workflow en plaats een **[!UICONTROL Answers to a survey]**-activiteit. Raadpleeg [deze sectie](../../web/using/publish--track-and-use-collected-data.md#using-the-collected-data) voor meer informatie over het gebruik van deze activiteit.
1. Bewerk de activiteit en selecteer de enquête waarvan u de antwoorden wilt analyseren.
1. Schakel de optie **[!UICONTROL Select all the answer data]** in om alle informatie te verzamelen.

   ![](assets/reporting_usecase_1_01.png)

1. Selecteer de kolommen die u wilt extraheren (in dit geval: selecteren: alle gearchiveerde velden. Dit zijn de velden die de antwoorden bevatten.

   ![](assets/reporting_usecase_1_02.png)

1. Zodra het vakje van de antwoordinzameling wordt gevormd, plaats **[!UICONTROL List update]** typeactiviteit om de gegevens te bewaren.

   ![](assets/reporting_usecase_1_04.png)

   Geef in deze activiteit de lijst op die moet worden bijgewerkt en schakel de optie **[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]** uit: antwoorden worden toegevoegd aan de bestaande tabel. Met deze optie kunt u verwijzen naar de lijst in een kubus. Het schema dat aan de lijst wordt gekoppeld, wordt niet opnieuw gegenereerd voor elke update. Dit garandeert de integriteit van de kubus die deze lijst gebruikt.

   ![](assets/reporting_usecase_1_03.png)

1. Start de workflow om de configuratie ervan te bevestigen.

   ![](assets/reporting_usecase_1_05.png)

   De gespecificeerde lijst wordt gecreeerd en omvat het schema van de antwoorden aan het onderzoek.

1. Voeg een planner toe om de dagelijkse inzameling van antwoorden en de lijstupdate te automatiseren.

   De **[!UICONTROL List update]**- en **[!UICONTROL Scheduler]**-activiteiten worden beschreven in .

## Stap 2 - Het creëren van de kubus, zijn maatregelen en zijn indicatoren {#step-2---creating-the-cube--its-measures-and-its-indicators}

U kunt dan de kubus tot stand brengen en zijn maatregelen vormen: zij zullen worden gebruikt om de indicatoren te creëren die in het verslag zullen worden getoond . Raadpleeg [Informatie over kubussen](../../reporting/using/about-cubes.md) voor meer informatie over het maken en configureren van kubussen.

In dit voorbeeld is de kubus gebaseerd op de gegevens in de lijst die worden gevoed door de eerder gemaakte workflow.

![](assets/reporting_usecase_2_01.png)

Definieer de afmetingen en de maatregelen die in het rapport moeten worden weergegeven. Hier willen we de contractdatum en het land van de geënquêteerde weergeven.

![](assets/reporting_usecase_2_02.png)

Met het tabblad **[!UICONTROL Preview]** kunt u de rendering van het rapport beheren.

## Stap 3 - het creëren van het rapport en het vormen van de gegevenslay-out binnen de lijst {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

U kunt dan een rapport creëren dat op deze kubus wordt gebaseerd en de gegevens en de informatie verwerken.

![](assets/reporting_usecase_3_01.png)

Pas de informatie aan om weer te geven op basis van uw behoeften.

![](assets/reporting_usecase_3_02.png)
