---
solution: Campaign Classic
product: campaign
title: Publiceren op Twitter
description: Publiceren op Twitter
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 5%

---


# Publiceren op Twitter{#publishing-on-twitter}

## {#publishing-on-your-twitter-accounts} publiceren op uw Twitter-accounts

Zodra de configuratie is voltooid, kunt u met Social Marketing tweets verzenden naar uw Twitter-accounts.

### Beperkingen {#limitations}

De volgende beperkingen zijn inherent aan Twitter.

* Het bericht mag niet langer zijn dan 140 tekens.
* HTML-indeling wordt niet ondersteund.

### De levering maken {#creating-the-delivery}

Creeer een nieuwe levering die op **[!UICONTROL Tweet (twitter)]** leveringsmalplaatje wordt gebaseerd.

![](assets/social_twitter_delivery_001.png)

### Het hoofddoel selecteren {#selecting-the-main-target}

Selecteer de account(s) waarnaar u tweets wilt verzenden.

1. Klik op de koppeling **[!UICONTROL To]**.

   ![](assets/social_twitter_delivery_002.png)

1. Klik op de knop **[!UICONTROL Add]**.

   ![](assets/social_twitter_delivery_006.png)

1. Selecteer **[!UICONTROL A Twitter account]**.

   ![](assets/social_twitter_delivery_007.png)

1. Selecteer in het veld **[!UICONTROL Folder]** de servicemap die de Twitter-account bevat. Selecteer vervolgens het Twitter-account waarnaar u uw tweet wilt verzenden.

   ![](assets/social_twitter_delivery_011.png)

### Doel van proefdruk {#selecting-the-target-of-the-proof} selecteren

Op het tabblad **[!UICONTROL Target of the proofs]** kunt u de Twitter-account definiëren die voor testleveringen moet worden gebruikt voordat de uiteindelijke levering plaatsvindt. Daarom raden we u aan een persoonlijke Twitter-account te maken voor het verzenden van proefdrukken. Raadpleeg [Een testaccount maken op Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter) voor meer informatie over het maken van een persoonlijke Twitter-account. De stappen voor het selecteren van het proefdrukdoel zijn hetzelfde als voor het selecteren van het hoofddoel. Zie [Een testaccount maken op Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter).

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>Als u dezelfde Twitter-testaccount gebruikt voor al uw leveringen, kunt u het proefdrukdoel opslaan in de **[!UICONTROL Tweet]**-leveringssjabloon, geopend via het knooppunt **[!UICONTROL Resources > Templates > Delivery templates]**. Het proefdrukdoel wordt dan standaard ingevoerd voor elke nieuwe levering.

### De berichtinhoud definiëren {#defining-the-message-content}

Typ de inhoud van de tweet op het tabblad **[!UICONTROL Content]**.

![](assets/social_twitter_delivery_005.png)

### De voorvertoning {#viewing-the-preview} weergeven

Op het tabblad **[!UICONTROL Preview]** kunt u een rendering van de tweet weergeven.

1. Klik op het tabblad **[!UICONTROL Preview]**.
1. Klik op het vervolgkeuzemenu **[!UICONTROL Test personalization]** en selecteer **[!UICONTROL Service]**.
1. Selecteer in het veld **[!UICONTROL Folder]** de servicemap die uw Twitter-account bevat.
1. Kies de Twitter-account waarmee u de voorvertoning wilt testen.

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>De voorvertoning kan iets afwijken van de uiteindelijke tweet. We raden u aan een proefdruk vóór de uiteindelijke aflevering te verzenden om een exacte weergave van de tweet te bekijken. Zie [De proefdruk verzenden](#sending-the-proof).

### Reeksspatiëring {#configuring-tracking} configureren

Het volgen kan in de leveringsrapporten en op **[!UICONTROL Edit > Tracking]** lusje van de levering en de dienst worden bekeken.

De volgende configuratie is het zelfde als voor een e-maillevering. Raadpleeg [deze sectie](../../delivery/using/about-delivery-monitoring.md) voor meer informatie.

>[!NOTE]
>
>In het **[!UICONTROL Tweet]** leveringsmalplaatje, wordt het volgen toegelaten door gebrek.

>[!IMPORTANT]
>
>We kunnen het verschil niet zien tussen robots die tweets analyseren en gebruikers die klikken.

### De proefdruk {#sending-the-proof} verzenden

We raden u ten zeerste aan een bewijs van uw publicatie vóór de uiteindelijke levering te verzenden om een exacte weergave van de publicatie op een persoonlijke Twitter-testpagina te krijgen. Raadpleeg [Een testaccount maken op Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter) voor meer informatie over het maken van een persoonlijke Twitter-account. De stappen voor het selecteren van het proefdrukdoel worden beschreven in [Het doel van de proefdruk selecteren](#selecting-the-target-of-the-proof).

Bewijs van levering is identiek aan e-mailleveringen. Zie [deze sectie](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Het bericht {#sending-the-message} verzenden

1. Wanneer de inhoud is goedgekeurd, klikt u op de knop **[!UICONTROL Send]**.
1. Selecteer **[!UICONTROL Deliver as soon as possible]** en klik **[!UICONTROL Analyze]** knoop.

   >[!NOTE]
   >
   >Met de optie **[!UICONTROL Postpone the delivery]** kunt u de levering uitstellen tot een latere datum.

   ![](assets/social_twitter_delivery_012.png)

1. Controleer het resultaat als de analyse is voltooid.
1. Klik **[!UICONTROL Confirm delivery]**, dan klik **[!UICONTROL Yes]**.

![](assets/social_facebook_delivery_016.png)

## Directe berichten verzenden aan abonnees {#sending-direct-messages-to-subscribers}

### Werkwijze {#operating-principle}

De **[!UICONTROL Synchronize Twitter accounts]**-workflow (zie [Twitter-accounts synchroniseren](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts)) herstelt de lijst met Twitter-abonnees zodat u deze directe berichten kunt sturen. De herstelde volgers worden opgeslagen in een specifieke tabel: de bezoekerslijst. Ga naar het knooppunt **[!UICONTROL Profiles and Targets > Visitors]** om de lijst met Twitter-volgers weer te geven.

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>De workflow kan alleen de lijst met Twitter-volgers herstellen als het selectievakje **[!UICONTROL Synchronize Twitter accounts]** is ingeschakeld in het scherm Bewerken van de service die aan de account is gekoppeld. Raadpleeg voor meer informatie: [Schrijftoegang delegeren aan Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign).

Adobe Campaign herstelt voor elk van de volgende gegevens:

* **[!UICONTROL Origin]**: naam van het sociale netwerk (in dit geval **** Twittert)
* **[!UICONTROL External ID]**: gebruikersnaam
* **[!UICONTROL User name]**: accountnaam van de gebruiker
* **[!UICONTROL Full name]**: naam van de gebruiker
* **[!UICONTROL Language]**: gebruikerstaal
* **[!UICONTROL Number of friends]**: aantal volgers
* **[!UICONTROL Time zone]**: tijdzone van gebruiker
* **[!UICONTROL Verified]**: in dit veld wordt aangegeven of de gebruiker een geverifieerde Twitter-account heeft

### Beperkingen {#limitations-1}

De volgende beperkingen zijn inherent aan Twitter.

* Het bericht mag niet langer zijn dan 140 tekens.
* HTML wordt niet ondersteund.
* U kunt niet meer dan 250 directe berichten per dag verzenden. Als u wilt voorkomen dat deze drempelwaarde wordt overschreden, kunt u in verschillende golven leveren. Leveringen in golven worden geconfigureerd als e-mailleveringen. Raadpleeg [deze sectie](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) voor meer informatie.

### De levering maken {#creating-the-delivery-}

Creeer een nieuwe levering die op **[!UICONTROL Tweet (Direct Message)]** leveringsmalplaatje wordt gebaseerd.

![](assets/social_twitter_delivery_010.png)

### Het hoofddoel selecteren {#selecting-the-main-target-1}

Selecteer de volgers aan wie u uw directe bericht wilt verzenden.

1. Klik op de koppeling **[!UICONTROL To]**.

   ![](assets/social_twitter_delivery_016.png)

1. Klik op de knop **[!UICONTROL Add]**.

   ![](assets/social_twitter_delivery_006.png)

1. Selecteer een type doelverwijzing.

   ![](assets/social_twitter_delivery_017.png)

   * Selecteer **[!UICONTROL Twitter subscribers]** om een direct bericht naar alle volgers van de account te verzenden.

      >[!IMPORTANT]
      >
      >U kunt niet meer dan 250 berichten per dag verzenden. Als uw Twitter-account meer dan 250 volgers heeft, raden we u ten zeerste aan om uw account in golven te leveren. Dit omvat hetzelfde proces als e-mailleveringen. Zie [deze sectie](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

   * Selecteer **[!UICONTROL Filter conditions]** om een vraag te bepalen en zijn resultaat te bekijken. Deze optie is hetzelfde als voor e-mailleveringen. Zie [deze sectie](../../platform/using/defining-filter-conditions.md) voor meer informatie.

      ![](assets/social_twitter_delivery_018.png)

### Doel van proefdruk {#selecting-the-target-of-the-proof-1} selecteren

Op het tabblad **[!UICONTROL Target of the proofs]** kunt u de volgende persoon selecteren die de proefdruk van uw directe bericht ontvangt. Het selectieproces is hetzelfde als voor het hoofddoel. Zie [Het hoofddoel selecteren](#selecting-the-main-target).

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>Als u al uw directe berichtproefdrukken naar de zelfde Twitter volgster wilt verzenden, kunt u het proefdrukdoel in het **[!UICONTROL Tweet (Direct Message)]** leveringsmalplaatje opslaan, dat via **[!UICONTROL Resources > Templates > Delivery templates]** knoop wordt betreden. Het proefdrukdoel wordt dan standaard ingevoerd voor elke nieuwe levering.

### Inhoud van bericht {#defining-message-content-} definiëren

Typ de inhoud van de tweet op het tabblad **[!UICONTROL Content]**.

![](assets/social_twitter_delivery_015.png)

Velden voor persoonlijke voorkeur kunnen op dezelfde manier worden gebruikt als voor e-mailleveringen, bijvoorbeeld om de naam van de volgende persoon toe te voegen aan de hoofdtekst van het bericht. De verpersoonlijking van de inhoud wordt gedetailleerd in [deze sectie](../../delivery/using/about-personalization.md).

![](assets/social_twitter_delivery_021.png)

De volgende stappen zijn hetzelfde als het verzenden van een tweet naar een Twitter-account. Raadpleeg [Publiceren op uw Twitter-accounts](#publishing-on-your-twitter-accounts).
