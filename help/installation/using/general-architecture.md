---
product: campaign
title: Campaign Classic algemene architectuur
description: Leer hoe u Campaign Classic installeert en configureert
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: 04e6dc17-427b-4745-84cc-bf45c03dbf81
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 0%

---

# Algemene architectuur{#general-architecture}



De gebruikelijke Adobe Campaign-implementatie van oplossingen bestaat uit de volgende onderdelen:

* **Persoonlijke clientomgeving**

   Intuïtieve grafische interface waarin gebruikers marketingaanbiedingen kunnen communiceren en volgen, campagnes kunnen maken, alle marketingactiviteiten, programma&#39;s en plannen (inclusief e-mails, workflows en bestemmingspagina&#39;s) kunnen beoordelen en beheren, klantprofielen kunnen maken en beheren en klantsoorten kunnen definiëren.

* **Ontwikkelingsomgeving**

   Server-side software die de marketing campagnes door gekozen communicatie kanalen, met inbegrip van e-mail, SMS, dupberichten, direct mail, Web of sociaal uitvoert, op de regels en de werkschema&#39;s die in het gebruikersinterface worden bepaald.

* **Databasecontainers**

   Gebaseerd op relationele gegevensbestandtechnologie, slaat het gegevensbestand van Adobe Campaign alle klanteninformatie, campagnecomponenten, aanbiedingen en werkschema&#39;s, evenals campagneresultaten in de containers van het klantengegevensbestand op.

Adobe Campaign is gebaseerd op een servicegerichte architectuur (SOA) en bestaat uit verschillende functionele modules. Deze modules kunnen op één of meerdere computers, in enige of veelvoudige instanties, afhankelijk van beperkingen in termen van scalability, beschikbaarheid en de dienstisolatie worden opgesteld. Het werkingsgebied van plaatsingsconfiguraties is daarom zeer breed, en overspant één enkele, centrale computer door aan configuraties met inbegrip van veelvoudige specifieke servers over veelvoudige plaatsen.

>[!NOTE]
>
>Als softwareleverancier specificeren wij compatibele hardware en softwareinfrastructuur. De hardwareaanbevelingen die hier worden gegeven, dienen uitsluitend ter informatie en zijn gebaseerd op onze ervaring. Adobe is niet aansprakelijk voor besluiten die op hen zijn gebaseerd. Het zal ook van uw bedrijfsregels en praktijken en de kritiek en vereiste prestatiesniveaus van het project afhangen.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Indien niet uitdrukkelijk anders vermeld, vallen de installatie, updates en het onderhoud op alle componenten van een Adobe Campaign-platform onder de verantwoordelijkheid van de systeembeheerder(s) die deze host(s). Dit omvat het implementeren van de voorwaarden voor Adobe Campaign-toepassingen en het naleven van Campagne [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md) tussen componenten.

## Presentatielaag {#presentation-layer}

De toepassing kan op verschillende manieren worden benaderd, afhankelijk van de behoeften van de gebruikers: Rich client-, thin client- of API-integratie.

* **Rijke client**: De hoofdgebruikersinterface van de toepassing is een rijke client, met andere woorden een native toepassing (Windows) die alleen communiceert met de Adobe Campaign-toepassingsserver met standaard internetprotocollen (SOAP, HTTP, enzovoort). Deze console biedt grote gebruiksvriendelijkheid voor productiviteit, gebruikt zeer weinig bandbreedte (door het gebruik van een lokale cache) en is ontworpen voor eenvoudige implementatie. Deze console kan vanuit een internetbrowser worden geïmplementeerd, kan automatisch worden bijgewerkt en vereist geen specifieke netwerkconfiguratie omdat alleen HTTP(S)-verkeer wordt gegenereerd.
* **Dunne client**: Bepaalde delen van de toepassing zijn toegankelijk via een eenvoudige webbrowser met behulp van een gebruikersinterface van HTML, zoals de rapporteringsmodule, de goedkeuringsfasen van de levering, de functies van de module Distributed Marketing (centraal/lokaal), de controle van instanties, enz. Met deze modus kunt u Adobe Campaign-functies opnemen in een intranet of extranet.
* **Integratie via de API&#39;s**: In bepaalde gevallen, kan het systeem van externe toepassing worden geroepen gebruikend de Diensten APIs van het Web die via het protocol van de ZEEP worden blootgesteld.

## Logische toepassingslaag {#logical-application-layer}

Adobe Campaign is één platform met verschillende toepassingen die combineren tot het maken van een open en schaalbare architectuur. Het platform van Adobe Campaign wordt geschreven op een flexibele toepassingslaag en is gemakkelijk configureerbaar om aan de bedrijfsbehoeften van een bedrijf te voldoen. Dit beantwoordt aan de groeiende behoeften van de onderneming vanuit zowel functioneel als technisch oogpunt. De verdeelde architectuur verzekert lineaire systeemscalability die van duizenden berichten aan miljoenen berichten schrapt.

Adobe Campaign vertrouwt op een reeks server-zijprocessen die samenwerken.

De belangrijkste processen zijn:

**Toepassingsserver** (nlserver-web)

Dit proces stelt de volledige waaier van de functionaliteit van Adobe Campaign via de APIs van de Diensten van het Web (ZEEP - HTTP + XML) bloot. Bovendien kan het de Web-pagina&#39;s dynamisch produceren die voor op HTML-Gebaseerde toegang (rapporten, de vormen van het Web, enz.) worden gebruikt. Hiertoe bevat dit proces een Apache Tomcat JSP-server. Dit is het proces waaraan de console verbindt.

**Workflow-engine** (nlserver wfserver)

Het voert de werkschemaprocessen uit die in de toepassing worden bepaald.

Het behandelt ook periodiek uitgevoerde technische werkschema&#39;s, die omvatten:

* Tekstspatiëring: Trackinglogboeken herstellen en consolideren. Het laat u de logboeken van de omleidingsserver terugwinnen en de gezamenlijke indicatoren creëren die door de rapporteringsmodule worden gebruikt.
* Overbodig verwijderen: Database reinigen. Wordt gebruikt om oude records leeg te maken en te voorkomen dat de database exponentieel groeit.
* Facturering: Automatisch verzenden van een activiteitenrapport voor het platform (databasegrootte, aantal marketingacties, aantal actieve profielen, enz.).

**Leveringsserver** (nlserver mta)

Adobe Campaign heeft native functionaliteit voor e-mailuitzending. Dit proces functioneert als SMTP agent van de postoverdracht (MTA). Het voert &quot;één-op-één&quot;verpersoonlijking van berichten uit en behandelt hun fysieke levering. Het werkt met leveringstaken en handelt automatische pogingen af. Wanneer reeksspatiëring is ingeschakeld, worden de URL&#39;s automatisch vervangen, zodat ze naar de omleidingsserver verwijzen.

Dit proces kan de aanpassing en het automatische verzenden naar een derderouter voor SMS, fax en directe post behandelen.

**Redirection-server** (nlserver-webmdl)

Voor e-mail, behandelt Adobe Campaign automatisch open en klikt het volgen (transactie het volgen op het niveau van de Website is een verdere mogelijkheid). Hiertoe worden de URL&#39;s die in de e-mailberichten zijn opgenomen, herschreven zodat ze naar deze module verwijzen. Deze module registreert het doorgeven van de internetgebruiker voordat deze naar de vereiste URL wordt doorgestuurd.

Om de hoogste beschikbaarheid te garanderen, is dit proces volledig onafhankelijk van het gegevensbestand: de andere serverprocessen communiceren ermee met behulp van alleen SOAP-aanroepen (HTTP, HTTP(S) en XML). Technisch, wordt deze functionaliteit uitgevoerd in een uitbreidingsmodule van een server van HTTP (ISAPI uitbreiding in IIS, of een module van DSO Apache, enz.) en is alleen beschikbaar in Windows.

Er zijn ook andere meer technische processen beschikbaar:

**Bounce-e-mails beheren** (nlserver inMail)

Dit proces laat u toe om e-mail van brievenbussen automatisch op te nemen die worden gevormd om teruggestuurde berichten te ontvangen die in het geval van leveringsmislukking zijn teruggekeerd. Deze berichten worden dan op regel-gebaseerde verwerking ondergaan om de redenen voor niet levering (onbekende ontvanger, quota overschreden, etc.) te bepalen en de leveringsstatus in de database bij te werken.

Al deze verrichtingen zijn volledig automatisch en vooraf gevormd.

**Status van SMS-verzending** (nlserver sms)

Dit proces pollt de router van SMS om vooruitgangsstatus te verzamelen en het gegevensbestand bij te werken.

**Logboekberichten schrijven** (nlserver-syslogd)

Dit technische proces vangt logboekberichten en sporen die door de andere processen worden geproduceerd en schrijft hen aan de harde schijf. Dit maakt ruime informatie beschikbaar voor diagnose in het geval van problemen.

**Logbestanden voor bijhouden schrijven** (nlserver trackinglogd)

Dit proces bewaart aan schijf de volgende logboeken die door het omleidingsproces worden geproduceerd.

**Inkomende gebeurtenissen schrijven** (Nlserver-interactief)

Dit proces verzekert de opname aan de schijf van binnenkomende gebeurtenissen, binnen het kader van Interactie.

**Toezichtmodules** (nlserver waakhond)

Dit technische proces fungeert als een primair proces dat de anderen voortbrengt. Het bewaakt ze ook en start ze automatisch opnieuw in geval van incidenten, zodat het systeem maximaal uptime kan blijven.

**Statistische server** (nlserver-status)

Dit proces handhaaft statistieken over het aantal verbindingen, de berichten die voor elke postserver worden verzonden die berichten worden verzonden naar, evenals hun beperkingen (hoogste aantal gelijktijdige verbindingen, berichten per uur/en of verbinding). Het laat u ook verscheidene instanties of machines federeren als zij de zelfde openbare IP adressen delen.

>[!NOTE]
>
>De volledige lijst met Adobe Campaign-modules is beschikbaar in [dit document](../../production/using/operating-principle.md).

## Persistentielaag {#persistence-layer}

De database wordt gebruikt als een persistentielaag en bevat bijna alle informatie die door Adobe Campaign wordt beheerd. Dit omvat zowel functionele gegevens (profielen, abonnementen, inhoud, enz.), technische gegevens (leveringstaken en logbestanden, trackinglogbestanden, enz.) en werkgegevens (aankopen, leads).

De betrouwbaarheid van de database is van het grootste belang omdat de meeste Adobe Campaign-componenten toegang tot de database vereisen om hun taken uit te voeren (met uitzondering van de omleidingsmodule).

Het platform wordt vooraf bepaald met een marketing gecentreerde datamarkt of kan gemakkelijk op een bestaande gegevensmarkt en een schema plaatsen gebruikend om het even welk van de belangrijkste Relationele Systemen van het Beheer van het Gegevensbestand (RDBMS). Alle gegevens binnen de datamarkt zijn toegankelijk voor het Adobe Campaign-platform via SQL-aanroepen van Adobe Campaign naar de database. Adobe Campaign biedt ook een volledige aanvulling op de ETL-gereedschappen (Extract Transform and Load) voor het importeren en exporteren van gegevens naar en vanuit het systeem.
