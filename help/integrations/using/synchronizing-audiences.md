---
title: Synchroniseren van publiek
seo-title: Synchroniseren van publiek
description: Synchroniseren van publiek
seo-description: null
page-status-flag: never-activated
uuid: eda67bf7-8a0a-4240-8b31-de364be5d572
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 749a084e-69ee-46b4-b09b-cb91bb1da3cd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Synchroniseren van publiek{#synchronizing-audiences}

U kunt een geavanceerde lijst maken met de geavanceerde functies van Campagne v7 en deze lijst direct en in real-time delen met de Campagnestandaard (inclusief extra gegevens), zonder problemen. De gebruiker van de Standaard van de Campagne kan dan het publiek in de Norm van de Campagne van Adobe verbruiken.

Complexe gericht gebruiken van extra gegevens die niet in de Norm van de Campagne worden herhaald kan slechts worden bereikt gebruikend Campagne v7.

U kunt lijsten van ontvangers of gegevens ook eenvoudig delen die door een schakelaar zoals de Dynamiek van Microsoft met de Norm van de Campagne komen.

In dit geval kunt u zien hoe u het doel van uw levering in Campagne v7 voorbereidt en hoe u dit doel en de aanvullende gegevens ervan opnieuw kunt gebruiken in een levering die u hebt gemaakt en verzonden met Adobe Campaign Standard.

>[!NOTE]
>
>U kunt gegevens ook verrijken met aggregaten en verzamelingen in Adobe Campagne Standard als alle gegevens die u nodig hebt, al zijn gerepliceerd.

## Vereisten {#prerequisites}

Hiervoor hebt u het volgende nodig:

* Ontvangers die zijn opgeslagen in de Campagne v7-database en zijn gesynchroniseerd met Campagnestandaard. Raadpleeg de sectie [Synchronizing profiles](../../integrations/using/synchronizing-profiles.md) .
* Aanvullende gegevens, zoals abonnementen of transacties die zijn opgeslagen in tabellen met betrekking tot namen:ontvangers in de Campagne v7-database. Deze gegevens kunnen uit de schema&#39;s OOB van de Campagne v7 of douanetabellen komen. Deze zijn standaard niet beschikbaar in de campagnestandaard omdat ze niet zijn gesynchroniseerd.
* Recht om werkschema&#39;s in zowel Campagne v7 als de Norm van de Campagne uit te voeren.
* Recht om een levering in de Norm van de Campagne tot stand te brengen en uit te voeren.

## Een doelworkflow met aanvullende gegevens maken in Campagne v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Complexe gericht gebruiken van extra gegevens die niet in de Norm van de Campagne worden herhaald kan slechts worden bereikt gebruikend Campagne v7.

Zodra het doel en zijn extra gegevens worden bepaald, is het mogelijk om het als lijst op te slaan die met de Norm van de Campagne kan worden gedeeld.

>[!NOTE]
>
>Dit is een voorbeeld. Afhankelijk van uw vereisten, kunt u eenvoudig een lijst van ontvangers vragen en het met ACS zonder enige verdere verwerking delen. U kunt ook andere gegevensbeheeractiviteiten gebruiken om uw uiteindelijke doel voor te bereiden.

Zo krijgt u het uiteindelijke publiek en de aanvullende gegevens:

1. Maak een nieuwe workflow via **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Voeg een **[!UICONTROL Query]** activiteit toe en selecteer de ontvangers waarnaar u de laatste e-mail wilt verzenden. Bijvoorbeeld alle ontvangers tussen 18 en 30 jaar oud die in Frankrijk wonen.

   ![](assets/acs_connect_query1.png)

1. Voeg aanvullende gegevens toe vanuit de query. Raadpleeg de sectie Gegevens [](../../workflow/using/query.md#adding-data) toevoegen voor meer informatie.

   In dit voorbeeld ziet u hoe u een aggregaat toevoegt om te tellen hoeveel leveringen een ontvanger in een jaar heeft ontvangen.

   Selecteer in het **[!UICONTROL Query]** vak **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. Selecteer **[!UICONTROL Data linked to the filtering dimension]** en klik op **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. Kies **[!UICONTROL Data linked to the filtering dimension]** en selecteer vervolgens het **[!UICONTROL Recipient delivery logs]** knooppunt en klik op **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. Selecteer **[!UICONTROL Aggregates]** in het **[!UICONTROL Data collected]** veld en klik op **[!UICONTROL Next]**.

   ![](assets/acs_connect_query5.png)

1. Voeg een het filtreren voorwaarde toe om rekening slechts logboeken te houden die tijdens de laatste 365 dagen werden gecreeerd en klik **[!UICONTROL Next]**.

   ![](assets/acs_connect_query6.png)

1. Definieer de uitvoerkolommen. Hier is de enige benodigde kolom die het aantal leveringen telt. Dat doet u als volgt:

   * Selecteer **[!UICONTROL Add]** rechts van het venster.
   * Klik in het **[!UICONTROL Select field]** venster op **[!UICONTROL Advanced selection]**.
   * Selecteer **[!UICONTROL Aggregate]**, dan **[!UICONTROL Count]**. Controleer de **[!UICONTROL Distinct]** optie en klik op **[!UICONTROL Next]**.
   * Selecteer in de lijst met velden het veld dat wordt gebruikt voor de functie **Tellen** . Kies een veld dat altijd wordt ingevuld, bijvoorbeeld het **[!UICONTROL Primary key]** veld, en klik **[!UICONTROL Finish]**.
   * Wijzig de expressie in de **[!UICONTROL Alias]** kolom. Met deze alias kunt u de toegevoegde kolom in de uiteindelijke aflevering gemakkelijk ophalen. Bijvoorbeeld **NBDeliies**.
   * Klik **[!UICONTROL Finish]** en sla de **[!UICONTROL Query]** activiteitenconfiguratie op.
   ![](assets/acs_connect_query7.png)

1. Sla de workflow op. Het volgende gedeelte laat zien hoe u de populatie deelt met ACS.

## Het doel delen met de Campagnestandaard {#share-the-target-with-campaign-standard}

Zodra de doelpopulatie wordt bepaald, kunt u het met ACS door een **[!UICONTROL List update]** activiteit delen.

1. Voeg in de eerder gemaakte workflow een **[!UICONTROL List update]** activiteit toe en geef de lijst op die u wilt bijwerken of maken.

   Geef de map op waarin u de lijst wilt opslaan in Campagne v7. Lijsten zijn onderworpen aan de omslagafbeelding die tijdens de implementatie wordt bepaald, die hun zichtbaarheid kan beïnvloeden zodra zij in de Norm van de Campagne worden gedeeld. Raadpleeg de sectie [Rechtenomzetting](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) .

1. Controleer of de **[!UICONTROL Share with ACS]** optie is ingeschakeld. Deze optie is standaard ingeschakeld.

   ![](assets/acs_connect_listupdate1.png)

1. Sla de workflow op en voer deze uit.

   Het doel en de bijbehorende aanvullende gegevens worden opgeslagen in een lijst in Campagne v7 en worden direct gedeeld als een lijstpubliek in de Standaard van de Campagne. Alleen de profielen die zijn gerepliceerd, worden gedeeld met ACS.

Als een fout op de **[!UICONTROL List update]** activiteit voorkomt, betekent het dat de synchronisatie met de Norm van de Campagne kan ontbroken hebben. Ga naar **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Deze map bevat synchronisatieworkflows die worden geactiveerd door het uitvoeren van de **[!UICONTROL List update]** activiteit. Verwijs naar het [Oplossen van problemen de sectie van de Schakelaar](../../integrations/using/troubleshooting-the-acs-connector.md) ACS.

## Haal de gegevens op in de Standaard van de Campagne en gebruik het in een levering {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Zodra het richten werkschema in Campagne v7 wordt uitgevoerd, kunt u het lijstpubliek op read-only wijze van het **[!UICONTROL Audiences]** menu van de Norm van de Campagne vinden.

![](assets/acs_connect_deliveryworkflow_audience.png)

Door een leveringswerkschema in de Norm van de Campagne te creëren, is het dan mogelijk om dit publiek evenals de extra gegevens te gebruiken die het in een levering bevat.

1. Maak een nieuwe workflow in het **[!UICONTROL Marketing activities]** menu.
1. Voeg een **[!UICONTROL Read audience]** activiteit toe en selecteer het publiek u eerder van Campagne v7 deelde.

   Deze activiteit wordt gebruikt om de gegevens van het geselecteerde publiek terug te winnen. U kunt **[!UICONTROL Source Filtering]** indien nodig ook een extra waarde toevoegen via het tabblad &#39;op basis&#39; van deze activiteit.

1. Voeg een **[!UICONTROL Email delivery]** activiteit toe en vorm het als een andere [e-mailleveringsactiviteit](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html).
1. Open de leveringsinhoud.
1. Voeg een verpersoonlijkingsgebied toe. Zoek in het pop-upvenster het **[!UICONTROL Additional data (targetData)]** knooppunt. Dit knooppunt bevat de aanvullende gegevens van het publiek die zijn berekend in de initiële doelworkflow. U kunt ze als elk ander verpersoonlijkingsveld gebruiken.

   In dit voorbeeld zijn de aanvullende gegevens die afkomstig zijn van de oorspronkelijke doelworkflow het aantal leveringen dat in de laatste 365 dagen aan elke ontvanger is verzonden. De alias NBDeliies die is opgegeven in de doelworkflow is hier zichtbaar.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Sla de levering en de workflow op.

   De workflow kan nu worden uitgevoerd. De levering wordt geanalyseerd en kan worden verzonden.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Uw levering verzenden en controleren {#send-and-monitor-your-delivery}

Zodra de levering en zijn inhoud klaar zijn, verzend de levering, zoals die met meer details in [deze sectie](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html)wordt beschreven:

1. Voer de leveringswerkstroom uit. Met deze stap wordt het e-mailbericht voorbereid voor verzending.
1. Van het leveringsdashboard, bevestig manueel dat de levering kan worden verzonden.
1. Controleer de rapporten en logboeken van de levering:

   * **In de standaard** Campagne: Toegang tot [rapporten](https://docs.adobe.com/content/help/en/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) en [logboeken](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) met betrekking tot de levering zoals voor om het even welke levering.
   * **in Campaign v7 en Campaign Standard**: Logbestanden voor levering-id&#39;s, e-mailbrede logboeken en e-mailtracking worden gesynchroniseerd met Campagne v7. U kunt dan tot 360° mening van uw marketing campagnes van Campaign v7 krijgen.

      Quarantines worden automatisch opnieuw gesynchroniseerd naar Campagne v7. Hierdoor kan niet-te leveren informatie in aanmerking worden genomen voor het volgende doel dat wordt uitgevoerd in Campaign v7.

      Meer informatie over quarantainebeheer vindt u in Campagnestandaard in [deze sectie](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html).

