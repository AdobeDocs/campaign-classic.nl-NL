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
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Mobiel toepassingskanaal{#about-mobile-app-channel}

>[!CAUTION]
>
>In dit document wordt beschreven hoe u uw mobiele toepassing kunt integreren met het Adobe Campaign-platform. De klasse biedt geen informatie over hoe de mobiele toepassing moet worden gemaakt of hoe deze moet worden geconfigureerd voor het beheer van meldingen. Raadpleeg de officiële Apple- [documentatie](https://developer.apple.com/) en de Android- [documentatie](https://developer.android.com/index.html)voor meer informatie hierover.

In de onderstaande secties vindt u informatie die specifiek is voor het mobiele toepassingskanaal.

 Raadpleeg[deze sectie](../../delivery/using/steps-about-delivery-creation-steps.md)voor algemene informatie over het maken van een levering.

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
>* U moet ervoor zorgen dat de meldingen die naar een mobiele toepassing worden verzonden, voldoen aan de voorwaarden en vereisten die door Apple (Apple Push Notification Service) en Google (Firebase Cloud Messaging) zijn opgegeven.
>* Waarschuwing: in sommige landen vereist de wet dat u de gebruikers informeert over uw verzamelde datatype mobiele toepassingen en het doel van hun verwerking . U moet de wetgeving controleren.


Met de **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt)-workflow worden abonnementen op mobiele apparaten bijgewerkt. Raadpleeg de handleiding [Workflows voor](../../workflow/using/mobile-app-channel.md)meer informatie over deze workflow.

Adobe Campaign is compatibel met zowel binaire als HTTP/2-APNS. Raadpleeg de sectie Een mobiele toepassing [configureren in Adobe Campagne](../../delivery/using/configuring-the-mobile-application.md) voor meer informatie over de configuratiestappen.

## Gegevenspad {#data-path}

In de volgende schema&#39;s worden de stappen beschreven waarmee een mobiele toepassing gegevens kan uitwisselen met Adobe Campaign. Dit proces omvat drie entiteiten:

* de mobiele toepassing
* de kennisgevingsdienst: APNS (Apple Push Notification Service) voor Apple en FCM (Firebase Cloud Messaging) voor Android
* Adobe-campagne

De drie belangrijkste stappen van het kennisgevingsproces zijn: registratie van de toepassing in Adobe Campaign (abonnementsinzameling), leveringen en tracering.

### Stap 1: Abonnementsverzameling {#step-1--subscription-collection}

De mobiele toepassing wordt door de gebruiker gedownload van de App Store of van Google Play. Deze toepassing bevat de verbindingsinstellingen (iOS-certificaat en de projectsleutel voor Android) en de integratietoets. De eerste keer dat de toepassing wordt geopend (afhankelijk van de configuratie), kan de gebruiker worden gevraagd registratiegegevens in te voeren (@userKey: e-mail- of accountnummer bijvoorbeeld). Tegelijkertijd vraagt de toepassing de meldingsservice om een bericht-id (push-id) te verzamelen. Al deze gegevens (verbindingsinstellingen, integratiesleutel, bericht-id, userKey) worden naar Adobe Campagne verzonden.

![](assets/nmac_register_view.png)

### Stap 2: Aflevering {#step-2--delivery}

Marketers richten zich op toepassingsabonnees. Het leveringsproces verzendt de verbindingsmontages naar de berichtdienst (iOS certificaat en projectsleutel voor Android), bericht identiteitskaart (duw identiteitskaart) en de inhoud van het bericht. De kennisgevingsdienst stuurt meldingen naar de beoogde terminals.

De volgende informatie is beschikbaar in de Campagne van Adobe:

* Alleen Android: aantal apparaten dat de melding heeft weergegeven (afbeeldingen)
* Android en iOS: aantal klikken op het bericht

![](assets/nmac_delivery_view.png)

De Adobe Campaign-server moet contact kunnen opnemen met de APNS-server op de volgende poorten:

* 2195 (verzenden) en 2186 (feedbackservice) voor binaire iOS-connector
* 443 voor iOS HTTP/2-connector

Om te controleren dat het correct werkt, gebruik de volgende bevelen:

* Voor tests:

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* In productie:

   ```
   telnet gateway.push.apple.com
   ```

Als een binaire iOS-connector wordt gebruikt, moeten de MTA en de webserver contact kunnen opnemen met de APNS op poort 2195 (verzenden), moet de workflowserver contact kunnen opnemen met de APNS op poort 2196 (feedbackservice).

Als een iOS HTTP/2-connector wordt gebruikt, moeten de MTA-, webserver- en workflowserver contact kunnen opnemen met de APNS op poort 443.

