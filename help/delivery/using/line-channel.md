---
solution: Campaign Classic
product: campaign
title: LINE-kanaal
description: LINE-kanaal
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1100'
ht-degree: 3%

---


# LINE-kanaal{#line-channel}

LINE is een toepassing voor gratis instant messaging-, spraak- en videogesprekken die beschikbaar zijn op alle smartphones (iPhone, Android, Windows Phone, Blackberry, Nokia) en op pc&#39;s. Met Adobe Campaign kunt u LIJNberichten verzenden.

De LIJN is slechts beschikbaar voor op-gebouw of beheerde de diensteninstallaties.

De LIJN kan ook met de transactionele berichtmodule worden gecombineerd om berichten in real time op LINE te verzenden die in de mobiele apparaten van de consument wordt geïnstalleerd. Raadpleeg [deze pagina](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line) voor meer informatie.

![](assets/line_message.png)

De onderstaande secties bevatten specifieke informatie over het lijnkanaal. Voor globale informatie over hoe te om een levering tot stand te brengen, verwijs naar [deze sectie](../../delivery/using/steps-about-delivery-creation-steps.md).

De stappen voor het gebruiken van het kanaal van de LIJN zijn:

1. Een levering maken
1. De inhoud van het bericht configureren
1. De doelpopulatie selecteren
1. De berichten verzenden
1. Controle van de levering (volgen, quarantining, rapporten, enz.).

## Regelkanaal {#setting-up-line-channel} instellen

### Een LINE-account en een externe account maken {#creating-a-line-account-and-an-external-account-}

>[!NOTE]
>
>Voordat u een LINE-account en een externe account maakt, moet u eerst het LINE-pakket op uw exemplaar installeren. Raadpleeg de sectie [LINE](../../installation/using/installing-campaign-standard-packages.md#line-package) in de installatiehandleiding voor meer informatie hierover.

U moet eerst een LINE-account maken, zodat u deze aan Adobe Campaign kunt koppelen. Vervolgens kunt u LIJNberichten verzenden naar de gebruikers die uw LIJNaccount in hun mobiele toepassing hebben toegevoegd. Externe accounts en LINE-account kunnen alleen worden beheerd door de functionele beheerder van het platform.

Zie [https://developers.line.me/](https://developers.line.me/) om een LINE-account te maken en te configureren.

Zie [Abonnementen beheren](../../delivery/using/managing-subscriptions.md) voor informatie over het maken en configureren van een LINE-service.

![](assets/line_service.png)

Ten slotte een externe account maken op Adobe Campaign:

1. Klik in **Beheer** > **Platform** boomstructuur op het tabblad **Externe accounts**.
1. Klik vervolgens op het pictogram **Nieuw**.

   ![](assets/line_config.png)

1. Vul de velden **Label** en **Interne naam** in.
1. Selecteer in het veld **[!UICONTROL Type]** de optie Verpletteren en selecteer REGEL in het veld **Kanaal**.
1. Klik op **[!UICONTROL Save]** om uw externe LINE-account te maken.
1. Een **LINE** verpersoonlijkingsgebied verschijnt dan onder het **Algemene** pictogram, vult de volgende gebieden:

   ![](assets/line_config_2.png)

   * **Kanaalalias**: wordt via uw LINE-account op het  **[!UICONTROL Channels]** tabblad  **[!UICONTROL Technical configuration]** > aangeboden.
   * **Kanaal-id**: wordt via uw LINE-account opgegeven op het tabblad  **Kanalen**  >  **Basisinformatie** .
   * **Kanaalgeheime sleutel**: wordt via uw LINE-account opgegeven op het tabblad  **Kanalen**  >  **Basisinformatie** .
   * **Toegangstoken**: wordt verstrekt via uw rekening van de LIJN in het ontwikkelaarsportaal of door de  **[!UICONTROL Get access token]** knoop te klikken.
   * **Vervaldatum** toegangstoken: staat u toe om de vervaldatum van het teken van de Toegang te specificeren.
   * **Service** voor lijnabonnement: staat u toe om de diensten te specificeren waarop de gebruikers zullen worden ingetekend.

>[!NOTE]
>
>U moet verifiëren dat de **[!UICONTROL LINE access token update (updateLineAccessToken)]** en **[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]** werkschema&#39;s zijn begonnen. Klik in de verkenner op **[!UICONTROL Administration > Production > Technical workflows > LINE workflows]** om de status van de workflows te controleren.

## De levering maken {#creating-the-delivery}

Als u een **LINE** levering wilt maken, moet u de volgende stappen volgen:

>[!NOTE]
>
>Algemene concepten voor het maken van leveringen worden weergegeven in [deze sectie](../../delivery/using/steps-about-delivery-creation-steps.md).

1. Selecteer **[!UICONTROL Campaigns]** op het tabblad &lt;a0/> en klik op de knop **[!UICONTROL Create]**.**[!UICONTROL Deliveries]**
1. Selecteer in het venster dat wordt weergegeven de leveringssjabloon **[!UICONTROL LINE V2 delivery]**.

   ![](assets/line_message_01.png)

1. Identificeer uw levering met een etiket, code, en beschrijving. Raadpleeg [deze sectie](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery) voor meer informatie.
1. Klik **[!UICONTROL Continue]** om uw levering tot stand te brengen.

## De content definiëren {#defining-the-content}

Om de inhoud van een levering van de LIJN te bepalen, moet u eerst berichttype aan uw levering toevoegen. Elke lijnlevering kan tot 5 berichten bevatten.

U kunt kiezen uit twee berichttypen:

* Tekstbericht
* Afbeelding en koppeling

### Het vormen van een bericht van de Tekst levering {#configuring-a-text-message-delivery}

Een **Tekstbericht** Regellevering is een bericht dat naar ontvangers in tekstvorm wordt verzonden.

![](assets/line_message_02.png)

De configuratie voor dit type van bericht is gelijkaardig aan de configuratie van **text** in e-mail. Raadpleeg deze [pagina](../../delivery/using/defining-the-email-content.md#message-content) voor meer informatie.

### Een afbeelding configureren en levering van koppelingen {#configuring-an-image-and-link-delivery} configureren

Een **Afbeelding en koppeling** Regellevering is een bericht dat naar ontvangers wordt verzonden in de vorm van een afbeelding die een of meerdere URL&#39;s kan bevatten.

U kunt het volgende gebruiken:

* a **Gepersonaliseerde afbeelding**,

   >[!NOTE]
   >
   >U kunt de **%SIZE%** variabele gebruiken: met deze variabele kunt u de beeldweergave optimaliseren op basis van de schermgrootte van het mobiele apparaat van de ontvanger.

   ![](assets/line_message_04.png)

* een **URL van afbeelding**,

   ![](assets/line_message_03.png)

   Met de afbeeldings-URL&#39;s kunt u verschillende afbeeldingsresoluties gebruiken om de zichtbaarheid van de levering op mobiele apparaten te optimaliseren. Alleen afbeeldingen met dezelfde hoogte en breedte worden ondersteund.

   Afbeeldingen kunnen worden gedefinieerd op basis van de schermgrootte:

   * 1040 px
   * 700 px
   * 460 px
   * 300 px
   * 240 px

   >[!NOTE]
   >
   >De grootte van 1040 x 1040 px is verplicht voor elke lijnafbeelding met koppeling.

   Vervolgens moet u alternatieve tekst toevoegen die op het mobiele apparaat van de ontvanger verschijnt.

* en **[!UICONTROL Links]**.

   ![](assets/line_message_05.png)

   In de sectie **[!UICONTROL Links]** kunt u kiezen tussen verschillende lay-outs die de afbeelding verdelen in meerdere klikbare gebieden. Vervolgens kunt u aan elk onderdeel een specifieke koppeling toewijzen.

>[!NOTE]
>
>Met de syntaxis &lt;%@ include option=&#39;NmsServer_URL&#39; %>/webApp/APP3?id=&lt;%=escapeUrl(cryptString(bezoeker.id))%> kunt u een koppeling naar een webtoepassing opnemen in een LINE-bericht.

### Aanbevelingen {#recommendations}

* Wanneer u een lijnlevering naar een nieuwe ontvanger voor het eerst verzendt, moet u het officiële bericht van de LIJN betreffende de voorwaarden van gebruik en toestemming in de levering toevoegen. Het officiële bericht is beschikbaar op de volgende link: [https://terms.line.me/OA_privacy/](https://terms.line.me/OA_privacy/sp?lang=fr).

## De doelpopulatie selecteren {#selecting-the-target-population}

Het selecteren van ontvangers van een LINE levering is gelijkaardig aan het bepalen van e-mailleveringsontvangers. Raadpleeg [Doelpopulaties identificeren](../../delivery/using/steps-defining-the-target-population.md) voor meer informatie.

Het richten wordt uitgevoerd op **bezoekers**.

## Berichten verzenden {#sending-messages}

Wanneer uw levering correct wordt gecreeerd en gevormd, kunt u het naar het vroeger bepaalde doel verzenden.

Het verzenden van LIJNleveringen lijkt op het verzenden van een e-maillevering. Voor meer informatie bij het verzenden van een levering, verwijs naar [Verzendende berichten](../../delivery/using/sending-messages.md).

## Rapporten openen {#accessing-reports}

U kunt rapporten over de dienst van de LIJN bekijken door **[!UICONTROL Profiles and Targets > Services and Subscriptions > LINE]** in de ontdekkingsreiziger te klikken. Klik vervolgens op het pictogram **[!UICONTROL Reports]** in de LINE-service.

![](assets/line_reports.png)

Als u rapporten wilt weergeven over lijnleveringen, klikt u op **[!UICONTROL Campaign Management > Deliveries]** en selecteert u de gewenste levering. De volgende rapporten wijzen op het klikthrough tarief. De lijn houdt geen rekening met het open tarief.

![](assets/line_reports_01.png)

## Voorbeeld: een gepersonaliseerd lijnbericht {#example--create-and-send-a-personalized-line-message} maken en verzenden

In dit voorbeeld, gaan wij een tekstbericht en een beeld tot stand brengen en vormen die gegevens bevatten die volgens de ontvanger zullen worden gepersonaliseerd.

1. Creeer uw levering van de LIJN door de **[!UICONTROL Create]** knoop van **[!UICONTROL Campaign]** tabel te klikken.

   ![](assets/line_usecase.png)

1. Selecteer de leveringssjabloon **[!UICONTROL LINE V2 delivery]** en geef uw levering een naam.

   ![](assets/line_usecase_01.png)

1. Selecteer in het configuratievenster van uw levering de doelpopulatie.

   ![](assets/line_usecase_02.png)

1. Klik **[!UICONTROL Add]** om uw bericht tot stand te brengen en **[!UICONTROL Message type]** te selecteren.

   Hier willen we eerst een tekstbericht maken.

   ![](assets/line_usecase_03.png)

1. Plaats de cursor op de plaats waar u de gepersonaliseerde tekst wilt invoegen en klik op het vervolgkeuzepictogram en selecteer **[!UICONTROL Visitor > First name]**.

   ![](assets/line_usecase_05.png)

1. Volg dezelfde procedure om een afbeelding toe te voegen door **[!UICONTROL Image and links]** te selecteren in de vervolgkeuzelijst **[!UICONTROL Message type]**.

   Voeg de URL van de afbeelding toe.

   ![](assets/line_usecase_07.png)

1. Selecteer in de sectie **[!UICONTROL Links]** de lay-out die de afbeelding in meerdere klikbare gebieden zal verdelen.
1. Wijs een URL toe aan elk gebied van uw afbeelding.

   ![](assets/line_usecase_08.png)

1. Sla de levering op en klik op **[!UICONTROL Send]** om de levering te analyseren en naar het doel te verzenden.

   De levering wordt verzonden naar het doel.

   ![](assets/line_usecase_06.png)
