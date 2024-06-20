---
product: campaign
title: De mobiele Android-toepassing configureren in Adobe Campaign
description: Leer hoe u uw mobiele toepassing instelt voor Android
feature: Push
role: User, Developer
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 81b47231b027a189bc8b9029b7d48939734d08ed
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 9%

---

# Configuratiestappen voor Android

Nadat het pakket is geïnstalleerd, kunt u de instellingen voor uw Android-app definiëren in Adobe Campaign Classic.

De belangrijkste stappen zijn:

1. [De externe Android-account configureren](#configuring-external-account-android)
1. [De Android-service configureren](#configuring-android-service)
1. [De mobiele app maken in Campagne](#creating-android-app)
1. [Het app-schema uitbreiden met aanvullende gegevens](#extend-subscription-schema)

Dan kunt u [een Android-rijk bericht maken](create-notifications-android.md).

>[!IMPORTANT]
>
>In 2024 komt er een versie met enkele belangrijke wijzigingen voor de service FCM (Android Firebase Cloud Messaging). Deze kunnen van invloed zijn op uw Adobe Campaign-implementatie. De configuratie van uw lidmaatschapsservices voor Android-pushberichten moet mogelijk worden bijgewerkt om deze wijziging te ondersteunen. U kunt al controleren en actie ondernemen. Meer informatie in deze [Adobe Campaign v8-technologie](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=nl){target="_blank"}.


## Externe Android-account configureren {#configuring-external-account-android}

Voor Android zijn twee connectors beschikbaar:

* De V1 schakelaar die één verbinding per kind MTA toestaat.
* De V2-connector die gelijktijdige verbindingen met de FCM-server mogelijk maakt om de doorvoer te verbeteren.

Voer de volgende stappen uit om te kiezen welke aansluiting u wilt gebruiken:

1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecteer de **[!UICONTROL Android routing]** externe rekening.
1. In de **[!UICONTROL Connector]** tabblad, vult de **[!UICONTROL JavaScript used in the connector]** veld:

   Voor Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > U kunt het ook configureren als volgt: https://localhost:8080/nms/jsp/androidPushConnector.js, maar u wordt aangeraden versie 2 van de connector te gebruiken.

   ![](assets/nmac_connectors3.png)

1. Voor Android V2 is er één extra parameter beschikbaar in het configuratiebestand van de Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Maximale limiet van parallelle HTTP-aanvragen voor de FCM die door elke onderliggende server worden gestart (standaard 8).

## Een Android-service configureren {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Leer hoe u een Android-service configureert in video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign){target="_blank"}.

1. Ga naar de **[!UICONTROL Profiles and Targets > Services and subscriptions]** knoop en klik **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Een **[!UICONTROL Label]** en **[!UICONTROL Internal name]**.
1. Ga naar de **[!UICONTROL Type]** veld en selecteer **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >De standaardwaarde **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** doeltoewijzing is gekoppeld aan de tabel met ontvangers. Als u een andere doelafbeelding wilt gebruiken, moet u een nieuwe doeltoewijzing maken en deze invoeren in het dialoogvenster **[!UICONTROL Target mapping]** van de dienst. Raadpleeg voor meer informatie over het maken van doeltoewijzingen de [deze sectie](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klik vervolgens op de knop **[!UICONTROL Add]** Selecteer het toepassingstype.

   ![](assets/nmac_service_2.png)

1. Maak uw Android-toepassing. Raadpleeg [deze sectie](configuring-the-mobile-application-android.md#creating-android-app) voor meer informatie.

## De mobiele Android-toepassing maken {#creating-android-app}

Nadat u de service hebt gemaakt, moet u nu uw Android-toepassing maken:

1. Klik op de knop **[!UICONTROL Add]** Selecteer het toepassingstype.

   ![](assets/nmac_service_2.png)

1. Selecteren **[!UICONTROL Create an Android application]** en voert u een **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Zorg ervoor dat **[!UICONTROL Integration key]** wordt gedefinieerd in Adobe Campaign en in de toepassingscode via de SDK. <!--For more on this, refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->

   >[!NOTE]
   >
   > De **[!UICONTROL Integration key]** is volledig aanpasbaar met tekenreekswaarde, maar moet exact hetzelfde zijn als de waarde die in de SDK is opgegeven.

1. Selecteer de **[!UICONTROL API version]**: HTTP v1 of HTTP (legacy). Deze configuraties worden beschreven in [deze sectie](#select-api-version)

1. Vul de **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** velden.

1. Klikken **[!UICONTROL Finish]** dan **[!UICONTROL Save]**. Uw Android-toepassing kan nu worden gebruikt in het Campaign Classic.

Standaard slaat Adobe Campaign een toets op in het dialoogvenster **[!UICONTROL User identifier]** (@userKey) in het veld **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** tabel. Met deze sleutel kunt u een abonnement koppelen aan een ontvanger. Als u aanvullende gegevens wilt verzamelen (zoals een complexe afstemmingssleutel), moet u de volgende configuratie toepassen:

### De API-versie configureren{#select-api-version}

>[!IMPORTANT]
>
>In 2024 komt er een versie met enkele belangrijke wijzigingen voor de service FCM (Android Firebase Cloud Messaging). Deze kunnen van invloed zijn op uw Adobe Campaign-implementatie. Als onderdeel van de voortdurende inspanningen van Google om haar diensten te verbeteren, zullen de bestaande FCM API&#39;s worden stopgezet op **20 juni 2024**. Meer informatie in deze [Adobe Campaign v8-technologie](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=nl){target="_blank"}.

Nadat u de service en een nieuwe mobiele toepassing hebt gemaakt, moet u uw mobiele toepassing configureren. De **HTTP (verouderd)** API mag niet worden geselecteerd omdat deze is vervangen door Google.

Voer de volgende stappen uit om de HTTP v1 API-versie te configureren:

1. In uw **[!UICONTROL Mobile application creation wizard]** venster, selecteert u **[!UICONTROL HTTPV1]** in de **[!UICONTROL API version]** vervolgkeuzelijst.

1. Klikken **[!UICONTROL Load project json file to extract project details...]** om uw JSON-sleutelbestand rechtstreeks te laden. Voor meer informatie over het uitpakken van uw JSON-bestand raadpleegt u [deze pagina](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   U kunt ook handmatig de volgende gegevens invoeren:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Klikken **[!UICONTROL Test the connection]** om te controleren of uw configuratie correct is en of de marketingserver toegang heeft tot de FCM.

   >[!CAUTION]
   >
   >Voor de implementatie van middelmatige bronnen **[!UICONTROL Test connection]** niet controleert of de MID-server toegang heeft tot de FCM-server.

   ![](assets/nmac_android_11.png)

1. Als optie kunt u de inhoud van een pushbericht verrijken met wat **[!UICONTROL Application variables]** indien nodig. Deze zijn volledig aanpasbaar en een deel van de berichtlading wordt verzonden naar het mobiele apparaat.

1. Klikken **[!UICONTROL Finish]** dan **[!UICONTROL Save]**. Uw Android-toepassing kan nu worden gebruikt in het Campaign Classic.

Hieronder vindt u de namen van FCM-ladingen om uw pushmelding verder aan te passen:

| Berichttype | Configureerbaar berichtelement (FCM-ladenaam) | Configureerbare opties (FCM-ladenaam) |
|:-:|:-:|:-:|
| gegevensbericht | N.v.t. | validate_only |
| meldingsbericht | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

## Het schema appsubscriptionRcp uitbreiden {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Leer hoe u het schema appsubscriptionRcp in video kunt uitbreiden](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html#extending-the-app-subscription-schema-to-personalize-push-notifications)

U moet het dialoogvenster **appsubscriptionRcp** om nieuwe extra gebieden te bepalen om parameters van app in het gegevensbestand van de Campagne op te slaan. Deze velden worden bijvoorbeeld gebruikt voor personalisatie. Dit doet u als volgt:

1. Een extensie maken van de **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** en definieert u de nieuwe velden. Meer informatie over schema-extensies vindt u in [deze pagina](../../configuration/using/about-schema-edition.md)

1. De toewijzing definiëren in het dialoogvenster **[!UICONTROL Subscription parameters]** tab.

   >[!CAUTION]
   >
   >Zorg ervoor dat de configuratienamen in het dialoogvenster **[!UICONTROL Subscription parameters]** zijn dezelfde als die in de code van de mobiele toepassing. <!--Refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->
