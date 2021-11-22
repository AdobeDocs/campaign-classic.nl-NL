---
product: campaign
title: Cross-channel leveringen
description: Meer informatie over leveringen via meerdere kanalen
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 8%

---

# Cross-channel leveringen{#cross-channel-deliveries}

![](../../assets/common.svg)

Kanaaloverschrijdende leveringen zijn beschikbaar in het dialoogvenster **[!UICONTROL Deliveries]** tabblad van activiteiten in verband met de campagneworkflow.

De verschillende beschikbare kanalen zijn:

* [Email](../../delivery/using/about-email-channel.md)
* [Direct mail](../../delivery/using/about-direct-mail-channel.md)
* [Mobiel](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md) (alleen Campaign Classic v7)
* [Facebook](../../social/using/publishing-on-facebook.md) (alleen Campaign Classic v7)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Selecteer de sjabloon waarop u de levering wilt baseren en definieer de inhoud ervan.

U kunt een doel voor uw levering vóór het werkschema specificeren gebruikend de verschillende het richten activiteiten.

In het onderstaande voorbeeld maken we een workflow voor het verzenden van een e-mail of een SMS voor gebruikers met pushberichten en een week later een pushmelding. Dit doet u als volgt:

1. Een campagne maken.
1. In de **[!UICONTROL Targeting and workflows]** tabblad van uw campagne, voegt u een **[!UICONTROL Query]** naar uw workflow.
1. Configure your query. Hier selecteren we bijvoorbeeld de ontvangers die zijn geabonneerd op pushberichten als doeldimensie.

   >[!NOTE]
   >
   >Voor de pushberichten gebruikt u de **abonneetoepassingen** doeldimensie.

   ![](assets/cross_channel_delivery_1.png)

1. Add the filter conditions to your query. In this case, we will select recipients who have a mobile number or email address.

   ![](assets/cross_channel_delivery_2.png)

1. Voeg een **[!UICONTROL Split]** activiteit aan uw werkschema om ontvangers te verdelen die een mobiel aantal en degenen hebben die een e-mailadres hebben.
1. In the **[!UICONTROL Delivery]** tab, select a delivery for each of your targets.

   U kunt uw levering op dezelfde manier maken als met een klassieke wizard voor levering door te dubbelklikken op de leveringsactiviteit in uw workflow. Raadpleeg [deze pagina](../../delivery/using/about-email-channel.md) voor meer informatie.

   ![](assets/cross_channel_delivery_3.png)

1. Add and configure a **[!UICONTROL Wait]** activity in order for the recipients not to receive too many deliveries at once.
1. Add a **[!UICONTROL Split]** activity to divide subscribers of an iOS or Android mobile applications.

   Select a service for each of the operating systems. Raadpleeg voor meer informatie over het maken van services deze [page](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Selecteer en configureer een levering van een mobiele toepassing voor elk besturingssysteem.

   ![](assets/cross_channel_delivery_5.png)
