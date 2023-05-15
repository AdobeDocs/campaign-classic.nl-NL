---
product: campaign
title: Een pushmelding maken voor Android-apparaten
description: Meer informatie over het maken van pushmeldingen voor Android
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Push
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 1%

---

# Meldingen maken voor Android{#create-notificaations-android}



Gebruik Adobe Campaign om pushmeldingen te verzenden op Android-apparaten. Algemene concepten voor het creëren van levering worden weergegeven in [deze sectie](steps-about-delivery-creation-steps.md).

Begin door een nieuwe levering te maken.

![](assets/nmac_delivery_1.png)

Met Firebase Cloud Messaging kunt u kiezen uit twee typen berichten:

* **[!UICONTROL Data message]**, afgehandeld door de clienttoepassing.
   <br>De berichten worden verzonden rechtstreeks naar de mobiele toepassing die het android bericht aan het apparaat zal produceren en tonen. Gegevensberichten bevatten alleen aangepaste toepassingsvariabelen.

* **[!UICONTROL Notification message]**, automatisch afgehandeld door de FCM SDK.
   <br> FCM geeft automatisch het bericht weer op de apparaten van uw gebruikers namens de client-app. Meldingsberichten bevatten een vooraf gedefinieerde set parameters en opties, maar kunnen nog steeds verder worden aangepast met aangepaste toepassingsvariabelen.

Raadpleeg voor meer informatie over berichten in Firebase Cloud [FCM-documentatie](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages).

## Een gegevensbericht maken {#creating-data-message}

1. Ga naar **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klik op **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecteren **[!UICONTROL Deliver on Android (android)]** in de **[!UICONTROL Delivery template]** vervolgkeuzelijst. Voeg een **[!UICONTROL Label]** op uw levering.

1. Klikken **[!UICONTROL To]** om de doelgroep te bepalen. Standaard worden de **[!UICONTROL Subscriber application]** doeltoewijzing wordt toegepast. Klikken **[!UICONTROL Add]** om uw service te selecteren.

   ![](assets/nmac_android_7.png)

1. In de **[!UICONTROL Target type]** venster, selecteert u **[!UICONTROL Subscribers of an Android mobile application]** en klik op **[!UICONTROL Next]**.

1. In de **[!UICONTROL Service]** drop-down, selecteer uw eerder gecreeerde dienst dan toepassing en klik **[!UICONTROL Finish]**.
De **[!UICONTROL Application variables]** worden automatisch toegevoegd afhankelijk van wat tijdens de configuratiestappen werd toegevoegd.

   ![](assets/nmac_android_6.png)

1. Selecteren **[!UICONTROL data message]** als **[!UICONTROL Message Type]**.

1. Bewerk uw uitgebreide melding.

   ![](assets/nmac_android_5.png)

1. U kunt informatie toevoegen in uw eerder geconfigureerde **[!UICONTROL Application variables]** indien nodig. **[!UICONTROL Application variables]** moet worden geconfigureerd in de Android-service en maakt deel uit van de berichtlading die naar het mobiele apparaat wordt verzonden.

1. Klikken **[!UICONTROL Save]** en verzend uw levering.

De afbeelding en webpagina moeten worden weergegeven in het pushbericht wanneer deze worden ontvangen op de mobiele Android-apparaten van de abonnees.

![](assets/nmac_android_4.png)

## Een meldingsbericht maken {#creating-notification-message}

>[!NOTE]
>
>Aanvullende opties voor berichten zijn alleen beschikbaar bij de HTTP v1 API-configuratie. Raadpleeg deze [sectie](configuring-the-mobile-application-android.md#android-service-httpv1) voor meer informatie.

![](assets/do-not-localize/how-to-video.png) [Leer hoe u een Android-pushmelding maakt in video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. Ga naar **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klik op **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecteren **[!UICONTROL Deliver on Android (android)]** in de **[!UICONTROL Delivery template]** vervolgkeuzelijst. Voeg een **[!UICONTROL Label]** op uw levering.

1. Klikken **[!UICONTROL To]** om de doelgroep te bepalen. Standaard worden de **[!UICONTROL Subscriber application]** doeltoewijzing wordt toegepast. Klikken **[!UICONTROL Add]** om uw service te selecteren.

   ![](assets/nmac_android_7.png)

1. In de **[!UICONTROL Target type]** venster, selecteert u **[!UICONTROL Subscribers of an Android mobile application]** en klik op **[!UICONTROL Next]**.

1. In de **[!UICONTROL Service]** drop-down, selecteer uw eerder gecreeerde dienst dan toepassing en klik **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. Selecteren **[!UICONTROL notification message]** als **[!UICONTROL Message Type]**.

1. Voeg een titel toe en bewerk uw bericht. Pas uw pushmelding aan met de **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: Stel de kanaal-id van uw melding in. De app moet een kanaal met deze kanaal-id maken voordat meldingen met deze kanaal-id worden ontvangen.
   * **[!UICONTROL Sound]**: Stel het geluid in dat moet worden afgespeeld wanneer het apparaat het bericht ontvangt.
   * **[!UICONTROL Color]**: Stel de kleur van het pictogram van uw melding in.
   * **[!UICONTROL Icon]**: Stel het pictogram van het bericht in op weergave op de apparaten van uw profielen.
   * **[!UICONTROL Tag]**: Stel de id in die wordt gebruikt om bestaande meldingen in de meldingslade te vervangen.
   * **[!UICONTROL Click action]**: Stel de handeling in die aan een gebruiker is gekoppeld, en klik op het bericht.

   Voor meer informatie over **[!UICONTROL Notification options]** en hoe u deze velden kunt vullen, raadpleegt u [FCM-documentatie](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_8.png)

1. Als uw toepassing is geconfigureerd met het HTTP v1 API-protocol, kunt u uw pushmelding verder personaliseren met het volgende **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: Stel de tekst van de markering in voor uw melding. Alleen beschikbaar voor apparaten die zijn ingesteld op Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: Stel de URL van de afbeelding in die in uw melding moet worden weergegeven.
   * **[!UICONTROL Notification Count]**: Stel het aantal nieuwe ongelezen gegevens in dat u rechtstreeks op het toepassingspictogram wilt weergeven.
   * **[!UICONTROL Sticky]**: Ingesteld op true of false. Indien ingesteld op false, wordt het bericht automatisch genegeerd wanneer de gebruiker erop klikt. Indien ingesteld op true, wordt het bericht nog steeds weergegeven, zelfs wanneer de gebruiker erop klikt.
   * **[!UICONTROL Notification Priority]**: Plaats de prioritaire niveaus van uw bericht aan gebrek, minimum, laag of hoog. Raadpleeg voor meer informatie hierover [FCM-documentatie](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: Stel de zichtbaarheidsniveaus van uw melding in op openbaar, privé of geheim. Raadpleeg voor meer informatie hierover [FCM-documentatie](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Voor meer informatie over **[!UICONTROL HTTP v1 additional options]** en hoe u deze velden kunt vullen, raadpleegt u [FCM-documentatie](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_9.png)

1. U kunt informatie toevoegen in uw eerder geconfigureerde **[!UICONTROL Application variables]** indien nodig. **[!UICONTROL Application variables]** moet worden geconfigureerd in de Android-service en maakt deel uit van de berichtlading die naar het mobiele apparaat wordt verzonden.

1. Klikken **[!UICONTROL Save]** en verzend uw levering.

De afbeelding en webpagina moeten worden weergegeven in het pushbericht wanneer deze worden ontvangen op de mobiele Android-apparaten van de abonnees.
