---
product: campaign
title: Regelleveringen maken
description: Leer hoe u REGELS maakt
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Line App
role: User
exl-id: 1baaabbd-9fd7-4d9b-b78e-d2a559d7dddb
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '1165'
ht-degree: 2%

---

# Regelleveringen maken{#line-channel}



[!DNL LINE] is een toepassing voor gratis instant messaging-, spraak- en videogesprekken, beschikbaar op elk mobiel besturingssysteem en op pc.

[!DNL LINE] kan ook met de transactionele berichtmodule worden gecombineerd om berichten in real time op te sturen [!DNL LINE] in mobiele apparaten voor consumenten geïnstalleerd. Raadpleeg [deze pagina](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line) voor meer informatie.

![](assets/line_message.png)

De stappen voor het gebruik van de [!DNL LINE] kanaal zijn:

1. [LINE-kanaal instellen](#setting-up-line-channel)
1. [Een levering maken](#creating-the-delivery)
1. [Het inhoudstype configureren](#defining-the-content)
1. [Bewaking van de aflevering (volgen, quarantining, rapporten, enz.)](#accessing-reports)

## LINE-kanaal instellen {#setting-up-line-channel}

Voordat u een [!DNL LINE] -account en externe account, moet u eerst het LINE-pakket op uw exemplaar installeren. Raadpleeg voor meer informatie hierover [deze sectie](../../installation/using/installing-campaign-standard-packages.md#line-package).

U moet eerst een [!DNL LINE] -account, zodat u deze aan Adobe Campaign kunt koppelen. Vervolgens kunt u [!DNL LINE] berichten aan de gebruikers die uw [!DNL LINE] in hun mobiele toepassing. Externe rekeningen en [!DNL LINE] -account kan alleen worden beheerd door de functionele beheerder van het platform.

Om een [!DNL LINE] account, zie [Documentatie voor lijnontwikkelaars](https://developers.line.me/).

### Creeer en vorm de dienst van de LIJN {#configure-line-service}

Als u uw [!DNL LINE] service:

1. Selecteer op de Adobe Campaign Classic-homepage de optie **[!UICONTROL Profiles and Targets]** tab.

1. Selecteer in het menu aan de linkerkant de optie **[!UICONTROL Services and Subscriptions]** en klik op **[!UICONTROL Create]**.

   ![](assets/line_service_1.png)

1. Voeg een **[!UICONTROL Label]** en **[!UICONTROL Internal name]** naar uw nieuwe service.

1. Selecteren **[!UICONTROL LINE]** van de **[!UICONTROL Type]** vervolgkeuzelijst.

   ![](assets/line_service_2.png)

1. Klik op **[!UICONTROL Save]**.

Zie voor meer informatie over abonnementen en services [Abonnementen beheren](managing-subscriptions.md).

### Externe LINE-account configureren {#configure-line-external}

Nadat u uw [!DNL LINE] de dienst, moet u vormen [!DNL LINE] externe rekening op Adobe Campaign:

1. In de **[!UICONTROL Administration]** > **[!UICONTROL Platform]** boomstructuur, klik **[!UICONTROL External Accounts]** tab.

1. De ingebouwde **[!UICONTROL LINE V2 routing]** externe rekening.

   ![](assets/line_config.png)

1. Klik op de knop **[!UICONTROL LINE]** van uw externe account om uw externe account te configureren. Vul de volgende velden in:

   ![](assets/line_config_2.png)

   * **[!UICONTROL Channel Alias]**: wordt geleverd via uw [!DNL LINE] in de **[!UICONTROL Channels]** > **[!UICONTROL Technical configuration]** tab.
   * **[!UICONTROL Channel ID]**: wordt geleverd via uw [!DNL LINE] in de **[!UICONTROL Channels]** > **[!UICONTROL Basic Information panel]** tab.
   * **[!UICONTROL Channel secret key]**: wordt geleverd via uw [!DNL LINE] in de **[!UICONTROL Channels]** > **[!UICONTROL Basic Information panel]** tab.
   * **[!UICONTROL Access token]**: wordt geleverd via uw [!DNL LINE] in de ontwikkelaarportal of door op de knop **[!UICONTROL Get access token]** knop.
   * **[!UICONTROL Access token expiration date]**: hiermee kunt u de vervaldatum van het toegangstoken opgeven.
   * **[!UICONTROL LINE subscription service]**: staat u toe om de diensten te specificeren waarop de gebruikers zullen worden ingetekend.

1. Zodra uw configuratie gereed is, klikt u op **[!UICONTROL Save]**.

1. Van de **[!UICONTROL Explorer]**, selecteert u **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL LINE workflows]** om te controleren of de **[!UICONTROL LINE V2 access token update (updateLineAccessToken)]** en **[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]** Er zijn workflows gestart.

De [!DNL LINE] is nu geconfigureerd in Adobe Campaign, kunt u beginnen met het maken en verzenden van lijnleveringen naar abonnees.

## LINE-levering maken {#creating-the-delivery}

>[!NOTE]
>
>Wanneer u een [!DNL LINE] voor het eerst aan een nieuwe ontvanger leveren, moet u het officiële lijnbericht betreffende de gebruiksvoorwaarden en de toestemming in de levering toevoegen. Het officiële bericht is beschikbaar op het [volgende koppeling](https://terms.line.me/OA_privacy/).

Een [!DNL LINE] levering u moet deze stappen volgen:

1. Van de **[!UICONTROL Campaigns]** tab, selecteert u **[!UICONTROL Deliveries]** Klik vervolgens op de knop **[!UICONTROL Create]** knop.

   ![](assets/line_message_07.png)

1. Selecteren **[!UICONTROL LINE V2 delivery]** leveringssjabloon.

   ![](assets/line_message_01.png)

1. Identificeer uw levering met een **[!UICONTROL Label]**, **[!UICONTROL Delivery code]**, en  **[!UICONTROL Description]**. Raadpleeg [deze sectie](steps-create-and-identify-the-delivery.md#identifying-the-delivery) voor meer informatie.

1. Klikken **[!UICONTROL Continue]** om uw levering te maken.

1. Selecteer in de leveringseditor de optie **[!UICONTROL To]** om de ontvangers van uw [!DNL LINE] levering. Er wordt gericht op **[!UICONTROL Visitor subscriptions (nms:visitorSub)]**.

   Raadpleeg voor meer informatie [Doelpopulaties identificeren](steps-defining-the-target-population.md).

   ![](assets/line_message_08.png)

1. Klikken **[!UICONTROL Add]** om uw **[!UICONTROL Delivery target population]**.

   ![](assets/line_message_09.png)

1. Kiezen als u wilt richten [!DNL LINE] abonnees direct of als u gebruikers afhankelijk van hun wilt richten [!DNL LINE] abonnement en klik op **[!UICONTROL Next]**. In dit voorbeeld hebben we **[!UICONTROL By LINE V2 subscription]**.

1. Selecteren **[!UICONTROL Line-V2]** in de **[!UICONTROL Folder]** vervolgkeuzelijst en daarna uw [!DNL LINE] service. Klikken **[!UICONTROL Finish]** dan **[!UICONTROL Ok]** om uw levering aan te passen.

   ![](assets/line_message_10.png)

1. Klik in de leveringseditor op **[!UICONTROL Add]** om een of meerdere berichten toe te voegen en de **[!UICONTROL Content type]**.

   Voor meer informatie over de verschillende **[!UICONTROL Content type]** beschikbaar, raadpleegt u [Het inhoudstype definiëren](#defining-the-content).

   ![](assets/line_message_11.png)

1. Wanneer uw levering correct wordt gecreeerd en gevormd, kunt u het naar het vroeger bepaalde doel verzenden.

   Voor meer informatie over het verzenden van een levering raadpleegt u [Berichten verzenden](sending-messages.md).

1. Na het verzenden van uw bericht, heb toegang tot uw rapport om de doeltreffendheid van uw levering te meten.

   Voor meer informatie over [!DNL LINE] rapporten, zie [Toegangsrapporten](#accessing-reports).

## Het inhoudstype definiëren {#defining-the-content}

De inhoud van een [!DNL LINE] levering, moet u eerst berichttype aan uw levering toevoegen. Elk [!DNL LINE] de levering kan maximaal 5 berichten bevatten.

U kunt kiezen uit drie berichttypen:

* [Tekstbericht](#configuring-a-text-message-delivery)
* [Afbeelding en koppeling](#configuring-an-image-and-link-delivery)
* [Video-bericht](#configuring-a-video-message-delivery)

### De levering van een tekstbericht configureren {#configuring-a-text-message-delivery}

>[!NOTE]
>
>De `<%@ include option='NmsServer_URL' %>/webApp/APP3?id=<%=escapeUrl(cryptString(visitor.id))%>` kunt u een koppeling naar een webtoepassing opnemen in een LINE-bericht.

A **[!UICONTROL Text message]** [!DNL LINE] De levering is een bericht dat in tekstvorm aan ontvangers wordt verzonden.

![](assets/line_message_02.png)

De configuratie voor dit type van bericht is gelijkaardig aan de configuratie van **[!UICONTROL Text]** in een e-mail. Raadpleeg deze voor meer informatie [page](defining-the-email-content.md#message-content).

### Afbeelding en koppelingslevering configureren {#configuring-an-image-and-link-delivery}

An **[!UICONTROL Image and link]** [!DNL LINE] levering is een bericht dat aan ontvangers wordt verzonden in de vorm van een afbeelding die een of meerdere URL&#39;s kan bevatten.

U kunt het volgende gebruiken:

* a **[!UICONTROL Personalized image]**,

  >[!NOTE]
  >
  >U kunt de **%SIZE%** variabele om de beeldweergave te optimaliseren volgens de schermgrootte van het mobiele apparaat van de ontvanger.

  ![](assets/line_message_04.png)

* een **[!UICONTROL Image URL]** per apparaatschermgrootte,

  ![](assets/line_message_03.png)

  De **[!UICONTROL Define images per device screen size]** kunt u verschillende afbeeldingsresoluties gebruiken om de zichtbaarheid van de levering op mobiele apparaten te optimaliseren. Alleen afbeeldingen met dezelfde hoogte en breedte worden ondersteund.

  Afbeeldingen kunnen worden gedefinieerd op basis van de schermgrootte:

   * 1040px
   * 700px
   * 460px
   * 300px
   * 240px

  >[!CAUTION]
  >
  >De grootte van 1040 x 1040 px is verplicht voor elke lijnafbeelding met koppeling.

  Vervolgens moet u alternatieve tekst toevoegen die op het mobiele apparaat van de ontvanger verschijnt.

* en **[!UICONTROL Links]**.

  De **[!UICONTROL Links]** kunt u kiezen tussen verschillende lay-outs die de afbeelding verdelen in meerdere klikbare gebieden. U kunt dan elk van hen toewijzen een specifiek **[!UICONTROL Link URL]**.

  ![](assets/line_message_05.png)

### Een videoboodschap configureren {#configuring-a-video-message-delivery}

A **[!UICONTROL Video message]** [!DNL LINE] De levering is een bericht dat aan ontvangers in de vorm van een video wordt verzonden die een URL kan bevatten.

De **[!UICONTROL Preview Image URL]** kunt u de URL toevoegen van een voorvertoning met een tekenlimiet van 1000. JPEG en PNG worden ondersteund met een maximale bestandsgrootte van 1 MB.

De **[!UICONTROL Video Image URL]** kunt u de URL van het videobestand toevoegen met een tekenlimiet van 1000. Alleen MP4-indeling wordt ondersteund met een maximale bestandsgrootte van 200 MB.

Brede of lange video&#39;s kunnen worden bijgesneden wanneer deze op bepaalde apparaten worden afgespeeld.

![](assets/line_message_06.png)

## Toegang tot rapporten {#accessing-reports}

Nadat u de levering hebt verzonden, kunt u uw [!DNL LINE] rapporten via het menu **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** van de **[!UICONTROL Explorer]**.

>[!NOTE]
>
>De het volgen rapporten wijzen op het klikthrough tarief. [!DNL LINE] houdt geen rekening met de open rente.

![](assets/line_reports_01.png)

Voor [!DNL LINE] servicerapporten, toegang tot het menu **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Services and Subscriptions]** > **[!UICONTROL LINE-V2]** van de **[!UICONTROL Explorer]** tab. Klik vervolgens op de knop **[!UICONTROL Reports]** in het deelvenster [!DNL LINE] service.

![](assets/line_reports.png)

## Voorbeeld: een gepersonaliseerd lijnbericht maken en verzenden {#example--create-and-send-a-personalized-line-message}

In dit voorbeeld, gaan wij een tekstbericht en een beeld tot stand brengen en vormen die gegevens bevatten die volgens de ontvanger zullen worden gepersonaliseerd.

1. Maak uw [!DNL LINE] levering door op de knop **[!UICONTROL Create]** van de knop **[!UICONTROL Campaign]** tab.

   ![](assets/line_usecase.png)

1. Selecteer de **[!UICONTROL LINE V2 delivery]** leveringssjabloon en naam van levering.

   ![](assets/line_usecase_01.png)

1. Selecteer in het configuratievenster van uw levering de doelpopulatie.

   Raadpleeg voor meer informatie [Doelpopulaties identificeren](steps-defining-the-target-population.md).

   ![](assets/line_usecase_02.png)

1. Klikken **[!UICONTROL Add]** om uw bericht te creëren en selecteer **[!UICONTROL Content type]**.

   Hier willen we eerst een **[!UICONTROL Text message]**.

   ![](assets/line_usecase_03.png)

1. Plaats de cursor op de plaats waar u de gepersonaliseerde tekst wilt invoegen en klik op het vervolgkeuzepictogram en selecteer **[!UICONTROL Visitor]** > **[!UICONTROL First name]**.

   ![](assets/line_usecase_05.png)

1. Volg dezelfde procedure om een afbeelding toe te voegen, door **[!UICONTROL Image and links]** in de **[!UICONTROL Message type]** vervolgkeuzelijst.

   Voeg uw **[!UICONTROL Image URL]**.

   ![](assets/line_usecase_07.png)

1. In de **[!UICONTROL Links]** selecteert u de lay-out waarin de afbeelding wordt verdeeld in meerdere gebieden waarop kan worden geklikt.

1. Wijs een URL toe aan elk gebied van uw afbeelding.

   ![](assets/line_usecase_08.png)

1. Sla uw levering op en klik op **[!UICONTROL Send]** om te analyseren en naar het doel te verzenden.

   De levering wordt verzonden naar het doel.

   ![](assets/line_usecase_06.png)

