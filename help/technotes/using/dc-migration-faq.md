---
product: campaign
title: Migratie naar veelgestelde vragen over Adobe Managed Services (Public Cloud)
description: Veelgestelde vragen over Campaign Classic-migratie naar openbare cloud
feature: Overview
role: User
level: Beginner
exl-id: a9cd08b0-55c2-4405-9fb8-f0c623cd4ccb
source-git-commit: 1f050ada481a7307a59ea6c81290bb0b24a3bf6c
workflow-type: tm+mt
source-wordcount: '2243'
ht-degree: 0%

---

# Veelgestelde vragen over migratie naar openbare cloud{#dc-faq}

![](../../assets/v7-only.svg)

Als onderdeel van het [Gold Standard Initiative](../../rn/using/gold-standard.md) ontmantelt Adobe het oude Data Center. Campaign Classic-instanties moeten worden overgebracht naar AWS (Public Cloud Amazon Web Services). [Meer weten over dit initiatief](dc-migration.md)?

Hieronder vindt u een aantal veelgestelde vragen over dit project, de invloed op uw campagneomgeving en andere nuttige bronnen.

Voor elke andere vraag kunt u [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support) bereiken.

## Infrastructuureffecten

![](assets/do-not-translate/database.png)

De wereldwijde gevolgen voor de database en de infrastructuur worden hieronder vermeld.

* **Zal de database veranderen? Wat is de versie van de nieuwe database? Welk besturingssysteem wordt gebruikt?**

   Adobe behoudt zich het recht voor om de meest geschikte database-beheerengine te kiezen en te implementeren om Adobe Campaign Service onder optimale omstandigheden te bedienen.

   Bovendien zal Adobe, om het beste veiligheidsniveau te handhaven, geen gedetailleerde informatie over de infrastructuur verstrekken.

* **Is er een risico op gegevensverlies?**

   De database wordt uit het oude datacenter verwijderd en hersteld in de Public Cloud (AWS). Wanneer de toepassing opnieuw wordt gestart in het nieuwe datacenter, wordt deze hervat in de toestand die vóór de migratie was. De gebruikers zullen geen verschil zien, behalve dat zullen sommige geplande taken vertraagd zijn.

* **Zijn er verschillen in de grootte van het pakket tussen het oude datacenter en de openbare cloud?**

   In de Public Cloud (AWS) zijn nieuwe pakketdefinities beschikbaar op basis van de huidige databasegrootte, schijfgrootte enzovoort. Als een klant bijvoorbeeld één toepassingsserver in een verouderde datacenter heeft, kunnen deze twee toepassingsservers in de openbare cloud (AWS) hebben op basis van pakketdefinities.

* **Zal het bouwstijlaantal of de versie van de Campagne veranderen?**

   Als eerste stap zullen we dezelfde Campaign Classic opbouwen met migratie.

   In een volgende stap zullen we doorgaan met de upgrade naar de nieuwste Campaign Classic GA-build. Raadpleeg voor meer informatie de [Veelgestelde vragen over upgrades voor build](../../platform/using/faq-build-upgrade.md) en [Opmerkingen bij de release van de Goudstandaard campagne](../../rn/using/gold-standard.md).

* **Wat is het plan om eventuele problemen na migratie aan te pakken?**

   Er zouden uitgebreide tests worden uitgevoerd voordat de productiesystemen migreren. In geval van problemen blijft [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support) echter het belangrijkste contactpunt. Adobe heeft een team van deskundigen ingesteld om indien nodig geavanceerde ondersteuning te bieden.

## Leveringseffecten

![](assets/do-not-translate/features.png)

De wereldwijde gevolgen voor IP&#39;s, lijst van gewezen personen, subdomeinen en URL&#39;s worden hieronder vermeld.

* **Hoe zal IP op de lijst van gewenste personen worden behandeld? Zullen de klanten nieuwe IP adressen aan de lijst van gewenste personen voor inkomend verkeer van Campagne moeten toevoegen?**

   Het IP-adres van de Adobe-servers wordt gewijzigd. Zo kunnen de klanten die nieuwe IP adressen in de lijst van gewenste personen in hun systeem moeten toevoegen.

   [Klik ](#config) hier voor meer details over IP op de lijst van gewenste personen.

* **Hoe zullen wij haven behandelen die aan de lijst van gewenste personen voor toegang SFTP/FTP wordt toegevoegd?**

   SFTP-configuratie (openbare sleutels + IP op de lijst van gewenste personen) wordt ook verplaatst van het oude datacenter naar de openbare cloud (AWS). Geen actie verwacht van de klant.

* **Worden IPs veranderd?**

   Het IP-adres van de Adobe-servers wordt gewijzigd. Zo kunnen de klanten die nieuwe IP adressen aan de lijst van gewenste personen in hun systeem moeten toevoegen.

   [Klik ](#config) hier voor meer details over IP op de lijst van gewenste personen.

* **Hoe zal subdomeindelegatie worden behandeld?**

   Bestaande subdomeinen worden verplaatst van het oude datacenter naar de openbare cloud (AWS). Dit onderdeel wordt door het Adobe-leveringsteam afgehandeld als onderdeel van het migratieproces.

   Adobe begeleidt de klant door de vereiste tests om te controleren of de configuratie na de migratie wordt uitgevoerd op nieuwe servers van de Public Cloud (AWS).

* **Zal de migratie nieuwe URL&#39;s produceren voor tracering, bronnen en webtoepassingen?**

   Nee, bestaande URL&#39;s blijven behouden.

* **Zal er een verandering in subdomain van Neolane.net in campagne.adobe.com zijn?**

   Zowel `neolane.net` als `campaign.adobe.com` worden na de migratie geplaatst. Zo eenvoudig maakt u het: we zullen neolane.net omleiden naar nieuwe instanties in de Public Cloud (AWS), zodat de klant geen wijzigingen hoeft aan te brengen.

* **Wat is het plan voor IP Warm?**

   Allereerst zal de Leverbaarheid van Adobe de status van de leverbaarheid van het platform beoordelen en een plan voor de omschakeling aan nieuwe IPs aanbevelen

   Na de migratie is geen opwarmen vereist. Het kan een uitzondering zijn en in dat geval zal [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support) de klanten bereiken.

   Het is echter de bedoeling om deze operatie transparant te maken voor het bedrijf, in tegenstelling tot de eerste oprijplaat die tijdens het liveproces wordt uitgevoerd.

   Wanneer de migratie volledig is, zal de instantie van de Campagne volledig verschillend het verzenden IPs hebben. Om een vlotte overgang te verzekeren, zal Adobe een oprijving van nieuwe verzendende IPs door verkeer van oude aan nieuwe IPs geleidelijk te schakelen uitvoeren.

* **Bewegen wij over URL op de lijst van gewenste personen?**

   Ja, dit wordt opgeslagen in het dossier van de serverconfiguratie dat van de bron over aan de nieuwe instantie zal worden gekopieerd.

* **Wat zou het effect moeten zijn met ons gedelegeerde subdomein dat we gebruiken om onze communicatie onder de aandacht te brengen?**

   De subdomeinen die worden gebruikt voor marketingcommunicatie blijven hetzelfde. Afhankelijk van de implementatie zijn echter acties aan de clientzijde nodig:
   * In het geval van subdomein delegatie aan Adobe (gebrek), zorgt Adobe voor alle veranderingen en verzekert een naadloze overgang.
   * In het geval van opstelling CNAME (uitzondering), wordt de cliënt gevraagd om veranderingen, in coördinatie met Adobe uit te voeren.

## Gevolgen voor configuratie en connectiviteit

![](assets/do-not-translate/maintenance.png)

### Nota over IP op de lijst van gewenste personen{#config}

Migratie naar openbare cloud wordt geleverd met nieuwe IP&#39;s voor Adobe Campaign-toepassingsservers, zodat het wijzigen van IP-adressen invloed kan hebben op de connectiviteit tussen Adobe-servers en uw informatiesystemen.

![](assets/migration.png)

Laten we de twee gevallen in overweging nemen:

* Binnenkomend verkeer: Alle netwerkactiviteiten die worden geïnitieerd vanaf uw systemen of een andere derde partij naar Adobe Campaign-servers. De configuratie wordt tijdens de migratie door Adobe afgehandeld en vervolgens van de oudere naar de openbare cloud gekopieerd. Dan zal de connectiviteit voor binnenkomend verkeer worden bewaard zoals is na de migratie en geen actie van de kant van de Klant wordt verwacht

* Uitgaand verkeer: Alle netwerkactiviteiten die door Adobe Campaign-servers worden geïnitieerd naar uw Informatiesysteem of een andere derde (bijvoorbeeld: SMS provider). Afhankelijk van veiligheidsbeleid op zijn plaats in uw organisatie, kan IPs die de verrichting van de lijst van gewenste personen van uw Systeem van het Informatie of een andere derde veranderen vereisen

### Algemene effecten

De wereldwijde gevolgen voor configuratie, connectiviteit met andere systemen en producten, API&#39;s en tijdzone worden hieronder vermeld.

* **Zal de migratie connectiviteit aan externe rekeningen beïnvloeden?**

   Ja. Integraties van derden, zoals SMS-providers, moeten nieuwe IP-adressen van Adobe Campaign-toepassingsservers toevoegen aan de lijst van gewenste personen.

* **Zal de migratie invloed hebben op de verbinding met Adobe Analytics via de Genesis-connector? Wat over het toevoegen van de IP van de Campagne adressen aan de lijst van gewenste personen op de kant van Adobe Analytics?**

   IP-adressen van Adobe Campaign-toepassingsservers worden gewijzigd. Deze stap wordt na de migratie afgehandeld door de klantenservice van Adobe.

* **Zal de migratie connectiviteit met andere Adobe oplossingen (AEM, Doel, enz.) beïnvloeden?**

   De integraties zijn een combinatie IP adressen die op de lijst van gewenste personen en de configuratie van de de rekeningsrekening van de Webdienst worden verklaard. Dit wordt geboekt en eigendom van de klantenservice van Adobe.

   Er zullen IP adressen op de lijst van gewenste personen zijn die in de externe oplossing zullen worden vereist aangezien de servers IP van de Toepassing zal veranderen. Deze informatie wordt verstrekt. Andere onderdelen van de integratie zijn gebaseerd op IMS en zouden ongewijzigd moeten werken.

* **Hoe zit het met de klant die niet gekoppeld is aan de organisatie-id voor IMS-integratie?**

   Klanten die geen IMS hebben, krijgen een van deze programma&#39;s: een IMS org ID zal aan hun instantie worden vastgemaakt.

* **Heeft de migratie gevolgen voor configuraties met meerdere merken?**

   Zodra subdomein en alle bijbehorende configuratie correct van het oude datacenter naar de openbare cloud (AWS) worden verplaatst of omgeleid, verwachten we geen effect.

* **Heeft de migratie invloed op de API-connectiviteit?**

   Het IP-adres van de Adobe-servers wordt gewijzigd. Zo kunnen de klanten die nieuwe IP adressen aan de lijst van gewenste personen in hun systeem moeten toevoegen.

   [Klik ](#config) hier voor meer details over IP op lijst van gewenste personen.

* **Zorgen we ervoor dat alle JavaScript-parameters voor geheugenconfiguratie na de migratie correct zijn ingesteld?**

   Instantieconfiguratie wordt gekopieerd van het oude datacenter naar de openbare cloud (AWS), zodat deze waarden na de migratie behouden blijven.

* **Bestaat er enig risico voor de toegang tot bepaalde bestandsextensies?**

   De klant kan wensen om doopvontdossiers, de dossiers van de outlook vergadering toe te staan om in openbare middelenomslag worden geladen. Deze configuratie wordt gedaan in huidig `config-<instance>.xml` dossier. Dit wordt gekopieerd met configuratiebestanden.

* **Verandert de tijdzone op nieuwe server? Kan de klant zijn huidige tijdzone behouden?**

   Het kan veranderen afhankelijk van nieuwe serverplaats. Nochtans zal de klant hun huidige timezone kunnen behouden.

   [Klik ](../../workflow/using/managing-time-zones.md) hier voor meer informatie over tijdzonebeheer in Adobe Campaign Classic v7.


## Beveiliging en machtigingen

![](assets/do-not-translate/security.png)

Met deze migratie naar de Public Cloud (AWS) worden de klantomgevingen bijgewerkt met alle vereiste beveiligingsvereisten. Dit omvat:

* Nieuwste patches voor besturingssysteem en beveiliging op periodieke basis
* Isolatie van infrastructuur per klant
* Beheerde beveiligings- en auditbeoordelingen voor ondersteuning van cloudinfrastructuur, zoals taakverdelingsmechanisme, netwerkbeveiligingsregels en opslagcodering.

De gevolgen voor toestemmingen, certificaten en toegang SFTP zijn hieronder vermeld.

* **Gaan we alle certificaten naar de nieuwe servers verplaatsen?**

   Ja, alle certificaten worden als onderdeel van deze migratie verplaatst.

* **Hebben wij nieuwe STP toegangssleutels van klant nodig?**

   Nee, Adobe kopieert SFTP-toegangstoetsen net als op de nieuwe server.

* **Hoe worden de toestemmingen van SFTP behandeld?**

   We zorgen ervoor dat de nieuwe SFTP-server, gebruikers, mappen en bestanden precies dezelfde machtigingsniveaus hebben.

* **Als SFTP-verbinding niet tot stand kon worden gebracht, wat is dan de oplossing/het plan om de klant operationeel te houden?**

   Het enige connectiviteitsprobleem dat zich kan voordoen, is gerelateerd aan de lijst van gewenste personen aan de kant van de klant. De klant dient deze test op een niet-productieomgeving toe te voegen om ervoor te zorgen dat deze test werkt voordat hij naar de testomgeving overschakelt.

* **Zijn er om het even welke configuraties van de lijst van gewenste personen van het gegevenscentrum specifieke die zich over moeten bewegen?**

   Nee, er is geen datacenterspecifieke configuratie voor lijsten van gewenste personen die u wilt beheren.

* **Zorgen we ervoor dat aangepaste scripts met succes worden uitgevoerd in de nieuwe omgeving?**

   De implementatie van de klant kan douanescripts (Perl/Shell/Python/JavaScript) in werkschema&#39;s gebruiken om dossiers en omslagen bijvoorbeeld te manipuleren.

   Op de gehoste instantie worden scripts alleen uitgevoerd via de JavaScript-engine. Deze specifieke implementaties kunnen veiligheidstekortkomingen en postupgradekwesties veroorzaken. Ze worden niet ondersteund.

* **Werkt IMS-integratie zoals in nieuwe versies of is er een extra configuratieupdate nodig?**

   Aangezien wij de zelfde DNS namen houden, zou het moeten werken zoals na migratie is.


## Migratie-uitvoering

![](assets/do-not-translate/upgrades.png)

De wereldwijde effecten tijdens de migratie worden hieronder vermeld.

* **Moeten we een stopzetting van de marketingactiviteiten tijdens de migratie plannen?**

   Adobe raadt aan alle uitvoeringen te vertragen en idealiter te pauzeren vlak voordat de toepassing wordt afgesloten in het oude datacenter: leveringen en workflows. Hierdoor wordt het opnieuw opstarten op de Cloud Server (AWS) eenvoudiger, omdat processen tijd hebben gekregen om &#39;netjes&#39; te pauzeren en eventuele uitvoeringsstatus in uitvoering op te slaan.

* **Verwachten we downtime van onze Adobe Campaign-service?**

   De migratie zal met een onvermijdelijke platform onderbreking komen. Het doel van dit plan is deze uitvaltijd tot een minimum te beperken.

   De gegevensoverdracht tussen de Centra van Gegevens is op de kritieke weg van onderbreking. De gegevens worden op twee manieren opgeslagen:

   * De database is verreweg het belangrijkste
   * Bestanden op de toepassingsserver (gegevens importeren en exporteren)

   Het verkleinen van de omvang van de database is van het grootste belang om de gegevensoverdracht te versnellen. Suggesties:

   * Verminder de bewaartermijnen van historische gegevens (leveringslogboeken, het volgen logboeken, enz.)
   * Lege records uit andere tabellen verwijderen (leveringen, ontvangers, aangepaste tabellen)


* **Wat is de geschatte downtime voor het migreren van een instantie?**

   De downtime is volledig afhankelijk van de grootte van de database en SFTP-bestandsopslag van de klant. Neem contact op met de klantenservice om een geschatte duur te krijgen.

* **Wat met berichten die van de erfenisserver worden verzonden. Zijn koppelingen altijd toegankelijk?**

   Tijdens het uitvoeren van de migratie blijft slechts één service functioneel: e-mailkoppelingen worden omgeleid. Alle ontvangers kunnen de bestemmingspagina bereiken wanneer ze in een e-mail klikken. Deze kliks worden echter niet bijgehouden, dus klik de tarieven voor de leveringen die kort voor de migratie zijn begonnen lager dan normaal.

* **Hoe zit het met midsoucing-/RT-omgevingen?**

   MID-sourcing en RT worden behandeld als elk ander gehoste stuk infrastructuur.

* **In welke volgorde zullen migraties plaatsvinden?**

   De omgevingen worden in de volgende volgorde gemigreerd:

   1. Ontwikkelomgevingen
   1. Stage-omgevingen
   1. Productieomgevingen
   1. RT-omgevingen
   1. Midden-sourcingomgevingen

* **Wat is het terugdraaiplan?**

   Het plan van het terugschroeven van prijzen is DNS terug te schakelen en brongegevensbestand terug te plaatsen aan read-write van read only. Uiteindelijk zullen we er automatisering voor hebben.

* **Kunnen we na de migratie nog steeds toegang krijgen tot oude gevallen?**

   Wanneer de migratie van de toepassing is voltooid, is er geen plan om een proces opnieuw uit te voeren in het oude datacenter. We verwachten dat alle gegevens in het oude datacenter kunnen worden gewist, behalve voor tijdelijke back-updoeleinden, totdat de geplande back-upprocessen zijn uitgevoerd op de Public Cloud (AWS).

* **Hoeveel tijd is er toegestaan voor het testen van elke instantie na de migratie naar de Public Cloud?**

   Afhankelijk van de complexiteit van de klant is een badtijd van ten minste 1 week vereist tussen de Stage-omgeving en de Production-omgeving.

* **Wie zal het toevoegen van nieuwe IPs aan de lijst van gewenste personen behandelen?**

   Het team van de Zorg van de Adobe Klant zal ervoor zorgen dat de klant en om het even welke derde tot het nieuwe systeem kunnen toegang hebben door nieuwe IPs aan de lijst van gewenste personen toe te voegen.

## Ondersteuning en andere handige koppelingen{#support}

* [Migratie naar door Adobe beheerde services (openbare cloud)](dc-migration.md)
* [Upgrade van gouden standaard](../../rn/using/gs-overview.md)
* [Veelgestelde vragen over upgrade maken](../../platform/using/faq-build-upgrade.md)
