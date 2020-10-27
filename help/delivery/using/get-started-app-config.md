---
title: 'De mobiele applicatie configureren in Adobe Campaign '
description: Leer hoe u begint met de configuratie van de mobiele toepassing
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
translation-type: tm+mt
source-git-commit: fd75f7f75e8e77d7228233ea311dd922d100417c
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 4%

---


# Aan de slag met de toepassingsconfiguratie

U kunt in deze sectie een configuratiemonster vinden die op een bedrijf wordt gebaseerd dat online vakantiepakketten verkoopt. Zijn mobiele toepassing (Neotrips) is beschikbaar aan zijn klanten in twee versies: Neotrips voor Android en Neotrips voor iOS.

Als u pushberichten wilt verzenden in Adobe Campaign, moet u:

* Maak een **[!UICONTROL Mobile application]** tekstinformatieservice voor de mobiele toepassing Neotrips. Zie [deze sectie voor iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). en [deze sectie voor Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Voeg de iOS- en Android-versies van de toepassing toe aan deze service.
* Maak een levering voor zowel iOS als Android. [Zie deze pagina](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Ga naar het **[!UICONTROL Subscriptions]** tabblad van de service om de lijst met abonnees van de service weer te geven, dat wil zeggen alle personen die de toepassing op hun mobiele telefoon hebben geïnstalleerd en ermee hebben ingestemd meldingen te ontvangen.

## Het pakket installeren {#installing-package-ios}

Als hybride/gehoste klant neemt u contact op met het Adobe Customer Care-team voor toegang tot het pushmeldkanaal in de campagne.

Als klant op locatie moet u de volgende installatiestappen uitvoeren:

1. Open de wizard voor het importeren van pakketten vanuit **[!UICONTROL Tools > Advanced > Package import...]** de Adobe Campaign-clientconsole.

   ![](assets/package_ios.png)

1. Selecteer **[!UICONTROL Install a standard package]**.

1. Controleer in de lijst die wordt weergegeven **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Klik **[!UICONTROL Next]** en vervolgens **[!UICONTROL Start]** om de pakketinstallatie te starten.

   Nadat de pakketten zijn geïnstalleerd, wordt op de voortgangsbalk **100%** weergegeven. In de installatielogboeken ziet u het volgende bericht: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** het installatievenster.

Zodra deze stap is uitgevoerd, kunt u uw Android- en iOS-toepassingen configureren.
Raadpleeg de volgende secties:

* [Configuratiestappen voor iOS](../../delivery/using/configuring-the-mobile-application.md)

* [Configuratiestappen voor Android](../../delivery/using/configuring-the-mobile-application-android.md)
