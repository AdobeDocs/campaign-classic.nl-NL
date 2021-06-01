---
product: campaign
title: Publiceren op Facebook-walls
description: Publiceren op Facebook-walls
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2135a836-245f-406e-b351-c27d38e0f9fd
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 2%

---

# Publiceren op Facebook-walls{#publishing-on-facebook-walls}

Adobe Campaign kan alleen publicaties naar Facebook walls verzenden als u de schrijftoegang voor deze pagina&#39;s aan Adobe Campaign delegeert. Dit omvat de volgende configuratiestappen:

1. Maak een Facebook-account met een of meer pagina&#39;s.
1. Maak een Facebook-testpagina voor het verzenden van proefdrukken.
1. Een Facebook-applicatie maken.
1. Voer de Facebook-toepassingsinstellingen in Adobe Campaign in op de externe account **[!UICONTROL Facebook routing]**.

## Vereisten {#prerequisites}

Begin door een Facebook-account en meerdere pagina&#39;s te maken: deze zullen worden gebruikt voor de verzending van publicaties .

* Als u een Facebook-account wilt maken, gebruikt u de koppeling [https://www.facebook.com](https://www.facebook.com).
* Als u een Facebook-pagina wilt maken, gebruikt u de koppeling [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create).

   We raden je aan om hetzelfde Facebook-account te gebruiken voor het beheer van al je pagina&#39;s. Op deze manier hebt u slechts één Facebook-toepassing en één externe account nodig om op alle pagina&#39;s van de account te schrijven.

   ![](assets/social_diagram_fb_external_account.png)

## Een Facebook-testpagina {#creating-a-test-facebook-page} maken

We raden u aan een persoonlijke Facebook-pagina te maken voor het afleveren van proefdrukken (zie [De proefdruk verzenden](../../social/using/publishing-on-facebook.md#sending-the-proof) voor meer informatie.

1. Meld u aan bij de Facebook-account waarmee u uw pagina&#39;s beheert.
1. Maak een nieuwe Facebook-pagina.
1. Klik op de knop **[!UICONTROL Settings]** in de rechterbovenhoek.
1. Wijzig op het tabblad **[!UICONTROL General]** de zichtbaarheidsparameters van de pagina: Schakel het selectievakje **[!UICONTROL Page unpublished]** in.
1. Klik op de knop **[!UICONTROL Save Changes]**.

![](assets/social_facebook_test_page.png)

## Een Facebook-applicatie maken {#creating-a-facebook-application}

Adobe Campaign kan alleen op de wanden van uw pagina&#39;s publiceren als u een Facebook-toepassing maakt. Hiervoor voert u de volgende stappen uit:

1. Meld u aan bij de Facebook-account waarmee u pagina&#39;s beheert.
1. Voer het volgende adres in uw browser in: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!IMPORTANT]
   >
   >Afhankelijk van het type account dat u hebt, kunnen een of meer machtigingen nodig zijn.
   >
   >Als u een Facebook-toepassing wilt maken, hebt u een **geverifieerde** Facebook-account nodig.

1. Klik op de knop **[!UICONTROL Add a New App]** in de rechterbovenhoek van de pagina. Voer een toepassingsnaam en een e-mailbericht met contactgegevens in en geef vervolgens de beveiligingscontrole door.

   ![](assets/social_create_facebook_app_002.png)

1. Klik onder **[!UICONTROL Settings > Basic]** op **[!UICONTROL Add a platform]** en selecteer het type **[!UICONTROL Facebook Web Games]**.

   ![](assets/social_create_facebook_app_003.png)

1. Controleer in de sectie **[!UICONTROL Products]** in het linkermenu of u het product **[!UICONTROL Facebook Login]** ziet. Als dat niet het geval is, voegt u een nieuw product toe en selecteert u **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. Nadat de toepassing is gemaakt, selecteert u het tabblad **[!UICONTROL App Review]** en publiceert u de toepassing.

   ![](assets/social_create_facebook_app_004.png)

## Schrijftoegang delegeren aan Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Als u schrijftoegang wilt delegeren aan Adobe Campaign voor het plaatsen op de wanden van uw pagina&#39;s, moet u de parameters van de eerder gemaakte Facebook-toepassing invoeren.

Voor deze stap hebt u zowel toegang tot uw Adobe Campaign-console als tot een internetbrowser die is aangemeld bij de Facebook-account die u gebruikt voor paginabeheer:

>[!IMPORTANT]
>
>De Adobe Campaign-exploitant moet beheerrechten hebben om deze configuratie uit te voeren.

* **Facebook**: Selecteer de eerder gemaakte toepassing (  [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) en selecteer het  **[!UICONTROL Settings > Basic]** tabblad.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Als de **[!UICONTROL Facebook Web Games]** sectie niet verschijnt, klik **[!UICONTROL Add Platform]** knoop, bij de bodem van de pagina, en selecteer **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: Ga naar het  **[!UICONTROL Administration > Platform > External Accounts]** knooppunt van de structuur, selecteer de  **[!UICONTROL Facebook routing]** externe account en klik op het  **[!UICONTROL Connector]** tabblad.

   ![](assets/social_facebook_external_account_001.png)

1. Kopieer in de Adobe Campaign-console het adres in het veld **[!UICONTROL Secure Canvas URL]** en plak het in het veld **[!UICONTROL Secure Web Games URL (https)]** in Facebook (in de sectie **[!UICONTROL Facebook Web Games]**).

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >U mag in geen geval de onveilige URL gebruiken.

   Kopieer en plak deze URL ook onder **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. Als u de geldigheid van de URL wilt controleren, slaat u de toepassing op, kopieert en plakt u de URL in het veld **[!UICONTROL Redirect URI to Check]** en klikt u op **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. Kopieer in Facebook de inhoud van de velden **[!UICONTROL App ID]** en **[!UICONTROL App Secret]** en plak deze in de overeenkomende velden van de console.

   ![](assets/social_facebook_external_account_007.png)

1. Klik in Facebook op de knop **[!UICONTROL Save Changes]** onder aan de pagina.
1. Ga naar de Adobe Campaign-console, sla de externe account op.

   >[!NOTE]
   >
   >Het veld **[!UICONTROL Marketing URL]** is optioneel.

1. Klik in de Adobe Campaign-console op de koppeling **[!UICONTROL Request the authorization from the application]** onder aan het tabblad **[!UICONTROL Connector]**. De **[!UICONTROL Synchronize Facebook pages]** workflow wordt automatisch geactiveerd en verzamelt alle Facebook-pagina&#39;s die door de beheerder worden beheerd. Raadpleeg [Facebook-pagina&#39;s synchroniseren](#synchronizing-facebook-pages) voor meer informatie.

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Standaard worden de pagina&#39;s toegevoegd aan de servicemap **[!UICONTROL Facebook]**, die beschikbaar is via het knooppunt **[!UICONTROL Profiles and Targets > Services and Subscriptions]**. In het veld **[!UICONTROL Folder]** van het tabblad **[!UICONTROL Connector]** kunt u de servicemap wijzigen waarin de Facebook-pagina&#39;s na synchronisatie worden gemaakt. U kunt ook de Facebook-pagina&#39;s selecteren die u in Adobe Campaign wilt synchroniseren via het veld **[!UICONTROL Filter]**. Als u dit veld leeg laat, worden alle Facebook-pagina&#39;s die door de beheerder worden beheerd, gesynchroniseerd.

1. Er wordt een dialoogvenster weergegeven met de verschillende Facebook-machtigingsinstellingen. Hiermee kan Adobe Campaign publicaties naar de Facebook-accountpagina&#39;s verzenden.

   Accepteer de verschillende machtigingsaanvragen.

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign heeft het recht om op de wanden van de pagina&#39;s van het Facebook-account te publiceren.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Als de Facebook-account meerdere pagina&#39;s beheert, configureert u gewoon één externe account om op elke pagina van de Facebook-account te schrijven. Voor elke nieuwe Facebook-account moet u een nieuwe **[!UICONTROL Routing]**-type externe account maken.

Met de **[!UICONTROL Synchronization of Facebook pages]**-workflow worden alle pagina&#39;s gesynchroniseerd die door de Facebook-account worden beheerd, zodat u rechtstreeks via Adobe Campaign op de muur kunt plaatsen. Raadpleeg [Facebook-pagina&#39;s synchroniseren](#synchronizing-facebook-pages) voor meer informatie.

## Facebook-pagina&#39;s {#synchronizing-facebook-pages} synchroniseren

Met de **[!UICONTROL Synchronization of Facebook pages]**-workflow, die toegankelijk is via het **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**-knooppunt, kunt u (in Adobe Campaign) de pagina&#39;s van de Facebook-account synchroniseren die eerder zijn geconfigureerd. Door gebrek, wordt dit werkschema gevormd om één keer per dag te lopen of wanneer een beheerder de **[!UICONTROL Request an authorization from the application]** verbinding in het scherm van de de dienstconfiguratie klikt (verwijs naar [Delend schrijf toegang aan Adobe Campaign](#delegating-write-access-to-adobe-campaign)).

Nadat de synchronisatie is voltooid, worden de verzamelde pagina&#39;s weergegeven in de servicemap die is ingevoerd in de externe account (zie [Schrijftoegang delegeren naar Adobe Campaign](#delegating-write-access-to-adobe-campaign)). Pagina&#39;s worden standaard toegevoegd aan de hoofdmap van de servicemap **[!UICONTROL Facebook]**, die beschikbaar is via het menu **[!UICONTROL Profiles and Targets > Services and subscriptions]**.

![](assets/social_facebook_service_002.png)

U kunt nu rechtstreeks via Adobe Campaign publiceren op de wanden van uw Facebook-pagina&#39;s. Raadpleeg [Publiceren op Facebook](#publishing-on-facebook-walls) voor meer informatie.
