---
title: LINE-kanaal
seo-title: LINE-kanaal
description: LINE-kanaal
seo-description: null
page-status-flag: never-activated
uuid: 94b4e044-3f5d-42a6-b249-29f417386156
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
discoiquuid: 1d3cc650-3c79-4a1d-b2bc-e7eb6d59d2f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# LINE-kanaal{#line-channel}

LINE is een toepassing voor gratis instant messaging-, spraak- en videogesprekken die beschikbaar zijn op alle smartphones (iPhone, Android, Windows Phone, Blackberry, Nokia) en op pc&#39;s. Met Adobe Campaign kunt u LINE-berichten verzenden.

De LIJN is slechts beschikbaar voor op-gebouw of beheerde de diensteninstallaties.

De LIJN kan ook met de transactionele berichtmodule worden gecombineerd om berichten in real time op LINE te verzenden die in de mobiele apparaten van de consument wordt geïnstalleerd. Raadpleeg deze [pagina](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line)voor meer informatie.

![](assets/line_message.png)

De onderstaande secties bevatten specifieke informatie over het lijnkanaal. Raadpleeg[deze sectie](../../delivery/using/steps-about-delivery-creation-steps.md)voor algemene informatie over het maken van een levering.

De stappen voor het gebruiken van het kanaal van de LIJN zijn:

1. Een levering maken
1. De inhoud van het bericht configureren
1. De doelpopulatie selecteren
1. De berichten verzenden
1. Controle van de levering (volgen, quarantining, rapporten, enz.).

## Regelkanaal instellen {#setting-up-line-channel}

### Een LINE-account en een externe account maken {#creating-a-line-account-and-an-external-account-}

>[!NOTE]
>
>Voordat u een LINE-account en een externe account maakt, moet u eerst het LINE-pakket op uw exemplaar installeren. Raadpleeg de sectie [LINE](../../installation/using/installing-campaign-standard-packages.md#line-package) in de installatiehandleiding voor meer informatie hierover.

U moet eerst een LINE-account maken, zodat u deze aan Adobe Campaign kunt koppelen. Vervolgens kunt u LIJNberichten verzenden naar de gebruikers die uw LIJNaccount in hun mobiele toepassing hebben toegevoegd. Externe accounts en LINE-account kunnen alleen worden beheerd door de functionele beheerder van het platform.

Zie [https://developers.line.me/](https://developers.line.me/)voor informatie over het maken en configureren van een LINE-account.

Om de dienst van de LIJN tot stand te brengen en te vormen, zie het [Leiden abonnementen](../../delivery/using/managing-subscriptions.md).

![](assets/line_service.png)

Tot slot kunt u als volgt een extern account maken op de Adobe-campagne:

1. Klik in het **venster Beheer** > **Platformstructuur** op het tabblad **Externe accounts** .
1. Klik vervolgens op het pictogram **Nieuw** .

   ![](assets/line_config.png)

1. Vul de velden **Label** en **Interne naam** in.
1. Op het **[!UICONTROL Type]** gebied, selecteert het uitgezochte Verpletteren en op het gebied van het **Kanaal** , LIJN.
1. Klik **[!UICONTROL Save]** om uw externe LINE-account te maken.
1. Vervolgens wordt onder het pictogram **Algemeen** een veld **Lijneigenschappen** weergegeven en worden de volgende velden ingevuld:

   ![](assets/line_config_2.png)

   * **Kanaalalias**: wordt via uw LINE-account opgegeven op het tabblad **[!UICONTROL Channels]** > **[!UICONTROL Technical configuration]** .
   * **Kanaal-id**: wordt via uw LINE-account weergegeven op het tabblad **Kanalen** > **Basisinformatie** .
   * **Kanaalgeheime sleutel**: wordt via uw LINE-account weergegeven op het tabblad **Kanalen** > **Basisinformatie** .
   * **Toegangstoken**: wordt verstrekt via uw rekening van de LIJN in het ontwikkelaarsportaal of door de **[!UICONTROL Get access token]** knoop te klikken.
   * **Vervaldatum** toegangstoken: staat u toe om de vervaldatum van het teken van de Toegang te specificeren.
   * **Service** voor lijnabonnement: staat u toe om de diensten te specificeren waarop de gebruikers zullen worden ingetekend.

>[!NOTE]
>
>U moet controleren of de **[!UICONTROL LINE access token update (updateLineAccessToken)]** en **[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]** workflows zijn gestart. Klik in de verkenner **[!UICONTROL Administration > Production > Technical workflows > LINE workflows]** om de status van de workflows te controleren.

## De levering maken {#creating-the-delivery}

Voer de volgende stappen uit als u een **LIJNlevering** wilt maken:

>[!NOTE]
>
>Algemene concepten voor het maken van leveringen worden in [deze sectie](../../delivery/using/steps-about-delivery-creation-steps.md)beschreven.

1. Selecteer op het **[!UICONTROL Campaigns]** tabblad de optie **[!UICONTROL Deliveries]** en klik op de **[!UICONTROL Create]** knop.
1. Selecteer de **[!UICONTROL LINE V2 delivery]** leveringssjabloon in het venster dat wordt weergegeven.

   ![](assets/line_message_01.png)

1. Identificeer uw levering met een etiket, code, en beschrijving. Zie [deze sectie](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery)voor meer informatie.
1. Klik **[!UICONTROL Continue]** om de levering te maken.

## De inhoud definiëren {#defining-the-content}

Om de inhoud van een levering van de LIJN te bepalen, moet u eerst berichttype aan uw levering toevoegen. Elke lijnlevering kan tot 5 berichten bevatten.

U kunt kiezen uit twee berichttypen:

* Tekstbericht
* Afbeelding en koppeling

### De levering van een tekstbericht configureren {#configuring-a-text-message-delivery}

Een **tekstbericht** LINE levering is een bericht dat in tekstvorm naar ontvangers wordt verzonden.

![](assets/line_message_02.png)

De configuratie voor dit type van bericht is gelijkaardig aan de configuratie van de **tekst** in e-mail. Raadpleeg deze [pagina](../../delivery/using/defining-the-email-content.md#message-content)voor meer informatie.

### Afbeelding en koppelingslevering configureren {#configuring-an-image-and-link-delivery}

Een **afbeelding en koppelingslijn** is een bericht dat naar ontvangers wordt verzonden in de vorm van een afbeelding die een of meer URL&#39;s kan bevatten.

U kunt het volgende gebruiken:

* een **persoonlijke afbeelding**,

   >[!NOTE]
   >
   >U kunt de variabele **%SIZE%** gebruiken: met deze variabele kunt u de beeldweergave optimaliseren op basis van de schermgrootte van het mobiele apparaat van de ontvanger.

   ![](assets/line_message_04.png)

* een **afbeeldings-URL**,

   ![](assets/line_message_03.png)

   Met de afbeeldings-URL&#39;s kunt u verschillende afbeeldingsresoluties gebruiken om de zichtbaarheid van de levering op mobiele apparaten te optimaliseren. Alleen afbeeldingen met dezelfde hoogte en breedte worden ondersteund.

   Afbeeldingen kunnen worden gedefinieerd op basis van de schermgrootte:

   * 1040px
   * 700px
   * 460px
   * 300px
   * 240px
   >[!NOTE]
   >
   >De grootte van 1040 x 1040 px is verplicht voor elke lijnafbeelding met koppeling.

   Vervolgens moet u alternatieve tekst toevoegen die op het mobiele apparaat van de ontvanger verschijnt.

* en **[!UICONTROL Links]**.

   ![](assets/line_message_05.png)

   In de **[!UICONTROL Links]** sectie kunt u kiezen tussen verschillende lay-outs waarmee u de afbeelding opdeelt in meerdere gebieden waarop u kunt klikken. Vervolgens kunt u aan elk onderdeel een specifieke koppeling toewijzen.

>[!NOTE]
>
>Met de syntaxis &lt;%@ include option=&#39;NmsServer_URL&#39; %>/webApp/APP3?id=&lt;%=escapeUrl(cryptString(bezoeker.id))%> kunt u een koppeling naar een webtoepassing opnemen in een LINE-bericht.

### Aanbevelingen {#recommendations}

* Wanneer u een lijnlevering naar een nieuwe ontvanger voor het eerst verzendt, moet u het officiële bericht van de LIJN betreffende de voorwaarden van gebruik en toestemming in de levering toevoegen. Het officiële bericht is beschikbaar op de volgende link: [https://terms.line.me/OA_privacy/](https://terms.line.me/OA_privacy/sp?lang=fr).

## De doelpopulatie selecteren {#selecting-the-target-population}

Het selecteren van ontvangers van een LINE levering is gelijkaardig aan het bepalen van e-mailleveringsontvangers. Zie [Doelpopulaties](../../delivery/using/steps-defining-the-target-population.md)identificeren voor meer informatie.

Er wordt gerichte aandacht besteed aan **bezoekers**.

## Berichten verzenden {#sending-messages}

Wanneer uw levering correct wordt gecreeerd en gevormd, kunt u het naar het vroeger bepaalde doel verzenden.

Het verzenden van LIJNleveringen lijkt op het verzenden van een e-maillevering. Voor meer informatie bij het verzenden van een levering, verwijs naar het [Verzenden van berichten](../../delivery/using/sending-messages.md).

## Toegang tot rapporten {#accessing-reports}

U kunt rapporten over de dienst van de LIJN bekijken door **[!UICONTROL Profiles and Targets > Services and Subscriptions > LINE]** in ontdekkingsreiziger te klikken. Klik vervolgens op het **[!UICONTROL Reports]** pictogram in de LINE-service.

![](assets/line_reports.png)

Als u rapporten over lijnleveringen wilt weergeven, klikt u op **[!UICONTROL Campaign Management > Deliveries]** en selecteert u de gewenste levering. De volgende rapporten wijzen op het klikthrough tarief. De lijn houdt geen rekening met het open tarief.

![](assets/line_reports_01.png)

## Voorbeeld: een gepersonaliseerd lijnbericht maken en verzenden {#example--create-and-send-a-personalized-line-message}

In dit voorbeeld, gaan wij een tekstbericht en een beeld tot stand brengen en vormen die gegevens bevatten die volgens de ontvanger zullen worden gepersonaliseerd.

1. Maak uw lijnlevering door op de **[!UICONTROL Create]** knop op het **[!UICONTROL Campaign]** tabblad te klikken.

   ![](assets/line_usecase.png)

1. Selecteer de **[!UICONTROL LINE V2 delivery]** leveringstemplate en geef een naam op voor uw levering.

   ![](assets/line_usecase_01.png)

1. Selecteer in het configuratievenster van uw levering de doelpopulatie.

   ![](assets/line_usecase_02.png)

1. Klik **[!UICONTROL Add]** om uw bericht te creëren en de **[!UICONTROL Message type]** te selecteren.

   Hier willen we eerst een tekstbericht maken.

   ![](assets/line_usecase_03.png)

1. Plaats de cursor op de plaats waar u de gepersonaliseerde tekst wilt invoegen en klik op het vervolgkeuzepictogram en selecteer vervolgens **[!UICONTROL Visitor > First name]**.

   ![](assets/line_usecase_05.png)

1. Volg dezelfde procedure om een afbeelding toe te voegen en selecteer deze **[!UICONTROL Image and links]** in de **[!UICONTROL Message type]** vervolgkeuzelijst.

   Voeg de URL van de afbeelding toe.

   ![](assets/line_usecase_07.png)

1. Selecteer in de **[!UICONTROL Links]** sectie de lay-out waarmee de afbeelding wordt verdeeld in meerdere klikbare gebieden.
1. Wijs een URL toe aan elk gebied van uw afbeelding.

   ![](assets/line_usecase_08.png)

1. Sla de levering op en klik **[!UICONTROL Send]** om de levering te analyseren en naar het doel te verzenden.

   De levering wordt verzonden naar het doel.

   ![](assets/line_usecase_06.png)
