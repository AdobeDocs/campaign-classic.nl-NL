---
product: campaign
title: Cross-channel leveringsworkflow
description: Meer informatie over workflows voor levering via meerdere kanalen
feature: Workflows, Channels Activity
hide: true
hidefromtoc: true
exl-id: dfd36d2c-44ff-49a9-80b4-09eaf3377072
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 3%

---

# Cross-channel leveringsworkflow{#cross-channel-delivery-workflow}



In dit geval wordt een voorbeeld weergegeven met een workflow voor levering over meerdere kanalen. Het algemene concept van dwars-kanaalleveringen wordt voorgesteld in [ deze sectie ](cross-channel-deliveries.md).

Het doel is een publiek van de ontvangers van uw gegevensbestand in verschillende groepen te segmenteren met als doel een e-mail naar een groep en een SMS-bericht naar een andere groep te verzenden.

De belangrijkste stappen voor de implementatie van dit gebruiksgeval zijn als volgt:

1. Een **[!UICONTROL Query]** -activiteit maken om uw doelgroep te bereiken.
1. Een **[!UICONTROL Email delivery]** -activiteit maken die een koppeling naar een aanbieding bevat.
1. Een **[!UICONTROL Split]** -activiteit gebruiken om:

   * Stuur een andere e-mail naar de ontvangers die het eerste e-mailbericht niet hebben geopend.
   * Verzend een SMS-bericht naar de ontvangers die het e-mailbericht hebben geopend, maar klik niet op de koppeling naar het voorstel.
   * Voeg aan het gegevensbestand de ontvangers toe die e-mail opende en de verbinding klikte.

![](assets/wkf_cross-channel_7.png)

## Stap 1: De doelgroep kiezen {#step-1--targeting-the-audience}

Om uw doel te bepalen, creeer een vraag om de ontvangers te identificeren.

1. Maak een campagne. Raadpleeg [deze sectie](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign) voor meer informatie.
1. In het **[!UICONTROL Targeting and workflows]** lusje van uw campagne, voeg de activiteit van de a **Vraag** aan uw werkschema toe. Voor meer bij het gebruiken van deze activiteit, verwijs naar [ deze sectie ](query.md).
1. Bepaal de ontvangers die uw leveringen zullen ontvangen. Selecteer bijvoorbeeld &#39;Gold&#39;-leden als doeldimensie.
1. Voeg filtervoorwaarden aan uw vraag toe. Selecteer in dit voorbeeld ontvangers met een e-mailadres en een mobiel nummer.

   ![](assets/wkf_cross-channel_3.png)

1. Sla uw wijzigingen op.

## Stap 2: Een e-mail maken met een aanbieding {#step-2--creating-an-email-including-an-offer}

1. Maak een **[!UICONTROL Email delivery]** -activiteit en dubbelklik erop in de workflow om deze te bewerken. Voor meer bij het creëren van een e-mail, verwijs naar [ deze sectie ](../../delivery/using/about-email-channel.md).
1. Ontwerp het bericht en voeg een verbinding met inbegrip van een aanbieding in de inhoud op.

   ![](assets/wkf_cross-channel_1.png)

   Voor meer bij het integreren van een aanbieding in het lichaam van een bericht, verwijs naar [ deze sectie ](../../interaction/using/integrating-an-offer-via-the-wizard.md#delivering-with-a-call-to-the-offer-engine).

1. Sla uw wijzigingen op.
1. Klik met de rechtermuisknop op de **[!UICONTROL Email delivery]** -activiteit om deze te openen.
1. Selecteer de optie **[!UICONTROL Generate an outbound transition]** om de populatie en de logbestanden voor bijhouden te herstellen.

   ![](assets/wkf_cross-channel_2.png)

   Hierdoor kunt u deze informatie gebruiken om een andere levering te verzenden, afhankelijk van het gedrag van de ontvangers bij het ontvangen van de eerste e-mail.

1. Voeg een **[!UICONTROL Wait]** -activiteit toe zodat de ontvangers het e-mailbericht enkele dagen kunnen openen.

   ![](assets/wkf_cross-channel_4.png)

## Stap 3: Het resulterende publiek segmenteren {#step-3--segmenting-the-resulting-audience}

Zodra uw doel wordt geïdentificeerd en uw eerste levering gecreeerd, moet u het doel in verschillende populaties segmenteren gebruikend het filtreren voorwaarden.

1. Voeg a **Gesplitste** activiteit aan het werkschema toe en open het. Voor meer bij het gebruiken van deze activiteit, verwijs naar [ deze sectie ](split.md).
1. Creeer drie segmenten van de bevolking die stroomopwaarts in de vraag wordt berekend.

   ![](assets/wkf_cross-channel_6.png)

1. Voor de eerste subset selecteert u de optie **[!UICONTROL Add a filtering condition on the inbound population]** en klikt u op **[!UICONTROL Edit]** .

   ![](assets/wkf_cross-channel_8.png)

1. Selecteer **[!UICONTROL Recipients of a delivery]** als het restrictiefilter en klik op **[!UICONTROL Next]** .

   ![](assets/wkf_cross-channel_9.png)

1. Selecteer in de filterinstellingen de optie **[!UICONTROL Recipients who have not opened or clicked (email)]** in de vervolgkeuzelijst **[!UICONTROL Behavior]** en selecteer de e-mail met de aanbieding die u wilt verzenden in de leveringslijst. Klik op **[!UICONTROL Finish]**.

   ![](assets/wkf_cross-channel_10.png)

1. Ga op dezelfde manier verder voor de tweede subset en selecteer **[!UICONTROL Recipients who have not clicked (email)]** in de vervolgkeuzelijst **[!UICONTROL Behavior]** .

   ![](assets/wkf_cross-channel_11.png)

1. Voor de derde subset selecteert u de optie **[!UICONTROL Add a filtering condition on the inbound population]** nadat u op **[!UICONTROL Edit]** hebt geklikt. **[!UICONTROL Use a specific filtering dimension]**
1. Selecteer **[!UICONTROL Recipient tracking log]** in de **[!UICONTROL Filtering dimension]** vervolgkeuzelijst, markeer **[!UICONTROL Filtering conditions]** in de **[!UICONTROL List of restriction filters]** en klik op **[!UICONTROL Next]** .

   ![](assets/wkf_cross-channel_12.png)

1. Selecteer de filtervoorwaarden als volgt:

   ![](assets/wkf_cross-channel_13.png)

1. Klik op **[!UICONTROL Finish]** om de wijzigingen op te slaan.

## Stap 4: De workflow voltooien {#step-4--finalizing-the-workflow}

1. Voeg de relevante activiteiten toe aan uw werkstroom na de drie subsets die het resultaat zijn van de **[!UICONTROL Split]** -activiteit:

   * Voeg een **[!UICONTROL Email delivery]** -activiteit toe om een herinnering-e-mail naar de eerste subset te verzenden.
   * Voeg een **[!UICONTROL Mobile delivery]** -activiteit toe om een SMS-bericht naar de tweede subset te verzenden.
   * Voeg een **[!UICONTROL List update]** activiteit toe om de overeenkomstige ontvangers aan het gegevensbestand toe te voegen.

1. Dubbelklik op de leveringsactiviteiten in uw workflow om deze te bewerken. Voor meer bij het creëren van een e-mail en een SMS, verwijs naar [ E-mailkanaal ](../../delivery/using/about-email-channel.md) en [ het kanaal van SMS ](../../delivery/using/sms-channel.md).
1. Dubbelklik op de **[!UICONTROL List update]** -activiteit en selecteer de optie **[!UICONTROL Generate an outbound transition]** .

   Vervolgens kunt u de resulterende ontvangers van Adobe Campaign naar de Adobe Experience Cloud exporteren. U kunt bijvoorbeeld het publiek in Adobe Target gebruiken door een **[!UICONTROL Update shared audience]** -activiteit aan de workflow toe te voegen. Voor meer op dit, verwijs naar [ Exporterend een publiek ](../../integrations/using/importing-and-exporting-audiences.md#exporting-an-audience).

1. Klik de **knoop van het Begin** in de actiebar om het werkschema uit te voeren.

De bevolking die door de **vraag** activiteit wordt gericht zal worden gesegmenteerd om een e-mail of een levering van SMS volgens het gedrag van de ontvangers te ontvangen. De resterende populatie wordt met de **[!UICONTROL List update]** -activiteit toegevoegd aan de database.
