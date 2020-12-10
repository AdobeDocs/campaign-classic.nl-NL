---
solution: Campaign Classic
product: campaign
title: Pushmeldingen maken
description: Meer informatie over het maken van pushmeldingen
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 4%

---


# Meldingen maken{#creating-notifications}

In deze sectie worden de elementen beschreven die specifiek zijn voor de levering van iOS- en Android-berichten. Algemene concepten voor het maken van leveringen worden weergegeven in [deze sectie](../../delivery/using/steps-about-delivery-creation-steps.md).

Begin door een nieuwe levering te maken.

![](assets/nmac_delivery_1.png)

## Meldingen verzenden op iOS {#sending-notifications-on-ios}

1. Selecteer de leveringssjabloon **[!UICONTROL Deliver on iOS]**.

   ![](assets/nmac_delivery_ios_1.png)

1. Als u het doel van de melding wilt definiëren, klikt u op de koppeling **[!UICONTROL To]** en vervolgens op **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >Het gedetailleerde proces wanneer het selecteren van de doelpopulatie van een levering wordt voorgesteld in [deze sectie](../../delivery/using/steps-defining-the-target-population.md).
   >
   >Raadpleeg [Informatie over personalisatie](../../delivery/using/about-personalization.md) voor meer informatie over het gebruik van verpersoonlijkingsvelden.
   >
   >Voor meer op de opneming van een zaadlijst, verwijs naar [Ongeveer zaadadressen](../../delivery/using/about-seed-addresses.md).

1. Selecteer **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, selecteer de service die relevant is voor uw mobiele toepassing (in dit geval Neotrips) en selecteer vervolgens de iOS-versie van de toepassing.

   ![](assets/nmac_delivery_ios_3.png)

1. Selecteer het berichttype: **[!UICONTROL Alert]**, **[!UICONTROL Badge]**, of **[!UICONTROL Alert and badge]** of **[!UICONTROL Silent Push]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >De modus **Silent Push** is beschikbaar in iOS 7. Hierdoor kan een &quot;stille&quot; melding naar een mobiele toepassing worden verzonden. De gebruiker wordt niet op de hoogte gebracht van de aankomst van de melding. Deze wordt rechtstreeks naar de toepassing overgedragen.

1. Voer in het veld **[!UICONTROL Title]** het label in van de titel die u in het bericht wilt weergeven. Deze wordt alleen weergegeven in de lijst met meldingen die beschikbaar zijn in het meldingscentrum. In dit veld kunt u de waarde definiëren van de parameter **title** van de payload van de iOS-melding.

1. Als u de HTTP/2-connector gebruikt, kunt u een ondertitel (waarde van de parameter **subtitle** van de iOS-berichtlading) toevoegen. Raadpleeg de sectie [Mobiele toepassing configureren in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Voer vervolgens de **[!UICONTROL Message]** en **[!UICONTROL Value of the badge]** in op basis van het gekozen berichttype.

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** en  **[!UICONTROL Alert and badge]** typedeclaraties kunt u de waarde van de badge wijzigen (het nummer boven het logo van de mobiele toepassing). Als u de badge wilt vernieuwen, hoeft u alleen 0 als waarde in te voeren. Als het veld leeg is, verandert de waarde van de badge niet.

1. Klik op het pictogram **[!UICONTROL Insert emoticon]** om emoticons in te voegen bij uw pushmelding. Als u de lijst met emoticonen wilt aanpassen, raadpleegt u [het aanpassen van de lijst met emoticonen](../../delivery/using/customizing-emoticon-list.md)

1. Met **[!UICONTROL Action button]** kunt u een label definiëren voor de actieknop die wordt weergegeven in de waarschuwingsberichten (**action_loc_key** veld van de payload). Als uw iOS-toepassing landinstellbare tekenreeksen beheert (**Localizable.strings**), voert u de bijbehorende sleutel in dit veld in. Als uw toepassing geen landinstellbare tekst beheert, voert u het label in dat u wilt zien op de actieknop. Raadpleeg de [documentatie van Apple](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) voor meer informatie over landinstellbare tekenreeksen.
1. Selecteer in het veld **[!UICONTROL Play a sound]** het geluid dat door de mobiele terminal moet worden afgespeeld wanneer het bericht wordt ontvangen.

   >[!NOTE]
   >
   >Geluiden moeten in de toepassing worden opgenomen en worden gedefinieerd wanneer de service wordt gemaakt. Zie [Externe iOS-account configureren](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios).

1. Voer in het veld **[!UICONTROL Application variables]** de waarde van elke variabele in. Met toepassingsvariabelen kunt u berichtgedrag definiëren: U kunt bijvoorbeeld een specifiek toepassingsscherm configureren dat moet worden weergegeven wanneer de gebruiker het bericht activeert.

   >[!NOTE]
   >
   >Toepassingsvariabelen moeten worden gedefinieerd in de code van de mobiele toepassing en moeten worden ingevoerd tijdens het maken van de service. Raadpleeg voor meer informatie: [Een mobiele toepassing configureren in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Zodra het bericht wordt gevormd, klik **[!UICONTROL Preview]** lusje om voorproef de bericht.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >De berichtstijl (banner of waarschuwing) wordt niet gedefinieerd in Adobe Campaign. Het hangt van de configuratie af die door de gebruiker in hun iOS montages wordt geselecteerd. In Adobe Campaign kunt u echter elk type berichtstijl bekijken. Klik op de pijl rechtsonder om van de ene stijl naar de andere te gaan.
   >
   >In de voorvertoning wordt de iOS 10-vormgeving gebruikt.

Als u een bewijs wilt verzenden en de uiteindelijke levering wilt verzenden, gebruikt u hetzelfde proces als voor e-mailleveringen.

Nadat u berichten hebt verzonden, kunt u de leveringen controleren en volgen. Raadpleeg deze secties voor meer informatie hierover:

* [Push notification quarantines](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Een levering controleren](../../delivery/using/about-delivery-monitoring.md)
* [Leveringsfouten begrijpen](../../delivery/using/understanding-delivery-failures.md)

## Meldingen verzenden op Android {#sending-notifications-on-android}

1. Begin door **[!UICONTROL Deliver on Android (android)]** leveringsmalplaatje te selecteren.

   ![](assets/nmac_delivery_android_1.png)

1. Als u het doel van de melding wilt definiëren, klikt u op de koppeling **[!UICONTROL To]** en vervolgens op **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_android_2.png)

1. Selecteer **[!UICONTROL Subscribers of an Android mobile application]**, kies de dienst relevant voor uw mobiele toepassing (in dit geval Neotrips), dan selecteer de Android versie van de toepassing.

   ![](assets/nmac_delivery_android_3.png)

1. Voer vervolgens de inhoud voor het bericht in.

   ![](assets/nmac_delivery_android_4.png)

1. Klik op het pictogram **[!UICONTROL Insert emoticon]** om emoticons in te voegen bij uw pushmelding. Als u de lijst met emoticonen wilt aanpassen, raadpleegt u [het aanpassen van de lijst met emoticonen](../../delivery/using/defining-interactive-content.md)

1. Voer in het veld **[!UICONTROL Application variables]** de waarde van elke variabele in. Met toepassingsvariabelen kunt u berichtgedrag definiëren: U kunt bijvoorbeeld een specifiek toepassingsscherm configureren dat moet worden weergegeven wanneer de gebruiker het bericht activeert.

   >[!NOTE]
   >
   >Toepassingsvariabelen moeten worden gedefinieerd in de code van de mobiele toepassing en moeten worden ingevoerd tijdens het maken van de service. Raadpleeg voor meer informatie: [Een mobiele toepassing configureren in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Zodra het bericht wordt gevormd, klik **[!UICONTROL Preview]** lusje om voorproef de bericht.

   ![](assets/nmac_intro_1.png)

Als u een bewijs wilt verzenden en de uiteindelijke levering wilt verzenden, gebruikt u hetzelfde proces als voor e-mailleveringen.

Het gedetailleerde proces voor het valideren en verzenden van een levering wordt in de volgende secties weergegeven:

* [De levering valideren](../../delivery/using/steps-validating-the-delivery.md)
* [De levering verzenden](../../delivery/using/steps-sending-the-delivery.md)

Nadat u berichten hebt verzonden, kunt u de leveringen controleren en volgen. Raadpleeg deze secties voor meer informatie hierover:

* [Push notification quarantines](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Een levering controleren](../../delivery/using/about-delivery-monitoring.md)
* [Leveringsfouten begrijpen](../../delivery/using/understanding-delivery-failures.md)
