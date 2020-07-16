---
title: Gold Standard-release
seo-title: Gold Standard-release
description: Gold Standard-release
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7ff58cee4b189c51fbff20880ac800d91f1b0147
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Gold Standard-release{#gold-standard}

Als gebruiker van de Gold Standard profiteert u automatisch van de Gold Standard-upgrade met de nieuwste stabiele versie zonder enige actie.

Op locatie en op Hybride klanten kunnen ook profiteren van de Gold Standard-releases.

Dit is onze supportrelease voor de lange termijn. Als u van een oude bouwstijl migreert, adviseren wij dat u eerst aan deze versie bevordert.

Deze pagina bevat de Gold Standard-releases.

Raadpleeg dit [artikel](https://helpx.adobe.com/campaign/kb/gold-standard.html)voor meer informatie over de Gold Standard-upgrade.

## ![](assets/do-not-localize/green_2.png) Gold Standard 10-release{#gs-10}

_7 juli 2020_

De build 9032@efd8a94 bevat de volgende oplossing:

* Probleem verholpen waarbij tracering niet werkte toen de handtekeningfunctie was uitgeschakeld. (NEO-26411)

>[!CAUTION]
>
>Wij adviseren dat u de cliëntconsole met beschikbaar in deze versie bevordert. Zie deze [pagina](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) Gold Standard 9-release{#gs-9}

_22 juni 2020_

De build 9032@800be2e bevat de volgende oplossingen:

* De iOS HTTP2-connector is verbeterd (updates van derden en foutbeheer). (NEO-25904, NEO-25903, NEO-25799)

De volgende oplossingen hebben betrekking op het beveiligingsmechanisme voor koppelingen bijhouden (zie de checklist [Beveiliging en Privacy](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)):

* Probleem verholpen waardoor het bijhouden van &#39;berichtklikken&#39; niet kon worden uitgevoerd (iOS- en Android-pushmeldingen). (NEO-25965)
* Probleem verholpen waardoor u URL&#39;s voor bijhouden niet kunt openen of erop kunt klikken wanneer u bepaalde oudere versies van Outlook gebruikt.  (NEO-25688)
* Probleem verholpen waarbij het bijhouden van URL&#39;s met fragmenten in personalisatieparameters (ankerlabels met hekje) niet werkte. (NEO-25774)
* Probleem verholpen met de antiphishingservice. (NEO-25283)
* Probleem met bijhouden opgelost bij het gebruik van specifieke aangepaste volgformules. (NEO-25277)

## ![](assets/do-not-localize/red_2.png) Gold Standard 8-release{#gs-8}

_29 april 2020_

De build 9032@3a9dc9c bevat de volgende oplossingen:

* Verbeterde beveiliging voor het bijhouden van koppelingen in e-mail. Dit is standaard ingeschakeld voor alle klanten. Er is een extra, verbeterde beveiligingsfunctie beschikbaar die kan worden ingeschakeld door de klantenservice te bereiken. Meer informatie over de functie en de stappen die niet-gehoste klanten moeten uitvoeren, vindt u in de checklist [voor](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)beveiliging en privacy.

>[!CAUTION]
>
>Als u problemen ondervindt met pushberichten via koppelingen voor reeksspatiëring of met ankerlabels voor leveringen, raden we u aan het nieuwe handtekeningmechanisme voor het bijhouden van koppelingen uit te schakelen. De procedure wordt in deze [pagina beschreven](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)

* Probleem verholpen waarbij afbeeldingen niet konden worden weergegeven bij levering op regel. (NEO-23207)
* Probleem verholpen met de **bestandsoverdrachtactiviteit** waardoor verificatie op basis van SFTP-sleutels niet kon werken op Debian 9. (NEO-23183)
* Probleem verholpen die invloed kan hebben op pushberichten wanneer deze op een hoge frequentie worden verzonden. (NEO-20516)
* Probleem verholpen in responsbeheer voor aanbiedingen die tot een vastlopen van de webserver kan leiden. (NEO-19482)
* Correctie van een fout in het beheer van LibreOffice waardoor u rapporten niet kon exporteren. (NEO-20982)
* Probleem verholpen dat een fout veroorzaakte bij het upgraden van een groot aantal workflows met behulp van een enquêteactiviteit.
* Verbeterd LibreOffice-beheer om fouten in de voorvertoning van e-mail met .odt-bestanden te voorkomen.
* Verbeterd beheer van Apache-verbinding om latentie op webservice te voorkomen.
* De weergave van versietag (7 cijfers) in het menu **Info** is verbeterd.
* Oplossing voor een regressie in lijstbeheer waardoor aanbiedingen niet konden worden gepubliceerd.
* Oplossing voor een regressie die ertoe leidde dat de opschoonworkflow vastliep.
* Oplossing voor een kleine regressie in de logboeken van de opschoonworkflow.

## ![](assets/do-not-localize/orange_2.png) Gold Standard 6-release{#gs-6}

_9 maart 2020_

De build 9032@19f73c5 bevat de volgende oplossing:

* Probleem met externe accounts met FTP via SSL opgelost. (NEO-20498)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 5-release{#gs-5}

_17 december 2019_

De build 9032@d6b8062 bevat de volgende oplossing:

* Probleem met bijhouden van gegevens op de volgende communicatiekanalen verholpen: mobiele (SMS, MMS), push (iOS, Android) en sociale netwerken (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 4-release{#gs-4}

_11 december 2019_

De build 9032@bc4a935 bevat de volgende oplossing:

* Oplossing voor een prestatieprobleem bij het verzenden van berichten met een MSSQL-database. (NEO-1758)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 3-release{#gs-3}

_20 november 2019_

De build 9032@3468c7b bevat de volgende oplossingen:

* Oplossing voor een aanmeldingsprobleem via IMS-verificatie. (NEO-17312)
* Probleem verholpen bij het weergeven van cumulatieve rapporten over meerdere leveringen. (NEO-18165)
* Probleem verholpen waarbij de webserver vastliep of kon blokkeren.

## ![](assets/do-not-localize/red_2.png) Gold Standard 2-release{#gs-2}

_19 september 2019_

De build 9032@cee805c bevat de volgende oplossingen:

* Probleem verholpen bij gebruik van de CRM-connector voor Salesforce. (NEO-17712)
* Probleem verholpen met een index die prestatieproblemen kan veroorzaken bij het verzenden van transactieberichten.

## ![](assets/do-not-localize/red_2.png) Release 19.1.4 - build 9032{#release-19-1-4-build-9032}

_13 augustus 2019_

De eerste build 19.1.4 bevat de volgende oplossingen:

* Oplossing voor een probleem met de planneractiviteit die ongewenste foutberichten tijdens de configuratie van de wizard genereerde. Bijwerken vanuit NEO-11662 wordt ongedaan gemaakt. (NEO-17097)
* Oplossing voor een regressie veroorzaakt door NEO-12727 die ertoe zou kunnen leiden dat werkstromen worden gestopt wanneer een testactiviteit tweemaal werd uitgevoerd. (NEO-16835)
* Probleem verholpen waarbij een onjuiste HTTP-code werd geretourneerd (HTTP 200 OK in plaats van HTTP 403 Verboden) wanneer een ongeldig of verlopen sessietoken werd gebruikt in API-aanroepen. (NEO-16826)
* Probleem verholpen met de DKIM-sleutel die niet meer in e-mails was ingesloten, waardoor problemen met de te leveren items ontstonden. (NEO-16804)
* Verschillende problemen met workflowplanning zijn opgelost. De werkschema&#39;s werden gepland om één keer per dag te worden uitgevoerd zonder rekening te houden met de plannerconfiguratie. (NEO-16619, NEO-16426)
