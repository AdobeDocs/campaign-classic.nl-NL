---
product: campaign
title: Publiceren op Facebook
description: Publiceren op Facebook
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: 84d6cb2e-c7f9-43d7-a98c-22613d456193
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 3%

---

# Publiceren op Facebook{#publishing-on-facebook}

![](../../assets/v7-only.svg)

Als de configuratie is voltooid, kunt u via Social Marketing publicaties op de muren van uw Facebook-pagina&#39;s plaatsen.

## Beperkingen {#limitations}

De volgende beperkingen zijn inherent aan Facebook.

* Berichten mogen niet langer zijn dan 1.000 tekens.
* HTML wordt niet ondersteund.

## De levering maken {#creating-the-delivery}

Een nieuwe levering maken met de **[!UICONTROL Publish to a brand page]** leveringssjabloon.

![](assets/social_facebook_delivery_001.png)

## Het hoofddoel selecteren {#selecting-the-main-target}

U moet de pagina(&#39;s) selecteren waarop u uw publicatie wilt plaatsen.

1. Klik op de koppeling **[!UICONTROL To]**.

   ![](assets/social_facebook_delivery_010.png)

1. Klik op de knop **[!UICONTROL Add]**.

   ![](assets/social_facebook_delivery_011.png)

1. Selecteer **[!UICONTROL A Facebook page]**.

   ![](assets/social_facebook_delivery_012.png)

1. In de **[!UICONTROL Folder]** , selecteert u de servicemap die de Facebook-pagina bevat. Pagina&#39;s worden standaard opgeslagen in de hoofdmap van het dialoogvenster **[!UICONTROL Facebook]** servicemap. Selecteer vervolgens de Facebook-pagina waarop u wilt plaatsen.

   ![](assets/social_facebook_delivery_013.png)

## Het proefdrukdoel selecteren {#selecting-the-proof-target}

De **[!UICONTROL Target of the proofs]** kunt u de Facebook-pagina definiëren die u wilt gebruiken voor het testen van leveringen voordat u deze verzendt. We raden u aan hiervoor een speciale persoonlijke Facebook-pagina te maken. Voor meer informatie over het maken van een persoonlijke Facebook-pagina raadpleegt u [Een Facebook-testpagina maken](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). Als u het proefdrukdoel wilt selecteren, voert u dezelfde stappen uit als voor het hoofddoel: [Het hoofddoel selecteren](#selecting-the-main-target).

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>Als u dezelfde Facebook-testpagina gebruikt voor alle leveringen, kunt u het proefdrukdoel opslaan in het dialoogvenster **[!UICONTROL Publish to a brand page]** leveringssjabloon, dat toegankelijk is via de **[!UICONTROL Resources > Templates > Delivery templates]** knooppunt. Het proefdrukdoel wordt standaard ingevoerd voor elke nieuwe levering.

## Het publiek definiëren {#defining-the-audience}

Als u lokale segmenten wilt gebruiken om het type openbaar te verfijnen dat is geautoriseerd om de publicatie te bekijken, raden we u aan één Facebook-pagina per segment te maken (bijvoorbeeld: Adobe Campaign Paris, Adobe Campaign London, enz.).

Het is echter ook mogelijk om de publieksfilters te gebruiken die door Facebook worden gebruikt. De **[!UICONTROL Audience]** tabblad van het dialoogvenster **[!UICONTROL Select target window]** biedt vier filters:

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!IMPORTANT]
>
>Wees voorzichtig met deze functie. In leveringsrapporten, **[!UICONTROL Number of fans]** Deze Facebook-filters worden niet in aanmerking genomen.
>
>Facebook kan de lijst met publieksfilters en de bijbehorende waarden wijzigen.

## Berichtinhoud definiëren {#defining-message-content}

Selecteer het type publicatie met de opdracht **[!UICONTROL Content type]** vervolgkeuzemenu.

![](assets/social_facebook_delivery_006.png)

De volgende typen leveringen zijn beschikbaar:

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### Een status publiceren {#publishing-a-status}

Een levering van een statustype kan alleen tekst bevatten, zoals in het onderstaande voorbeeld:

![](assets/social_create_facebook_wall_post_004.png)

Voer de publicatiestatus in de invoerzone in.

![](assets/social_facebook_delivery_015.png)

### Een status met een koppeling publiceren {#publishing-a-status-with-a-link}

Een levering van het statustype met een koppeling kan tekst, afbeeldingen en een koppeling bevatten. In de volgende sectie wordt de symmetrie beschreven tussen de velden van het bewerkingsscherm en de laatste publicatie op Facebook:

![](assets/social_facebook_delivery_007.png)

Voer de verschillende velden in:

>[!IMPORTANT]
>
>Alle URL&#39;s moeten beginnen met **&quot;http://&quot;** of **&quot;https://&quot;**.

1. In de **[!UICONTROL Status]** voert u de tekst in die onder de naam van de pagina wordt weergegeven.
1. In de **[!UICONTROL Name]** Voer de titel van de publicatie in.
1. In de **[!UICONTROL Link]** voert u de URL in waarnaar de publicatie verwijst.

   >[!NOTE]
   >
   >Als u de **[!UICONTROL Link]** We raden u aan het veld aan te passen aan de URL van een Facebook-toepassing om dit te promoten.
   >
   >1. De Facebook-toepassing selecteren [https://developers.facebook.com/apps](https://developers.facebook.com/apps)en selecteert u de **[!UICONTROL Settings > Basic]** tab.
   >1. Voer de **[!UICONTROL Namespace]** veld.
   >1. Voer de **[!UICONTROL Mobile Site URL]** veld: wanneer een gebruiker op de publicatiekoppeling op zijn smartphone klikt, wordt deze automatisch door Facebook omgeleid naar de URL die in dit veld is gedefinieerd.
   >1. Maak uw webtoepassing zodat de Facebook-weergave wordt gepersonaliseerd als een functie van het gebruikte apparaat (smartphone of pc).
   >1. Ga naar de **[!UICONTROL Link]** Voer in het veld van de publicatie via de Adobe Campaign-console de URL van het **[!UICONTROL Canvas page]** veld.


1. In de **[!UICONTROL Image]** Voer de URL in van de afbeelding die links van de publicatie wordt weergegeven.

   >[!IMPORTANT]
   >
   >De afbeelding moet op een openbare website worden gehost, anders kan Facebook deze niet uploaden.

1. In de **[!UICONTROL Caption]** voert u de tekst in die aan het einde van de publicatie wordt weergegeven.
1. Ga naar de **[!UICONTROL Description]** en voert u de tekst in die onder de titel moet worden weergegeven.

![](assets/social_facebook_delivery_005.png)

### Een status publiceren met een YouTube-koppeling {#publishing-a-status-with-a-youtube-link}

Met dit type inhoud kunt u een koppeling naar een YouTube-video publiceren. Net als bij een status met een gewone koppeling kunt u een status, naam, bijschrift, beschrijving en aanvullende koppeling definiëren. De afbeelding wordt automatisch door Facebook toegevoegd. De symmetrieën tussen de velden van het bewerkingsscherm van de levering en de definitieve publicatie op Facebook worden hieronder beschreven:

![](assets/social_facebook_delivery_youtube_1.png)

Voer de verschillende velden in:

>[!IMPORTANT]
>
>Alle URL&#39;s moeten beginnen met **&quot;http://&quot;** of **&quot;https://&quot;**.

1. In de **[!UICONTROL Status]** voert u de tekst in die onder de naam van de pagina wordt weergegeven.
1. In de **[!UICONTROL Name]** Voer de titel van de publicatie in.
1. In de **[!UICONTROL Video code]** voert u de code van de YouTube-video in. Voor de koppeling &#39;https://www.youtube.com/watch?v=abc123456&#39;&#39; is de videocode &#39;abc123456&#39;.
1. In de **[!UICONTROL Caption]** voert u de tekst in die aan het einde van de publicatie wordt weergegeven.
1. Ga naar de **[!UICONTROL Description]** en voert u de tekst in die onder de titel moet worden weergegeven.

![](assets/social_facebook_delivery_youtube.png)

### Een fotoalbum publiceren {#publishing-a-photo-album}

Met dit type inhoud kunt u een fotoalbum publiceren. U kunt voor elke foto een naam en een beschrijving voor het album en een bijschrift toevoegen. De symmetrieën tussen de velden van het bewerkingsscherm van de levering en de definitieve publicatie op Facebook worden hieronder beschreven:

![](assets/social_facebook_delivery_photos_1.png)

Voer de verschillende velden in:

1. Begin door de **[!UICONTROL Album name]**.
1. Voer vervolgens de **[!UICONTROL Description]** boven de foto&#39;s worden weergegeven.
1. Als u een foto wilt toevoegen, klikt u op de knop **[!UICONTROL Add]** selecteert u de foto en klikt u op **[!UICONTROL Open]**.
1. Aan elke foto kan een bijschrift worden toegevoegd.

![](assets/social_facebook_delivery_photos.png)

## Voorvertoning {#previewing}

De **[!UICONTROL Preview]** kunt u de rendering van de publicatie weergeven.

1. Klik op de knop **[!UICONTROL Preview]** tab.
1. Klik op de knop **[!UICONTROL Test personalization]** vervolgkeuzelijst en selecteert u **[!UICONTROL Service]**.
1. In de **[!UICONTROL Folder]** , selecteert u de servicemap die uw Facebook-pagina&#39;s bevat. Pagina&#39;s worden standaard in de hoofdmap van het dialoogvenster **[!UICONTROL Facebook]** servicemap.
1. Selecteer de Facebook-pagina waarop u de voorvertoning wilt testen.

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>De voorvertoning kan iets afwijken van de uiteindelijke Facebook-publicatie. We raden u aan vóór de definitieve levering een bewijs te verzenden voor een exacte weergave van de publicatie. Zie [De proefdruk verzenden](#sending-the-proof).

## Tekstspatiëring configureren {#configuring-tracking}

Het volgen kan in de leveringsrapporten en in worden bekeken **[!UICONTROL Edit > Tracking]** tabblad van de levering en de service.

Klik op de URL in de levering wordt gemeten door Adobe Campaign. Het aantal klikken op de knop **[!UICONTROL Like]** , het aantal opmerkingen en het aantal ventilatoren wordt door Facebook gemeten.

De volgende configuratie is het zelfde als voor een e-maillevering. Raadpleeg [deze sectie](../../delivery/using/about-delivery-monitoring.md) voor meer informatie.

>[!NOTE]
>
>In de **[!UICONTROL Publish to a brand page]** leveringssjabloon; reeksspatiëring is standaard ingeschakeld.

## De proefdruk verzenden {#sending-the-proof}

We raden u aan een bewijs van uw publicatie vóór de uiteindelijke levering te verzenden om de exacte weergave van de publicatie op een persoonlijke Facebook-testpagina te bekijken. Voor meer informatie over het maken van een persoonlijke Facebook-testpagina raadpleegt u [Een Facebook-testpagina maken](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). De stappen voor het selecteren van de doelproefdruk worden beschreven in [Het proefdrukdoel selecteren](#selecting-the-proof-target).

Bewijs van levering is identiek aan e-mailleveringen. Zie [deze sectie](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Het bericht verzenden {#sending-the-message}

1. Als de inhoud is goedgekeurd, klikt u op de knop **[!UICONTROL Send]** knop.
1. Selecteren **[!UICONTROL Deliver as soon as possible]** en klik op de knop **[!UICONTROL Analyze]** knop.

   >[!NOTE]
   >
   >De **[!UICONTROL Postpone the delivery]** kunt u de levering uitstellen tot een latere datum.

   ![](assets/social_facebook_delivery_009.png)

1. Controleer het resultaat wanneer de analyse is voltooid.
1. Klikken **[!UICONTROL Confirm delivery]** en klik vervolgens op **[!UICONTROL Yes]**.

   ![](assets/social_facebook_delivery_016.png)
