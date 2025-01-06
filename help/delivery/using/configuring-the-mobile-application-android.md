---
product: campaign
title: De mobiele Android-toepassing in Adobe Campaign configureren
description: Meer informatie over het instellen van uw mobiele toepassing voor Android
feature: Push
role: User, Developer
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 9%

---

# Configuratiestappen voor Android

Nadat het pakket is geïnstalleerd, kunt u de Android-toepassingsinstellingen in Adobe Campaign Classic definiëren.

De belangrijkste stappen zijn:

1. [De externe Android-account configureren](#configuring-external-account-android)
1. [De Android-service configureren](#configuring-android-service)
1. [De mobiele app maken in Campagne](#creating-android-app)
1. [Het app-schema uitbreiden met aanvullende gegevens](#extend-subscription-schema)

U zult dan een rijk bericht van Android ](create-notifications-android.md) kunnen tot stand brengen. [

>[!IMPORTANT]
>
>In 2024 komt er een versie met enkele belangrijke wijzigingen voor de service FCM (Android Firebase Cloud Messaging). Deze kunnen van invloed zijn op uw Adobe Campaign-implementatie. De configuratie van uw lidmaatschapsservices voor Android-pushberichten moet mogelijk worden bijgewerkt om deze wijziging te ondersteunen. U kunt al controleren en actie ondernemen. Leer meer in dit [ Adobe Campaign v8 technote ](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=nl) {target="_blank"}.


## Externe Android-account configureren {#configuring-external-account-android}

Voor Android zijn twee connectors beschikbaar:

* De V1 schakelaar die één verbinding per kind MTA toestaat.
* De V2-connector die gelijktijdige verbindingen met de FCM-server mogelijk maakt om de doorvoer te verbeteren.

Voer de volgende stappen uit om te kiezen welke aansluiting u wilt gebruiken:

1. Ga naar **[!UICONTROL Administration > Platform > External accounts]** .
1. Selecteer de **[!UICONTROL Android routing]** externe account.
1. Vul op het tabblad **[!UICONTROL Connector]** het veld **[!UICONTROL JavaScript used in the connector]** in:

   Voor Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > U kunt het ook configureren als volgt: https://localhost:8080/nms/jsp/androidPushConnector.js, maar u wordt aangeraden versie 2 van de connector te gebruiken.

   ![](assets/nmac_connectors3.png)

1. Voor Android V2 is er één extra parameter beschikbaar in het configuratiebestand van de Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Maximale grens van parallelle HTTP- verzoeken aan FCM die door elke kindserver (8 door gebrek in werking wordt gesteld).

## Een Android-service configureren {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [ Leer hoe te om de dienst van Android in video ](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign) te vormen {target="_blank"}.

1. Ga naar het knooppunt **[!UICONTROL Profiles and Targets > Services and subscriptions]** en klik op **[!UICONTROL New]** .

   ![](assets/nmac_service_1.png)

1. Definieer een **[!UICONTROL Label]** en een **[!UICONTROL Internal name]** .
1. Ga naar het veld **[!UICONTROL Type]** en selecteer **[!UICONTROL Mobile application]** .

   >[!NOTE]
   >
   >De standaarddoeltoewijzing **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** is gekoppeld aan de tabel met ontvangers. Als u een andere doelafbeelding wilt gebruiken, moet u een nieuwe doeltoewijzing maken en deze invoeren in het veld **[!UICONTROL Target mapping]** van de service. Voor meer bij het creëren van doelafbeelding, verwijs naar [ deze sectie ](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klik vervolgens op de knop **[!UICONTROL Add]** om het toepassingstype te selecteren.

   ![](assets/nmac_service_2.png)

1. Maak uw Android-toepassing. Raadpleeg [deze sectie](configuring-the-mobile-application-android.md#creating-android-app) voor meer informatie.

## De mobiele Android-toepassing maken {#creating-android-app}

Nadat u uw service hebt gemaakt, moet u nu uw Android-toepassing maken:

1. Klik vanuit de nieuwe service op de knop **[!UICONTROL Add]** om het toepassingstype te selecteren.

   ![](assets/nmac_service_2.png)

1. Selecteer **[!UICONTROL Create an Android application]** en voer een **[!UICONTROL Label]** in.

   ![](assets/nmac_android.png)

1. Zorg ervoor dat **[!UICONTROL Integration key]** ook in Adobe Campaign en in de toepassingscode via de SDK is gedefinieerd. <!--For more on this, refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** is volledig aanpasbaar met tekenreekswaarde, maar moet precies hetzelfde zijn als de waarde die in de SDK is opgegeven.

1. Selecteer **[!UICONTROL API version]**: HTTP v1 of HTTP (verouderd). Deze configuraties zijn gedetailleerd in [ deze sectie ](#select-api-version)

1. Vul de velden **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** in.

1. Klik op **[!UICONTROL Finish]** en vervolgens op **[!UICONTROL Save]** . Uw Android-toepassing kan nu in Campaign Classic worden gebruikt.

Standaard slaat Adobe Campaign een toets op in het veld **[!UICONTROL User identifier]** (@userKey) van de tabel **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** . Met deze sleutel kunt u een abonnement koppelen aan een ontvanger. Als u aanvullende gegevens wilt verzamelen (zoals een complexe afstemmingssleutel), moet u de volgende configuratie toepassen:

### De API-versie configureren{#select-api-version}

>[!IMPORTANT]
>
>In 2024 komt er een versie met enkele belangrijke wijzigingen voor de service FCM (Android Firebase Cloud Messaging). Deze kunnen van invloed zijn op uw Adobe Campaign-implementatie. Als deel van Google dat voortdurend probeert om zijn diensten te verbeteren, zal erfenis FCM APIs op **juni 20, 2024** worden opgeheven. Leer meer in dit [ Adobe Campaign v8 technote ](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=nl) {target="_blank"}.

Nadat u de service en een nieuwe mobiele toepassing hebt gemaakt, moet u uw mobiele toepassing configureren. **HTTP (erfenis)** API zou niet moeten worden geselecteerd aangezien het door Google is verouderd.

Voer de volgende stappen uit om de HTTP v1 API-versie te configureren:

1. Selecteer in het **[!UICONTROL Mobile application creation wizard]** -venster **[!UICONTROL HTTPV1]** in de vervolgkeuzelijst **[!UICONTROL API version]** .

1. Klik op **[!UICONTROL Load project json file to extract project details...]** om het JSON-sleutelbestand rechtstreeks te laden. Voor meer informatie over hoe te om uw JSON- dossier te halen, verwijs naar [ deze pagina ](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   U kunt ook handmatig de volgende gegevens invoeren:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Klik op **[!UICONTROL Test the connection]** om te controleren of uw configuratie correct is en of de marketingserver toegang heeft tot de FCM.

   >[!CAUTION]
   >
   >Voor Mid-sourcing-implementatie controleert de knop **[!UICONTROL Test connection]** niet of de MID-server toegang heeft tot de FCM-server.

   ![](assets/nmac_android_11.png)

1. U kunt desgewenst ook de inhoud van een pushbericht verrijken met wat **[!UICONTROL Application variables]** . Deze zijn volledig aanpasbaar en een deel van de berichtlading wordt verzonden naar het mobiele apparaat.

1. Klik op **[!UICONTROL Finish]** en vervolgens op **[!UICONTROL Save]** . Uw Android-toepassing kan nu in Campaign Classic worden gebruikt.

Hieronder vindt u de namen van FCM-ladingen om uw pushmelding verder aan te passen:

| Berichttype | Configureerbaar berichtelement (FCM-ladenaam) | Configureerbare opties (FCM-ladenaam) |
|:-:|:-:|:-:|
| gegevensbericht | N.v.t. | validate_only |
| meldingsbericht | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

## Het schema appsubscriptionRcp uitbreiden {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [ Leer hoe te om het schema appsubscriptionRcp in video uit te breiden ](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html#extending-the-app-subscription-schema-to-personalize-push-notifications)

U moet **appsubscriptionRcp** uitbreiden om nieuwe extra gebieden te bepalen om parameters van app in het gegevensbestand van de Campagne op te slaan. Deze velden worden bijvoorbeeld gebruikt voor personalisatie. Dit doet u als volgt:

1. Maak een extensie van het schema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** en definieer de nieuwe velden. Leer meer over schemauitbreiding in [ deze pagina ](../../configuration/using/about-schema-edition.md)

1. Definieer de toewijzing op het tabblad **[!UICONTROL Subscription parameters]** .

   >[!CAUTION]
   >
   >Zorg ervoor dat de configuratienamen op het tabblad **[!UICONTROL Subscription parameters]** gelijk zijn aan die in de code van de mobiele toepassing. <!--Refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->
