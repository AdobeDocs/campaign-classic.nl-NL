---
solution: Campaign Classic
product: campaign
title: Een Facebook-applicatie maken
description: Een Facebook-applicatie maken
audience: social
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 1%

---


# Een Facebook-applicatie maken{#creating-a-facebook-application}

Dankzij webtoepassingen kunt u met Social Marketing gepersonaliseerde inhoud weergeven in uw Facebook-toepassingen, waardoor het eenvoudiger wordt om vooruitzichten te krijgen via dit sociale netwerk. Raadpleeg [Voorbeelden van Facebook-apps](../../social/using/examples-of-facebook-apps.md) voor meer voorbeelden van Facebook-webtoepassingen.

>[!NOTE]
>
>Het is ook mogelijk om Adobe Campaign te integreren met een Facebook-toepassing die door een partner is ontwikkeld. In dit geval is het niet nodig om de Adobe Campaign-webtoepassing te gebruiken voor het aanschaffen van Facebook-profielen. Voor meer op dit, verwijs naar [Het vormen van externe rekeningen](#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

Pas de volgende configuratiestappen toe:

1. Maak een of meer Facebook-toepassingen. Raadpleeg voor meer informatie: [Een Facebook-toepassing maken](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application).
1. Voer de **[!UICONTROL terms of service]**- en **[!UICONTROL Privacy policy]**-koppelingen in die moeten worden weergegeven op het scherm voor het aanvragen van bevoegdheden op Facebook. Raadpleeg voor meer informatie: [De koppelingen voor service- en privacybeleid invoeren](#entering-the-terms-of-service-and-privacy-policy-links).
1. Maak voor elke Facebook-toepassing een **[!UICONTROL Facebook Connect]** type extern account. Raadpleeg voor meer informatie: [Externe accounts configureren](#configuring-external-accounts).
1. Maak voor elke Facebook-toepassing een Facebook-webtoepassing in Adobe Campaign. Raadpleeg voor meer informatie: [Een webtoepassing van het type Facebook maken](#creating-a-facebook-type-web-application).
1. Configureer uw Facebook-toepassingen zodat deze als tabbladen op uw Facebook-pagina worden weergegeven. Raadpleeg voor meer informatie: [Facebook-tabs configureren](#configuring-facebook-tabs).

## Externe accounts configureren {#configuring-external-accounts}

Voor elke Facebook-toepassing moet u een **[!UICONTROL Facebook Connect]** type extern account maken.

Voor deze stap hebt u toegang tot zowel uw Adobe Campaign-console als een internetbrowser die u hebt aangemeld bij de Facebook-account die u gebruikt voor paginabeheer:

* **Facebook**: Selecteer de eerder gemaakte toepassing (  [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) en selecteer het  **[!UICONTROL Settings]** >  **[!UICONTROL Basic]** tabblad.

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Als de **[!UICONTROL Facebook Web Games]** sectie niet verschijnt, klik **[!UICONTROL Add Platform]** knoop, bij de bodem van de pagina, en selecteer **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: Ga naar de  **[!UICONTROL Administration > Platform > External accounts]** knoop van de boom en klik  **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. Voer een label en een interne naam in en selecteer het type **[!UICONTROL Facebook Connect]**.

   ![](assets/social_webapp_fb_006.png)

1. Selecteer een hostingmodus voor de toepassing: **[!UICONTROL hosted by a partner]** of **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **Toepassing die door een partner wordt ontvangen**

   Het is mogelijk om Adobe Campaign te integreren met een Facebook-toepassing die door een partner is ontwikkeld. In dit geval is het niet nodig om de Adobe Campaign-webtoepassingen te gebruiken voor het aanschaffen van Facebook-profielen. Wanneer de Facebook-gebruiker de toepassing installeert, wordt een toets (toegangstoken) gegenereerd. De partner door:sturen dit toegangstoken aan Adobe Campaign door de Webdienst op te roepen. Adobe Campaign gebruikt dit token vervolgens om zich aan te melden bij de Facebook-database en de gegevens te verzamelen die de gebruiker via de toepassing deelt.

   >[!NOTE]
   >
   >De parameters van de webservice worden beschreven in het WSDL-bestand dat hier beschikbaar is: **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   Als u de externe toepassing wilt integreren in Adobe Campaign, moet u de inhoud van de Facebook-velden **[!UICONTROL App ID]** en **[!UICONTROL App Secret]** kopiëren en deze in de **[!UICONTROL Application ID]**- en **[!UICONTROL Application secret]**-velden van de console plakken.

   ![](assets/social_facebook_external_account_013.png)

   **Toepassing die door deze instantie wordt gehost**

   Als u de toepassing op deze instantie wilt hosten (als u geen externe toepassing hebt), moet u de Adobe Campaign-webtoepassingen gebruiken om Facebook-profielen aan te schaffen. Raadpleeg [Voorbeelden van Facebook-apps](../../social/using/examples-of-facebook-apps.md) voor meer informatie.

   Kopieer in de Adobe Campaign-console het adres in het veld **[!UICONTROL Secure Canvas URL]** en plak het in het veld **[!UICONTROL Facebook Web games (https)]** op Facebook (in de sectie **[!UICONTROL Facebook Web Games]**).

   ![](assets/social_facebook_external_account_009.png)

   >[!IMPORTANT]
   >
   >U mag in geen geval de onveilige URL gebruiken.

   Kopieer op Facebook de inhoud van de velden **[!UICONTROL App ID]** en **[!UICONTROL App Secret]** en plak deze in de velden **[!UICONTROL Application ID]** en **[!UICONTROL Application secret]** in de console.

   ![](assets/social_facebook_external_account_008.png)

1. Klik op Facebook op de knop **[!UICONTROL Save Changes]** onder aan de pagina.
1. Klik in de Adobe Campaign-console op de knop **[!UICONTROL Subscribe]** om Adobe Campaign in staat te stellen de gegevens in real-time te herstellen wanneer een ventilator via deze toepassing incheckt. Raadpleeg voor meer informatie: [Voorbeelden van Facebook-apps](../../social/using/examples-of-facebook-apps.md).

   ![](assets/social_webapp_fb_013.png)

## De koppelingen voor service- en privacybeleid invoeren {#entering-the-terms-of-service-and-privacy-policy-links}

We raden u ten zeerste aan de **[!UICONTROL Terms of service]**- en **[!UICONTROL Privacy policy]**-koppelingen toe te voegen, die moeten worden weergegeven op het scherm voor het aanvragen van bevoegdheden op Facebook.

![](assets/social_fb_terms_of_services_001.png)

De configuratiestadia zijn als volgt:

1. Voer het volgende adres in: [https://developers.facebook.com/apps](https://developers.facebook.com/apps), dan selecteer de toepassing van Facebook.
1. Selecteer de tab **[!UICONTROL Settings > Basic]** en voer de velden **[!UICONTROL Privacy Policy URL]** en **[!UICONTROL Terms of Service URL]** in.

   ![](assets/social_fb_terms_of_services.png)

## Een webtoepassing van het type Facebook maken {#creating-a-facebook-type-web-application}

Met de Adobe Campaign Facebook-toepassing kunt u persoonlijke inhoud weergeven in uw Facebook-toepassing. Voor elke Facebook-toepassing moet u een webtoepassing in Adobe Campaign maken. Ga als volgt te werk om een Facebook-webtoepassing te maken:

1. Ga naar **[!UICONTROL Social networks]** universum, klik **[!UICONTROL Applications]** verbinding, dan **[!UICONTROL Create]** knoop.

   ![](assets/social_webapp_001.png)

1. Selecteer een Facebook-webtoepassingssjabloon in de lijst en voer het label in.

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >Er worden standaard vier sjablonen voor Facebook-webtoepassingen aangeboden:
   >
   >* **[!UICONTROL New Facebook application]**: Selecteer deze sjabloon als u vanuit een lege toepassing wilt starten.
   >* **[!UICONTROL Pre-entered form]**: Een Facebook-toepassing met een formulier en een knop voor aanmelding bij Facebook waarmee gebruikers de velden van het formulier kunnen automatisch kunnen invullen met behulp van de gegevens uit hun profiel. Hierdoor kunnen gebruikers het formulier sneller invullen en kunnen merken informatie van betere kwaliteit verkrijgen.
   >* **[!UICONTROL "Canvas page" competition]**: De toepassing van Facebook die over het scherm voor een betere visuele ervaring voor de gebruikers wordt getoond.
   >* **[!UICONTROL "Page Tab" competition]**: De Facebook-toepassing is volledig geïntegreerd in de tabbladen van de merkpagina&#39;s.


1. Voer in het veld **[!UICONTROL Application]** de externe account in die is gekoppeld aan de Facebook-toepassing. Raadpleeg voor meer informatie: [Externe accounts configureren](#configuring-external-accounts).

   ![](assets/social_webapp_005.png)

1. Selecteer het tabblad **[!UICONTROL Edit]** en bewerk vervolgens de webtoepassing. Raadpleeg voor meer informatie: [Voorbeelden van Facebook-apps](../../social/using/examples-of-facebook-apps.md).

   ![](assets/social_webapp_003.png)

1. Wanneer de webtoepassing is voltooid, selecteert u het tabblad **[!UICONTROL Dashboard]** en klikt u op **[!UICONTROL Publish]** om online te publiceren.

   ![](assets/social_webapp_004.png)

## Facebook-tabbladen configureren {#configuring-facebook-tabs}

U kunt uw Facebook-toepassingen configureren om als tabbladen op uw Facebook-pagina te worden weergegeven. Hiervoor voert u de volgende stappen uit:

1. Selecteer de Facebook-toepassing ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) en selecteer het tabblad **[!UICONTROL Settings > Basic]**.

   ![](assets/social_webapp_fb_008.png)

1. Klik onder aan de pagina op de knop **[!UICONTROL Add Platform]** en selecteer **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. Voer in het veld **[!UICONTROL Page Tab Name]** van de sectie **[!UICONTROL Page Tab]** het label in zoals u het wilt weergeven op de Facebook-pagina.

   ![](assets/social_webapp_fb_001.png)

1. Voer in het veld **[!UICONTROL Secure Page Tab URL]** de openbare URL van de webtoepassing in. Deze URL is toegankelijk via het tabblad **[!UICONTROL Dashboard]** van de webtoepassing. Raadpleeg [Een webtoepassing van het type Facebook maken](#creating-a-facebook-type-web-application) voor meer informatie over het maken van webtoepassingen van het type Facebook.

   ![](assets/social_webapp_fb_002.png)

1. Klik op de koppeling **[!UICONTROL Dashboard]** van de webtoepassing.**[!UICONTROL Add a page tab]**

   ![](assets/social_webapp_fb_0010.png)

1. Selecteer de Facebook-pagina waaraan u het tabblad wilt toevoegen en klik op **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)

