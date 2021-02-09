---
solution: Campaign Classic
product: campaign
title: 'De mobiele applicatie configureren in Adobe Campaign '
description: Leer hoe u begint met de configuratie van de mobiele toepassing
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 965aee2e310dd7e35d7a65bf9a1bda5dc8eb0959
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 8%

---


# Aan de slag met de app-configuratie

U kunt in deze sectie een configuratiemonster vinden die op een bedrijf wordt gebaseerd dat online vakantiepakketten verkoopt. Zijn mobiele toepassing (Neotrips) is beschikbaar aan zijn klanten in twee versies: Neotrips voor Android en Neotrips voor iOS.

Als u pushberichten wilt verzenden in Adobe Campaign, moet u:

* Maak een **[!UICONTROL Mobile application]**-tekstinformatieservice voor de mobiele toepassing Neotrips. Zie [deze sectie voor iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). en [deze sectie voor Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Voeg de iOS- en Android-versies van de toepassing toe aan deze service.
* Maak een levering voor zowel iOS als Android. [Zie deze pagina](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Ga naar het tabblad **[!UICONTROL Subscriptions]** van de service om de lijst met abonnees van de service weer te geven, d.w.z. alle personen die de toepassing op hun mobiele telefoon hebben geïnstalleerd en ermee hebben ingestemd meldingen te ontvangen.

## Het pakket {#installing-package-ios} installeren

![](assets/do-not-localize/how-to-video.png) [Leer hoe u het pakket voor de mobiele app in video installeert](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

Als hybride/gehoste klant neemt u contact op met het team van [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om toegang te krijgen tot het pushmeldingskanaal in Campagne.

Als klant op locatie moet u een ingebouwd pakket installeren.

>[!CAUTION]
>
>Meer informatie over ingebouwde pakketten, beste praktijken en aanbevelingen van de Campagne in [deze pagina](../../installation/using/installing-campaign-standard-packages.md).

Installatiestappen zijn:

1. Open de wizard voor het importeren van pakketten vanuit **[!UICONTROL Tools > Advanced > Package import...]** in de Adobe Campaign-clientconsole.

   ![](assets/package_ios.png)

1. Selecteer **[!UICONTROL Install a standard package]**.

1. Controleer **[!UICONTROL Mobile App Channel]** in de lijst die wordt weergegeven.

   ![](assets/package_ios_2.png)

1. Klik **[!UICONTROL Next]**, dan **[!UICONTROL Start]** om de pakketinstallatie te beginnen.

   Zodra de pakketten worden geïnstalleerd, toont de vooruitgangsbar **100%** en u kunt het volgende bericht in de installatielogboeken zien: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** het installatievenster.

Zodra deze stap is uitgevoerd, kunt u uw Android- en iOS-toepassingen configureren.
Raadpleeg de volgende secties:

* [Configuratiestappen voor iOS](../../delivery/using/configuring-the-mobile-application.md)

* [Configuratiestappen voor Android](../../delivery/using/configuring-the-mobile-application-android.md)
