---
solution: Campaign Classic
product: campaign
title: TechNote
description: TechNote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 87844fae046dff69193d3462c802057499f406ef
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 5%

---


# Adobe Campaign-configuratieupdates - maart 2021 {#acc-config-updates}

U moet uw infrastructuur en instellingen up-to-date houden met de nieuwste builds en productoplossingen. Deze correcties zijn verplicht om de continuïteit en veiligheid van de service te waarborgen.

Campagnegebruikers moeten een upgrade uitvoeren naar een van de nieuwste versies hieronder:

* Gold Standard 11. [Meer informatie](../rn/using/gold-standard.md)
* Release van campagne 21.1.1. [Meer informatie](../rn/using/latest-release.md)
* Release van campagne 20.3.3. [Meer informatie](../rn/using/release--20-3.md)
* Release van campagne 20.2.4. [Meer informatie](../rn/using/release--20-2.md)
* Release van campagne 20.1.4. [Meer informatie](../rn/using/release--20-1.md)
* Release van campagne 19.2.4. [Meer informatie](../rn/using/release--19-2.md)
* Release van campagne 19.1.8. [Meer informatie](../rn/using/release--19-1.md)

Deze gebouwen zorgen voor de continuïteit van bepaalde campagnediensten: Experience Cloud brengt integratie, APNs authentificatie en het nieuwe verbindingsprotocol teweeg dat Adobe Identity Management Service (IMS) authentificatiemechanisme beïnvloedt.

Als gehoste klant is geen actie nodig: Adobe bezit de bouwstijlverbetering en configuratieupdates voor u.

Als klant op locatie/hybride klant moet u een upgrade uitvoeren naar een van de hierboven vermelde versies. Bovendien moet u een aantal handmatige taken uitvoeren om ervoor te zorgen dat uw omgeving veilig is en klaar is voor toekomstige wijzigingen van Adobe- of andere systemen.

## Beveiligingsupdates

De recentste versies van de Campagne komen met een veiligheidsmoeilijke situatie die bescherming tegen de kwesties van het Verzoek van de Server van de Zijde (SSRF) versterkt. Meer informatie [op deze pagina](https://helpx.adobe.com/nl/security/products/campaign/apsb21-04.html).

**Heb je invloed op?**

Als uw omgeving zich op een lagere build bevindt dan Campagne 21.1, heeft dit gevolgen voor u.

**Hoe kan ik bijwerken?**

U moet een upgrade uitvoeren naar een van de nieuwere builds die hierboven worden vermeld.

* Als hybride klant zal Adobe de mid-sourcing instantie aan de nieuwe versie bevorderen en u wordt hoogst geadviseerd om hun marketing instantie ook te bevorderen.

   De nieuwe bouwstijl is compatibel met minstens versie Campaign Classic 17.9, maar om om het even welk veiligheidstekort te verhinderen, adviseert Adobe sterk om alle instanties aan een nieuwe bouwstijl te bevorderen. 

* Als klant op locatie, wordt u gevraagd om marketing- en midsourcinginstanties te upgraden naar een nieuwe build.

>[!CAUTION]
>
>Als u momenteel geen upgrade kunt uitvoeren, moet u **contact opnemen met het Adobe-team van de klantenservice om een beveiligingscorrectie op uw exemplaren handmatig toe te passen**.


## Update voor clientconsole voor campagne

De nieuwste Gold Standard 11-build verhelpt een regressie die het gebruik van bepaalde componenten van de console, zoals de datumkiezer en het beheer van afbeeldingen in leveringen, heeft verhinderd. Consoleupgrade is verplicht.

[Meer informatie](../rn/using/gold-standard.md).

## Verbinding maken met Campagne via IMS

Met ingang van 30 juni 2021 zal de Adobe Identity Service (IMS) stoppen met het ondersteunen van de oude Internet Explorer-versies. [Meer informatie](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html). De Campagne Console is bijgewerkt om verenigbaarheid met IMS te verzekeren.

**Heb je invloed op?**

Als u via een Adobe ID](../integrations/using/about-adobe-id.md) verbinding maakt met Campagne via de Adobe Identity Service (IMS), is een upgrade naar een van de hierboven vermelde nieuwe versies verplicht, zodat zowel de Campagneserver als de clientconsole verbinding kunnen maken met Campagne na **30 juni 2021**.[

**Hoe kan ik bijwerken?**

Als gehoste klant is geen actie nodig: Adobe heeft uw exemplaar(s) al bijgewerkt naar een nieuwere versie.

Als klant op locatie/hybride dient u een upgrade uit te voeren naar een van de nieuwere versies om te profiteren van de nieuwe clientconsole en een naadloze overgang **vóór 31 maart 2021** te garanderen.

## Integratie met Experience Cloud Triggers

De erfenis Auth-authenticatiedienst heeft het einde van de levensduur bereikt en zal op 30 juni 2021 met pensioen gaan. [Meer informatie](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411).

**Heb je invloed op?**

Als u een oudere versie van de integratie van Trekkers door authentificatie Auth gebruikt, **moet u naar Adobe I/O** bewegen.

**Hoe kan ik bijwerken?**

[Leer hoe u naar Adobe I/O](../integrations/using/configuring-adobe-io.md) migreert.

## API voor op HTTP/2 gebaseerde APNs-providers

De Apple Push Notification service (APNs) biedt vanaf 31 maart 2021 geen ondersteuning meer voor het binaire oudere protocol. [Meer informatie](https://developer.apple.com/news/?id=c88acm2b).

**Heeft u gevolgen?**

Als uw instanties op een oudere versie dan Campagne 21.1 lopen, en dupberichten met het erfenis binaire protocol van Apple verzenden, moet u aan de op HTTP/2-Gebaseerde leverancier API bijwerken.

**Hoe kan ik bijwerken?**

Als gehoste klant is geen actie nodig: Adobe heeft uw instantie(s) al bijgewerkt naar de op HTTP/2 gebaseerde API.

Als op-gebouw/ontvangen klant, moet u uw configuratie bijwerken. [Leer hoe u naar HTTP/2 kunt migreren](https://helpx.adobe.com/campaign/kb/migrate-to-apns-http2.html)

## Updates van APNs-basiscertificaten

Op 29 maart 2021 is een APN-infrastructuurupdate (Apple Push Notification service) van invloed op het Adobe Campaign Classic iOS-kanaal. Een wijziging in de configuratie van het besturingssysteem is **verplicht** om uitval van het iOS-pushkanaal te voorkomen.

Meer informatie over APNs verandert [op deze pagina](https://developer.apple.com/news/?id=7gx0a2lp).

**Heb je invloed op?**

Als u via Campagne pushmeldingen verzendt op iOS-apparaten, heeft dit gevolgen voor u.

**Hoe kan ik bijwerken?**

Als gehoste klant is geen actie nodig: Adobe heeft het nieuwe basiscertificaat al in uw omgeving opgenomen.

Als klant op locatie/hybride dient u uw configuratie bij te werken voor een naadloze overgang **vóór 29 maart 2021**.

[Meer informatie over het opnemen van het nieuwe certificaat](ios-certificate-update.md)
