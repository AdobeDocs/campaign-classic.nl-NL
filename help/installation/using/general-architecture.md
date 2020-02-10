---
title: Algemene architectuur
seo-title: Algemene architectuur
description: Algemene architectuur
seo-description: null
page-status-flag: never-activated
uuid: 686bc660-2403-4bab-a4ea-9b872adf8fa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 7c28c179-eb18-437e-baf2-25829566c766
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Algemene architectuur{#general-architecture}

De gebruikelijke implementatie van de Adobe Campaign-oplossing bestaat uit de volgende onderdelen:

* **Persoonlijke clientomgeving**

   Intuïtieve grafische interface waarin gebruikers marketingaanbiedingen kunnen communiceren en volgen, campagnes kunnen maken, alle marketingactiviteiten, programma&#39;s en plannen (inclusief e-mails, workflows en bestemmingspagina&#39;s) kunnen beoordelen en beheren, klantprofielen kunnen maken en beheren en klantsoorten kunnen definiëren.

* **Ontwikkelingsomgeving**

   Server-side software die de marketing campagnes door gekozen communicatie kanalen, met inbegrip van e-mail, SMS, dupberichten, direct mail, Web of sociaal uitvoert, op de regels en de werkschema&#39;s die in het gebruikersinterface worden bepaald.

* **Databasecontainers**

   Op basis van relationele databasetechnologie slaat de Adobe Campagne-database alle klantgegevens, campagnecomponenten, aanbiedingen en workflows op, evenals de resultaten van de campagne in de databasecontainers van de klant.

De Campagne van Adobe is gebaseerd op een dienst-georiënteerde architectuur (SOA) en omvat verscheidene functionele modules. Deze modules kunnen op één of meerdere computers, in enige of veelvoudige instanties, afhankelijk van beperkingen in termen van scalability, beschikbaarheid en de dienstisolatie worden opgesteld. Het werkingsgebied van plaatsingsconfiguraties is daarom zeer breed, en overspant één enkele, centrale computer door aan configuraties met inbegrip van veelvoudige specifieke servers over veelvoudige plaatsen.

>[!NOTE]
>
>Als softwareleverancier specificeren wij compatibele hardware en softwareinfrastructuur. De hardwareaanbevelingen die hier worden gegeven, dienen uitsluitend ter informatie en zijn gebaseerd op onze ervaring. Adobe is niet aansprakelijk voor besluiten die op basis daarvan worden genomen. Het zal ook van uw bedrijfsregels en praktijken en de kritiek en vereiste prestatiesniveaus van het project afhangen.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Tenzij uitdrukkelijk anders vermeld, vallen de installatie, updates en onderhoud op alle componenten van een Adobe Campagneplatform onder de verantwoordelijkheid van de systeembeheerder(s) die de componenten host. Dit omvat het implementeren van de voorwaarden voor Adobe Campagne-toepassingen en het naleven van de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) tussen componenten.

## Presentatielaag {#presentation-layer}

De toepassing kan op verschillende manieren worden benaderd, afhankelijk van de behoeften van de gebruikers: Rich client-, thin client- of API-integratie.

* **Rijke client**: De hoofdgebruikersinterface van de toepassing is een rijke client, met andere woorden een native toepassing (Windows) die alleen communiceert met de Adobe Campagne-toepassingsserver met standaard internetprotocollen (SOAP, HTTP, enzovoort). Deze console biedt grote gebruiksvriendelijkheid voor productiviteit, gebruikt zeer weinig bandbreedte (door het gebruik van een lokale cache) en is ontworpen voor eenvoudige implementatie. Deze console kan vanuit een internetbrowser worden geïmplementeerd, kan automatisch worden bijgewerkt en vereist geen specifieke netwerkconfiguratie omdat alleen HTTP(S)-verkeer wordt gegenereerd.
* **Dunne client**: Bepaalde delen van de toepassing kunnen via eenvoudige browser van het Web worden betreden gebruikend een HTML- gebruikersinterface, met inbegrip van de rapporteringsmodule, de stadia van de leveringsgoedkeuring, functionaliteit van de Verdeelde module van de Marketing (centraal/lokaal), instantie controle, enz. In deze modus kunt u de functionaliteit van Adobe Campagne opnemen in een intranet of extranet.
* **Integratie via de API**&#39;s: In bepaalde gevallen, kan het systeem van externe toepassing worden geroepen gebruikend de Diensten APIs van het Web die via het protocol van de ZEEP worden blootgesteld.

## Logische toepassingslaag {#logical-application-layer}

Adobe Campaign is één platform met verschillende toepassingen die in combinatie een open en schaalbare architectuur creëren. Het Adobe Campaign-platform is geschreven op een flexibele toepassingslaag en kan eenvoudig worden geconfigureerd om aan de zakelijke behoeften van een bedrijf te voldoen. Dit beantwoordt aan de groeiende behoeften van de onderneming vanuit zowel functioneel als technisch oogpunt. De verdeelde architectuur verzekert lineaire systeemscalability die van duizenden berichten aan miljoenen berichten schrapt.

Adobe Campagne is afhankelijk van een reeks server-side processen die samenwerken.

De belangrijkste processen zijn:

**Toepassingsserver** (extern web)

Dit proces stelt het volledige gamma van de functionaliteit van de Campagne van Adobe via de APIs van de Diensten van het Web (ZEEP - HTTP + XML) bloot. Bovendien kan het de Web-pagina&#39;s dynamisch produceren die voor op HTML-Gebaseerde toegang (rapporten, de vormen van het Web, enz.) worden gebruikt. Hiertoe bevat dit proces een Apache Tomcat JSP-server. Dit is het proces waaraan de console verbindt.

**Workflow-engine** (nlserver wfserver)

Het voert de werkschemaprocessen uit die in de toepassing worden bepaald.

Het behandelt ook periodiek uitgevoerde technische werkschema&#39;s, die omvatten:

* Tekstspatiëring: Trackinglogboeken herstellen en consolideren. Het laat u de logboeken van de omleidingsserver terugwinnen en de gezamenlijke indicatoren creëren die door de rapporteringsmodule worden gebruikt.
* Overbodig verwijderen: Database reinigen. Wordt gebruikt om oude records leeg te maken en te voorkomen dat de database exponentieel groeit.
* Facturering: Automatisch verzenden van een activiteitenverslag voor het platform (databasegrootte, aantal marketingacties, enz.).

**Leveringsserver** (nlserver mta)

Adobe Campaign beschikt over de native functionaliteit voor e-mailuitzending. Dit proces functioneert als SMTP agent van de postoverdracht (MTA). Het voert &quot;één-op-één&quot;verpersoonlijking van berichten uit en behandelt hun fysieke levering. Het werkt met leveringstaken en handelt automatische pogingen af. Wanneer reeksspatiëring is ingeschakeld, worden de URL&#39;s automatisch vervangen, zodat ze naar de omleidingsserver verwijzen.

Dit proces kan de aanpassing en het automatische verzenden naar een derderouter voor SMS, fax en directe post behandelen.

**Redirection server** (nlserver webmdl)

Voor e-mail, behandelt de Campagne van Adobe automatisch open en klikt het volgen (transactie het volgen op het niveau van de Website is een verdere mogelijkheid). Hiertoe worden de URL&#39;s die in de e-mailberichten zijn opgenomen, herschreven zodat ze naar deze module verwijzen. Deze module registreert het doorgeven van de internetgebruiker voordat deze naar de vereiste URL wordt doorgestuurd.

Om de hoogste beschikbaarheid te garanderen, is dit proces volledig onafhankelijk van het gegevensbestand: de andere serverprocessen communiceren ermee met behulp van alleen SOAP-aanroepen (HTTP, HTTP(S) en XML). Technisch, wordt deze functionaliteit uitgevoerd in een uitbreidingsmodule van een server van HTTP (ISAPI uitbreiding in IIS, of een module van DSO Apache, enz.) en is alleen beschikbaar in Windows.

Er zijn ook andere meer technische processen beschikbaar:

**Bounce-e-mailberichten** beheren (nlserver inMail)

Dit proces laat u toe om e-mail van brievenbussen automatisch op te nemen die worden gevormd om teruggestuurde berichten te ontvangen die in het geval van leveringsmislukking zijn teruggekeerd. Deze berichten worden dan op regel-gebaseerde verwerking ondergaan om de redenen voor niet levering (onbekende ontvanger, quota overschreden, etc.) te bepalen en de leveringsstatus in de database bij te werken.

Al deze verrichtingen zijn volledig automatisch en vooraf gevormd.

**Leveringsstatus** van SMS (nlserver sms)

Dit proces pollt de router van SMS om vooruitgangsstatus te verzamelen en het gegevensbestand bij te werken.

**Logberichten** schrijven (nlserver-syslogd)

Dit technische proces vangt logboekberichten en sporen die door de andere processen worden geproduceerd en schrijft hen aan de harde schijf. Dit maakt ruime informatie beschikbaar voor diagnose in het geval van problemen.

**Logbestanden voor** tekstspatiëring schrijven (logd voor reeksspatiëring)

Dit proces bewaart aan schijf de volgende logboeken die door het omleidingsproces worden geproduceerd.

**Inbound-gebeurtenissen** schrijven (nlserver-interactie)

Dit proces verzekert de opname aan de schijf van binnenkomende gebeurtenissen, binnen het kader van Interactie.

**Controlemodules** (nlserver watchdog)

Dit technische proces fungeert als een hoofdproces dat de anderen voortbrengt. Het bewaakt ze ook en start ze automatisch opnieuw in geval van incidenten, zodat het systeem maximaal uptime kan blijven.

**Statistische server** (nlserver stat)

Dit proces handhaaft statistieken over het aantal verbindingen, de berichten die voor elke postserver worden verzonden die berichten worden verzonden naar, evenals hun beperkingen (hoogste aantal gelijktijdige verbindingen, berichten per uur/en of verbinding). Het laat u ook verscheidene instanties of machines federeren als zij de zelfde openbare IP adressen delen.

>[!NOTE]
>
>De volledige lijst met Adobe Campagnemodules is beschikbaar in [dit document](../../production/using/operating-principle.md).

## Persistentielaag {#persistence-layer}

De database wordt gebruikt als een persistentielaag en bevat bijna alle informatie die wordt beheerd door Adobe Campaign. Dit omvat zowel functionele gegevens (profielen, abonnementen, inhoud, enz.), technische gegevens (leveringstaken en logbestanden, trackinglogbestanden, enz.) en werkgegevens (aankopen, leads).

De betrouwbaarheid van de database is van het grootste belang omdat de meeste componenten van Adobe Campagne toegang tot de database vereisen om hun taken uit te voeren (met uitzondering van de omleidingsmodule).

Het platform wordt vooraf gedefinieerd met een marketing gecentreerde datamarkt of kan gemakkelijk op een bestaande gegevensmarkt en een schema plaatsen gebruikend om het even welk van de belangrijkste Relationele Systemen van het Beheer van het Gegevensbestand (RDBMS). Alle gegevens in de datamarkt worden benaderd door het Adobe Campaign-platform via SQL-aanroepen van Adobe Campaign naar de database. Adobe Campaign beschikt ook over een volledig pakket met de ETL-gereedschappen (Extract Transform and Load) waarmee u gegevens kunt importeren en exporteren naar en uit het systeem.
