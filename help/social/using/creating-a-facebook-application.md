---
product: campaign
title: Een Facebook-applicatie maken
description: Een Facebook-applicatie maken
audience: social
content-type: reference
topic-tags: configuration
exl-id: 5c11bd0f-2df7-4c7f-b682-955fedf8e664
source-git-commit: d891a235002d465f3b00fafa375d87d42ebafaa6
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 5%

---

# Een Facebook-applicatie maken{#creating-a-facebook-application}

![](../../assets/v7-only.svg)

Met behulp van webtoepassingen kunt u in de module Campagne Social Marketing gepersonaliseerde inhoud weergeven in uw Facebook-toepassingen, waardoor het eenvoudiger wordt om vooruitzichten te krijgen via deze sociale media. Raadpleeg voor meer voorbeelden van webtoepassingen van het Facebook-type de [deze pagina](../../social/using/examples-of-facebook-apps.md).

>[!NOTE]
>
>U kunt Adobe Campaign ook integreren met een Facebook-toepassing die door een partner is ontwikkeld. In dit geval hoeft u de Adobe Campaign-webtoepassing niet te gebruiken voor het aanschaffen van Facebook-profielen. [Meer informatie](#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

Configuratiestappen zijn:

1. Maak een of meer Facebook-toepassingen.
1. Voer de **[!UICONTROL terms of service]** en **[!UICONTROL Privacy policy]** koppelingen die moeten worden weergegeven op het scherm voor Facebook-machtigingsaanvragen. [Meer informatie](#entering-the-terms-of-service-and-privacy-policy-links)
1. Voor elke Facebook-toepassing maakt u een **[!UICONTROL Facebook Connect]** type external account. [Meer informatie](#configuring-external-accounts)
1. Maak voor elke Facebook-toepassing een Facebook-webtoepassing in Adobe Campaign. [Meer informatie](#creating-a-facebook-type-web-application)
1. Configureer uw Facebook-toepassingen zodanig dat deze als tabbladen op uw Facebook-pagina worden weergegeven. [Meer informatie](#configuring-facebook-tabs)

## Externe accounts configureren {#configuring-external-accounts}

Voor elke Facebook-toepassing moet u een **[!UICONTROL Facebook Connect]** type external account.

Voor deze stap hebt u toegang tot uw Adobe Campaign-console en uw Facebook-beheerdersaccount nodig:

* Aan **Facebook**: Selecteer de eerder gemaakte toepassing ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) en selecteert u de **[!UICONTROL Settings]** > **[!UICONTROL Basic]** tab.

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Als de **[!UICONTROL Facebook Web Games]** niet wordt weergegeven, klikt u op de knop **[!UICONTROL Add Platform]** onder aan de pagina en selecteert u **[!UICONTROL Facebook Web Games]**.

* Aan **Adobe Campaign**: bladeren naar **[!UICONTROL Administration > Platform > External accounts]** en klik op **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. Voer een label en een interne naam in en selecteer de **[!UICONTROL Facebook Connect]** type.

   ![](assets/social_webapp_fb_006.png)

1. Selecteer de hostingmodus van de toepassing: **[!UICONTROL hosted by a partner]** of **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **Toepassing die door een partner wordt ontvangen**

   Het is mogelijk om Adobe Campaign te integreren met een Facebook-toepassing die door een partner is ontwikkeld. In dit geval is het niet nodig om Adobe Campaign-webtoepassingen te gebruiken voor het aanschaffen van Facebook-profielen. Wanneer de Facebook-gebruiker de toepassing installeert, wordt een toets (toegangstoken) gegenereerd. De partner door:sturen dit toegangstoken aan Adobe Campaign door de Webdienst op te roepen. Adobe Campaign gebruikt dit token vervolgens om zich aan te melden bij de Facebook-database en de gegevens te verzamelen die de gebruiker via de toepassing deelt.

   >[!NOTE]
   >
   >De parameters van de webservice worden beschreven in het WSDL-bestand dat hier beschikbaar is: **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   Als u de externe toepassing wilt integreren in Adobe Campaign, moet u de inhoud van het dialoogvenster **[!UICONTROL App ID]** en **[!UICONTROL App Secret]** Facebook-velden en plak deze in de **[!UICONTROL Application ID]** en **[!UICONTROL Application secret]** velden van de console.

   ![](assets/social_facebook_external_account_013.png)

   **Toepassing die door deze instantie wordt gehost**

   Als u de toepassing op deze instantie wilt hosten (als u geen externe toepassing hebt), moet u de Adobe Campaign-webtoepassingen gebruiken om Facebook-profielen aan te schaffen. Raadpleeg [deze pagina](../../social/using/examples-of-facebook-apps.md) voor meer informatie.

   Kopieer in de Adobe Campaign-console het adres in het dialoogvenster **[!UICONTROL Secure Canvas URL]** veld en plak het in het **[!UICONTROL Facebook Web games (https)]** veld op Facebook (in het **[!UICONTROL Facebook Web Games]** ).

   ![](assets/social_facebook_external_account_009.png)

   >[!CAUTION]
   >
   >Gebruik geen onveilige URL&#39;s.

   Kopieer in Facebook de inhoud van de **[!UICONTROL App ID]** en **[!UICONTROL App Secret]** velden en plak deze in de **[!UICONTROL Application ID]** en **[!UICONTROL Application secret]** velden in de console.

   ![](assets/social_facebook_external_account_008.png)

1. Klik in Facebook op de knop **[!UICONTROL Save Changes]** onder aan de pagina.
1. Klik in de Adobe Campaign-console op de knop **[!UICONTROL Subscribe]** om Adobe Campaign in staat te stellen de gegevens in real-time te herstellen telkens wanneer een ventilator via deze toepassing incheckt.  [Meer informatie](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_fb_013.png)

## Voer de koppelingen voor service- en privacybeleid in {#entering-the-terms-of-service-and-privacy-policy-links}

We raden u aan de **[!UICONTROL Terms of service]** en **[!UICONTROL Privacy policy]** koppelingen, die worden weergegeven op het scherm voor Facebook-machtigingsaanvragen.

![](assets/social_fb_terms_of_services_001.png)

De configuratiestadia zijn als volgt:

1. Voer het volgende adres in: [https://developers.facebook.com/apps](https://developers.facebook.com/apps)selecteert u vervolgens de Facebook-toepassing.
1. Selecteer **[!UICONTROL Settings > Basic]** en voert u de **[!UICONTROL Privacy Policy URL]** en **[!UICONTROL Terms of Service URL]** velden.

   ![](assets/social_fb_terms_of_services.png)

## Een Facebook-webtoepassing maken {#creating-a-facebook-type-web-application}

Met de Adobe Campaign Facebook-toepassing kunt u persoonlijke inhoud weergeven in uw Facebook-toepassing. Voor elke Facebook-toepassing moet u een webtoepassing maken in Adobe Campaign. Ga als volgt te werk om een Facebook-webtoepassing te maken:

1. Ga naar de **[!UICONTROL Social networks]** klikt u op de knop **[!UICONTROL Applications]** dan de koppeling **[!UICONTROL Create]** knop.

   ![](assets/social_webapp_001.png)

1. Selecteer een Facebook-webtoepassingssjabloon in de lijst en voer het label in.

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >Standaard worden vier Facebook-webtoepassingssjablonen aangeboden:
   >
   >* **[!UICONTROL New Facebook application]**: Selecteer deze sjabloon als u vanuit een lege toepassing wilt starten.
   >* **[!UICONTROL Pre-entered form]**: Facebook-toepassing met een formulier en een knop voor Facebook-aanmelding waarmee gebruikers de formuliervelden automatisch kunnen invullen met behulp van de gegevens uit hun profiel. Hierdoor kunnen gebruikers het formulier sneller invullen en kunnen merken informatie van betere kwaliteit verkrijgen.
   >* **[!UICONTROL "Canvas page" competition]**: Facebook-toepassing die op het scherm wordt weergegeven voor een betere visuele ervaring voor de gebruikers.
   >* **[!UICONTROL "Page Tab" competition]**: De facebook-toepassing is volledig geïntegreerd in de tabbladen van de merkpagina.


1. In de **[!UICONTROL Application]** Voer de externe account in die is gekoppeld aan de Facebook-toepassing. [Meer informatie](#configuring-external-accounts)

   ![](assets/social_webapp_005.png)

1. Selecteer **[!UICONTROL Edit]** en bewerkt u de webtoepassing. [Meer informatie](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_003.png)

1. Als de webtoepassing is voltooid, selecteert u de optie **[!UICONTROL Dashboard]** tab, en klik vervolgens op **[!UICONTROL Publish]** om online te publiceren.

   ![](assets/social_webapp_004.png)

## Facebook-tabbladen configureren {#configuring-facebook-tabs}

U kunt uw Facebook-toepassingen configureren om als tabbladen op uw Facebook-pagina te worden weergegeven. Hiervoor voert u de volgende stappen uit:

1. Selecteer de Facebook-toepassing ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) en selecteert u de **[!UICONTROL Settings > Basic]** tab.

   ![](assets/social_webapp_fb_008.png)

1. Klik onder aan de pagina op de knop **[!UICONTROL Add Platform]** en selecteert u **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. In de **[!UICONTROL Page Tab Name]** van het **[!UICONTROL Page Tab]** voert u het label in zoals u het wilt weergeven op de Facebook-pagina.

   ![](assets/social_webapp_fb_001.png)

1. In de **[!UICONTROL Secure Page Tab URL]** in, voert u de openbare URL in van de webtoepassing die toegankelijk is via de **[!UICONTROL Dashboard]** van de webtoepassing. Raadpleeg voor meer informatie over het maken van webtoepassingen van het Facebook-type de [deze sectie](#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_fb_002.png)

1. Op de **[!UICONTROL Dashboard]** van de webtoepassing klikt u op de knop **[!UICONTROL Add a page tab]** koppeling.

   ![](assets/social_webapp_fb_0010.png)

1. Selecteer de Facebook-pagina waaraan u het tabblad wilt toevoegen en klik op **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)
