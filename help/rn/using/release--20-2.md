---
solution: Campaign Classic
product: campaign
title: Release 20.2
description: Release 20.2
audience: rns
content-type: reference
topic-tags: campaign-release-notes, latest-release-notes
translation-type: tm+mt
source-git-commit: b5b9e42eca25193cf4d69f654e74a02afd8adca9
workflow-type: tm+mt
source-wordcount: '2556'
ht-degree: 90%

---


# Release 20.2{#release-20-2}

![](assets/do-not-localize/cp-icon.png) **Release van nieuw Configuratiescherm in oktober** met domeinconfiguratie met CNAME-records en nieuwe mogelijkheden voor databasecontrole. [Meer informatie](https://docs.adobe.com/content/help/nl-NL/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/green_2.png) Release 20.2.4 - build 9187 {#release-20-2-4-build-9187}

_22 december 2020_

>[!CAUTION]
>
> * Deze versie wordt geleverd met een nieuw verbindingsprotocol: Als u verbinding maakt met Campagne via de Adobe Identity Service (IMS), is een upgrade verplicht voor zowel de Campagneserver als de clientconsole om verbinding te kunnen maken met Campagne na **31 maart 2021**.
> * Deze release wordt geleverd met een [beveiligingsoplossing](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): een upgrade is verplicht om de beveiliging van uw omgeving te versterken.
> * Als u via Auth-verificatie de integratie Experience Cloug Triggers gebruikt, moet u naar Adobe I/O gaan zoals [op deze pagina](../../integrations/using/configuring-adobe-io.md) wordt beschreven. De oude Auth-verificatiemodus wordt op **30 april 2021** beëindigd.



**Verbeteringen**

* Het verbindingsprotocol is bijgewerkt en aangepast aan het nieuwe IMS-verificatiemechanisme.
* De de integratieauthentificatie van trekkers oorspronkelijk die op de authentificatie van AUTH wordt gebaseerd om tot pijpleiding toegang te hebben is veranderd en naar Adobe I/O verplaatst. [Meer informatie](../../integrations/using/configuring-adobe-io.md)
* Na [einde van steun voor iOS APNs erfenis binair protocol](https://developer.apple.com/news/?id=c88acm2b), worden alle instanties die dit protocol gebruiken bijgewerkt aan HTTP/2 protocol tijdens postupgrade.
* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-27777)
* Probleem verholpen waarbij de SMPP-connector werd gedeactiveerd na een verbindingsfout, waardoor andere SMS-leveringen niet werden verzonden en prestatieproblemen optraden. (NEO-28609)
* Er is een probleem verholpen waarbij de server vastliep door geheugenbeschadiging te voorkomen tijdens het opschonen van de expressieparser. (NEO-26856)
* Er is een probleem verholpen waarbij de server vastliep bij het weergeven van de doeldata van de rest van een **Splitsen**-activiteit in een workflow.
* Er is een probleem verholpen waarbij soms een foutbericht werd weergegeven wanneer werd geprobeerd sms-berichten weer te geven na een query op een ander schema dan **Ontvanger** (nms:recipient). (NEO-27517)
* Probleem verholpen bij het indienen van een HTTPS-verbindingsaanvraag met het poortnummer dat expliciet in de hostnaam is gedefinieerd, het aanroepen is mislukt vanwege een certificaatfout. (NEO-29146)
* Probleem opgelost in POSIX-draadbeheer dat grote core dump-bestanden heeft gegenereerd voor de marketinginstantie. (NEO-28117, NEO-29281)
* Correctie van problemen die ertoe kunnen leiden dat het webproces vastloopt bij het voorbereiden van leveringen of bij terugkerende voorvertoning van levering. (NEO-27790, NEO-27517)
* Probleem verholpen waarbij leveringen of het verzenden van bewijzen mislukten wanneer deze door een niet-beheerder werden geactiveerd. (NEO-28597)

## ![](assets/do-not-localize/red_2.png) Release 20.2.3 - build 9182 {#release-20-2-3-build-9182}

_11 september 2020_

* Oplossing voor een regressie die ertoe leidde dat een leveringsvoorbereiding werd geblokkeerd als gevolg van één foutieve functie in het leveringsonderdeel, wat tot geheugenoverbelasting leidde. (NEO-27346)
* Probleem verholpen met een post-upgrade waarbij Apache en de webserver werden uitgeschakeld voordat de webapplicatie opnieuw werd gepubliceerd. (NEO-27155)
* Oplossing voor een regressie bij HTML-sjabloonbeheer die ertoe leidde dat tracking-URL&#39;s zichtbaar werden vanwege een foute interpretatie van tabs. (NEO-25909)
* Probleem verholpen met de opschoningsworkflow voor databases die zou kunnen mislukken als gevolg van een niet-beheerde gegevensbron. (NEO-23160, NEO-23364)
* Tijdens de opschoningsworkflow worden nu verlopen lijsten in batches van 100 verwijderd in plaats van één voor één.
* Oplossing voor een regressie waardoor u niet de interne naam van een extern account kon wijzigen. (NEO-27323)
* Oplossing voor een regressie tijdens een post-upgrade die een onjuiste start van nlserver (foutenlogboeken) veroorzaakte.
* Het updatebeheer voor gedeeld geheugen is verbeterd. De extra stappen die zijn vereist in 20.2, zijn niet meer nodig.

## ![](assets/do-not-localize/red_2.png) Release 20.2.2 - build 9180 {#release-20-2-2-build-9180}

_woensdag 22 juli 2020_

* Er is een probleem verholpen waarbij tracking niet werkte als de handtekeningfunctie was uitgeschakeld. (NEO-26411)
* Probleem verholpen waarbij niet-ondertekende koppelingen van gepersonaliseerde domeinen werden geblokkeerd terwijl ze moesten worden toegestaan. (NEO-25210)
* Er is een probleem verholpen waardoor u tracking-URL’s niet kon openen of er niet op kon klikken bij gebruik van bepaalde oudere versies van Outlook. (NEO-25688)
* Probleem verholpen waarbij URL&#39;s van spiegelpagina&#39;s onjuist werden gedefinieerd in e-mailleveringen (vanwege onjuiste ASCII-tekenbesturing). (NEO-26084)
* Probleem verholpen met de codering van URL-beheer in de service voor antiphishing. (NEO-25283)
* Er is een probleem verholpen waarbij de tracking van URL’s met fragmenten in personalisatieparameters (ankerlabels met pondteken) niet werkte. (NEO-25774)
* Er is een probleem verholpen met tracking bij gebruik van specifieke aangepaste trackingformules. (NEO-25277)
* Er is een probleem verholpen waardoor tracking van ‘berichtklikken’ niet kon worden uitgevoerd (iOS- en Android-pushmeldingen). (NEO-25965)
* Oplossing voor een regressie die invloed had op berekende velden in een workflow waardoor de workflow mislukte. (NEO-25194)
* Oplossing voor een regressie waardoor het direct kunnen maken van webtracking-URL’s niet werkte. (NEO-20999)
* Oplossing voor een regressieprobleem met standaard leveringsrapporten die afgekapt leken te zijn bij het exporteren naar PDF. (NEO-25757)
* Probleem verholpen waarbij de implementatiewizard vastliep.
* Probleem verholpen waarbij de workflow voor het melden van aanbiedingen niet goed kon werken nadat een post-upgrade was uitgevoerd.
* De iOS HTTP2-connector is verbeterd (updates van derden en foutbeheer). (NEO-25904, NEO-25903)
* De lijst jarsToSkip in catalina.properties is bijgewerkt om de verwijzing naar een jar-bestand dat niet meer werd gebruikt, te verwijderen (iOS-meldingen).
* Probleem verholpen waarbij de leveringsvoorbereiding na het uitvoeren van de post-upgrade werd geblokkeerd.
* Na de overstap naar het [nieuwe ID-mechanisme voor reeksen](https://helpx.adobe.com/nl/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence) worden alle webapplicaties waarmee de tabel met ontvangers worden bijgewerkt, opnieuw gepubliceerd tijdens de post-upgrade.
* Een mogelijke XSS-kwetsbaarheid in de leveringscontent is verholpen. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **Release van nieuw configuratiescherm in juni** met controle van actieve profielen, controle van de leverbaarheid van subdomeinen en beheer van GPG-sleutels. [Meer informatie](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/red_2.png) Release 20.2.1 - build 9178 {#release-20-2-1-build-9178}

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
   <p>De Braziliaanse wet inzake gegevensbescherming (Lei Geral de Proteção de Dados, LGPD) wordt begin 2021 van kracht voor alle bedrijven die in Brazilië persoonsgegevens verzamelen of verwerken.</p>
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

* Nieuwe optie in workflowactiviteiten **[!UICONTROL Javascript Code]** en **[!UICONTROL Advanced Javascript Code]** om uitvoering na een bepaalde limiet te stoppen. Standaardwaarde is 1 uur. [Meer informatie](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

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
* Probleem verholpen waarbij de parameterwaarde voor codering tijdens het omleiden van een tracking-URL werd verwijderd (van invloed op Japanse tekens). (NEO-25637)
* Probleem verholpen waarbij een query niet werkte bij het vergelijken van getallen met drijvende komma’s. (NEO-23243)
* Probleem verholpen waarbij de weergave van de content van de kolom **Modified by** kon worden verhinderd nadat een workflow opnieuw was gestart. (NEO-23035)
* Probleem opgelost waarbij het downloaden van logboekbestanden uit een tweede container tot mislukken van de technische workflow voor tracking leidde. (NEO-23159)
* Probleem verholpen waarbij workflows konden mislukken wanneer een activiteit **Verrijking** werd uitgevoerd. (NEO-17338)
* Er is een controle toegevoegd aan het veld **Doubles to keep** in de workflowactiviteit **Deduplicatie** om te voorkomen dat er ongeldige of negatieve waarden worden ingevoerd.
* De **planningswizard** is verwijderd uit de terugkerende campagnes om te voorkomen dat uren en minuten worden vermeld. Alleen datums worden in aanmerking genomen.
* Probleem verholpen met extra opslagvelden tijdens het maken van leveringen via de optie **Computed by a script** in de workflowactiviteit **Script**. (NEO-20609)
* Probleem verholpen waarbij dubbele workflows niet werden verwijderd binnen de opschoningstaken voor de database.
* Probleem verholpen waarbij de technische workflow voor **facturering (actieve profielen)** mislukte. (NEO-19777)
* Oplossing voor een regressieprobleem tijdens het gebruik van de ACS-connectorfunctie waardoor er geen verbinding kon worden gemaakt met een Campaign Standard-instantie (onjuist beheer van de FOH/FOH2-verbinding). (NEO-23433)
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
* Oplossing voor een regressieprobleem met een databaseverbinding waarbij de webserver voortdurend opnieuw werd opgestart vanwege een probleem met de databasecodering. Dit kan leiden tot overmatig verbruik. (NEO-23264)
