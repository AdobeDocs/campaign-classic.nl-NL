---
product: campaign
title: TechNote - Adobe Campaign-configuratieupdates
description: Adobe Campaign-configuratieupdates
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 8%

---

# Adobe Campaign-configuratie-updates 2021 {#acc-config-updates}



Infrastructuur en instellingen moeten regelmatig worden bijgewerkt met de nieuwste builds en productcorrecties. Deze fixes zijn noodzakelijk om continuïteit van de dienst en veiligheid te verzekeren. Daarnaast zijn upgrades vereist om deze uit te lijnen met wijzigingen van derden.

Als **Gehoste of Managed Services-klant**, zal de Adobe u van bouwstijlverbeteringen op regelmatige intervallen op de hoogte brengen. U moet een upgrade uitvoeren overeenkomstig de aanbevelingen om naleving te garanderen.

Als **Op locatie of hybride klant** dient u uw implementatie regelmatig bij te werken in overeenstemming met de meest recente versies van builds.

Om veiligheidsredenen moet u nu een upgrade uitvoeren naar een van de onderstaande versies. Naast de standaard upgradestappen moeten enkele handmatige taken worden uitgevoerd om ervoor te zorgen dat uw omgeving veilig is en klaar is voor toekomstige wijzigingen van Adobe- of externe systemen.

>[!NOTE]
>
>Voor vragen over deze wijzigingen neemt u contact op met de [Adobe-klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Beveiligingsupdates {#acc-security-updates}

De recentste versies van de Campagne komen met een veiligheidsmoeilijke situatie die bescherming tegen de kwesties van het Verzoek van de Server van de Zijde (SSRF) versterkt. Meer informatie vindt u [op deze pagina](https://helpx.adobe.com/nl/security/products/campaign/apsb21-04.html).

**Heeft dit gevolgen voor u?**

Als uw omgeving zich op een lagere build bevindt dan de hieronder vermelde, heeft dit gevolgen voor u:

* Gold Standard 11. [Meer informatie](../../rn/using/gold-standard.md)
* Release van campagne 21.1.1. [Meer informatie](../../rn/using/latest-release.md)
* Release van campagne 20.2.5.
* Release van campagne 20.1.4.
* Release van campagne 19.2.4.
* Release van campagne 19.1.8.

Leer hoe u uw versie kunt controleren [in deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hoe kan ik bijwerken?**

U moet een upgrade uitvoeren naar een van de nieuwere builds die hierboven worden vermeld.

* Als hybride klant, zal de Adobe u van de geplande verbeteringsdata voor uw midsourcing instanties op de hoogte brengen. Adobe raadt u ten zeerste aan ook uw marketingexemplaar te upgraden.

  De nieuwe build is achterwaarts compatibel met de release van Campaign Classic 17.9, maar Adobe raadt een upgrade van alle instanties sterk aan om beveiligingskwetsbaarheden te verhelpen

* Als klant op locatie wordt u gevraagd om marketing en media-sourcing te upgraden naar de nieuwste build.

>[!CAUTION]
>
>Als u niet binnen de aanbevolen periode kunt upgraden **u dient contact op te nemen met het klantenzorgteam van de Adobe om een handmatige beveiligingsoplossing voor de korte termijn toe te passen op uw instanties**.
>

## Update voor Campaign Classic-clientconsole  {#acc-cc-updates}

De **nu beschikbaar** consoleversies hieronder zouden moeten worden geïnstalleerd om een onlangs geïdentificeerde regressie op te lossen. Door deze regressie konden sommige componenten van de clientconsole niet worden gebruikt, zoals de datumkiezer en het beheer van afbeeldingen in leveringen. **Consoleupgrade** is verplicht.

* Nieuwste Gold Standard 11 build 9032@10c2709. [Meer informatie](../../rn/using/gold-standard.md)
* Release van campagne 20.1.4.
* Release van campagne 19.2.4.
* Release van campagne 19.1.8.

## Adobe Identity Management System (IMS)-update

De Dienst van de Identiteit van de Adobe (IMS) zal ophouden ondersteunend oude versies Internet Explorer van **30 juni 2021**. [Meer informatie](https://helpx.adobe.com/nl/x-productkb/global/update-operating-system-and-browser.html).

Een upgrade van de Campagne Client Console is vereist om compatibiliteit met Adobe IMS te garanderen.

**Heeft dit gevolgen voor u?**

Als u verbinding maakt met Campagne [via een Adobe ID](../../integrations/using/about-adobe-id.md)Via Adobe Identity Management Service (IMS) is een upgrade naar een van de onderstaande nieuwe versies verplicht:

* Gold Standard 11. [Meer informatie](../../rn/using/gold-standard.md)
* Release van campagne 21.1.1. [Meer informatie](../../rn/using/latest-release.md)
* Release van campagne 20.2.5.
* Release van campagne 20.1.4.
* Release van campagne 19.2.4.
* Release van campagne 19.1.8.

Deze versies worden geleverd met een nieuw verbindingsprotocol: een upgrade is verplicht voor zowel de campagneserver als de clientconsole om verbinding te kunnen maken met Campagne na **30 juni 2021**.

Leer hoe u uw versie kunt controleren [in deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hoe kan ik bijwerken?**

Als gehoste klant werkt Adobe samen met u om uw exemplaar(s) binnenkort te upgraden naar de nieuwere versie.

Als klant op locatie/hybride klant moet u een upgrade uitvoeren naar een van de nieuwere versies om te profiteren van de nieuwe clientconsole en een naadloze overgang te garanderen **vóór 30 juni 2021**.

Zodra alle instanties worden bevorderd, moet de Console van de Cliënt ook aan deze versie worden bevorderd.

* Meer informatie over toegang [Softwaredistributie Adoben](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=nl-NL).

* [Meer informatie over het installeren van Campagne Client Console](../../installation/using/installing-the-client-console.md).

## Integratie met Experience Cloud Triggers {#acc-triggers-updates}

De erfenis Auth authentificatiedienst heeft eind-van-leven bereikt. De de integratieauthentificatie van trekkers, oorspronkelijk gebaseerd op de authentificatie van AUTH om tot pijpleiding toegang te hebben, is bewogen aan Adobe I/O. Verouderde verificatiemodus voor auteur met campagne [is met pensioen](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) op **september 2021**. Gehoste omgevingen profiteren van een verlenging tot **23 februari 2022**. Als klant op locatie of hybride klant neemt u contact op met de klantenservice van de Adobe om de ondersteuning uit te breiden tot februari 2022. U moet de [AppID van de OAuth-applicatie](../../integrations/using/configuring-pipeline.md#step-optional) aan Adobe verstrekken.

**Heeft dit gevolgen voor u?**

Als uw instanties op een **oudere versie dan Campagne 19.1.8, 20.2.4, Gold Standard 11**, dan gebruikt u een oudere versie van de integratie van Trekkers door Authentificatie Auth: **moet u een upgrade uitvoeren naar een nieuwere versie en naar Adobe I/O gaan**.

U dient een upgrade uit te voeren naar een van de nieuwe versies die hieronder worden vermeld.

* Gold Standard 11. [Meer informatie](../../rn/using/gold-standard.md)
* Release van campagne 21.1.1. [Meer informatie](../../rn/using/latest-release.md)
* Release van campagne 20.2.5.
* Release van campagne 19.1.8.

Leer hoe u uw versie kunt controleren [in deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hoe kan ik bijwerken?**

Zodra de instanties aan een nieuwere versie worden bevorderd, moeten alle klanten volgen [de procedure gaat naar de nieuwe authentificatiemodus](../../integrations/using/about-triggers.md#implement). Hiervoor moet u het nieuwe Adobe I/O-token genereren en gebruiken in de implementatie.  

Bovendien moeten klanten voor hybride omgevingen ervoor zorgen dat de pijpleiding wordt geconfigureerd op een mid-sourcing-instantie. [Meer informatie](../../integrations/using/configuring-pipeline.md).

[Meer informatie over migreren naar Adobe I/O](../../integrations/using/about-triggers.md#implement).

## APNs-updates {#acc-apns-updates}

### API voor op HTTP/2 gebaseerde APNs-providers

Sinds **31 maart 2021**, steunt de dienst van het Bericht van de Duw van Apple (APNs) niet meer het oudere binaire protocol. [Meer informatie](https://developer.apple.com/news/?id=c88acm2b).

**Heeft u gevolgen?**

Als uw instanties op een **oudere versie dan Campagne 21.1,** en als u pushmeldingen verzendt met het oude binaire Apple-protocol, moet u de API voor de op HTTP/2 gebaseerde APNs-provider bijwerken.

Leer hoe u uw versie kunt controleren [in deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hoe kan ik bijwerken?**

Als gehoste klant, als u aan de nieuwe bouwstijl hebt bevorderd, heeft de Adobe reeds uw instantie(s) aan op HTTP/2-Gebaseerde API bijgewerkt.

Als klant op locatie/hybride klant moet u de configuratie bijwerken.

### Updates van APNs-basiscertificaten

Op 29 maart 2021 heeft een infrastructuurupdate van de Apple Push Notification Service (APNs) gevolgen voor het Adobe Campaign Classic iOS-kanaal. Een wijziging in de configuratie van het besturingssysteem is **verplicht** om uitval van het iOS-pushkanaal te voorkomen.

Meer informatie over APNs-wijzigingen [op deze pagina](https://developer.apple.com/news/?id=7gx0a2lp).

**Heeft dit gevolgen voor u?**

Als u campagne gebruikt om pushmeldingen te verzenden op iOS-apparaten, heeft dit gevolgen voor u.

**Hoe kan ik bijwerken?**

Als gehoste klant is geen actie nodig: Adobe heeft het nieuwe basiscertificaat al in uw omgeving opgenomen.

Als klant op locatie/hybride klant moet u uw configuratie bijwerken om een naadloze overgang te garanderen **vóór 29 maart 2021**.

[Meer informatie over het opnemen van het nieuwe certificaat](ios-certificate-update.md).

## Nuttige koppelingen

* [Upgrade uw omgeving](../../production/using/build-upgrade.md)
* [Veelgestelde vragen over buildupgrades](../../platform/using/faq-build-upgrade.md)
* [Build Campaign Classic downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [De nieuwe clientconsole beschikbaar maken voor gebruikers](../../installation/using/client-console-availability-for-windows.md)
