---
product: campaign
title: Cross-channel leveringsworkflow
description: Meer informatie over workflows voor levering via meerdere kanalen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: dfd36d2c-44ff-49a9-80b4-09eaf3377072
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---

# Cross-channel leveringsworkflow{#cross-channel-delivery-workflow}



In dit geval wordt een voorbeeld weergegeven met een workflow voor levering over meerdere kanalen. Het algemene concept van de levering over meerdere kanalen wordt weergegeven in [deze sectie](cross-channel-deliveries.md).

Het doel is een publiek van de ontvangers van uw gegevensbestand in verschillende groepen te segmenteren met als doel een e-mail naar een groep en een SMS-bericht naar een andere groep te verzenden.

De belangrijkste stappen voor de implementatie van dit gebruiksgeval zijn als volgt:

1. Een **[!UICONTROL Query]** activiteit om uw publiek te richten.
1. Een **[!UICONTROL Email delivery]** activiteit die een link naar een aanbieding bevat.
1. Een **[!UICONTROL Split]** activiteit naar:

   * Stuur een andere e-mail naar de ontvangers die het eerste e-mailbericht niet hebben geopend.
   * Verzend een SMS-bericht naar de ontvangers die het e-mailbericht hebben geopend, maar klik niet op de koppeling naar het voorstel.
   * Voeg aan het gegevensbestand de ontvangers toe die e-mail opende en de verbinding klikte.

![](assets/wkf_cross-channel_7.png)

## Stap 1: Het doelpubliek {#step-1--targeting-the-audience}

Om uw doel te bepalen, creeer een vraag om de ontvangers te identificeren.

1. Een campagne maken. Raadpleeg [deze sectie](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign) voor meer informatie.
1. In de **[!UICONTROL Targeting and workflows]** tabblad van uw campagne, voegt u een **Query** activiteit aan uw werkschema. Raadpleeg voor meer informatie over het gebruik van deze activiteit [deze sectie](query.md).
1. Bepaal de ontvangers die uw leveringen zullen ontvangen. Selecteer bijvoorbeeld &#39;Gold&#39;-leden als doeldimensie.
1. Voeg filtervoorwaarden aan uw vraag toe. Selecteer in dit voorbeeld ontvangers met een e-mailadres en een mobiel nummer.

   ![](assets/wkf_cross-channel_3.png)

1. Sla uw wijzigingen op.

## Stap 2: Een e-mail maken met een aanbieding {#step-2--creating-an-email-including-an-offer}

1. Een **[!UICONTROL Email delivery]** en dubbelklik erop in uw workflow om deze te bewerken. Raadpleeg voor meer informatie over het maken van een e-mailbericht [deze sectie](../../delivery/using/about-email-channel.md).
1. Ontwerp het bericht en voeg een verbinding met inbegrip van een aanbieding in de inhoud op.

   ![](assets/wkf_cross-channel_1.png)

   Voor meer informatie over het integreren van een aanbieding in de tekst van een bericht raadpleegt u [deze sectie](../../interaction/using/integrating-an-offer-via-the-wizard.md#delivering-with-a-call-to-the-offer-engine).

1. Sla uw wijzigingen op.
1. Klik met de rechtermuisknop op de knop **[!UICONTROL Email delivery]** activiteit om het te openen.
1. Selecteer **[!UICONTROL Generate an outbound transition]** optie om de populatie en de trackinglogboeken te herstellen.

   ![](assets/wkf_cross-channel_2.png)

   Hierdoor kunt u deze informatie gebruiken om een andere levering te verzenden, afhankelijk van het gedrag van de ontvangers bij het ontvangen van de eerste e-mail.

1. Voeg een **[!UICONTROL Wait]** activiteit om de ontvangers een paar dagen te laten het e-mailbericht openen.

   ![](assets/wkf_cross-channel_4.png)

## Stap 3: Het resulterende publiek segmenteren {#step-3--segmenting-the-resulting-audience}

Zodra uw doel wordt geïdentificeerd en uw eerste levering gecreeerd, moet u het doel in verschillende populaties segmenteren gebruikend het filtreren voorwaarden.

1. Voeg een **Splitsen** aan de werkstroom en open het. Raadpleeg voor meer informatie over het gebruik van deze activiteit [deze sectie](split.md).
1. Creeer drie segmenten van de bevolking die stroomopwaarts in de vraag wordt berekend.

   ![](assets/wkf_cross-channel_6.png)

1. Selecteer voor de eerste subset de optie **[!UICONTROL Add a filtering condition on the inbound population]** en klik op **[!UICONTROL Edit]**.

   ![](assets/wkf_cross-channel_8.png)

1. Selecteren **[!UICONTROL Recipients of a delivery]** als het restrictiefilter en klik op **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_9.png)

1. Selecteer in de filterinstellingen de optie **[!UICONTROL Recipients who have not opened or clicked (email)]** van de **[!UICONTROL Behavior]** en selecteer de e-mail met het aanbod dat u wilt verzenden in de leveringslijst. Klik op **[!UICONTROL Finish]**.

   ![](assets/wkf_cross-channel_10.png)

1. Ga op dezelfde manier verder voor de tweede subset en selecteer **[!UICONTROL Recipients who have not clicked (email)]** van de **[!UICONTROL Behavior]** vervolgkeuzelijst.

   ![](assets/wkf_cross-channel_11.png)

1. Voor de derde subset selecteert u de opdracht **[!UICONTROL Add a filtering condition on the inbound population]** en klikken **[!UICONTROL Edit]**, selecteert u de **[!UICONTROL Use a specific filtering dimension]** optie.
1. Selecteren **[!UICONTROL Recipient tracking log]** van de **[!UICONTROL Filtering dimension]** vervolgkeuzelijst, markeren **[!UICONTROL Filtering conditions]** van de **[!UICONTROL List of restriction filters]** en klik op **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_12.png)

1. Selecteer de filtervoorwaarden als volgt:

   ![](assets/wkf_cross-channel_13.png)

1. Klikken **[!UICONTROL Finish]** om uw wijzigingen op te slaan.

## Stap 4: De workflow voltooien {#step-4--finalizing-the-workflow}

1. Voeg relevante activiteiten toe aan uw werkstroom na de drie subsets die het resultaat zijn van de **[!UICONTROL Split]** activiteit:

   * Een **[!UICONTROL Email delivery]** activiteit om een herinnering e-mail naar de eerste subset te verzenden.
   * Voeg een **[!UICONTROL Mobile delivery]** activiteit om een bericht van SMS naar de tweede ondergroep te verzenden.
   * Voeg een **[!UICONTROL List update]** activiteit om de overeenkomstige ontvangers aan het gegevensbestand toe te voegen.

1. Dubbelklik op de leveringsactiviteiten in uw workflow om deze te bewerken. Raadpleeg voor meer informatie over het maken van een e-mail en een sms [E-mailkanaal](../../delivery/using/about-email-channel.md) en [SMS-kanaal](../../delivery/using/sms-channel.md).
1. Dubbelklik op de knop **[!UICONTROL List update]** activiteit en selecteer **[!UICONTROL Generate an outbound transition]** optie.

   Vervolgens kunt u de resulterende ontvangers van Adobe Campaign naar de Adobe Experience Cloud exporteren. U kunt bijvoorbeeld het publiek in Adobe Target gebruiken door een **[!UICONTROL Update shared audience]** activiteit aan de werkstroom. Raadpleeg voor meer informatie hierover [Een publiek exporteren](../../integrations/using/importing-and-exporting-audiences.md#exporting-an-audience).

1. Klik op de knop **Start** in de actiebalk om de workflow uit te voeren.

De door de **Query** de activiteit zal worden gesegmenteerd om een e-mail of een levering van SMS volgens het gedrag van de ontvangers te ontvangen. De resterende populatie wordt met behulp van de **[!UICONTROL List update]** activiteit.
