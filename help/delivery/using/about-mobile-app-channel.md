---
product: campaign
title: Aan de slag met het kanaal voor mobiele apps
description: Ga aan de slag met het kanaal voor mobiele apps in Adobe Campaign
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 2%

---

# Aan de slag met het kanaal voor mobiele apps{#about-mobile-app-channel}

Met Adobe Campaign kunt u pushberichten maken om persoonlijke berichten naar gebruikers van uw mobiele app te sturen.

Met pushberichten kunt u gebruikers op iOS en Android in real-time inschakelen. Of u updates, aankondigingen of promoties verzendt, u kunt de inhoud, timing en het richten controleren. Leer hoe te opstelling en het duw kanaal te gebruiken, het beheren van abonnementen, het integreren met APNs en FCM, en het personaliseren van berichten in [ Adobe Campaign v8 documentatie ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/emails/email){target=_blank}.

In het kader van het promotieinitiatief Campaign v8 is de documentatie van Campaign Classic gereorganiseerd. Algemene functies zijn nu alleen beschikbaar in de documentatieset van Campagne v8.

>[!BEGINTABS]

>[!TAB  documentatie van het het kanaalduim ]

Meer over het kanaal van het duw- bericht leren, verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}.

[![afbeelding](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}


>[!TAB  de verwezenlijking van de duimlevering ]

Leer de belangrijkste stappen met betrekking tot het maken van push-levering in de documentatie van Campagne v8:

* [ creeer een duw bericht ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-create){target="_blank"}: Leer over de verschillende stappen nodig om tot een duw levering te leiden.
* [ verzend en controleer het dupbericht ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-test){target="_blank"}: Leer hoe te om uw leveringen te bevestigen, te verzenden en te volgen.
* [ Ontwerp en de rijke duw levering van Android ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html){target="_blank"}: Leer om rijke dupberichten voor de apparaten van Android tot stand te brengen en te vormen.
* [ Ontwerp een rijke duw levering van iOS ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html){target="_blank"}: Leer hoe te om rijke dupberichten voor de apparaten van iOS in Adobe Campaign v8 te ontwerpen en te vormen.


>[!TAB  Push parameters ]

Raadpleeg de volgende pagina&#39;s voor meer informatie over de push-parameters in de documentatie bij Campagne v8:

* [ de eerste vereisten van de Configuratie ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#before-starting){target="_blank"}: Leer hoe te opstellingstoestemmingen en uw app vormen.
* [ vorm het lanceringsbezit ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#launch-property){target="_blank"}: Leer hoe te opstelling een mobiel markeringsbezit in de Inzameling van de Gegevens van Adobe Experience Platform om pushberichten toe te laten.
* [ vormt de duw diensten mobiele diensten ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#push-service){target="_blank"}: De de dupdiensten van de opstelling iOS en van Android in Adobe om gerichte dupberichten voor uw mobiele app gebruikers toe te laten.
* [ vorm de uitbreiding in uw mobiel bezit ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#configure-extension){target="_blank"}: Integreer de uitbreiding van de Campagne in uw mobiel bezit om dupberichten toe te laten en gebruikersinteractie effectief te beheren.

>[!ENDTABS]


De volgende informatie is specifiek voor Campaign Classic.

+++ **de installatie van het Pakket**

![](assets/do-not-localize/how-to-video.png) [ Leer hoe te om het mobiele app pakket in video te installeren ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html#sending-messages)

Als hybride/ontvangen klant, contacteer [ team van de Zorg van de Klant van 0} Adobe om tot het kanaal van het pushbericht in Campagne toegang te hebben.](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)

Als klant op locatie moet u een ingebouwd pakket installeren.

>[!CAUTION]
>
>Leer meer over de ingebouwde pakketten van de Campagne, beste praktijken en aanbevelingen in [ deze pagina ](../../installation/using/installing-campaign-standard-packages.md).

Installatiestappen zijn:

1. Open de importassistent voor pakketten vanuit **[!UICONTROL Tools > Advanced > Import package]** in de Adobe Campaign-clientconsole.

   ![](assets/package_ios.png)

1. Selecteer **[!UICONTROL Install a standard package]**.

1. Controleer **[!UICONTROL Mobile App Channel]** in de lijst die wordt weergegeven.

   ![](assets/package_ios_2.png)

1. Klik op **[!UICONTROL Next]** en vervolgens op **[!UICONTROL Start]** om de pakketinstallatie te starten.

   Zodra de pakketten worden geïnstalleerd, toont de vooruitgangsbar **100%** en u kunt het volgende bericht in de installatielogboeken zien: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** het installatievenster.

Zodra deze stap is uitgevoerd, kunt u uw Android- en iOS-toepassingen configureren. Verwijs naar de Campagne v8 [ documentatie ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target="_blank"}.

+++

+++ **Problemen oplossen**

Als uw mobiele apparaat is verbonden met Wi-Fi en u ontvangt geen meldingen, controleert u of de FCM-/APN-poorten niet worden geblokkeerd door uw firewall.

**Android**: Het mobiele apparaat verbindt met de servers FCM op havens 5228 tot 5230. Daarom moet u de firewall zo configureren dat verbinding met FCM wordt toegestaan. De open poorten zijn: 5228 (de meest gebruikte), 5229 en 5230.

**iOS**:

HTTP/2-connector: u moet communicatie toestaan van en naar de volgende servers:

* api.push.apple.com: poort 443
* api.development.push.apple.com: poort 443

>[!NOTE]
>
>Voor meer informatie over de twee schakelaars, verwijs naar de Campagne v8 [ documentatie ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html){target="_blank"}.

+++
