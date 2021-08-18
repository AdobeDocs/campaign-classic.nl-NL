---
product: campaign
title: TechNote
description: TechNote
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: 8e18a3633e6b806a971678d985c55c123854438e
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 11%

---

# Adobe Campaign-configuratieupdates - maart 2021 {#acc-config-updates}

Infrastructuur en instellingen moeten regelmatig worden bijgewerkt met de nieuwste builds en productcorrecties. Deze fixes zijn noodzakelijk om continuïteit van de dienst en veiligheid te verzekeren. Daarnaast zijn upgrades vereist om deze uit te lijnen met wijzigingen van derden.

Als **Gehoste of Managed Services klant**, zal Adobe u van bouwstijlverbeteringen op regelmatige intervallen op de hoogte brengen. U moet een upgrade uitvoeren overeenkomstig de aanbevelingen om naleving te garanderen.

Als **Op locatie of Hybride klant**, zou u uw implementatie met regelmatige intervallen in lijn met de recentste vrijgegeven bouwstijlen moeten bevorderen.

Om veiligheidsredenen moet u nu een upgrade uitvoeren naar een van de onderstaande versies. Naast de standaard upgradestappen moeten enkele handmatige taken worden uitgevoerd om ervoor te zorgen dat uw omgeving veilig is en klaar is voor toekomstige wijzigingen van Adobe- of externe systemen.

>[!NOTE]
>
>Voor vragen over deze wijzigingen neemt u contact op met de [Adobe-klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Beveiligingsupdates {#acc-security-updates}

De recentste versies van de Campagne komen met een veiligheidsmoeilijke situatie die bescherming tegen de kwesties van het Verzoek van de Server van de Zijde (SSRF) versterkt. Meer informatie vindt u [op deze pagina](https://helpx.adobe.com/nl/security/products/campaign/apsb21-04.html).

**Heeft dit gevolgen voor u?**

Als uw omgeving zich op een lagere build bevindt dan de hieronder vermelde, heeft dit gevolgen voor u:

* Gold Standard 11. [Meer informatie](../rn/using/gold-standard.md)
* Release van campagne 21.1.1. [Meer informatie](../rn/using/latest-release.md)
* Release van campagne 20.2.4. [Meer informatie](../rn/using/release--20-2.md)
* Release van campagne 20.1.4. [Meer informatie](../rn/using/release--20-1.md)
* Release van campagne 19.2.4. [Meer informatie](../rn/using/release--19-2.md)
* Release van campagne 19.1.8. [Meer informatie](../rn/using/release--19-1.md)

Leer hoe u uw versie [in deze sectie ](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) controleert.

**Hoe kan ik bijwerken?**

U moet een upgrade uitvoeren naar een van de nieuwere builds die hierboven worden vermeld.

* Als hybride klant, zal Adobe u van de geplande verbeteringsdata voor uw midsourcing instanties op de hoogte brengen. Adobe raadt u ten zeerste aan om ook een upgrade uit te voeren voor uw marketingexemplaar.

   De nieuwe build is achterwaarts compatibel met de release van Campaign Classic 17.9, maar Adobe raadt een upgrade van alle instanties aan om beveiligingskwetsbaarheden te verhelpen

* Als klant op locatie wordt u gevraagd om marketing en media-sourcing te upgraden naar de nieuwste build.

>[!CAUTION]
>
>Als u niet binnen de aanbevolen periode kunt upgraden, **dient u contact op te nemen met het team van de klantenservice van Adobe om een handmatige beveiligingsoplossing voor de korte termijn toe te passen op uw exemplaar**.


## Campaign Classic Client Console-update  {#acc-cc-updates}

De **nu beschikbare** consoleversies hieronder zouden moeten worden geïnstalleerd om een onlangs geïdentificeerde regressie op te lossen. Door deze regressie konden sommige componenten van de clientconsole niet worden gebruikt, zoals de datumkiezer en het beheer van afbeeldingen in leveringen. **Upgrade van console** is verplicht.

* Nieuwste Gold Standard 11 build 9032@10c2709. [Meer informatie](../rn/using/gold-standard.md)
* Release van campagne 20.1.4. [Meer informatie](../rn/using/release--20-1.md)
* Release van campagne 19.2.4. [Meer informatie](../rn/using/release--19-2.md)
* Release van campagne 19.1.8. [Meer informatie](../rn/using/release--19-1.md)

## Adobe Identity Management System (IMS)-update

Adobe Identity Service (IMS) biedt geen ondersteuning meer voor oude Internet Explorer-versies vanaf **30 juni 2021**. [Meer info](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Een upgrade van de Campagne Client Console is vereist om compatibiliteit met Adobe IMS te garanderen.

**Heeft dit gevolgen voor u?**

Als u via een Adobe ID](../integrations/using/about-adobe-id.md) via Adobe Identity Management Service (IMS) verbinding maakt met Campagne, is een upgrade naar een van de onderstaande nieuwe versies verplicht:[

* Gold Standard 11. [Meer informatie](../rn/using/gold-standard.md)
* Release van campagne 21.1.1. [Meer informatie](../rn/using/latest-release.md)
* Release van campagne 20.2.5. [Meer informatie](../rn/using/release--20-2.md)
* Release van campagne 20.1.4. [Meer informatie](../rn/using/release--20-1.md)
* Release van campagne 19.2.4. [Meer informatie](../rn/using/release--19-2.md)
* Release van campagne 19.1.8. [Meer informatie](../rn/using/release--19-1.md)

Deze versies worden geleverd met een nieuw verbindingsprotocol: De upgrade is verplicht voor zowel de Campagneserver als de Clientconsole om verbinding te kunnen maken met Campagne na **30 juni 2021**.

Leer hoe u uw versie [in deze sectie ](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) controleert.

**Hoe kan ik bijwerken?**

Als gehoste klant werkt Adobe binnenkort samen met u om uw exemplaar(s) bij te werken naar de nieuwere versie.

Als klant op locatie/hybride klant moet u een upgrade uitvoeren naar een van de nieuwere versies om te profiteren van de nieuwe clientconsole en een naadloze overgang **garanderen voor 30 juni 2021**.

Zodra alle instanties worden bevorderd, moet de Console van de Cliënt ook aan deze versie worden bevorderd.

* Leer hoe te om tot [de Distributie van de Software van de Adobe toegang te hebben](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Leer hoe u de Campagne Client Console](../installation/using/installing-the-client-console.md) installeert.

## Integratie met Experience Cloud Triggers {#acc-triggers-updates}

De erfenis Auth authentificatiedienst heeft eind-van-leven bereikt. De de integratieauthentificatie van trekkers, oorspronkelijk gebaseerd op de authentificatie van AUTH om tot pijpleiding toegang te hebben, is bewogen aan Adobe I/O. Deze wordt op **30 november 2021** ingetrokken. [Meer info](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email).

**Heeft dit gevolgen voor u?**

Als uw instanties op een **oudere versie dan Campagne 19.1.8, 20.2.4, Gouden Standaard 11** lopen, dan gebruikt u een oudere versie van de integratie van Triggers door authentificatie Auth: **u moet een upgrade uitvoeren naar een nieuwere versie en overschakelen naar Adobe I/O**.

U moet een upgrade uitvoeren naar een van de nieuwe versies die hieronder worden vermeld.

* Gold Standard 11. [Meer informatie](../rn/using/gold-standard.md)
* Release van campagne 21.1.1. [Meer informatie](../rn/using/latest-release.md)
* Release van campagne 20.2.5. [Meer informatie](../rn/using/release--20-2.md)
* Release van campagne 19.1.8. [Meer informatie](../rn/using/release--19-1.md)

Leer hoe u uw versie [in deze sectie ](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) controleert.

**Hoe kan ik bijwerken?**

Als de exemplaren zijn bijgewerkt naar een nieuwere versie, moeten alle klanten de [procedure volgen en overschakelen naar de nieuwe verificatiemodus](../integrations/using/configuring-adobe-io.md). Dit vereist u om het nieuwe teken van Adobe I/O te produceren en het in de implementatie te gebruiken.  

Bovendien moeten klanten voor hybride omgevingen ervoor zorgen dat de pijpleiding wordt geconfigureerd op een mid-sourcing-instantie. [Meer info](../integrations/using/configuring-pipeline.md).

[Leer hoe u naar Adobe I/O](../integrations/using/configuring-adobe-io.md) migreert.

## APNs-updates {#acc-apns-updates}

### API voor op HTTP/2 gebaseerde APNs-providers

Sinds **31 Maart, 2021**, steunt de dienst van het Bericht van de Push van Apple (APNs) niet meer het erfenis binaire protocol. [Meer informatie](https://developer.apple.com/news/?id=c88acm2b).

**Heeft u gevolgen?**

Als uw instanties op een **oudere versie dan Campagne 21.1,** lopen en u dupberichten met het erfenis binaire protocol van Apple verzendt, moet u aan de op HTTP/2-Gebaseerde leverancier API van APNs bijwerken.

Leer hoe u uw versie [in deze sectie ](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) controleert.

**Hoe kan ik bijwerken?**

Als gehoste klant, als u aan de nieuwe bouwstijl hebt bevorderd, heeft Adobe reeds uw instantie(s) aan op HTTP/2-Gebaseerde API bijgewerkt.

Als klant op locatie/hybride klant moet u de configuratie bijwerken. [Leer hoe u naar HTTP/2 kunt migreren](https://helpx.adobe.com/nl/campaign/kb/migrate-to-apns-http2.html)

### Updates van APNs-basiscertificaten

Op 29 maart 2021 heeft een APN-infrastructuurupdate (Apple Push Notification service) invloed op het Adobe Campaign Classic iOS-kanaal. Een wijziging in de configuratie van het besturingssysteem is **verplicht** om uitval van het iOS-pushkanaal te voorkomen.

Meer informatie over APNs verandert [op deze pagina](https://developer.apple.com/news/?id=7gx0a2lp).

**Heeft dit gevolgen voor u?**

Als u via Campagne pushmeldingen verzendt op iOS-apparaten, heeft dit gevolgen voor u.

**Hoe kan ik bijwerken?**

Als gehoste klant is geen actie nodig: Adobe heeft het nieuwe basiscertificaat al in uw omgeving opgenomen.

Als klant op locatie/hybride dient u uw configuratie bij te werken voor een naadloze overgang **vóór 29 maart 2021**.

[Leer hoe u het nieuwe certificaat](ios-certificate-update.md) invoegt.

## Nuttige koppelingen

* [Upgrade uw omgeving](../production/using/build-upgrade.md)
* [Veelgestelde vragen over buildupgrades](../platform/using/faq-build-upgrade.md)
* [Campaign Classic-build downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [De nieuwe clientconsole beschikbaar maken voor gebruikers](../installation/using/client-console-availability-for-windows.md)
