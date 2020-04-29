---
title: Release 19.1
seo-title: Release 19.1
description: Release 19.1
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
source-git-commit: eab67029d477044bc853f2a5c2de06ace70ebbee

---


# Release 19.1{#release-19-1}

[Upgrade](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) maken| [Release](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) van het regelpaneel| [Documentatie-updates](../../rn/using/documentation-updates.md) | [Eerdere versies](../../rn/using/release--19-1.md) | [Verouderde kenmerken](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>Algemene beschikbaarheid</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Releasekandidaat</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>Niet meer beschikbaar</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>Vervangen</strong></td> 
  </tr> 
   <tr> 
   <td>Nieuwste stabiele build beschikbaar. Build gevalideerd in productie.<br> </td>
   <td>Build gevalideerd door Adobe. Wachten op proefdrukken van de productie.<br> </td>
   <td>Nieuwere build beschikbaar met foutoplossingen. Bijwerken is vereist.<br> </td>
   <td>Bevat bekende regressies. Bijwerken is verplicht.<br> </td>
  </tr> 
 </tbody> 
</table>

De **laatste stabiele build** is 9032 (3a9dc9c). Klik [hier](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/do-not-localize/orange_2.png) Release 19.1.6 - build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Deze build is alleen bedoeld voor installaties op locatie. Voor hybride plaatsingen, zullen de ontvangen instanties blijven lopend de 9032 bouwstijl. Upgrade uw marketingexemplaar niet naar de 9035-build omdat deze niet compatibel is met 9032.

_3 oktober 2019_

**Verbeteringen**

* Probleem verholpen bij gebruik van de CRM-connector voor Salesforce. (NEO-17712)
* Probleem verholpen met een index die prestatieproblemen kan veroorzaken bij het verzenden van transactieberichten.
* Oplossing voor een prestatieprobleem bij het verzenden van berichten. (NEO-1758)
* Probleem verholpen dat ertoe kon leiden dat bepaalde berichten niet werden verwerkt door de server voor middeluitgaven. (NEO-12395)
* Probleem verholpen waardoor de SQL-gegevensbeheeractiviteit niet volledig kon worden gebruikt (het genoemde recht SQL-gegevensbeheer ontbreekt).

## ![](assets/do-not-localize/orange_2.png) Release 19.1.5 - build 9033{#release-19-1-5-build-9033}

_13 augustus 2019_

**Verbeteringen**

* Probleem verholpen met de SQL-instructie &#39;SELECT COUNT&#39;, die werd uitgevoerd in de standaarddatabase in plaats van in de FDA-database tijdens het ophalen van gegevens in gegevensbeheeractiviteiten.
* Om de mogelijkheden van de klanteninfrastructuur te verbeteren, is een de volmachtsverklaring van SFTP nu beschikbaar in het dossier van de serverconfiguratie.
* Probleem verholpen waarbij de clientconsole vastliep wanneer een gekoppelde tabel werd toegevoegd aan de activiteit van de RDBMS-workflow (Data Loading) zonder tabelnaam. (NEO-12213)
* Probleem verholpen met de installatie van het midEmetter-pakket via de opdrachtregel.
* Een nieuwe authentificatieoptie is toegevoegd om geloofsbrieven OAuth binnen de AC schakelaar met de Dynamica van Microsoft te steunen. (NEO-11982)
* Probleem met UUID (Unique Universal Identifier) verrijkingsactiviteit mislukt met Hive FDA.

## Release 19.1.4 - build 9032{#release-19-1-4-build-9032}

![](assets/do-not-localize/green_2.png) 29 **april 2020**: new build (9032@3a9dc9c), die de volgende oplossing bevat:

* Verbeterde beveiliging voor het bijhouden van koppelingen in e-mail. Dit is standaard ingeschakeld voor alle klanten. Er is een extra, verbeterde beveiligingsfunctie beschikbaar die kan worden ingeschakeld door de klantenservice te bereiken. Meer informatie over de functie en de stappen die niet-gehoste klanten moeten uitvoeren, vindt u in de checklist [voor](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)beveiliging en privacy.
* Probleem verholpen waarbij afbeeldingen niet konden worden weergegeven bij levering op regel. (NEO-23207)

![](assets/do-not-localize/orange_2.png) 5 **maart 2020**: new build (9032@19f73c5), die de volgende oplossing bevat:

* Probleem met externe accounts met FTP via SSL opgelost. (NEO-20498)

![](assets/do-not-localize/orange_2.png) 17 **december 2019**: new build (9032@d6b8062), die de volgende oplossing bevat:

* Probleem met bijhouden van gegevens op de volgende communicatiekanalen verholpen: mobiele (SMS, MMS), push (iOS, Android) en sociale netwerken (Facebook, Twitter). (NEO-19595)

![](assets/do-not-localize/orange_2.png) 11 **december 2019**: new build (9032@bc4a935), die de volgende oplossing bevat:

* Oplossing voor een prestatieprobleem bij het verzenden van berichten met een MSSQL-database. (NEO-1758)

![](assets/do-not-localize/orange_2.png) 20 **november 2019**: new build (9032@3468c7b) met de volgende oplossingen:

* Oplossing voor een aanmeldingsprobleem via IMS-verificatie. (NEO-17312)
* Probleem verholpen bij het weergeven van cumulatieve rapporten over meerdere leveringen. (NEO-18165)
* Probleem verholpen waarbij de webserver vastliep of kon blokkeren.

![](assets/do-not-localize/orange_2.png) 19 **september 2019**: new build (9032@cee805c) met de volgende oplossingen:

* Probleem verholpen bij gebruik van de CRM-connector voor Salesforce. (NEO-17712)
* Probleem verholpen met een index die prestatieproblemen kan veroorzaken bij het verzenden van transactieberichten.

![](assets/do-not-localize/orange_2.png) 13 **augustus 2019**: eerste 19.1.4-build met de volgende oplossingen:

* Oplossing voor een probleem met de planneractiviteit die ongewenste foutberichten tijdens de configuratie van de wizard genereerde. Update van NEO-11662 wordt teruggedraaid. (NEO-17097)
* Oplossing voor een regressie veroorzaakt door NEO-12727 die ertoe zou kunnen leiden dat werkstromen worden gestopt wanneer een testactiviteit tweemaal werd uitgevoerd. (NEO-16835)
* Probleem verholpen waarbij een onjuiste HTTP-code werd geretourneerd (HTTP 200 OK in plaats van HTTP 403 Verboden) wanneer een ongeldig of verlopen sessietoken werd gebruikt in API-aanroepen. (NEO-16826)
* Probleem verholpen met de DKIM-sleutel die niet meer in e-mails was ingesloten, waardoor problemen met de te leveren items ontstonden. (NEO-16804)
* Verschillende problemen met workflowplanning zijn opgelost. De werkschema&#39;s werden gepland om één keer per dag te worden uitgevoerd zonder rekening te houden met de plannerconfiguratie. (NEO-16619, NEO-16426)

## ![](assets/do-not-localize/orange_2.png) Release 19.1.2 - build 9029{#release-19-1-2-build-9029}

_21 juni 2019_

**Verbeterde beveiliging**

* Om de beveiliging te optimaliseren, is de Java-bibliotheek (Netty) bijgewerkt naar de nieuwste versie (4.1.34). (NEO-12788)

**Verbeteringen**

* Oplossing voor een regressie in verband met het beheer van domeinkolommen waardoor e-mails niet konden worden verzonden op bepaalde configuraties.
* Om de prestaties te verbeteren, is een _operation=&quot;niets&quot;attribuut toegevoegd aan de vraag van de ZEEP rtEvent om &quot;SELECT VOOR UPDATE&quot;verzoeken te vermijden.
* Probleem met workflowweergave met uitgaande overgangen na de testactiviteit verholpen. (NEO-12727)
* Wij staan nu de schrapping van dummy verslagen toe die in de Dynamica van Microsoft tijdens het invoeren werkschema worden gecreeerd.
* Verbeterde machtigingen om het pakket met de beveiligingszone uit te voeren wanneer u een interne account gebruikt.

## ![](assets/do-not-localize/orange_2.png) Release 19.1 - build 9026{#release-19-1-build-9026}

_30 mei 2019_

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
   <td> Deelvenster Beheer<br /> </td> 
   <td> <p>Om uw werk als Admin gebruiker efficiënter te maken, beheer montages van uw servers SFTP door opslag, het fluiten van IP adressen, en het installeren van de sleutels van SSH voor elke instantie te controleren. Houd er rekening mee dat het Configuratiescherm vanaf vandaag alleen beschikbaar is voor klanten die op AWS worden gehost (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">meld u vandaag</a>aan via de Experience Cloud).</p> <p>Raadpleeg voor meer informatie de <a href="https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html">gedetailleerde documentatie</a> en de <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/control-panel-acc/control-panel-overview.html">Hoe kan ik-video</a>. </p><p>Opmerking: U hoeft niet te upgraden naar de nieuwste build voor campagnes om toegang te krijgen tot het Configuratiescherm.</p> </td> 
  </tr> 
    <tr> 
   <td> Audittrail<br /> </td> 
   <td> <p>Als beheerder verhoogt u de productiviteit door de wijzigingen te controleren en te beheren die in de Adobe Campagne Classic-instantie zijn aangebracht. Het audittrail zal acties registreren die op Bronschema's, Werkschema's en Opties worden gemaakt. U kunt snel zien of is een element gecreeerd, gewijzigd of geschrapt.</p><p>Raadpleeg voor meer informatie de <a href="../../production/using/audit-trail.md">gedetailleerde documentatie</a> en <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/monitoring/audit-trail.html">hoe kan ik-video</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Guardrail, robuustheid en schaalbaarheid<br /> </td> 
   <td> Er is een aantal verbeteringen toegevoegd aan Campaign Classic. Hieronder vindt u verbeteringen op het gebied van geleidbaarheid, robuustheid en schaalbaarheid.<br /> </td> 
  </tr> 
  <tr> 
   <td> Update over compatibiliteitsmatrix<br /> </td> 
   <td> Met deze nieuwe versie ondersteunt Adobe Campaign nu de volgende databasesystemen. Raadpleeg de <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">compatibiliteitsmatrix</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* Om veiligheidsredenen kunt u geen willekeurige opdrachten meer invoegen wanneer u de **[!UICONTROL Pre-process the file]** optie gebruikt in een **[!UICONTROL Data loading (file)]** werkstroomactiviteit. Er is nu een vervolgkeuzelijst beschikbaar waarmee u uit drie opties kunt kiezen: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) of **[!UICONTROL Decrypt]** (gpg). De XtkSecurity_Disable_Preproc-beveiligingsmarkering is toegevoegd. Voor nieuwe klanten wordt deze optie ingesteld op 0. Voor bestaande klanten, zal deze optie aan 1 door postupgrade worden geplaatst om het vorige gedrag te houden. Zie deze [sectie](../../workflow/using/data-loading--file-.md).
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

* Lifespan - Optimalisatie van het reeksgebruik van XtkNewId: de meest verbruikende lijsten zijn verplaatst van de xtkNewId opeenvolging naar specifieke opeenvolgingen. [Meer informatie](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* FDA over HTTP v2: De FDA over het protocol van HTTP wordt wijd gebruikt op Hybride plaatsingen, vooral voor de herwinning en de leveringsvoorbereiding bredeLogboek. De robuustheid is verbeterd om netwerkkwesties en mogelijke fouten te vermijden zoals het terugwinnen van of het duwen van gegevens. Dit vereist dat bouwt bij beide einden van de verbinding bijgewerkt is, anders zal het oude protocol nog worden gebruikt.
* Workflow voor bijhouden: de volgwerkstroom is robuuster geworden. Verschillende problemen met betrekking tot het bijhouden van logbestanden, invoegingen/updates en aanpassing van URL-tracking zijn opgelost. Bovendien detecteert de workflow voor bijhouden nu problemen met trackinglogbestanden die tot fouten kunnen leiden en de workflow kunnen stoppen. Deze kwesties worden nu genegeerd en niet verwerkt.
* Workflow voor opschonen: de opschoningsworkflow is verbeterd om mogelijke fouten en stops te voorkomen . Hierdoor worden de databasegrootte en de prestaties geoptimaliseerd.
* Ingesloten afbeeldingen in transactieberichten: wij hebben de volledige steun van ingebedde beelden in transactionele berichten toegevoegd, om mogelijke neerstortingen of ontbrekende beelden te vermijden.
* Databasegrootte - XtkJobLog: er is een zuiveringsmechanisme toegevoegd aan deze tabel. Dit heeft een positief effect op de databasegrootte.
* BCC-archivering: de standaardparameters voor BCC-archivering zijn gewijzigd om de archiveringssnelheid te verhogen. [Meer informatie](../../installation/using/email-archiving.md#parameters)
* Update van databasestructuur: SQL de verzoeken die door de Tovenaar van de Update van de Structuur van het Gegevensbestand worden geproduceerd zijn verbeterd voor snellere uitvoering.
* Hulplijnen voor handelingen van de operator: er zijn diverse instructies ingevoerd om te voorkomen dat exploitanten acties uitvoeren die de integriteit van het platform kunnen aantasten . De ingebouwde schema&#39;s kunnen niet meer door de interface worden geschrapt. De XML van de workflowbron kan ook niet meer worden bewerkt door gebruikers die geen beheerder zijn.
* Er zijn twee nieuwe opties beschikbaar gesteld: **XtkSecurity_Restrict_EditXML** (staat u toe om de uitgave van de code van XML van leveringen&#39; onbruikbaar te maken) en **NmsOperation_OperationMgtDebug** (staat u toe om de technische werkschemauitvoering te controleren operationMgt). [Meer informatie](../../installation/using/configuring-campaign-options.md)

**Overige wijzigingen**

* Pushmeldingen: ondersteunen we nu de optie Thread ID voor iOS-push.
* Verbeterde het beheer van lange naamindexen die postupgrade-problemen kunnen veroorzaken.
* Nu, tijdens de analyse van een decomail levering, als de publicatiemodus aan **[!UICONTROL None]** in de plaatsingstovenaar wordt geplaatst, wordt een fout geregistreerd en de analyse wordt tegengehouden: &quot;Publicatiemodus is ingesteld op &#39;none&#39;: Kan afbeelding niet insluiten. De beelden zullen niet op eigenschaptelefoon worden getoond.&quot; (NEO-12208)
* Het breedbandbeheer is verbeterd voor transactioneel overseinen. Wanneer de uitzendingen van de uitvoeringsinstantie aan de controleinstantie worden gesynchroniseerd, wordt het @lastModified gebied bijgewerkt aan de huidige datum van het systeem. De optie MC_Update_BlLastModified is toegevoegd voor besturingsinstanties. Waar betekent dat de huidige datum op de controleinstantie (standaardgedrag) zal worden gebruikt. Onwaar betekent dat we de @lastModified-datum van de uitzendingsinstantie gebruiken. (NEO-12579)
* Er zijn indexen toegevoegd aan de tijdelijke tabellen met coupons om het verzenden van leveringen te optimaliseren. (NEO-12437)
* In de integratie Analytics is het nu toegestaan om AAM-segmentgegevens met %-teken op te halen. (NEO-12025)
* Verwijderd de recordlimiet van 10.000 in WorkflowHeatmap om een probleem met ontbrekende gegevens op te lossen. (NEO-12329)
* Open Office wordt niet ondersteund en wordt nu volledig uit de toepassing verwijderd. Als u het nog steeds gebruikt, ga naar Libre Office omdat het vanaf 19.1 niet meer werkt.
* U kunt schrijven toegang tot de activiteit van de Update in Werkschema nu beperken gebruikend systeemfilterattributen. [Meer informatie](../../configuration/using/filtering-schemas.md)

**Patches**

* Probleem verholpen waardoor het certificaat niet kon worden geüpload voor mobiele pushberichten voor iOS.
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
* Probleem verholpen bij de installatie van het pakket **Sociale netwerken** beheren (Social Marketing). (NEO-12081)
* Probleem verholpen waarbij u een webtoepassing niet kon verwijderen, zelfs als u de juiste toegangsrechten had. (NEO-12072)
* Probleem verholpen waarbij enkele waarden zouden kunnen worden overschreven bij het exporteren en vervolgens importeren van een object via XML. De optie XtkExport_IncludeDefaultValues is toegevoegd. Wanneer ingesteld op Waar (standaardgedrag), worden alle waarden geëxporteerd. Wanneer ingesteld op Onwaar, worden wijzigingen overschreven met de standaardwaarde. (NEO-11979)
* Probleem verholpen waarbij de **[!UICONTROL Alert]** workflowactiviteit mislukte wanneer een verrijkingsactiviteit werd toegevoegd na een query. (NEO-12132)
* Probleem verholpen met Oracle-instellingen waarbij verschuivingen van de pijplijn (triggers) niet met succes zijn opgehaald uit de database waardoor duplicaten werden veroorzaakt. (NEO-12121)
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
* Probleem verholpen met de activiteit van de Update van de Lijst wanneer het invoeren van publiek van de Manager van het Publiek. (NEO-11226)
* Oplossing voor een probleem met de activiteiten en configuratie van de tijdzone van het Programma. (NEO-11662)
* Probleem verholpen waarbij de traceringsworkflow mislukte in het geval van onjuist gevormde URL&#39;s.
* Probleem met externe accounts opgelost na het importeren van het pakket met mobiele toepassingen.
* Probleem verholpen bij het toewijzen van een tijdzone aan een operator. (NEO-12464)
* Probleem verholpen waarbij fouten in de onderliggende logboeken konden optreden. (NEO-11539, NEO-8978)
* Probleem verholpen door te klikken op het pictogram Historie in een opgeslagen rapport. (NEO-11620)
* Probleem verholpen tijdens het bewerken van een draaiingstabel in een rapport. (NEO-12068)
