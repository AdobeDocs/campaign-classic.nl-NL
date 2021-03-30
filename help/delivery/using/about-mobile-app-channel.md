---
solution: Campaign Classic
product: campaign
title: Mobiel toepassingskanaal in Adobe Campaign Classic
description: Deze sectie bevat algemene informatie die specifiek is voor het mobiele toepassingskanaal in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 9237e11edec4114b2bd0932e6128775f36aad27c
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---


# Aan de slag met mobiel toepassingskanaal{#about-mobile-app-channel}

Met het **Mobile App Channel** kunt u het Adobe Campaign-platform gebruiken om persoonlijke pushberichten naar iOS- en Android-terminals te verzenden via apps.

>[!CAUTION]
>
>In dit document wordt beschreven hoe u uw mobiele toepassing kunt integreren met het Adobe Campaign-platform. De klasse biedt geen informatie over hoe de mobiele toepassing moet worden gemaakt of hoe deze moet worden geconfigureerd voor het beheer van meldingen. Raadpleeg de officiële documentatie [van Apple](https://developer.apple.com/) en Android [documentatie](https://developer.android.com/index.html) als u hierover meer informatie wilt.

Er zijn twee leveringskanalen beschikbaar:

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
>* U moet ervoor zorgen dat de meldingen die naar een mobiele toepassing worden verzonden, voldoen aan de voorwaarden en vereisten die door Apple (Apple Push Notification Service) en Google (Firebase Cloud Messaging) zijn opgegeven.
>* Waarschuwing: in sommige landen vereist de wet dat u de gebruikers informeert over uw verzamelde datatype mobiele toepassingen en het doel van hun verwerking . U moet de wetgeving controleren.


Met de **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt)-workflow worden abonnementen op mobiele apparaten bijgewerkt. Raadpleeg de [lijst met technische workflows](../../workflow/using/about-technical-workflows.md) voor meer informatie over deze workflow.

Adobe Campaign is compatibel met HTTP/2 APNs. Voor meer details over de configuratiestappen, verwijs naar [deze sectie](../../delivery/using/configuring-the-mobile-application.md) sectie.

Voor globale informatie over hoe te om een levering tot stand te brengen, verwijs naar [deze sectie](../../delivery/using/steps-about-delivery-creation-steps.md).

## Gegevenspad {#data-path}

In de volgende schema&#39;s worden de stappen beschreven waarmee een mobiele toepassing gegevens kan uitwisselen met Adobe Campaign. Dit proces omvat drie entiteiten:

* de mobiele toepassing
* de kennisgevingsdienst: APNs (Apple Push Notification Service) voor Apple en FCM (Firebase Cloud Messaging) voor Android
* Adobe Campaign

De drie belangrijkste stappen van het kennisgevingsproces zijn: registratie van de toepassing in Adobe Campaign (abonnementsverzameling), levering en tracering.

### Stap 1: Abonnementsverzameling {#step-1--subscription-collection}

De mobiele toepassing wordt door de gebruiker gedownload van de App Store of van Google Play. Deze toepassing bevat de verbindingsinstellingen (iOS-certificaat en de projectsleutel voor Android) en de integratietoets. De eerste keer dat de toepassing wordt geopend (afhankelijk van de configuratie), kan de gebruiker worden gevraagd registratiegegevens in te voeren (@userKey: e-mail- of accountnummer bijvoorbeeld). Tegelijkertijd vraagt de toepassing de meldingsservice om een bericht-id (push-id) te verzamelen. Al deze informatie (verbindingsinstellingen, integratiesleutel, bericht-id, userKey) wordt naar Adobe Campaign verzonden.

![](assets/nmac_register_view.png)

### Stap 2: Levering {#step-2--delivery}

Marketers richten zich op toepassingsabonnees. Het leveringsproces verzendt de verbindingsmontages naar de berichtdienst (iOS certificaat en projectsleutel voor Android), bericht identiteitskaart (duw identiteitskaart) en de inhoud van het bericht. De kennisgevingsdienst stuurt meldingen naar de beoogde terminals.

De volgende informatie is beschikbaar in Adobe Campaign:

* Alleen Android: aantal apparaten dat de melding heeft weergegeven (afbeeldingen)
* Android en iOS: aantal klikken op het bericht

![](assets/nmac_delivery_view.png)

De Adobe Campaign-server moet contact kunnen opnemen met de APNs-server op de 443-poort voor de iOS HTTP/2-connector.

Om te controleren dat het correct werkt, gebruik de volgende bevelen:

* Voor tests:

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* In productie:

   ```
   telnet gateway.push.apple.com
   ```

Met de iOS HTTP/2-connector moeten de MTA-, webserver- en workflowserver contact kunnen opnemen met de APN&#39;s op poort 443.

