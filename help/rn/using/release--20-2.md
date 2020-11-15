---
title: Release 20.2
description: Release 20.2
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: campaign-release-notes, latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '2183'
ht-degree: 80%

---


# Release 20.2{#release-20-2}

![](assets/do-not-localize/cp-icon.png) **De nieuwe versie** van oktober van het Controlebord met domeinconfiguratie die CNAMEs en nieuwe gegevensbestand controlemogelijkheden gebruikt. [Meer informatie](https://docs.adobe.com/content/help/nl-NL/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/green_2.png) Release 20.2.3 - build 9182 {#release-20-2-3-build-9182}

_11 september 2020_

* Oplossing voor een regressie waarbij de voorbereiding van de levering werd geblokkeerd als gevolg van één foutieve functie op het leveringsonderdeel, wat tot geheugenoverbelasting leidde. (NEO-27346)
* Probleem verholpen waarbij Apache en de webserver werden uitgeschakeld voordat de webtoepassing opnieuw werd gepubliceerd. (NEO-27155)
* Oplossing voor een regressie in HTML-sjabloonbeheer die ertoe leidde dat URL&#39;s werden bijgehouden omdat tabs verkeerd werden geïnterpreteerd. (NEO-25909)
* Probleem opgelost met de workflow voor het opschonen van databases die zou kunnen mislukken als gevolg van niet-beheerde gegevensbron. (NEO-23160, NEO-23364)
* De opschoningsworkflow wordt nu verwijderd door verlopen lijsten met 100 batches in plaats van één voor één.
* Probleem verholpen waarbij de interne naam van een externe account niet kon worden gewijzigd. (NEO-27323)
* Een regressie herstellen tijdens een postupgrade, wat een onjuiste start van nlserver veroorzaakt (foutlogboeken).
* Het updatebeheer voor gedeeld geheugen is verbeterd. De extra stappen die in 20.2 worden vereist zijn niet meer nodig.

## ![](assets/do-not-localize/orange_2.png) Release 20.2.2 - build 9180 {#release-20-2-2-build-9180}

_22 juli 2020_

* Er is een probleem verholpen waarbij tracking niet werkte als de handtekeningfunctie was uitgeschakeld. (NEO-26411)
* Probleem verholpen waarbij niet-ondertekende koppelingen van gepersonaliseerde domeinen werden geblokkeerd op het moment dat ze moesten worden toegestaan. (NEO-25210)
* Er is een probleem verholpen waardoor u tracking-URL’s niet kon openen of er niet op kon klikken bij gebruik van bepaalde oudere versies van Outlook. (NEO-25688)
* Probleem verholpen waarbij pagina-URL&#39;s die niet correct zijn gedefinieerd in e-mailleveringen werden gespiegeld (vanwege onjuiste ASCII-tekenbesturing). (NEO-26084)
* Probleem met coderen van URL-beheer in de service voor anti-phishing is opgelost. (NEO-25283)
* Er is een probleem verholpen waarbij de tracking van URL’s met fragmenten in personalisatieparameters (ankerlabels met pondteken) niet werkte. (NEO-25774)
* Er is een probleem verholpen met tracking bij gebruik van specifieke aangepaste trackingformules. (NEO-25277)
* Er is een probleem verholpen waardoor tracking van ‘berichtklikken’ niet kon worden uitgevoerd (iOS- en Android-pushmeldingen). (NEO-25965)
* Oplossing voor een regressie die invloed had op berekende velden in een werkstroom waardoor de werkstroom mislukte. (NEO-25194)
* Oplossing voor een regressie die ervoor zorgde dat het direct maken van URL&#39;s voor webtracering niet werkte. (NEO-20999)
* Probleem met regressie verholpen met leveringsrapporten buiten de doos die werden afgekapt tijdens het exporteren naar PDF. (NEO-25757)
* Probleem verholpen waarbij de toepassing vastliep in de wizard voor implementatie.
* Probleem verholpen waardoor de workflow voor het melden van voorstellen na een postupgrade niet correct kon werken.
* De iOS HTTP2-connector is verbeterd (updates van derden en foutbeheer). (NEO-25904, NEO-25903)
* De lijst jarsToSkip in catalina.properties is bijgewerkt om de verwijzing naar een jar-bestand te verwijderen dat niet meer werd gebruikt (iOS-meldingen).
* Probleem verholpen waarbij de voorbereiding van de levering na de upgrade werd geblokkeerd.
* Na de schakelaar aan het [nieuwe mechanisme](https://helpx.adobe.com/nl/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)van opeenvolging ID, worden alle Webtoepassingen die de ontvankelijke lijst bijwerken opnieuw gepubliceerd tijdens postupgrade.
* Oplossing voor een mogelijke XSS-kwetsbaarheid in de leveringsinhoud. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **Release van nieuw configuratiescherm in juni** met controle van actieve profielen, controle van de leverbaarheid van subdomeinen en beheer van GPG-sleutels. [Meer informatie](https://docs.adobe.com/content/help/nl-NL/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/orange_2.png) Release 20.2.1 - build 9178 {#release-20-2-1-build-9178}

_8 juni 2020_

**Nieuwe functies**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Ondersteuning voor emoticons</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Bij het ontwerpen van een bericht in Campaign kunt nu gemakkelijk emoticons invoegen in de hoofdtekst van het bericht met behulp van een speciale knop. U kunt ze ook toevoegen aan de onderwerpregel van de e-mail. U kunt de lijst met beschikbare emoticons in de interface aanpassen.</p>
    <p>Raadpleeg de <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">gedetailleerde documentatie</a> voor meer informatie over het toevoegen van emoticons. Leer <a href="../../delivery/using/customizing-emoticon-list.md">in deze sectie</a> hoe u de lijst met emoticons kunt aanpassen.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>U kunt uw instantie van Campaign nu verbinden met uw externe database van Azure Synapse. Deze verbinding wordt beheerd via een nieuw extern account.</p>
    <p>Azure Synapse is alleen beschikbaar voor hybride en on-premise omgevingen. Raadpleeg de <a href="../../installation/using/configure-fda-synapse.md">gedetailleerde documentatie</a> voor meer informatie.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Thaise en Braziliaanse privacywetten</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>De Thaise wet inzake de bescherming van persoonsgegevens (PDPA) is de nieuwe privacywet die de vereisten inzake databescherming voor Thailand harmoniseert en moderniseert. </p>
   <p>Lei Geral de Proteção de Dados (LGPD) van Brazilië zal begin 2021 in werking treden voor alle bedrijven die in Brazilië persoonsgegevens verzamelen of verwerken.</p>
   <p>Deze voorschriften zijn van toepassing op Adobe Campaign-klanten die data bewaren voor in deze landen wonende betrokken personen. Naast de privacymogelijkheden die reeds beschikbaar zijn in Campaign (met inbegrip van toestemmingsbeheer, instellingen voor dataretentie en gebruikersrollen), grijpen wij deze kans om extra mogelijkheden op te nemen om u te helpen uw gereedheid voor PDPA en LGPD te vergemakkelijken:</p>
   <ul> 
     <li><p>Recht op toegang en recht op verwijdering: wij gebruiken de mogelijkheden die voor AVG en CCPA zijn toegevoegd. <a href="https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html">Meer informatie</a></p></li> 
     <li> <p>Wanneer u een aanvraag om toegang tot persoonsgegevens maakt met de Campaign-interface of -API, selecteert u nu het type <strong>Regulation</strong>: PDPA, LGPD, AVG, CCPA. <a href="https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Meer informatie</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* Alle klanten hebben standaard een betere beveiliging voor het bijhouden van koppelingen in e-mails. Er is een extra, verbeterde beveiligingsfunctie beschikbaar die kan worden ingeschakeld door contact op te nemen met de klantenservice. Meer informatie over de functie en de stappen die niet-gehoste klanten moeten uitvoeren, vindt u in de [Controlelijst voor beveiliging en privacy](https://helpx.adobe.com/nl/campaign/kb/acc-security.html). (NEO-24232)

* Om de beveiliging te optimaliseren is het MD5-hashalgoritme waarmee bestandsnamen worden gegenereerd, versterkt met sha256 voor het uploaden van openbare bestanden. (NEO-17044)

* Om de beveiliging tegen XSS-aanvallen te versterken worden scripts aan de clientzijde onbruikbaar gemaakt bij het uitvoeren van een spiegelpagina. (NEO-17987)

* Probleem verholpen waarbij de technische workflow voor **het opschonen van privacyaanvragen** niet kon worden gebruikt om afstemmingsdata te verwijderen. (NEO-25168, NEO-21004)

* Probleem verholpen met de activiteit **Bestand overdragen** waardoor verificatie op basis van SFTP-sleutels niet kon werken op Debian 9. (NEO-23183)

**Verbeteringen op gebied van compatibiliteit**

De volgende systemen worden nu ondersteund met Campaign:
* Besturingssystemen: Debian 10
* RDBMS: Oracle 18c en Oracle 19c
* FDA: Azure Synapse Analytics

Kom meer te weten in de [Campaign-compatibiliteitsmatrix](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html).

**Verbeteringen**

* Transactionele berichten zijn verbeterd voor een betere gebruikerservaring. U kunt nu de publicatie van een transactionele berichtsjabloon ongedaan maken, waardoor deze uit de uitvoeringsinstanties wordt verwijderd. [Meer informatie](../../message-center/using/template-unpublication.md).

* Er zijn nieuwe opties beschikbaar om beperkingen in te stellen bij het verzenden van e-mails die afbeeldingen of bijlagen bevatten. Deze beveiligingen kunnen prestatieproblemen vermijden, wat in het bijzonder nuttig is bij transactionele berichten. [Meer informatie](../../installation/using/configuring-campaign-options.md#delivery)

* Met de nieuwe optie **Prepare the delivery parts in the database** kunt u de levering direct in de database voorbereiden. Hierdoor kan de analyse aanzienlijk worden versneld. Deze optie is alleen beschikbaar voor specifieke configuraties. [Meer informatie](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* De prestaties van de activiteit [CRM Connector](../../workflow/using/crm-connector.md) voor Microsoft Dynamics zijn verbeterd. (NEO-13303, NEO-12710)

* De versie van het gedeelde geheugen is verhoogd.

   >[!WARNING]
   >
   >Deze verbetering vereist een extra stap na het uitvoeren van de upgrade. Raadpleeg de onderstaande sectie over **Technische ontwikkelingen**.

* De opschoningsworkflow is verbeterd. Zwevende werktabellen van alle verwijderde workflows worden nu ook automatisch verwijderd door de opschoningsworkflow. [Meer informatie](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Certificaten voor mobiele iOS-applicaties met de iOS HTTP2-connector worden nu gevalideerd voordat pushmeldingen worden verzonden, zodat leveringen niet mislukken vanwege verlopen certificaten.

* Het beheer van HTTP-proxyverbindingen is verbeterd. [Meer informatie](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Overige wijzigingen**

* Verouderde sms-connectoren zijn nu afgeschaft. Raadpleeg de [pagina met verouderde functies](../../rn/using/deprecated-features.md).

* U kunt uw eigen Litmus-account niet meer gebruiken voor provisioning en gebruik van inboxrendering in Adobe Campaign. [Meer informatie](../../delivery/using/inbox-rendering.md).

* Voor een beter onderscheid tussen weergaven en mappen is de kleur van weergavenamen gewijzigd van donkerblauw in donkercyaan. [Meer informatie](../../platform/using/access-management.md#about-views)

* Campaign Classic kan nu worden verbonden met Microsoft Dynamics CRM-accounts die worden gehost in de regio’s Verenigd Koninkrijk, India en Canada. Dit is van toepassing op Office 365 en op on-premise implementatietypen (Dynamics 2015).

* Campaign voert nu een TLS-verificatie uit om te controleren of de hostnaam van de server overeenkomt met de hostnaam in het opgegeven certificaat.

* De tabel met leverings- en trackingstatistieken geeft nu één vermelding per levering op voor het sms-kanaal in plaats van één vermelding per leveringsontvanger.

* Er is een foutbericht toegevoegd in het logboekbestand om gebruikers te waarschuwen wanneer het gedownloade bestand groter is dan de schijfruimte.

* De volgende functies zijn nu beschikbaar voor de Snowflake-connector: MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Technische ontwikkelingen**

Deze nieuwe build werkt het gedeelde geheugen bij en vereist extra stappen om de upgrade uit te voeren. Als Campaign-beheerder dient u geheugensegmenten te verwijderen. Deze stappen zijn verplicht, omdat oude segmenten het starten van nlserver/nlsrvmod verhinderen.

In Windows moet het systeem opnieuw worden opgestart.

In Debian/CentOs moet het gedeelde geheugen worden verwijderd. Dit zijn de stappen die u moet uitvoeren:

Voor de upgrade moet u de volgende stappen uitvoeren:

1. Stop de service apache2 (http2 op CentOS) als deze actief is.
1. Stop de service nlserver (nlserver6 voor oudere builds) als deze actief is.

Na de upgrade:

1. Verwijder het gedeelde geheugen met de opdracht **ipcrm** als de versie ouder is dan de huidige versie.
1. Start de service nlserver als deze actief was.
1. Start de service apache2 als deze actief was.

Hier zijn de opdrachtregels voor Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Een voorbeeld voor Linux is beschikbaar op deze [pagina](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Patches**

* Oplossing voor een kleine regressie in de logboeken van de opschoningsworkflow.
* Probleem verholpen met de activiteit **Laden (SOAP)** tijdens het parseren van WSDL-bestanden in de workflow.
* Probleem verholpen dat een fout veroorzaakte bij het upgraden van een groot aantal workflows met behulp van een activiteit **Enquête** om een groot aantal workflows efficiënt te verwerken.
* Oplossing voor een probleem met onregelmatige verbinding tijdens de verwerking van inMail-berichten van de Enhanced MTA. (NEO-20380)
* Probleem verholpen waarbij de percentages voor hot clicks niet correct werden weergegeven wanneer afbeeldingen met een breedte van 100% werden weergegeven in de HTML. (NEO-23203)
* Probleem verholpen waardoor de voorwaardelijke content van de levering niet volledig kon worden weergegeven in het rapport met hot clicks. (NEO-18729)
* Probleem verholpen waarbij de stap voor doelgoedkeuring werd overgeslagen wanneer een workflow werd hervat om een terugkerende levering te verzenden. (NEO-18166)
* Probleem verholpen waardoor de knop **Restart message preparation** niet kon worden hervat nadat een fout in de workflow was verholpen. (NEO-13488)
* Probleem verholpen waarbij leveringen in de midsourcingmodus tijdens de opbouwfase konden mislukken, waarbij ontvangers in de Japanse e-mailindeling werden opgenomen. (NEO-23846)
* Probleem met tijdzoneconversie verholpen met de Snowflake-connector (NEO-20105)
* Probleem met externe accounts met FTP via SSL opgelost. (NEO-20498)
* Probleem verholpen waarbij afbeeldingen niet konden worden weergegeven in Line-leveringen. (NEO-23207)
* Probleem verholpen dat een fout veroorzaakte bij het publiceren van een aanbieding. (NEO-23312)
* Probleem verholpen met pushmeldingen die het mogelijk maakten testverbindingen te gebruiken in mobiele applicaties, zelfs als het certificaat verlopen was. (NEO-22991)
* Probleem verholpen dat invloed zou kunnen hebben op pushmeldingen wanneer deze op een hoge frequentie worden verzonden. (NEO-20516)
* Probleem verholpen waarbij bij de volgende trackingdata duplicaten werden opgenomen, ook al werden deze niet bijgehouden in de trackinglogboeken. (NEO-20040)
* Probleem verholpen waarbij dubbele transactionele e-mails werden verzonden nadat een fout met de communicatie van de trackingserver was verholpen. (NEO-23640)
* Probleem verholpen waarbij de waarde van de coderingsparameter werd verwijderd bij omleiding van een URL voor reeksspatiëring (invloed op Japanse tekens). (NEO-25637)
* Probleem verholpen waarbij een query niet werkte bij het vergelijken van getallen met drijvende komma’s. (NEO-23243)
* Probleem verholpen waarbij de weergave van de content van de kolom **Modified by** kon worden verhinderd nadat een workflow opnieuw was gestart. (NEO-23035)
* Probleem opgelost waarbij het downloaden van logboekbestanden uit een tweede container tot mislukken van de technische workflow voor tracking leidde. (NEO-23159)
* Probleem verholpen waarbij workflows konden mislukken wanneer een activiteit **Verrijking** werd uitgevoerd. (NEO-17338)
* Er is een controle toegevoegd aan het veld **Doubles to keep** in de workflowactiviteit **Deduplicatie** om te voorkomen dat er ongeldige of negatieve waarden worden ingevoerd.
* De **planningswizard** is verwijderd uit de terugkerende campagnes om te voorkomen dat uren en minuten worden vermeld. Alleen datums worden in aanmerking genomen.
* Probleem verholpen met extra opslagvelden tijdens het maken van leveringen via de optie **Computed by a script** in de workflowactiviteit **Script**. (NEO-20609)
* Probleem verholpen waarbij dubbele workflows niet werden verwijderd binnen de opschoningstaken voor de database.
* Probleem verholpen waarbij de technische workflow voor **facturering (actieve profielen)** mislukte. (NEO-19777)
* Oplossing voor een regressieprobleem bij gebruik van de ACS-connectorfunctie die de verbinding met een Campaign Standard-instantie heeft verhinderd (onjuist beheer van de FOH/FOH2-verbinding). (NEO-23433)
* Probleem verholpen waardoor u geen schema-extensie voor een primaire sleutel met meerdere kolommen met een Hadoop-tabel kon maken. (NEO-17390)
* Probleem verholpen in de activiteit **Laden (SOAP)** waardoor WSDL-bestanden soms niet niet vanaf een URL konden worden geladen. (NEO-16924)
* Probleem verholpen waardoor u geen **onvoorwaardelijke stop** kon uitvoeren via de console wanneer meerdere actieve workflowservers een gelijke taakverdeling hadden. (NEO-19556)
* Oplossing voor een regressie die ertoe leidde dat de opschoningsworkflow vastliep.
* Probleem verholpen dat kon optreden wanneer een sjabloon op een uitvoeringsinstantie werd gepubliceerd.
* Probleem verholpen waardoor de technische workflow van collectPrivacyRequests niet kon worden uitgevoerd. (NEO-20513, NEO-25169)
* Problemen verholpen die konden optreden wanneer werd geprobeerd verbinding te maken met Audience Manager na een upgrade naar build 9080. (NEO-20511, NEO-25167)
* Problemen verholpen die konden optreden bij het exporteren van rapporten in PDF- of XLS-indeling. (NEO-20982, NEO-23493, NEO-23348)
* Probleem verholpen waarbij een levering twee keer in de leveringslijst kon worden weergegeven nadat deze was verzonden.
* Probleem met de leveringsvoorbereiding verholpen dat kon optreden wanneer de routeringsconfiguratie was ingesteld om de levering via midsourcing te verzenden.
* Probleem verholpen waarbij een foutbericht kon worden weergegeven wanneer op een koppeling voor een webapplicatie in een Line-bericht werd geklikt.
* Probleem verholpen waarbij de geschiedenis van de activiteit **Incrementele query** werd verwijderd na het uitvoeren van de opschoningsworkflow.
* Probleem verholpen bij het maken van een extern account voor midsourcing waarbij de optie NmsMidSourcing_LastBroadLog_&lt;InternalName> ontbrak..
* Probleem met regressie bij databaseverbinding verholpen waarbij de webserver voortdurend opnieuw werd opgestart als gevolg van een probleem met de databasecodering. Dit kan leiden tot overconsumptie. (NEO-23264)
