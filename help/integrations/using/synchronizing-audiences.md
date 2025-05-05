---
product: campaign
title: Doelgroepen synchroniseren
description: Leer hoe te om publiek met Schakelaar ACS te synchroniseren
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 88e581cf-43cd-4c43-9347-d016c62fdf42
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 1%

---

# Doelgroepen synchroniseren{#synchronizing-audiences}



U kunt een geavanceerde lijst maken met de geavanceerde functies van Campagne v7 en deze lijst direct en in real time delen met Campaign Standard (inclusief extra gegevens), zonder problemen. Uw gebruiker van het Campaign Standard kan dan het publiek in Adobe Campaign Standard verbruiken.

Complexe gericht gebruiken van extra gegevens die niet in Campaign Standard worden herhaald kan slechts worden bereikt gebruikend Campagne v7.

U kunt lijsten van ontvangers of gegevens ook eenvoudig delen die door een schakelaar zoals de Dynamiek van Microsoft met Campaign Standard komen.

In dit geval ziet u hoe u het doel van uw levering in Campagne v7 voorbereidt en hoe u dit doel en de aanvullende gegevens ervan opnieuw kunt gebruiken in een levering die u met Adobe Campaign Standard hebt gemaakt en verzonden.

>[!NOTE]
>
>U kunt gegevens ook verrijken met aggregaten en verzamelingen in Adobe Campaign Standard als alle benodigde gegevens al zijn gerepliceerd.

## Vereisten {#prerequisites}

Hiervoor hebt u het volgende nodig:

* Ontvangers die zijn opgeslagen in de Campagne v7-database en zijn gesynchroniseerd met Campaign Standard. Zie de [Profielen synchroniseren](../../integrations/using/synchronizing-profiles.md) sectie.
* Aanvullende gegevens, zoals abonnementen of transacties die zijn opgeslagen in tabellen met betrekking tot namen:ontvangers in de Campagne v7-database. Deze gegevens kunnen uit de schema&#39;s OOB van de Campagne v7 of douanetabellen komen. Deze zijn standaard niet beschikbaar in het Campaign Standard omdat ze niet zijn gesynchroniseerd.
* Recht om werkschema&#39;s in zowel Campagne v7 als Campaign Standard uit te voeren.
* Recht om een levering in Campaign Standard tot stand te brengen en uit te voeren.

## Een doelworkflow met aanvullende gegevens maken in Campagne v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Complexe gericht gebruiken van extra gegevens die niet in Campaign Standard worden herhaald kan slechts worden bereikt gebruikend Campagne v7.

Zodra het doel en zijn extra gegevens worden bepaald, is het mogelijk om het als lijst op te slaan die met Campaign Standard kan worden gedeeld.

>[!NOTE]
>
>Dit is een voorbeeld. Afhankelijk van uw vereisten, kunt u eenvoudig een lijst van ontvangers vragen en het met ACS zonder enige verdere verwerking delen. U kunt ook andere gegevensbeheeractiviteiten gebruiken om uw uiteindelijke doel voor te bereiden.

Zo krijgt u het uiteindelijke publiek en de aanvullende gegevens:

1. Een nieuwe workflow maken op basis van **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Voeg een **[!UICONTROL Query]** en selecteer de ontvangers waarnaar u de laatste e-mail wilt verzenden. Bijvoorbeeld alle ontvangers tussen 18 en 30 jaar oud die in Frankrijk wonen.

   ![](assets/acs_connect_query1.png)

1. Voeg aanvullende gegevens toe vanuit de query. Raadpleeg voor meer informatie de [Gegevens toevoegen](../../workflow/using/query.md#adding-data) sectie.

   In dit voorbeeld ziet u hoe u een aggregaat toevoegt om te tellen hoeveel leveringen een ontvanger in een jaar heeft ontvangen.

   In de **[!UICONTROL Query]**, selecteert u **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. Selecteer **[!UICONTROL Data linked to the filtering dimension]** en klik op **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. Kies **[!UICONTROL Data linked to the filtering dimension]** en selecteert u vervolgens de **[!UICONTROL Recipient delivery logs]** knoop en klik **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. Selecteren **[!UICONTROL Aggregates]** in de **[!UICONTROL Data collected]** veld en klik op **[!UICONTROL Next]**.

   ![](assets/acs_connect_query5.png)

1. Voeg een het filtreren voorwaarde toe om rekening slechts logboeken te houden die tijdens de laatste 365 dagen werden gecreeerd en klik **[!UICONTROL Next]**.

   ![](assets/acs_connect_query6.png)

1. Geef de uitvoerkolommen op. Hier is de enige benodigde kolom die het aantal leveringen telt. Dat doet u als volgt:

   * Selecteren **[!UICONTROL Add]** rechts van het venster.
   * Van de **[!UICONTROL Select field]** venster, klikt u op **[!UICONTROL Advanced selection]**.
   * Selecteren **[!UICONTROL Aggregate]** vervolgens **[!UICONTROL Count]**. Controleer de **[!UICONTROL Distinct]** en klik op **[!UICONTROL Next]**.
   * Selecteer in de lijst met velden het veld dat wordt gebruikt voor de **Aantal** functie. Kies een veld dat altijd wordt gevuld, bijvoorbeeld het veld **[!UICONTROL Primary key]** en klik op **[!UICONTROL Finish]**.
   * De expressie in het dialoogvenster **[!UICONTROL Alias]** kolom. Met deze alias kunt u de toegevoegde kolom in de uiteindelijke aflevering gemakkelijk ophalen. Bijvoorbeeld **NBleveries**.
   * Klikken **[!UICONTROL Finish]** en sla de **[!UICONTROL Query]** activiteitenconfiguratie.

   ![](assets/acs_connect_query7.png)

1. Sla de workflow op. Het volgende gedeelte laat zien hoe u de populatie deelt met ACS.

## Doel delen met Campaign Standard {#share-the-target-with-campaign-standard}

Zodra de doelpopulatie wordt bepaald, kunt u het met ACS door delen **[!UICONTROL List update]** activiteit.

1. Voeg in de eerder gemaakte workflow een **[!UICONTROL List update]** en geeft u de lijst op die u wilt bijwerken of maken.

   Geef de map op waarin u de lijst wilt opslaan in Campagne v7. Lijsten zijn onderworpen aan de omslagafbeelding die tijdens de implementatie wordt bepaald, die hun zichtbaarheid kan beïnvloeden zodra zij in Campaign Standard worden gedeeld. Zie de [Omzetting van rechten](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) sectie.

1. Zorg ervoor dat de **[!UICONTROL Share with ACS]** is ingeschakeld. Deze optie is standaard ingeschakeld.

   ![](assets/acs_connect_listupdate1.png)

1. Sla de workflow op en voer deze uit.

   Het doel en de bijbehorende aanvullende gegevens worden opgeslagen in een lijst in Campagne v7 en worden direct gedeeld als een lijstpubliek in Campaign Standard. Alleen de profielen die zijn gerepliceerd, worden gedeeld met ACS.

Als er een fout optreedt op het tabblad **[!UICONTROL List update]** activiteit, betekent het dat de synchronisatie met Campaign Standard kan ontbroken hebben. Ga naar **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Deze map bevat synchronisatieworkflows die worden geactiveerd door de **[!UICONTROL List update]** activiteit uitvoeren. Zie de [Het oplossen van problemen de Schakelaar ACS](../../integrations/using/troubleshooting-the-acs-connector.md) sectie.

## Haal de gegevens op in het Campaign Standard en gebruik deze bij levering {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Wanneer de doelworkflow in Campagne v7 is uitgevoerd, kunt u het publiek van de lijst in de modus Alleen-lezen vinden in het menu **[!UICONTROL Audiences]** menu van Campaign Standard.

![](assets/acs_connect_deliveryworkflow_audience.png)

Door een leveringswerkschema in Campaign Standard te creëren, is het dan mogelijk om dit publiek evenals de extra gegevens te gebruiken die het in een levering bevat.

1. Een nieuwe workflow maken op basis van de **[!UICONTROL Marketing activities]** -menu.
1. Voeg een **[!UICONTROL Read audience]** en selecteer het publiek dat u eerder hebt gedeeld vanuit Campagne v7.

   Deze activiteit wordt gebruikt om de gegevens van het geselecteerde publiek terug te winnen. U kunt ook een extra **[!UICONTROL Source Filtering]** indien nodig door het tabblad volgens van deze activiteit te gebruiken.

1. Een **[!UICONTROL Email delivery]** activiteit en vorm het als andere [e-mailleveringsactiviteit](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html?lang=nl-NL).
1. Open de leveringsinhoud.
1. Een personalisatieveld toevoegen. Zoek vanuit de pop-up de **[!UICONTROL Additional data (targetData)]** knooppunt. Dit knooppunt bevat de aanvullende gegevens van het publiek die zijn berekend in de initiële doelworkflow. U kunt ze als elk ander verpersoonlijkingsveld gebruiken.

   In dit voorbeeld zijn de aanvullende gegevens die afkomstig zijn van de oorspronkelijke doelworkflow het aantal leveringen dat in de laatste 365 dagen aan elke ontvanger is verzonden. De alias NBDeliies die is opgegeven in de doelworkflow is hier zichtbaar.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Sla de levering en de workflow op.

   De workflow kan nu worden uitgevoerd. De levering wordt geanalyseerd en kan worden verzonden.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Uw levering verzenden en controleren {#send-and-monitor-your-delivery}

Zodra de levering en zijn inhoud klaar zijn, verzend de levering:

1. Voer de leveringswerkstroom uit. Met deze stap wordt het e-mailbericht voorbereid voor verzending.
1. Van het leveringsdashboard, bevestig manueel dat de levering kan worden verzonden.
1. Controleer de rapporten en logboeken van de levering:

   * **In Campaign Standard**: Toegang [rapporten](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html?lang=nl-NL) en [logs](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html?lang=nl-NL) in verband met de levering, zoals voor elke levering.
   * **in Campagne v7 en Campaign Standard**: Logbestanden voor bezorgings-id&#39;s, e-mailbrede logboeken en e-mailtracking worden gesynchroniseerd met Campagne v7. U kunt dan tot 360° mening van uw marketing campagnes van Campaign v7 krijgen.

     Quarantines worden automatisch opnieuw gesynchroniseerd naar Campagne v7. Hierdoor kan niet-te leveren informatie in aanmerking worden genomen voor het volgende doel dat wordt uitgevoerd in Campaign v7.

     Meer informatie over quarantainebeheer vindt u in Campaign Standard in [deze sectie](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=nl-NL).
