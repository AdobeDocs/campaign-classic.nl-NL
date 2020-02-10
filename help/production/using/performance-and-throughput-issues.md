---
title: Problemen met prestaties en doorvoer
seo-title: Problemen met prestaties en doorvoer
description: Problemen met prestaties en doorvoer
seo-description: null
page-status-flag: never-activated
uuid: 28c35453-9a15-44a3-9961-f4c604c209c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: ec66e3e3-b09a-44a4-914d-e3b38c7643f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# Problemen met prestaties en doorvoer{#performance-and-throughput-issues}

>[!NOTE]
>
>Eerst en vooral, zou u moeten controleren dat u de recentste bouwstijl hebt geïnstalleerd. Dit zorgt ervoor dat u de recentste eigenschappen en insectenmoeilijke situaties hebt. Raadpleeg de [opmerkingen bij](https://docs.campaign.adobe.com/doc/AC/en/RN.html) de release voor meer informatie over de inhoud van elke release.

## Hardware en infrastructuur {#hardware-and-infrastructure}

Algemene richtlijnen voor hardwarevereisten voor on-premise Campaign Classic worden in dit [artikel](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)beschreven.

Het raadplegende team kan ontvangen klanten een hulpmiddel verstrekken dat u toestaat om gemakkelijk te bekijken hoeveel ruimte door diverse types van lijsten in het gegevensbestand evenals de ruimte wordt gebruikt die op de plaats SFTP wordt gebruikt. Daarnaast beschikt de toepassing over gereedschappen waarmee u overbodige gegevens kunt opschonen. Neem contact op met de consulteer- of supportteams als u dit hulpprogramma nodig hebt. Hier volgen enkele belangrijke zaken die u met dit gereedschap kunt controleren:

* Als de indexgrootte groter is dan de tabelgrootte, is een vacuüm vereist.
* Controleer de tabellen die het maximale bloat hebben. Als deze tabellen vaak worden gebruikt, moeten ze worden opgevuld.
* Door databaseblokkering kunnen e-mails niet meer worden verzonden.

Adobe Campaign beschikt ook over een [programma](../../production/using/monitoring-processes.md#manual-monitoring) om het CPU- en RAM-verbruik te controleren. Gebruik dit hulpmiddel en bekijk specifieke indicatoren zoals: **Geheugen**, **Wisselend Geheugen**, **Schijf**, **Actieve Processen**. Als de waarden te hoog zijn, kunt u proberen het aantal werkstromen te verminderen of werkschema&#39;s plannen om op verschillende tijden te beginnen.

## Databaseprestaties {#database-performances}

Meestal zijn prestatieproblemen gekoppeld aan databaseonderhoud. Hier volgen de belangrijkste onderdelen:

* Configuratie: We raden u aan de eerste configuratie van het Adobe Campaign-platform te controleren en een volledige hardwarefout uit te voeren.
* Installatie en configuratie van het Adobe Campaign-platform: controleer de opties voor netwerkconfiguratie en platformleverantie.
* Onderhoud database: zorg ervoor dat de taak van de gegevensbestandschoonmaakbeurt operationeel is en dat het gegevensbestandonderhoud correct gepland en uitgevoerd is. Controleer het aantal en de grootte van werktabellen.
* Realtime diagnose: controleer het proces en de dossiers van het platformlogboek, dan controleert gegevensbestandactiviteit terwijl het ontspannen van de kwestie.

>[!NOTE]
>
>Zie deze sectie voor meer informatie: Prestaties van [databases](../../production/using/database-performances.md).

## Toepassingsconfiguratie {#application-configuration}

Hier volgt een lijst met artikelen die betrekking hebben op de aanbevolen werkwijzen voor toepassingsconfiguratie:

* MTA en MTAChild processen en geheugen: de **mta** module verspreidt berichten aan zijn **mtachild** modules. Elk **mtachild** bereidt berichten voor alvorens om een vergunning van de statistiekserver te verzoeken, en hen te verzenden. Raadpleeg deze [pagina](../../installation/using/email-deliverability.md) voor meer informatie.
* TLS-configuratie: het wereldwijd inschakelen van TLS wordt afgeraden omdat dit de doorvoer kan verminderen. In plaats daarvan moeten de TLS-instellingen per domein, beheerd door het leveringsteam, worden afgestemd op de behoeften. Raadpleeg deze [pagina](../../installation/using/email-deliverability.md#mx-configuration) voor meer informatie.
* DKIM: Om het veiligheidsniveau van DKIM te verzekeren, is 1024b de Beste praktijken geadviseerde encryptiegrootte. De lagere sleutels DKIM zullen niet als geldig door de meerderheid van toegangsleveranciers worden beschouwd. Zie deze [pagina](../../delivery/using/technical-recommendations.md#domainkeys-identified-mail--dkim-) en dit [technische artikel](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html).

## Leverbaarheidsproblemen {#deliverability-issues}

Hier volgt een lijst met best practices en artikelen met betrekking tot de te leveren items:

* IP-reputatie: als de IP reputatie niet goed genoeg is, zal er een effect op prestaties zijn. De module **Leverbaarheidscontrole** biedt verschillende tools om de prestaties van uw platform bij te houden. Zie deze [pagina](../../delivery/using/technical-monitoring.md).
* Opwarmen IP: IP warm-up wordt uitgevoerd door het leveringsteam. Dit houdt in dat het aantal e-mails over een periode van een paar weken geleidelijk wordt verhoogd via nieuwe IP&#39;s.
* Instellen IP-affiniteit: Een onjuiste IP affiniteitopstelling kan de e-mail volledig tegenhouden (onjuiste exploitant/affiniteitsnaam in configuratie) of de productie (klein aantal IPs in de affiniteit) verminderen. Zie deze [pagina](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* E-mailformaat: De e-mailgrootte speelt een belangrijke rol in productie. De aanbevolen maximale e-mailgrootte is 60 kB. Zie deze [pagina](https://helpx.adobe.com/legal/product-descriptions/campaign.html). Controleer in het rapport [Leveringsdoorvoer](../../reporting/using/reports-on-deliveries.md#delivery-throughput) het aantal bytes dat per uur is overgedragen.
* Groot aantal ongeldige ontvangers: wanneer er een groot aantal ongeldige ontvangers is, kan het effect op de productie hebben. De MTA blijft het verzenden van e-mails naar ongeldige ontvangers opnieuw proberen. Controleer of de database goed wordt onderhouden.
* Hoeveelheid personalisatie: als een levering in &quot;Personalisatie lopend&quot;blijft, controleer JavaScript die in verpersoonlijkingsblokken wordt gebruikt.

>[!NOTE]
>
>Vergeet niet de gids over [aflevering aan de slag](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) te raadplegen.

