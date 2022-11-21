---
product: campaign
title: Cross-channel leveringen
description: Meer informatie over leveringen via meerdere kanalen
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: 31a475c98b09bbeca6a16c6fd98698af10016033
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 8%

---

# Cross-channel leveringen{#cross-channel-deliveries}

![](../../assets/v7-only.svg)

Kanaaloverschrijdende leveringen zijn beschikbaar in het dialoogvenster **[!UICONTROL Deliveries]** tabblad van activiteiten in verband met de campagneworkflow.

De verschillende beschikbare kanalen zijn:

* [Email](../../delivery/using/about-email-channel.md)
* [Direct mail](../../delivery/using/about-direct-mail-channel.md)
* [Mobiel](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Selecteer de sjabloon waarop u de levering wilt baseren en definieer de inhoud ervan.

U kunt een doel voor uw levering vóór het werkschema specificeren gebruikend de verschillende het richten activiteiten.

In het onderstaande voorbeeld maken we een workflow voor het verzenden van een e-mail of een SMS voor gebruikers met pushberichten en een week later een pushmelding. Dit doet u als volgt:

1. Een campagne maken.
1. In de **[!UICONTROL Targeting and workflows]** tabblad van uw campagne, voegt u een **[!UICONTROL Query]** naar uw workflow.
1. Configureer uw query. Hier selecteren we bijvoorbeeld de ontvangers die zijn geabonneerd op pushberichten als doeldimensie.

   >[!NOTE]
   >
   >Voor de pushberichten gebruikt u de **abonneetoepassingen** doeldimensie.

   ![](assets/cross_channel_delivery_1.png)

1. Voeg de filtervoorwaarden aan uw vraag toe. In dit geval selecteren we ontvangers met een mobiel nummer of e-mailadres.

   ![](assets/cross_channel_delivery_2.png)

1. Voeg een **[!UICONTROL Split]** activiteit aan uw werkschema om ontvangers te verdelen die een mobiel aantal en degenen hebben die een e-mailadres hebben.
1. In de **[!UICONTROL Delivery]** selecteert u een levering voor elk van uw doelen.

   U kunt uw levering op dezelfde manier maken als met een klassieke wizard voor levering door te dubbelklikken op de leveringsactiviteit in uw workflow. Raadpleeg [deze pagina](../../delivery/using/about-email-channel.md) voor meer informatie.

   ![](assets/cross_channel_delivery_3.png)

1. Een **[!UICONTROL Wait]** om ervoor te zorgen dat de ontvangers niet te veel leveringen tegelijk ontvangen.
1. Voeg een **[!UICONTROL Split]** activiteit om abonnees van mobiele iOS- of Android-toepassingen te verdelen.

   Selecteer een service voor elk besturingssysteem. Raadpleeg voor meer informatie over het maken van services deze [page](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Selecteer en configureer een levering van een mobiele toepassing voor elk besturingssysteem.

   ![](assets/cross_channel_delivery_5.png)
