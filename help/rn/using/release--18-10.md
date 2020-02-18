---
title: Release 18.10
seo-title: Release 18.10
description: Release 18.10
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a8c4face331ab6d646480322c0f53a7147251aa6

---


# Release 18.10{#release-18-10}

## Release 18.10.6 - build 8985{#release-18-10-6-build-8985}

12 juli 2019

**Verbeteringen**

* Wij staan nu de schrapping van dummy verslagen toe die in de Dynamica van Microsoft tijdens het invoeren werkschema worden gecreeerd.
* Probleem verholpen met de werkstroomactiviteit van de Bestandsverzamelaar die fouten in de lusbewerking kon aanmelden wanneer de toegang tot een bestand werd geweigerd. (NEO-12085)
* Probleem opgelost waarbij discrepanties tussen gebruikersactiviteiten werden gemeld en rapporten voor de open leveringsindicator werden bijgehouden. (NEO-11742)
* Verbeterde machtigingen om het pakket met de beveiligingszone uit te voeren wanneer u een interne account gebruikt.
* Probleem verholpen waarbij fouten in de onderliggende logboeken konden optreden. (NEO-8978)

## Release 18.10.5 - build 8984{#release-18-10-5-build-8984}

23 april 2019

**Verbeteringen**

* Probleem verholpen met SQL-impasse die ertoe leidde dat de leveringsanalyse mislukte in het geval van gelijktijdige analyse/verzending (wanneer twee leveringen tegelijkertijd werden geanalyseerd). (NEO-13026)
* Verwijderd de recordlimiet van 10.000 in WorkflowHeatmap om een probleem met ontbrekende gegevens op te lossen. (NEO-12329)
* Probleem verholpen bij het gebruik van de optie &quot;Alle aanvullende gegevens uit de hoofdset behouden&quot; in een verrijkingswerkstroom. (NEO-13291)

## Release 18.10.4 - build 8983{#release-18-10-4-build-8983}

15 april 2019

**Verbeteringen**

* Probleem verholpen met het rekenproces van het volgen van indicatoren voor transactieberichten. (NEO-12529, NEO-12581)
* Probleem verholpen met de HTTPRequest-API, die niet wachtte op alle callbacks om te voltooien. (NEO-12628)
* Er zijn indexen toegevoegd aan de tijdelijke tabellen met coupons om het verzenden van leveringen te optimaliseren. (NEO-12437)
* Probleem verholpen tijdens het analyseren van een bericht waarin ontvangers voor Japanse (.JP) domeinen als doel werden ingesteld. (NEO-12246)
* In de integratie Analytics is het nu toegestaan om AAM-segmentgegevens met %-teken op te halen. (NEO-12025)
* Probleem verholpen waarbij Tomcat vastliep tijdens het verzenden van pushberichten via HTTP2. (NEO-12701)

## Release 18.10.3 - build 8981{#release-18-10-3-build-8981}

29 januari 2019

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. Voer een [upgrade uit naar de nieuwste build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) of neem contact op met de [technische ondersteuning](https://support.neolane.net/).

**Verbeteringen**

* Probleem verholpen met de s3-activiteit van de workflow voor bestandsoverdracht. (NEO-12473)
* Probleem met de workflow voor bijhouden opgelost. (NEO-12520)
* Probleem verholpen met de IMS-aanmelding.
* Probleem verholpen met voorvertoning en goedkeuring van inhoud in Transactieberichten bij gebruik van een grote aanbieding-id.
* Probleem verholpen met de workflow voor tussenproducten (leveringstellers).
* Probleem verholpen met de update van de databasestructuur die nieuwe indexen op NmsRecipient heeft laten vallen.
* Probleem verholpen waarbij de console vastloopt die kan optreden wanneer de optie Gedefinieerd in een extern bestand wordt gebruikt voor het hoofddoel van een levering. (NEO-12349)
* Verschillende InMail-crashes zijn verholpen.
* Probleem verholpen bij het gebruik van een activiteit in de gegevenswerkstroom bijwerken om records te verwijderen die zijn opgeslagen in een FDA Teradata-database.
* Correctie van inconsistentieproblemen in geheime sleutelbeheer.
* Probleem verholpen met verrijkingsactiviteit tijdens het typen van een veld als: xml=true en calculate=true
* Probleem verholpen waarbij een fout met tekens werd gegenereerd bij het verzenden van pushberichten op een mobiele toepassing.
* Probleem verholpen waarbij werd voorkomen dat in een externe account van het type Midden-sourcing werd overgeschakeld van de FDA naar de SOAP-synchronisatiemethode.

## Release 18.10.2 - build 8978{#release-18-10-2-build-8978}

6 december 2018

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. Voer een [upgrade uit naar de nieuwste build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) of neem contact op met de [technische ondersteuning](https://support.neolane.net/).

**Verbeteringen**

* Verschillende problemen verholpen bij het uitvoeren van workflows met MySQL op FDA. (NEO-11652)
* Probleem met prestaties verholpen bij het verzenden van pushberichten. (NEO-11787)
* Probleem verholpen met uitputting van id&#39;s bij gebruik van zaadadressen in een levering. (NEO-11842)
* Oplossing voor een probleem met de blokkering van clients dat zich kon voordoen bij het gebruik van complexe workflows. (NEO-11847)
* Oplossing voor een weergaveprobleem bij het gebruik van een verdeling van waarden met een 1:N-koppeling. (NEO-11820)
* Oracle-fout in Workflow Heatmap verholpen.
* Probleem opgelost bij het toevoegen van een voorstel in een verrijkingsactiviteit.
* Probleem verholpen met een verbinding voor SQL-gegevensbeheer.
* Probleem verholpen met het genereren van tabelnamen voor tijdelijke werkstromen in het geval van negatieve id&#39;s.
* Probleem opgelost met de berekening van de werkstroomduur in Workflow HeatMap.


## Release 18.10 - build 8977{#release-18-10-build-8977}

5 nov. 2018

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. Voer een [upgrade uit naar de nieuwste build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) of neem contact op met de [technische ondersteuning](https://support.neolane.net/).

**Wat is nieuw?**

<table> 
 <thead> 
  <tr> 
   <th> Functionaliteit<br /> </th> 
   <th> Beschrijving<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Verbeteringen voor pushmeldingen<br /> </td> 
   <td> Er zijn een aantal verbeteringen geïmplementeerd voor pushberichten in Adobe Campaign:<br /> 
    <ul> 
     <li> <p>Stil meldingen bijhouden in iOS </p> </li> 
     <li> <p>Feedback op registratieaanroepen in iOS implementeren</p> </li> 
     <li> <p>De voorbereidingssnelheid voor iOS-levering verbeteren</p> </li> 
    </ul> <p>Als onderdeel van GCM-afschrijving door Google staat Android V2-connector nu alleen verbindingen met de FCM-server toe.</p><p>Raadpleeg de <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">gedetailleerde documentatie</a>voor meer informatie. De handmatige upgrade naar FCM vindt u in dit <a href="https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html">artikel</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> SQL-gegevensbeheer<br /> </td> 
   <td> <p>Er is een nieuwe werkstroomactiviteit voor gegevensbeheer toegevoegd. Met de activiteit <strong>SQL-gegevensbeheer</strong> kunt u uw eigen SQL-scripts schrijven of kopiëren en plakken om werktabellen te maken en te vullen (alleen FDA). </p> <p>Raadpleeg de <a href="../../workflow/using/sql-data-management.md">gedetailleerde documentatie</a>voor meer informatie.</p></td> 
  </tr> 
  <tr> 
   <td> Workflowbewaking<br /> </td> 
   <td> <p>Met de nieuwe Adobe Campagne Workflow HeatMap beschikken de platformbeheerders over een snelle grafische weergave van alle gelijktijdige workflows, waardoor ze de belasting op de instantie kunnen controleren en de workflows op basis daarvan kunnen plannen.</p> <p>Raadpleeg de <a href="../../workflow/using/heatmap.md">gedetailleerde documentatie</a>voor meer informatie.</p> <p>Het Workflow HeatMap-pakket is ook beschikbaar op aanvraag voor builds vóór 8977 (vanaf build 8700). Raadpleeg <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">deze pagina</a>voor meer informatie over aanvragen en installeren.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* Oplossing voor een beveiligingsprobleem dat tot kwetsbaarheden voor SSRF-aanvallen (Server Side Request Modiery) en DoS-aanvallen (Denial of Service) zou kunnen leiden. (NEO-11453)
* Inhoud (doorsturen, spiegelen, enquêtes, enz.) Wordt nu aangeboden door Campagne met de X-Robots-Tag: nocache header. Zo voorkomt u dat deze inhoud wordt geïndexeerd door internetzoekprogramma&#39;s. (NEO-11101)
* Probleem met XTK-injectie verholpen in de API voor abonnementen (nms:subscription:Unsubscribe en nms:subscription:Subscribe).
* Probleem met XTK-injectie verholpen in de webtoepassing zonder abonnement.
* Verwijderde wachtwoorden die onveilig in sommige logboeken van SMS werden getoond.

**Verbeteringen**

* Klassieke API&#39;s voor campagnes zijn nu beschikbaar op een [specifieke pagina](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html). Als u het bestand jsapi.chm gebruikte, moet u nu naar de nieuwe onlineversie verwijzen.
* PostgreSQL 10, Debian 9 en Teradata 16.20 worden nu ondersteund. Raadpleeg de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).
* Wanneer u een SFTP-verbinding maakt, kunt u nu proxyverificatie gebruiken. Raadpleeg de [gedetailleerde documentatie](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration) (NEO-9868) voor meer informatie.
* De optie **van de de berekeningsformule** van de Datum is nu beschikbaar in de leveringseigenschappen wanneer het creëren van één enkele levering gebruikend het direct-mailleveringsmalplaatje. (NEO-9792)
* Het beheer van domeinnamen is verbeterd voor het bijhouden van cookies en webtoepassingen. Zie de sectie &#39;Technische ontwikkelingen&#39; hieronder voor meer informatie.
* De import van gedeelde Adobe Marketing Cloud-middelen op een bezorgings- of bestemmingspagina is verbeterd op het gebied van beveiliging en prestaties.
* Er is een nieuw selectievakje beschikbaar in de externe account van het mobiele kanaal om uitgebreide SMPP-sporen in te schakelen in het logbestand. Hierdoor is deze uitvoer rechtstreeks toegankelijk via de interface van Adobe Campagne.
* In de uitzendingen, is er nu een onderscheid tussen het maximumaantal verbindingen en het maximumaantal berichten per uur. Wanneer de grenzen worden bereikt, is het dan mogelijk te weten waarom de productie beperkt is. Eerder was hetzelfde bericht (&quot;met quotum bereikt&quot;) van toepassing op beide gevallen.
* U kunt nu een SQL-script opgeven dat moet worden uitgevoerd wanneer u een verbinding verwerft vanuit de pool. Dit script kan worden gebruikt om het standaardschema in te stellen. Dit script wordt toegepast na query-streepvorming. (NEO-11256)
* In de campagne-SDK wordt de gebruikersnaam niet meer opgeslagen om te voldoen aan onze PII-regels. Gegevens worden nu opgeslagen als een hash.
* Bij het importeren van een XML-pakketexportbestand wordt tijdens de campagne nu de aanwezigheid van BOM in het bestand ondersteund, zelfs als de codering expliciet in het bestand wordt gedeclareerd.

**Technische ontwikkelingen**

Cliënt en serververbetering

>[!CAUTION]
>
>Als u een server hebt die aan 18.10 is bijgewerkt, zult u een cliënt 18.10 moeten gebruiken om tot uw server toegang te hebben. De 18.10-client kan verbinding maken met een oudere serverversie.

Domeinnaambeheer

Het beheer van domeinnamen is verbeterd voor het bijhouden van cookies en webtoepassingen.

Nu worden alle domeinnamen van het tweede niveau met twee letters standaard ondersteund (bijvoorbeeld .aa.com). Voor complexere domeinnamen (bijvoorbeeld tweefasige domeinen met drie letters zoals .com.au), moet u deze toevoegen in de optie **cookieDomains** van de serverConf (onder de omrichtingstag). Hier volgt een voorbeeld:

```
<redirection cookiedomain="http://toureiffel.paris">
```

Indexverbeteringen

De indexen op NmsRecipient zijn herzien. Dit zou prestaties op vragen moeten verbeteren die deze lijst gebruiken. Als u een uitbreiding van NmsRecipient had gedaan, kunt u willen verifiëren dat u geen indexen hebt die de nieuwe indexen dupliceren (om ruimtegebruik op de gegevensbestandserver te minimaliseren). (NEO-8228)

Op PostgreSql wanneer het gebruiken van een sortering UTF-8, is het nu mogelijk om indexen tot stand te brengen die &quot;ALS &quot;koord%&quot;(of &quot;begint met&quot;) verrichtingen zullen optimaliseren. Als u andere bewerkingen uitvoert op dezelfde kolom (bijvoorbeeld rangschikken bij of samenvoegen), is een andere standaardindex vereist. Aan de schemazijde, zal dit worden gedaan door indexOption=&quot;searchFromStart&quot;op de indexdefinitie toe te voegen (het zal tot een varchar_pattern_ops index in plaats van een standaardboomindex leiden). Bijvoorbeeld (op NmsRecipient):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

Er zijn nieuwe indexen toegevoegd aan NmsRtEvent en NmsEventHisto (in de kolom &quot;Gepland&quot;). Hierdoor wordt de weergavetijd op de corresponderende vorm verkort (NEO-11738).

Deze indexveranderingen kunnen tot een toename van de tijd leiden die wordt vereist om post-verbetering uit te voeren.

**Patches**

* Correctie van een fout die ervoor zorgde dat bestanden niet konden worden gedownload van de **webdownloadworkflowactiviteit** . (NEO-11105)
* Correctie van een fout die het **verzenden van indicatoren en de workflow voor campagnerekenmerken** af en toe in de toestand Niet geslaagd liet (NEO-10820).
* Probleem verholpen waarbij de lijst met ontvangers die is gemaakt nadat de List-updateactiviteit in een workflow was uitgevoerd, werd verwijderd. (NEO-11696)
* Probleem verholpen waarbij de campagnes een maand eerder in de Campagne-kalender onjuist werden weergegeven (op een Japans exemplaar). (NEO-11445)
* Probleem verholpen waardoor de configuratie Analytics niet kon worden weergegeven op het tabblad Web Analytics van de leveringseigenschappen. (NEO-11619)
* Correctie van een fout die werd weergegeven bij het bewerken en opslaan van de namen:invoerformulier voor levering. (NEO-10973)
* Probleem verholpen met een externe accountconfiguratie die optrad bij het uitvoeren van een workflow met bestandsoverdracht. (NEO-11012)
* Probleem verholpen waarbij lege regels werden geretourneerd wanneer de functie zcat werd gebruikt om bestanden te laden in de activiteit Gegevens laden. (NEO-11273)
* Probleem verholpen waarbij tijdens de analyse van de levering gedupliceerde brede logs werden gegenereerd. (NEO-11360)
* Probleem verholpen waarbij de levering mislukte omdat een vreemde-koppelingssleutel ontbrak nadat de verrijkingsactiviteit in een workflow was uitgevoerd. (NEO-11537)
* Probleem verholpen waarbij het verwijderen of repareren van Adobe Campaign niet kon worden verholpen wanneer het installatiepad bepaalde Chinese GB18030-tekens bevatte.
* Probleem verholpen waarbij sommige trackinglogboeken werden gekoppeld aan de verkeerde levering. (NEO-11412)
* Probleem verholpen waarbij sommige delen van de leveringslogs langer dan verwacht in behandeling zouden kunnen blijven. (NEO-11336)
* Oplossing voor een fout die optrad bij het bewerken van een query om een coupon aan een levering toe te voegen. (NEO-11037)
* Probleem verholpen in rapporten die ervoor zorgden dat de grafieken altijd de som van de waarden berekenden, ongeacht de geaggregeerde operator die werd geselecteerd. (NEO-10913)
* Aangezien de &quot;request.scheme&quot;functie wordt afgekeurd, is het verwijderd uit de documentatie JSAPI. (NEO-10828)
* Probleem verholpen waardoor sommige gebruikers met specifieke configuraties voor tijdzones zich niet konden aanmelden bij Adobe Campaign. (NEO-10712)
* Probleem verholpen die optrad bij het instellen van een externe account voor een mobiel kanaal met behulp van de uitgebreide algemene SMPP-connector: als u het gebruiken van verschillende parameters voor de ontvanger specificeerde, zou de zender die parameters verkeerd gebruiken in plaats van zijn eigen parameters.
* Probleem opgelost waarbij geplande leveringen mislukten bij het instellen van een frequentie voor de drukregel, omdat de leveringen na de eerste arbitrage voortdurend opnieuw werden berekend. (NEO-10016)
* Probleem verholpen waarbij de IIS-webserver vastliep tijdens het recyclingproces van de toepassingspool (in de bibliotheek nlsrvmod.dll). (NEO-10862)
* Probleem verholpen waarbij niet kon worden gezocht naar een ontvanger in het scherm **Profielen en Doel** . (NEO-8228)
* Probleem verholpen waarbij een time-outfout kon optreden bij het openen van de map Gebeurtenisgeschiedenis in het geval van een groot aantal records. (NEO-11738)
* Probleem opgelost waarbij ontvangers van lijnbezorging onjuist werden geretourneerd als &quot;Onbereikbaar&quot;. (NEO-10833)
* Probleem verholpen bij het uitvoeren van een workflowquery met een extra kolom op Oracle. (NEO-11615)
* Er is een verbetering aangebracht om ervoor te zorgen dat gesloten verbindingen niet te lang in de verbindingspool worden gehouden. (NEO-11392)
* Probleem verholpen bij het gebruik van een doelworkflowactiviteit (query, data loading (RDBMS) enz.) via FDA verbonden met een externe Oracle-tabel met UTF8-tekens (in de tabelnaam, veldnaam enz.) en die ook een primaire-sleutelbeperking met een door het systeem gegenereerde standaardbeperkingsnaam bevatten. (NEO-10714)
* Probleem opgelost waarbij de HTML-inhoud van een levering niet kon worden verwijderd. (NEO-11327)
* Probleem verholpen met de voorvertoning van XML- en CSV-bestanden in een directe e-mail nadat een campagne was gestart. (NEO-11290)
* Probleem verholpen bij het sorteren van gegevens in een verrijkingswerkstroomactiviteit. (NEO-11394)
* Probleem verholpen bij het sorteren van gegevens in een aangepast rapport. (NEO-10896)
* Probleem verholpen dat tot fouten leidde bij het gebruik van de instelling useVault met Teradata. (NEO-11399)
* Probleem verholpen waarbij de clientconsole van Adobe Campagne vastliep wanneer meerdere queryregels werden verwijderd. (NEO-10744)
* Probleem opgelost waarbij drukregels in sommige gevallen niet konden worden toegepast bij het verzenden van direct mail. (NEO-9004)
* Probleem verholpen die optrad bij het gebruik van de activiteit Gegevens bij het importeren van een kolom met het gegevenstype &quot;time&quot;: het tijdscheidingsteken wordt opnieuw ingesteld, zelfs nadat het is verwijderd. (NEO-10743)
* Probleem verholpen waardoor de map Deliveries niet kon worden weergegeven in de lijst met uitvoeringsmappen in de leveringseigenschappen tijdens het bewerken van een terugkerende levering. (NEO-11094)
* Probleem verholpen waardoor het venster Weergavepopulatie niet meer dan 200 records kon weergeven als het resulterende doel van een query-activiteit in een workflow. (NEO-11195)
* Probleem verholpen in Oracle waarbij een DELETE-query niet kon worden uitgevoerd met meer dan 1000 geselecteerde elementen. (NEO-11171)
* Probleem verholpen waarbij URL&#39;s werden gecodeerd als bijgehouden URL&#39;s in de aanvullende parameters van de levering van een Android-pushmelding. (NEO-11468)
* Oplossing voor een scriptfout die optrad in het rapport Gebruikersactiviteiten bij het instellen van de parameters op &quot;Intervallen van één dag&quot; en &quot;Openen&quot;. (NEO-11655)
* Probleem verholpen die optrad wanneer verbinding werd gemaakt met de server voor midsourcing of met Message Center via een geverifieerde webproxy. (NEO-11309)
* Oplossing voor een Oracle-fout die optrad wanneer een nieuwe leveringscompositie werd opgeslagen na het selecteren van een element van een specifiek schema **op basis van een SQL-weergave**. (NEO-11682)
* Probleem verholpen waarbij bestanden met foutieve positieven werden gegenereerd die een ZIP-bestand met een CSV-bestand verwerkten via een activiteit voor het laden van bestanden met de optie Decompressie.
* xtkjoblog wordt nu gezuiverd door de opschoonfunctie.

