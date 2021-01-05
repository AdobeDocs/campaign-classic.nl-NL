---
solution: Campaign Classic
product: campaign
title: Gold Standard-release
description: Opmerkingen bij de release van Campaign Classic Gold Standard
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 802818fcd27e0dc40cc640092da1ef70ff21a191
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 86%

---


# Gold Standard-releases{#gold-standard}

Gold Standard is de ondersteuningsrelease van Campaign Classic voor de lange termijn. Als gehoste gebruiker van de Gold Standard profiteert u automatisch van de Gold Standard-upgrade met de nieuwste stabiele versie zonder enige actie. Klanten op locatie en Hybride kunnen ook profiteren van Gold Standard-releases.

Als u van een oude bouwstijl migreert, adviseren wij dat u aan deze versie eerst bevordert.

Deze pagina vermeldt de Gold Standard-releases.

Raadpleeg [dit artikel](https://helpx.adobe.com/nl/campaign/kb/gold-standard.html)voor meer informatie over het Campaign Gold Standard-programma.

## ![](assets/do-not-localize/limited_2.png) De Gold Standard 11-release{#gs-11}

_22 december 2020_

>[!CAUTION]
>
>Deze versie wordt geleverd met een nieuw verbindingsprotocol: De upgrade is verplicht voor zowel de campagneserver als de clientconsole om verbinding te kunnen maken met Campagne na 21 maart 2021.

De build 9032@2a2a028 bevat de volgende verbeteringen en oplossingen:

* Het verbindingsprotocol is bijgewerkt en aangepast aan het nieuwe IMS-verificatiemechanisme.

* De Triggers-integratieverificatie die oorspronkelijk was gebaseerd op de oAUTH-verificatieset-up voor toegang tot de pipeline is nu gewijzigd en verplaatst naar Adobe I/O. [Meer informatie](../../integrations/using/configuring-adobe-io.md)

* Na het einde van de ondersteuning voor het oudere binaire protocol voor iOS APNs worden alle instanties die dit protocol gebruiken bijgewerkt naar het HTTP/2-protocol tijdens de postupgrade.

* Oplossing voor een beveiligingsprobleem dat de beveiliging tegen SSRF-problemen (Server Side Request Smeery) moet versterken. (NEO-27777)

## ![](assets/do-not-localize/green_2.png) De Gold Standard 10-release{#gs-10}

_7 juli 2020_

De build 9032@efd8a94 bevat de volgende oplossing:

Er is een probleem verholpen waarbij tracking niet werkte als de handtekeningfunctie was uitgeschakeld. (NEO-26411)

>[!CAUTION]
>
>Wij adviseren u de clientconsole bij te werken met de beschikbare console in deze release. Zie [deze pagina](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) De Gold Standard 9-release{#gs-9}

_22 juni 2020_

De build 9032@800be2e bevat de volgende oplossingen:

* De iOS HTTP2-connector is verbeterd (updates van derden en foutbeheer). (NEO-25904, NEO-25903, NEO-25799)

De volgende correcties betreffen het beveiligingsmechanisme voor koppelingen bijhouden (meer informatie vindt u in de [checklist voor beveiliging en privacy](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)):

* Er is een probleem verholpen waardoor tracking van ‘berichtklikken’ niet kon worden uitgevoerd (iOS- en Android-pushmeldingen). (NEO-25965)
* Er is een probleem verholpen waardoor u tracking-URL’s niet kon openen of er niet op kon klikken bij gebruik van bepaalde oudere versies van Outlook. (NEO-25688)
* Er is een probleem verholpen waarbij de tracking van URL’s met fragmenten in personalisatieparameters (ankerlabels met pondteken) niet werkte. (NEO-25774)
* Er is een probleem verholpen met de antiphishingservice. (NEO-25283)
* Er is een probleem verholpen met tracking bij gebruik van specifieke aangepaste trackingformules. (NEO-25277)

## ![](assets/do-not-localize/red_2.png) De Gold Standard 8-release{#gs-8}

_29 april 2020_

De build 9032@3a9dc9c bevat de volgende oplossingen:

* Verbeterde beveiliging voor tracking van koppelingen in e-mails. Dit is standaard ingeschakeld voor alle klanten. Er is een extra, verbeterde beveiligingsfunctie beschikbaar die kan worden ingeschakeld door contact op te nemen met de klantenservice. Meer informatie over de functie en de stappen die niet-gehoste klanten moeten uitvoeren, vindt u in de [Controlelijst voor beveiliging en privacy](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Als u problemen hebt met pushmeldingen via trackingkoppelingen, of leveringen die ankerlabels gebruiken, raden we u aan het nieuwe handtekeningmechanisme voor tracking van koppelingen uit te schakelen. De procedure wordt [op deze pagina](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism) nader beschreven

* Er is een probleem verholpen waarbij afbeeldingen niet konden worden weergegeven in Line-leveringen. (NEO-23207)
* Probleem verholpen met de activiteit **Bestand overdragen** waardoor verificatie op basis van SFTP-sleutels niet kon werken op Debian 9. (NEO-23183)
* Er is een probleem verholpen in verband met pushmeldingen wanneer deze op een hoge frequentie werden verzonden. (NEO-20516)
* Er is een probleem verholpen in responsbeheer voor aanbiedingen waardoor de webserver kon vastlopen. (NEO-19482)
* Er is een fout verholpen in het beheer van LibreOffice waardoor u rapporten niet kon exporteren. (NEO-20982)
* Er is een probleem verholpen dat een fout veroorzaakte bij het upgraden van een groot aantal workflows via een enquêteactiviteit.
* LibreOffice-beheer is verbeterd om fouten in de voorvertoning van e-mails met .odt-bestanden te voorkomen.
* Beheer van de Apache-verbinding is verbeterd om latentie op de webservice te voorkomen.
* De weergave van versietags (7 cijfers) in het menu **Info** is verbeterd.
* Er is een regressie verholpen in lijstbeheer waardoor aanbiedingen niet konden worden gepubliceerd.
* Oplossing voor een regressie die ertoe leidde dat de opschoningsworkflow vastliep.
* Oplossing voor een kleine regressie in de logboeken van de opschoningsworkflow.

## ![](assets/do-not-localize/red_2.png) De Gold Standard 6-release{#gs-6}

_9 maart 2020_

De build 9032@19f73c5 bevat de volgende oplossing:

* Probleem met externe accounts met FTP via SSL opgelost. (NEO-20498)

## ![](assets/do-not-localize/red_2.png) De Gold Standard 5-release{#gs-5}

_17 december 2019_

De build 9032@d6b8062 bevat de volgende oplossing:

* Er is een trackingprobleem verholpen op de volgende communicatiekanalen: mobiel (sms, mms), push (iOS, Android) en sociale netwerken (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/red_2.png) De Gold Standard 4-release{#gs-4}

_11 december 2019_

De build 9032@bc4a935 bevat de volgende oplossing:

* Er is een prestatieprobleem verholpen met het verzenden van berichten met een MSSQL-database. (NEO-17558)

## ![](assets/do-not-localize/red_2.png) De Gold Standard 3-release{#gs-3}

_20 november 2019_

De build 9032@3468c7b bevat de volgende oplossingen:

* Er is een aanmeldingsprobleem via IMS-verificatie verholpen. (NEO-17312)
* Er is een probleem verholpen met het weergeven van cumulatieve rapporten over meerdere leveringen. (NEO-18165)
* Er is een probleem verholpen waarbij de webserver geblokkeerd kon raken of vastlopen.

## ![](assets/do-not-localize/red_2.png) De Gold Standard 2-release{#gs-2}

_19 september 2019_

De build 9032@cee805c bevat de volgende oplossingen:

* Er is een probleem verholpen met het gebruik van de CRM-connector voor Salesforce. (NEO-17712)
* Er is een indexprobleem verholpen dat prestatieproblemen kon veroorzaken bij het verzenden van transactieberichten.

## ![](assets/do-not-localize/red_2.png) Release 19.1.4 - build 9032{#release-19-1-4-build-9032}

_13 augustus 2019_

De eerste 19.1.4-build bevat de volgende oplossingen:

* Er is een probleem verholpen met de planneractiviteit die ongewenste foutberichten genereerde tijdens de configuratie van de wizard. Update van NEO-11662 is teruggedraaid. (NEO-17097)
* Er is een regressie verholpen die werd veroorzaakt door NEO-12727 en die kon leiden tot het stoppen van workflows als een Test-activiteit tweemaal werd uitgevoerd. (NEO-16835)
* Er is een probleem verholpen waardoor een onjuiste HTTP-code werd geretourneerd (HTTP 200 OK in plaats van HTTP 403 Verboden) wanneer een ongeldig of verlopen sessietoken werd gebruikt in API-aanroepen. (NEO-16826)
* Er is een probleem verholpen met de DKIM-sleutel die niet meer in e-mails werd ingesloten, waardoor leveringsproblemen ontstonden. (NEO-16804)
* Er zijn diverse problemen met workflowplanning verholpen. Workflows werden gepland om één keer per dag te worden uitgevoerd zonder rekening te houden met de plannerconfiguratie. (NEO-16619, NEO-16426)
