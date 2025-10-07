---
product: campaign
title: De mobiele iOS-toepassing in Adobe Campaign configureren
description: Meer informatie over het instellen van uw mobiele toepassing voor iOS
feature: Push
role: User, Developer
level: Intermediate, Experienced
hide: true
hidefromtoc: true
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
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

U zult dan een duw bericht voor de apparaten van iOS [&#x200B; kunnen tot stand brengen.](create-notifications-ios.md)

## Externe iOS-account configureren {#configuring-external-account-ios}

Voor iOS verzendt de iOS HTTP/2-connector meldingen naar de HTTP/2 APNs.

Om deze schakelaar te vormen, volg deze stappen:

1. Ga naar **[!UICONTROL Administration > Platform > External accounts]** .
1. Selecteer de **[!UICONTROL iOS routing]** externe account.
1. Vul op het tabblad **[!UICONTROL Connector]** het veld **[!UICONTROL Access URL of the connector]** in met de volgende URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. Klik op **[!UICONTROL Save]**.

Uw iOS-aansluiting is nu geconfigureerd. U kunt uw service gaan maken.

## IOS-service configureren {#configuring-ios-service}

>[!CAUTION]
>
>De toepassing moet zijn geconfigureerd voor push-acties voordat deze kan worden geïntegreerd met Adobe SDK.
>
>Als dit niet het geval is, gelieve te verwijzen naar [&#x200B; deze pagina &#x200B;](https://developer.apple.com/documentation/usernotifications).

1. Ga naar het knooppunt **[!UICONTROL Profiles and Targets > Services and subscriptions]** en klik op **[!UICONTROL New]** .

   ![](assets/nmac_service_1.png)

1. Definieer een **[!UICONTROL Label]** en een **[!UICONTROL Internal name]** .
1. Ga naar het veld **[!UICONTROL Type]** en selecteer **[!UICONTROL Mobile application]** .

   >[!NOTE]
   >
   >Het gebrek **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** doelafbeelding is verbonden met de ontvankelijkheidstabel. Als u een andere doelafbeelding wilt gebruiken, moet u een nieuwe doeltoewijzing maken en deze invoeren in het veld **[!UICONTROL Target mapping]** van de service. Voor meer bij het creëren van doelafbeelding, verwijs naar de [&#x200B; gids van de Configuratie &#x200B;](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klik vervolgens op de knop **[!UICONTROL Add]** om het toepassingstype te selecteren.

   ![](assets/nmac_service_2.png)

1. Maak uw iOS-ontwikkelings- en productietoepassingen. Raadpleeg deze [sectie](configuring-the-mobile-application.md#creating-ios-app) voor meer informatie.

## IOS mobile-app maken {#creating-ios-app}

Nadat u de service hebt gemaakt, maakt u uw iOS-toepassing in Campagne. Volg de onderstaande stappen:

1. Klik vanuit de nieuwe service op de knop **[!UICONTROL Add]** om het toepassingstype te selecteren.

   ![](assets/nmac_service_2.png)

1. Het volgende venster wordt weergegeven. Selecteer **[!UICONTROL Create an iOS application]** en typ **[!UICONTROL Label]** om te beginnen.

   ![](assets/nmac_ios_2.png)

1. U kunt desgewenst ook de inhoud van een pushbericht verrijken met wat **[!UICONTROL Application variables]** . Deze zijn volledig aanpasbaar en een deel van de berichtlading wordt verzonden naar het mobiele apparaat.
In het volgende voorbeeld, voegen wij **mediaURl** en **mediaExt** toe om rijke duw bericht tot stand te brengen en dan de toepassing van het beeld te voorzien om binnen het bericht te tonen.

   ![](assets/nmac_ios_3.png)

1. Het **[!UICONTROL Subscription parameters]** lusje staat u toe om de afbeelding met een uitbreiding van het **[!UICONTROL Subscriber applications (nms:appsubscriptionRcpte bepalen)]** schema.

   >[!NOTE]
   >
   >Zorg ervoor dat u niet hetzelfde certificaat gebruikt voor de ontwikkelingsversie (sandbox) en de productieversie van de toepassing.

1. Op het tabblad **[!UICONTROL Sounds]** kunt u opgeven welk geluid moet worden afgespeeld. Klik op **[!UICONTROL Add]** en vul **[!UICONTROL Internal name]** veld in dat de naam moet bevatten van het bestand dat is ingesloten in de toepassing of de naam van het systeemgeluid.

1. Klik op **[!UICONTROL Next]** om de ontwikkeltoepassing te configureren.

1. Zorg ervoor dat **[!UICONTROL Integration key]** ook in Adobe Campaign en in de toepassingscode via de SDK is gedefinieerd. <!--For more on this, refer to [this page](integrating-campaign-sdk-into-the-mobile-application.md).--> Met deze integratietoets, die specifiek is voor elke toepassing, kunt u de mobiele toepassing koppelen aan het Adobe Campaign-platform.

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** is volledig aanpasbaar met tekenreekswaarde, maar moet precies hetzelfde zijn als de waarde die in de SDK is opgegeven.

1. Selecteer een van de pictogrammen uit de doos in het veld **[!UICONTROL Application icon]** om de mobiele toepassing in uw service aan te passen.

1. Selecteer **[!UICONTROL Authentication mode]**.

   ![](assets/nmac_ios_5.png)

   Er zijn twee modi beschikbaar:

   * (Aanbevolen) **[!UICONTROL Token-based authentication]**: vul de instellingen voor de APNs-verbinding in **[!UICONTROL Key Id]** , **[!UICONTROL Team Id]** en **[!UICONTROL Bundle Id]** en selecteer vervolgens het p8-certificaat door op **[!UICONTROL Enter the private key...]** te klikken. Voor meer op **[!UICONTROL Token-based authentication]**, verwijs naar [&#x200B; documentatie van Apple &#x200B;](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}.

   * **[!UICONTROL Certificate-based authentication]**: Klik op **[!UICONTROL Enter the certificate...]** en selecteer de p12-toets. Voer vervolgens het wachtwoord in dat door de ontwikkelaar van de mobiele toepassing is opgegeven.

   >[!NOTE]
   >
   > Adobe raadt u aan **[!UICONTROL Token-based authentication]** voor uw iOS-configuratie te gebruiken, aangezien de P8-verificatietoetsen nieuwer en veiliger zijn.

1. Gebruik de knop **[!UICONTROL Test the connection]** om uw configuratie te valideren.

1. Klik op **[!UICONTROL Next]** om de productietoepassing te configureren en dezelfde stappen uit te voeren als hierboven beschreven.


1. Klik op **[!UICONTROL Finish]**.

Uw iOS-toepassing kan nu worden gebruikt in Campaign Classic.
