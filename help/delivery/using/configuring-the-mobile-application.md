---
solution: Campaign Classic
product: campaign
title: De mobiele iOS-toepassing configureren in Adobe Campaign
description: Leer hoe u uw mobiele toepassing instelt voor iOS
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: a1bd8dc2b5946b74cb880eff934e3b35cadfb2d2
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 8%

---


# Configuratiestappen voor iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

Nadat het pakket is geïnstalleerd, kunt u de iOS-toepassingsinstellingen definiëren in Adobe Campaign Classic.

>[!NOTE]
>
>Raadpleeg deze [sectie](../../delivery/using/configuring-the-mobile-application-android.md) voor informatie over het configureren van uw app voor Android en het maken van een levering voor Android.

## Externe iOS-account {#configuring-external-account-ios} configureren

Voor iOS verzendt de iOS HTTP/2-connector meldingen naar de HTTP/2 APNs.

Om deze schakelaar te vormen, volg deze stappen:

1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecteer de externe account **[!UICONTROL iOS routing]**.
1. Vul op het tabblad **[!UICONTROL Connector]** het veld **[!UICONTROL Access URL of the connector]** met de volgende URL in: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   >[!NOTE]
   >
   > Vanaf Campaign versie 20.3 is de verouderde binaire iOS-connector van iOS afgeschaft. Als u deze connector gebruikt, moet u uw implementatie dienovereenkomstig aanpassen. [Meer informatie](https://helpx.adobe.com/campaign/kb/migrate-to-apns-http2.html)

   ![](assets/nmac_connectors.png)

1. Klik op **[!UICONTROL Save]**.

Uw iOS-connector is nu geconfigureerd. U kunt uw service gaan maken.

## iOS-service {#configuring-ios-service} configureren

>[!CAUTION]
>
>De toepassing moet zijn geconfigureerd voor pushacties VOORDAT deze wordt geïntegreerd in de SDK van Adobe Campaign.
>
>Als dit niet het geval is, te verwijzen gelieve [deze pagina](https://developer.apple.com/documentation/usernotifications).

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

1. Maak uw iOS-ontwikkelings- en -productieprogramma&#39;s. Raadpleeg deze [sectie](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app) voor meer informatie.

## Mobiele iOS-toepassing {#creating-ios-app} maken

Nadat u de service hebt gemaakt, moet u nu uw iOS-toepassing maken:

1. Klik op de knop **[!UICONTROL Add]** van de zojuist gemaakte service om het toepassingstype te selecteren.

   ![](assets/nmac_service_2.png)

1. Het volgende venster wordt weergegeven. Selecteer **[!UICONTROL Create an iOS application]** en begin door **[!UICONTROL Label]** in te gaan.

   ![](assets/nmac_ios_2.png)

1. Als optie kunt u de inhoud van een pushbericht desgewenst verrijken met **[!UICONTROL Application variables]**. Deze zijn volledig aanpasbaar en een deel van de berichtlading wordt verzonden naar het mobiele apparaat.
In het volgende voorbeeld voegen we **mediaURl** en **mediaExt** toe om een rijke pushmelding te maken en geeft vervolgens de toepassing de afbeelding weer die binnen de melding moet worden weergegeven.

   ![](assets/nmac_ios_3.png)

1. Op het tabblad **[!UICONTROL Subscription parameters]** kunt u de toewijzing definiëren met een extensie van het schema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**.

   >[!NOTE]
   >
   >Zorg ervoor dat u niet hetzelfde certificaat gebruikt voor de ontwikkelingsversie (sandbox) en de productieversie van de toepassing.

1. Op het tabblad **[!UICONTROL Sounds]** kunt u opgeven welk geluid moet worden afgespeeld. Klik op **[!UICONTROL Add]** en vul **[!UICONTROL Internal name]** veld in dat de naam moet bevatten van het bestand dat is ingesloten in de toepassing of de naam van het systeemgeluid.

1. Klik **[!UICONTROL Next]** beginnen de ontwikkelingstoepassing te vormen.

1. Zorg ervoor dat **[!UICONTROL Integration key]** in Adobe Campaign en in de toepassingscode via de SDK wordt gedefinieerd. Raadpleeg voor meer informatie: [De campagne-SDK integreren in de mobiele toepassing](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md). Met deze integratietoets, die specifiek is voor elke toepassing, kunt u de mobiele toepassing koppelen aan het Adobe Campaign-platform.

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** is volledig aanpasbaar met koordwaarde maar moet precies het zelfde zijn zoals gespecificeerd in SDK.

1. Selecteer een van de pictogrammen uit de doos in het **[!UICONTROL Application icon]** gebied om mobiele toepassing in uw dienst te personaliseren.

1. Selecteer het **[!UICONTROL Authentication mode]**. U kunt de verificatiemodus altijd later wijzigen op het tabblad **[!UICONTROL Certificate]** van uw mobiele toepassing.
   * **[!UICONTROL Certificate-based authentication]**: Klik  **[!UICONTROL Enter the certificate...]**  vervolgens op de p12-toets en voer het wachtwoord in dat door de ontwikkelaar van de mobiele toepassing is opgegeven.
   * **[!UICONTROL Token-based authentication]**: Vul de verbindingsinstellingen in  **[!UICONTROL Key ID]** en  **[!UICONTROL Team ID]** selecteer uw p8-certificaat door op  **[!UICONTROL Bundle ID]**   **[!UICONTROL Enter the private key]**. Raadpleeg [documentatie van Apple](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns) voor meer informatie.**[!UICONTROL Token-based authentication]**

   >[!NOTE]
   >
   > Adobe raadt u aan **[!UICONTROL Token-based authentication]** te gebruiken voor uw iOS-configuratie omdat deze verificatiemodus beter is beveiligd en niet aan certificaatvervaldatum is gebonden.

   ![](assets/nmac_ios_4.png)

1. U kunt **[!UICONTROL Test the connection]** klikken om ervoor te zorgen het succesvol is.

1. Klik **[!UICONTROL Next]** beginnen de productietoepassing te vormen en de zelfde stappen te volgen zoals hierboven gedetailleerd.

   ![](assets/nmac_ios_5.png)

1. Klik op **[!UICONTROL Finish]**.

Uw iOS-toepassing kan nu worden gebruikt in Campaign Classic.

## Een rijke melding voor iOS maken {#creating-ios-delivery}

Met iOS 10 of hoger is het mogelijk om rijke meldingen te genereren. Adobe Campaign kan meldingen verzenden met behulp van variabelen waarmee het apparaat een uitgebreide melding kan weergeven.

U moet nu een nieuwe levering maken en deze koppelen aan de mobiele toepassing die u hebt gemaakt.

1. Ga naar **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klik op **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecteer **[!UICONTROL Deliver on iOS (ios)]** in **[!UICONTROL Delivery template]** drop-down. Voeg een **[!UICONTROL Label]** aan uw levering toe.

1. Klik op **[!UICONTROL To]** om de doelpopulatie te definiëren. Standaard wordt de **[!UICONTROL Subscriber application]**-doeltoewijzing toegepast. Klik **[!UICONTROL Add]** om onze eerder gecreeerde dienst te selecteren.

   ![](assets/nmac_ios_9.png)

1. Selecteer **[!UICONTROL Target type]** in het venster &lt;a0/> en klik **[!UICONTROL Next]**.**[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Service]** de eerder gemaakte service, selecteer vervolgens de toepassing die u als doel wilt instellen en klik op **[!UICONTROL Finish]**.
**[!UICONTROL Application variables]** worden automatisch toegevoegd afhankelijk van wat tijdens de configuratiestappen werd toegevoegd.

   ![](assets/nmac_ios_6.png)

1. Bewerk uw uitgebreide melding.

   ![](assets/nmac_ios_7.png)

1. Schakel het vakje **[!UICONTROL Mutable content]** in het meldingsvenster Bewerken in zodat de mobiele toepassing media-inhoud kan downloaden.

1. Klik **[!UICONTROL Save]** en verzend uw levering.

De afbeelding en webpagina moeten in de pushmelding worden weergegeven wanneer deze worden ontvangen op de mobiele iOS-apparaten van de abonnees.

![](assets/nmac_ios_8.png)
