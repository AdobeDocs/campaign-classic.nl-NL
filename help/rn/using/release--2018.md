---
product: campaign
title: Release van Campaign Classic 2018
description: Meer informatie over de release van Campaign Classic 2018
source-git-commit: eb0e572f0bb6196a58a7dab4999df784d5c4851f
workflow-type: tm+mt
source-wordcount: '5414'
ht-degree: 7%

---

# releases van 2018{#release-2018}

![](../../assets/v7-only.svg)

## Release 18.10

### Release 18.10.6 - build 8985{#release-18-10-6-build-8985}

12 juli 2019

**Verbeteringen**

* We staan nu toe dat dummy-records die in Microsoft Dynamics zijn gemaakt, worden verwijderd tijdens de workflow voor importeren.
* Probleem verholpen met de werkstroomactiviteit van de Bestandsverzamelaar die fouten in de lusbewerking kon aanmelden wanneer de toegang tot een bestand werd geweigerd. (NEO-12085)
* Probleem opgelost waarbij discrepanties tussen gebruikersactiviteiten werden gemeld en rapporten voor de open leveringsindicator werden bijgehouden. (NEO-11742)
* Verbeterde machtigingen om het pakket met de beveiligingszone uit te voeren wanneer u een interne account gebruikt.
* Probleem verholpen waarbij fouten in de onderliggende logboeken konden optreden. (NEO-8978)

### Release 18.10.5 - build 8984{#release-18-10-5-build-8984}

23 april 2019

**Verbeteringen**

* Probleem verholpen met SQL-impasse die ertoe leidde dat de leveringsanalyse mislukte in het geval van gelijktijdige analyse/verzending (wanneer twee leveringen tegelijkertijd werden geanalyseerd). (NEO-13026)
* Verwijderd de recordlimiet van 10.000 in WorkflowHeatmap om een probleem met ontbrekende gegevens op te lossen. (NEO-12329)
* Probleem verholpen bij het gebruik van de optie &quot;Alle aanvullende gegevens uit de hoofdset behouden&quot; in een verrijkingswerkstroom. (NEO-13291)

### Release 18.10.4 - build 8983{#release-18-10-4-build-8983}

15 april 2019

**Verbeteringen**

* Probleem verholpen met het rekenproces van het volgen van indicatoren voor transactieberichten. (NEO-12529, NEO-12581)
* Probleem verholpen met de HTTPRequest-API, die niet wachtte op alle callbacks om te voltooien. (NEO-12628)
* Er zijn indexen toegevoegd aan de tijdelijke tabellen met coupons om het verzenden van leveringen te optimaliseren. (NEO-12437)
* Probleem verholpen tijdens het analyseren van een bericht waarin ontvangers voor Japanse (.JP) domeinen als doel werden ingesteld. (NEO-12246)
* In de integratie Analytics is het nu toegestaan AAM segmentgegevens op te halen met het teken %. (NEO-12025)
* Probleem verholpen waarbij Tomcat vastliep tijdens het verzenden van pushberichten via HTTP2. (NEO-12701)

### Release 18.10.3 - build 8981{#release-18-10-3-build-8981}

29 januari 2019

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. Gelieve [upgrade naar de nieuwste build](../../production/using/build-upgrade.md)  of contact opnemen [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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

### Release 18.10.2 - build 8978{#release-18-10-2-build-8978}

6 december 2018

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. Gelieve [upgrade naar de nieuwste build](../../production/using/build-upgrade.md) of contact opnemen [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Verbeteringen**

* Verschillende problemen verholpen bij het uitvoeren van workflows met MySQL op FDA. (NEO-11652)
* Probleem met prestaties verholpen bij het verzenden van pushberichten. (NEO-11787)
* Probleem verholpen met uitputting van id&#39;s bij gebruik van zaadadressen in een levering. (NEO-11842)
* Oplossing voor een probleem met de blokkering van clients dat zich kon voordoen bij het gebruik van complexe workflows. (NEO-11847)
* Oplossing voor een weergaveprobleem bij het gebruik van een verdeling van waarden met een 1:N-koppeling. (NEO-11820)
* Probleem verholpen met een Oracle-fout in WorkflowHeatmap.
* Probleem opgelost bij het toevoegen van een voorstel in een verrijkingsactiviteit.
* Probleem verholpen met een verbinding voor SQL-gegevensbeheer.
* Probleem verholpen met het genereren van tabelnamen voor tijdelijke werkstromen in het geval van negatieve id&#39;s.
* Probleem opgelost met de berekening van de werkstroomduur in Workflow HeatMap.


### Release 18.10.1 - build 8977{#release-18-10-build-8977}

5 nov. 2018

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. Gelieve [upgrade naar de nieuwste build](../../production/using/build-upgrade.md) of contact opnemen [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Nieuwe functies**

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
   <td> Een aantal verbeteringen is geïmplementeerd voor pushberichten in Adobe Campaign:<br /> 
    <ul> 
     <li> <p>Zeldzame meldingen bijhouden in iOS </p> </li> 
     <li> <p>Feedback op registratieaanroepen in iOS implementeren</p> </li> 
     <li> <p>De voorbereidingssnelheid voor iOS-levering verbeteren</p> </li> 
    </ul> <p>Als onderdeel van GCM-afschrijving door Google staat Android V2-connector nu alleen verbindingen met de FCM-server toe.</p><p>Raadpleeg de <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">gedetailleerde documentatie</a> voor meer informatie. De handmatige upgrade naar FCM wordt in dit <a href="https://helpx.adobe.com/nl/campaign/kb/migrate-to-fcm.html">artikel</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> SQL-gegevensbeheer<br /> </td> 
   <td> <p>Er is een nieuwe werkstroomactiviteit voor gegevensbeheer toegevoegd. De <strong>SQL-gegevensbeheer</strong> Met activiteit kunt u uw eigen SQL-scripts schrijven of kopiëren en plakken om werktabellen te maken en te vullen (alleen FDA). </p> <p>Raadpleeg de <a href="../../workflow/using/sql-data-management.md">gedetailleerde documentatie</a> voor meer informatie.</p></td> 
  </tr> 
  <tr> 
   <td> Workflowbewaking<br /> </td> 
   <td> <p>Met de nieuwe Adobe Campaign Workflow HeatMap beschikken de platformbeheerders over een snelle grafische weergave van alle gelijktijdige workflows, waardoor ze de belasting op de instantie kunnen controleren en de workflows dienovereenkomstig kunnen plannen.</p> <p>Raadpleeg de <a href="../../workflow/using/heatmap.md">gedetailleerde documentatie</a> voor meer informatie.</p> <p>Het Workflow HeatMap-pakket is ook beschikbaar op aanvraag voor builds vóór 8977 (vanaf build 8700). Raadpleeg voor meer informatie over het aanvragen en installeren van de toepassing <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">deze pagina</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* Oplossing voor een beveiligingsprobleem dat tot kwetsbaarheden voor SSRF-aanvallen (Server Side Request Modiery) en DoS-aanvallen (Denial of Service) zou kunnen leiden. (NEO-11453)
* Inhoud (doorsturen, spiegelen, enquêtes, enz.) Wordt nu aangeboden door Campagne met de X-Robots-Tag: nocache header. Zo voorkomt u dat deze inhoud wordt geïndexeerd door internetzoekprogramma&#39;s. (NEO-11101)
* Probleem met XTK-injectie verholpen in abonnement-API (nms):subscription:Abonnement en nms opzeggen:subscription:Abonneren).
* Probleem met XTK-injectie verholpen in de webtoepassing zonder abonnement.
* Verwijderde wachtwoorden die onveilig in sommige logboeken van SMS werden getoond.

**Verbeteringen**

* Campaign Classic API’s zijn nu beschikbaar op een [speciale pagina](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=nl). Als u het bestand jsapi.chm gebruikte, moet u nu naar de nieuwe onlineversie verwijzen.
* PostgreSQL 10, Debian 9 en Teradata 16.20 worden nu ondersteund. Raadpleeg de [compatibiliteitsmatrix](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html).
* Wanneer u een SFTP-verbinding maakt, kunt u nu proxyverificatie gebruiken. Raadpleeg voor meer informatie de [gedetailleerde documentatie](../../installation/using/file-res-management.md) (NEO-9868)
* De **Datumberekeningsformule** Deze optie is nu beschikbaar in de leveringseigenschappen wanneer u één levering maakt met behulp van de sjabloon voor directe verzending. (NEO-9792)
* Het beheer van domeinnamen is verbeterd voor het bijhouden van cookies en webtoepassingen. Zie de sectie &#39;Technische ontwikkelingen&#39; hieronder voor meer informatie.
* De import van gedeelde Adobe Marketing Cloud-middelen op een bezorgings- of landingspagina is verbeterd op het gebied van beveiliging en prestaties.
* Er is een nieuw selectievakje beschikbaar in de externe account van het mobiele kanaal om uitgebreide SMPP-sporen in te schakelen in het logbestand, waardoor deze uitvoer rechtstreeks toegankelijk wordt via de Adobe Campaign-interface.
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

Nu worden alle domeinnamen van het tweede niveau met twee letters standaard ondersteund (bijvoorbeeld .aa.com). Voor complexere domeinnamen (bijvoorbeeld tweefalige domeinen met drie letters, zoals .com.au), moet u deze toevoegen in het dialoogvenster **cookieDomains** optie van serverConf (onder de redirection markering). Hier volgt een voorbeeld:

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

* Er is een fout opgetreden waardoor bestanden niet in het dialoogvenster **Webdownload** workflowactiviteit vanaf het downloaden. (NEO-11105)
* Probleem verholpen waarbij het **Verzending van indicatoren en campagnerekenmerken** werkstroom in de status Niet geslaagd (NEO-10820).
* Probleem verholpen waarbij de lijst met ontvangers die is gemaakt nadat de List-updateactiviteit in een workflow was uitgevoerd, werd verwijderd. (NEO-11696)
* Probleem verholpen waarbij de campagnes een maand eerder in de Campagne-kalender onjuist werden weergegeven (op een Japans exemplaar). (NEO-11445)
* Probleem verholpen waardoor de configuratie Analytics niet kon worden weergegeven op het tabblad Web Analytics van de leveringseigenschappen. (NEO-11619)
* Correctie van een fout die werd weergegeven bij het bewerken en opslaan van de namen:invoerformulier voor levering. (NEO-10973)
* Probleem verholpen met een externe accountconfiguratie die optrad bij het uitvoeren van een workflow met bestandsoverdracht. (NEO-11012)
* Probleem verholpen waarbij lege regels werden geretourneerd wanneer de functie zcat werd gebruikt om bestanden te laden in de activiteit Gegevens laden. (NEO-11273)
* Probleem verholpen waarbij tijdens de analyse van de levering gedupliceerde brede logs werden gegenereerd. (NEO-11360)
* Probleem verholpen waarbij de levering mislukte omdat een vreemde-koppelingssleutel ontbrak nadat de verrijkingsactiviteit in een workflow was uitgevoerd. (NEO-11537)
* Probleem verholpen waardoor Adobe Campaign niet correct kon worden verwijderd of gerepareerd wanneer het installatiepad bepaalde GB18030 Chinese tekens bevatte.
* Probleem verholpen waarbij sommige trackinglogboeken werden gekoppeld aan de verkeerde levering. (NEO-11412)
* Probleem verholpen waarbij sommige delen van de leveringslogs langer dan verwacht in behandeling zouden kunnen blijven. (NEO-11336)
* Oplossing voor een fout die optrad bij het bewerken van een query om een coupon aan een levering toe te voegen. (NEO-11037)
* Probleem verholpen in rapporten die ervoor zorgden dat de grafieken altijd de som van de waarden berekenden, ongeacht de geaggregeerde operator die werd geselecteerd. (NEO-10913)
* Aangezien de &quot;request.scheme&quot;functie wordt afgekeurd, is het verwijderd uit de documentatie JSAPI. (NEO-10828)
* Probleem verholpen waardoor sommige gebruikers met specifieke configuraties voor tijdzones zich niet konden aanmelden bij Adobe Campaign. (NEO-10712)
* Probleem verholpen die optrad bij het instellen van een externe account voor een mobiel kanaal met behulp van de uitgebreide algemene SMPP-connector: als u het gebruiken van verschillende parameters voor de ontvanger specificeerde, zou de zender die parameters verkeerd gebruiken in plaats van zijn eigen parameters.
* Probleem opgelost waarbij geplande leveringen mislukten bij het instellen van een frequentie voor de drukregel, omdat de leveringen na de eerste arbitrage voortdurend opnieuw werden berekend. (NEO-10016)
* Probleem verholpen waarbij de IIS-webserver vastliep tijdens het recyclingproces van de toepassingspool (in de bibliotheek nlsrvmod.dll). (NEO-10862)
* Probleem verholpen waarbij een ontvanger niet kon worden gezocht in het dialoogvenster **Profielen en doel** scherm. (NEO-8228)
* Probleem verholpen waarbij een time-outfout kon optreden bij het openen van de map Gebeurtenisgeschiedenis in het geval van een groot aantal records. (NEO-11738)
* Probleem opgelost waarbij ontvangers van lijnbezorging onjuist werden geretourneerd als &quot;Onbereikbaar&quot;. (NEO-10833)
* Probleem verholpen bij het uitvoeren van een workflowquery met een extra kolom op het Oracle. (NEO-11615)
* Er is een verbetering aangebracht om ervoor te zorgen dat gesloten verbindingen niet te lang in de verbindingspool worden gehouden. (NEO-11392)
* Probleem verholpen bij het gebruik van een doelworkflowactiviteit (query, data loading (RDBMS) enz.) via FDA verbonden met een externe Oracle-tabel met UTF8-tekens (in de tabelnaam, veldnaam enz.) en die ook een primaire-sleutelbeperking met een door het systeem gegenereerde standaardbeperkingsnaam bevatten. (NEO-10714)
* Probleem opgelost waarbij de HTML-inhoud van een levering niet kon worden verwijderd. (NEO-11327)
* Probleem verholpen met de voorvertoning van XML- en CSV-bestanden in een directe e-mail nadat een campagne was gestart. (NEO-11290)
* Probleem verholpen bij het sorteren van gegevens in een verrijkingswerkstroomactiviteit. (NEO-11394)
* Probleem verholpen bij het sorteren van gegevens in een aangepast rapport. (NEO-10896)
* Probleem verholpen dat tot fouten leidde bij het gebruik van de instelling useVault met Teradata. (NEO-11399)
* Probleem opgelost waarbij de Adobe Campaign-clientconsole vastliep bij het verwijderen van meerdere queryregels. (NEO-10744)
* Probleem opgelost waarbij drukregels in sommige gevallen niet konden worden toegepast bij het verzenden van direct mail. (NEO-9004)
* Probleem verholpen die optrad bij het gebruik van de activiteit Gegevens bij het importeren van een kolom met het gegevenstype &quot;time&quot;: het tijdscheidingsteken wordt opnieuw ingesteld, zelfs nadat het is verwijderd. (NEO-10743)
* Probleem verholpen waardoor de map Deliveries niet kon worden weergegeven in de lijst met uitvoeringsmappen in de leveringseigenschappen tijdens het bewerken van een terugkerende levering. (NEO-11094)
* Probleem verholpen waardoor het venster Weergavepopulatie niet meer dan 200 records kon weergeven als het resulterende doel van een query-activiteit in een workflow. (NEO-11195)
* Probleem verholpen in Oracle waardoor een DELETE-query niet kon worden uitgevoerd met meer dan 1000 geselecteerde elementen. (NEO-11171)
* Probleem verholpen waarbij URL&#39;s werden gecodeerd als bijgehouden URL&#39;s in de aanvullende parameters van de levering van een Android-pushmelding. (NEO-11468)
* Oplossing voor een scriptfout die optrad in het rapport Gebruikersactiviteiten bij het instellen van de parameters op &quot;Intervallen van één dag&quot; en &quot;Openen&quot;. (NEO-11655)
* Probleem verholpen die optrad wanneer verbinding werd gemaakt met de server voor midsourcing of met Message Center via een geverifieerde webproxy. (NEO-11309)
* Oplossing voor een fout in het Oracle die optrad wanneer een nieuwe leveringscompositie werd opgeslagen na het selecteren van een element van een specifiek schema **gebaseerd op een SQL-weergave**. (NEO-11682)
* Probleem verholpen waarbij bestanden met fout positieven werden gegenereerd die een ZIP-bestand met een CSV-bestand verwerkten via een bestandsactiviteit voor laden met de optie Decompressie.
* xtkjoblog wordt nu gezuiverd door de opschoonfunctie.

## Release 18.6

### Release 18.6.2 - build 8949{#release-18-6-3-build-8949}

22 augustus 2018

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. Gelieve [upgrade naar de nieuwste build](../../production/using/build-upgrade.md) of contact opnemen [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Nieuwe functies**

<table> 
 <thead> 
  <tr> 
   <th> Functionaliteit<br /> </th> 
   <th> Beschrijving<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Query-streepjescodes<br /> </td> 
   <td> <p>Wanneer de veelvoudige gebruikers van de Campagne met de zelfde FDA Teradata externe rekening verbinden, kunt u een vraagband (sleutel/waardeparen) nu overgaan specifiek voor elke gebruiker. Elke keer dat een campagnegebruiker een query uitvoert op de Teradata-database, kan Adobe Campaign nu metagegevens verzenden die aan de gebruiker zijn gekoppeld. Deze gegevens, die uit een lijst van sleutels en waarden bestaan kunnen dan door de beheerders van Teradata voor controledoeleinden of om toegangsrechten, bijvoorbeeld te beheren worden gebruikt.</p><p>Raadpleeg de <a href="../../installation/using/external-accounts.md">gedetailleerde documentatie</a> voor meer informatie.</p> </td>
  </tr> 
 </tbody> 
</table>

**Verbeteringen**

* Logbestanden voor e-mailarchivering zijn verbeterd, waardoor het eenvoudiger en duidelijker wordt om te controleren welke e-mails met succes zijn geleverd of niet zijn gearchiveerd via BCC-archivering. (NEO-10675)
* Probleem verholpen dat leidde tot de weergave van IP&#39;s van het taakverdelingsmechanisme in plaats van IP&#39;s van de klant in de weblogs voor het bijhouden van berichten. (NEO-11295)
* Probleem verholpen waarbij een willekeurig probleem werd opgelost waardoor de eigenschappen van een levering onjuist werden overschreven. (NEO-11015)
* Oplossing voor een syntaxisfout bij het sorteren van de resultaten van verrijkingsactiviteiten. (NEO-11394)
* Probleem verholpen bij het gebruik van berekende velden in een **[!UICONTROL Survey answers]** workflowactiviteit. (NEO-11382)
* Tomcat is bijgewerkt om misbruik van kwetsbaarheden te voorkomen. (NEO-11503)
* Oplossing voor een fout met LATIN1-codering bij gebruik van een FDA-verbinding met een PostSQL-database. (NEO-11299)
* Probleem verholpen dat optrad tijdens het gebruik van het dialoogvenster **[!UICONTROL Prepare the personalization data with a workflow]** leveringsoptie. (NEO-11047)
* Probleem verholpen waarbij het verzenden van SMS tijdens het gebruik van een uitgebreide connector werd verhinderd.
* Verbeterde import/export van pakketten (logboek en regio zijn toegevoegd aan de interface).
* Probleem verholpen waarbij nutteloze fouten in het postupgradelogboek werden weergegeven als een **[!UICONTROL Survey answers]** workflowactiviteit is niet volledig geconfigureerd.

**Technische ontwikkelingen**

Query-streepjescodes

Een specifieke sleutel (PROXYUSER of PROXYROLE) wordt gebruikt om een gebruiker of een rol van de Teradata aan een gebruiker van de Campagne te associëren. Er is een nieuwe machtiging toegevoegd om deze proxygebruiker/rol te gebruiken. U moet de GRANT CONNECT door toegangsrecht tot de gegevensbestandrekening (die in de Teradata externe rekening wordt bepaald) toevoegen.

Er is een nieuw tabblad toegevoegd aan de externe accounts van Teradata. De **[!UICONTROL Query banding]** bevat de volgende opties:

* **[!UICONTROL Active]**: Schakel dit selectievakje in om de functie te activeren.
* **[!UICONTROL Default]**: Voer een standaardquerybinding in die wordt gebruikt als een gebruiker geen querybinding heeft. Als er geen standaard bepaalde vraagband is, zullen de gebruikers die geen bijbehorende vraagband hebben geen Teradata kunnen gebruiken.
* **[!UICONTROL Users]**: voor elke gebruiker, specificeer een vraagband. U kunt zoveel sleutel-/waardeparen toevoegen als u nodig hebt. Bijvoorbeeld: &quot;priority=1;workload=high;&quot;

Raadpleeg de volgende artikelen voor meer informatie over querybinding:

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### Release 18.6.1 - build 8947{#release-18-6-build-8947}

25 juni 2018

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. Gelieve [upgrade naar de nieuwste build](../../production/using/build-upgrade.md) of contact opnemen [technische ondersteuning](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Nieuwe functies**

<table> 
 <thead> 
  <tr> 
   <th> Functionaliteit<br /> </th> 
   <th> Beschrijving<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Beveiligingsverbeteringen<br /> </td> 
   <td> Aan Campaign Classic is een aantal verbeteringen op het gebied van beveiliging toegevoegd. Hieronder vindt u verbeteringen en correcties.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ondersteuning voor Windows Server 2016<br /> </td> 
   <td> Adobe Campaign is nu compatibel met Windows Server 2016. Zie <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic-compatibiliteitsmatrix</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

decryptString

De **decryptString** functie is afgekeurd. Zie de [Verouderde en verwijderde functies](deprecated-features.md) artikel.

Voor nieuwe klanten, wordt deze functie nu slechts gebruikt om crypt identiteitskaart van de ontvanger in het landen pagina&#39;s te decoderen. Als u wachtwoorden wilt decoderen die zijn opgeslagen in een externe account, gebruikt u de nieuwe **decryptPassword** functie.

Voor bestaande klanten, wordt het gedrag van deze functie niet veranderd maar wij adviseren dat u gebruikt **decryptPassword** in plaats van **decryptString**. De **XtkSecurity_Unsafe_DecryptString** de compatibiliteitsoptie wordt toegevoegd door de postupgrade en standaard geactiveerd, zodat u de functie kunt blijven gebruiken. Als u wilt deactiveren **decryptString**, deactiveer de optie.

decryptPassword

De **decryptPassword** functie is toegevoegd. Hiermee kunt u een wachtwoord decoderen dat is opgeslagen in een externe account. Zie de [JSAPI](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) documentatie voor meer informatie.

Bestand-API&#39;s

Voor nieuwe installaties is maptoegang via bestand-API&#39;s beperkt tot de **var**, **sftp** en tijdelijke mappen van Adobe Campaign.

Voor bestaande klanten hebben bestands-API&#39;s geen toegang meer tot de **conf** map van Adobe Campaign. De **XtkSecurity_Disable_JSFileSandboxing** de compatibiliteitsoptie wordt toegevoegd door de postupgrade en standaard geactiveerd, zodat u de andere mappen kunt blijven gebruiken. Als u de toegang tot **var**, **sftp** en tijdelijke mappen van Adobe Campaign, deactiveer de optie.

**Reparatie**

* Probleem verholpen dat gevolgen kon hebben voor de prestaties van SMS-berichten. (NEO-9812)

## Release 18.4

### Release 18.4.5 - build 8937{#release-18-4-5-build-8937}

21 november 2018

**Verbeteringen**

* Verschillende problemen verholpen bij het uitvoeren van workflows met MySQL op FDA. (NEO-11652)
* Probleem verholpen waarbij een deel van de leveringspopulatie in bepaalde gevallen in behandeling bleef. (NEO-11336)
* Correctie van een periodiek probleem met de automatische reactie van SMS. (NEO-11811)
* Probleem verholpen met uitputting van id&#39;s bij gebruik van zaadadressen in een levering. (NEO-11842)
* Oplossing voor een syntaxisfout bij het sorteren in een verrijkingswerkstroomactiviteit. (NEO-11394)
* Probleem verholpen waarbij een webserver vastliep als IIS opnieuw wordt gestart. (NEO-10862)
* Probleem verholpen waarbij de traceringsworkflow mislukte na een upgrade van de build (FDA - SQL). (NEO-11635)
* Probleem verholpen waarbij gegevens uit de workflowlijst verloren konden gaan. (NEO-11696)
* Probleem met prestaties verholpen bij het verzenden van pushberichten. (NEO-11787)
* Probleem verholpen waarbij webtracering niet werkte voor &#39;com.au&#39;-domeinen (NEO-4385).
* Oplossing voor een probleem met de blokkering van clients dat zich kon voordoen bij het gebruik van complexe workflows. (NEO-11847)
* Probleem verholpen met een fout in het Oracle bij het opslaan van een nieuwe levering nadat een element van een specifiek schema was geselecteerd (NEO-11682).
* Probleem verholpen bij het opvragen van een veld met tekens met accenten (FDA/Teradata). Met de externe account kunt u nu de codering wijzigen die wordt gebruikt voor de communicatie met het stuurprogramma voor Teradata. (NEO-11818).
* Probleem met bijhouden bij het doorgeven van URL&#39;s in extra variabelen in een pushmelding verholpen dat kan leiden tot onjuiste of onjuiste gegevens die door de mobiele toepassing worden ontvangen. (NEO-11468, NEO-11960)
* Probleem verholpen dat een weergaveprobleem veroorzaakte bij het gebruik van een verdeling van waarden met een koppeling 1:N. (NEO-11820)
* Probleem verholpen waardoor de bulklading niet op Teradata 16 kon werken.
* De buffergrootte voor tijdstempel op Teradata is vergroot om problemen met de binding met 15.10-stuurprogramma te voorkomen.
* Verbeterde het beheer van lange naamindexen die postupgrade-problemen kunnen veroorzaken.
* Verbeterde beschikbare tijd voor gedeeld geheugen tijdens dood verwerken van kinderen (MTA).
* Oplossing voor een mogelijke impasse in Apache (tracking).


### Release 18.4.4 - build 8936{#release-18-4-4-build-8936}

1 augustus 2018

**Verbeteringen**

* Logbestanden voor e-mailarchivering zijn verbeterd, waardoor het eenvoudiger en duidelijker wordt om te controleren welke e-mails met succes zijn geleverd of niet zijn gearchiveerd via BCC-archivering. (NEO-10675)
* Probleem verholpen dat leidde tot de weergave van IP&#39;s van het taakverdelingsmechanisme in plaats van IP&#39;s van de klant in de weblogs voor het bijhouden van berichten. (NEO-11295)
* Oplossing voor een fout met LATIN1-codering bij gebruik van een FDA-verbinding met een PostSQL-database. (NEO-11299)
* Probleem verholpen dat optrad tijdens het gebruik van het dialoogvenster **[!UICONTROL Prepare the personalization data with a workflow]** leveringsoptie. (NEO-11047, NEO-11301)
* Probleem verholpen waarbij een willekeurig probleem werd opgelost waardoor de eigenschappen van een levering onjuist werden overschreven. (NEO-11015)
* Probleem verholpen bij het gebruik van berekende velden in een **[!UICONTROL Survey answers]** workflowactiviteit. (NEO-11382)
* Probleem verholpen bij het gebruik van gegevens die zijn opgeslagen in XML in een **[!UICONTROL Survey answers]** workflowactiviteit. (NEO-10816)
* Probleem verholpen bij het uitvoeren van de serverupgrade met build 8935.
* Probleem verholpen waarbij nutteloze fouten in het postupgradelogboek werden weergegeven als een **[!UICONTROL Survey answers]** workflowactiviteit is niet volledig geconfigureerd.
* FDA-Teradata: Probleem verholpen met automatisch verhoogde velden en indexen in SQL-tabellen.

### Release 18.4.3 - build 8935{#release-18-4-3-build-8935}

22 juni 2018

**Verbeteringen**

* Probleem met codering van bijhouden opgelost met Microsoft Edge en Internet Explorer. (NEO-11257)
* Probleem verholpen met aanpassen van afbeeldingskoppelingen in lijnleveringen. (NEO-11077)
* Probleem verholpen waardoor het genereren van de id-reeks niet correct werkte. (NEO-11115)
* Probleem verholpen waarbij privacyverzoeken (GDPR) niet werkten bij het gebruik van een aangepaste naamruimte met een combinatietoets. (NEO-11123)
* Oplossing voor een fout die kan optreden bij het gebruik van de **[!UICONTROL Distribution of values]** optie in **[!UICONTROL Query]** workflowactiviteiten. (NEO-10958)
* Probleem verholpen bij het synchroniseren van aanbiedingsruimten van de marketinginstantie naar de interactie-instantie. (NEO-11162)
* Verbeterd beheer van lange naamindexen tijdens postupgrade

### Release 18.4.2 - build 8932{#release-18-4-2-build-8932}

22 mei 2018

**Verbeteringen**

* Probleem verholpen waarbij de Windows Server-update niet correct werkte.
* Probleem opgelost in het dialoogvenster **[!UICONTROL Survey Result]** activiteit wanneer het gebruiken van gegevens die in XML worden opgeslagen. Het rapport is onjuist weergegeven. (NEO-10816)
* Oplossing voor een prestatieprobleem dat met het InMail-proces kon optreden bij het gebruik van een stuiterende mailserver. (NEO-10641)
* Oplossing voor een probleem met een databaseupgrade dat zich kon voordoen wanneer u meer dan 1000 schema&#39;s bijwerkte.

### Release 18.4.1 - build 8931{#release-18-4-build-8931}

24 apr. 2018

**Nieuwe functies**

<table> 
 <thead> 
  <tr> 
   <th> Functionaliteit<br /> </th> 
   <th> Beschrijving<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Algemene EU-verordening inzake gegevensbescherming (GDPR)<br /> </td> 
   <td> <p>GDPR is de nieuwe privacywet van de Europese Unie (EU) die de vereisten inzake gegevensbescherming harmoniseert en moderniseert en op 25 mei 2018 van kracht wordt. AVG is van toepassing op Adobe Campaign-klanten die data bewaren voor in de EU wonende betrokken personen.</p> <p>Naast de privacy mogelijkheden reeds beschikbaar in Adobe Campaign (met inbegrip van toestemmingsbeheer, montages van het gegevensbehoud, en gebruikersrollen), nemen wij deze kans in onze rol als Bewerker van Gegevens om extra mogelijkheden te omvatten, om uw bereidheid als Datacontrole voor bepaalde GDPR verzoeken te helpen vergemakkelijken:</p> 
    <ul> 
     <li> <p>Recht op toegang: staat de betrokkene toe een kopie te ontvangen van zijn persoonsgegevens die door gegevensverwerkingsverantwoordelijken zijn vastgelegd, met inbegrip van gegevens die mogelijk in Adobe Campaign zijn opgeslagen.</p> </li> 
     <li> <p>Rechts om te verwijderen: geeft de betrokkene het recht zijn persoonsgegevens te laten wissen door gegevensverwerkingsverantwoordelijken, eventueel met inbegrip van gegevens die in Adobe Campaign zijn opgeslagen.</p> </li> 
    </ul> Raadpleeg de <a href="https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html">gedetailleerde documentatie</a> voor meer informatie.<br /> </td> 
  </tr> 
  <tr> 
   <td> Actieve profielen<br /> </td> 
   <td> <p>Adobe Campaign biedt nu een lijst met actieve profielen, die maandelijks wordt bijgewerkt via een specifieke workflow.</p> <p>Raadpleeg de <a href="../../platform/using/about-profiles.md#active-profiles">gedetailleerde documentatie</a> voor meer informatie.</p> </td> 
  </tr> 
  <tr> 
   <td> Verbetering Android-pushconnector<br /> </td> 
   <td> <p>De Android-connector is verbeterd en biedt nu ondersteuning voor een hogere doorvoer. </p> <p>Raadpleeg de <a href="../../delivery/using/configuring-the-mobile-application.md">gedetailleerde documentatie</a> voor meer informatie.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* De uitbreiding van externe entiteiten is nu uitgeschakeld om potentiële aanvallen van niet-geverifieerde gebruikers te voorkomen. (NEO-10173)
* Verharde machtigingen om te voorkomen dat standaardgebruikers de parameters voor de instantieconfiguratie kunnen wijzigen, zoals toegangs-URL&#39;s voor toepassingen, LDAP-instellingen, enz. (NEO-10171)
* Probleem verholpen waarbij gevoelige informatie via stacktraceringen kon worden weergegeven. De details van de fout worden nu het programma geopend in het achterste eind aan een plaats ontoegankelijk van het externe netwerk. (NEO-10176)
* Verharde machtigingen om te voorkomen dat standaardgebruikers de geüploade documenten en/of geëxporteerde pakketten van een beheerder kunnen bekijken. (NEO-10170)

**Verbeteringen**

* **LINE-kanaal - architectuurverbetering**: Net als bij alle andere kanalen in Adobe Campaign wordt het LINE-kanaal nu ondersteund voor alle implementatietypen: gehost, hybride en op locatie.
* **Volgorde automatisch genereren**: Het mechanisme voor het genereren van id&#39;s is verbeterd en vergroot de levensduur van campagneinstanties met grote volumes objecten. Raadpleeg deze voor meer informatie [technote](https://helpx.adobe.com/nl/campaign/kb/sequence_auto_generation.html).

**Andere wijzigingen**

* Er is een nieuwe modus beschikbaar voor het importeren van pakketten via de opdrachtregel, zodat ronde afhankelijkheden mogelijk zijn (niet aanbevolen voor grote pakketten). Zie de sectie &#39;Technische ontwikkelingen&#39; voor meer informatie. (NEO-8979)
* De betere prestaties voor grote hoeveelheid gegevens die in Teradata worden geladen en verholpen een kwestie die verhinderde de juiste waarde van gegevens te tonen die in het logboek worden verwerkt. (NEO-10429)
* Het importeren van soorten publiek uit Audience Manager werkt nu met gesplitste bestanden. Eerder werd alleen het laatste bestand van het segment geïmporteerd door de technische workflow van importSharedAudience. (NEO-10156)
* In Windows is het standaardinstallatiepad van de Campagneserver gewijzigd. Wanneer u de installatie van de 64-bits versie start, is het standaardinstallatiepad nu: **C:\Program Files\Adobe\Adobe Campaign Classic v7** in plaats van **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* De standaard MX regels zijn verbeterd om meer domeinen te omvatten en productie te optimaliseren.
* Afgedwongen toegangsbeperkingen voor de SOAP-aanroep van de implementatiewizard (xtk:serverOptions#SaveOptions).
* De verouderde bibliotheek weka.jar is verwijderd en de OpenSSL-bibliotheek is bijgewerkt voor optimalisatie van de beveiliging.
* Verbeterde technische workflow voor facturering om uitvoeringen van instanties te beveiligen.
* De mogelijkheid voor beheerders om het wachtwoord van een operator in te stellen of opnieuw in te stellen, is hersteld. Klik hiertoe met de rechtermuisknop op een operator en selecteer **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** en stelt u het nieuwe wachtwoord van de operator in. We raden operatoren aan hun wachtwoord te wijzigen wanneer ze opnieuw verbinden. Raadpleeg de [gedetailleerde documentatie](../../production/using/lost-password.md) voor meer informatie.
* Ter ondersteuning van de nieuwe functie voor meervoud in Adobe Target kan nu een nieuwe parameter &quot;at_property&quot; aan URL&#39;s worden toegevoegd wanneer u opties en externe accounts voor de integratie met Target configureert. De waarde die voor deze parameter moet worden gebruikt, is te vinden in Adobe Target en wordt door Campagne gebruikt bij het uitvoeren van aanroepen naar Doel. Raadpleeg de [gedetailleerde documentatie](../../integrations/using/inserting-a-dynamic-image.md) voor meer informatie.
* U kunt nu een standaard openingspagina opgeven die moet worden geopend wanneer u klikt op een afbeelding die wordt geleverd door Adobe Target. Als u voorheen op die afbeelding klikte, werd de standaardafbeeldingsset gebruikt bij het maken van de e-mail. Raadpleeg de [gedetailleerde documentatie](../../integrations/using/inserting-a-dynamic-image.md) voor meer informatie.
* Toegevoegd **SMPP-sporen inschakelen** Schakel het selectievakje in de externe account in om de uitvoer te forceren. Raadpleeg de [gedetailleerde documentatie](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account) voor meer informatie.

**Technische ontwikkelingen**

queryDef

queryDef is gewijzigd met betrekking tot de &quot;orderBy&quot;clausule. Vóór de wijziging zou de primaire sleutel van de betwiste lijst impliciet aan de &quot;orderBy&quot;clausules worden toegevoegd. Bij sommige database-engines (ten minste postgressief) wordt het gebruik van indexen voorkomen (alle velden van de orderBy-component moeten door dezelfde index worden gedekt). Als u van dit gedrag afhankelijk was, zult u de primaire sleutel in uw &quot;orderBy&quot;clausule uitdrukkelijk moeten toevoegen.

Bijvoorbeeld, als u de volgende vraag hebt:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

Het zou impliciet worden overhandigd als (vóór de wijzigingen van 18.4):

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode, functie

De JavaScript-functie urlEncode werkt niet correct voor niet-ASCII-tekens. Deze is gecorrigeerd en werkt nu met alle Unicode-tekens (inclusief Japanse tekens). Als u op het gedrag &quot;urlEncode&quot;voor niet karakter ASCII vertrouwde, zult u uw code moeten aanpassen.

Nieuwe modus voor importeren pakket

Er is een nieuwe modus beschikbaar voor het importeren van pakketten via de opdrachtregel, zodat ronde afhankelijkheden mogelijk zijn (niet aanbevolen voor grote pakketten). De bestaande functionaliteit blijft behouden. Voor dergelijke pakketten met circulaire afhankelijkheden, een nieuwe markering **-usejs** is toegevoegd aan het importeren van opdrachtregelpakketten. Wanneer uitgevoerd, zal het JSEngine als gebruiken wanneer de pakketinvoer van de interface wordt uitgevoerd.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Patches**

* Probleem met synchronisatie verholpen bij het repliceren van bezorgings- en trackinglogboeken van Adobe Campaign Standard naar Adobe Campaign Classic. (NEO-10023)
* Probleem verholpen met de afhandeling van Error- en Log-tabellen in Teradata toen een ETL-workflow werd hervat na een fout bij een snelle laadbewerking. De tabellen Error en Log worden nu op de juiste wijze verwijderd telkens wanneer de workflow wordt hervat. (NEO-10672)
* Probleem verholpen na upgrade waarbij het Hive-pakket automatisch werd geïnstalleerd (nodig voor Hadoop) als het FDA-pakket is geïnstalleerd. (NEO-10592)
* Oplossing voor een fout die ongeldige domeinen als een **Niet gedefinieerd** fout. (NEO-10248)
* Probleem verholpen waarbij logboekbestanden in de tabel deliveryLogStats werden gedupliceerd bij het verzenden van Anroid-pushleveringen. (NEO-10234)
* Probleem verholpen waarbij bepaalde streepjescode-indelingen mogelijk niet leesbaar werden door streepjescodescanners. (NEO-10125)
* Probleem verholpen met de JavaScript-functie urlEncode wanneer niet-ASCII-tekens werden gebruikt. Zie de sectie &#39;Technische ontwikkelingen&#39; voor meer informatie. (NEO-10123)
* Probleem verholpen bij het uitvoeren van een query, waaronder sha256-functies op Teradata-databases. (NEO-10119)
* De fouten van het werkschemamegeheugen die in de activiteit SalesForce konden voorkomen wanneer het gebruiken van zeer grote lijsten SalesForce. (NEO-9900)
* Probleem verholpen met de **Complement genereren** optie bij het toewijzen van workflowactiviteiten bij gebruik van FDA. (NEO-9878)
* Het probleem dat tot **Verwerkt** en **Succes** metriek die niet op de marketinginstantie wordt bijgewerkt bij gebruik van mid-sourcing. (NEO-9454)
* Regels inzake vaste interactienon-repropositie wanneer in het platform in totaal meer dan 10.000 aanbiedingen worden gedaan (NEO-9352)
* Probleem verholpen waarbij het doel van een levering niet kon worden opgegeven bij gebruik van een extern XML-bestand. (NEO-9312)
* Probleem verholpen dat tot workflowfouten kon leiden wanneer een hypothese over een aanbieding werd uitgevoerd en de status van het voorstel werd bijgewerkt. (NEO-9304)
* Fouten verholpen die optraden tijdens de afleveringsanalyse bij het gebruik van drukregels op basis van een kenmerk van de Android-aflevering. (NEO-9202)
* Probleem verholpen bij het sorteren op kolommen in de lijst met ontvangers die tot prestatieproblemen kunnen leiden. Zie de sectie &#39;Technische ontwikkelingen&#39; hieronder voor meer informatie over de wijzigingen queryDef. (NEO-9042)
* Probleem verholpen waarbij de koppelingen in een goedkeurings-e-mail zouden kunnen verwijzen naar een onjuiste aanmeldings-URL, vooral wanneer u een aanmeldingstype Federated ID gebruikt. (NEO-9011)
* Probleem opgelost waarbij onjuiste datums werden weergegeven in de datumkiezers van rapporten voor bepaalde tijdzones. (NEO-9007)
* Probleem verholpen waarbij het doel van een uitgaande database niet kon worden weergegeven bij gebruik van een FDA SQL-database. (NEO-8924)
* Probleem verholpen waardoor de MS Dynamics CRM-connector er niet in slaagde gegevens te verzamelen gedurende de eerste 7 dagen van de maand. (NEO-8803)
* Probleem verholpen met integratie met Analytics waardoor gebruikers internationale tekens niet konden opnemen. (NEO-8719)
* Probleem opgelost waarbij workflowbewerking zonder de juiste rechten mogelijk was. (NEO-8708)
* Probleem verholpen met FDA via HTTP&#39;s bij gebruik van Message Center in een hybride architectuur, wat leidde tot het neerzetten of het verlies van verbinding (timeout). (NEO-8438)
* Workflowfouten die optraden bij incrementele queryactiviteit voor negatieve id&#39;s. Dit probleem is nu opgelost. (NEO-8229)
* Probleem verholpen dat tot de weergave van dubbele schuifbalken in bepaalde schermen kan leiden. (NEO-8208)
* Probleem verholpen die ertoe leidde dat een foutbericht werd weergegeven wanneer de wizard voor updatedatabasestructuur werd uitgevoerd. De PostUpgrade voert een nieuwe naam van indexen uit met namen die langer zijn dan 30. Houd er rekening mee dat voor grote tabellen de indexvervanging tijd in beslag neemt. (NEO-7983)
* Probleem verholpen waarbij trackinglogboeken niet correct werden gesynchroniseerd van de uitvoeringsinstantie van het Centrum van het Bericht om instantie te besturen. (NEO-7286)
* Oplossing voor een prestatieprobleem met de activiteit van de aanbiedingsverrijking. (NEO-7263)
* Probleem verholpen waarbij de functie DaysAgo niet kon worden gebruikt bij het opvragen van een Redshift-database via FDA. (NEO-7099)
* Oplossing voor een regressie in gegevensbeheer die het maken van indexen op verrijkingsachtige werkstroomactiviteiten verhinderde.
* Probleem opgelost dat zich kon voordoen bij het maken van externe bronnen met de titel @id
* Probleem verholpen die kan optreden wanneer gecomprimeerde bestanden worden geüpload via een FTP-server of wanneer bestanden met jokertekens in de bestandsnaam worden geüpload.
* Probleem verholpen met lange opsommingen van basistypen in externe aangepaste bronnen die in Campaign Standard zijn gemaakt.
* Probleem verholpen dat ertoe kon leiden dat SMS werd verzonden, zelfs wanneer de verbinding met de provider niet tot SMS-verlies leidde.
* Probleem verholpen waarbij een SMTP-verbinding voor onbepaalde tijd vastliep.
* Probleem verholpen met druktypologische regels tijdens de voorbereiding van berichten bij het gebruik van een LIJN-toewijzing of bij het filteren en aanwijzen van schema&#39;s die verschillen.
