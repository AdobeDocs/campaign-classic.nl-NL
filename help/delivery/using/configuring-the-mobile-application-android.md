---
title: De mobiele Android-toepassing configureren in Adobe Campaign
description: Leer hoe u uw mobiele toepassing instelt voor Android
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dfa3938433fcd67eb8f38269e82ee1102eda41ce
workflow-type: tm+mt
source-wordcount: '1593'
ht-degree: 2%

---


# Configuratiestappen voor Android

Nadat het pakket is geïnstalleerd, kunt u de instellingen voor uw Android-app definiëren in Adobe Campaign Classic.

>[!NOTE]
>
>Raadpleeg deze [sectie](../../delivery/using/configuring-the-mobile-application.md)voor meer informatie over het configureren van uw app voor iOS en het maken van een levering voor iOS.

De belangrijkste stappen zijn:

1. [De externe Android-account configureren](#configuring-external-account-android)
1. [De Android-service configureren](#configuring-android-service)
1. [De mobiele app maken in Campagne](#creating-android-app)
1. [Het app-schema uitbreiden met aanvullende gegevens](#extend-subscription-schema)

Vervolgens kunt u een uitgebreide Android-melding [maken](#creating-android-delivery).

## Externe Android-account configureren {#configuring-external-account-android}

Voor Android zijn twee connectors beschikbaar:

* De V1 schakelaar die één verbinding per kind MTA toestaat.
* De V2-connector die gelijktijdige verbindingen met de FCM-server mogelijk maakt om de doorvoer te verbeteren.

Voer de volgende stappen uit om te kiezen welke aansluiting u wilt gebruiken:

1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**.
1. Select the **[!UICONTROL Android routing]** external account.
1. Vul op het **[!UICONTROL Connector]** tabblad het **[!UICONTROL JavaScript used in the connector]** veld in:

   Voor Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > U kunt het ook configureren als volgt: https://localhost:8080/nms/jsp/androidPushConnector.js, maar u wordt aangeraden versie 2 van de connector te gebruiken.

   ![](assets/nmac_connectors3.png)

1. Voor Android V2 is er één aanvullende parameter beschikbaar in het configuratiebestand van de Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Maximale limiet van parallelle HTTP-aanvragen voor de FCM die door elke onderliggende server worden geïnitieerd (standaard 8).

## Android-service configureren {#configuring-android-service}

1. Ga naar het **[!UICONTROL Profiles and Targets > Services and subscriptions]** knooppunt en klik **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Define a **[!UICONTROL Label]** and an **[!UICONTROL Internal name]**.
1. Ga naar het **[!UICONTROL Type]** veld en selecteer **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >De standaarddoelafbeelding is gekoppeld aan de tabel met ontvangers. **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** Als u een verschillende doelafbeelding wilt gebruiken, moet u een nieuwe doelafbeelding tot stand brengen en het ingaan op het **[!UICONTROL Target mapping]** gebied van de dienst. Voor meer bij het creëren van doelafbeelding, verwijs naar de gids [van de](../../configuration/using/about-custom-recipient-table.md)Configuratie.

   ![](assets/nmac_ios.png)

1. Klik vervolgens op de **[!UICONTROL Add]** knop om het toepassingstype te selecteren.

   ![](assets/nmac_service_2.png)

1. Maak uw Android-toepassing. Raadpleeg deze [sectie](../../delivery/using/configuring-the-mobile-application-android.md#creating-android-app) voor meer informatie.

## Android mobiele toepassing maken {#creating-android-app}

Nadat u de service hebt gemaakt, moet u nu uw Android-toepassing maken:

1. Klik vanuit de nieuwe service op de **[!UICONTROL Add]** knop om het toepassingstype te selecteren.

   ![](assets/nmac_service_2.png)

1. Selecteer **[!UICONTROL Create an Android application]** en typ een **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Zorg ervoor dat dit in Adobe Campaign en in de toepassingscode via de SDK **[!UICONTROL Integration key]** is gedefinieerd. Raadpleeg voor meer informatie: [Campagne SDK integreren in de mobiele toepassing](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > De eigenschap **[!UICONTROL Integration key]** is volledig aanpasbaar met tekenreekswaarde, maar moet exact hetzelfde zijn als de waarde die in de SDK is opgegeven.

1. Selecteer het **[!UICONTROL API version]**:

   * HTTPV1. De configuratie wordt gedetailleerd in deze [sectie](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1).
   * HTTP (verouderd). De configuratie wordt gedetailleerd in deze [sectie](../../delivery/using/configuring-the-mobile-application-android.md#android-service-http).


1. Fill in the **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** fields.

1. Klik op **[!UICONTROL Finish]** en vervolgens op **[!UICONTROL Save]**. Uw Android-toepassing kan nu worden gebruikt in Campaign Classic.

Standaard slaat Adobe Campaign een toets op in het veld **[!UICONTROL User identifier]** (@userKey) van de **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** tabel. Met deze sleutel kunt u een abonnement koppelen aan een ontvanger. Als u aanvullende gegevens wilt verzamelen (zoals een complexe afstemmingssleutel), moet u de volgende configuratie toepassen:

### Selecteer de API-versie{#select-api-version}

Nadat u de service en een nieuwe mobiele toepassing hebt gemaakt, moet u de mobiele toepassing configureren, afhankelijk van de gekozen API-versie.

Raadpleeg deze [sectie voor meer informatie over het maken van services en mobiele toepassingen](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service)

#### HTTP v1 API-versie gebruiken{#android-service-httpv1}

Voer de volgende stappen uit om de HTTP v1 API-versie te configureren:

1. Selecteer in uw **[!UICONTROL Mobile application creation wizard]** venster **[!UICONTROL HTTPV1]** de **[!UICONTROL API version]** vervolgkeuzelijst.

1. Klik **[!UICONTROL Load project json file to extract projet details...]** om het JSON-sleutelbestand rechtstreeks te laden. Raadpleeg deze [pagina](https://firebase.google.com/docs/admin/setup#initialize-sdk)voor meer informatie over het uitpakken van uw JSON-bestand.

   U kunt ook handmatig de volgende gegevens invoeren:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Klik **[!UICONTROL Test the connection]** om te controleren of uw configuratie correct is en of de marketingserver toegang heeft tot de FCM.

   >[!CAUTION]
   >
   >Voor Mid-sourcing Plaatsing, zal de **[!UICONTROL Test connection]** knoop niet controleren of de server MID toegang tot de server FCM heeft.

   ![](assets/nmac_android_11.png)

1. U kunt desgewenst ook de inhoud van een pushbericht verrijken met andere inhoud **[!UICONTROL Application variables]** . Deze zijn volledig aanpasbaar en een deel van de berichtlading wordt verzonden naar het mobiele apparaat.

1. Klik op **[!UICONTROL Finish]** en vervolgens op **[!UICONTROL Save]**. Uw Android-toepassing kan nu worden gebruikt in Campaign Classic.

Hieronder vindt u de namen van FCM-ladingen om uw pushmelding verder aan te passen:

| Berichttype | Configureerbaar berichtelement (FCM-ladenaam) | Configureerbare opties (FCM-ladenaam) |
|:-:|:-:|:-:|
| gegevensbericht | N.v.t. | validate_only |
| meldingsbericht | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

<br>
<br>

#### HTTP API-versie{#android-service-http}

Voer de volgende stappen uit om de HTTP-versie (verouderd) te configureren:

1. Selecteer in uw **[!UICONTROL Mobile application creation wizard]** venster **[!UICONTROL HTTP (legacy)]** de **[!UICONTROL API version]** vervolgkeuzelijst.

1. Voer de gegevens in **[!UICONTROL Project key]** die door de ontwikkelaar van de mobiele toepassing zijn opgegeven.

1. U kunt desgewenst ook de inhoud van een pushbericht verrijken met andere inhoud **[!UICONTROL Application variables]** . Deze zijn volledig aanpasbaar en een deel van de berichtlading wordt verzonden naar het mobiele apparaat.

   In het volgende voorbeeld voegen we een **titel**, **imageURL** en **iconURL** toe om uitgebreide pushmeldingen te maken. Vervolgens krijgen de toepassing de afbeelding, titel en het pictogram te zien die binnen het bericht worden weergegeven.

   ![](assets/nmac_android_2.png)

1. Klik op **[!UICONTROL Finish]** en vervolgens op **[!UICONTROL Save]**. Uw Android-toepassing kan nu worden gebruikt in Campaign Classic.

Hieronder vindt u de namen van FCM-ladingen om uw pushmelding verder aan te passen:

| Berichttype | Configureerbaar berichtelement (FCM-ladenaam) | Configureerbare opties (FCM-ladenaam) |
|:-:|:-:|:-:|
| gegevensbericht | N.v.t. | dryRun |
| meldingsbericht | title, body, android_channel_id, icon, sound, tag, color, click_action <br> | dryRun |

<br>

## Het schema appsubscriptionRcp uitbreiden {#extend-subscription-schema}

U moet het **appsubscriptionRcp** uitbreiden om nieuwe extra gebieden te bepalen om parameters van app in het gegevensbestand van de Campagne op te slaan. Deze velden worden bijvoorbeeld gebruikt voor personalisatie. Dit doet u als volgt:

1. Maak een extensie van het **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schema en definieer de nieuwe velden. Meer informatie over schema-extensies vindt u op [deze pagina](../../configuration/using/about-schema-edition.md)

1. Definieer de toewijzing op het **[!UICONTROL Subscription parameters]** tabblad.

   >[!CAUTION]
   >
   >Zorg ervoor dat de configuratienamen op het **[!UICONTROL Subscription parameters]** tabblad gelijk zijn aan die in de code van de mobiele toepassing. Raadpleeg de [Integrating Campaign SDK in de sectie over mobiele toepassingen](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md) .


## Android-berichten maken {#creating-android-delivery}

Met Firebase Cloud Messaging kunt u kiezen uit twee typen berichten:

* **[!UICONTROL Data message]**, afgehandeld door de clienttoepassing.
   <br>De berichten worden verzonden rechtstreeks naar de mobiele toepassing die het android bericht aan het apparaat zal produceren en tonen. Gegevensberichten bevatten alleen aangepaste toepassingsvariabelen.

* **[!UICONTROL Notification message]**, automatisch afgehandeld door de FCM SDK.
   <br> FCM geeft automatisch het bericht weer op de apparaten van uw gebruikers namens de client-app. Meldingsberichten bevatten een vooraf gedefinieerde set parameters en opties, maar kunnen nog steeds verder worden aangepast met aangepaste toepassingsvariabelen.

Raadpleeg de [FCM-documentatie](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages)voor meer informatie over de berichttypen in Firebase Cloud Messaging.

### Een gegevensbericht maken {#creating-data-message}

1. Ga naar **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klik op **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecteer **[!UICONTROL Deliver on Android (android)]** in de **[!UICONTROL Delivery template]** drop-down. Voeg een **[!UICONTROL Label]** object toe aan uw levering.

1. Klik **[!UICONTROL To]** om de populatie te bepalen die moet worden gericht. Standaard wordt de **[!UICONTROL Subscriber application]** doeltoewijzing toegepast. Klik **[!UICONTROL Add]** om uw service te selecteren.

   ![](assets/nmac_android_7.png)

1. Selecteer in het **[!UICONTROL Target type]** venster **[!UICONTROL Subscribers of an Android mobile application]** en klik op **[!UICONTROL Next]**.

1. Selecteer in de **[!UICONTROL Service]** vervolgkeuzelijst eerst de eerder gemaakte service en vervolgens de toepassing en klik op **[!UICONTROL Finish]**.
Het **[!UICONTROL Application variables]** wordt automatisch toegevoegd afhankelijk van wat tijdens de configuratiestappen werd toegevoegd.

   ![](assets/nmac_android_6.png)

1. Selecteren **[!UICONTROL data message]** als **[!UICONTROL Message Type]**.

1. Bewerk uw uitgebreide melding.

   ![](assets/nmac_android_5.png)

1. U kunt informatie in eerder gevormd toevoegen **[!UICONTROL Application variables]** indien nodig. **[!UICONTROL Application variables]** moet worden geconfigureerd in de Android-service en maakt deel uit van de berichtlading die naar het mobiele apparaat wordt verzonden.

1. Klik en verzend uw levering. **[!UICONTROL Save]**

De afbeelding en webpagina moeten worden weergegeven in het pushbericht wanneer deze worden ontvangen op de mobiele Android-apparaten van de abonnees.

![](assets/nmac_android_4.png)

### Een meldingsbericht maken {#creating-notification-message}

>[!NOTE]
>
>Aanvullende opties voor berichten zijn alleen beschikbaar bij de HTTP v1 API-configuratie. Raadpleeg deze [sectie](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1) voor meer informatie.

1. Ga naar **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klik op **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecteer **[!UICONTROL Deliver on Android (android)]** in de **[!UICONTROL Delivery template]** drop-down. Voeg een **[!UICONTROL Label]** object toe aan uw levering.

1. Klik **[!UICONTROL To]** om de populatie te bepalen die moet worden gericht. Standaard wordt de **[!UICONTROL Subscriber application]** doeltoewijzing toegepast. Klik **[!UICONTROL Add]** om uw service te selecteren.

   ![](assets/nmac_android_7.png)

1. Selecteer in het **[!UICONTROL Target type]** venster **[!UICONTROL Subscribers of an Android mobile application]** en klik op **[!UICONTROL Next]**.

1. Selecteer in de **[!UICONTROL Service]** vervolgkeuzelijst eerst de eerder gemaakte service en vervolgens de toepassing en klik op **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. Selecteren **[!UICONTROL notification message]** als **[!UICONTROL Message Type]**.

1. Voeg een titel toe en bewerk uw bericht. Pas uw pushmelding aan met de **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: Stel de kanaal-id van uw melding in. De app moet een kanaal met deze kanaal-id maken voordat meldingen met deze kanaal-id worden ontvangen.
   * **[!UICONTROL Sound]**: Stel het geluid in dat moet worden afgespeeld wanneer het apparaat het bericht ontvangt.
   * **[!UICONTROL Color]**: Stel de kleur van het pictogram van uw melding in.
   * **[!UICONTROL Icon]**: Stel het pictogram van het bericht in op weergave op de apparaten van uw profielen.
   * **[!UICONTROL Tag]**: Stel de id in die wordt gebruikt om bestaande meldingen in de meldingslade te vervangen.
   * **[!UICONTROL Click action]**: Stel de handeling in die aan een gebruiker is gekoppeld, en klik op het bericht.

   Raadpleeg de **[!UICONTROL Notification options]** FCM-documentatie [voor meer informatie over het invullen van deze velden](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification)en hoe u deze kunt invullen.

   ![](assets/nmac_android_8.png)

1. Als uw toepassing is geconfigureerd met het HTTP v1 API-protocol, kunt u uw pushmelding verder aanpassen met het volgende **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: Stel de tekst van de markering in voor uw melding. Alleen beschikbaar voor apparaten die zijn ingesteld op Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: Stel de URL van de afbeelding in die in uw melding moet worden weergegeven.
   * **[!UICONTROL Notification Count]**: Stel het aantal nieuwe ongelezen gegevens in dat u rechtstreeks op het toepassingspictogram wilt weergeven.
   * **[!UICONTROL Sticky]**: Ingesteld op true of false. Indien ingesteld op false, wordt het bericht automatisch genegeerd wanneer de gebruiker erop klikt. Indien ingesteld op true, wordt het bericht nog steeds weergegeven, zelfs wanneer de gebruiker erop klikt.
   * **[!UICONTROL Notification Priority]**: Plaats de prioritaire niveaus van uw bericht aan gebrek, minimum, laag of hoog. For more on this, refer to [FCM documentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: Stel de zichtbaarheidsniveaus van uw melding in op openbaar, privé of geheim. For more on this, refer to [FCM documentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Raadpleeg de **[!UICONTROL HTTP v1 additional options]** FCM-documentatie [voor meer informatie over het invullen van deze velden](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification)en hoe u deze kunt invullen.

   ![](assets/nmac_android_9.png)

1. U kunt informatie in eerder gevormd toevoegen **[!UICONTROL Application variables]** indien nodig. **[!UICONTROL Application variables]** moet worden geconfigureerd in de Android-service en maakt deel uit van de berichtlading die naar het mobiele apparaat wordt verzonden.

1. Klik en verzend uw levering. **[!UICONTROL Save]**

De afbeelding en webpagina moeten worden weergegeven in het pushbericht wanneer deze worden ontvangen op de mobiele Android-apparaten van de abonnees.
