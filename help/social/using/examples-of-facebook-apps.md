---
solution: Campaign Classic
product: campaign
title: Voorbeelden van Facebook-apps
description: Voorbeelden van Facebook-apps
audience: social
content-type: reference
topic-tags: annexes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 1%

---


# Voorbeelden van Facebook-apps{#examples-of-facebook-apps}

Wanneer een gebruiker op de tab van een Facebook-toepassing klikt, wordt deze weergegeven in een ruimte van 810 pixels breed. Adobe Campaign gebruikt een webtoepassing van het type Facebook waarmee u de inhoud die in de Facebook-toepassing wordt weergegeven, kunt definiëren en aanpassen, zodat het eenvoudiger wordt profielen aan te schaffen.

>[!NOTE]
>
>Het is ook mogelijk om Adobe Campaign te integreren met een Facebook-toepassing die door een partner is ontwikkeld. In dit geval is het niet nodig om de Adobe Campaign-webtoepassing te gebruiken voor het aanschaffen van Facebook-profielen. Voor meer op dit, verwijs naar [Het vormen van externe rekeningen](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

>[!IMPORTANT]
>
>Volg de configuratiestappen die worden beschreven in [Een Facebook-toepassing maken](../../social/using/creating-a-facebook-application.md).

>[!NOTE]
>
>In deze sectie worden de elementen beschreven die zijn gekoppeld aan webtoepassingen van het type Facebook. Alle elementen die worden gedeeld met standaardwebtoepassingen worden beschreven in [deze sectie](../../web/using/about-web-applications.md).

Hier worden de volgende voorbeelden gegeven van webtoepassingen van het type Facebook:

* Hoe maakt u in 7 stappen een Facebook-toepassing. Raadpleeg [Snel starten: het maken van een Facebook-toepassing in 7 stappen](#quick-start--creating-a-facebook-application-in-7-steps).
* Instellingen doorsturen naar een Facebook-toepassing. Zie [Hoe kan ik instellingen doorsturen naar een Facebook-toepassing?](#how-to-forward-settings-to-a-facebook-application-).
* Hoe verkrijgt u ventilatorgegevens. Raadpleeg [Hoe verkrijgt u ventilatorgegevens?](#how-to-acquire-fan-data-).

>[!IMPORTANT]
>
>Deze eenvoudige gebruiksgevallen worden gegeven als voorbeelden om de functionaliteit van Facebook-webtoepassingen te illustreren.

## Aanbevelingen {#recommendations}

De volgende beperkingen zijn rechtstreeks gekoppeld aan Facebook:

* U moet al uw webtoepassingen maken in HTTPS.
* Een Facebook-toepassing die via een tabblad wordt weergegeven, heeft een breedte van 810 pixels.

## Snel starten: een Facebook-toepassing maken in 7 stappen {#quick-start--creating-a-facebook-application-in-7-steps}

In dit voorbeeld wordt stapsgewijs uitgelegd hoe u een Adobe Campaign-toepassing die op Facebook is gebouwd, kunt weergeven. In dit geval, willen wij een toepassing tot stand brengen die u het **Welkome** bericht laat tonen wanneer de gebruiker het toepassingslusje (**App01**) klikt.

Voer de volgende stappen uit om deze toepassing te maken:

1. Maak een toepassing op Facebook ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)). Raadpleeg voor meer informatie: [Een Facebook-toepassing maken](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application).

   ![](assets/social_create_facebook_app_002.png)

1. Maak een **[!UICONTROL Facebook Connect]**-type externe account en voer de parameters van de Facebook-toepassing in. Raadpleeg voor meer informatie: [Externe accounts configureren](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

   ![](assets/social_quick_start_2.png)

1. Voer de **[!UICONTROL Terms of service]**- en **[!UICONTROL Privacy policy]**-koppelingen in die moeten worden weergegeven op het scherm voor het aanvragen van bevoegdheden op Facebook. Raadpleeg voor meer informatie: [De koppelingen voor service- en privacybeleid invoeren](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links).

   ![](assets/social_quick_start_1.png)

1. Maak een Facebook-webtoepassing in Adobe Campaign. Raadpleeg voor meer informatie: [Een webtoepassing van het type Facebook maken](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_005.png)

1. Bewerk uw webtoepassing. In dit voorbeeld hebben we een **[!UICONTROL Page]**-activiteit toegevoegd en een titel daarvoor gedefinieerd.

   ![](assets/social_quick_start_4.png)

1. Implementeer uw toepassing.

   ![](assets/social_webapp_004.png)

1. Configureer uw Facebook-toepassing zodat deze als een tabblad op uw Facebook-pagina wordt weergegeven. Raadpleeg voor meer informatie: [Facebook-tabs configureren](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs).

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

Controleer of het tabblad van de toepassing **App01** wordt weergegeven op uw Facebook-pagina. Als u erop klikt, wordt het bericht **Welcome** weergegeven.

![](assets/social_webapp_042.png)

## Hoe kan ik instellingen doorsturen naar een Facebook-toepassing? {#how-to-forward-settings-to-a-facebook-application-}

>[!IMPORTANT]
>
>Volg de configuratiestappen die in [Een Facebook-toepassing](../../social/using/creating-a-facebook-application.md) worden beschreven.

In voorbeeld 1 hebben we de weergave van de Facebook-pagina aangepast aan de waarde in het veld **[!UICONTROL Fan of the page]**. Het is ook mogelijk het veld **[!UICONTROL Application settings]** te verwerken. Met dit veld kunt u gegevens herstellen die zijn opgeslagen in een koppeling die door Adobe Campaign via Facebook is gegenereerd.

Laten we het voorbeeld nemen van een bedrijf dat besluit een e-mailcampagne te verzenden. Tijdens de levering wijst een koppeling naar de Facebook-toepassing. Deze koppeling is gepersonaliseerd dankzij de parameter **[!UICONTROL app_data]** die aan het einde van de URL is toegevoegd. De waarde van deze parameter zou een indicator kunnen zijn die op klantenbelangrijkheid wijst. In ons voorbeeld zijn de waarden van de parameter **[!UICONTROL app_data]** **[!UICONTROL big]** (significante klant) en **[!UICONTROL small]** (minder belangrijke klant).

Zodra het wordt gepersonaliseerd, kijkt URL als dit:

* `http://<path of the Facebook application>&app_data=big` (voor een belangrijke klant)
* `http://<path of the Facebook application>&app_data=small` (voor een minder belangrijke klant)

Onder de anonieme gegevens die door Facebook naar Adobe Campaign worden doorgestuurd, wordt de waarde van het veld **[!UICONTROL Application parameters]** verzameld, zodat Adobe Campaign de weergave van de toepassing op basis van deze parameter kan aanpassen.

Als de gebruiker een belangrijke klant is (de waarde van de parameter **[!UICONTROL app_data]** is **[!UICONTROL big]**), wordt het volgende beeld getoond:

![](assets/social_webapp_017.png)

Als de gebruiker een minder belangrijke klant is (de waarde van de parameter **[!UICONTROL app_data]** is **[!UICONTROL small]**), wordt het volgende beeld getoond:

![](assets/social_webapp_016.png)

Voor het opnieuw maken van dit gebruiksgeval hebben we een webtoepassing gemaakt die bestaat uit de volgende elementen:

* A **[!UICONTROL Test]** activity based on the **[!UICONTROL Application parameter]** field.
* twee pagina&#39;s die de afbeeldingen bevatten die moeten worden weergegeven volgens de waarde van het veld **[!UICONTROL Application parameter]**.

![](assets/social_webapp_018.png)

## Hoe verkrijgt u ventilatorgegevens? {#how-to-acquire-fan-data-}

>[!IMPORTANT]
>
>Volg de configuratiestappen die in [Een Facebook-toepassing](../../social/using/creating-a-facebook-application.md) worden beschreven.

In dit voorbeeld ziet u hoe u contact opneemt met Facebook-gebruikers en hen aanbiedt hun profielgegevens te delen. Laten we het voorbeeld nemen van een bedrijf dat vooruitzichten wil verwerven en een wedstrijd organiseert op zijn Facebook-pagina om ze aan te trekken.

Wanneer een gebruiker op het tabblad **[!UICONTROL App03]** klikt, wordt hen gevraagd of zij aan de wedstrijd willen deelnemen.

![](assets/social_webapp_fb_000.png)

Als zij besluiten aan de wedstrijd deel te nemen, bieden wij hun aan hun profielinformatie te delen.

![](assets/social_webapp_021.png)

Als ze hun gegevens willen delen, wordt het volgende scherm weergegeven.

![](assets/social_webapp_022.png)

Voor het samenstellen van dit gebruiksgeval hebben we een webtoepassing gemaakt die de volgende elementen bevat:

* een **[!UICONTROL Test]**-activiteit
* drie pagina&#39;s
* een **[!UICONTROL Access control]** activiteit
* een **[!UICONTROL Pre-loading]**-activiteit
* een **[!UICONTROL Save]**-activiteit
* een **[!UICONTROL End]** activiteit

![](assets/social_webapp_019.png)

### Testactiviteit {#test-activity}

De **[!UICONTROL Test]** activiteit is gebaseerd op **[!UICONTROL ID]** en **[!UICONTROL Application parameters]** gebied.

![](assets/social_webapp_023.png)

Het bestaat uit drie bijkantoren:

* **[!UICONTROL identifier (UID) is empty]** : De identificatiecode wordt alleen door Facebook doorgestuurd als de gebruiker al heeft ingestemd met het delen van zijn gegevens. Met de eerste vertakking van de activiteit **[!UICONTROL Test]** kunt u de concurrentie alleen beschikbaar maken voor gebruikers die nog nooit zijn ingegaan, dat wil zeggen gebruikers met een lege id.
* **[!UICONTROL application parameter equals 'thanks']** : Als u een weergavefout wilt toevoegen die is gekoppeld aan Facebook, wijst de eindpagina van de webtoepassing naar de URL van de Facebook-toepassing die met de  **[!UICONTROL app_data]** parameter wordt toegevoegd aan het gebruik van de  **[!UICONTROL thanks]** waarde (zie voor meer informatie:  [Eindactiviteit](#end-activity)). De tweede tak laat u weten of de gebruiker uit de **[!UICONTROL End]** activiteit van de eerste tak (en is enkel ingegaan op de concurrentie) komt om een dankwoord te tonen. Raadpleeg voor meer informatie over het gebruik van aanvullende URL-parameters: [Hoe kan ik instellingen doorsturen naar een Facebook-toepassing?](#how-to-forward-settings-to-a-facebook-application-).
* **[!UICONTROL Default branch]** : als de gebruiker reeds op een vorige datum (toepassingsparameter verschillend van) de concurrentie (reeds ingegaan identiteitskaart) is ingegaan, zullen wij een pagina tonen die zegt dat zij reeds zijn ingegaan.  **[!UICONTROL thanks]**

### Mededingingspagina {#competition-page}

Als u de aan Facebook gekoppelde weergavefout wilt negeren, moet u **[!UICONTROL Parent window]** of **[!UICONTROL In the top window]** ook selecteren in het veld **[!UICONTROL Window]** van de wedstrijdpagina.

![](assets/social_webapp_028.png)

### Activiteit van toegangsbeheer {#access-control-activity}

Met de activiteit **[!UICONTROL Access control]** kunt u de pagina voor aanvragen van Facebook-machtigingen weergeven wanneer de gebruiker de wedstrijd opent. Als zij ermee instemmen hun informatie te delen, wordt deze tijdens het vooraf laden teruggewonnen. Raadpleeg voor meer informatie: [Voorladingsactiviteit](#pre-loading-activity).

Als u eerder het externe account hebt ingevoerd bij het maken van de webtoepassing (zie [Een webtoepassing van het type Facebook maken](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)), hoeft u de activiteit niet te bewerken. Als dat niet het geval is, gaat u naar het veld **[!UICONTROL Application]** en selecteert u de externe account die is gekoppeld aan de Facebook-toepassing.

![](assets/social_webapp_024.png)

### Activiteiten {#pre-loading-activity} vooraf laden

Selecteer de gegevensbron die moet worden gebruikt voor het vooraf laden:

* **[!UICONTROL Marketing database]** : Met deze optie kunt u gegevens vooraf laden via de Adobe Campaign-database.
* **[!UICONTROL Facebook]** : Met deze optie kunt u gegevens vooraf laden via Facebook.

![](assets/social_webapp_029.png)

**Marketing Database**

Met deze optie kunt u de gegevens herstellen van een profiel dat bestaat in de tabel met bezoekers. De verificatie wordt uitgevoerd op basis van de externe Facebook-id die wordt hersteld wanneer de gebruiker op het tabblad Facebook-toepassing klikt. Als u een formulier toevoegt na de **[!UICONTROL Pre-loading]**-activiteit, worden de velden die informatie in de database bevatten, vooraf geladen.

![](assets/social_webapp_030.png)

>[!NOTE]
>
>Raadpleeg [deze sectie](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data) voor meer informatie over het vooraf laden van gegevens via de Adobe Campaign-database.

**Facebook**

Met deze optie kunt u de Facebook-profielgegevens definiëren die u wilt verzamelen, onder de informatie die de gebruiker heeft willen delen, om deze op te slaan.

![](assets/social_webapp_025.png)

Met de optie **[!UICONTROL Database information]** kunt u de volgende gegevens verzamelen:

* **[!UICONTROL External ID]**: gebruikersnaam
* **[!UICONTROL Gender]**: geslacht van de gebruiker
* **[!UICONTROL Verified]** : in dit veld wordt aangegeven of de gebruiker een geverifieerd Facebook-account heeft.
* **[!UICONTROL Full name]**: volledige naam van gebruiker
* **[!UICONTROL First name]**: voornaam van gebruiker
* **[!UICONTROL Last name]**: achternaam van gebruiker
* **[!UICONTROL Language]**: taal van de gebruiker

U kunt ook besluiten om de profielfoto, de lijst met vrienden, e-mailadres, geboortedatum, interesses en locatie te verzamelen door de juiste vakjes in te schakelen.

Controleer het vakje **[!UICONTROL I agree to comply with Facebook conditions of use]** voordat u op **[!UICONTROL Ok]** klikt.

>[!NOTE]
>
>Als u een of meer vakjes in de **[!UICONTROL Private information]** sectie controleert, zal het Facebook toestemmingsverzoekscherm automatisch het toegangsverzoek voor deze gegevens tonen.
>
>Als u de geselecteerde gegevens wilt verzamelen, moet de gebruiker ermee instemmen deze te delen.
>
>Als u beide typen voorladen wilt gebruiken (via Adobe Campaign en via Facebook), voegt u twee vooraf geladen vakken achter elkaar toe.

### Activiteiten opslaan {#save-activity}

Met de activiteit **[!UICONTROL Save]** kunt u de informatie opslaan die tijdens de vorige fasen in de bezoekerslijst is verzameld.

Als het profiel al in de bezoekerslijst bestaat, worden hun gegevens bijgewerkt met de nieuwe verzamelde gegevens.

Als het profiel niet bestaat in de database en het e-mailadres van de Facebook-gebruiker is verzameld, wordt een bezoeker gemaakt in de tabel met bezoekers.

![](assets/social_webapp_026.png)

1. Selecteer in het veld **[!UICONTROL Visitor creation folder]** de map waarin het profiel wordt gemaakt. In het geval van een Facebook-webtoepassing is de standaardmap voor het maken van bestanden **[!UICONTROL Visitors]**.
1. Selecteer in het veld **[!UICONTROL Reconciliation mode]** de afstemmingsmodus die u wilt gebruiken:

   * **[!UICONTROL Automatic]** : De afstemming vindt plaats op basis van e-mail, achternaam, voornaam en geboortedatum.
   * **[!UICONTROL Manual]** : Selecteer een of meer afstemmingssleutels.
   * **[!UICONTROL None]** : Er vindt geen verzoening plaats.

1. Selecteer in het veld **[!UICONTROL Mapping]** het schema waarop u de afstemming wilt uitvoeren.

   >[!IMPORTANT]
   >
   >Zorg ervoor dat de velden op het tabblad **[!UICONTROL Social networks]** correct zijn ingevoerd in de leveringstoewijzing. Leveringstoewijzingen zijn toegankelijk via het knooppunt **[!UICONTROL Administration > Campaign management > Target mappings]**.

1. U kunt een zoekmap selecteren voor afstemming en een map maken voor nieuwe profielen. Als de velden leeg zijn, worden profielen gezocht naar en gemaakt in de standaardmap van het toewijzingsschema.

### Eindactiviteit {#end-activity}

Als u de weergavefout wilt negeren die aan Facebook is gekoppeld, moet u het vakje **[!UICONTROL Use an external URL]** controleren en de URL van de Facebook-toepassing invoeren, gevolgd door de parameter **[!UICONTROL app_data]** en een waarde. Deze waarde wordt gebruikt in de **[!UICONTROL Test]** activiteit om te ontdekken of de gebruiker enkel de concurrentie is ingegaan, en om een dankwoord te tonen indien van toepassing. Raadpleeg voor meer informatie: [Testactiviteit](#test-activity).

In ons voorbeeld wordt **bedankt** gebruikt.

![](assets/social_webapp_027.png)

### Scherm Details van een bezoeker {#details-screen-of-a-visitor}

Net als voor Twitter-volgers (zie: [Operationeel principe](../../social/using/publishing-on-twitter.md#operating-principle)), herstelde Facebook-profielen worden opgeslagen in de tabel met bezoekers. Ga naar het knooppunt **[!UICONTROL Profiles and Targets > Visitors]** om de lijst met bezoekers weer te geven.

Elk Facebook-perspectief dat ermee instemt hun profielgegevens te delen, wordt toegevoegd aan de lijst met bezoekers. Als de **[!UICONTROL Friends]** doos in **[!UICONTROL Pre-load]** activiteit wordt gecontroleerd (verwijs naar: [Aan het vooraf laden worden ook vrienden toegevoegd.](#pre-loading-activity)

![](assets/social_webapp_037.png)

In de sectie **[!UICONTROL Summary]** van het detailvenster van de bezoeker, zijn er twee mogelijke staten voor **[!UICONTROL New Contact]** indicator:

![](assets/social_webapp_038.png)

Als een groen vinkje wordt weergegeven, betekent dit dat de bezoeker zich niet heeft aangesloten bij ontvangers. In dit geval wordt een nieuw profiel gemaakt in de lijst met ontvangers.

![](assets/social_webapp_039.png)

Een rood kruis betekent dat de bezoeker in overeenstemming is gebracht met een ontvanger. U kunt op de vergroting rechts van het veld **[!UICONTROL Recipient]** klikken om de overeenkomende ontvanger weer te geven.

![](assets/social_webapp_040.png)

Ga naar het detailvenster van een ontvanger om de overeenkomende bezoeker, indien van toepassing, weer te geven. Selecteer het tabblad **[!UICONTROL Others]** en dubbelklik vervolgens op de naam van de bezoeker in de sectie **[!UICONTROL Web identities]**.

![](assets/social_webapp_041.png)

Het scherm **[!UICONTROL Activities]** van de detailpagina van een bezoeker bevat de volgende informatie:

* Ventilatoractiviteiten van het type &quot;Open Graph&quot;: muziek, video&#39;s die worden afgespeeld, artikelen die worden gelezen en gelezen en waarop de geïnstalleerde toepassingen zijn gebaseerd (Deezer, Spotify, Dailymotion, Yahoo News, enz.)

   ![](assets/social_facebook_activities.png)

* &quot;Likes&quot; en opmerkingen toegevoegd door de ventilator na leveringen verzonden door Adobe Campaign
* pagina&#39;s die door de ventilator worden gevonden
* inchecken door de ventilator

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >Als u wilt dat Adobe Campaign de insteekmodules van een ventilator verzamelt, moet u op de knop **[!UICONTROL Subscribe]** op het serviceconfiguratiescherm klikken. Voor meer op dit, verwijs naar [Het vormen van externe rekeningen](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

## De velden van een formulier vooraf laden met Facebook-profielgegevens {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

Met de toepassing **[!UICONTROL Social Marketing]** kunt u ook een knop aan een formulier toevoegen, zodat u velden vooraf kunt laden met Facebook-profielgegevens. Deze optie, die beschikbaar is in alle malplaatjes van de Webtoepassing (**[!UICONTROL Page]** typeactiviteiten) wordt gedetailleerd in [deze sectie](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/social_webapp_035.png)

>[!NOTE]
>
>Voordat u deze functie gaat gebruiken, moet u een Facebook-toepassing maken en een externe account van het type **[!UICONTROL Facebook Connect]**. Voor meer op dit, verwijs naar [Het vormen van externe rekeningen](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

