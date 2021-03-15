---
solution: Campaign Classic
product: campaign
title: TechNote
description: TechNote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: c9e3d12f8975b2c87f6f4aaf306fae71803786ad
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 4%

---


# Adobe Campaign-configuratieupdates - maart 2021 {#acc-config-updates}

U moet uw infrastructuur en instellingen bijwerken met de nieuwste builds en productoplossingen. Deze correcties zijn verplicht om de continuïteit en veiligheid van de service te waarborgen.

Campagnegebruikers moeten een upgrade uitvoeren naar een van de recentste versies hieronder:

* Gold Standard 11. [Meer informatie](../rn/using/gold-standard.md)
* Release van campagne 21.1.1. [Meer informatie](../rn/using/latest-release.md)
* Release van campagne 20.3.3. [Meer informatie](../rn/using/release--20-3.md)
* Release van campagne 20.2.4. [Meer informatie](../rn/using/release--20-2.md)
* Release van campagne 20.1.4. [Meer informatie](../rn/using/release--20-1.md)
* Release van campagne 19.2.4. [Meer informatie](../rn/using/release--19-2.md)
* Release van campagne 19.1.8. [Meer informatie](../rn/using/release--19-1.md)

Deze gebouwen zorgen voor de continuïteit van bepaalde campagnediensten: Experience Cloud brengt integratie, APNs authentificatie en het nieuwe verbindingsprotocol teweeg dat Adobe Identity Management Service (IMS) authentificatiemechanisme beïnvloedt.

Als ontvangen klant, zal Adobe u van vereiste bouwstijlverbeteringen op regelmatige intervallen op de hoogte brengen. U moet een upgrade uitvoeren in overeenstemming met de aanbevelingen om naleving te garanderen.

Als klant op locatie/hybride klant moet u een upgrade uitvoeren naar een van de hierboven vermelde versies. Daarnaast moeten enkele handmatige taken worden uitgevoerd om ervoor te zorgen dat uw omgeving veilig is en klaar is voor toekomstige wijzigingen van Adobe- of externe systemen.

>[!NOTE]
>
>Voor elke vraag over deze wijzigingen neemt u contact op met [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Beveiligingsupdates

De recentste versies van de Campagne komen met een veiligheidsmoeilijke situatie die bescherming tegen de kwesties van het Verzoek van de Server van de Zijde (SSRF) versterkt. Meer informatie [op deze pagina](https://helpx.adobe.com/nl/security/products/campaign/apsb21-04.html).

**Heb je invloed op?**

Als uw omgeving zich op een lagere build bevindt dan Campagne 19.1.8, 19.2.4, 20.1.4, 20.2.4, 20.3.3 of Gold Standard 11, heeft dit gevolgen voor u.

**Hoe kan ik bijwerken?**

U moet een upgrade uitvoeren naar een van de nieuwere builds die hierboven worden vermeld.

* Als hybride klant zal Adobe de mid-sourcing instantie aan de nieuwe versie bevorderen en u wordt hoogst geadviseerd om hun marketing instantie ook te bevorderen.

   De nieuwe build is compatibel met minstens versie Campaign Classic 17.9, maar om een eventuele veiligheidstekortkomingen te voorkomen, raadt Adobe u ten zeerste aan alle instanties te upgraden naar een nieuwe build. 

* Als klant op locatie wordt u gevraagd om marketing en media-sourcing te upgraden naar een nieuwere build.

>[!CAUTION]
>
>Als u momenteel geen upgrade kunt uitvoeren, moet u **contact opnemen met het team van de klantenservice van Adobe om handmatig een beveiligingscorrectie toe te passen op uw instanties**.


## Update voor clientconsole voor campagne

De nieuwste Gold Standard 11-build verhelpt een regressie die het gebruik van bepaalde componenten van de console, zoals de datumkiezer en het beheer van afbeeldingen in leveringen, heeft verhinderd. Consoleupgrade is verplicht.

[Meer informatie](../rn/using/gold-standard.md).


>[!NOTE]
>
>Updates voor andere versies zijn binnenkort beschikbaar.

## Verbinding maken met Campagne via IMS

Met ingang van 30 juni 2021 zal de Adobe Identity Service (IMS) stoppen met het ondersteunen van de oude Internet Explorer-versies. [Meer informatie](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html). De Campagne Console is bijgewerkt om verenigbaarheid met IMS te verzekeren.

**Heb je invloed op?**

Als u via een Adobe ID](../integrations/using/about-adobe-id.md) via de Adobe Identity Service (IMS) verbinding maakt met Campagne [is een upgrade naar een van de hierboven vermelde nieuwe versies verplicht. Deze versies worden geleverd met een nieuw verbindingsprotocol: een upgrade is verplicht, zodat zowel de Campagneserver als de clientconsole verbinding kunnen maken met Campagne na **30 juni 2021**.

**Hoe kan ik bijwerken?**

Als gehoste klant is geen actie nodig: Adobe heeft uw exemplaar(s) al bijgewerkt naar een nieuwere versie.

Als klant op locatie/hybride klant moet u een upgrade uitvoeren naar een van de nieuwere versies om te profiteren van de nieuwe clientconsole en een naadloze overgang **garanderen voor 30 juni 2021**.

Zodra alle instanties worden bevorderd, moet de cliëntconsole ook aan deze versie worden bevorderd.

* Leer hoe te om tot [de Distributie van de Software van de Adobe toegang te hebben](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Leer hoe u de Campagne Client Console](../installation/using/installing-the-client-console.md) installeert.

## Integratie met Experience Cloud Triggers

De erfenis Auth authentificatiedienst heeft eind-van-leven bereikt. De de integratieauthentificatie van trekkers, oorspronkelijk gebaseerd op de authentificatie van AUTH om tot pijpleiding toegang te hebben, is bewogen aan Adobe I/O. Deze wordt ingetrokken op **30 april 2021**. [Meer informatie](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411).

**Heb je invloed op?**

Als uw omgeving zich op een lagere build bevindt dan Campagne 19.1.8, 20.2.4, Gold Standard 11, gebruikt u een oudere versie van Triggers-integratie via Auth-verificatie: **u moet naar Adobe I/O** bewegen.

**Hoe kan ik bijwerken?**

Als de exemplaren zijn bijgewerkt naar een nieuwere versie, moeten alle klanten de [procedure volgen en overschakelen naar de nieuwe verificatiemodus](../integrations/using/configuring-adobe-io.md). Dit vereist om het nieuwe teken van Adobe I/O te produceren en het in de implementatie te gebruiken.  

Bovendien moeten klanten voor hybride omgevingen ervoor zorgen dat de pijpleiding wordt geconfigureerd op een mid-sourcing-instantie. [Meer informatie](../integrations/using/configuring-pipeline.md).

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

[Leer hoe u het nieuwe certificaat](ios-certificate-update.md) invoegt.
