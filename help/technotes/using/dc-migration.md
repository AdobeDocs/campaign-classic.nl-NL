---
product: campaign
title: Migratie naar Public Cloud
description: Meer informatie over Campaigns Classic migreren naar Public Cloud
feature: Technote, Upgrade
role: User
level: Beginner
exl-id: 2b282221-d048-4f6e-b52e-f8e584af2c0e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1533'
ht-degree: 2%

---

# Overzicht{#dc-ovv}



## Context

Als gewaardeerde Adobe Campaign Classic-klant zijn wij vastbesloten u de beste ervaring en waarde te bieden. In de loop der jaren hebben we de waarde en betrouwbaarheid ingezien van het hosten van onze klanten in de cloud.  Als deel van ons [ Jaarlijks Initiatief van de Verbetering ](../../rn/using/rn-overview.md#yearly-upgrade), bewegen wij al onze klanten aan Adobe Managed Services (Openbare Wolk op AWS) om betere en betrouwbaardere diensten te verlenen.

Dit programma heeft drie hoofddoelstellingen:

* Oplossing van geïdentificeerde beveiligingskwetsbaarheden door de infrastructuur te verplaatsen naar een beveiligde en moderne omgeving (AWS).
* Elimineer potentieel omslachtige het schrapen processen, verstrek toegang tot onze [ Verbeterde MTAs ](../../delivery/using//sending-with-enhanced-mta.md) en verbeter alle niveaus van de onderhoudsdienst.
* Bereid uw exemplaar voor voor de toekomst van Adobe Campaign Classic, met inbegrip van meer geautomatiseerde, regelmatige upgrades die niet zo veel middelen, noch zoveel tijd zullen vereisen.

### Verklarende woordenlijst

* **Bouwstijl Verbetering** - wanneer de software van Adobe Campaign Classic aan het recentste veilige bouwstijlaantal wordt bijgewerkt, maar blijft in zelfde belangrijke/minder bouwt Niveau. Bijvoorbeeld: Campaign versie 7 20.2.3 build 9182 to Campaign v7 21.2.5 build 9188. [Meer informatie](../../platform/using/faq-build-upgrade.md).
* **MID/RT** - de uitvoeringsservers van Berichten die op de Wolk van de Adobe worden ontvangen (MID voor partijcampagnes en RT voor Echte - tijd unitaire berichten)
* **Jaarlijks Programma van de Verbetering** - dit programma verstrekt betere veiligheid, verbeterde steun, verbeterd onderhoud en stabiliteit. Het maakt toekomstige verbeteringen gemakkelijker en verleent toegang tot nieuwe mogelijkheden in Campagne.  [Meer informatie](../../rn/using/rn-overview.md#yearly-upgrade).
* **AWS** - Amazon Web Services (de Openbare Wolk van Amazon)
* **SFTP** - het Beveiligde Protocol van de Overdracht van het Dossier. [Meer informatie](../../platform/using/sftp-server-usage.md).


>[!NOTE]
>De migratie van Campaign Classic v7 naar de Openbare Cloud beïnvloedt klanten gebruikend **Adobe Managed Services** slechts.


## Voordelen

**Veiligheid**

* Laatste beveiligingsoplossingen
* Gegevenscodering in rust
* Verbeterde verificatie (IMS)

**Infrastructuur**

* Flexibele schaalbaarheid van hardware
* Sneller herstellen
* Verbeterde betrouwbaarheid en stabiliteit
* Geharmoniseerde operationele procedures

**Prestaties**

* Verbeterde e-mailcapaciteit
* Grotere databases
* Proofing Campagne

**breng een robuuste, betrouwbare oplossing voor de klanten van Adobe Campaign Classic**

1. Betere productieprocedures, wat leidt tot meer betrouwbaarheid, snellere reactiviteit in geval van problemen, sneller herstel in geval van een groot incident.
1. Hogere verzendcapaciteit voor e-mail. Exemplaren die in het nieuwe datacenter worden gehost, kunnen profiteren van een gespecialiseerde infrastructuur voor e-maillevering. Dat zou tot hogere e-mailleveringssnelheid kunnen leiden of voor het gebruiken van minder verzendende IPs toestaan.
1. Betere schaalbaarheid van hardware. Het verhogen van hardwaremiddelen kan veel sneller worden gedaan. Technisch gezien zou dat in de orde van grootte van 1 uur in plaats van enkele dagen zijn.

**jaarlijkse verbeteringen maakt toekomstige verbeteringen gemakkelijker**

1. Hoe langer uw organisatie wacht op een upgrade, hoe complexer uw upgrade wordt en hoe kwetsbaarheden toenemen (vooral wanneer u van een oudere versie overschakelt).
1. Met de jaarlijkse upgrade van Campagne (voorheen Gold Standard) wordt uw exemplaar gemoderniseerd en is het klaar om meer geautomatiseerde en regelmatige updates te ontvangen met minder handmatige interventie en minder bronnen.

![](assets/GSMigrations.png)

## Migratie

Om deze inspanning op gang te brengen, zullen de rekeningen die deze migratie vereisen een e-mailmededeling van Adobe ontvangen die een chronologie en toegang tot documentatie verstrekken. Dit is uw melding dat uw account is gepland voor migratie.

Een migratie kan worden in werking gesteld door [ een nieuw de steunkaartje van de Zorg van de Klant te openen ](https://experienceleague.adobe.com/?support-solution=Campaign#support). Gebruik de onderwerpregel &#39;Migreren naar AWS&#39;.

### Is deze migratie verplicht?

Deze migratie aan de Wolk is **eerste stap aan het [ jaarlijkse verbeteringsprogramma](../../rn/using/rn-overview.md#yearly-upgrade)** van uw instanties van Adobe Campaign. Deze migratie is verplicht als u wordt gehost in een datacenter dat niet de openbare cloud (AWS) is.

De Adobe Managed Services cloud wordt gehost op Amazon Web Services (AWS), een moderne, veilige en geoptimaliseerde omgeving. [ leer meer over AWS ](https://aws.amazon.com/application-hosting/benefits/).

Adobe is van plan het oude datacenter uit te schakelen, Adobe Campaign-instanties die daar actief zijn, moeten worden overgebracht naar het nieuwe referentiecentrum in AWS.

Dit is een kritieke weg voorwaarts aangezien uw huidige plaats aan **veiligheid en prestatieskwetsbaarheid** kan worden blootgesteld.

Bovendien is deze migratie nu a **eerste vereiste aan om het even welke toekomstige verbetering van de Bouwstijl** van uw Adobe Campaign. Upgrade bouwen is niet meer mogelijk in het oude datacenter.

De Adobe heeft er alles aan gedaan om uw gegevens te beveiligen en u op koers te brengen voor de toekomst van Adobe Campaign. We hebben uw partnerschap nodig om het tot een gezamenlijk succes te maken!


**wij hebben een team** van de specifieke Reps van de Zorg van de Klant, de Managers van het Succes van de Klant, de Managers van het Product, Ingenieurs, de Specialisten van TechOps en de Adviseurs van het Product georganiseerd om de ervaring te helpen en te verzekeren is vlot en naadloos. We doen er alles aan om u te voorzien van alle relevante project- en contactinformatie.

We hebben enorme inspanningen gedaan om technologieën te ontwikkelen die deze migratie snel, naadloos en veilig maken.

### Restricties

* De migratie zal met een onvermijdelijke platform onderbreking komen. Het doel van dit plan is deze uitvaltijd tot een minimum te beperken.
* IP verandering voor gegevensintegratie.
* De oprijving van de leverbaarheid van nieuwe verzendende IPs. Het is echter de bedoeling om deze operatie transparant te maken voor het bedrijf, in tegenstelling tot de eerste oprijplaat die tijdens het liveproces wordt uitgevoerd.

Leer meer in de migratie van de Campagne aan [ Openbare Cloud FAQ ](dc-migration-faq.md).


## Migratiepad naar openbare cloud

De meeste handelingen worden door de Adobe afgehandeld. We hebben u nodig voor validatie en aftekening.

![](assets/MigrationPath.png)

## Richtlijnen voor migratie

### Globale aanpak

**Database**

De database wordt uit het oude datacenter verwijderd en hersteld in Public Cloud (AWS). Wanneer u de toepassing opnieuw start in het nieuwe datacenter, wordt deze hervat in de toestand die deze was voordat de toepassing werd afgesloten. De gebruikers zullen geen verschil zien, behalve dat zullen sommige geplande taken vertraagd zijn geweest.

**E-mail die IPs verzendt**

Wanneer de migratie volledig is, zal de instantie van de Campagne volledig verschillend het verzenden IPs hebben. Als kwestie van het verzekeren van een vlotte overgang, zal de Adobe een oprijving van nieuwe verzendende IPs door progressief overschakelingsverkeer van oude aan nieuwe IPs uitvoeren.

**de integratie IPs van Gegevens**

De integratie van gegevens op de cliëntkant zou door de verandering van IPs voor gegevensintegratie kunnen worden beïnvloed. De wijziging kan van invloed zijn op beide richtingen, afhankelijk van het feit of de campagne als server of client fungeert.
Typische gevallen:

* SFTP, mogelijk beide richtingen
* HTTP, mogelijk beide richtingen
* SMPP (verbinding aan de leverancier van SMS), Campagne als cliënt, verandering bronIP

In het algemeen betekent dit dat de client mogelijke IP-beperkingen op hun firewalls moet controleren en deze dienovereenkomstig moet aanpassen.*

**Servers van de Campagne**

Bestaande campagnemeservers (containers in feite) worden verplaatst naar de Public Cloud (AWS) via een &quot;lift-and-shift&quot;-aanpak. Er is dus geen nieuwe serverinstallatie nodig, maar de volledige server wordt naar het nieuwe datacenter overgebracht. Voor de bewerking is alleen een technische herconfiguratie op laag niveau nodig.

**de namen van de Server**

Onder het subdomein(en) dat (die) wordt (worden) gebruikt voor marketingcommunicatie: blijft hetzelfde. Afhankelijk van de implementatie kunnen er echter acties aan de clientzijde nodig zijn:

* In het geval van subdomeindelegatie (normaal geval) zorgt de Adobe voor alle wijzigingen en zorgt zij voor een naadloze overgang
* In het geval van opstelling CNAME (uitzondering), zal de cliënt worden gevraagd om veranderingen uit te voeren. Coördinatie met Adobe is nodig.

Voor gebruikerstoegang en gegevensintegratie blijven de namen onder neolane.net ongewijzigd.

Dat betekent de verandering voor gebruikers, en de implementaties van de gegevensintegratie transparant zal zijn, als de servernamen niet door hard-gecodeerde IPs werden vervangen.

### Voorbereiding

**E-mail die IPs verzendt**

Eerst, zal de Leverbaarheid van de Adobe de leveringsstatus van het platform beoordelen en een plan voor de omschakeling aan nieuwe IPs adviseren.

Adobe zal het zelfde aantal IPs op het nieuwe gegevenscentrum verstrekken.

De oprijving van nieuwe IPs kan beginnen zodra nieuwe IPs provisioned is.

**Opschonen van de Toepassing**
De gegevensoverdracht tussen gegevenscentra is op de kritieke weg van onderbreking.

De gegevens worden op twee manieren opgeslagen:

1. De database is verreweg het belangrijkste
1. Bestanden op de toepassingsserver (gegevens importeren en exporteren)

Het verkleinen van de omvang van de database is van het grootste belang om de gegevensoverdracht te versnellen.

Suggesties:

* Verminder de bewaartermijnen van historische gegevens (leveringslogboeken, het volgen logboeken, enz.)
* Lege records uit andere tabellen verwijderen (leveringen, ontvangers, aangepaste tabellen)

### Execution

**de uitvoeringen van de Pauze**

We raden u aan alle uitvoeringen te vertragen en idealiter te pauzeren vlak voordat de toepassing wordt afgesloten in het oude datacenter: leveringen en workflows. Hierdoor wordt het opnieuw opstarten van Public Cloud (AWS) eenvoudiger, omdat processen tijd hebben gekregen om ‘netjes’ te pauzeren en eventuele uitvoeringsstatus in uitvoering op te slaan.

**tijdens de migratie**

Tijdens de migratie blijft slechts één service actief: e-mailkoppelingen worden omgeleid. Met andere woorden, ontvangers kunnen de bestemmingspagina bereiken wanneer ze in een e-mail klikken. Deze kliks worden echter niet opgenomen, dus klik voor de leveringen die kort voor de migratie zijn gestart op een lagere snelheid dan normaal.

**Begin** opnieuw

Nadat de toepassing naar de nieuwe omgeving is gemigreerd, wordt de toepassing geleidelijk opnieuw gestart:

* Eerste consoletoegang, zodat kunnen de gebruikers de status controleren zonder om het even wat actief nog loopt
* Vervolgens workflows en leveringen

### Na de migratie

**Schrapping van instanties op het centrum van erfenisgegevens**

Wanneer de migratie van de toepassing is voltooid, is er geen plan om een proces opnieuw uit te voeren in het oude datacenter. We verwachten dat alle gegevens in het oude datacenter kunnen worden gewist, behalve voor tijdelijke back-updoeleinden, totdat de geplande back-upprocessen zijn uitgevoerd op Public Cloud (AWS).

**DNS Delegatie**

Normaal, is het domein dat voor het verzenden van e-mail (deel op het recht van @ teken in het foutenadres) van Campagne wordt gebruikt afgevaardigd aan Adobe. De delegatie kan worden gewijzigd en geïmplementeerd in de richting van de AWS DNS-servers.


## Ondersteuning en andere handige koppelingen{#support}

* [Veelgestelde vragen over migratie naar Adobe Managed Services (Public Cloud)](dc-migration-faq.md)
* [Jaarlijkse upgrades campagne](../../rn/using/rn-overview.md)
* [Veelgestelde vragen over upgrade maken](../../platform/using/faq-build-upgrade.md)
