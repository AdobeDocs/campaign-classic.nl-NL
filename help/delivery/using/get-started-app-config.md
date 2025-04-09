---
product: campaign
title: De mobiele toepassing configureren in Adobe Campaign
description: Leer hoe u begint met de configuratie van de mobiele toepassing
feature: Push
role: User, Developer
level: Intermediate, Experienced
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 5%

---

# Aan de slag met de appconfiguratie



U kunt in deze sectie een configuratiemonster vinden die op een bedrijf wordt gebaseerd dat online vakantiepakketten verkoopt. De mobiele toepassing (Neotrips) van Neotrips is beschikbaar voor klanten in twee versies: Neotrips voor Android en Neotrips voor iOS.

Als u pushberichten wilt verzenden in Adobe Campaign, moet u:

* Maak een **[!UICONTROL Mobile application]** type information service voor de mobiele toepassing Neotrips. Verwijs naar [ deze sectie voor iOS ](configuring-the-mobile-application.md#configuring-ios-service). en [ deze sectie voor Android ](configuring-the-mobile-application-android.md#configuring-android-service).
* Voeg de iOS- en Android-versies van de toepassing toe aan deze service.
* Creeer een levering voor [ iOS ](create-notifications-ios.md) en [ Android ](create-notifications-android.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Ga naar het tabblad **[!UICONTROL Subscriptions]** van de service om de lijst met abonnees van de service weer te geven, dat wil zeggen alle personen die de toepassing op hun mobiele telefoon hebben geïnstalleerd en ermee hebben ingestemd meldingen te ontvangen.

## Het pakket installeren {#installing-package-ios}

[!BADGE  Op-gebouw &amp; Hybrid ]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"}

![](assets/do-not-localize/how-to-video.png) [ Leer hoe te om het mobiele app pakket in video te installeren ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html#sending-messages)

Als hybride/ontvangen klant, contacteer ](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team van de Zorg van de Klant van 0} Adobe om tot het kanaal van het pushbericht in Campagne toegang te hebben.[

Als klant op locatie moet u een ingebouwd pakket installeren.

>[!CAUTION]
>
>Leer meer over de ingebouwde pakketten van de Campagne, beste praktijken en aanbevelingen in [ deze pagina ](../../installation/using/installing-campaign-standard-packages.md).

Installatiestappen zijn:

1. Open de importassistent voor pakketten vanuit **[!UICONTROL Tools > Advanced > Import package]** in de Adobe Campaign-clientconsole.

   ![](assets/package_ios.png)

1. Selecteer **[!UICONTROL Install a standard package]**.

1. Controleer **[!UICONTROL Mobile App Channel]** in de lijst die wordt weergegeven.

   ![](assets/package_ios_2.png)

1. Klik op **[!UICONTROL Next]** en vervolgens op **[!UICONTROL Start]** om de pakketinstallatie te starten.

   Zodra de pakketten worden geïnstalleerd, toont de vooruitgangsbar **100%** en u kunt het volgende bericht in de installatielogboeken zien: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** het installatievenster.

Zodra deze stap is uitgevoerd, kunt u uw Android- en iOS-toepassingen configureren.
Raadpleeg de volgende secties:

* [Configuratiestappen voor iOS](configuring-the-mobile-application.md)

* [Configuratiestappen voor Android](configuring-the-mobile-application-android.md)
