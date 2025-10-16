---
product: campaign
title: Opt-out voor tracking van een webapplicatie
description: Opt-out voor tracking van een webapplicatie
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Web Apps
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
source-git-commit: 0507e0372a81351adc145dafdd3cbe5d5422dc00
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 2%

---

# Opt-out voor tracking van een webapplicatie{#web-application-tracking-opt-out}



Met Adobe Campaign kunt u het webgedrag niet meer volgen van eindgebruikers die zich afmelden voor het volgen van gedrag via cookies of webbakens. De functie omvat de mogelijkheid om een banner weer te geven om de eindgebruiker die optie te bieden; u kunt deze banners toevoegen aan webtoepassingen of landingspagina&#39;s.

Als een eindgebruiker via cookies of webbeacons de functie voor het bijhouden van gedrag uitschakelt, wordt die informatie met JavaScript API&#39;s naar de Adobe Campaign-traceringsserver verzonden. Houd er rekening mee dat sommige rechtsgebieden vereisen dat de klant eindgebruikers een opt-in biedt voordat een opt-out kan worden aangeboden (of andere wettelijke vereisten heeft) en dat de klant verantwoordelijk is voor het naleven van de toepasselijke wetgeving.

>[!NOTE]
>
>Wanneer het scripting altijd de richtlijnen volgt die in [&#x200B; worden beschreven checklist van de Veiligheid en van de Privacy &#x200B;](https://helpx.adobe.com/campaign/kb/acc-security.html#dev).

## De banner configureren {#configuring-the-banner-}

Om binnen de toepassingen van het Web of het Landing pagina&#39;s te worden getoond, moet de banner worden gevormd.

Adobe Campaign wordt geleverd met een voorbeeldbanner die u aan uw behoeften moet aanpassen. Deze bannerversie wordt weergegeven als een verpersoonlijkingsblok in de map van het inhoudsmodel. verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html){target="_blank"}.

>[!IMPORTANT]
>
>Als u uw eigen banner wilt maken, moet u de uit-van-de-box banner personaliseren.

Om de banner te activeren, moet u de de toepassingseigenschappen van het Web vormen. Verwijs naar [&#x200B; het Ontwerpen van een sectie van de Webtoepassing &#x200B;](designing-a-web-application.md).

Als het Web het volgen wordt geactiveerd, kunt u of hebben:

* Geen banner.
* Configureer de banner handmatig op elke pagina: controleer deze optie en selecteer de banner op elke pagina in de pagina-eigenschappen.

  ![](assets/pageproperties.png)

* Voeg automatisch de banner aan alle pagina&#39;s toe: selecteer de banner rechtstreeks in de de toepassingseigenschappen van het Web.

  ![](assets/optoutconfig.png)

>[!NOTE]
>
>Er is een compatibiliteitsmodus beschikbaar voor de v5 Web-toepassing met hetzelfde gedrag.

De standaardbanner heeft de volgende structuur:

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

U moet **vervangen gelieve uw bericht hier** met het blok op te nemen dat uw het volgen informatie bevat. Deze vervanging zou in uw nieuw personaliseringsblok met betrekking tot de uit opt-banner moeten worden uitgevoerd.

De banner wordt geleverd met een specifieke CSS. U kunt de stijlen echter overschrijven bij het maken en configureren van een webpagina. Zie [deze pagina](content-editor-interface.md).

## De uitschakelcookie instellen met API {#setting-the-opt-out-cookie-using-api}

Adobe Campaign wordt geleverd met API&#39;s waarmee u de cookiewaarde kunt beheren en gebruikersvoorkeuren kunt ophalen.

De koekjesnaam is **acoptout**. De gemeenschappelijke waarden zijn:

* 0: gebruiker heeft webspatiëring toegestaan (standaardwaarde)
* 1: gebruiker heeft webtracking verboden
* null: gebruiker heeft niet gekozen, maar webtracking is toegestaan omdat dit de standaardwaarde is

De beschikbare client-side API&#39;s om de banner aan te passen zijn:

* **NL.ClientWebTracking.allow ()**: Plaatst de opt-out koekjeswaarde om Web het volgen toe te staan. Webspatiëring is standaard toegestaan.
* **NL.ClientWebTracking.forbid ()**: Plaatst de opt-out koekjeswaarde om het volgen van het Web te verbieden. Webtracering vereist dat gebruikersinvoer wordt verboden.
* **NL.ClientWebTracking.closeOptOutBanner (bannerDomElt)**: Sluit de opt-out koekjesbanner nadat de gebruiker Accepteert of de knoop van de Weigering heeft geklikt. (tijdens de terugkoppelfase van de klikgebeurtenis)

  bannerDomElt {DOMElement} het hoofd-DOM-element van de cookie-banner die moet worden verwijderd

* **NL.ClientWebTracking.hasUserPrefs ()**: Keert waar terug als de gebruiker hun voorkeur voor het volgen van het Web heeft gekozen.
* **NL.ClientWebTracking.getUserPrefs ()**: Keert de opt-out koekjeswaarde terug die de voorkeur van de gebruiker bepaalt.

Als u een JSSP moet schrijven, zijn de server-zij APIs beschikbaar:

* **NL.ServerWebTracking.generateOptOutBanner (escapeJs)**: Produceert de prijsverhoging voor de opt-out banner om in de JSSP pagina op te nemen

  **escapeJs{Boolean}**: waar wanneer de geproduceerde prijsverhoging moet zijn ontsnapt om binnen JavaScript te worden gebruikt.

  Het retourneert de HTML van de opmaakcode voor de uitschakelbanner die op de pagina moet worden afgedrukt.

* **NL.ServerWebTracking._displayOptOutBanner()**

  Retourneert &quot;true&quot; als de uitschakelbanner moet worden weergegeven nadat de beheerder een uitschakelbanner heeft geselecteerd

  Deze code wordt geroepen wanneer de beheerder reeds heeft gekozen om de Web het volgen opt-out banner te gebruiken.

  De banner moet worden weergegeven als de gebruiker er nog niet voor heeft gekozen om te worden bijgehouden of niet.

* **NL.ServerWebTracking.renderOptOutBanner (escapeJs)**

  Geeft de prijsverhoging voor de opt-out banner door het in te voegen in de JSSP pagina terug. Wordt aangeroepen als in JPEG tussen &lt;% %>

  **escapeJs{Boolean}**: waar wanneer de geproduceerde prijsverhoging moet zijn ontsnapt om binnen JavaScript te worden gebruikt

JSSP-voorbeeld:

```
<%@ page import="/nl/core/shared/nl.js" %>
<!doctype html>
<%
NL.require('/nl/core/shared/webTracking.js');
NL.client.require('/nl/core/shared/webTracking.js');
%>
<html>
<head>
<%==NL.client.deps()%>
</head>

<body>

<!-- TEST USING SERVER API IN JSSP -->
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
webTracking.renderOptOutBanner();
%>

<!-- TEST USING SERVER API IN A SCRIPT -->
<!--
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
%>
<script>var el = document.createElement('div'); el.innerHTML =  "<% webTracking.renderOptOutBanner(true); %>";document.body.appendChild(el);</script>
-->

<!-- TEST OF THE CLIENT API -->
<!--
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
-->
</body>
</html>
```
