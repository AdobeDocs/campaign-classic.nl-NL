---
solution: Campaign Classic
product: campaign
title: TechNote
description: TechNote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 9b4b1bb5d016df8a7933ac0b96c6f110b0c4d7ac
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 7%

---


# Adobe Campaign-configuratieupdates - maart 2021 {#acc-config-updates}

U moet uw infrastructuur en instellingen bijwerken met de nieuwste builds en productoplossingen. Deze correcties zijn verplicht om de continuïteit en veiligheid van de service te waarborgen. Bovendien moet u uw implementatie aanpassen om zich aan derdeveranderingen aan te passen.

Als ontvangen klant, zal Adobe u van vereiste bouwstijlverbeteringen op regelmatige intervallen op de hoogte brengen. U moet een upgrade uitvoeren in overeenstemming met de aanbevelingen om naleving te garanderen.

Als klant op locatie/hybride dient u om beveiligingsredenen een upgrade uit te voeren naar een van de versies die op deze pagina worden vermeld. Daarnaast moeten enkele handmatige taken worden uitgevoerd om ervoor te zorgen dat uw omgeving veilig is en klaar is voor toekomstige wijzigingen van Adobe- of externe systemen.

>[!NOTE]
>
>Voor elke vraag over deze wijzigingen neemt u contact op met [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Beveiligingsupdates

De recentste versies van de Campagne komen met een veiligheidsmoeilijke situatie die bescherming tegen de kwesties van het Verzoek van de Server van de Zijde (SSRF) versterkt. Meer informatie [op deze pagina](https://helpx.adobe.com/nl/security/products/campaign/apsb21-04.html).

**Heb je invloed op?**

Als uw omgeving zich op een lagere build bevindt dan de hieronder vermelde, heeft dit gevolgen voor u:

* Gold Standard 11. [Meer informatie](../rn/using/gold-standard.md)
* Release van campagne 21.1.1. [Meer informatie](../rn/using/latest-release.md)
* Release van campagne 20.3.3. [Meer informatie](../rn/using/release--20-3.md)
* Release van campagne 20.2.4. [Meer informatie](../rn/using/release--20-2.md)
* Release van campagne 20.1.4. [Meer informatie](../rn/using/release--20-1.md)
* Release van campagne 19.2.4. [Meer informatie](../rn/using/release--19-2.md)
* Release van campagne 19.1.8. [Meer informatie](../rn/using/release--19-1.md)

**Hoe kan ik bijwerken?**

U moet een upgrade uitvoeren naar een van de nieuwere builds die hierboven worden vermeld.

* Als hybride klant, zal Adobe de marketing instantie aan de nieuwe versie bevorderen en u wordt hoogst geadviseerd om hun marketing instantie ook te bevorderen.

   De nieuwe build is compatibel met minstens versie Campaign Classic 17.9, maar om een eventuele veiligheidstekortkomingen te voorkomen, raadt Adobe u ten zeerste aan alle instanties te upgraden naar een nieuwe build. 

* Als klant op locatie wordt u gevraagd om marketing en media-sourcing te upgraden naar een nieuwere build.

>[!CAUTION]
>
>Als u momenteel geen upgrade kunt uitvoeren, moet u **contact opnemen met het team van de klantenservice van Adobe om handmatig een beveiligingscorrectie toe te passen op uw instanties**.


## Update voor clientconsole voor campagne

De nieuwste Gold Standard 11-build verhelpt een regressie die het gebruik van bepaalde componenten van de Client Console, zoals de datumkiezer en het beheer van afbeeldingen in leveringen, heeft verhinderd. Consoleupgrade is verplicht.

[Meer informatie](../rn/using/gold-standard.md).

>[!NOTE]
>
>Deze correctie is ook beschikbaar in de recentste [19.1.8](../rn/using/release--19-1.md#release-19-1-8-build-9039), [19.2.4](../rn/using/release--19-2.md#release-19-2-4-build-9082) en [20.1.4](../rn/using/release--20-1.md#release-20-1-4-build-9126).

## Adobe Identity Management System (IMS)-update

Adobe Identity Service (IMS) biedt geen ondersteuning meer voor oude Internet Explorer-versies vanaf **30 juni 2021**. [Meer informatie](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

De Campagne Client Console is bijgewerkt om verenigbaarheid met Adobe IMS te verzekeren.

**Heb je invloed op?**

Als u via een Adobe ID](../integrations/using/about-adobe-id.md) via Adobe Identity Management Service (IMS) verbinding maakt met Campagne, is een upgrade naar een van de onderstaande nieuwe versies verplicht:[

* Gold Standard 11. [Meer informatie](../rn/using/gold-standard.md)
* Release van campagne 21.1.1. [Meer informatie](../rn/using/latest-release.md)
* Release van campagne 20.3.3. [Meer informatie](../rn/using/release--20-3.md)
* Release van campagne 20.2.4. [Meer informatie](../rn/using/release--20-2.md)
* Release van campagne 20.1.4. [Meer informatie](../rn/using/release--20-1.md)
* Release van campagne 19.2.4. [Meer informatie](../rn/using/release--19-2.md)
* Release van campagne 19.1.8. [Meer informatie](../rn/using/release--19-1.md)

Deze versies worden geleverd met een nieuw verbindingsprotocol: De upgrade is verplicht voor zowel de Campagneserver als de Clientconsole om verbinding te kunnen maken met Campagne na **30 juni 2021**.

**Hoe kan ik bijwerken?**

Als gehoste klant is geen actie nodig: Adobe heeft uw exemplaar(s) al bijgewerkt naar een nieuwere versie.

Als klant op locatie/hybride klant moet u een upgrade uitvoeren naar een van de nieuwere versies om te profiteren van de nieuwe clientconsole en een naadloze overgang **garanderen voor 30 juni 2021**.

Zodra alle instanties worden bevorderd, moet de Console van de Cliënt ook aan deze versie worden bevorderd.

* Leer hoe te om tot [de Distributie van de Software van de Adobe toegang te hebben](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Leer hoe u de Campagne Client Console](../installation/using/installing-the-client-console.md) installeert.

## Integratie met Experience Cloud Triggers

De erfenis Auth authentificatiedienst heeft eind-van-leven bereikt. De de integratieauthentificatie van trekkers, oorspronkelijk gebaseerd op de authentificatie van AUTH om tot pijpleiding toegang te hebben, is bewogen aan Adobe I/O. Deze wordt op **30 november 2021** ingetrokken. [Meer informatie](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email).

**Heb je invloed op?**

Als uw instanties op een **oudere versie dan Campagne 19.1.8, 20.2.4, Gouden Standaard 11** lopen, dan gebruikt u een oudere versie van de integratie van Triggers door authentificatie Auth: **u moet een upgrade uitvoeren naar een nieuwere versie en overschakelen naar Adobe I/O**.

U moet een upgrade uitvoeren naar een van de nieuwe versies die hieronder worden vermeld.

* Gold Standard 11. [Meer informatie](../rn/using/gold-standard.md)
* Release van campagne 21.1.1. [Meer informatie](../rn/using/latest-release.md)
* Release van campagne 20.3.3. [Meer informatie](../rn/using/release--20-3.md)
* Release van campagne 20.2.4. [Meer informatie](../rn/using/release--20-2.md)
* Release van campagne 19.1.8. [Meer informatie](../rn/using/release--19-1.md)

**Hoe kan ik bijwerken?**

Als de exemplaren zijn bijgewerkt naar een nieuwere versie, moeten alle klanten de [procedure volgen en overschakelen naar de nieuwe verificatiemodus](../integrations/using/configuring-adobe-io.md). Dit vereist om het nieuwe teken van Adobe I/O te produceren en het in de implementatie te gebruiken.  

Bovendien moeten klanten voor hybride omgevingen ervoor zorgen dat de pijpleiding wordt geconfigureerd op een mid-sourcing-instantie. [Meer informatie](../integrations/using/configuring-pipeline.md).

[Leer hoe u naar Adobe I/O](../integrations/using/configuring-adobe-io.md) migreert.

## APNs-updates

### API voor op HTTP/2 gebaseerde APNs-providers

De Apple Push Notification service (APNs) biedt vanaf **31 maart 2021** geen ondersteuning meer voor het oudere binaire protocol. [Meer informatie](https://developer.apple.com/news/?id=c88acm2b).

**Heeft u gevolgen?**

Als uw instanties op een **oudere versie dan Campagne 21.1,** lopen en dupberichten met het erfenis binaire protocol van Apple verzenden, moet u aan de op HTTP/2-Gebaseerde leverancier API van APNs bijwerken.

**Hoe kan ik bijwerken?**

Als gehoste klant is geen actie nodig: Adobe heeft uw instantie(s) al bijgewerkt naar de op HTTP/2 gebaseerde API.

Als op-gebouw/ontvangen klant, moet u uw configuratie bijwerken. [Leer hoe u naar HTTP/2 kunt migreren](https://helpx.adobe.com/campaign/kb/migrate-to-apns-http2.html)

### Updates van APNs-basiscertificaten

Op 29 maart 2021 is een APN-infrastructuurupdate (Apple Push Notification service) van invloed op het Adobe Campaign Classic iOS-kanaal. Een wijziging in de configuratie van het besturingssysteem is **verplicht** om uitval van het iOS-pushkanaal te voorkomen.

Meer informatie over APNs verandert [op deze pagina](https://developer.apple.com/news/?id=7gx0a2lp).

**Heb je invloed op?**

Als u via Campagne pushmeldingen verzendt op iOS-apparaten, heeft dit gevolgen voor u.

**Hoe kan ik bijwerken?**

Als gehoste klant is geen actie nodig: Adobe heeft het nieuwe basiscertificaat al in uw omgeving opgenomen.

Als klant op locatie/hybride dient u uw configuratie bij te werken voor een naadloze overgang **vóór 29 maart 2021**.

[Leer hoe u het nieuwe certificaat](ios-certificate-update.md) invoegt.


## Nuttige koppelingen

* [Upgrade uw omgeving](../production/using/build-upgrade.md)
* [Veelgestelde vragen over upgrades samenstellen](../platform/using/faq-build-upgrade.md)
* [Campaign Classic-build downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [De nieuwe clientconsole beschikbaar maken voor gebruikers](../installation/using/client-console-availability-for-windows.md)
