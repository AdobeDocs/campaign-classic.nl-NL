---
product: campaign
title: Veelgestelde vragen over migratie naar Adobe Managed Services (Public Cloud)
description: Veelgestelde vragen over migratie van Campaigns Classic naar openbare cloud
feature: Technote, Upgrade
role: User
level: Beginner
exl-id: a9cd08b0-55c2-4405-9fb8-f0c623cd4ccb
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '2225'
ht-degree: 0%

---

# Veelgestelde vragen over migratie naar openbare cloud{#dc-faq}



Adobe ontmantelt het oude datacenter: instanties van Campaigns Classic moeten worden overgedragen naar de Public Cloud Amazon Web Services (AWS). [ Leer meer over dit initiatief ](dc-migration.md).

Hieronder vindt u een aantal veelgestelde vragen over dit project, de invloed op uw campagneomgeving en andere nuttige bronnen.

Voor een andere vraag, kunt u uit naar [ de Zorg van de Klant van de Adobe ](https://experienceleague.adobe.com/?support-solution=Campaign#support) reiken.

## Infrastructuureffecten

![](assets/do-not-translate/database.png)

De wereldwijde gevolgen voor de database en de infrastructuur worden hieronder vermeld.

* **gaat het gegevensbestand veranderen? Wat is de versie van de nieuwe database? Welk Werkende Systeem zal worden gebruikt?**

  Adobe behoudt zich het recht voor om de meest geschikte database-beheerengine te kiezen en te implementeren om Adobe Campaign Service onder optimale omstandigheden te bedienen.

  Bovendien zal de Adobe, om het optimale veiligheidsniveau te handhaven, geen gedetailleerde informatie over de infrastructuur verstrekken.

* **is er een risico van gegevensverlies?**

  De database wordt uit het oude datacenter verwijderd en hersteld in Public Cloud (AWS). Wanneer de toepassing opnieuw wordt gestart in het nieuwe datacenter, wordt deze hervat in de toestand die vóór de migratie was. De gebruikers zullen geen verschil zien, behalve dat zullen sommige geplande taken vertraagd zijn geweest.

* **zijn er om het even welke verschillen in de grootte van het pakket tussen het Verouderde gegevenscentrum en de Openbare Wolk?**

  In de Public Cloud (AWS) zijn nieuwe pakketdefinities beschikbaar op basis van de huidige databasegrootte, schijfgrootte enzovoort. Als een klant bijvoorbeeld één toepassingsserver in een verouderde datacenter heeft, kunnen deze twee toepassingsservers in de openbare cloud (AWS) hebben op basis van pakketdefinities.

* **gaat het bouwstijlaantal of de versie van de Campagne veranderen?**

  Als eerste stap zullen we hetzelfde Campaign Classic blijven bouwen met migratie.

  In een volgende stap zullen we doorgaan met de upgrade naar de nieuwste Campaign Classic GA-build. Raadpleeg [deze pagina](../../rn/using/rn-overview.md) voor meer informatie.

* **wat is het plan om om het even welke post migratiekwesties te behandelen?**

  Er zouden uitgebreide tests worden uitgevoerd voordat de productiesystemen migreren. Nochtans in het geval van om het even welke kwesties, [&#128279;](https://experienceleague.adobe.com/?support-solution=Campaign#support) de Zorg van de Klant van de Adobe zal het belangrijkste punt van contact blijven.  Adobe heeft een team van deskundigen ingesteld om indien nodig geavanceerde ondersteuning te bieden.

## Afzetbaarheidseffecten

![](assets/do-not-translate/features.png)

De wereldwijde gevolgen voor IP&#39;s, lijst van gewezen personen, subdomeinen en URL&#39;s worden hieronder vermeld.

* **Hoe zal IP op de lijst van gewenste personen worden behandeld? Zullen de klanten nieuwe IP adressen aan de lijst van gewenste personen voor inkomend verkeer van Campagne moeten toevoegen?**

  Het IP adres van de servers van de Adobe zal veranderen. Zo kunnen de klanten die nieuwe IP adressen in de lijst van gewenste personen in hun systeem moeten toevoegen.

  [ leer meer ](#config) over IP op de lijst van gewenste personen.

* **hoe wij haven zullen behandelen die aan de lijst van gewenste personen voor toegang wordt toegevoegd SFTP/FTP?**

  SFTP-configuratie (openbare sleutels + IP op de lijst van gewenste personen) wordt ook verplaatst van het oude datacenter naar de openbare cloud (AWS). Geen actie verwacht van de klant.

* **veranderen wij IPs?**

  Het IP adres van de servers van de Adobe zal veranderen. Zo kunnen de klanten die nieuwe IP adressen aan de lijst van gewenste personen in hun systeem moeten toevoegen.

  [ leer meer ](#config) over IP op de lijst van gewenste personen.

* **hoe subdomain delegatie zal worden behandeld?**

  Bestaande subdomeinen worden verplaatst van het oude datacenter naar de openbare cloud (AWS). Dit onderdeel wordt als onderdeel van het migratieproces afgehandeld door het leveringsteam van de Adobe.

  >[!NOTE]
  >
  >De betrokkenheid van het leveringsteam is gebaseerd op een contract en klanten dienen contact op te nemen met hun Adobe voor informatie over de leveringsservice.

  De Adobe begeleidt de klant door de vereiste tests om ervoor te zorgen dat de configuratie na de migratie wordt uitgevoerd op nieuwe servers van de Public Cloud (AWS).

* **zal de migratie nieuwe URLs voor het volgen, middelen en Webtoepassingen veroorzaken?**

  Nee, bestaande URL&#39;s blijven behouden.

* **zal er een verandering in subdomain van Neolane.net aan campaign.adobe.com zijn?**

  Zowel `neolane.net` als `campaign.adobe.com` zijn na de migratie beschikbaar. Om het eenvoudig te maken: we zullen neolane.net omleiden naar nieuwe instanties in de Public Cloud (AWS), zodat de klant geen wijzigingen hoeft aan te brengen.

* **wat is het plan voor IP Warm?**

  Allereerst zal de Leverbaarheid van de Adobe de leveringsstatus van het platform beoordelen en een plan voor de omschakeling aan nieuwe IPs aanbevelen

  Na de migratie is geen opwarmen vereist. Het zou één of andere uitzondering kunnen zijn en, in zulk geval, zal de [&#128279;](https://experienceleague.adobe.com/?support-solution=Campaign#support) Zorg van de Klant van de Adobe aan klanten bereiken.

  Het is echter de bedoeling om deze operatie transparant te maken voor het bedrijf, in tegenstelling tot de eerste oprijplaat die tijdens het liveproces wordt uitgevoerd.

  Wanneer de migratie volledig is, zal de instantie van de Campagne volledig verschillend het verzenden IPs hebben. Om een vlotte overgang te verzekeren, zal de Adobe een opvoeren van nieuwe verzendende IPs door verkeer van oude aan nieuwe IPs geleidelijk te schakelen uitvoeren.

* **bewegen wij over URL op de lijst van gewenste personen?**

  Ja, dit wordt opgeslagen in het dossier van de serverconfiguratie dat van de bron over aan de nieuwe instantie zal worden gekopieerd.

* **wat het effect met onze gedelegeerde sub-domain zou moeten zijn wij gebruiken om onze mededeling te merken?**

  De subdomeinen die worden gebruikt voor marketingcommunicatie blijven hetzelfde. Afhankelijk van de implementatie zijn echter acties aan de clientzijde nodig:
   * In het geval van subdomein delegatie aan Adobe (gebrek), zorgt de Adobe voor alle veranderingen en verzekert een naadloze overgang.
   * In het geval van opstelling CNAME (uitzondering), wordt de cliënt gevraagd om veranderingen, in coördinatie met Adobe uit te voeren.

## Effecten van configuratie en connectiviteit

![](assets/do-not-translate/maintenance.png)

### Nota over IP op de lijst van gewenste personen{#config}

Migratie naar openbare cloud wordt geleverd met nieuwe IP&#39;s voor Adobe Campaign-toepassingsservers, zodat het wijzigen van IP-adressen invloed kan hebben op de connectiviteit tussen Adobe servers en uw informatiesystemen.

![](assets/migration.png)

Laten we eens kijken naar de twee gevallen:

* Binnenkomend verkeer: alle netwerkactiviteit die van uw systemen of een andere derde aan de servers van Adobe Campaign in werking wordt gesteld. De configuratie wordt tijdens de migratie door de Adobe afgehandeld en vervolgens van de oudere naar de openbare cloud gekopieerd. Dan zal de connectiviteit voor binnenkomend verkeer worden bewaard zoals is na de migratie en geen actie van de kant van de Klant wordt verwacht

* Uitgaand verkeer: Alle netwerkactiviteit die door de servers van Adobe Campaign aan uw Systeem van de Informatie of een andere derde (zoals de leverancier van SMS) in werking wordt gesteld. Afhankelijk van veiligheidsbeleid op zijn plaats in uw organisatie, kan IPs die de verrichting van de lijst van gewenste personen van uw Systeem van het Informatie of een andere derde veranderen vereisen

### Algemene effecten

De wereldwijde gevolgen voor configuratie, connectiviteit met andere systemen en producten, API&#39;s en tijdzone worden hieronder vermeld.

* **zal de connectiviteit van het migratieeffect aan externe rekeningen?**

  Ja. Integraties van derden, zoals SMS-providers, moeten nieuwe IP-adressen van Adobe Campaign-toepassingsservers toevoegen aan de lijst van gewenste personen.

* **Zal de migratie connectiviteit aan Adobe Analytics beïnvloeden gebruikend de schakelaar van de Genesis? Wat over het toevoegen van Campagne IP adressen aan de lijst van gewenste personen op de kant van Adobe Analytics?**

  IP-adressen van Adobe Campaign-toepassingsservers worden gewijzigd. Deze stap wordt na de Adobe afgehandeld door de klantenservice.

* **zal de connectiviteit van het migratieeffect met andere Adobe oplossingen (AEM, Doel, enz.)?**

  De integraties zijn een combinatie IP adressen die op de lijst van gewenste personen en de configuratie van de de rekeningsrekening van de Webdienst worden verklaard. Dit wordt geboekt en eigendom van de Adobe Klantenservice.

  Er zullen IP adressen op de lijst van gewenste personen zijn die in de externe oplossing zullen worden vereist aangezien de servers IP van de Toepassing zal veranderen. Deze informatie wordt verstrekt. Andere onderdelen van de integratie zijn gebaseerd op IMS en zouden ongewijzigd moeten werken.

* **wat over klant die niet in bijlage aan identiteitskaart van de Organisatie voor integratie IMS is?**

  Klanten die geen IMS hebben, krijgen er een: een organisatie-id wordt aan hun exemplaar gekoppeld.

* **zijn multi-branding configuraties beïnvloed door de migratie?**

  Zodra subdomein en alle bijbehorende configuratie correct van het oude datacenter naar de Public Cloud (AWS) worden verplaatst of omgeleid, verwachten we geen effect.

* **wordt API connectiviteit beïnvloed door de migratie?**

  Het IP adres van de servers van de Adobe zal veranderen. Zo kunnen de klanten die nieuwe IP adressen aan de lijst van gewenste personen in hun systeem moeten toevoegen.

  [ leer meer ](#config) over IP op lijst van gewenste personen.

* **zullen wij ervoor zorgen dat alle parameters van de het geheugenconfiguratie van JavaScript correct na de migratie worden geplaatst?**

  Instantieconfiguratie wordt gekopieerd van het oude datacenter naar de openbare cloud (AWS). Deze waarden blijven dus behouden na de migratie.

* **is er om het even welk risico op de toegang tot bepaalde dossieruitbreidingen?**

  De klant kan wensen om doopvontdossiers, de dossiers van de outlook vergadering toe te staan om in openbare middelenomslag worden geladen. Deze configuratie wordt uitgevoerd in het huidige `config-<instance>.xml` -bestand. Dit wordt gekopieerd met configuratiebestanden.

* **Verandert de tijdzone op nieuwe server? Zal de klant hun huidige timezone kunnen behouden?**

  Het kan veranderen afhankelijk van nieuwe serverplaats. Nochtans zal de klant hun huidige timezone kunnen behouden.

  [ leer meer ](../../workflow/using/managing-time-zones.md) over timezone beheer in Adobe Campaign Classic v7.


## Beveiliging en machtigingen

![](assets/do-not-translate/security.png)

Met deze migratie naar Public Cloud (AWS) worden de klantomgevingen bijgewerkt met alle vereiste beveiligingsvereisten. Dit omvat:

* Nieuwste patches voor besturingssysteem en beveiliging op periodieke basis
* Isolatie van infrastructuur per klant
* Beheerde beveiligings- en auditbeoordelingen voor ondersteuning van cloudinfrastructuur, zoals taakverdelingsmechanisme, netwerkbeveiligingsregels en opslagcodering.

De gevolgen voor toestemmingen, certificaten en toegang SFTP zijn hieronder vermeld.

* **gaan wij alle certificaten naar de nieuwe servers verplaatsen?**

  Ja, alle certificaten worden als onderdeel van deze migratie verplaatst.

* **hebben wij nieuwe STP toegangssleutels van klant nodig?**

  Nee, Adobe kopieert SFTP-toegangstoetsen net als op de nieuwe server.

* **hoe worden de toestemmingen van SFTP behandeld?**

  We zorgen ervoor dat de nieuwe SFTP-server, gebruikers, mappen en bestanden precies dezelfde machtigingsniveaus hebben.

* **als de verbinding SFTP niet kon worden gevestigd toen wat de aanzet/plan is om klant operationeel te houden?**

  Het enige connectiviteitsprobleem dat zich kan voordoen, is gerelateerd aan de lijst van gewenste personen aan de kant van de klant. De klant dient deze test op een niet-productieomgeving toe te voegen om ervoor te zorgen dat deze test werkt voordat hij naar de testomgeving overschakelt.

* **zijn er om het even welke specifieke configuraties van de lijst van gewenste personen van het gegevenscentrum die over moeten bewegen?**

  Nee, er is geen datacenterspecifieke configuratie voor lijsten van gewenste personen die u wilt beheren.

* **verzekeren wij dat de douanescripts met succes in het nieuwe milieu zullen worden uitgevoerd?**

  De implementatie van de klant kan douanescripts (Perl/Shell/Python/JavaScript) in werkschema&#39;s gebruiken om dossiers en omslagen bijvoorbeeld te manipuleren.

  Op de gehoste instantie worden scripts alleen uitgevoerd via de JavaScript-engine. Deze specifieke implementaties kunnen veiligheidstekortkomingen en postupgradekwesties veroorzaken. Ze worden niet ondersteund.

* **met integratie IMS, zal het werken zoals in nieuwe instantie is of zal om het even welke extra configuratieupdate nodig zijn?**

  Aangezien wij de zelfde DNS namen houden, zou het moeten werken zoals na migratie is.


## Migratie-uitvoering

![](assets/do-not-translate/upgrades.png)

De wereldwijde effecten tijdens de migratie worden hieronder vermeld.

* **moeten wij het tegenhouden van de activiteit van de Marketing tijdens de migratie plannen?**

  Adobe raadt aan alle uitvoeringen te vertragen en idealiter te pauzeren vlak voordat de toepassing wordt afgesloten in het oude datacenter: leveringen en workflows. Hierdoor wordt het opnieuw opstarten op de Cloud Server (AWS) eenvoudiger, omdat processen tijd hebben gekregen om &#39;netjes&#39; te pauzeren en eventuele uitvoeringsstatus in uitvoering op te slaan.

* **verwachten wij onderbreking van onze dienst van Adobe Campaign?**

  De migratie zal met een onvermijdelijke platform onderbreking komen. Het doel van dit plan is deze uitvaltijd tot een minimum te beperken.

  De gegevensoverdracht tussen de Centra van Gegevens is op de kritieke weg van onderbreking. De gegevens worden op twee manieren opgeslagen:

   * De database is verreweg het belangrijkste
   * Bestanden op de toepassingsserver (gegevens importeren en exporteren)

  Het verkleinen van de omvang van de database is van het grootste belang om de gegevensoverdracht te versnellen. Suggesties:

   * Verminder de bewaartermijnen van historische gegevens (leveringslogboeken, het volgen logboeken, enz.)
   * Lege records uit andere tabellen verwijderen (leveringen, ontvangers, aangepaste tabellen)

* **wat is de geschatte onderbreking voor het migreren van een instantie?**

  De downtime is volledig afhankelijk van de grootte van de database- en SFTP-bestandsopslag van de klant. Neem contact op met de klantenservice om een geschatte duur te krijgen.

* **wat over berichten die van de erfenisserver worden verzonden. Zullen de verbindingen altijd toegankelijk zijn?**

  Tijdens het uitvoeren van de migratie blijft slechts één service actief: e-mailkoppelingen worden omgeleid. Alle ontvangers kunnen de bestemmingspagina bereiken wanneer ze in een e-mail klikken. Deze kliks worden echter niet bijgehouden, dus klik de tarieven voor de leveringen die kort voor de migratie zijn begonnen lager dan normaal.

* **wat over midde-bron/milieu&#39;s RT?**

  MID-sourcing en RT worden behandeld als elk ander gehoste stuk infrastructuur.

* **welke orde binnen migraties zal worden gedaan?**

  De omgevingen worden in de volgende volgorde gemigreerd:

   1. Ontwikkelomgevingen
   1. Stage-omgevingen
   1. Productieomgevingen
   1. RT-omgevingen
   1. Midsourcingomgevingen

* **wat is het terugschroeven van prijzenplan?**

  Het plan van het terugschroeven van prijzen is DNS terug te schakelen en brongegevensbestand terug te plaatsen aan read-write van read only. Uiteindelijk zullen we er automatisering voor hebben.

* **Na de migratie, kunnen wij nog tot oude instanties toegang hebben?**

  Wanneer de migratie van de toepassing is voltooid, is er geen plan om een proces opnieuw uit te voeren in het oude datacenter. We verwachten dat alle gegevens in het oude datacenter kunnen worden gewist, behalve voor tijdelijke back-updoeleinden, totdat de geplande back-upprocessen zijn uitgevoerd op Public Cloud (AWS).

* **hoeveel tijd voor het testen van elke instantie na migratie aan Openbare Cloud zal worden toegestaan?**

  Afhankelijk van de complexiteit van de klant is een badtijd van ten minste 1 week vereist tussen de Stage-omgeving en de Production-omgeving.

* **wie zal behandelen toevoegend nieuwe IPs aan de lijst van gewenste personen?**

  Het team van de Zorg van de Klant van de Adobe zal ervoor zorgen dat de klant en om het even welke derden tot het nieuwe systeem kunnen toegang hebben door nieuwe IPs aan de lijst van gewenste personen toe te voegen.

## Ondersteuning en andere handige koppelingen{#support}

* [Migratie naar Adobe Managed Services (Public Cloud)](dc-migration.md)
* [Jaarlijkse upgrade van campagne](../../rn/using/rn-overview.md#yeary-upgrade)
* [Veelgestelde vragen over upgrade maken](../../platform/using/faq-build-upgrade.md)
