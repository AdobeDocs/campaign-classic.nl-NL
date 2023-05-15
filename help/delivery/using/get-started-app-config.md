---
product: campaign
title: De mobiele toepassing configureren in Adobe Campaign
description: Leer hoe u begint met de configuratie van de mobiele toepassing
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Push
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: e011333411af79b985166a4e73592a1860749cf1
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 10%

---

# Aan de slag met de appconfiguratie



U kunt in deze sectie een configuratiemonster vinden die op een bedrijf wordt gebaseerd dat online vakantiepakketten verkoopt. De mobiele toepassing (Neotrips) van Neotrips is in twee versies beschikbaar voor klanten: Neotrips voor Android en Neotrips voor iOS.

Als u pushberichten wilt verzenden in Adobe Campaign, moet u:

* Een **[!UICONTROL Mobile application]** type information service for the Neotrips mobile application. Zie [deze sectie voor iOS](configuring-the-mobile-application.md#configuring-ios-service). en [deze sectie voor Android](configuring-the-mobile-application-android.md#configuring-android-service).
* Voeg de iOS- en Android-versies van de toepassing toe aan deze service.
* Een levering maken voor [iOS](create-notifications-ios.md) en [Android](create-notifications-android.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Ga naar de **[!UICONTROL Subscriptions]** tabblad van de service om de lijst met abonnees van de service weer te geven, d.w.z. alle personen die de toepassing op hun mobiele telefoon hebben geïnstalleerd en ermee hebben ingestemd meldingen te ontvangen.

## Het pakket installeren {#installing-package-ios}

[!BADGE Op locatie en hybride]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"}

![](assets/do-not-localize/how-to-video.png) [Leer hoe u het pakket voor de mobiele app in video installeert](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

Als hybride/gehoste klant neemt u contact op met [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) -team voor toegang tot het pushmeldingskanaal in Campagne.

Als klant op locatie moet u een ingebouwd pakket installeren.

>[!CAUTION]
>
>Meer informatie over geïntegreerde pakketten, aanbevolen procedures en aanbevelingen in de campagne vindt u in [deze pagina](../../installation/using/installing-campaign-standard-packages.md).

Installatiestappen zijn:

1. De wizard Pakket importeren openen vanuit **[!UICONTROL Tools > Advanced > Import package]** in de Adobe Campaign-clientconsole.

   ![](assets/package_ios.png)

1. Selecteer **[!UICONTROL Install a standard package]**.

1. Controleer in de lijst die wordt weergegeven **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Klikken **[!UICONTROL Next]** vervolgens **[!UICONTROL Start]** om de pakketinstallatie te starten.

   Nadat de pakketten zijn geïnstalleerd, wordt op de voortgangsbalk weergegeven **100%** en u kunt het volgende bericht in de installatielogboeken zien: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** het installatievenster.

Zodra deze stap is uitgevoerd, kunt u uw Android- en iOS-toepassingen configureren.
Raadpleeg de volgende secties:

* [Configuratiestappen voor iOS](configuring-the-mobile-application.md)

* [Configuratiestappen voor Android](configuring-the-mobile-application-android.md)
