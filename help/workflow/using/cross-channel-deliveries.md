---
product: campaign
title: Cross-channel leveringen
description: Meer informatie over leveringen via meerdere kanalen
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 6%

---

# Cross-channel leveringen{#cross-channel-deliveries}



Kanaaloverschrijdende leveringen zijn beschikbaar op het tabblad **[!UICONTROL Deliveries]** van activiteiten in de campagnewerkstroom.

De verschillende beschikbare kanalen zijn:

* [Email](../../delivery/using/about-email-channel.md)
* [Direct mail](../../delivery/using/about-direct-mail-channel.md)
* [Mobiel](../../delivery/using/sms-channel.md)
* [X (voorheen bekend als Twitter)](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Selecteer de sjabloon waarop u de levering wilt baseren en definieer de inhoud ervan.

U kunt een doel voor uw levering vóór het werkschema specificeren gebruikend de verschillende het richten activiteiten.

In het onderstaande voorbeeld maken we een workflow voor het verzenden van een e-mail of een SMS voor gebruikers met pushberichten en een week later een pushmelding. Dit doet u als volgt:

1. Maak een campagne.
1. Voeg op het tabblad **[!UICONTROL Targeting and workflows]** van uw campagne een **[!UICONTROL Query]** toe aan uw workflow.
1. Configureer uw query. Hier selecteren we bijvoorbeeld de ontvangers die zijn geabonneerd op pushberichten als doeldimensie.

   >[!NOTE]
   >
   >Voor de duw berichten, gebruik de **doelafmeting van de 0} abonneetoepassingen.**

   ![](assets/cross_channel_delivery_1.png)

1. Voeg de filtervoorwaarden aan uw vraag toe. In dit geval selecteren we ontvangers met een mobiel nummer of e-mailadres.

   ![](assets/cross_channel_delivery_2.png)

1. Voeg een **[!UICONTROL Split]** activiteit aan uw werkschema toe om ontvangers te verdelen die een mobiel aantal en degenen hebben die een e-mailadres hebben.
1. Selecteer op het tabblad **[!UICONTROL Delivery]** een levering voor elk van uw doelen.

   Creeer uw levering op de zelfde manier zoals met een klassieke leveringsmedewerker door de leveringsactiviteit in uw werkschema tweemaal te klikken. Raadpleeg [deze pagina](../../delivery/using/about-email-channel.md) voor meer informatie.

   ![](assets/cross_channel_delivery_3.png)

1. Voeg en vorm een **[!UICONTROL Wait]** activiteit toe opdat de ontvangers niet teveel leveringen in één keer ontvangen.
1. Voeg een **[!UICONTROL Split]** -activiteit toe om abonnees van mobiele iOS- of Android-toepassingen te verdelen.

   Selecteer een service voor elk besturingssysteem. Voor meer op de dienstverwezenlijking, verwijs naar deze [ pagina ](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Selecteer en configureer een levering van een mobiele toepassing voor elk besturingssysteem.

   ![](assets/cross_channel_delivery_5.png)
