---
product: campaign
title: Ondersteuning voor TLS 1.0 en 1.1 verloopt
description: Ondersteuning voor TLS 1.0 en 1.1 verloopt
feature: Technote
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: e18d43b6-2a77-4881-85e7-ca36248d4634
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 3%

---

# Ondersteuning voor TLS 1.0 en 1.1 verloopt{#eol-tls-support}



De Adobe steunt niet meer gebruikerssystemen en cliëntsystemen die niet volgzaam met het Protocol van de Veiligheid van de Laag van het Vervoer (TLS) 1.2 zijn. Als u oudere versies van TLS blijft gebruiken, kan de toegang tot alle producten en services van de Adobe verloren gaan.

## Waarom zie ik deze pagina?

Als u het volgende bericht ziet: **Deze pagina kan niet worden weergegeven**, betekent dit dat voor de Adobe-apps, webpagina&#39;s of services die u wilt gebruiken, een veiligere netwerkverbinding met uw webbrowser, besturingssysteem of app is vereist. Het is verplicht **TLS 1.2** voor beveiligde netwerkcommunicatie en gegevensuitwisseling tussen gebruikerssystemen en Adobe-apps en webservices.

Adobe heeft afgekeurde ondersteuning voor lagere versies van TLS (inclusief TLS 1.0 en 1.1). Voor technische details over het TLS 1.2-protocol raadpleegt u [Veelgestelde vragen](#faq).

## Wat kan ik doen om de dienst te hervatten?

Moderne webbrowsers ondersteunen TLS 1.2. Als u uw browser upgradet, hebt u toegang tot deze apps en services.

U kunt een van de volgende populaire browsers downloaden en installeren:

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/en-us/edge)

Als u een andere browser gebruikt, dient u ervoor te zorgen dat deze ondersteuning biedt voor TLS 1.2.

Het besturingssysteem en de toepassingsframeworks moeten ook ondersteuning bieden voor TLS 1.2. Als de upgrade van uw browser het probleem niet verhelpt, controleert u of uw computer voldoet aan de systeemvereisten die worden vermeld in [Matrix voor cameracompatibiliteit](../../rn/using/compatibility-matrix.md).

## Veelgestelde vragen{#faq}

* **Wat is de Veiligheid van de Laag van het Vervoer (TLS)?**

  [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS) is een beveiligingsprotocol dat privacy en gegevensintegriteit biedt tussen twee communicerende toepassingen. Het wordt wijd opgesteld voor Webbrowsers en andere toepassingen die gegevens vereisen om veilig over een netwerk worden geruild.

  Volgens de protocolspecificatie omvat TLS twee lagen, het TLS Record-protocol en het TLS Handshake-protocol. Het protocol Record biedt verbindingsbeveiliging. Met het Handshake-protocol kunnen de server en client elkaar verifiëren en onderhandelen over versleutelingsalgoritmen en cryptografische sleutels voordat gegevens worden uitgewisseld.

* **Wat is de impact?**

  De veiligheidsnalevingsnormen van de Adobe vereisen dat oudere protocollen met ingang van mei 2018 worden afgeschaft en verplicht het gebruik van TLS 1.2 als de bijgewerkte versie. Als uw systeem niet compatibel is met TLS 1.2, is de toegang tot bepaalde Adobe-apps en -services beperkt.

* **Hoe beïnvloedt TLS u?**

  U kunt alleen bepaalde Adobe-apps en -services gebruiken via een beveiligde netwerkverbinding. TLS zorgt ervoor dat de verbinding tussen uw browser en deze apps en webservices veilig en betrouwbaar is.

  Wanneer nieuwe browsers en besturingssystemen worden uitgebracht, worden de beveiligingsstandaarden bijgewerkt om een hogere mate van privacy en gegevensintegriteit te garanderen. Oudere versies van deze browsers of het besturingssysteem worden echter niet bijgewerkt met de nieuwste standaarden.

  Aangezien het aanvaardbare niveau van veiligheid stijgt, worden deze oudere, minder veilige browser versies en toepassingen achtergelaten.

  Als u verbinding wilt maken met beveiligde sites, werkt u uw besturingssysteem- en browserversies bij.

* **Is TLS kwetsbaar voor hackers?**

  Er zijn gedocumenteerde aanvallen tegen TLS 1.0 geweest die een oudere encryptiemethode gebruiken en de oudere versies zijn kwetsbaarder dan TLS 1.2. Zie Aanvallen tegen TLS/SSL voor meer informatie.

* **Waarom schakelt de Adobe steun voor TLS 1.0 en 1.1 uit?**

  De Adobe heeft normen van de veiligheids naleving die het onbruikbaar maken steun voor oudere protocollen vereisen. Eén van deze standaarden zorgt voor compatibiliteit met de betaalkaartindustrie (PCI). De de aanpassingsserver van PCI is een reeks veiligheidsnormen vereist organisaties die, creditcardinformatie goedkeuren verwerken, opslaan of overbrengen om een veilige milieu te handhaven.

  PGB-compatibiliteit verplicht het gebruik van TLS 1.1 of hoger vanaf mei 2018.

* **Waarom verplicht de Adobe het gebruik van TLS 1.2 in plaats van TLS 1.1 of TLS 1.0 toe te staan?**

  De meeste aanvragen voor Adobe-apps en webservices zijn afkomstig van TLS 1.2-compatibele gebruikerssystemen, met weinig verkeer van TLS 1.1-systemen.

  De Adobe is gemigreerd naar TLS 1.2, zodat de toepassingen en webservices van de toepassing veiliger worden benaderd.

* **Wat is de laatste datum waarop ik een oudere versie van TLS kan gebruiken?**

  Adobe moedigt gebruikers aan om snel af te zien van de oudere versies om blootstelling aan veiligheidskwetsbaarheden te voorkomen. Neem voor meer informatie contact op met de klantenservice van de Adobe of met de succesmanager van de klant.

* **Welk foutenbericht verschijnt als ik browser gebruik die niet voor TLS 1.2 wordt gevormd?**

  Het hangt van browser af die u gebruikt. Alle browsers vermeld in [Matrix voor cameracompatibiliteit](../../rn/using/compatibility-matrix.md) zijn geconfigureerd voor het gebruik van TLS 1.2. Werk de browser bij als u een browser of versie gebruikt die niet in de lijst voorkomt.

  Adobe bestuurt geen foutenmeldingen die door de SSL communicatie laag worden geproduceerd. De browser genereert deze berichten voordat verbinding wordt gemaakt met Adobe-apps en -services. Hier volgt een voorbeeld van een fout die in Windows 7 kan optreden met Internet Explorer 11:

  ![](assets/do-not-translate/page-not-displayed.png)

  TLS 1.2 is standaard ingeschakeld in Internet Explorer 11, maar als deze optie is uitgeschakeld, kunt u deze inschakelen. In dit geval schakelt u TLS 1.2 uit het dialoogvenster Geavanceerde instellingen in plaats van andere opties te gebruiken. Andere fouten, zoals het volgende, kunnen ook voorkomen:

   * Kan geen verbinding maken met de service
   * Service niet beschikbaar
   * Fout in verbinding
