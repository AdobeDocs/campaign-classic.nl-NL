---
product: campaign
title: Aan de slag met het kanaal voor mobiele apps
description: Ga aan de slag met het kanaal voor mobiele apps in Adobe Campaign
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 81b47231b027a189bc8b9029b7d48939734d08ed
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 7%

---

# Aan de slag met het kanaal voor mobiele apps{#about-mobile-app-channel}

De **Mobiel App-kanaal** Hiermee kunt u het Adobe Campaign-platform gebruiken om persoonlijke pushmeldingen naar iOS- en Android-terminals te verzenden via apps.

Er zijn twee leveringskanalen beschikbaar:

* Een iOS-kanaal waarmee u meldingen kunt verzenden naar mobiele Apple-apparaten.

  ![](assets/nmac_intro_2.png)

* Een Android-kanaal waarmee u gegevensberichten kunt verzenden naar mobiele Android-apparaten.

  ![](assets/nmac_intro_1.png)

  >[!IMPORTANT]
  >
  >In 2024 komt er een versie met enkele belangrijke wijzigingen voor de service FCM (Android Firebase Cloud Messaging). Deze kunnen van invloed zijn op uw Adobe Campaign-implementatie. De configuratie van uw lidmaatschapsservices voor Android-pushberichten moet mogelijk worden bijgewerkt om deze wijziging te ondersteunen. U kunt al controleren en actie ondernemen. Meer informatie in deze [Adobe Campaign v8-technologie](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=nl){target="_blank"}.

Voor deze twee kanalen zijn er twee leveringsactiviteiten in de campagneworkflows. Twee transactionele berichtmalplaatjes zijn ook beschikbaar voor transactieoverseinen.

![](assets/nmac_intro_3.png)


U kunt het gedrag van de toepassing bepalen wanneer de gebruiker het bericht activeert om het scherm te tonen dat de toepassingscontext aanpast. Bijvoorbeeld:

* Een bericht wordt verzonden naar de klant om hen te laten weten hun pakket het pakhuis heeft verlaten. Als u het bericht activeert, wordt er een pagina met leveringsgerelateerde informatie geopend.
* De gebruiker heeft items aan het winkelwagentje toegevoegd, maar heeft de toepassing verlaten zonder de aankoop te voltooien. Er wordt een bericht verzonden waarin wordt aangegeven dat hun winkelwagen is verlaten. Wanneer ze het bericht activeren, wordt het item op het scherm weergegeven.

>[!CAUTION]
>
>* U moet ervoor zorgen dat de berichten die naar een mobiele toepassing worden verzonden, voldoen aan de voorwaarden en vereisten die door Apple (Apple Push Notification Service) en Google (Firebase Cloud Messaging) zijn opgegeven.
>* Waarschuwing: in sommige landen vereist de wet dat u gebruikers op de hoogte stelt van uw verzamelde gegevenstype mobiele toepassingen en het doel van hun verwerking. U moet de wetgeving controleren.

De **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt)-workflowupdates voor meldingsabonnementen op mobiele apparaten. Raadpleeg voor meer informatie over deze workflow de [lijst van technische werkstromen](../../workflow/using/about-technical-workflows.md).

Adobe Campaign is compatibel met HTTP/2 APNs. Raadpleeg voor meer informatie over de configuratiestappen de [deze sectie](configuring-the-mobile-application.md) sectie.

Raadpleeg voor algemene informatie over het maken van een levering de [deze sectie](steps-about-delivery-creation-steps.md).


## Pushmeldingskanaal configureren {#push-notification-configuration}

Als u pushmeldingen wilt verzenden met Adobe Campaign, moet u eerst uw omgeving en app configureren. Voordat u pushberichten met Adobe Campaign gaat verzenden, moet u ervoor zorgen dat er configuraties en integratie zijn in de mobiele app en voor tags in Adobe Experience Platform. Adobe Experience Platform Mobile SDK biedt client-side integratie-API&#39;s voor uw mobiele apparaten via met Android en iOS compatibele SDK&#39;s. De configuratie SDKs wordt beheerd door de Inzameling UI van Gegevens voor flexibele configuratie en verlengbare, op regels-gebaseerde integratie. Meer informatie in [Adobe Campaign v8-documentatie](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/push/push-settings).


## Gegevenspad {#data-path}

In de volgende schema&#39;s worden de stappen beschreven waarmee een mobiele toepassing gegevens kan uitwisselen met Adobe Campaign. Dit proces omvat drie entiteiten:

* de mobiele toepassing
* de meldingsservice: APNs (Apple Push Notification Service) voor Apple en FCM (Firebase Cloud Messaging) voor Android
* Adobe Campaign

De drie belangrijkste stappen in het meldingsproces zijn: registratie van de toepassing in Adobe Campaign (abonnementsinzameling), leveringen en tracering.

### Stap 1: De inzameling van het abonnement {#step-1--subscription-collection}

De mobiele toepassing wordt door de gebruiker gedownload van de App Store of van Google Play. Deze toepassing bevat de verbindingsinstellingen (iOS-certificaat en projectsleutel voor Android) en de integratietoets. De eerste keer dat de toepassing wordt geopend (afhankelijk van de configuratie), kan de gebruiker worden gevraagd registratiegegevens in te voeren (@userKey: e-mail- of accountnummer bijvoorbeeld). Tegelijkertijd vraagt de toepassing de meldingsservice om een bericht-id (push-id) te verzamelen. Al deze informatie (verbindingsinstellingen, integratiesleutel, bericht-id, userKey) wordt naar Adobe Campaign verzonden.

![](assets/nmac_register_view.png)

### Stap 2: Levering {#step-2--delivery}

Marketers richten zich op toepassingsabonnees. Het leveringsproces verzendt de verbindingsmontages naar de berichtdienst (het certificaat van iOS en de projectsleutel voor Android), bericht identiteitskaart (duw identiteitskaart) en de inhoud van het bericht. De kennisgevingsdienst stuurt meldingen naar de beoogde terminals.

De volgende informatie is beschikbaar in Adobe Campaign:

* Alleen Android: aantal apparaten dat het bericht heeft weergegeven (afbeeldingen)
* Android en iOS: aantal klikken op het bericht

![](assets/nmac_delivery_view.png)

De Adobe Campaign-server moet contact kunnen opnemen met de APNs-server op de 443-poort voor de iOS HTTP/2-connector.

Om te controleren dat het correct werkt, gebruik de volgende bevelen:

* Voor tests:

  ```
  api.development.push.apple.com:443
  ```

* In productie:

  ```
  api.push.apple.com:443
  ```

Met de iOS HTTP/2-connector moeten de MTA en de webserver contact kunnen opnemen met de APN&#39;s op poort 443.

Als u de iOS HTTP/2-connector via een proxy moet gebruiken, raadpleegt u deze [page](../../installation/using/file-res-management.md#proxy-connection-configuration).
