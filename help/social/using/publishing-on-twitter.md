---
product: campaign
title: Publiceren op Twitter
description: Publiceren op Twitter
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: e030c029-d1ee-4749-94e3-6bdfc8d89a34
source-git-commit: d11c918213e72fe4bf6adb464e516fac19b63d54
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 6%

---

# Publiceren op Twitter{#publishing-on-twitter}

![](../../assets/v7-only.svg)

## Publiceren op je Twitter-accounts {#publishing-on-your-twitter-accounts}

Als de configuratie is voltooid, kunt u met Social Marketing tweets verzenden naar uw Twitter-accounts.

### Beperkingen {#limitations}

De volgende beperkingen zijn beperkingen die inherent zijn aan Twitter.

* Het bericht mag niet langer zijn dan 140 tekens.
* HTML-indeling wordt niet ondersteund.

### De levering maken {#creating-the-delivery}

Maak een nieuwe levering op basis van de **[!UICONTROL Tweet (twitter)]** leveringssjabloon.

![](assets/social_twitter_delivery_001.png)

### Selecteer het hoofddoel {#selecting-the-main-target}

Selecteer de account(s) waarnaar u tweets wilt verzenden.

1. Klik op de koppeling **[!UICONTROL To]**.

   ![](assets/social_twitter_delivery_002.png)

1. Klik op de knop **[!UICONTROL Add]**.

   ![](assets/social_twitter_delivery_006.png)

1. Selecteer **[!UICONTROL A Twitter account]**.

   ![](assets/social_twitter_delivery_007.png)

1. In de **[!UICONTROL Folder]** , selecteert u de servicemap die de Twitter-account bevat. Selecteer vervolgens de Twitter-account waarnaar u uw tweet wilt verzenden.

   ![](assets/social_twitter_delivery_011.png)

### Doel van proefdruk selecteren {#selecting-the-target-of-the-proof}

De **[!UICONTROL Target of the proofs]** kunt u de Twitter-account definiëren die u voor testleveringen wilt gebruiken voordat de levering is voltooid. Daarom raden we u aan een persoonlijke Twitter-account te maken die gewijd is aan het verzenden van proefdrukken. Voor meer informatie over het maken van een particuliere Twitter-account raadpleegt u [deze sectie](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). De stappen voor het selecteren van het proefdrukdoel zijn hetzelfde als voor het selecteren van het hoofddoel. Zie [deze sectie](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter).

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>Als u voor al uw leveringen dezelfde Twitter-testaccount gebruikt, kunt u het proefdrukdoel opslaan in het dialoogvenster **[!UICONTROL Tweet]** leveringssjabloon, toegankelijk via **[!UICONTROL Resources > Templates > Delivery templates]** knooppunt. Het proefdrukdoel wordt dan standaard ingevoerd voor elke nieuwe levering.

### De inhoud van het bericht definiëren {#defining-the-message-content}

Typ de inhoud van uw tweet in het dialoogvenster **[!UICONTROL Content]** tab.

![](assets/social_twitter_delivery_005.png)

### Een voorvertoning van het bericht weergeven {#viewing-the-preview}

De **[!UICONTROL Preview]** kunt u een rendering van de tweet weergeven.

1. Klik op de knop **[!UICONTROL Preview]** tab.
1. Klik op de knop **[!UICONTROL Test personalization]** vervolgkeuzelijst en selecteert u **[!UICONTROL Service]**.
1. In de **[!UICONTROL Folder]** , selecteert u de servicemap die uw Twitter-account bevat.
1. Kies de Twitter-account waarmee u de voorvertoning wilt testen.

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>De voorvertoning kan iets afwijken van de uiteindelijke tweet. We raden u aan een proefdruk vóór de uiteindelijke aflevering te verzenden om een exacte weergave van de tweet te bekijken. Zie [deze sectie](#sending-the-proof).

### Tracking configureren {#configuring-tracking}

Het volgen kan in de leveringsrapporten en in worden bekeken **[!UICONTROL Edit > Tracking]** tabblad van de levering en de service.

De volgende configuratie is het zelfde als voor een e-maillevering. Raadpleeg [deze sectie](../../delivery/using/about-delivery-monitoring.md) voor meer informatie.

>[!NOTE]
>
>In de **[!UICONTROL Tweet]** leveringssjabloon; reeksspatiëring is standaard ingeschakeld.

>[!CAUTION]
>
>We kunnen het verschil niet zien tussen robots die tweets analyseren en gebruikers die klikken.

### De proefdruk verzenden {#sending-the-proof}

We raden u aan een bewijs van uw publicatie vóór de uiteindelijke levering te verzenden om een exacte weergave van de publicatie op een persoonlijke Twitter-testpagina te verkrijgen. Voor meer informatie over het maken van een particuliere Twitter-account raadpleegt u [deze sectie](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). De stappen voor het selecteren van het proefdrukdoel worden nader beschreven in [deze sectie](#selecting-the-target-of-the-proof).

Bewijs van levering is identiek aan e-mailleveringen. Zie [deze sectie](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Bericht verzenden {#sending-the-message}

1. Als de inhoud is goedgekeurd, klikt u op de knop **[!UICONTROL Send]** knop.
1. Selecteren **[!UICONTROL Deliver as soon as possible]** en klik op de knop **[!UICONTROL Analyze]** knop.

   >[!NOTE]
   >
   >De **[!UICONTROL Postpone the delivery]** kunt u de levering uitstellen tot een latere datum.

   ![](assets/social_twitter_delivery_012.png)

1. Controleer het resultaat als de analyse is voltooid.
1. Klikken **[!UICONTROL Confirm delivery]** en klik vervolgens op **[!UICONTROL Yes]**.

![](assets/social_facebook_delivery_016.png)

## Directe berichten naar abonnees verzenden {#sending-direct-messages-to-subscribers}

### Werkwijze {#operating-principle}

De **[!UICONTROL Synchronize Twitter accounts]** workflow (zie [Meer informatie](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts)) herstelt de lijst met Twitter-abonnees zodat u deze directe berichten kunt sturen. De herstelde volgers worden opgeslagen in een specifieke tabel: de bezoekerslijst. Als u de lijst met Twitter-volgers wilt weergeven, gaat u naar de **[!UICONTROL Profiles and Targets > Visitors]** knooppunt.

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>Als u wilt dat de workflow de lijst met Twitter-volgers herstelt, kunt u de **[!UICONTROL Synchronize Twitter accounts]** moet zijn ingeschakeld in het scherm Bewerken van de service die aan de account is gekoppeld. Raadpleeg voor meer informatie: [Schrijftoegang delegeren aan Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign).

Adobe Campaign herstelt voor elk van de volgende gegevens:

* **[!UICONTROL Origin]**: naam van het sociale netwerk (**Twitter** in dit geval)
* **[!UICONTROL External ID]**: gebruikersnaam
* **[!UICONTROL User name]**: accountnaam van de gebruiker
* **[!UICONTROL Full name]**: naam van de gebruiker
* **[!UICONTROL Language]**: gebruikerstaal
* **[!UICONTROL Number of friends]**: aantal volgers
* **[!UICONTROL Time zone]**: tijdzone van gebruiker
* **[!UICONTROL Verified]**: in dit veld wordt aangegeven of de gebruiker een geverifieerde Twitter-account heeft

### Beperkingen {#limitations-1}

De volgende beperkingen zijn beperkingen die inherent zijn aan Twitter.

* Het bericht mag niet langer zijn dan 140 tekens.
* HTML wordt niet ondersteund.
* U kunt niet meer dan 250 directe berichten per dag verzenden. Als u wilt voorkomen dat deze drempelwaarde wordt overschreden, kunt u in verschillende golven leveren. Leveringen in golven worden geconfigureerd als e-mailleveringen. Raadpleeg [deze sectie](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) voor meer informatie.

### De levering maken {#creating-the-delivery-}

Maak een nieuwe levering op basis van de **[!UICONTROL Tweet (Direct Message)]** leveringssjabloon.

![](assets/social_twitter_delivery_010.png)

### Selecteer het hoofddoel {#selecting-the-main-target-1}

Selecteer de volgers aan wie u uw directe bericht wilt verzenden.

1. Klik op de koppeling **[!UICONTROL To]**.

   ![](assets/social_twitter_delivery_016.png)

1. Klik op de knop **[!UICONTROL Add]**.

   ![](assets/social_twitter_delivery_006.png)

1. Selecteer een type doelverwijzing.

   ![](assets/social_twitter_delivery_017.png)

   * Selecteren **[!UICONTROL Twitter subscribers]** om een rechtstreeks bericht naar alle rekeninghouders te sturen.

      >[!IMPORTANT]
      >
      >U kunt niet meer dan 250 berichten per dag verzenden. Als uw Twitter-account meer dan 250 volgers heeft, raden we u ten zeerste aan om uw account in golven aan te bieden. Dit omvat hetzelfde proces als e-mailleveringen. Zie [deze sectie](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

   * Selecteren **[!UICONTROL Filter conditions]** om een vraag te bepalen en zijn resultaat te bekijken. Deze optie is hetzelfde als voor e-mailleveringen. Zie [deze sectie](../../platform/using/defining-filter-conditions.md) voor meer informatie .

      ![](assets/social_twitter_delivery_018.png)

### Doel van proefdruk selecteren {#selecting-the-target-of-the-proof-1}

De **[!UICONTROL Target of the proofs]** kunt u de volgende persoon selecteren die de proefdruk van uw directe bericht ontvangt. Het selectieproces is hetzelfde als voor het hoofddoel. Zie [Het hoofddoel selecteren](#selecting-the-main-target).

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>Als u al uw directe-berichtproefdrukken naar dezelfde Twitter-volger wilt verzenden, kunt u het proefdrukdoel opslaan in het dialoogvenster **[!UICONTROL Tweet (Direct Message)]** leveringssjabloon, toegankelijk via **[!UICONTROL Resources > Templates > Delivery templates]** knooppunt. Het proefdrukdoel wordt dan standaard ingevoerd voor elke nieuwe levering.

### Berichtinhoud definiëren {#defining-message-content-}

Voer de inhoud van de tweet in het dialoogvenster **[!UICONTROL Content]** tab.

![](assets/social_twitter_delivery_015.png)

Velden voor persoonlijke voorkeur kunnen op dezelfde manier worden gebruikt als voor e-mailleveringen, bijvoorbeeld om de naam van de volgende persoon toe te voegen aan de hoofdtekst van het bericht. De inhoudpersonalisatie wordt gedetailleerd in [deze sectie](../../delivery/using/about-personalization.md).

![](assets/social_twitter_delivery_021.png)

De volgende stappen zijn hetzelfde als voor het verzenden van een tweet naar een Twitter-account. Zie [Publiceren op je Twitter-accounts](#publishing-on-your-twitter-accounts).
