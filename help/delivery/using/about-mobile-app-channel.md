---
title: Over het mobiele toepassingskanaal in Adobe Campaign Classic
description: Deze sectie bevat algemene informatie die specifiek is voor het mobiele toepassingskanaal in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: e8d26b33-dc7c-4abd-956a-92f419a117e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 6b3fe8b9-dae6-4f8e-83e1-3376c0fe72a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c581f22261af7e083f6bd47e603d17d2d71e7ce6

---


# Mobiel toepassingskanaal{#about-mobile-app-channel}

>[!CAUTION]
>
>In dit document wordt beschreven hoe u uw mobiele toepassing kunt integreren met het Adobe Campaign-platform. De klasse biedt geen informatie over hoe de mobiele toepassing moet worden gemaakt of hoe deze moet worden geconfigureerd voor het beheer van meldingen. Raadpleeg de officiële documentatie van Apple ([https://developer.apple.com/](https://developer.apple.com/)) en Android ([https://developer.android.com/index.html](https://developer.android.com/index.html)) voor meer informatie hierover.

In de onderstaande secties vindt u informatie die specifiek is voor het mobiele toepassingskanaal. Raadpleeg[deze sectie](../../delivery/using/steps-about-delivery-creation-steps.md)voor algemene informatie over het maken van een levering.

Met het **Mobile App Channel** kunt u het Adobe Campagne-platform gebruiken om gepersonaliseerde meldingen naar iOS- en Android-terminals te verzenden via apps. Er zijn twee leveringskanalen beschikbaar:

* Een iOS-kanaal waarmee u meldingen kunt verzenden naar mobiele Apple-apparaten.

   ![](assets/nmac_intro_2.png)

* Een Android-kanaal waarmee u gegevensberichten kunt verzenden naar mobiele Android-apparaten.

   ![](assets/nmac_intro_1.png)

Voor deze twee kanalen zijn er twee leveringsactiviteiten in de campagneworkflows:

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>Twee transactionele berichtmalplaatjes zijn ook beschikbaar voor transactieoverseinen.

U kunt het toepassingsgedrag bepalen voor wanneer de gebruiker het bericht activeert om het scherm te tonen dat de toepassingscontext aanpast. Bijvoorbeeld:

* Een bericht wordt verzonden naar de klant om hen te laten weten hun pakket het pakhuis heeft verlaten. Als u het bericht activeert, wordt er een pagina met leveringsgerelateerde informatie geopend.
* De gebruiker heeft items aan het winkelwagentje toegevoegd, maar heeft de toepassing verlaten zonder de aankoop te voltooien. Er wordt een bericht verzonden waarin wordt aangegeven dat hun winkelwagen is verlaten. Wanneer ze het bericht activeren, wordt het item op het scherm weergegeven.

>[!CAUTION]
>
>* U moet ervoor zorgen dat de meldingen die naar een mobiele toepassing worden verzonden, voldoen aan de voorwaarden en vereisten die door Apple (Apple Push Notification Service) en Google (Google Cloud Messaging) zijn opgegeven.
>* Waarschuwing: in sommige landen vereist de wet dat u de gebruikers informeert over uw verzamelde datatype mobiele toepassingen en het doel van hun verwerking . U moet de wetgeving controleren.


Met de **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt)-workflow worden abonnementen op mobiele apparaten bijgewerkt. Raadpleeg de handleiding [Workflows voor](../../workflow/using/mobile-app-channel.md)meer informatie over deze workflow.

Adobe Campaign is compatibel met zowel binaire als HTTP/2-APNS. Voor meer details over de configuratiestappen, verwijs naar de sectie van [Verbindingen](../../delivery/using/setting-up-mobile-app-channel.md#connectors) .
