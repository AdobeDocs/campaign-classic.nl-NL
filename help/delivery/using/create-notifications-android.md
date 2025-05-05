---
product: campaign
title: Een pushmelding maken voor Android-apparaten
description: Meer informatie over het maken van pushmeldingen voor Android
feature: Push
role: User, Developer, Data Engineer
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Meldingen maken voor Android{#create-notificaations-android}

Gebruik Adobe Campaign om pushmeldingen te verzenden op Android-apparaten. De globale concepten op leveringsverwezenlijking worden voorgesteld in [ deze sectie ](steps-about-delivery-creation-steps.md).

Begin door een nieuwe levering te maken.

![](assets/nmac_delivery_1.png)

Met Firebase Cloud Messaging kunt u kiezen uit twee typen berichten:

* **[!UICONTROL Data message]** wordt afgehandeld door de clienttoepassing.
  <br> de Berichten worden verzonden rechtstreeks naar de mobiele toepassing die het android bericht aan het apparaat zal produceren en tonen. Gegevensberichten bevatten alleen aangepaste toepassingsvariabelen.

* **[!UICONTROL Notification message]**, automatisch afgehandeld door de FCM SDK.
  <br> FCM geeft automatisch het bericht weer op de apparaten van uw gebruikers namens de client-app. Meldingsberichten bevatten een vooraf gedefinieerde set parameters en opties, maar kunnen nog steeds verder worden aangepast met aangepaste toepassingsvariabelen.

Voor meer informatie over de berichttypes van het Overseinen van de Wolk van de Wolk van de Vuurbasis, verwijs naar [ documentatie FCM ](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages){target="_blank"} .


## Een gegevensbericht maken {#creating-data-message}

1. Ga naar **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** .

1. Klik op **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecteer **[!UICONTROL Deliver on Android (android)]** in de vervolgkeuzelijst **[!UICONTROL Delivery template]** . Voeg een **[!UICONTROL Label]** toe aan uw levering.

1. Klik op **[!UICONTROL To]** om de doelpopulatie te definiëren. Standaard wordt de doeltoewijzing **[!UICONTROL Subscriber application]** toegepast. Klik op **[!UICONTROL Add]** om uw service te selecteren.

   ![](assets/nmac_android_7.png)

1. Selecteer **[!UICONTROL Subscribers of an Android mobile application]** in het **[!UICONTROL Target type]** -venster en klik op **[!UICONTROL Next]** .

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Service]** eerst de eerder gemaakte service en vervolgens de toepassing en klik op **[!UICONTROL Finish]** .
**[!UICONTROL Application variables]** wordt automatisch toegevoegd afhankelijk van wat tijdens de configuratiestappen werd toegevoegd.

   ![](assets/nmac_android_6.png)

1. Selecteer **[!UICONTROL data message]** als **[!UICONTROL Message Type]** .

1. Bewerk uw uitgebreide melding.

   ![](assets/nmac_android_5.png)

1. U kunt desgewenst informatie toevoegen in de eerder geconfigureerde **[!UICONTROL Application variables]** . **[!UICONTROL Application variables]** moet worden geconfigureerd in de Android-service en maakt deel uit van de berichtlading die naar het mobiele apparaat wordt verzonden.

1. Klik op **[!UICONTROL Save]** en verzend de levering.

De afbeelding en webpagina moeten in de pushmelding worden weergegeven wanneer deze worden ontvangen op de mobiele Android-apparaten van de abonnees.

![](assets/nmac_android_4.png)

## Een meldingsbericht maken {#creating-notification-message}

![](assets/do-not-localize/how-to-video.png) [ Leer hoe te om een de duwbericht van Android in video ](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html#additional-resources){target="_blank"} tot stand te brengen .

1. Ga naar **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** .

1. Klik op **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecteer **[!UICONTROL Deliver on Android (android)]** in de vervolgkeuzelijst **[!UICONTROL Delivery template]** . Voeg een **[!UICONTROL Label]** toe aan uw levering.

1. Klik op **[!UICONTROL To]** om de doelpopulatie te definiëren. Standaard wordt de doeltoewijzing **[!UICONTROL Subscriber application]** toegepast. Klik op **[!UICONTROL Add]** om uw service te selecteren.

   ![](assets/nmac_android_7.png)

1. Selecteer **[!UICONTROL Subscribers of an Android mobile application]** in het **[!UICONTROL Target type]** -venster en klik op **[!UICONTROL Next]** .

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Service]** eerst de eerder gemaakte service en vervolgens de toepassing en klik op **[!UICONTROL Finish]** .

   ![](assets/nmac_android_6.png)

1. Selecteer **[!UICONTROL notification message]** als **[!UICONTROL Message Type]** .

1. Voeg een titel toe en bewerk uw bericht. Pas uw pushmelding aan met de **[!UICONTROL Notification options]** :

   * **[!UICONTROL Channel ID]**: stel de kanaal-id van uw melding in. De app moet een kanaal met deze kanaal-id maken voordat meldingen met deze kanaal-id worden ontvangen.
   * **[!UICONTROL Sound]**: stel het geluid in dat moet worden afgespeeld wanneer het apparaat uw melding ontvangt.
   * **[!UICONTROL Color]**: stel de kleur van het pictogram van uw melding in.
   * **[!UICONTROL Icon]**: stel het pictogram van het bericht in op weergave op de apparaten van uw profielen.
   * **[!UICONTROL Tag]**: stel de id in die wordt gebruikt om bestaande meldingen in de meldingslade te vervangen.
   * **[!UICONTROL Click action]**: Stel de actie in die aan een gebruiker is gekoppeld, en klik op het bericht.

   Voor meer op **[!UICONTROL Notification options]** en hoe te om deze gebieden te vullen, verwijs naar [ documentatie FCM ](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"} .

   ![](assets/nmac_android_8.png)

1. Als uw toepassing is geconfigureerd met het HTTP v1 API-protocol, kunt u uw pushmelding verder aanpassen met de volgende **[!UICONTROL HTTPV1 additional options]** :

   * **[!UICONTROL Ticker]**: stel de tekst van de markering in voor de melding. Alleen beschikbaar voor apparaten die zijn ingesteld op Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: stel de URL van de afbeelding in die in de melding moet worden weergegeven.
   * **[!UICONTROL Notification Count]**: stel het aantal nieuwe ongelezen gegevens in dat rechtstreeks op het toepassingspictogram moet worden weergegeven.
   * **[!UICONTROL Sticky]**: ingesteld op true of false. Indien ingesteld op false, wordt het bericht automatisch genegeerd wanneer de gebruiker erop klikt. Indien ingesteld op true, wordt het bericht nog steeds weergegeven, zelfs wanneer de gebruiker erop klikt.
   * **[!UICONTROL Notification Priority]**: stel de prioriteitsniveaus van uw melding in op de standaardwaarde, minimum, laag of hoog. Voor meer op dit, verwijs naar [ documentatie FCM ](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: stel de zichtbaarheidsniveaus van uw melding in op openbaar, privé of geheim. Voor meer op dit, verwijs naar [ documentatie FCM ](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Voor meer op **[!UICONTROL HTTP v1 additional options]** en hoe te om deze gebieden te vullen, verwijs naar [ documentatie FCM ](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"} .

   ![](assets/nmac_android_9.png)

1. U kunt desgewenst informatie toevoegen in de eerder geconfigureerde **[!UICONTROL Application variables]** . **[!UICONTROL Application variables]** moet worden geconfigureerd in de Android-service en maakt deel uit van de berichtlading die naar het mobiele apparaat wordt verzonden.

1. Klik op **[!UICONTROL Save]** en verzend de levering.

De afbeelding en webpagina moeten in de pushmelding worden weergegeven wanneer deze worden ontvangen op de mobiele Android-apparaten van de abonnees.
