---
product: campaign
title: Aanbevelingen voor hardwareaanpassing voor Campaign Classic v7
description: Aanbevelingen voor hardwareaanpassing voor Campaign Classic v7
feature: Technote
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: c47e73a0-dbd8-43f5-a363-7e6783dc7685
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '2519'
ht-degree: 1%

---

# Aanbevelingen voor hardwareaanpassing{#hardware-sizing-reco}



## Overzicht

>[!CAUTION]
>
>Dit artikel is alleen bedoeld als algemene voorbeeldgids. U moet contact opnemen met uw Adobe Campaign Customer Success Manager om de exacte grootte van uw implementatie te meten voordat u uw Campagne-project start. **Niet gebruiken** infrastructuur of hardware aanschaffen of implementeren totdat dit gebeurt.

Dit document bevat algemene aanbevelingen voor Adobe Campaign Classic v7-implementatie in uw on-premise datacenter of gevirtualiseerde cloud-omgeving. Dit soort inzet, waarnaar wordt verwezen als **hybride** of **midsourcing**, plaatst u de marketinginstantie en de marketingdatabase van Campagne onder uw controle en gebruikt u de services van Adobe Cloud Messaging om e-mails, SMS- of SMPP-berichten te verzenden en e-mail te verzamelen die is geopend, stuit en klik op volggegevens.

De marketinginstantie is het deel van de Adobe Campaign-architectuur dat alle marketingactiviteiten stuurt en alle gegevens van de ontvanger en de analytische gegevens opslaat die door campagnes worden geretourneerd. De marketinginstantie is een set on-premise servers waarop Adobe Campaign-services worden uitgevoerd, en een relationele database.

>[!CAUTION]
>
>De informatie in dit document is niet van toepassing als u een volledig gehoste Adobe Campaign-instantie gebruikt (geïmplementeerd in Adobe-Cloud Services).

Softwarecompatibiliteit wordt nader beschreven in het gedeelte [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).


### Scenarios

De diagrammen van de plaatsing en de aanbevelingen van de hardwarerangschikking worden verstrekt voor drie representatieve scenario&#39;s:

1. [Gemiddelde grootte](#scenario-1) - 5 miljoen actieve ontvangers in het systeem
1. [Groot](#scenario-2) - 20 miljoen actieve ontvangers in het systeem
1. [Enterprise](#scenario-3) - 50 miljoen actieve ontvangers, met transactieberichten

### Veronderstellingen

Dit document veronderstelt ook de volgende types van gebruik voor alle drie scenario&#39;s:

* Twee keer per week worden grote e-mailcampagnes verzonden naar ongeveer 50% van de actieve ontvangers
* Directe post wordt geproduceerd eens per maand voor elke ontvanger in het systeem
* SMS-berichten worden elke maand naar ongeveer 10% van de actieve ontvangers verzonden
* Het databaseschema dat elke ontvanger definieert, is uitgebreid met één extra tabel, die ongeveer 200 bytes aan gegevens voor elke ontvanger bevat
* De Adobe Campaign-interactiemodule wordt gebruikt om aanbiedingen toe te voegen aan uitgaande e-mail
* Gegevens voor e-mailtracking worden 90 dagen bewaard in het campagnesysteem

## Algemene richtsnoeren

Campagne is een database-centric toepassing, en de prestaties van de gegevensbestandserver zijn kritiek. De lopende werkschema&#39;s, segmentatie, het volgen van gegevens uploadt, binnenkomende Interacties, analyses en andere activiteiten allen produceren gegevensbestandactiviteit. Over het algemeen bepalen de grootte en frequentie van deze bewerkingen de grootte van uw databaseservers.

De toepassingsservers in uw marketinginstantie vereisen voldoende CPU en geheugen om workflows uit te voeren en te reageren op SOAP API-aanroepen, inclusief verzoeken van Campagnegebruikers. De vereisten van cpu kunnen voor werkschema&#39;s significant zijn die uitgaande interactie met complexe aanbiedingsregels, werkschema&#39;s gebruiken die douaneJavaScript, en Webtoepassingen met hoge verkeersniveaus uitvoeren.

Campagne-webtoepassingen kunnen ook worden geïmplementeerd op de App-servers voor marketinginstanties of op afzonderlijke webserversystemen. Omdat werklasten van webtoepassingen conflicteren met kritieke workflows en Campagnegebruikers, kunnen webtoepassingen en binnenkomende interacties worden geïmplementeerd op afzonderlijke servers om ervoor te zorgen dat de functionaliteit van de kerncampagne betrouwbaar werkt met goede prestaties.

Voor veiligheid en beschikbaarheid, adviseert Adobe het scheiden van het verkeer van Internet van het verkeer dat door de bedrijfsgebruikers wordt geproduceerd. Om die reden, bevatten de diagrammen twee groepen servers: de server van het Web (Internet die Web1 en Web2 onder ogen ziet), en de servers van de App (bedrijfsprocessen App1 en App2).

Het is een wettelijke vereiste voor commerciële e-mailzenders om een functionele opt-out-webpagina te hebben. Adobe raadt u aan om voor failover-scenario&#39;s in elke groepsserver een redundante computer op te nemen. Dit geldt vooral als Adobe Campaign de pagina&#39;s voor niet-deelname host.

### Proxy&#39;s omkeren

De architectuur van de Campagne dwingt hoge veiligheid af door SSL over HTTP (HTTPS) te gebruiken om tussen uw marketing instantie en het Overseinen van de Wolk van Adobe te communiceren. De veiligheid, de betrouwbaarheid, en de beschikbaarheid worden afgedwongen door omgekeerde volmachten in &quot;gedemilitariseerde streek&quot;(DMZ) subnet te gebruiken om de marketing instantieservers en het gegevensbestand te isoleren en te beveiligen.

### Load balancer

Het taakverdelingsmechanisme voor de servers App wordt opstelling in een actieve/passieve configuratie, met HTTPS geëindigd bij de volmacht. Het taakverdelingsmechanisme voor de servers van het Web wordt opstelling in een actieve/actieve configuratie, met HTTPS geëindigd bij de volmacht.

Adobe biedt u de exclusieve lijst met URL-paden die u kunt afspelen op de Adobe Campaign-server in uw implementatieomgeving.

### Architectuur

De algemene architectuur is vrijwel identiek, ongeacht de volumes. De veiligheids en hoge beschikbaarheidsvereisten bepalen een minimum van vier servers; twee servers als geen WebApps wordt gebruikt. Het verschil in configuratie varieert hoofdzakelijk in de hardwareconfiguratie zoals de kern van cpu en geheugen.

## Scenario 1: Moderne Plaatsing{#scenario-1}

![](assets/scenario-1.png)

Geraamd volume:

| Kanaal | Volume |
| ----------------------- | ----------------- |
| Actieve ontvangers | 5 miljoen |
| Email | 4,2 miljoen/maand |
| Direct mail | 1 miljoen/maand |
| Mobiele SMS | 100.000/maand |
| Maximale dagelijkse e-mailvolume | 500 |

Voor deze volumes biedt een paar Adobe Campaign-toepassingsserversystemen alle functionaliteit voor Adobe Campaign Client-gebruikers en workflowuitvoering. Voor 5 miljoen actieve ontvangers en dit e-mailvolume zijn de werklasten van de toepassingsserver niet CPU- of I/O-intensief; het grootste deel van de belasting ligt in de database.

De servers van het Web van Adobe Campaign worden getoond in de veilige streek.

### Web- en toepassingsservers

In dit scenario wordt aangeraden Adobe Campaign op vier computers te installeren, met de volgende specificatie:

**3Ghz+ quad-core CPU, 8-GB RAM, RAID 1 of 10, 2 x 80-GB SSD**

Deze systemen creëren de Server van de toepassing van de marketinginstantie, die direct uw gebruikers van de Console van de Campagne steunt en de campagnewerkschema&#39;s uitvoert.

Reverse volmachten in een DMZ verkeer van de ladingsbalans aan de servers van het Web van Adobe Campaign. De Adobe Campaign-softwarestack hoeft niet te worden geïnstalleerd op proxycomputers. Eventuele reverse-proxysoftware of netwerkapparatuur kan worden gebruikt.

De functies voor het kiezen voor een abonnement of het weigeren en het instellen van een voorkeurscentrum kunnen via de campagne of via uw eigen website worden aangeboden. Als u ervoor kiest om deze functionaliteit op uw website te implementeren, moet u ervoor zorgen dat voorkeur- en abonnementsgegevens worden doorgegeven aan de marketingdatabase voor campagnes. Dit gebeurt gewoonlijk door extractiebestanden te maken die automatisch worden geüpload door campagneworkflows.

Het verbruik van schijfruimte op toepassingsservers is afhankelijk van de bewaarperiode van bestanden die worden uitgewisseld met externe servicebureaus (bijvoorbeeld leveranciers van gedrukte publicaties voor Direct Mail) en van de grootte en het behoud van geïmporteerde platte bestanden, zoals abonnements- of voorkeursupdates van uw website, of van extracten van uw eigen CRM- of marketingsystemen.

### Database

De aanbevelingen van de hardware voor de gegevensbestandserver zijn als volgt:

**3 GHz+ 4-core CPU, 16-GB RAM, RAID 1 of 10, 128 GB SSD minimaal**

De geheugenschatting gaat uit van volledige caching van ongeveer 500.000 ontvangers voor een grote campagnelancering, plus RDBMS bufferruimte voor het uitvoeren van werkschema&#39;s, het invoeren van volggegevens, en andere gezamenlijke activiteiten.

Er wordt geschat dat de schijfruimte die nodig is voor de database voor het opslaan van alle technische gegevens van Adobe Campaign (campagnes, bijhouden, werktabellen enzovoort), ongeveer 35 GB is op basis van een bewaarperiode van drie maanden. Als u ervoor kiest om de volgende gegevens gedurende 6 maanden te behouden, neemt de databasegrootte toe tot ongeveer 40 GB en bij een bewaarperiode van 12 maanden neemt de databasegrootte toe tot ongeveer 45 GB. De ontvangende gegevens verbruiken ongeveer 5 GB voor deze omgeving.

>[!CAUTION]
>
>In deze schatting zijn geen aanvullende klantgegevens opgenomen. Als u van plan bent om extra kolommen of lijsten van klantengegevens in het gegevensbestand van Adobe Campaign te herhalen, dan moet u de extra behoefte van de schijfruimte voor het schatten. Geüploade segmenten/lijsten vereisen ook meer opslag, afhankelijk van hun grootte, frequentie en retentieperiode.

Houd er ook rekening mee dat vanwege het dagelijks verwerkte gegevensvolume de IOPS van de databaseserver van essentieel belang is. Bijvoorbeeld, op een piekdag, kunt u campagnes opstellen die in totaal 500.000 ontvangers richten. Om elke campagne uit te voeren, neemt Adobe Campaign 500.000 verslagen in een lijst op die ruwweg 12 miljoen verslagen (de lijst van het leveringslogboek) bevatten. Om acceptabele prestaties tijdens de campagnemplementatie te bieden, adviseert Adobe een minimum van 60.000 4-KB Willekeurige lees-schrijfIOPS voor dit scenario.


## Scenario 2: grootschalige implementatie{#scenario-2}

![](assets/scenario-2.png)

Geraamd volume:

| Kanaal | Volume |
| ----------------------- | ----------------- |
| Actieve ontvangers | 20 miljoen |
| Email | 42 miljoen per maand |
| Direct mail | 10 miljoen/maand |
| Mobiele SMS | 1.000.000/maand |
| Maximale dagelijkse e-mailvolume | 5,000,000 |

### Web- en toepassingsservers

In dit scenario raadt Adobe aan Adobe Campaign te installeren op vier computers, twee toepassingsservers en twee webservers, met de volgende specificatie:

**3Ghz+ quad-core CPU, 8-GB RAM, RAID 1 of 10, 80-GB SSD**

De toepassingsservers ondersteunen rechtstreeks de gebruikers van de Campagne Console en de uitvoering van campagneworkflows. Deze functionaliteit wordt opgesteld op twee identieke servers voor hoge beschikbaarheid, delend een netwerk-Attached Storage (NAS) dossiersysteem om failover toe te laten.

De servers van het Web ontvangen het Webtoepassingen van de Campagne die de 10 miljoen actieve ontvangers in het systeem steunen.

Zie [Scenario 1: Moderne Plaatsing](#scenario-1) voor meer opmerkingen over proxy&#39;s, voorkeurscentra/abonnementsafhandeling en schijfruimtegebruik.

### Database

De aanbevelingen van de hardware voor de gegevensbestandserver zijn als volgt:

**3 GHz+ 8-core CPU, 64-GB RAM, RAID 1 of 10, 2 x 320-GB SSD of RAID 10, minimaal 640 GB SSD**

De geheugenschatting gaat uit van volledige caching van ongeveer 5.000.000 ontvangers voor een grote lancering van de campagne, plus RDBMS bufferruimte voor het uitvoeren van werkschema&#39;s, het invoeren van volggegevens, en andere gezamenlijke activiteiten.

Er wordt geschat dat de schijfruimte die nodig is voor de database voor het opslaan van alle technische gegevens van Adobe Campaign (campagnes, bijhouden, werktabellen enzovoort), ongeveer 280 GB is op basis van een bewaarperiode van 3 maanden. Als u ervoor kiest om de volgende gegevens gedurende 6 maanden te behouden, neemt de databasegrootte toe tot ongeveer 450 GB en bij een bewaarperiode van 12 maanden neemt de databasegrootte toe tot ongeveer 900 GB. De ontvangende gegevens verbruiken ongeveer 15 GB voor deze omgeving.

## Scenario 3: De Plaatsing van de onderneming met het Centrum van het Bericht{#scenario-3}

![](assets/scenario-3.png)

Geraamd volume:

| Kanaal | Volume |
| ----------------------- | ----------------- |
| Actieve ontvangers | 50 miljoen |
| Email | 108 miljoen per maand |
| Direct mail | 25 miljoen per maand |
| Mobiele SMS | 2,5 miljoen/maand |
| Transactionele berichten | 2,5 miljoen/maand |
| Maximale dagelijkse e-mailvolume | 2,5 miljoen |


De plaatsing die 50 miljoen ontvangers steunt is hoofdzakelijk het zelfde zoals aangetoond in [Scenario 2](#scenario-2): Het verkeer van de Webtoepassing van de campagne wordt verpletterd aan de Webservers van de Campagne, zodat de uitbarstingen van Webverkeer na grote campagnelanceringen niet de werkschema&#39;s van de Campagne en de gebruikers van de Console van de Cliënt beïnvloeden.

Deze plaatsing omvat ook de vraag van het Centrum van het Bericht, die van uw eigen websites en toepassingen wordt gedreven.


### Web- en toepassingsservers

In dit scenario raadt Adobe aan Adobe Campaign als volgt op vier computers te installeren:

* Toepassingsservers
  **Twee systemen, 3GHz+ quad-core CPU, 8-GB RAM, RAID 1 of 10, 80-GB SSD**

* Webservers
  **Twee systemen, 3GHz+ quad-core CPU, 16-GB RAM, RAID 1 of 10, 80-GB SSD**


De toepassingsservers ondersteunen rechtstreeks de gebruikers van de Campagne Console en de uitvoering van campagneworkflows. Deze functionaliteit wordt opgesteld op twee identieke servers voor hoge beschikbaarheid, delend een netwerk-Attached Storage (NAS) dossiersysteem om failover toe te laten.

De servers van het Web ontvangen het Webtoepassingen van de Campagne die de 10 miljoen actieve ontvangers in het systeem steunen.

Zie [Scenario 1: Moderne Plaatsing](#scenario-1) voor meer opmerkingen over proxy&#39;s, voorkeurscentra/abonnementsafhandeling en schijfruimtegebruik.

### Database

De aanbevelingen van de hardware voor de gegevensbestandserver zijn als volgt:

**3 GHz+ 8-core CPU, 96-GB RAM, RAID 1 of 10, minimaal 1,5 TB SSD**

De geheugenschatting gaat uit van volledige caching van ongeveer 12.500.000 ontvangers voor een grote lancering van de campagne, plus RDBMS bufferruimte voor het uitvoeren van werkschema&#39;s, het invoeren van volggegevens, en andere gezamenlijke activiteiten.

Er wordt geschat dat de schijfruimte die nodig is voor de database voor het opslaan van alle technische gegevens van Adobe Campaign (campagnes, bijhouden, werktabellen enzovoort), ongeveer 700 GB is op basis van een bewaarperiode van 3 maanden. Als u ervoor kiest om het volgen gegevens voor 6 maanden te behouden, neemt de gegevensbestandgrootte tot ongeveer 1.2TB toe, en 12 maandenbehoud verhoogt gegevensbestandgrootte tot ongeveer 2TB. De ontvangende gegevens verbruiken ongeveer 50 GB voor deze omgeving.

## Richtlijnen voor het wijzigen van veronderstellingen

De aannames die voor deze scenario&#39;s zijn gemaakt, hebben allemaal een aanzienlijke invloed op de hardwareaanbevelingen en de implementatiearchitectuur. In deze sectie worden de richtlijnen rond verschillende veronderstellingen besproken. Neem contact op met het Adobe Campaign Consulting-team voor specifieke aanbevelingen om aan uw vereisten te voldoen.

* **Aantal ontvangers**
De actieve ontvangers vereisen zowel opslagruimte als ruimte van de gegevensbestandbuffer, zodat meer ontvangers over het algemeen meer geheugen en capaciteit van cpu op de gegevensbestandserver vereisen. Opslagverhogingen zijn relatief klein voor de ontvangers zelf, maar kunnen van belang zijn voor de gegevens voor het bijhouden van gebeurtenissen die worden bijgehouden voor e-mailcampagnes.

* **Grootte e-mailcampagne**
De frequentie van het lanceren van de campagne heeft een invloed op de vereisten van de gegevensbestandserver van cpu. Gecombineerd met directe post, binnenkomende Interacties, en andere werkschema&#39;s, plaatsen de segmenteringsverrichtingen voor e-mailcampagnes een significante lading op de gegevensbestandserver.

* **Directe e-mailfrequentie**
De frequentie van directe mailings kan de vereisten van CPU van de gegevensbestandserver beïnvloeden. Gecombineerd met campagnelanceringen en andere werkschema&#39;s, zetten de segmenteringsverrichtingen voor directe post een significante lading op de gegevensbestandserver.

* **SMS-berichtenvolume**
Net als de grootte van de e-mailcampagne worden met SMS-berichten geen grote hoeveelheden geladen op Campagneservers die zich op locatie bevinden. De bestanden worden vooral geladen op Adobe Cloud Messaging-servers in de cloud. Segmentering voor SMS-campagnes, zoals e-mail en direct mail, kan een aanzienlijke belasting voor de marketingdatabase betekenen. Daarom zijn de frequentie van de lanceringen van de campagne van SMS en de ingewikkeldheid van segmentatie relevanter dan het volume van SMS berichten.

* **Complexiteit databaseschema**
De hoeveelheid gegevens voor elke actieve ontvanger vereist zowel opslagruimte als databasebufferruimte, zodat meer ontvangers over het algemeen meer geheugen en CPU op de databaseserver nodig hebben. De complexe schema&#39;s vereisen ook meer lijsten om voor segmentatie worden aangesloten, zodat kunnen de segmentatieverrichtingen veel langzamer lopen, en vereisen meer gegevensbestandcpu en geheugen wanneer het gegeven over veelvoudige lijsten wordt verspreid.

  Het geheugen van de de serverserver van het gegevensbestand wordt geschat door ervoor te zorgen dat de pool van de gegevensbestandbuffer groot genoeg kan zijn om alle ontvankelijke gegevens, plus tijdelijke lijsten voor het runnen van werkschema&#39;s, plus een marge voor andere gegevensbestandverrichtingen te bevatten.

* **Het uitgaande Gebruik van de Interactie**
De regels voor Interactie op partijwijze worden geëvalueerd in werkschema&#39;s die alle berekeningsingewikkeldheid aan het gegevensbestand overdragen. De belangrijkste factor van inspanning voor de database is het totale aantal in aanmerking komende aanbiedingen dat tijdens één motoroproep is berekend (doelgrootte X gemiddeld aantal aanbiedingen per ontvanger voordat de beste N-aanbiedingen worden gehouden). De CPU-snelheid van de databaseserver is de eerste factor in prestaties.

* **Binnenkomende interacties of SOAP API-gebruik**
De binnenkomende regels en de aanbiedingen van de Interactie worden geëvalueerd in het marketing gegevensbestand, die significante middelen van de gegevensbestandserver, vooral cpu vereisen. Het zware gebruik van binnenkomende Interacties of APIs van de ZEEP vereist afzonderlijke Webservers om het werklading van het runnen van de werkschema&#39;s van de Campagne te scheiden.

* **Bewaarperiode van gegevens bijhouden**
Het verhogen van het behoud van het volgen van gegevens na 90 dagen vereist meer gegevensbestandopslag, en kan het systeem vertragen omdat het opnemen van nieuwe het volgen gegevens in grote lijsten gaat. Het bijhouden van gegevens is niet nuttig voor campagnesegmentatie na 90 dagen, dus de kortere retentieperiode wordt aanbevolen.

  Trackinggegevens moeten worden overgebracht naar Adobe Analytics of een ander analysesysteem als u een langetermijnanalyse van de marketingervaring van de geadresseerde nodig hebt.

## Virtualisatie

Alle campagnemeservers zijn goede kandidaten voor virtualisatie. Er moeten verschillende problemen worden opgelost om een passende beschikbaarheid en prestaties te garanderen.

* **Configuratie van mislukking**
Gegroepeerde servers, bijvoorbeeld, overtollige toepassingsservers onder een lading-in evenwicht gebrachte volmacht, moeten op afzonderlijke hardware worden opgesteld om ervoor te zorgen dat beide VMs niet daalt als er hardwaremislukking is.

* **I/O-configuratie**
Elke aanbevolen RAID-configuratie moet worden onderhouden voor databasebeveiliging, om te voorkomen dat gegevensverlies optreedt bij een opslagapparaat.

* **I/O-prestaties**
De aanbevolen IOPS-classificatie voor databaseopslag moet in acht worden genomen. Cloudservices zoals Amazon EC2 leveren mogelijk niet de vereiste prestaties en moeten zorgvuldig worden geëvalueerd. De Amazon EC2-volumes voor SSD-voorzieningen worden momenteel bijvoorbeeld op elk 20.000 IOPS beoordeeld. Meer informatie in [Amazon-documentatie](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html)), dus een 4-volume RAID-configuratie zou worden beoordeeld op 80.000 IOPS, wat wellicht niet voldoende is.

Adobe raadt aan om voor elke gevirtualiseerde implementatie van Adobe Campaign prestatietests uit te voeren voordat het systeem in productie wordt genomen.

## Verwante onderwerpen

* [Campagne-bewakingsprocessen](../../production/using/monitoring-processes.md)
* [Algemene architectuur van campagne](../../installation/using/general-architecture.md)
* [Prestaties en productieproblemen](../../production/using/performance-and-throughput-issues.md)
* [Controlelijst voor beveiliging en privacy](../../installation/using/get-started-security-privacy.md)
