---
product: campaign
title: De mobiele iOS-toepassing in Adobe Campaign configureren
description: Meer informatie over het instellen van uw mobiele toepassing voor iOS
feature: Push
role: User, Developer
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 81b47231b027a189bc8b9029b7d48939734d08ed
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 3%

---

# Configuratiestappen voor iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

Nadat het pakket is geïnstalleerd, kunt u de iOS-toepassingsinstellingen in Adobe Campaign Classic definiëren.

De belangrijkste stappen zijn:

1. [De externe iOS-account configureren](#configuring-external-account-ios)
1. [De iOS-service configureren](#configuring-ios-service)
1. [De mobiele iOS-app integreren in de campagne](#creating-ios-app)

Dan kunt u [een pushmelding maken voor iOS-apparaten](create-notifications-ios.md).

## Externe iOS-account configureren {#configuring-external-account-ios}

Voor iOS verzendt de iOS HTTP/2-connector meldingen naar de HTTP/2 APNs.

Om deze schakelaar te vormen, volg deze stappen:

1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecteer de **[!UICONTROL iOS routing]** externe rekening.
1. In de **[!UICONTROL Connector]** tabblad, vult de **[!UICONTROL Access URL of the connector]** veld met de volgende URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. Klik op **[!UICONTROL Save]**.

Uw iOS-aansluiting is nu geconfigureerd. U kunt uw service gaan maken.

## IOS-service configureren {#configuring-ios-service}

>[!CAUTION]
>
>De toepassing moet voor de Acties van de Duw vóór om het even welke integratie aan Adobe SDK zijn gevormd.
>
>Indien dit niet het geval is, gelieve te verwijzen naar [deze pagina](https://developer.apple.com/documentation/usernotifications).

1. Ga naar de **[!UICONTROL Profiles and Targets > Services and subscriptions]** knoop en klik **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Een **[!UICONTROL Label]** en **[!UICONTROL Internal name]**.
1. Ga naar de **[!UICONTROL Type]** veld en selecteer **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >De standaardwaarde **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** doeltoewijzing is gekoppeld aan de tabel met ontvangers. Als u een andere doelafbeelding wilt gebruiken, moet u een nieuwe doeltoewijzing maken en deze invoeren in het dialoogvenster **[!UICONTROL Target mapping]** van de dienst. Raadpleeg voor meer informatie over het maken van doeltoewijzingen de [Configuratiegids](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klik vervolgens op de knop **[!UICONTROL Add]** Selecteer het toepassingstype.

   ![](assets/nmac_service_2.png)

1. Maak uw iOS-ontwikkelings- en productietoepassingen. Raadpleeg deze [sectie](configuring-the-mobile-application.md#creating-ios-app) voor meer informatie.

## IOS mobile-app maken {#creating-ios-app}

Nadat u de service hebt gemaakt, maakt u uw iOS-toepassing in Campagne. Volg de onderstaande stappen:

1. Klik op de knop **[!UICONTROL Add]** Selecteer het toepassingstype.

   ![](assets/nmac_service_2.png)

1. Het volgende venster wordt weergegeven. Selecteren **[!UICONTROL Create an iOS application]** en begint met het invoeren van de **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Als optie kunt u de inhoud van een pushbericht verrijken met wat **[!UICONTROL Application variables]** indien nodig. Deze zijn volledig aanpasbaar en een deel van de berichtlading wordt verzonden naar het mobiele apparaat.
In het volgende voorbeeld voegen we **mediaURl** en **mediaExt** om uitgebreide pushmeldingen te maken en de toepassing de afbeelding te geven die binnen het bericht moet worden weergegeven.

   ![](assets/nmac_ios_3.png)

1. De **[!UICONTROL Subscription parameters]** kunt u de toewijzing definiëren met een extensie van de **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schema.

   >[!NOTE]
   >
   >Zorg ervoor dat u niet hetzelfde certificaat gebruikt voor de ontwikkelingsversie (sandbox) en de productieversie van de toepassing.

1. De **[!UICONTROL Sounds]** kunt u opgeven welk geluid moet worden afgespeeld. Klikken **[!UICONTROL Add]** en vullen **[!UICONTROL Internal name]** veld dat de naam moet bevatten van het bestand dat is ingesloten in de toepassing of de naam van het systeemgeluid.

1. Klikken **[!UICONTROL Next]** om de ontwikkelingstoepassing te configureren.

1. Zorg ervoor dat **[!UICONTROL Integration key]** wordt gedefinieerd in Adobe Campaign en in de toepassingscode via de SDK. <!--For more on this, refer to [this page](integrating-campaign-sdk-into-the-mobile-application.md).--> Met deze integratietoets, die specifiek is voor elke toepassing, kunt u de mobiele toepassing koppelen aan het Adobe Campaign-platform.

   >[!NOTE]
   >
   > De **[!UICONTROL Integration key]** is volledig aanpasbaar met tekenreekswaarde, maar moet exact hetzelfde zijn als de waarde die in de SDK is opgegeven.

1. Selecteer een van de pictogrammen voor de uit-van-de-doos in het menu **[!UICONTROL Application icon]** om de mobiele toepassing in uw service aan te passen.

1. Selecteer **[!UICONTROL Authentication mode]**.

   ![](assets/nmac_ios_5.png)

   Er zijn twee modi beschikbaar:

   * (Aanbevolen) **[!UICONTROL Token-based authentication]**: Vul de verbindingsinstellingen van APNs in **[!UICONTROL Key Id]**, **[!UICONTROL Team Id]** en **[!UICONTROL Bundle Id]** Selecteer vervolgens uw p8-certificaat door op **[!UICONTROL Enter the private key...]**. Voor meer informatie **[!UICONTROL Token-based authentication]**, zie [Apple-documentatie](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}.

   * **[!UICONTROL Certificate-based authentication]**: Klikken **[!UICONTROL Enter the certificate...]**  Selecteer vervolgens de p12-toets en voer het wachtwoord in dat de ontwikkelaar van de mobiele toepassing heeft opgegeven.

   >[!NOTE]
   >
   > Adobe raadt u aan **[!UICONTROL Token-based authentication]** voor uw iOS-configuratie aangezien de P8-verificatietoetsen nieuwer en veiliger zijn.

1. Gebruik de **[!UICONTROL Test the connection]** knoop om uw configuratie te bevestigen.

1. Klikken **[!UICONTROL Next]** om de productietoepassing te configureren en dezelfde stappen uit te voeren als hierboven beschreven.


1. Klik op **[!UICONTROL Finish]**.

Uw iOS-toepassing kan nu in Campaign Classic worden gebruikt.
