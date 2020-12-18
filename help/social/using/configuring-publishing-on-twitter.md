---
solution: Campaign Classic
product: campaign
title: Publiceren op Twitter configureren
description: Publiceren op Twitter configureren
audience: social
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 2%

---


# Publiceren op Twitter configureren{#configuring-publishing-on-twitter}

Adobe Campaign kan alleen tweets verzenden naar uw Twitter-accounts als u voor deze accounts schrijftoegang naar Adobe Campaign wilt delegeren. Hiervoor past u de volgende configuratiestappen toe:

* Maak een Twitter-account.
* Maak een Twitter-testaccount voor het verzenden van proefdrukken.
* Maak één Twitter-toepassing per Twitter-account.
* Maak voor elke Twitter-toepassing een nieuwe **[!UICONTROL Twitter]**-typeservice.

![](assets/social_diagram_twitter_service.png)

## Vereisten {#prerequisites}

Maak eerst een of meer Twitter-accounts waarnaar u uw tweets wilt verzenden.

Als u een Twitter-account wilt maken, gaat u naar [https://twitter.com](https://twitter.com).

## Een testaccount maken op Twitter {#creating-a-test-account-on-twitter}

We raden u ook aan een persoonlijke Twitter-account te maken die kan worden gebruikt voor het verzenden van tweet-proefdrukken (zie [De proefdruk verzenden](../../social/using/publishing-on-twitter.md#sending-the-proof) voor meer informatie):

* Maak een nieuw Twitter-account.
* Klik op het menu in de rechterbovenhoek en selecteer **[!UICONTROL Settings]**.
* Selecteer de tab **[!UICONTROL Security and privacy]** en schakel het selectievakje **[!UICONTROL Protect my Tweets]** in.
* Klik op de knop **[!UICONTROL Save Changes]** onder aan de pagina.

![](assets/social_twitter_test_page.png)

## Een toepassing maken op Twitter {#creating-an-application-on-twitter}

Adobe Campaign kan alleen tweets verzenden naar uw Twitter-accounts als u per Twitter-account één Twitter-toepassing maakt. Hiervoor voert u de volgende stappen uit:

1. Meld u aan bij uw Twitter-account.
1. Voer het volgende adres in uw internetbrowser in: [https://apps.twitter.com/](https://apps.twitter.com/).
1. Klik vervolgens op de knop **[!UICONTROL Create New App]** rechts.

   ![](assets/social_create_twitter_app_001.png)

1. Laat de tovenaar u door het proces begeleiden.

   Als u wilt dat deze toepassing Adobe Campaign toestaat tweets naar uw account te verzenden, gaat u naar het tabblad **[!UICONTROL Permissions]** van de toepassing en selecteert u **[!UICONTROL Read and Write]** voor de sectie **[!UICONTROL Access]**. Op het tabblad **[!UICONTROL Settings]** moet u ook het veld **[!UICONTROL Callback URL]** leeg laten.

   ![](assets/social_create_twitter_app_002.png)

## Schrijftoegang delegeren aan Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Voor elke Twitter-toepassing moet u een andere **[!UICONTROL Twitter]**-typeservice maken die de toepassingsinstellingen bevat.

Voor deze stap hebt u gelijktijdig toegang tot uw Adobe Campaign-console en een internetbrowser nodig die u hebt aangemeld bij uw Twitter-account:

* **Twitter**: Selecteer de eerder gemaakte toepassing ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) en klik op het  **[!UICONTROL Keys and Access Tokens]** tabblad.

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: Ga naar het  **[!UICONTROL Profiles and targets]** universum, klik de  **[!UICONTROL Services and Subscriptions]** verbinding en klik de  **[!UICONTROL Create]** knoop.

   ![](assets/social_twitter_service_007.png)

1. Selecteer het type **[!UICONTROL Twitter]**.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >De optie **[!UICONTROL Synchronize subscriptions]** is standaard ingeschakeld. Als het selectievakje is ingeschakeld, herstelt de workflow voor het synchroniseren van Twitter-accounts (zie [Twitter-accounts synchroniseren](#synchronizing-twitter-accounts)) de lijst met Twitter-volgers, zodat u ze directe berichten kunt sturen (zie [Directe berichten verzenden aan abonnees](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Schakel dit selectievakje uit als u de lijst met volgers niet wilt herstellen.

1. Voer het label en de interne naam van de service in.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >De **[!UICONTROL Internal name]** van de service moet gelijk zijn aan de naam van de Twitter-account. Voer de volgende stappen hieronder uit om ervoor te zorgen dat er geen invoerfouten optreden.

   * Klik op de knop **[!UICONTROL Save]**.
   * Klik in het overzicht van de services op de Twitter-typeservice die u zojuist hebt gemaakt.
   * Selecteer het tabblad **[!UICONTROL Twitter page]**. Het Twitter-account moet worden weergegeven.

      ![](assets/social_twitter_service_010.png)

1. Selecteer in het veld **[!UICONTROL Visitor folder]** de bezoekersmap waarin de volgers worden gemaakt. Raadpleeg [Bedrijfsbeginsel](../../social/using/publishing-on-twitter.md#operating-principle) voor meer informatie hierover. Standaard worden volgers gemaakt in de hoofdmap van de map **[!UICONTROL Visitors]**.

   ![](assets/social_twitter_service_010_b.png)

1. Kopieer op Twitter de inhoud van de velden **[!UICONTROL Consumer Key (API Key)]** en **[!UICONTROL Consumer Secret (API Secret)]** en plak deze in de velden **[!UICONTROL Consumer key]** en **[!UICONTROL Consumer secret]** van de console.

   ![](assets/social_twitter_service_012.png)

1. Kopieer op Twitter de inhoud van de velden **[!UICONTROL Access Token]** en **[!UICONTROL Access Token Secret]** en plak deze in de velden **[!UICONTROL Access token]** en **[!UICONTROL Access token secret]** van de console.

   ![](assets/social_twitter_service_013.png)

1. Klik in de Adobe Campaign-console op **[!UICONTROL Save]**. Het delegeren van schrijftoegang tot Adobe Campaign is nu voltooid.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>U moet één **[!UICONTROL Twitter]** typeservice per Twitter-toepassing maken.

Met de **[!UICONTROL Twitter account Synchronization]**-workflow worden Twitter-accounts in Adobe Campaign gesynchroniseerd. Raadpleeg [Facebook-pagina&#39;s synchroniseren](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages) voor meer informatie.

## Twitter-accounts synchroniseren {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Als de workflow de lijst met Twitter-abonnees wil herstellen, moet het selectievakje **[!UICONTROL Twitter account synchronization]** zijn ingeschakeld in de sectie Bewerken van de service die aan de account is gekoppeld. Voor meer op dit, verwijs naar [Delend schrijf toegang aan Adobe Campaign](#delegating-write-access-to-adobe-campaign).

Met de **[!UICONTROL Twitter account synchronization]**-workflow, die toegankelijk is via het **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**-knooppunt, kunt u eerder geconfigureerde Twitter-accounts synchroniseren met Adobe Campaign. Deze workflow wordt standaard elke donderdag om 7.30 uur geactiveerd.

>[!NOTE]
>
>Het is mogelijk om de workflow op elk gewenst moment te starten door de verwachte taakverwerking uit te voeren. U kunt de planner ook uitgeven om het werkschema te veranderen dat frequentie teweegbrengt. Voor meer op de planner, verwijs naar [deze sectie](../../workflow/using/scheduler.md).

U kunt nu tweets verzenden naar uw Twitter-accounts en directe berichten sturen naar uw volgers. Raadpleeg voor meer informatie: [Publiceren op Twitter](../../social/using/publishing-on-twitter.md).
