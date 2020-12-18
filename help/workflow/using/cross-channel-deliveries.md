---
solution: Campaign Classic
product: campaign
title: Leveringen tussen kanalen
description: Meer informatie over leveringen via meerdere kanalen
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 7%

---


# Leveringen tussen kanalen{#cross-channel-deliveries}

Kanaaloverschrijdende leveringen zijn beschikbaar op het tabblad **[!UICONTROL Deliveries]** van workflowactiviteiten voor campagnes.

Hiermee kunt u een levering maken die specifiek is voor een bepaald kanaal. U kunt het malplaatje specificeren waarop u uw levering evenals zijn inhoud wilt baseren, op de zelfde manier zoals met een klassieke leveringstovenaar.

De verschillende beschikbare kanalen zijn:

* [E-mail](../../delivery/using/about-email-channel.md)
* [Direct mail](../../delivery/using/about-direct-mail-channel.md)
* [Mobiel](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md)
* [Facebook](../../social/using/publishing-on-facebook.md)
* [iOS](../../delivery/using/creating-notifications.md#sending-notifications-on-ios)
* [Android](../../delivery/using/creating-notifications.md#sending-notifications-on-android)

U kunt een doel voor uw levering vóór het werkschema specificeren gebruikend de verschillende het richten activiteiten.

Hier maken we bijvoorbeeld een workflow voor het verzenden van een e-mail of een SMS voor gebruikers met pushberichten en een week later een pushmelding. Dit doet u als volgt:

1. Een campagne maken.
1. Voeg op het tabblad **[!UICONTROL Targeting and workflows]** van uw campagne een **[!UICONTROL Query]** toe aan uw workflow.
1. Configureer uw query. Hier selecteren we bijvoorbeeld de ontvangers die zijn geabonneerd op pushberichten als doeldimensie.

   >[!NOTE]
   >
   >Voor de dupberichten, herinner eraan om **abonneetoepassingen** doelafmeting te gebruiken.

   ![](assets/cross_channel_delivery_1.png)

1. Voeg de filtervoorwaarden aan uw vraag toe. In dit geval selecteren we ontvangers met een mobiel nummer of e-mailadres.

   ![](assets/cross_channel_delivery_2.png)

1. Voeg een **[!UICONTROL Split]** activiteit aan uw werkschema toe om ontvangers te verdelen die een mobiel aantal en zij hebben die een e-mailadres hebben.
1. Selecteer op het tabblad **[!UICONTROL Delivery]** een levering voor elk van uw doelen.

   U kunt uw levering op dezelfde manier maken als met een klassieke wizard voor levering door te dubbelklikken op de leveringsactiviteit in uw workflow. Raadpleeg [deze pagina](../../delivery/using/about-email-channel.md) voor meer informatie.

   ![](assets/cross_channel_delivery_3.png)

1. Voeg en vorm een **[!UICONTROL Wait]** activiteit toe opdat de ontvangers niet teveel leveringen in één keer ontvangen.
1. Voeg een **[!UICONTROL Split]** activiteit toe om abonnees van een mobiele iOS of Android toepassingen te verdelen.

   Selecteer een service voor elk besturingssysteem. Raadpleeg deze [pagina](../../delivery/using/configuring-the-mobile-application.md) voor meer informatie over het maken van services.

   ![](assets/cross_channel_delivery_4.png)

1. Selecteer en configureer een levering van een mobiele toepassing voor elk besturingssysteem.

   ![](assets/cross_channel_delivery_5.png)
