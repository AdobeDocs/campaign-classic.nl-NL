---
solution: Campaign Classic
product: campaign
title: De mobiele Android-toepassing configureren in Adobe Campaign
description: Leer hoe u uw mobiele toepassing instelt voor Android
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1d7d48f52f69e4902eafa6806c2cd9170c21fe5a
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 2%

---


# Configuratiestappen voor Android

Nadat het pakket is geïnstalleerd, kunt u de instellingen voor uw Android-app definiëren in Adobe Campaign Classic.

>[!NOTE]
>
>Raadpleeg deze [sectie](../../delivery/using/configuring-the-mobile-application.md) voor meer informatie over het configureren van uw app voor iOS en het maken van een levering voor iOS.

De belangrijkste stappen zijn:

1. [De externe Android-account configureren](#configuring-external-account-android)
1. [De Android-service configureren](#configuring-android-service)
1. [De mobiele app maken in Campagne](#creating-android-app)
1. [Het app-schema uitbreiden met aanvullende gegevens](#extend-subscription-schema)

Vervolgens kunt u [een uitgebreide Android-melding maken](#creating-android-delivery).

## Externe Android-account {#configuring-external-account-android} configureren

Voor Android zijn twee connectors beschikbaar:

* De V1 schakelaar die één verbinding per kind MTA toestaat.
* De V2-connector die gelijktijdige verbindingen met de FCM-server mogelijk maakt om de doorvoer te verbeteren.

Voer de volgende stappen uit om te kiezen welke aansluiting u wilt gebruiken:

1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecteer de externe account **[!UICONTROL Android routing]**.
1. Vul op het tabblad **[!UICONTROL Connector]** het veld **[!UICONTROL JavaScript used in the connector]** in:

   Voor Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > U kunt het ook configureren als volgt: https://localhost:8080/nms/jsp/androidPushConnector.js, maar u wordt aangeraden versie 2 van de connector te gebruiken.

   ![](assets/nmac_connectors3.png)

1. Voor Android V2 is er één aanvullende parameter beschikbaar in het configuratiebestand van de Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Maximale limiet van parallelle HTTP-aanvragen voor de FCM die door elke onderliggende server worden geïnitieerd (standaard 8).

## Android-service {#configuring-android-service} configureren

![](assets/do-not-localize/how-to-video.png) [Leer hoe u een Android-service configureert in video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. Ga naar **[!UICONTROL Profiles and Targets > Services and subscriptions]** knoop en klik **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definieer een **[!UICONTROL Label]** en een **[!UICONTROL Internal name]**.
1. Ga naar het **[!UICONTROL Type]** gebied en selecteer **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >De standaard **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** doelafbeelding is gekoppeld aan de tabel met ontvangers. Als u een verschillende doelafbeelding wilt gebruiken, moet u een nieuwe doelafbeelding maken en deze invoeren in het veld **[!UICONTROL Target mapping]** van de service. Voor meer bij het creëren van doelafbeelding, verwijs naar [de gids van de Configuratie](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klik vervolgens op de knop **[!UICONTROL Add]** om het toepassingstype te selecteren.

   ![](assets/nmac_service_2.png)

1. Maak uw Android-toepassing. Raadpleeg deze [sectie](../../delivery/using/configuring-the-mobile-application-android.md#creating-android-app) voor meer informatie.

## Mobiele Android-toepassing {#creating-android-app} maken

Nadat u de service hebt gemaakt, moet u nu uw Android-toepassing maken:

1. Klik op de knop **[!UICONTROL Add]** van de zojuist gemaakte service om het toepassingstype te selecteren.

   ![](assets/nmac_service_2.png)

1. Selecteer **[!UICONTROL Create an Android application]** en ga **[!UICONTROL Label]** in.

   ![](assets/nmac_android.png)

1. Zorg ervoor dat **[!UICONTROL Integration key]** in Adobe Campaign en in de toepassingscode via de SDK wordt gedefinieerd. Raadpleeg voor meer informatie: [De campagne-SDK integreren in de mobiele toepassing](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** is volledig aanpasbaar met koordwaarde maar moet precies het zelfde zijn zoals gespecificeerd in SDK.

1. Selecteer **[!UICONTROL API version]**: HTTP v1 of HTTP (verouderd). Deze configuraties worden beschreven in [deze sectie](#select-api-version)

1. Vul de **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** gebieden in.

1. Klik op **[!UICONTROL Finish]** en vervolgens op **[!UICONTROL Save]**. Uw Android-toepassing kan nu worden gebruikt in Campaign Classic.

Standaard slaat Adobe Campaign een toets op in het veld **[!UICONTROL User identifier]** (@userKey) van de tabel **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**. Met deze sleutel kunt u een abonnement koppelen aan een ontvanger. Als u aanvullende gegevens wilt verzamelen (zoals een complexe afstemmingssleutel), moet u de volgende configuratie toepassen:

### Selecteer de API-versie{#select-api-version}

Nadat u de service en een nieuwe mobiele toepassing hebt gemaakt, moet u de mobiele toepassing configureren, afhankelijk van de gekozen API-versie.

* **De HTTP v1** configuratie is gedetailleerd in deze  [sectie](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1).
* **De (erfenis)** configuratie van HTTP is gedetailleerd in deze  [sectie](../../delivery/using/configuring-the-mobile-application-android.md#android-service-http).

#### HTTP v1 API{#android-service-httpv1} configureren

Voer de volgende stappen uit om de HTTP v1 API-versie te configureren:

1. Selecteer **[!UICONTROL HTTPV1]** in de vervolgkeuzelijst **[!UICONTROL API version]** in het venster **[!UICONTROL Mobile application creation wizard]**.

1. Klik **[!UICONTROL Load project json file to extract projet details...]** om uw JSON-sleutelbestand rechtstreeks te laden. Raadpleeg deze [pagina](https://firebase.google.com/docs/admin/setup#initialize-sdk) voor meer informatie over het uitpakken van uw JSON-bestand.

   U kunt ook handmatig de volgende gegevens invoeren:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Klik **[!UICONTROL Test the connection]** om te controleren of uw configuratie correct is en of de marketingserver toegang heeft tot de FCM.

   >[!CAUTION]
   >
   >Voor Mid-sourcing-implementatie controleert de knop **[!UICONTROL Test connection]** niet of de MID-server toegang heeft tot de FCM-server.

   ![](assets/nmac_android_11.png)

1. Als optie kunt u de inhoud van een pushbericht desgewenst verrijken met **[!UICONTROL Application variables]**. Deze zijn volledig aanpasbaar en een deel van de berichtlading wordt verzonden naar het mobiele apparaat.

1. Klik op **[!UICONTROL Finish]** en vervolgens op **[!UICONTROL Save]**. Uw Android-toepassing kan nu worden gebruikt in Campaign Classic.

Hieronder vindt u de namen van FCM-ladingen om uw pushmelding verder aan te passen:

| Berichttype | Configureerbaar berichtelement (FCM-ladenaam) | Configureerbare opties (FCM-ladenaam) |
|:-:|:-:|:-:|
| gegevensbericht | N.v.t. | validate_only |
| meldingsbericht | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

<br>
<br>

#### HTTP-API (verouderd) configureren{#android-service-http}

Voer de volgende stappen uit om de HTTP-versie (verouderd) te configureren:

1. Selecteer **[!UICONTROL HTTP (legacy)]** in de vervolgkeuzelijst **[!UICONTROL API version]** in het venster **[!UICONTROL Mobile application creation wizard]**.

1. Voer de **[!UICONTROL Project key]** in die door de ontwikkelaar van de mobiele toepassing is opgegeven.

1. Als optie kunt u de inhoud van een pushbericht desgewenst verrijken met **[!UICONTROL Application variables]**. Deze zijn volledig aanpasbaar en een deel van de berichtlading wordt verzonden naar het mobiele apparaat.

   In het volgende voorbeeld voegen we **title**, **imageURL** en **iconURL** toe om een uitgebreide pushmelding te maken en geven we de toepassing vervolgens de afbeelding, titel en het pictogram weer die binnen de melding worden weergegeven.

   ![](assets/nmac_android_2.png)

1. Klik op **[!UICONTROL Finish]** en vervolgens op **[!UICONTROL Save]**. Uw Android-toepassing kan nu worden gebruikt in Campaign Classic.

Hieronder vindt u de namen van FCM-ladingen om uw pushmelding verder aan te passen:

| Berichttype | Configureerbaar berichtelement (FCM-ladenaam) | Configureerbare opties (FCM-ladenaam) |
|:-:|:-:|:-:|
| gegevensbericht | N.v.t. | dryRun |
| meldingsbericht | title, body, android_channel_id, icon, sound, tag, color, click_action <br> | dryRun |

<br>

## Het schema appsubscriptionRcp {#extend-subscription-schema} uitbreiden

![](assets/do-not-localize/how-to-video.png) [Leer hoe u het schema appsubscriptionRcp in video kunt uitbreiden](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

U moet **appsubscriptionRcp** uitbreiden om nieuwe extra gebieden te bepalen om parameters van app in het gegevensbestand van de Campagne op te slaan. Deze velden worden bijvoorbeeld gebruikt voor personalisatie. Dit doet u als volgt:

1. Maak een extensie van het schema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** en definieer de nieuwe velden. Meer informatie over schemaextensie in [deze pagina](../../configuration/using/about-schema-edition.md)

1. Definieer de toewijzing op het tabblad **[!UICONTROL Subscription parameters]**.

   >[!CAUTION]
   >
   >Zorg ervoor dat de configuratienamen op het tabblad **[!UICONTROL Subscription parameters]** gelijk zijn aan die in de code van de mobiele toepassing. Raadpleeg de sectie [Campagne SDK integreren in de mobiele toepassing](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

## Android-waarschuwingen maken {#creating-android-delivery}

Met Firebase Cloud Messaging kunt u kiezen uit twee typen berichten:

* **[!UICONTROL Data message]**, afgehandeld door de clienttoepassing.
   <br>De berichten worden verzonden rechtstreeks naar de mobiele toepassing die het android bericht aan het apparaat zal produceren en tonen. Gegevensberichten bevatten alleen aangepaste toepassingsvariabelen.

* **[!UICONTROL Notification message]**, automatisch afgehandeld door de FCM SDK.
   <br> FCM geeft automatisch het bericht weer op de apparaten van uw gebruikers namens de client-app. Meldingsberichten bevatten een vooraf gedefinieerde set parameters en opties, maar kunnen nog steeds verder worden aangepast met aangepaste toepassingsvariabelen.

Raadpleeg [FCM-documentatie](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages) voor meer informatie over de berichttypen in Firebase Cloud Messaging.

### Gegevensbericht {#creating-data-message} maken

1. Ga naar **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klik op **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecteer **[!UICONTROL Deliver on Android (android)]** in **[!UICONTROL Delivery template]** drop-down. Voeg een **[!UICONTROL Label]** aan uw levering toe.

1. Klik op **[!UICONTROL To]** om de doelpopulatie te definiëren. Standaard wordt de **[!UICONTROL Subscriber application]**-doeltoewijzing toegepast. Klik **[!UICONTROL Add]** om uw dienst te selecteren.

   ![](assets/nmac_android_7.png)

1. Selecteer **[!UICONTROL Target type]** in het venster &lt;a0/> en klik **[!UICONTROL Next]**.**[!UICONTROL Subscribers of an Android mobile application]**

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Service]** de eerder gemaakte service en klik vervolgens op **[!UICONTROL Finish]**.
**[!UICONTROL Application variables]** worden automatisch toegevoegd afhankelijk van wat tijdens de configuratiestappen werd toegevoegd.

   ![](assets/nmac_android_6.png)

1. Selecteer **[!UICONTROL data message]** als **[!UICONTROL Message Type]**.

1. Bewerk uw uitgebreide melding.

   ![](assets/nmac_android_5.png)

1. U kunt informatie in uw eerder gevormde **[!UICONTROL Application variables]** indien nodig toevoegen. **[!UICONTROL Application variables]** moet worden geconfigureerd in de Android-service en maakt deel uit van de berichtlading die naar het mobiele apparaat wordt verzonden.

1. Klik **[!UICONTROL Save]** en verzend uw levering.

De afbeelding en webpagina moeten worden weergegeven in het pushbericht wanneer deze worden ontvangen op de mobiele Android-apparaten van de abonnees.

![](assets/nmac_android_4.png)

### Een meldingsbericht maken {#creating-notification-message}

>[!NOTE]
>
>Aanvullende opties voor berichten zijn alleen beschikbaar bij de HTTP v1 API-configuratie. Raadpleeg deze [sectie](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1) voor meer informatie.

![](assets/do-not-localize/how-to-video.png) [Leer hoe u een Android-pushmelding maakt in video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. Ga naar **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klik op **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecteer **[!UICONTROL Deliver on Android (android)]** in **[!UICONTROL Delivery template]** drop-down. Voeg een **[!UICONTROL Label]** aan uw levering toe.

1. Klik op **[!UICONTROL To]** om de doelpopulatie te definiëren. Standaard wordt de **[!UICONTROL Subscriber application]**-doeltoewijzing toegepast. Klik **[!UICONTROL Add]** om uw dienst te selecteren.

   ![](assets/nmac_android_7.png)

1. Selecteer **[!UICONTROL Target type]** in het venster &lt;a0/> en klik **[!UICONTROL Next]**.**[!UICONTROL Subscribers of an Android mobile application]**

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Service]** de eerder gemaakte service en klik vervolgens op **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. Selecteer **[!UICONTROL notification message]** als **[!UICONTROL Message Type]**.

1. Voeg een titel toe en bewerk uw bericht. Pas uw pushmelding aan met de **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: Stel de kanaal-id van uw melding in. De app moet een kanaal met deze kanaal-id maken voordat meldingen met deze kanaal-id worden ontvangen.
   * **[!UICONTROL Sound]**: Stel het geluid in dat moet worden afgespeeld wanneer het apparaat het bericht ontvangt.
   * **[!UICONTROL Color]**: Stel de kleur van het pictogram van uw melding in.
   * **[!UICONTROL Icon]**: Stel het pictogram van het bericht in op weergave op de apparaten van uw profielen.
   * **[!UICONTROL Tag]**: Stel de id in die wordt gebruikt om bestaande meldingen in de meldingslade te vervangen.
   * **[!UICONTROL Click action]**: Stel de handeling in die aan een gebruiker is gekoppeld, en klik op het bericht.

   Raadpleeg [FCM-documentatie](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification) voor meer informatie over **[!UICONTROL Notification options]** en hoe u deze velden invult.

   ![](assets/nmac_android_8.png)

1. Als uw toepassing met het protocol van HTTP v1 API wordt gevormd, kunt u uw dupmelding verder personaliseren met het volgende **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: Stel de tekst van de markering in voor uw melding. Alleen beschikbaar voor apparaten die zijn ingesteld op Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: Stel de URL van de afbeelding in die in uw melding moet worden weergegeven.
   * **[!UICONTROL Notification Count]**: Stel het aantal nieuwe ongelezen gegevens in dat u rechtstreeks op het toepassingspictogram wilt weergeven.
   * **[!UICONTROL Sticky]**: Ingesteld op true of false. Indien ingesteld op false, wordt het bericht automatisch genegeerd wanneer de gebruiker erop klikt. Indien ingesteld op true, wordt het bericht nog steeds weergegeven, zelfs wanneer de gebruiker erop klikt.
   * **[!UICONTROL Notification Priority]**: Plaats de prioritaire niveaus van uw bericht aan gebrek, minimum, laag of hoog. Raadpleeg [FCM-documentatie](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority) voor meer informatie.
   * **[!UICONTROL Visibility]**: Stel de zichtbaarheidsniveaus van uw melding in op openbaar, privé of geheim. Raadpleeg [FCM-documentatie](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility) voor meer informatie.

   Raadpleeg [FCM-documentatie](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification) voor meer informatie over **[!UICONTROL HTTP v1 additional options]** en hoe u deze velden invult.

   ![](assets/nmac_android_9.png)

1. U kunt informatie in uw eerder gevormde **[!UICONTROL Application variables]** indien nodig toevoegen. **[!UICONTROL Application variables]** moet worden geconfigureerd in de Android-service en maakt deel uit van de berichtlading die naar het mobiele apparaat wordt verzonden.

1. Klik **[!UICONTROL Save]** en verzend uw levering.

De afbeelding en webpagina moeten worden weergegeven in het pushbericht wanneer deze worden ontvangen op de mobiele Android-apparaten van de abonnees.
