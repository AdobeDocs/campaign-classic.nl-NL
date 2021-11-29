---
product: campaign
title: Publiceren op Twitter configureren
description: Publiceren op Twitter configureren
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2d2a6e32-587d-4a7b-ba1c-d9140da53f64
source-git-commit: d11c918213e72fe4bf6adb464e516fac19b63d54
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 7%

---

# Configuratiestappen voor publicatie op Twitter{#configuring-publishing-on-twitter}

![](../../assets/v7-only.svg)

Adobe Campaign kan alleen tweets verzenden naar uw Twitter-accounts als u voor deze accounts schrijfrechten naar Adobe Campaign wilt delegeren. Hiervoor past u de volgende configuratiestappen toe:

* Maak een Twitter-account.
* Maak een Twitter-testaccount voor het verzenden van proefdrukken.
* Maak één Twitter-toepassing per Twitter-account.
* Voor elke Twitter-toepassing maakt u een nieuwe **[!UICONTROL Twitter]** typeservice.

![](assets/social_diagram_twitter_service.png)

## Vereisten {#prerequisites}

Maak eerst een of meer Twitter-accounts waarop u uw tweets wilt verzenden.

Ga naar [https://twitter.com](https://twitter.com){target=&quot;_blank&quot;}.

## Een testaccount maken op Twitter {#creating-a-test-account-on-twitter}

Een particuliere Twitter-account maken die kan worden gebruikt voor verzending [proefdrukken van tweet](../../social/using/publishing-on-twitter.md#sending-the-proof). Voer de onderstaande stappen uit om een particuliere Twitter-account te maken:

1. Maak een nieuwe Twitter-account.
1. Toegang krijgen tot de account  **[!UICONTROL Settings]**.
1. Bladeren naar **[!UICONTROL Privacy & Safety]** en **[!UICONTROL Audience and Tagging]** en de **[!UICONTROL Protect your Tweets]** optie. Uw tweets en andere accountgegevens zijn alleen zichtbaar voor de personen die u volgen.

![](assets/social_twitter_test_page.png)

## Een toepassing maken op Twitter {#creating-an-application-on-twitter}

Adobe Campaign kan alleen tweets verzenden naar uw Twitter-accounts als u één Twitter-toepassing per Twitter-account maakt. Hiervoor voert u de volgende stappen uit:

1. Meld u aan bij uw Twitter-account.
1. Voer het volgende adres in uw internetbrowser in: [https://developer.twitter.com/en/apps](https://developer.twitter.com/en/apps).
1. Klik vervolgens op de knop **[!UICONTROL Create an App]** rechts.

   ![](assets/social_create_twitter_app_001.png)

1. Laat de tovenaar u door het proces begeleiden.

   Als u wilt dat deze toepassing Adobe Campaign toestaat tweets naar uw account te verzenden, gaat u naar de **[!UICONTROL Permissions]** tabblad van de toepassing en selecteert u **[!UICONTROL Read and Write]** voor de **[!UICONTROL Access]** sectie. In de **[!UICONTROL Settings]** , moet u ook de **[!UICONTROL Callback URL]** veld leeg.

   ![](assets/social_create_twitter_app_002.png)

## Schrijftoegang delegeren aan Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Voor elke Twitter-toepassing moet u een andere toepassing maken **[!UICONTROL Twitter]** typeservice die de toepassingsinstellingen zal bevatten.

Voor deze stap hebt u gelijktijdig toegang tot uw Adobe Campaign-console en een internetbrowser nodig die u hebt aangemeld bij uw Twitter-account:

* in **Twitter**: van [deze pagina](https://developer.twitter.com/en/portal/projects-and-apps), selecteert u de eerder gemaakte app en bewerkt u de **Toepassingsmachtigingen**.

   ![](assets/social_twitter_service_002.png)

   Bewerk de **Toetsen en tokens** voor toegang tot uw toepassingsgegevens.

* in **Adobe Campaign**: ga naar **[!UICONTROL Profiles and targets]** klikt u op de knop **[!UICONTROL Services and Subscriptions]** en klik op de knop **[!UICONTROL Create]** knop.

   ![](assets/social_twitter_service_007.png)

1. Selecteer **[!UICONTROL Twitter]** type.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >De **[!UICONTROL Synchronize subscriptions]** is standaard ingeschakeld. Als het selectievakje is ingeschakeld, wordt de workflow voor synchronisatie van Twitter-accounts gebruikt (zie [Twitter-accounts synchroniseren](#synchronizing-twitter-accounts)) herstelt de lijst met Twitter-volgers, zodat u deze rechtstreeks kunt versturen (zie [Directe berichten verzenden aan abonnees](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Schakel dit selectievakje uit als u de lijst met volgers niet wilt herstellen.

1. Voer het label en de interne naam van de service in.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >De **[!UICONTROL Internal name]** van de service moet gelijk zijn aan de naam van de Twitter-account. Pas de volgende stappen hieronder toe om ervoor te zorgen dat er geen invoerfouten zijn.

   * Klik op de knop **[!UICONTROL Save]**.
   * Klik in het overzicht van de services op de Twitter-service die u zojuist hebt gemaakt.

   <!-- * Select the **[!UICONTROL Twitter page]** tab. The Twitter account should be displayed. 
    
      ![](assets/social_twitter_service_010.png)-->

1. In de **[!UICONTROL Visitor folder]** selecteert u de map waarin de mappen worden gemaakt. Raadpleeg [deze sectie](../../social/using/publishing-on-twitter.md#operating-principle) voor meer informatie. Standaard worden volgers opgeslagen in de **[!UICONTROL Visitors]** map.

   ![](assets/social_twitter_service_010_b.png)

1. Kopieer in Twitter de inhoud van de **[!UICONTROL Consumer Key (API Key)]** en **[!UICONTROL Consumer Secret (API Secret)]** velden en plak deze in de **[!UICONTROL Consumer key]** en **[!UICONTROL Consumer secret]** velden van de Campagne-clientconsole.

   ![](assets/social_twitter_service_012.png)

1. Kopieer in Twitter de inhoud van de **[!UICONTROL Access Token]** en **[!UICONTROL Access Token Secret]** velden en plak deze in de **[!UICONTROL Access token]** en **[!UICONTROL Access token secret]** velden van de Campagne-clientconsole.

   ![](assets/social_twitter_service_013.png)

1. Klik in de Campagne-clientconsole op **[!UICONTROL Save]**. U hebt nu schrijftoegang gedelegeerd aan Adobe Campaign.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>U moet er een maken **[!UICONTROL Twitter]** service per Twitter-toepassing.

De **[!UICONTROL Twitter account Synchronization]** synchroniseert Twitter-accounts in Adobe Campaign. Raadpleeg [deze pagina](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages) voor meer informatie.

## Twitter-accounts synchroniseren {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Als de workflow de lijst met Twitter-abonnees moet herstellen, **[!UICONTROL Twitter account synchronization]** moet zijn ingeschakeld in het gedeelte Bewerken van de service die aan de account is gekoppeld. Raadpleeg [deze sectie](#delegating-write-access-to-adobe-campaign) voor meer informatie.

De **[!UICONTROL Twitter account synchronization]** workflow, die toegankelijk is via de **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** -knooppunt, kunt u Twitter-accounts synchroniseren die eerder met Adobe Campaign zijn geconfigureerd. Deze workflow wordt standaard elke donderdag om 7.30 uur geactiveerd.

>[!NOTE]
>
>U kunt de workflow op elk gewenst moment starten door de verwachte taakverwerking uit te voeren. U kunt de planner ook uitgeven om het werkschema te veranderen dat frequentie teweegbrengt. Voor meer op de planner, verwijs naar [deze sectie](../../workflow/using/scheduler.md).

U kunt nu tweets verzenden naar uw Twitter-accounts en directe berichten sturen naar uw volgers. Raadpleeg [deze pagina](../../social/using/publishing-on-twitter.md) voor meer informatie.
