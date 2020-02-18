---
title: Publiceren op Twitter configureren
seo-title: Publiceren op Twitter configureren
description: Publiceren op Twitter configureren
seo-description: null
page-status-flag: never-activated
uuid: 88867881-fb59-4f0d-862e-537d498e9aef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 9d74ed9c-0055-4556-a205-6e5fea11816b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Publiceren op Twitter configureren{#configuring-publishing-on-twitter}

Als u wilt dat Adobe Campaign tweets kan verzenden naar uw Twitter-accounts, moet u voor deze accounts schrijftoegang delegeren naar Adobe Campaign. Hiervoor past u de volgende configuratiestappen toe:

* Maak een Twitter-account.
* Maak een Twitter-testaccount voor het verzenden van proefdrukken.
* Maak één Twitter-toepassing per Twitter-account.
* Maak voor elke Twitter-toepassing een nieuwe **[!UICONTROL Twitter]** tekstservice.

![](assets/social_diagram_twitter_service.png)

## Vereisten {#prerequisites}

Maak eerst een of meer Twitter-accounts waarnaar u uw tweets wilt verzenden.

Ga naar [http://twitter.com](http://twitter.com)om een Twitter-account te maken.

## Een testaccount maken op Twitter {#creating-a-test-account-on-twitter}

We raden u ook aan een persoonlijke Twitter-account te maken die kan worden gebruikt voor het verzenden van proefdrukken van tweets (raadpleeg voor meer informatie de [proefdruk](../../social/using/publishing-on-twitter.md#sending-the-proof)verzenden):

* Maak een nieuw Twitter-account.
* Klik op het menu in de rechterbovenhoek en selecteer **[!UICONTROL Settings]**.
* Selecteer het **[!UICONTROL Security and privacy]** tabblad en schakel het **[!UICONTROL Protect my Tweets]** selectievakje in.
* Klik op de **[!UICONTROL Save Changes]** knop onder aan de pagina.

![](assets/social_twitter_test_page.png)

## Een toepassing maken op Twitter {#creating-an-application-on-twitter}

Als u wilt dat Adobe Campagne tweets kan verzenden naar uw Twitter-accounts, moet u één Twitter-toepassing maken per Twitter-account. Hiervoor voert u de volgende stappen uit:

1. Meld u aan bij uw Twitter-account.
1. Voer het volgende adres in uw internetbrowser in: [https://apps.twitter.com/](https://apps.twitter.com/).
1. Klik vervolgens op de **[!UICONTROL Create New App]** knop aan de rechterkant.

   ![](assets/social_create_twitter_app_001.png)

1. Laat de tovenaar u door het proces begeleiden.

   Als u wilt dat deze toepassing Adobe Campagne tweets kan verzenden naar uw account, gaat u naar het **[!UICONTROL Permissions]** tabblad van de toepassing en selecteert u **[!UICONTROL Read and Write]** de **[!UICONTROL Access]** sectie. Op het **[!UICONTROL Settings]** tabblad moet u ook het **[!UICONTROL Callback URL]** veld leeg laten.

   ![](assets/social_create_twitter_app_002.png)

## Schrijftoegang delegeren naar Adobe Campagne {#delegating-write-access-to-adobe-campaign}

Voor elke Twitter-toepassing moet u een andere **[!UICONTROL Twitter]** typeservice maken die de toepassingsinstellingen bevat.

Voor deze stap hebt u gelijktijdig toegang tot uw Adobe Campagne-console en een internetbrowser nodig die u hebt aangemeld bij uw Twitter-account:

* **Twitter**: Selecteer de eerder gemaakte toepassing ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) en klik op het **[!UICONTROL Keys and Access Tokens]** tabblad.

   ![](assets/social_twitter_service_002.png)

* **Adobe-campagne**: Ga naar het **[!UICONTROL Profiles and targets]** universum, klik de **[!UICONTROL Services and Subscriptions]** verbinding en klik de **[!UICONTROL Create]** knoop.

   ![](assets/social_twitter_service_007.png)

1. Selecteer het **[!UICONTROL Twitter]** type.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >De **[!UICONTROL Synchronize subscriptions]** optie is standaard ingeschakeld. Als het selectievakje is ingeschakeld, herstelt de workflow voor het synchroniseren van Twitter-accounts (zie [Twitter-accounts](#synchronizing-twitter-accounts)synchroniseren) de lijst met Twitter-volgers, zodat u hun directe berichten kunt sturen (zie [Directe berichten verzenden aan abonnees](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Schakel dit selectievakje uit als u de lijst met volgers niet wilt herstellen.

1. Voer het label en de interne naam van de service in.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >De naam **[!UICONTROL Internal name]** van de service moet gelijk zijn aan de naam van de Twitter-account. Pas de volgende stappen hieronder toe om ervoor te zorgen dat er geen invoerfouten zijn.

   * Klik op de **[!UICONTROL Save]** knop.
   * Klik in het overzicht van de services op de Twitter-typeservice die u zojuist hebt gemaakt.
   * Selecteer het **[!UICONTROL Twitter page]** tabblad. Het Twitter-account moet worden weergegeven.

      ![](assets/social_twitter_service_010.png)

1. Selecteer in het **[!UICONTROL Visitor folder]** veld de map van de bezoeker waarin de volgers worden gemaakt. Voor meer informatie hierover, verwijs naar het [Exploitatiebeginsel](../../social/using/publishing-on-twitter.md#operating-principle). Standaard worden volgers gemaakt in de hoofdmap van de **[!UICONTROL Visitors]** map.

   ![](assets/social_twitter_service_010_b.png)

1. Kopieer op Twitter de inhoud van de **[!UICONTROL Consumer Key (API Key)]** en de **[!UICONTROL Consumer Secret (API Secret)]** velden en plak deze in de **[!UICONTROL Consumer key]** en **[!UICONTROL Consumer secret]** velden van de console.

   ![](assets/social_twitter_service_012.png)

1. Kopieer op Twitter de inhoud van de **[!UICONTROL Access Token]** en de **[!UICONTROL Access Token Secret]** velden en plak deze in de **[!UICONTROL Access token]** en **[!UICONTROL Access token secret]** velden van de console.

   ![](assets/social_twitter_service_013.png)

1. Klik in de Adobe Campaign-console op **[!UICONTROL Save]**. Het delegeren van schrijftoegang naar Adobe Campaign is nu voltooid.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>U moet één **[!UICONTROL Twitter]** typeservice maken per Twitter-toepassing.

De **[!UICONTROL Twitter account Synchronization]** workflow synchroniseert Twitter-accounts in Adobe Campagne. Raadpleeg [Facebook-pagina&#39;s](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages)synchroniseren voor meer informatie.

## Twitter-accounts synchroniseren {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Als u wilt dat de lijst met Twitter-abonnees door de workflow wordt hersteld, moet u het **[!UICONTROL Twitter account synchronization]** vakje inschakelen in de sectie Bewerken van de service die aan de account is gekoppeld. Raadpleeg voor meer informatie het [delegeren van schrijftoegang tot Adobe Campagne](#delegating-write-access-to-adobe-campaign).

Met de **[!UICONTROL Twitter account synchronization]** workflow, die u kunt openen via het **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** knooppunt, kunt u eerder geconfigureerde Twitter-accounts synchroniseren met Adobe Campaign. Deze workflow wordt standaard elke donderdag om 7.30 uur geactiveerd.

>[!NOTE]
>
>Het is mogelijk om de workflow op elk gewenst moment te starten door de verwachte taakverwerking uit te voeren. U kunt de planner ook uitgeven om het werkschema te veranderen dat frequentie teweegbrengt. Voor meer op de planner, verwijs naar [deze sectie](../../workflow/using/scheduler.md).

U kunt nu tweets verzenden naar uw Twitter-accounts en directe berichten sturen naar uw volgers. Raadpleeg voor meer informatie: [Publiceren op Twitter](../../social/using/publishing-on-twitter.md).
