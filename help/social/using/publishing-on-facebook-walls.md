---
product: campaign
title: Publiceren op Facebook-pagina's
description: Publiceren op Facebook-pagina's
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2135a836-245f-406e-b351-c27d38e0f9fd
source-git-commit: b5334de18eca8fc1147ae0c42fe23a6932bf71d2
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 4%

---

# Publiceren op Facebook-pagina&#39;s{#publishing-on-facebook-walls}

![](../../assets/v7-only.svg)

Adobe Campaign kan alleen publicaties naar Facebook walls verzenden als u de schrijftoegang voor deze pagina&#39;s aan Adobe Campaign delegeert. Dit omvat de volgende configuratiestappen:

1. Maak een Facebook-account met een of meer pagina&#39;s.
1. Maak een Facebook-testpagina voor het verzenden van proefdrukken.
1. Een Facebook-applicatie maken.
1. Voer de instellingen van de Facebook-toepassing in in Adobe Campaign, in het dialoogvenster **[!UICONTROL Facebook routing]** externe rekening.

## Vereisten {#prerequisites}

Begin door een Facebook-account en meerdere pagina&#39;s te maken: deze zullen worden gebruikt voor de verzending van publicaties .

* Als u een Facebook-account wilt maken, gebruikt u de [https://www.facebook.com](https://www.facebook.com) koppeling.
* Als u een Facebook-pagina wilt maken, gebruikt u de opdracht [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create) koppeling.

   We raden je aan om hetzelfde Facebook-account te gebruiken voor het beheer van al je pagina&#39;s. Op deze manier hebt u slechts één Facebook-toepassing en één externe account nodig om op alle pagina&#39;s van de account te schrijven.

   ![](assets/social_diagram_fb_external_account.png)

## Een Facebook-testpagina maken {#creating-a-test-facebook-page}

We raden u aan een persoonlijke Facebook-pagina te maken voor het afleveren van proefdrukken (zie voor meer informatie hierover [deze sectie](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. Meld u aan bij de Facebook-account waarmee u uw pagina&#39;s beheert.
1. Maak een nieuwe Facebook-pagina.
1. Klik op de knop **[!UICONTROL Settings]** in de rechterbovenhoek.
1. In de **[!UICONTROL General]** wijzigt u de zichtbaarheidsparameters van de pagina: controleren **[!UICONTROL Page unpublished]** doos.
1. Klik op de knop **[!UICONTROL Save Changes]**.

![](assets/social_facebook_test_page.png)

## Een Facebook-applicatie maken {#creating-a-facebook-application}

Adobe Campaign kan alleen op de wanden van uw pagina&#39;s publiceren als u een Facebook-toepassing maakt. Hiervoor voert u de volgende stappen uit:

1. Meld u aan bij de Facebook-account waarmee u pagina&#39;s beheert.
1. Voer het volgende adres in uw browser in: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!CAUTION]
   >
   >Afhankelijk van het type account dat u hebt, kunnen een of meer machtigingen nodig zijn.
   >
   >Als u een Facebook-toepassing wilt maken, hebt u een **geverifieerd** Facebook-account.

1. Klik op de knop **[!UICONTROL Add a New App]** in de rechterbovenhoek van de pagina. Voer een toepassingsnaam en een e-mailbericht met contactgegevens in en geef vervolgens de beveiligingscontrole door.

   ![](assets/social_create_facebook_app_002.png)

1. Onder **[!UICONTROL Settings > Basic]**, klikt u op **[!UICONTROL Add a platform]** en selecteert u de **[!UICONTROL Facebook Web Games]** type.

   ![](assets/social_create_facebook_app_003.png)

1. In de **[!UICONTROL Products]** in het linkermenu controleren of de **[!UICONTROL Facebook Login]** product. Als dat niet het geval is, voegt u een nieuw product toe en selecteert u **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. Als de toepassing eenmaal is gemaakt, selecteert u de optie **[!UICONTROL App Review]** en publiceert u de toepassing.

   ![](assets/social_create_facebook_app_004.png)

## Schrijftoegang delegeren aan Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Als u schrijftoegang wilt delegeren aan Adobe Campaign voor het plaatsen op de wanden van uw pagina&#39;s, moet u de parameters van de eerder gemaakte Facebook-toepassing invoeren.

Voor deze stap hebt u zowel toegang tot uw Adobe Campaign-console als tot een internetbrowser die is aangemeld bij de Facebook-account die u gebruikt voor paginabeheer:

>[!CAUTION]
>
>De Adobe Campaign-exploitant moet beheerrechten hebben om deze configuratie uit te voeren.

* **Facebook**: Selecteer de eerder gemaakte toepassing ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) en selecteert u de **[!UICONTROL Settings > Basic]** tab.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Als de **[!UICONTROL Facebook Web Games]** niet wordt weergegeven, klikt u op de knop **[!UICONTROL Add Platform]** onder aan de pagina en selecteert u **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: ga naar **[!UICONTROL Administration > Platform > External Accounts]** knoop van de boom, selecteer **[!UICONTROL Facebook routing]** externe account en klik op de knop **[!UICONTROL Connector]** tab.

   ![](assets/social_facebook_external_account_001.png)

1. Kopieer in de Adobe Campaign-console het adres in het dialoogvenster **[!UICONTROL Secure Canvas URL]** veld en plak het in het **[!UICONTROL Secure Web Games URL (https)]** veld op Facebook (in het **[!UICONTROL Facebook Web Games]** ).

   ![](assets/social_facebook_external_account_006.png)

   >[!CAUTION]
   >
   >U mag in geen geval de onveilige URL gebruiken.

   Deze URL ook kopiëren en plakken onder **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. Als u de geldigheid van de URL wilt controleren, slaat u de toepassing op, kopieert en plakt u de URL in het dialoogvenster **[!UICONTROL Redirect URI to Check]** veld en klik op **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. Kopieer in Facebook de inhoud van de **[!UICONTROL App ID]** en **[!UICONTROL App Secret]** en plak het in de overeenkomstige gebieden van de console.

   ![](assets/social_facebook_external_account_007.png)

1. Klik in Facebook op de knop **[!UICONTROL Save Changes]** onder aan de pagina.
1. Ga naar de Adobe Campaign-console, sla de externe account op.

   >[!NOTE]
   >
   >De **[!UICONTROL Marketing URL]** veld is optioneel.

1. Klik in de Adobe Campaign-console op de knop **[!UICONTROL Request the authorization from the application]** koppeling onder aan **[!UICONTROL Connector]** tab. De **[!UICONTROL Synchronize Facebook pages]** de workflow wordt automatisch geactiveerd en verzamelt alle Facebook-pagina&#39;s die door de beheerder worden beheerd. [Meer informatie](#synchronizing-facebook-pages).

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Standaard worden de pagina&#39;s toegevoegd aan de **[!UICONTROL Facebook]** servicemap, beschikbaar via de **[!UICONTROL Profiles and Targets > Services and Subscriptions]** knooppunt. De **[!UICONTROL Folder]** van het **[!UICONTROL Connector]** kunt u de servicemap wijzigen waarin de Facebook-pagina&#39;s na synchronisatie worden gemaakt. U kunt ook de Facebook-pagina&#39;s selecteren die u in Adobe Campaign wilt synchroniseren dankzij de **[!UICONTROL Filter]** veld. Als u dit veld leeg laat, worden alle Facebook-pagina&#39;s die door de beheerder worden beheerd, gesynchroniseerd.

1. Er wordt een dialoogvenster weergegeven met de verschillende Facebook-machtigingsinstellingen. Hiermee kan Adobe Campaign publicaties naar de Facebook-accountpagina&#39;s verzenden.

   Accepteer de verschillende machtigingsaanvragen.

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign heeft het recht om op de wanden van de pagina&#39;s van het Facebook-account te publiceren.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Als de Facebook-account meerdere pagina&#39;s beheert, configureert u gewoon één externe account om op elke pagina van de Facebook-account te schrijven. Voor elke nieuwe Facebook-account moet je een nieuwe **[!UICONTROL Routing]** type external account.

De **[!UICONTROL Synchronization of Facebook pages]** Met deze workflow synchroniseert u alle pagina&#39;s die door de Facebook-account worden beheerd, zodat u rechtstreeks via Adobe Campaign op de muur kunt plaatsen. [Meer informatie](#synchronizing-facebook-pages).

## Facebook-pagina&#39;s synchroniseren {#synchronizing-facebook-pages}

De **[!UICONTROL Synchronization of Facebook pages]** workflow, die toegankelijk is via de **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** -knooppunt, kunt u (in Adobe Campaign) de pagina&#39;s synchroniseren van de Facebook-account die eerder is geconfigureerd. Deze workflow is standaard geconfigureerd om één keer per dag te worden uitgevoerd, of telkens wanneer een beheerder op de knop **[!UICONTROL Request an authorization from the application]** verbinding in het scherm van de de dienstconfiguratie. [Meer informatie](#delegating-write-access-to-adobe-campaign).

Zodra de synchronisatie is voltooid, worden de verzamelde pagina&#39;s weergegeven in de servicemap die is ingevoerd in de externe account. [Meer informatie](#delegating-write-access-to-adobe-campaign)).

Standaard worden pagina&#39;s toegevoegd aan de hoofdmap van het dialoogvenster **[!UICONTROL Facebook]** servicemap die beschikbaar is via de **[!UICONTROL Profiles and Targets > Services and subscriptions]** -menu.

![](assets/social_facebook_service_002.png)

U kunt nu rechtstreeks via Adobe Campaign publiceren op de wanden van uw Facebook-pagina&#39;s. [Meer informatie](#publishing-on-facebook-walls).
