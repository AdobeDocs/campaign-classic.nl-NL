---
product: campaign
title: Releases van Campaign Classic 2019
description: Meer informatie over Campaign Classic 2019-releases
hidefromtoc: true
exl-id: 8a36a542-e095-4208-b624-e59845592863
source-git-commit: c929557ee9f5467f9c3b8eb1ed25fae5399820ba
workflow-type: tm+mt
source-wordcount: '4825'
ht-degree: 24%

---

# Releases van 2019{#release-2019}

![](../../assets/v7-only.svg)

## Release 19.2{#release-19-2}

### ![](assets/do-not-localize/limited_2.png) Release 19.2.4 - build 9082 {#release-19-2-4-build-9082}

_15 april 2021_

* Er is een probleem met een regressie van de clientconsole opgelost die tot permanente foutberichten op het IMS-verbindingsscherm leidde. (NEO-34821)

**Alleen de console-upgrade is verplicht. Er is geen serverupgrade vereist.**

>[!NOTE]
>
> Maak verbinding met [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) om de nieuwe versie te downloaden. [Op deze pagina ](../../installation/using/client-console-availability-for-windows.md) leert u hoe u de console-update aan alle eindgebruikers kunt voorstellen.

_22 maart 2021_

* Er is een regressie opgelost die verhinderde dat bepaalde onderdelen van de console konden worden gebruikt, zoals de datumkiezer en afbeeldingsbeheer in verzendingen. (NEO-31453, NEO-31454)

**Alleen de console-upgrade is verplicht. Er is geen serverupgrade vereist.**

>[!NOTE]
>
> Maak verbinding met [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) om de nieuwe versie te downloaden. [Op deze pagina ](../../installation/using/client-console-availability-for-windows.md) leert u hoe u de console-update aan alle eindgebruikers kunt voorstellen.

_23 december 2020_

>[!CAUTION]
>
> * Deze release wordt geleverd met een nieuw verbindingsprotocol: als u verbinding maakt met Campaign via de Adobe Identity Service (IMS), is een upgrade verplicht voor zowel de Campaign-server als de clientconsole om na **30 juni 2021** verbinding te kunnen maken met Campaign. [Meer informatie](../../technotes/using/ims-updates.md)
>
> * Deze release wordt geleverd met een [oplossing voor een beveiligingsprobleem](https://helpx.adobe.com/nl/security/products/campaign/apsb21-04.html): een upgrade is verplicht om de beveiliging van uw IT-omgeving te versterken.



* Het verbindingsprotocol is bijgewerkt en aangepast aan het nieuwe IMS-verificatiemechanisme.
* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-27777)

### ![](assets/do-not-localize/red_2.png) Release 19.2.3 - build 9081 {#release-19-2-3-build-9081}

_7 februari 2020_

**Verbeteringen**

* Probleem met regressie verholpen als gevolg van de implementatie van SSL-certificering, waardoor de gebruikersverbinding op de Windows-server is mislukt. (NEO-20629)
* Probleem verholpen waarbij een onjuist versietnummer werd weergegeven in het dialoogvenster **Info** -menu.


### ![](assets/do-not-localize/red_2.png) Release 19.2 - build 9080 {#release-19-2-build-9080}

_2 december 2019_

**Nieuwe functies**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA is de nieuwe privacywet van de staat Californië die de vereisten inzake gegevensbescherming harmoniseert en moderniseert die van kracht worden op 1 januari 2020. CCPA is op de klanten van Adobe Campaign van toepassing die gegevens voor de Onderwerpen van Gegevens in Californië verblijven.</p>
    <p>Naast de privacymogelijkheden die al beschikbaar zijn (zoals beheer van toestemming, instellingen voor gegevensbewaring en gebruikersrollen), helpt Adobe Campaign u de bereidheid tot CCPA te vergemakkelijken:</p>
    <ul>
      <li>Recht op toegang en recht op verwijdering: We benutten de capaciteiten die voor GDPR zijn toegevoegd. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Meer informatie</a></li>
      <li>U kunt bijhouden of een consument heeft gekozen voor de verkoop van persoonlijke gegevens. Hiervoor moet u de tabel Profielen uitbreiden en een <strong>Uitschakelen voor CCPA</strong> veld. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Meer informatie</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Live bewaking van workflow</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>U kunt nu de uitvoeringsstatus van alle workflows op uw exemplaar controleren met behulp van vooraf gedefinieerde weergaven.</p>
   <p>Raadpleeg de <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">gedetailleerde documentatie</a> voor meer informatie.</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Interactieve inhoud met AMP</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Met Adobe Campaign kunt u de nieuwe interactieve <a href="https://amp.dev/about/email/">AMP voor e-mail</a> formaat, dat verkopers toestaat om de componenten van AMP binnen berichten te omvatten om de e-mailervaring met rijke, dynamische en interactieve inhoud te verbeteren, direct actionable in het bericht zelf.</p>
   <p>Dit vermogen wordt vrijgegeven als openbare bèta.</p>
   <p>Raadpleeg de <a href="../../delivery/using/defining-interactive-content.md">gedetailleerde documentatie</a> en de <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">videotutorial</a>voor meer informatie.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Beveiligd SMS-bericht (TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Beveiligd SMS wordt nu ondersteund via de uitgebreide algemene SMPP-connector. Hierdoor is een gecodeerde verbinding met de provider mogelijk.</p> <p><strong>Waarschuwing</strong> Voor deze functie is een up-to-date certificaat op alle servers vereist. Ongeldige, ingetrokken of verlopen certificaten genereren fouten die de algemene mogelijkheden voor het verzenden van SMS beïnvloeden.</p><p>Raadpleeg de <a href="https://helpx.adobe.com/nl/campaign/kb/sms-connector-protocol-and-settings.html">gedetailleerde documentatie</a> voor meer informatie. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* Oplossing voor een probleem met opgeslagen kwetsbaarheden voor scripts die verwijzen naar andere sites, in de Campagne-interface: validatie van invoergegevens en codering van uitvoer. (NEO-16810)
* Oplossing voor een beveiligingsprobleem met profielautorisatie dat toegang tot onbevoegde gegevens mogelijk maakt door het beleid voor aanmeldingsbeperkingen te versterken. (NEO-14445)

**Verbeteringen**

* Geheugenverbruik optimaliseren voor pushmeldingen.
* Voor optimalisatie van prestaties en opslag, de behandeling van **logins.log** bestand is verbeterd. Het bestand wordt nu in meerdere bestanden gesplitst, elke dag met maximaal 365 bestanden. [Meer informatie](../../production/using/log-files.md)
* De externe account van Microsoft Dynamics CRM kan nu worden geconfigureerd met wachtwoordreferenties (wachtwoord + gebruikersnaam) of certificaat (persoonlijke sleutel). [Meer informatie](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Sommige verbeteringen zijn toegevoegd aan de Hadoop FDA-aansluiting om de betrouwbaarheid te verbeteren
* Er is een specifieke hulplijn toegevoegd om schijfruimte te controleren voordat u openbare bronnen op de server kunt uploaden.
* Nieuw [Campagneopties](../../installation/using/configuring-campaign-options.md) zijn toegevoegd:
   * De **WdbcKillSessionPolicy** configuratieoptie staat u toe om te beïnvloeden **Onvoorwaardelijke stop** gedrag op alle werkschema&#39;s en PostSQL- gegevensbestandvragen.
   * De **NmsOperation_DeliveryPreparationWindow** kunt u opgeven hoeveel dagen u wilt overschrijden voordat leveringen met een inconsistente status van het aantal lopende leveringen worden uitgesloten.
   * De **WdbcOptions_TempDbName** staat u toe om een afzonderlijk gegevensbestand voor het werken van lijsten op de Server van Microsoft te vormen SQL. Hierdoor worden back-ups en replicatie geoptimaliseerd. [Meer informatie](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * De **XtkCleanup_NoStats** is verbeterd voor PostgreSQL om het gedrag van de stap van de opslagoptimalisering van het gegevensbestand schoonmaakwerkschema beter te controleren. [Meer informatie](../../production/using/database-cleanup-workflow.md#statistics-update)
* Er is een mechanisme voor het afsluiten van een account toegevoegd aan de **aanmelden()** API. Het verhindert verdere login pogingen na een bepaald aantal opeenvolgende ontbroken login pogingen binnen een gespecificeerd tijdsbestek.
* Een nieuwe **Maximale uitvoeringstijd voor personalisatie** optie in de leveringseigenschappen staat u toe om een onderbreking voor de verpersoonlijkingsruntime te bepalen, om de verpersoonlijkingsfase te verhinderen te lang te lopen. [Meer informatie](../../delivery/using/personalization-fields.md#timing-out-personalization)
* De **FTP-protocol** is toegevoegd om u toe te staan om een volmachtsconfiguratie voor verbindingen te gebruiken SFTP. [Meer informatie](../../installation/using/file-res-management.md)
* Nieuwe ondersteuning van proxytoegang tot een externe SFTP-server voor on-premise omgevingen.
* Er is een specifieke hulplijn toegevoegd om te voorkomen dat pakketten worden geïnstalleerd die niet compatibel zijn met de instantie Campagne. [Meer informatie](../../installation/using/installing-campaign-standard-packages.md)

_Verouderde systemen_

De volgende systemen zijn nu [verouderd](deprecated-features.md) voor Campaign Classic-implementaties:
* Apache 2.2
* Centos 6

Zorg ervoor dat u beschikt over ondersteunde versies van alle systemen die in de nieuwste matrix voor campagnecompatibiliteit worden vermeld. [Meer informatie](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html)

_Campagne Mobile SDK_

De build 1.0.26 van de iOS SDK is nu beschikbaar. In deze nieuwe build hebben we de ondersteuning van iOS 13 toegevoegd. Deze nieuwe versie ondersteunt nu meldingsprioriteit en het nieuwe beheerproces voor registratietoken voor iOS 13-pushberichten. Als u toepassingen uitvoert op een eerdere versie van de SDK, moet u de toepassingen opnieuw compileren met de nieuwe SDK. Neem contact op met [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Patches**

* Probleem verholpen waarbij het programma vastliep **Gekoppelde tabel toevoegen** veld is leeg in **Gegevens laden (RDBMS)** workflowactiviteit. (NEO-12213)
* Probleem verholpen dat ertoe kon leiden dat bepaalde berichten niet werden verwerkt door de server voor middeluitgaven. (NEO-12395)
* Probleem verholpen in de workflow voor het opschonen van databases bij gebruik van de optie voor het binden van query&#39;s met Teradata. (NEO-12399)
* Probleem opgelost dat invloed had op de leveringsanalyse met typologieregel, waaronder ne.jp domain. (NEO-12609)
* Probleem verholpen met betrekking tot SMS over TLS-updates die een restrictiever certificaatbeleid impliceerden. Deze updates kunnen leiden tot een verbindingsfout tussen marketing- en midsourcingservers in het geval van een verouderd certificaat. (NEO-17698)
* Probleem verholpen tijdens het gebruik van de **Verbinding testen** op een externe account in een omgeving voor midsourcing met Vault-verificatie. (NEO-12722)
* Probleem verholpen bij query&#39;s waarbij gebruik werd gemaakt van datumfuncties met een FDA Hadoop-verbinding. (NEO-12847)
* Probleem verholpen bij het vervangen van een afbeelding in de e-maileditor. (NEO-13098)
* Probleem verholpen waarbij na de upgrade fouten konden optreden in mappen die waren verwijderd of verplaatst naar een andere locatie. (NEO-13118)
* Probleem verholpen bij weergave van afbeelding bij gebruik van de optie **Afbeelding per schermgrootte van apparaat definiëren** optie op LINE berichten. (NEO-13228)
* Het probleem met de voorbereiding van de levering verholpen toen de **Dubbel adres tijdens levering uitsluiten** is uitgeschakeld. (NEO-13240)
* Probleem verholpen in workflows tijdens het gebruik van de **Bestandsoverdracht** activiteit om dossiers te downloaden gebruikend **Bronbestanden na overdracht verwijderen** met een naam die een spatieteken bevat. (NEO-13411)
* Probleem verholpen waarbij Tomcat-cache werd opgeschoond en dit tot geheugenproblemen kon leiden. (NEO-13456)
* Probleem verholpen bij installatie van de **Besturing van de aanbiedingsengine met uitvoeringsinstantie** Ingebouwd pakket op een bestaande besturingsinstantie die wordt uitgevoerd in Microsoft SQL 2017. (NEO-13539)
* Probleem met vastlopen van de console die kan optreden wanneer bijgehouden URL&#39;s in een e-mail worden uitgeschakeld, is opgelost via het dialoogvenster **Tekstinhoud** vanwege een niet-geïnitialiseerde variabele. (NEO-13545)
* Probleem verholpen met codering van Chinese afzendernaam. (NEO-13837)
* Oplossing voor een fout die kan optreden bij het weergeven van enquêteresolutiegegevens in de Verkenner. (NEO-14590)
* Probleem verholpen dat tot een discrepantie tussen de indeling van het leveringslogboek en de quarantainetabel kon leiden. (NEO-16547)
* Probleem verholpen met DKIM-sleutels die niet in e-mailberichten waren ingesloten. (NEO-16804)
* Probleem verholpen waarbij de onjuiste foutcode werd weergegeven toen een ongeldig sessietoken werd gebruikt in de context van API-aanroepen om gebeurtenissen te activeren. De foutcode was &#39;HTTP 200 OK&#39; in plaats van &#39;HTTP 403 Verboden&#39;. (NEO-16826)
* Probleem verholpen bij het weergeven van leveringsrapporten via webtoegang. (NEO-17015)
* Probleem verholpen met IMS-verificatie bij aanmelding bij Adobe Campaign. (NEO-17312)
* Probleem verholpen waarbij werd voorkomen dat in quarantaine geplaatste e-mails werden verwijderd tijdens het privacybeheerproces. (NEO-17314)
* Problemen met de doorvoer verholpen na upgrade naar 9031 met SQL-database. (NEO-17558)
* Probleem verholpen dat invloed had op de CRM-connector met Salesforce. (NEO-17712)
* Probleem met time-out verholpen bij het importeren van gegevens uit een externe SFTP. (NEO-19723)
* Probleem verholpen bij toegang tot voorspellende modellen. (NEO-19713)
* Probleem met willekeurige bemonstering verholpen **Splitsen** workflowactiviteit met Hadoop FDA-database. (NEO-16636)
* Oplossing voor een regressie op het Oracle waardoor sommige functies na de upgrade als ongeldig werden beschouwd. (NEO-12759)


## Release 19.1{#release-19-1}

### ![](assets/do-not-localize/limited_2.png) Release 19.1.8 - build 9039 {#release-19-1-8-build-9039}

_15 april 2021_

* Er is een probleem met een regressie van de clientconsole opgelost die tot permanente foutberichten op het IMS-verbindingsscherm leidde. (NEO-34821)
* Oplossing voor een regressie die de export van workflowgegevens naar een FDA-database kon blokkeren (Teradata, Snowflake).

**Alleen de console-upgrade is verplicht. Er is geen serverupgrade vereist.**

>[!NOTE]
>
> Maak verbinding met [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) om de nieuwe versie te downloaden. [Op deze pagina ](../../installation/using/client-console-availability-for-windows.md) leert u hoe u de console-update aan alle eindgebruikers kunt voorstellen.

_22 maart 2021_

* Er is een regressie opgelost die verhinderde dat bepaalde onderdelen van de console konden worden gebruikt, zoals de datumkiezer en afbeeldingsbeheer in verzendingen. (NEO-31453, NEO-31454)

**Alleen de console-upgrade is verplicht. Er is geen serverupgrade vereist.**

>[!NOTE]
>
> Maak verbinding met [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) om de nieuwe versie te downloaden. [Op deze pagina ](../../installation/using/client-console-availability-for-windows.md) leert u hoe u de console-update aan alle eindgebruikers kunt voorstellen.

_16 december 2020_

>[!CAUTION]
>
> * Deze release wordt geleverd met een nieuw verbindingsprotocol: als u verbinding maakt met Campaign via de Adobe Identity Service (IMS), is een upgrade verplicht voor zowel de Campaign-server als de clientconsole om na **30 juni 2021** verbinding te kunnen maken met Campaign. [Meer informatie](../../technotes/using/ims-updates.md)
> * Deze release wordt geleverd met een [oplossing voor een beveiligingsprobleem](https://helpx.adobe.com/nl/security/products/campaign/apsb21-04.html): een upgrade is verplicht om de beveiliging van uw IT-omgeving te versterken.
> * Als u via oAuth-verificatie de Experience Cloug Triggers-integratie gebruikt, moet u overstappen op Adobe I/O zoals [op deze pagina](../../integrations/using/configuring-adobe-io.md) wordt beschreven. De verouderde oAuth-authentificatiemodus met Campaign [is beëindigd](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) in **september 2021**. Gehoste omgevingen profiteren van een verlenging tot **23 februari 2022**. Als klant op locatie of hybride klant neemt u contact op met de klantenservice van Adobe om de ondersteuning uit te breiden tot februari 2022. U moet de [AppID van de OAuth-applicatie](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) aan Adobe verstrekken.



**Verbeteringen**

* Het verbindingsprotocol is bijgewerkt en aangepast aan het nieuwe IMS-verificatiemechanisme.
* De de integratieauthentificatie van trekkers oorspronkelijk gebaseerd op de authentificatie van de AUTH aan toegangspijplijn is veranderd en aan Adobe I/O verplaatst. [Meer informatie](../../integrations/using/configuring-adobe-io.md)
* Nu het verouderde binaire protocol voor iOS APN’s niet meer wordt ondersteund, zijn alle instanties die dit protocol gebruiken, bijgewerkt naar het HTTP/2-protocol tijdens de postupgrade.
* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-27777)
* Probleem verholpen waarbij de SMPP-connector werd gedeactiveerd na een verbindingsfout, waardoor andere SMS-leveringen niet werden verzonden en prestatieproblemen optraden.
* Probleem verholpen waarbij onjuiste percentages werden weergegeven bij het genereren van een beschrijvend rapport via een workflowactiviteit. (NEO-14314)
* Het probleem met de voorbereiding van de levering verholpen toen de **Dubbel adres tijdens levering uitsluiten** is uitgeschakeld. (NEO-13240)
* Probleem verholpen waarbij workflows konden mislukken wanneer een activiteit **Verrijking** werd uitgevoerd. (NEO-17338)
* Er is een probleem verholpen in workflows tijdens het ophalen van records uit een externe database en het invoegen van records in de Campaign-database. (NEO-26359)
* Er is een probleem verholpen waarbij de server vastliep door geheugenbeschadiging te voorkomen tijdens het opschonen van de expressieparser.
* Het probleem dat de **NoNull** functie van het werken in de gegevensbestanden van het Oracle na bevordering om 9032 te bouwen. (NEO-26488)
* Er is een probleem verholpen met de bewerking van een campagnesjabloonbeschrijving waardoor de knop **Opslaan** niet werd weergegeven bij het kopiëren en plakken van symbolen zoals bijvoorbeeld Japanse tekens. (NEO-27071)
* Er is een probleem verholpen waardoor de beschrijving van een campagne of campagnesjabloon niet kon worden opgeslagen wanneer er buiten het venster werd geklikt voordat op de knop **Opslaan** was geklikt. (NEO-27449)
* Er is een probleem verholpen op het niveau van proxyconfiguratie waardoor u zich na de laatste Windows 10-update niet kon aanmelden bij Adobe Campaign. (NEO-27813)
* Probleem verholpen met betrekking tot het beheer van lege regels in logbestanden, wat tot fouten in het MTA-procesgedrag leidde en tot prestatieverlies bij het verzenden van de levering.

**Technische ontwikkelingen**

Tomcat is bijgewerkt van versie 7 (7.0.103) naar versie 8 (8.5.57). De map `tomcat-7` is vervangen door een map `tomcat-8`. In Windows _zijn iis_neolane_setup.vbs_ en _apache_neolane.conf_ nu geïnstalleerd in de map `conf` (in plaats van `tomcat-7/conf` zoals eerder). In Linux is _apache_neolane.conf_ nu geïnstalleerd in de map `conf`.

In Linux gebruikt het opstarten van de netwerkservice nu een systeemeenheid in plaats van het script /etc/init.d/nlserver6. De migratie naar het nieuwe opstartschema wordt automatisch uitgevoerd wanneer u het 19.1.8-pakket installeert. /etc/init.d/nlserver6 wordt nog verstrekt maar voor het in wisselwerking staan met de nlserver dienst (begin, nieuw begin, einde, enz.), adviseren wij dat u het systeembevel direct gebruikt.


### ![](assets/do-not-localize/red_2.png) Release 19.1.7 - build 9036 {#release-19-1-7-build-9036}

_15 september 2020_

**Verbeteringen**

* Verbeterd gebruik van nlsrvmod voor Apache 2.4-thread voor het corrigeren van nlsrvmod-crashes.
* Probleem verholpen bij het gebruik van bestandsoverdrachtactiviteiten met een Azure extern account en een SSL-codering. De verbinding is uitgevoerd via HTTP in plaats van via HTTPS. (NEO-26720)
* Probleem verholpen met het mechanisme voor url-cache dat het label of de categorie niet heeft opgehaald.
* Probleem verholpen waarbij URL&#39;s van spiegelpagina&#39;s onjuist werden gedefinieerd in e-mailleveringen (vanwege onjuiste ASCII-tekenbesturing). (NEO-26084)
* De lijst jarsToSkip in catalina.properties is bijgewerkt om de verwijzing naar een jar-bestand dat niet meer werd gebruikt, te verwijderen (iOS-meldingen).
* Probleem verholpen waarbij een regressieprobleem werd verholpen dat na publicatie na de upgrade werd voorkomen.
* Oplossing voor een regressie met out-of-the-box leveringsrapporten die afgebroken bleken te zijn bij het exporteren naar PDF. (NEO-25757)
* Probleem verholpen waarbij de parameterwaarde voor codering tijdens het omleiden van een tracking-URL werd verwijderd (van invloed op Japanse tekens). (NEO-25637)
* Probleem verholpen waarbij niet-ondertekende koppelingen van gepersonaliseerde domeinen werden geblokkeerd terwijl ze moesten worden toegestaan. (NEO-25210)
* Oplossing voor een regressie die invloed had op berekende velden in een workflow waardoor de workflow mislukte. (NEO-25194)
* Probleem met compatibiliteit met Microsoft Dynamics (versie 8.2) verholpen waarbij sommige API-aanroepen niet konden worden uitgevoerd (RetrieveAllEntities). (NEO-24528)
* Oplossing voor een regressieprobleem tijdens het gebruik van de ACS-connectorfunctie waardoor er geen verbinding kon worden gemaakt met een Campaign Standard-instantie (onjuist beheer van de FOH/FOH2-verbinding). (NEO-23433)
* Oplossing voor een regressieprobleem met een databaseverbinding waarbij de webserver voortdurend opnieuw werd opgestart vanwege een probleem met de databasecodering. Dit kan leiden tot overmatig verbruik. (NEO-23264)
* Probleem verholpen met de opschoningsworkflow voor databases die zou kunnen mislukken als gevolg van een niet-beheerde gegevensbron. (NEO-23160, NEO-23364)
* Tijdens de opschoningsworkflow worden nu verlopen lijsten in batches van 100 verwijderd in plaats van één voor één.
* Na de overstap naar het nieuwe ID-mechanisme voor reeksen worden alle webapplicaties waarmee de tabel met ontvangers worden bijgewerkt, opnieuw gepubliceerd tijdens de post-upgrade.
* Probleem verholpen waarbij e-mailberichten niet konden worden verzonden als er JavaScript-code buiten de HTML-inhoudstag stond. (NEO-18628)
* Probleem verholpen waardoor de traceringsindicatoren voor transactionele berichten niet konden worden bijgewerkt door de workflow voor bijhouden. (NEO-17770)
* Verbeterde prestaties van de wizard Database bijwerken om minder SQL-instructies te maken en zo de responstijd te optimaliseren.
* Probleem met vastlopen van de console die kan optreden wanneer bijgehouden URL&#39;s in een e-mail worden uitgeschakeld, is opgelost via het dialoogvenster **Tekstinhoud** vanwege een niet-geïnitialiseerde variabele. (NEO-13545)
* Probleem verholpen waardoor u bestanden niet kon uploaden in een bestandsoverdrachtactiviteit met een externe account van de Azure Blob Storage vanwege een niet-geïnitialiseerde variabele (m_pCurlReader). (NEO-13717)
* Probleem verholpen met een post-upgrade waarbij Apache en de webserver werden uitgeschakeld voordat de webapplicatie opnieuw werd gepubliceerd. (NEO-27155)
* Probleem verholpen waarbij een regressie werd opgetreden die ertoe leidde dat een onjuiste tijdzone werd gekozen bij het instellen van tijd in een **Planner** workflowactiviteit.


### ![](assets/do-not-localize/red_2.png) Release 19.1.6 - build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Deze build is alleen bedoeld voor installaties op locatie. Voor hybride plaatsingen, zullen de ontvangen instanties blijven lopend de 9032 bouwstijl. Upgrade uw marketingexemplaar niet naar de 9035-build omdat deze niet compatibel is met 9032.

_3 oktober 2019_

**Verbeteringen**

* Er is een probleem verholpen met het gebruik van de CRM-connector voor Salesforce. (NEO-17712)
* Er is een indexprobleem verholpen dat prestatieproblemen kon veroorzaken bij het verzenden van transactieberichten.
* Oplossing voor een prestatieprobleem bij het verzenden van berichten. (NEO-17558)
* Probleem verholpen dat ertoe kon leiden dat bepaalde berichten niet werden verwerkt door de server voor middeluitgaven. (NEO-12395)
* Probleem verholpen waardoor de SQL-gegevensbeheeractiviteit niet volledig kon worden gebruikt (het genoemde recht SQL-gegevensbeheer ontbreekt).

### ![](assets/do-not-localize/red_2.png) Release 19.1.5 - build 9033{#release-19-1-5-build-9033}

_13 augustus 2019_

**Verbeteringen**

* Probleem verholpen met de SQL-instructie &#39;SELECT COUNT&#39;, die werd uitgevoerd in de standaarddatabase in plaats van in de FDA-database tijdens het ophalen van gegevens in gegevensbeheeractiviteiten.
* Om de mogelijkheden van de klanteninfrastructuur te verbeteren, is een de volmachtsverklaring van SFTP nu beschikbaar in het dossier van de serverconfiguratie.
* Probleem verholpen waarbij het programma vastliep **Gekoppelde tabel toevoegen** veld is leeg in **Gegevens laden (RDBMS)** workflowactiviteit. (NEO-12213)
* Probleem verholpen met de installatie van het midEmitter-pakket via de opdrachtregel.
* Er is een nieuwe verificatieoptie toegevoegd ter ondersteuning van OAuth-referenties in de AC-connector met Microsoft Dynamics. (NEO-11982)
* Probleem verholpen met UUID-beheer (Unique Universal Identifier) waardoor de workflowactiviteiten voor het laden van query&#39;s en gegevens mislukten met Hive FDA.
* Oplossing voor een regressie op het Oracle waardoor sommige functies na de upgrade als ongeldig werden beschouwd. (NEO-12759)
* Oplossing voor een regressie die leidde tot een onjuiste tijdzone die werd gekozen wanneer het plaatsen van de tijd in een de werkschemaactiviteit van de Planner.

### ![](assets/do-not-localize/green_2.png) Release 19.1.4 - Build 9032{#release-19-1-4-build-9032}


>[!NOTE]
>
>19.1.4. [!DNL Gold Standard] worden in deze [page](../../rn/using/gold-standard.md).


### ![](assets/do-not-localize/red_2.png) Release 19.1.2 - build 9029{#release-19-1-2-build-9029}

_21 juni 2019_

**Verbeterde beveiliging**

* Om de beveiliging te optimaliseren, is de Java-bibliotheek (Netty) bijgewerkt naar de nieuwste versie (4.1.34). (NEO-12788)

**Verbeteringen**

* Oplossing voor een regressie in verband met het beheer van domeinkolommen waardoor e-mails niet konden worden verzonden op bepaalde configuraties.
* Om de prestaties te verbeteren, is een _operation=&quot;niets&quot;attribuut toegevoegd aan de vraag van de ZEEP rtEvent om &quot;SELECT VOOR UPDATE&quot;verzoeken te vermijden.
* Probleem met workflowweergave met uitgaande overgangen na de testactiviteit verholpen. (NEO-12727)
* We staan nu toe dat dummy-records die in Microsoft Dynamics zijn gemaakt, worden verwijderd tijdens de workflow voor importeren.
* Verbeterde machtigingen om het pakket met de beveiligingszone uit te voeren wanneer u een interne account gebruikt.


### ![](assets/do-not-localize/red_2.png) Release 19.1 - build 9026{#release-19-1-build-9026}

_30 mei 2019_

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
   <td> Configuratiescherm<br /> </td> 
   <td> <p>Om uw werk als Admin gebruiker efficiënter te maken, beheer montages van uw servers SFTP door opslag te controleren, voeg IP adressen aan lijst van gewenste personen toe, en installeer de sleutels van SSH voor elke instantie. Houd er rekening mee dat het Configuratiescherm vanaf vandaag alleen beschikbaar is voor klanten die op AWS worden gehost (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">login door de Experience Cloud vandaag</a>).</p> <p>Raadpleeg voor meer informatie de <a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=nl">gedetailleerde documentatie</a> en de <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=nl">Hoe kan ik-video</a>. </p><p>Opmerking: U hoeft niet te upgraden naar de nieuwste build voor campagnes om toegang te krijgen tot het Configuratiescherm.</p> </td> 
  </tr> 
    <tr> 
   <td> Audit trail<br /> </td> 
   <td> <p>Als beheerder verhoogt u de productiviteit door de wijzigingen in de Adobe Campaign Classic-instantie te controleren en te beheren. Het audittrail zal acties registreren die op Bronschema's, Werkschema's en Opties worden gemaakt. U kunt snel zien of is een element gecreeerd, gewijzigd of geschrapt.</p><p>Raadpleeg voor meer informatie de <a href="../../production/using/audit-trail.md">gedetailleerde documentatie</a> en <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html">hoe kan ik-video</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Guardrail, robuustheid en schaalbaarheid<br /> </td> 
   <td> Aan Campaign Classic is een aantal verbeteringen toegevoegd. Hieronder vindt u verbeteringen op het gebied van geleidbaarheid, robuustheid en schaalbaarheid.<br /> </td> 
  </tr> 
  <tr> 
   <td> Update over compatibiliteitsmatrix<br /> </td> 
   <td> Met deze nieuwe versie ondersteunt Adobe Campaign nu de volgende databasesystemen. Zie de <a href="https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html">Compatibiliteitsmatrix</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18 quater</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* Om veiligheidsredenen kunt u geen willekeurige opdrachten meer invoegen wanneer u de opdracht **[!UICONTROL Pre-process the file]** in een **[!UICONTROL Data loading (file)]** workflowactiviteit. Er is nu een vervolgkeuzelijst beschikbaar waarmee u uit drie opties kunt kiezen: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) of **[!UICONTROL Decrypt]** (gpg). De XtkSecurity_Disable_Preproc-beveiligingsmarkering is toegevoegd. Voor nieuwe klanten wordt deze optie ingesteld op 0. Voor bestaande klanten, zal deze optie aan 1 door postupgrade worden geplaatst om het vorige gedrag te houden. Zie dit [sectie](../../workflow/using/data-loading--file-.md).
* Probleem met wachtwoordzichtbaarheid verholpen die optrad tijdens het testen van de verbinding van een externe FDA-account zonder tijdzone ingesteld.
* De PDFBox-bibliotheek is verwijderd.
* Tomcat is bijgewerkt naar versie 7.0.93.
* Oplossing voor een token-zichtbaarheidsprobleem dat optrad wanneer het beveiligingstoken ongeldig was.
* Oplossing voor een mogelijk XTK-injectieprobleem in de WSDL JSP (schemawsdl.jsp).
* De referentie- en wachtwoordopslag in de broncode en het brongeheugen van de toepassing is geoptimaliseerd.
* PII-weergavebeperking is geoptimaliseerd. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* Correctie van inconsistentieproblemen in geheime sleutelbeheer.
* Dezelfde algemene fout wordt nu weergegeven voor mislukte aanmeldingspogingen met een geldige of ongeldige gebruikersnaam.
* De naamgeving van geüploade bestanden is verbeterd.
* Er is een nieuwe optie XtkSecurity_Disable_GetSetEnv toegevoegd om het gebruik van setEnv- en getEnv-functies te blokkeren.
* Gevoelige informatie wordt nu verborgen in de stacktracering van de toepassing.

**Verbeteringen op het gebied van Guardrail, robuustheid en schaalbaarheid**

* Lifespan - Optimalisatie van het reeksgebruik van XtkNewId: de meest verbruikende lijsten zijn verplaatst van de xtkNewId opeenvolging naar specifieke opeenvolgingen.
* FDA over HTTP v2: De FDA over het protocol van HTTP wordt wijd gebruikt op Hybride plaatsingen, vooral voor de herwinning en de leveringsvoorbereiding bredeLogboek. De robuustheid is verbeterd om netwerkkwesties en mogelijke fouten te vermijden zoals het terugwinnen van of het duwen van gegevens. Dit vereist dat bouwt bij beide einden van de verbinding bijgewerkt is, anders zal het oude protocol nog worden gebruikt.
* Workflow voor bijhouden: de volgwerkstroom is robuuster geworden. Verschillende problemen met betrekking tot het bijhouden van logbestanden, invoegingen/updates en aanpassing van URL-tracking zijn opgelost. Bovendien detecteert de workflow voor bijhouden nu problemen met trackinglogbestanden die tot fouten kunnen leiden en de workflow kunnen stoppen. Deze kwesties worden nu genegeerd en niet verwerkt.
* Workflow voor opschonen: de opschoningsworkflow is verbeterd om mogelijke fouten en stops te voorkomen . Hierdoor worden de databasegrootte en de prestaties geoptimaliseerd.
* Ingesloten afbeeldingen in transactieberichten: wij hebben de volledige steun van ingebedde beelden in transactionele berichten toegevoegd, om mogelijke neerstortingen of ontbrekende beelden te vermijden.
* Databasegrootte - XtkJobLog: er is een zuiveringsmechanisme toegevoegd aan deze tabel. Dit heeft een positief effect op de databasegrootte.
* BCC-archivering: de standaardparameters voor BCC-archivering zijn gewijzigd om de archiveringssnelheid te verhogen. [Meer informatie](../../installation/using/email-archiving.md#parameters)
* Update van databasestructuur: SQL de verzoeken die door de Tovenaar van de Update van de Structuur van het Gegevensbestand worden geproduceerd zijn verbeterd voor snellere uitvoering.
* Hulplijnen voor handelingen van de operator: er zijn diverse instructies ingevoerd om te voorkomen dat exploitanten acties uitvoeren die de integriteit van het platform kunnen aantasten . De ingebouwde schema&#39;s kunnen niet meer door de interface worden geschrapt. De XML van de workflowbron kan ook niet meer worden bewerkt door gebruikers die geen beheerder zijn.
* Er zijn twee nieuwe opties beschikbaar gesteld: **XtkSecurity_Restrict_EditXML** (hiermee kunt u de XML-code van de leveringen uitschakelen) en **NmsOperation_OperationMgtDebug** (staat u toe om de technische werkschemauitvoering te controleren operationMgt). [Meer informatie](../../installation/using/configuring-campaign-options.md)

**Andere wijzigingen**

* Pushmeldingen: We ondersteunen nu de optie Thread ID voor iOS push.
* Verbeterde het beheer van lange naamindexen die postupgrade-problemen kunnen veroorzaken.
* Nu, tijdens de analyse van een decomail levering, als de publicatiemodus wordt geplaatst aan **[!UICONTROL None]** in de plaatsingstovenaar, wordt een fout geregistreerd en de analyse wordt tegengehouden: &quot;Publicatiemodus is ingesteld op &#39;none&#39;: Kan afbeelding niet insluiten. De beelden zullen niet op eigenschaptelefoon worden getoond.&quot; (NEO-12208)
* Het breedbandbeheer is verbeterd voor transactioneel overseinen. Wanneer de uitzendingen van de uitvoeringsinstantie aan de controleinstantie worden gesynchroniseerd, wordt het @lastModified gebied bijgewerkt aan de huidige datum van het systeem. De optie MC_Update_BlLastModified is toegevoegd voor besturingsinstanties. Waar betekent dat de huidige datum op de controleinstantie (standaardgedrag) zal worden gebruikt. Onwaar betekent dat we de @lastModified-datum van de uitzendingsinstantie gebruiken. (NEO-12579)
* Er zijn indexen toegevoegd aan de tijdelijke tabellen met coupons om het verzenden van leveringen te optimaliseren. (NEO-12437)
* In de integratie Analytics is het nu toegestaan AAM segmentgegevens op te halen met het teken %. (NEO-12025)
* Verwijderd de recordlimiet van 10.000 in WorkflowHeatmap om een probleem met ontbrekende gegevens op te lossen. (NEO-12329)
* Open Office wordt niet ondersteund en wordt nu volledig uit de toepassing verwijderd. Als u het nog steeds gebruikt, ga naar Libre Office omdat het vanaf 19.1 niet meer werkt.
* U kunt schrijven toegang tot de activiteit van de Update in Werkschema nu beperken gebruikend systeemfilterattributen. [Meer informatie](../../configuration/using/filtering-schemas.md)

**Patches**

* Probleem verholpen waardoor het certificaat niet kon worden geüpload voor mobiele pushberichten van iOS.
* Oplossing voor mogelijke terugkerende servercrashes voor pushberichten voor transacties. Andere problemen met crashes zijn opgelost.
* Probleem opgelost waarbij discrepanties tussen gebruikersactiviteiten werden gemeld en rapporten voor de open leveringsindicator werden bijgehouden. (NEO-11742)
* Probleem verholpen met de IMS-aanmelding.
* Probleem verholpen waarbij een afbeelding uit de bibliotheek werd toegevoegd en afbeeldingen in de levering konden ontbreken. (NEO-11900)
* Probleem opgelost dat zich kon voordoen bij het uitpakken van de details van de aanbieding in een directe postbestelling. (NEO-11700)
* Probleem verholpen dat gevolgen kon hebben voor de prestaties van SMS-berichten. (NEO-9812)
* Probleem verholpen waarbij de console vastloopt die kan optreden wanneer de optie Gedefinieerd in een extern bestand wordt gebruikt voor het hoofddoel van een levering. (NEO-12349)
* Probleem verholpen tijdens het analyseren van een bericht waarin ontvangers voor Japanse (.JP) domeinen als doel werden ingesteld. (NEO-12246)
* Oplossing voor een weergaveprobleem bij het gebruik van een verdeling van waarden met een 1:N-koppeling. (NEO-12212, NEO-11820)
* Probleem verholpen waarbij NmsMxDomain-fouten konden optreden in de MTA-logbestanden na een postupgrade. (NEO-12752)
* Probleem verholpen bij het gebruik van de optie &quot;Alle aanvullende gegevens uit de hoofdset behouden&quot; in een verrijkingswerkstroom. (NEO-13291)
* Probleem verholpen waarbij Tomcat vastliep tijdens het verzenden van pushberichten via HTTP2. (NEO-12701)
* Probleem verholpen met de HTTPRequest-API, die niet wachtte op alle callbacks om te voltooien. (NEO-12628)
* Probleem verholpen met het rekenproces van het volgen van indicatoren voor transactieberichten. (NEO-12529)
* Probleem opgelost met het gebruik van thema&#39;s in het beheer van aanbiedingen. (NEO-11804)
* Probleem met prestaties verholpen bij het verzenden van pushberichten. (NEO-11787)
* FIstelde een kwestie toen het voorvertonen van een uitgaand dossier van XML of CSV in aanbiedingsbeheer voor een directe postlevering. (NEO-11290)
* Probleem verholpen bij installatie van de **Sociale netwerken beheren** (Sociale marketing). (NEO-12081)
* Probleem verholpen waarbij u een webtoepassing niet kon verwijderen, zelfs als u de juiste toegangsrechten had. (NEO-12072)
* Probleem verholpen waarbij enkele waarden zouden kunnen worden overschreven bij het exporteren en vervolgens importeren van een object via XML. De optie XtkExport_IncludeDefaultValues is toegevoegd. Wanneer ingesteld op Waar (standaardgedrag), worden alle waarden geëxporteerd. Wanneer ingesteld op Onwaar, worden wijzigingen overschreven met de standaardwaarde. (NEO-11979)
* Het probleem dat de oorzaak was van de **[!UICONTROL Alert]** workflowactiviteit mislukt wanneer een verrijkingsactiviteit is toegevoegd na een query. (NEO-12132)
* Probleem verholpen met instellingen van Oracles waarbij verschuivingen van pijplijnen (triggers) niet correct zijn opgehaald uit de database waardoor duplicaten werden veroorzaakt. (NEO-12121)
* Correctie van een probleem dat weergavefouten kon veroorzaken in draaitabellen bij gebruik van de integratie Analytics (NEO-12103)
* Probleem opgelost met het rapport van de beschrijvende analyse. (NEO-11414)
* Probleem verholpen met CRM-connectors wanneer de externe tabel een veld met een onderstrepingsteken in de naam bevatte.
* Probleem opgelost waarbij valutasymbolen in Hypotheseverslagen konden worden weergegeven. (NEO-11634)
* Probleem met omleiding en tekstspatiëring verholpen bij het gebruik van bepaalde tekens voor het bijhouden van koppelingen.
* Probleem verholpen waarbij de voorvertoning van de aanbieding niet correct werkte.
* Probleem verholpen waarbij zachte grenzen niet uit de adrestabel werden verwijderd.
* Oplossing voor een JAVA-fout bij het gebruik van streepjescodes.
* Probleem met vertaling in webtoepassingen opgelost (NEO-12460)
* Probleem verholpen met de s3-activiteit van de workflow voor bestandsoverdracht. (NEO-12473)
* Probleem verholpen met datumvelden in webtoepassingen. (NEO-12496)
* Probleem verholpen met uitputting van id&#39;s bij gebruik van zaadadressen in een levering. (NEO-11842)
* Probleem verholpen met fantoomjs en Debian 9-compatibiliteit.
* Correctie van een fout bij het goedkeuren van de inhoud van een proefdruk. (NEO-12725)
* Probleem verholpen met de workflowfunctie &quot;Deze subset uitsluiten van populatie&quot;. (NEO-12441)
* Oplossing voor een probleem met de HTTPRequest-wait API die niet op alle callbacks wachtte. (NEO-12628)
* Probleem verholpen met de taak Gedeeld publiek bijwerken in een gesplitste activiteit. (NEO-11562)
* Probleem verholpen waarbij de webserver vastliep. (NEO-12904)
* Probleem verholpen met de parameter Natuur in transactiesjablonen. (NEO-12334)
* Probleem verholpen waarbij de console vastliep tijdens de weergave van bijgehouden URL&#39;s in de e-mailteksteditor. (NEO-13122)
* Probleem verholpen met de activiteit Bestand splitsen bij het importeren van soorten publiek uit Audience Manager. (NEO-11550)
* Probleem verholpen dat fouten veroorzaakte in het rapport met hot click. (NEO-11459)
* Probleem verholpen met renderen van aanbieding. (NEO-11565)
* Probleem verholpen met de activiteit van de Update van de Lijst wanneer het invoeren van publiek van Audience Manager. (NEO-11226)
* Oplossing voor een probleem met de activiteiten en configuratie van de tijdzone van het Programma. (NEO-11662)
* Probleem verholpen waarbij de traceringsworkflow mislukte in het geval van onjuist gevormde URL&#39;s.
* Probleem met externe accounts opgelost na het importeren van het pakket met mobiele toepassingen.
* Probleem verholpen bij het toewijzen van een tijdzone aan een operator. (NEO-12464)
* Probleem verholpen waarbij fouten in de onderliggende logboeken konden optreden. (NEO-11539, NEO-8978)
* Probleem verholpen door te klikken op het pictogram Historie in een opgeslagen rapport. (NEO-11620)
* Probleem verholpen tijdens het bewerken van een draaiingstabel in een rapport. (NEO-12068)
