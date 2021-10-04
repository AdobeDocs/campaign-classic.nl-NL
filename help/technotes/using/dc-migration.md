---
product: campaign
title: Migratie naar openbare cloud
description: Meer informatie over Campaign Classic-migratie naar openbare cloud
feature: Overview
role: User
level: Beginner
exl-id: 2b282221-d048-4f6e-b52e-f8e584af2c0e
source-git-commit: 1a9e0f8bf374e10af938d15dcebe943819ae327b
workflow-type: tm+mt
source-wordcount: '1572'
ht-degree: 2%

---

# Overzicht{#dc-ovv}

![](../../assets/v7-only.svg)

## Context

Als gewaardeerde Adobe Campaign Classic-klant zijn wij vastbesloten u de beste ervaring en waarde te bieden. In de loop der jaren hebben we de waarde en betrouwbaarheid ingezien van het hosten van onze klanten in de cloud.  Als onderdeel van ons [Gold Standard Initiative](../../rn/using/gold-standard.md) verplaatsen we al onze klanten naar Adobe Managed Services (Public Cloud op AWS) voor betere en betrouwbaardere services.

Dit programma heeft drie hoofddoelstellingen:

* Oplossing van geïdentificeerde beveiligingskwetsbaarheden door de infrastructuur te verplaatsen naar een beveiligde en moderne omgeving (AWS).
* Elimineer mogelijk lastige schaalprocessen, verbeter toegang tot onze [Enhanced MTA&#39;s](../../delivery/using//sending-with-enhanced-mta.md) en verbeter alle serviceniveaus voor onderhoud.
* Bereid uw exemplaar voor voor de toekomst van Adobe Campaign Classic, inclusief meer geautomatiseerde, regelmatige upgrades waarvoor niet zoveel bronnen en niet zoveel tijd nodig zijn.

### Verklarende woordenlijst

* **Upgrade**  van build-upgrade: wanneer de Adobe Campaign Classic-software wordt bijgewerkt naar het meest recente beveiligde buildnummer, blijft de software op hetzelfde niveau voor &#39;belangrijke/kleine build&#39; staan. Bijvoorbeeld: Campagne versie 7 20.2.3 build 9182 to Campaign v7 21.2.5 build 9188. [Meer info](../../platform/using/faq-build-upgrade.md).
* **MID/RT**  - de uitvoeringsservers van Berichten die op Adobe Cloud worden ontvangen (MID voor partijcampagnes en RT voor Echte - tijd unitaire berichten)
* **Gold Standard-upgrade** : dit programma biedt verbeterde beveiliging, verbeterde ondersteuning, verbeterd onderhoud en stabiliteit. Het maakt toekomstige verbeteringen gemakkelijker en verleent toegang tot nieuwe mogelijkheden in Campagne.  [Meer info](../../rn/using/gs-overview.md).
* **AWS**  - Amazon Web Services (Amazon Public Cloud)
* **SFTP**  - Beveiligd protocol voor bestandsoverdracht. [Meer info](../../platform/using/sftp-server-usage.md).


>[!NOTE]
>De Campaign Classic v7-migratie naar de openbare cloud is alleen van invloed op klanten die **Beheerde services van Adobe** gebruiken.


## Voordelen

**Beveiliging**

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
* Proofing Campagne-versie - Gold Standard

**Kies voor een robuuste, betrouwbare oplossing voor Adobe Campaign Classic-klanten**

1. Betere productieprocedures, wat leidt tot meer betrouwbaarheid, snellere reactiviteit in geval van problemen, sneller herstel in geval van een groot incident.
1. Hogere verzendcapaciteit voor e-mail. Exemplaren die in het nieuwe datacenter worden gehost, kunnen profiteren van een gespecialiseerde infrastructuur voor e-maillevering. Dat zou tot hogere e-mailleveringssnelheid kunnen leiden of voor het gebruiken van minder verzendende IPs toestaan.
1. Betere schaalbaarheid van hardware. Het verhogen van hardwaremiddelen kan veel sneller worden gedaan. Technisch gezien zou dat in de orde van grootte van 1 uur in plaats van enkele dagen zijn.

**Gold Standard maakt toekomstige upgrades eenvoudiger**

1. Hoe langer uw organisatie wacht op een upgrade, hoe complexer uw upgrade wordt en hoe kwetsbaarheden toenemen (vooral wanneer u van een oudere versie overschakelt).
1. Met de Gold Standard Upgrade wordt uw exemplaar gemoderniseerd en is het klaar om meer geautomatiseerde en regelmatige updates te ontvangen met minder handmatige interventie en minder bronnen.

![](assets/GSMigrations.png)

## Migratie

De migratie naar Adobe Managed Services (Public Cloud) vindt in 2020/2021 plaats voor betrokken accounts. Adobe zal uw organisatie door deze reis leiden en begeleiden.

Om deze inspanning op gang te brengen, zullen de rekeningen die deze migratie vereisen een e-mailmededeling van Adobe ontvangen die een chronologie en toegang tot documentatie verstrekken. Dit is uw melding dat uw account is gepland voor migratie.

Een migratie kan worden geïnitieerd door [een nieuw ondersteuningsticket voor de klantenservice te openen](https://experienceleague.adobe.com/?support-solution=Campaign#support). Gebruik de onderwerpregel &quot;Migreren naar AWS&quot;.

### Is deze migratie verplicht?

Deze migratie naar de cloud is **eerste stap naar de [Gold Standard-certificering](../../rn/using/gs-overview.md)** van uw Adobe Campaign-instanties. Deze migratie is verplicht als u wordt gehost in een datacenter dat niet de openbare cloud (AWS) is.

De Adobe Managed Services-cloud wordt gehost op Amazon Web Services (AWS), een moderne, veilige en geoptimaliseerde omgeving. [Meer weten over AWS](https://aws.amazon.com/application-hosting/benefits/)?

Adobe is van plan het oude datacenter uit te schakelen, Adobe Campaign-instanties die daar actief zijn, moeten worden overgebracht naar het nieuwe referentiecentrum, AWS.

Dit is een kritiek pad naar voren, aangezien uw huidige locatie mogelijk wordt blootgesteld aan **beveiligings- en prestatiekwetsbaarheden**.

Bovendien is deze migratie nu een **vereiste voor elke toekomstige upgrade van Build** van uw Adobe Campaign. Upgrade bouwen is niet meer mogelijk in het oude datacenter.

Adobe heeft alles in het werk gesteld om uw gegevens te beveiligen en u op koers te brengen voor de toekomst van Adobe Campaign. We hebben uw partnerschap nodig om het tot een gezamenlijk succes te maken!


**We hebben een** team van speciale Customer Care-medewerkers, Customer Success Managers, Product Managers, Engineers, TechOps-specialisten en Product Consultants georganiseerd om u te helpen en ervoor te zorgen dat de ervaring soepel en naadloos verloopt. We doen er alles aan om u te voorzien van alle relevante project- en contactinformatie.

We hebben enorme inspanningen gedaan om technologieën te ontwikkelen die deze migratie snel, naadloos en veilig maken.

### Restricties

* De migratie zal met een onvermijdelijke platform onderbreking komen. Het doel van dit plan is deze uitvaltijd tot een minimum te beperken.
* IP verandering voor gegevensintegratie.
* De oprijving van de leverbaarheid van nieuwe verzendende IPs. Het is echter de bedoeling om deze operatie transparant te maken voor het bedrijf, in tegenstelling tot de eerste oprijplaat die tijdens het liveproces wordt uitgevoerd.

Meer informatie over de migratie van campagnes naar [Veelgestelde vragen over openbare cloud](dc-migration-faq.md).


## Reizen naar Gold Standard-certificering

We helpen u bij de validatiestappen tussen elke mijlpaal.

![](assets/GS-milestones.png)

## Migratiepad naar openbare cloud

Adobe handelt de meeste acties af. We hebben u nodig voor validatie en aftekening.

![](assets/MigrationPath.png)

## Richtlijnen voor migratie

### Globale aanpak

**Database**

De database wordt uit het oude datacenter verwijderd en hersteld in de Public Cloud (AWS). Wanneer u de toepassing opnieuw start in het nieuwe datacenter, wordt deze hervat in de toestand die deze was voordat de toepassing werd afgesloten. De gebruikers zullen geen verschil zien, behalve dat zullen sommige geplande taken vertraagd zijn.

**IP&#39;s verzenden via e-mail**

Wanneer de migratie volledig is, zal de instantie van de Campagne volledig verschillend het verzenden IPs hebben. Als kwestie van het verzekeren van een vlotte overgang, zal Adobe een oprijving van nieuwe verzendende IPs door progressief omschakelingsverkeer van oude aan nieuwe IPs uitvoeren.

**IP&#39;s voor gegevensintegratie**

De integratie van gegevens op de cliëntkant zou door de verandering van IPs voor gegevensintegratie kunnen worden beïnvloed. De wijziging kan van invloed zijn op beide richtingen, afhankelijk van het feit of de campagne als server of client fungeert.
Typische gevallen:

* SFTP, mogelijk beide richtingen
* HTTP, mogelijk beide richtingen
* SMPP (verbinding aan de leverancier van SMS), Campagne als cliënt, verandering bronIP

In het algemeen betekent dit dat de client mogelijke IP-beperkingen op hun firewalls moet controleren en deze dienovereenkomstig moet aanpassen.*

**Campagneservers**

Bestaande campagnemeservers (containers in feite) worden in een &quot;lift-and-shift&quot;-aanpak verplaatst naar de Public Cloud (AWS). Er is dus geen nieuwe serverinstallatie nodig, maar de volledige server wordt naar het nieuwe datacenter overgebracht. Voor de bewerking is alleen een technische herconfiguratie op laag niveau nodig.

**Servernamen**

Onder het subdomein of subdomeinen dat/die wordt/worden gebruikt voor marketingcommunicatie: blijft hetzelfde. Afhankelijk van de implementatie kunnen er echter acties aan de clientzijde nodig zijn:

* In het geval van subdomeindelegatie (normaal geval) zorgt Adobe voor alle wijzigingen en zorgt hij voor een naadloze overgang
* In het geval van opstelling CNAME (uitzondering), zal de cliënt worden gevraagd om veranderingen uit te voeren. Coördinatie met Adobe is nodig.

Voor gebruikerstoegang en gegevensintegratie blijven de namen onder neolane.net ongewijzigd.

Dat betekent de verandering voor gebruikers, en de implementaties van de gegevensintegratie transparant zal zijn, als de servernamen niet door hard-gecodeerde IPs werden vervangen.

### Voorbereiding

**IP&#39;s verzenden via e-mail**

Eerst, zal de Leverbaarheid van de Adobe de leveringsstatus van het platform beoordelen en zal een plan voor de schakelaar aan nieuwe IPs adviseren.

Adobe zal het zelfde aantal IPs op het nieuwe gegevenscentrum verstrekken.

De oprijving van nieuwe IPs kan beginnen zodra nieuwe IPs provisioned is.

**Overdracht van gegevens tussen datacenters wordt**
door de toepassing opgeschoond.

De gegevens worden op twee manieren opgeslagen:

1. De database is verreweg het belangrijkste
1. Bestanden op de toepassingsserver (gegevens importeren en exporteren)

Het verkleinen van de omvang van de database is van het grootste belang om de gegevensoverdracht te versnellen.

Suggesties:

* Verminder de bewaartermijnen van historische gegevens (leveringslogboeken, het volgen logboeken, enz.)
* Lege records uit andere tabellen verwijderen (leveringen, ontvangers, aangepaste tabellen)

### Execution

**Uitvoeringen pauzeren**

We raden u aan alle uitvoeringen te vertragen en idealiter te pauzeren vlak voordat de toepassing wordt afgesloten in het oude datacenter: leveringen en workflows. Hierdoor wordt het opnieuw opstarten in de Public Cloud (AWS) eenvoudiger, omdat processen tijd hebben gekregen om &#39;netjes&#39; te pauzeren en eventuele uitvoeringsstatus in uitvoering op te slaan.

**Tijdens de migratie**

Tijdens de migratie blijft slechts één service functioneel: e-mailkoppelingen worden omgeleid. Met andere woorden, ontvangers kunnen de bestemmingspagina bereiken wanneer ze in een e-mail klikken. Deze kliks worden echter niet opgenomen, dus klik voor de leveringen die kort voor de migratie zijn gestart op een lagere snelheid dan normaal.

**Opnieuw starten**

Nadat de toepassing naar de nieuwe omgeving is gemigreerd, wordt de toepassing geleidelijk opnieuw gestart:

* Eerste consoletoegang, zodat kunnen de gebruikers de status controleren zonder om het even wat actief nog loopt
* Dan, werkschema&#39;s en leveranties

### Na migratie

**Verwijderen van instanties in het verouderde datacenter**

Wanneer de migratie van de toepassing is voltooid, is er geen plan om een proces opnieuw uit te voeren in het oude datacenter. We verwachten dat alle gegevens in het oude datacenter kunnen worden gewist, behalve voor tijdelijke back-updoeleinden, totdat de geplande back-upprocessen zijn uitgevoerd op de Public Cloud (AWS).

**DNS-delegatie**

Normaal, is het domein dat voor het verzenden van e-mail (deel op het recht van @ teken in het foutenadres) van Campagne wordt gebruikt afgevaardigd aan Adobe. De delegatie kan in de richting van de DNS-servers van AWS worden gewijzigd en geïmplementeerd.


## Ondersteuning en andere handige koppelingen{#support}

* [Migratie naar veelgestelde vragen over Adobe Managed Services (Public Cloud)](dc-migration-faq.md)
* [Upgrade van gouden standaard](../../rn/using/gs-overview.md)
* [Veelgestelde vragen over upgrade maken](../../platform/using/faq-build-upgrade.md)
