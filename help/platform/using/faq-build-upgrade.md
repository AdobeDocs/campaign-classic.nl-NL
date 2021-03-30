---
solution: Campaign Classic
product: campaign
title: Veelgestelde vragen over upgrades samenstellen
description: Algemene vragen met betrekking tot upgrades van de Campagne-build
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 7b1e6dd00943e10dff693d78b3aa7cf2ad3e6727
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 3%

---


# Veelgestelde vragen over upgrades maken {#build-upgrade-faq}

Adobe Campaign wordt regelmatig bijgewerkt. Als u bekend bent met onze gepubliceerde [Opmerkingen bij de release](../../rn/using/rn-overview.md), bent u zich waarschijnlijk bewust van het feit dat gemiddeld 2/3 kleine versies met nieuwe functies, verbeteringen en oplossingen elk jaar worden uitgebracht. Bovendien brengen wij periodiek versies uit met uitsluitend cumulatieve oplossingen. Deze regelmatige afwezigheid van updates is erop gericht om de nieuwste en grootste in uw handen te krijgen, uw omgeving volledig veilig te houden en duidelijk uw ervaring met ons product te verbeteren.

Het is essentieel dat onze klanten de meest recente versie van Adobe Campaign uitvoeren. Het staat ook Adobe toe om veel efficiënter te helpen in het geval u op kwesties loopt - het identificeren van, het reproduceren van en het bevestigen van een kwestie op een oude bouwstijl typisch meer tijd vergt, om niet te vermelden dat sommige kwesties u zou kunnen ontmoeten reeds zeer goed in een recente bouwstijl zijn opgelost.

[!DNL Gold Standard] is de Campaign Classic-supportrelease voor de lange termijn. Als gehoste [!DNL Gold Standard] gebruiker, profiteert u automatisch van [!DNL Gold Standard] verbetering met de recentste stabiele versie zonder enige actie. Klanten op locatie en Hybride kunnen ook profiteren van [!DNL Gold Standard]-releases. Als u van een oude build migreert, adviseren wij u eerst bij te werken naar deze versie. [Meer informatie](../../rn/using/gs-overview.md).

## Wat is een bouwstijlverbetering?

Een Build Upgrade wordt uitgevoerd wanneer de Adobe Campaign Classic-software wordt bijgewerkt naar het nieuwste beveiligde buildnummer, maar blijft op hetzelfde niveau voor &#39;main/minor&#39;. Bijvoorbeeld: Campaign Classic v7 build 9026 to Campaign v7 build 9032.

Meer informatie [in deze sectie](../../rn/using/rn-overview.md).

## Wat is de nieuwste versie van Adobe Campaign Classic?

De meest recente versie van Campaign Classic, inclusief nieuwe functies en documentatie, vindt u in de meest recente [Release-notities](../../rn/using/latest-release.md).

## Hoe weet ik welke versie ik heb?

Controleer uw versie via het menu **[!UICONTROL Help > About...]** in de Adobe Campaign Client Console. Het tekstvak **[!UICONTROL About]** bevat gedetailleerde informatie over de versie en build die u uitvoert voor zowel de console als de server.

Meer informatie [in deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Wat betekent de bouwstijlstatus?

Vanaf Campaign Classic 19.2, wordt een status geassocieerd aan elke bouwstijl.

Meer informatie [in deze sectie](../../rn/using/rn-overview.md).

## Is een bouwstijlverbetering het zelfde ding zoals een versieverbetering?

Nee. Een bouwstijlverbetering is een stijgende update binnen een bepaalde belangrijke versie, terwijl een versieverbetering een verandering van één belangrijke versie aan een andere is. De verbeteringen van de bouw zijn ongecompliceerd aangezien zij typisch geen belangrijke architecturale, technische of gegevensmodelveranderingen impliceren.

De verbeteringen van de versie aan de andere kant komen gewoonlijk met significante technische veranderingen en, afhankelijk van de diepte van de configuratie voor een bepaalde klant, kunnen significante configuratieveranderingen en/of gedeeltelijke herimplementatie vereisen.

Bijvoorbeeld, gebruikend de serverinformatie van het het schermschot in de vorige sectie:

* Een bouwstijlverbetering zou het bewegen van bouwstijl 6880 aan om het even welke bouwstijl groter dan 6880 impliceren. Versie 6.1.1-build 8222 tot v6.1.1-build 8666

* Bij een versieverbetering wordt overgeschakeld van versie 6.0.2 naar een versie die hoger is dan versie 6.0.2.  Bijvoorbeeld: v6.0.1 build 2222 to v6.1.1 build 8666

## Moet ik vóór deze updates back-ups maken van mijn gegevens?

Adobe zal een steun van uw systeem alvorens om het even welke veranderingen nemen. Nochtans, als er kritiek aanpassingswerk is dat in uw niet productiesysteem (ontwikkeling of het opvoeren servers) is, wordt het HIGH AANBEVOLEN u dat werk als pakket voorafgaand aan om het even welke verbetering uitvoert.

![](assets/do-not-localize/how-to-video.png) Kijk  [naar deze manier van video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html) voor meer informatie.

## Wanneer zullen de upgrades plaatsvinden?

Klanten krijgen een datumbereik te kiezen. Wijzigingen in het productiesysteem worden niet op feestdagen uitgevoerd.

De verbeteringen van de Bouwstijl kunnen van maandag tot Donderdag worden gedaan, en de Vriendagen worden slechts gebruikt voor non-production instanties.

## Hoe lang zal de bouwstijlverbetering vergen?

De tijd die wordt vereist om een bouwstijlverbetering uit te voeren is afhankelijk van verscheidene factoren:

* De grootte van de database waarvan een back-up of herstelbewerking moet worden gemaakt (grotere databases hebben meer tijd nodig om een upgrade uit te voeren)
* De grootte van de omgevingen (veel van onze klanten hebben verschillende servers die elk specifieke functies verwerken, met grotere omgevingen die meer tijd nodig hebben om te upgraden)
* De complexiteit van het systeem (sommige systemen hebben meer te controleren diensten en verbindingen, wat verificatie van de stabiliteit en prestaties van dergelijke systemen noodzakelijk maakt)

De verbetering van de bouw is een proces in twee stappen:

1. Het systeem voorbereiden op upgrade - Deze fase leidt, rekening houdend met de specifieke kenmerken van uw omgeving, in wezen tot een volledig gekwalificeerde upgrade op een niet-productieomgeving. Als de geüpgraded omgeving vanuit technisch en functioneel oogpunt groen is gemaakt, kan fase 2 plaatsvinden. Deze eerste fase kan, afhankelijk van de bovengenoemde factoren, van een paar dagen tot een paar weken duren.

1. De upgrade zelf: de productieomgeving wordt verbeterd. Deze fase wordt meestal binnen een paar uur uitgevoerd. Voor zeer complexe omgevingen moet een langere downtime worden verwacht. Als er iets verkeerd gaat, wordt een terugdraaistrategie gedefinieerd en kan deze worden uitgevoerd.

[Raadpleeg dit document](https://helpx.adobe.com/nl/campaign/kb/acc-build-upgrade.html) voor meer informatie.

## Welke middelen zijn nodig voor de bouwstijlverbetering?

Voor het upgradeproces voor build zijn de volgende bronnen vereist:

* Adobe Architect - Voor gehoste of cloud messaging/hybride architecturen moet de architect coördineren met de klantenservice.
* Projectmanager - Gehost: het hostingteam zal samenwerken met het zorgteam van de klant en de klant om de tijdlijn van de upgrade voor alle gevallen te coördineren.
* Adobe Campaign-beheerder - gehost: het hostingteam voert de upgrade uit.
* Adobe Campaign operator\marketing user - De operator voert tests uit op ontwikkelings-, test- en productieinstanties.

## Hoe kan ik voorbereidingen treffen voor de bouwstijlverbetering?

Exporteer in uw ontwikkelings- en staging-systemen werk dat essentieel is en dat behouden moet blijven. Voor meer informatie, [bekijk dit hoe te video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

Vernieuw uw kennis van de kritieke wegwerkschema&#39;s en leveringen die in uw loopboeken (of door uw raadplegend team/partner) worden ontwikkeld door de documentatie te herzien die aan uw team aan het eind van uw implementatie wordt verstrekt.

Identificeer laag volume of lage verkeerstijden die voor onderhoudsvensters ideaal zouden zijn aangezien zij het laagste bedrijfseffect zullen veroorzaken.

Controleer onze [controlelijst voor upgrades hieronder](#check-list) en uw testplannen en zorg ervoor dat bronnen die deze tests kunnen uitvoeren, binnen 24 tot 48 uur beschikbaar zijn. van de voltooiing van een upgrade.

[Raadpleeg dit document](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) voor meer informatie.

## Kunnen upgrades worden uitgevoerd &#39;s nachts of tijdens buiten kantooruren?

Upgrades kunnen buiten de kantooruren worden uitgevoerd. Het wordt altijd geadviseerd om het milieu tijdens zaken off-uren te bevorderen wanneer geen bedrijfsgebruikers met de instantie worden verbonden.

## Wat zijn de kosten verbonden aan een bouwstijlverbetering?

Er zijn geen kosten om de build-upgrade voor gehoste klanten te installeren. Als er aangepaste ontwikkelingen in het systeem zijn, zal de klant de bronnen moeten identificeren die nodig zijn om die ontwikkelingen na de upgrade te testen en om eventuele problemen met die aangepaste ontwikkelingen te verhelpen.

## Zal er toegang tot de instantie tijdens het verbeteringsproces zijn?

Nee. De server wordt afgesloten tijdens een upgrade om ervoor te zorgen dat de gegevensintegriteit behouden blijft terwijl het product wordt bijgewerkt. Zodra voltooid, wordt het opnieuw begonnen, en alle diensten hervatten.

## Zullen de e-mails tijdens het upgradeproces van het Message Center blijven worden verzonden?

Wanneer de upgrade voor Berichtencentrum (RT) plaatsvindt, worden geen e-mails van de instantie verzonden. Merk op, om het even welke processen die worden tegengehouden wanneer een systeem van de Campagne wordt gesloten automatisch hervat wanneer het systeem opnieuw wordt begonnen. Dit omvat actieve of geplande leveringen, het volgen, en metriekberekeningen voor eerder verzonden leveringen.

## Zullen de workflows blijven uitvoeren en de leveringen verzenden?

Nee. Tijdens bouwstijlverbetering, werkschema en de postdiensten worden allebei tegengehouden. Dit betekent dat werkstromen niet worden uitgevoerd en dat er geen leveringen worden verzonden. Ze worden hervat zodra het systeem opnieuw wordt opgestart. Adobe raadt echter ten zeerste aan dat alle workflows met kritieke paden na een upgrade worden gecontroleerd om ervoor te zorgen dat deze actief en gezond zijn.

## Werken mijn trackingkoppelingen nog tijdens de upgrade?

Het bijhouden van koppelingen werkt tijdens de upgrade. Er kunnen geen nieuwe e-mailberichten worden verzonden tijdens de upgrade, maar het bijhouden van koppelingen in reeds verzonden e-mails blijft werken

## Moet ik tijdens het proces van de bouwstijlverbetering beschikbaar zijn?

Ja. Klanten dienen Adobe een contactpunt te bieden dat beschikbaar is tijdens of onmiddellijk na de upgrade van hun productieapparaat.  Adobe zal via e-mail contact opnemen met deze persoon, tenzij er andere afspraken zijn gemaakt. Dit zorgt voor een soepele overgang en onmiddellijke validatie van kritieke taken. Adobe zal contact opnemen met de klant zodra de upgrade voor het samenstellen is voltooid.

## Moet ik de clientconsole bijwerken?

Ja. De cliëntconsole moet op de zelfde bouwstijl zoals de serverinstantie zijn. Zodra de verbetering is voltooid, zou uw cliëntconsole u moeten ertoe aanzetten om aan recentste bouwstijl te bevorderen om ervoor te zorgen dat het gericht op de server bouwt blijft.

## Wat is het terugdraaiplan? Worden back-ups van mijn gegevens bewaard?

Het terugdraaiplan is om het systeem met de recentste beschikbare steun te herstellen. Back-ups worden 7 dagen lang opgeslagen voor klanten van datacenters en 14 dagen voor klanten op Amazon Web Service (AWS).

## Hoe lang duurt het om terug te draaien?

Dit is afhankelijk van de back-upgrootte van de database. De gemiddelde tijd die nodig is is 4 uur om te voltooien.

## Welke types van tests worden uitgevoerd op mijn systeem na de verbetering?

Raadpleeg de [checklist voor upgrades hieronder](#check-list).

## Welk type test moet ik uitvoeren na mijn upgrade?

Ontwikkeling- en werkgebiedomgevingen worden op volgorde of samen geüpgraded, maar er is een aftekening nodig voordat de productie-instantie wordt bijgewerkt. Dit staat elke klant toe om grondig het testen te leiden alvorens uit te tekenen op om het even welke veranderingen in productie.

Zie de lijst [Controlelijst voor upgrades hieronder](#check-list). Klanten moeten soortgelijke tests uitvoeren als andere die ze nodig hebben voor de omgeving.

## Hoe vaak moet ik een upgrade uitvoeren?

Om optimale prestaties, beschikbaarheid en veiligheid van het systeem te garanderen, zal Adobe samenwerken met Klanten om ervoor te zorgen dat systemen minstens één keer per jaar worden bijgewerkt.

## Zal er een sluiting voor met een bouwstijlverbetering zijn?

Ja. De server wordt afgesloten tijdens een upgrade om ervoor te zorgen dat de gegevensintegriteit behouden blijft terwijl het product wordt bijgewerkt. Zodra voltooid, wordt het opnieuw begonnen, en alle diensten hervatten.

## Wie zou ik moeten contacteren om het bouwstijlverbeteringskaartje te openen?

Als u problemen ondervindt na een upgrade van de build, neemt u contact op met [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). De Zorg van de klant plant de bouwstijldata en opent bouwstijlgerelateerde kaartjes.

Meer informatie over de Help- en ondersteuningsopties voor Campaign Classic](../../support.md)[

## Controlelijst voor upgrades maken {#check-list}

### Checklist voor post-upgrade van de cloudberichtenserver

1. Een testlevering verzenden
   1. De leveringslogboeken en de bijbehorende workflow valideren
   1. Controleren of de logbestanden voor bijhouden zijn bijgewerkt
   1. Koppelingen spiegelen en bijhouden valideren
1. Bevestig alle technische werkschema&#39;s in begonnen staat zijn
1. Controleren of alle processen ook actief zijn

### Checklist voor post-upgrade van marketingserver

* Kan u zich aanmelden bij de server? De Client Console van de Campagne van de controle werkt zonder enige fout/waarschuwingspopups.
* Zorg ervoor om de zelfde consoleversie zoals bouwstijlversie na de verbetering te gebruiken.
* Hebt u Webtoepassingen die gegevens in het Gegevensbestand van de Campagne opnemen? Indien dit het geval is, voert u ze uit en
controleren of ze nieuwe records kunnen invoegen via de API.
* Kan je een test-e-mail verzenden? Nieuwe levering maken met een bekende sjabloon, verzenden naar
één testontvanger, verifieer verpersoonlijking, unsublink, spiegel alle werk.
* Werken al uw kritieke padworkflows? Workflows controleren, werkstroomjournaal openen, controleren
dat er geen fouten zijn.
* Zijn al uw mappen aanwezig, zichtbaar en toegankelijk? Blader door verschillende mappen en controleer deze.
alle inhoud wordt weergegeven en weergegeven.
* Komt uw leveringen door met de correcte tijdzone?

   * De aanmaakdatum en wijzigingsdatum verifiëren met de tijdstempel en de tijdzone
   * Verifieer dat de uitvoering van planner in een werkschema op de gespecificeerde tijd werkt
   * Lijst met werkstromen opzoeken die zijn gepauzeerd en waarvan de status MISLUKT is. Deze starten en controleren
   * AB Testen uitvoeren voor één scenario
   * Pushmeldingen testen en de bijbehorende trackingfunctionaliteit voor uitgebreide koppelingen
   * SMS verzenden testen
   * Als u een externe FDA hebt aangesloten, test of de gegevens beide manieren worden verzonden
   * Als u integraties gebruikt, zoals Adobe Campaign-Adobe Experience Manager, Adobe Campaign-Adobe Analytics, test dan of ze nog steeds werken zoals voorheen

**Zie ook**

* [Een build-upgrade uitvoeren](../../production/using/build-upgrade.md)
* [Opmerkingen bij de release Campaign Classic](../../rn/using/rn-overview.md)
* [Help- en ondersteuningsopties voor Campaign Classic](../../support.md)
* [[!DNL Gold Standard] programma](../../rn/using/gs-overview.md)
