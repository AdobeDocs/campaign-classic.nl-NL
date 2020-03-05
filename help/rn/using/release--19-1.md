---
title: Versie 19.1
seo-title: Versie 19.1
description: Versie 19.1
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
source-git-commit: fd7bc26fe12a26d8fb0dcccd2135b799e76b52bd

---


# Versie 19.1{#release-19-1}

[Upgrade](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) maken| [Door het bedieningspaneel afgegeven](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) gegevens| [Bijwerken](../../rn/using/documentation-updates.md) documentatie| [Eerdere introducties](../../rn/using/release--19-1.md) | [Afgekeurde kenmerken](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>Algemene beschikbaarheid</strong></td>
   <td><img src="assets/blue3.png"/><strong>Releasekandidaat</strong></td> 
   <td><img src="assets/orange3.png"/><strong>Niet meer beschikbaar</strong></td> 
   <td><img src="assets/red3.png"/><strong>Afgekeurd</strong></td> 
  </tr> 
   <tr> 
   <td>De nieuwste stabiele build beschikbaar. Gebouw gevalideerd in productie.<br> </td>
   <td>Bouw bevestigd door Adobe. Wachten op het testen van de productie.<br> </td>
   <td>De nieuwere bouw beschikbaar met insectenmoeilijke situaties. Update is vereist.<br> </td>
   <td>Bevat bekende regressies. Update is verplicht.<br> </td>
  </tr> 
 </tbody> 
</table>

De **laatste stabiele build** is 9032 (205c981c3). Klik [hier](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/orange_2.png) Versie 19.1.6 - Bouwstijl 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Dit bouwwerk is slechts voor op-gebouw installaties. Voor hybride plaatsingen, zullen de ontvangen instanties blijven lopend bouwen 9032. Upgrade uw marketinginstantie niet naar de 9035-build omdat deze niet compatibel is met 9032.

_3 oktober 2019_

**Verbeteringen**

* Vast een kwestie wanneer het gebruiken van de Schakelaar van CRM voor Salesforce. (NEO-17712)
* Vaste een indexkwestie die prestatieskwesties kon veroorzaken wanneer het verzenden van transactiemeldingen.
* Vast een prestatieskwestie wanneer het verzenden van berichten. (NEO-17558)
* Vast een kwestie die tot bepaalde berichten kon leiden die niet door de server worden verwerkt van de Midden-sourcing. (NEO-12395)
* Vaste een kwestie die het volledige gebruik van de SQL activiteit van het Gegevensbeheer (het &quot;SQL genoemde recht van het Gegevensbeheer&quot;verhinderde).

## ![](assets/orange_2.png) Versie 19.1.5 - Bouwstijl 9033{#release-19-1-5-build-9033}

_13 augustus 2019_

**Verbeteringen**

* Vaste een kwestie met de SQL verklaring &quot;UITGEZOCHTE TELLING&quot;die op het standaardgegevensbestand eerder dan het gegevensbestand FDA tijdens de extractie van Gegevens in de activiteit van het Gegevensbeheer werd uitgevoerd.
* Om de mogelijkheden van de klanteninfrastructuur te verbeteren, is een de volmachtsverklaring van SFTP nu beschikbaar in het dossier van de serverconfiguratie.
* Vaste een de consoleneerstorting van de Cliënt wanneer het &quot;toevoegen van een verbonden lijst&quot;in de het werkschemaactiviteit van de Lading van Gegevens (RDBMS) zonder lijstnaam. (NEO-12213)
* Vaste een kwestie met de midEmetter pakketinstallatie door bevellijn.
* Een nieuwe authentificatieoptie is toegevoegd om geloofsbrieven OAuth binnen de AC schakelaar met de Dynamica van Microsoft te steunen. (NEO-11982)
* Het oplossen van kwestie met UUID (Unieke Universele Identifier) veroorzaakt verrijkingsactiviteit om met Hive FDA te ontbreken.

## Versie 19.1.4 - Bouwstijl 9032{#release-19-1-4-build-9032}

![](assets/green_2.png) 5 **maart 2020**: nieuwe build (9032-...205c981c3) die de volgende reparatie omvat:

* Vaste een kwestie met externe rekeningen gebruikend FTP over SSL. (NEO-20498)

![](assets/orange_2.png) 17 **december 2019**: nieuwe build (9032-...9d34fb17e) die de volgende reparatie omvat:

* Vast een volgende kwestie op de volgende communicatiekanalen: mobiele (SMS, MMS), push (iOS, Android) en sociale netwerken (Facebook, Twitter).
(NEO-19595)

![](assets/orange_2.png) 11 **december 2019**: nieuw gebouw (9032-...e28b428b7), met de volgende prefix:

* Vast een prestatieskwestie wanneer het verzenden van berichten met een gegevensbestand MSSQL. (NEO-17558)

![](assets/orange_2.png) 20 **november 2019**: nieuwe build (9032-...3468c7bb5) die de volgende correcties omvat:

* Vast een login kwestie via authentificatie IMS. (NEO-17312)
* Vaste een kwestie wanneer het tonen van cumulatieve rapporten over veelvoudige leveringen. (NEO-18165)
* Vaste een kwestie die de botsing van de Webserver kon blokkeren of maken.

![](assets/orange_2.png) 19 **september 2019**: nieuw gebouw (9032-...lmoe 805c93 ) , waarin de volgende zaken zijn opgenomen :

* Vast een kwestie wanneer het gebruiken van de Schakelaar van CRM voor Salesforce. (NEO-17712)
* Vaste een indexkwestie die prestatieskwesties kon veroorzaken wanneer het verzenden van transactiemeldingen.

![](assets/orange_2.png) 13 **augustus 2019**: aanvankelijke 19.1.4 bouwstijl die de volgende moeilijke situaties omvat:

* Vaste een kwestie met de planneractiviteit die ongewenste foutenmeldingen tijdens tovenaarsconfiguratie produceert. Omkeerupdate van NEO-11662. (NEO-17097)
* Vaste een regressie die door NEO-12727 wordt veroorzaakt die tot werkschema&#39;s kon leiden die worden tegengehouden wanneer een activiteit van de Test tweemaal werd uitgevoerd. (NEO-16835)
* Vaste een kwestie die tot een onjuiste code van HTTP leidde die (HTTP 200 O.K. in plaats van HTTP 403 Verboden) werd teruggekeerd toen een ongeldig of verlopen zittingsteken in API vraag werd gebruikt. (NEO-16826)
* Vast een probleem met de DKIM-sleutel die niet meer in e-mails is geïntegreerd, waardoor problemen met de te leveren items worden veroorzaakt. (NEO-16804)
* Vaste diverse kwesties met werkschema het plannen. De werkschema&#39;s waren gepland om eens per dag zonder rekening te houden met de plannersconfiguratie worden uitgevoerd. (NEO-16619, NEO-16426)

## ![](assets/orange_2.png) Versie 19.1.2 - Bouwstijl 9029{#release-19-1-2-build-9029}

_21 juni 2019_

**Beveiligingsverbeteringen**

* Om veiligheid te optimaliseren, is de bibliotheek van Java (Netty) bijgewerkt aan de recentste versie (4.1.34). (NEO-12788)

**Verbeteringen**

* Vast een regressie verbonden aan het beheer van de domeinkolom die e-mails op bepaalde configuraties verhinderde worden verzonden.
* Om prestaties te verbeteren, is een attribuut _operation=&quot;niets&quot;toegevoegd aan de vraag van de ZEEP rtEvent om &quot;UITGEZOCHT VOOR UPDATE&quot;verzoeken te vermijden.
* Vast een kwestie van de werkschemavertoning met uitgaande overgangen na de activiteit van de Test. (NEO-12727)
* Wij staan nu de schrapping van dummy verslagen toe die in de Dynamica van Microsoft tijdens het de invoerwerkschema worden gecreeerd.
* Verbeterde toestemmingen om het pakket van de veiligheidsstreek uit te voeren wanneer het gebruiken van interne rekening.

## ![](assets/orange_2.png) Versie 19.1 - Bouwstijl 9026{#release-19-1-build-9026}

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
   <td> Configuratiescherm<br /> </td> 
   <td> <p>Om efficiency in uw werk als gebruiker te verhogen Admin, beheer montages van uw servers SFTP door opslag te controleren, die IP adressen fluitend, en de sleutels van SSH voor elke instantie te installeren. Houd er rekening mee dat het Configuratiescherm vanaf vandaag alleen beschikbaar is voor klanten die op AWS zijn gehost (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">aanmelden via de cloud van de huidige</a>ervaring).</p> <p>Voor meer informatie, verwijs naar de <a href="https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html">gedetailleerde documentatie</a> en de <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/control-panel-acc/control-panel-overview.html">hoe te video</a>. </p><p>Opmerking: de verbetering aan de recentste bouw van de Campagne wordt niet vereist om tot het Controlebord toegang te hebben.</p> </td> 
  </tr> 
    <tr> 
   <td> Controlespoor<br /> </td> 
   <td> <p>Als admin, verhogingsproductiviteit door veranderingen te controleren en te leiden die binnen de Klassieke instantie van de Campagne van Adobe worden aangebracht. Het spoor van de Controle zal acties registreren die op bronSchema's, Werkschema's en Opties worden gemaakt. U kunt snel zien of is een element gecreeerd, gewijzigd of geschrapt.</p><p>Voor meer informatie, verwijs naar de <a href="../../production/using/audit-trail.md">gedetailleerde documentatie</a> en de <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/monitoring/audit-trail.html">hoe te video</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Guardrail, robuustheid en schaalbaarheid<br /> </td> 
   <td> Er is een reeks verbeteringen toegevoegd aan de Klassieke campagne. De verbeteringen op het gebied van geleidbaarheid, robuustheid en schaalbaarheid worden hieronder weergegeven.<br /> </td> 
  </tr> 
  <tr> 
   <td> Update compatibiliteitstabel<br /> </td> 
   <td> Met deze nieuwe versie, steunt de Campagne van Adobe nu de volgende gegevensbestandsystemen. Raadpleeg de <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">compatibiliteitstabel</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Tera 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Beveiligingsverbeteringen**

* Om veiligheidsredenen, kunt u geen willekeurige bevelen meer opnemen wanneer het gebruiken van de **[!UICONTROL Pre-process the file]** optie in een **[!UICONTROL Data loading (file)]** werkschemaactiviteit. Er is nu een vervolgkeuzelijst beschikbaar, zodat u uit drie opties kunt selecteren: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) of **[!UICONTROL Decrypt]** (gpg). De XtkSecurity_Disable_Preproc veiligheidsvlag is toegevoegd. Voor nieuwe klanten, zal deze optie aan 0 worden geplaatst. Voor bestaande klanten, zal deze optie aan 1 door de postupgrade worden geplaatst om het vorige gedrag te houden. Zie deze [sectie](../../workflow/using/data-loading--file-.md).
* Vast een kwestie van het wachtwoordzicht die voorkwam toen het testen van de verbinding van een externe rekening FDA zonder tijdzonereeks.
* De bibliotheek PDFBox is verwijderd.
* Tomcat is bijgewerkt naar versie 7.0.93.
* Vaste een symbolische zichtbaarheidskwestie die voorkwam toen het veiligheidsteken ongeldig was.
* Vast een potentieel injectieprobleem XTK in WSDL JSP (schemawsdl.jsp) aan.
* De aanmeldingsgegevens en wachtwoordopslag in de broncode en het geheugen van de toepassing zijn geoptimaliseerd.
* PII-meningsbeperking is geoptimaliseerd. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* Vaste incoherentieproblemen bij geheim sleutelbeheer.
* De zelfde generische fout wordt nu getoond voor ontbroken login pogingen met een geldige of ongeldige gebruikersbenaming.
* De naam van geüploade bestanden is verbeterd.
* Een nieuwe optie XtkSecurity_Disable_GetSetEnv is toegevoegd om het gebruik van setEnv en getEnv functies te blokkeren.
* De gevoelige informatie is nu verborgen in het spoor van de toepassingsstapel.

**Verbetering van de geleidbaarheid, robuustheid en schaalbaarheid**

* De optimalisering van het de opeenvolgingsgebruik van de Leven - XtkNewId: de meest verbruikende lijsten zijn bewogen van de xtkNewId opeenvolging aan specifieke opeenvolgingen. [Meer informatie](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* FDA over HTTP v2: het protocol FDA over HTTP wordt wijd gebruikt op Hybride plaatsingen, vooral voor bredeLogopvraging en leveringsvoorbereiding. De robuustheid is verbeterd om netwerkkwesties en mogelijke fouten te vermijden zoals het terugwinnen van of het duwen van gegevens. Dit vereist dat de bouw op beide einden van de verbinding bijgewerkt is, anders zal het oude protocol nog worden gebruikt.
* Volgwerkschema: de robuustheid van de traceringsworkflow is verbeterd. Verscheidene kwesties met betrekking tot het volgen van logboektussenvoegsels/updates en URL het volgen aanpassing zijn bevestigd. Bovendien ontdekt het volgende werkschema nu het volgen logboekkwesties die tot fouten konden leiden en het werkschema tegenhouden. Deze kwesties worden nu weggegooid en niet verwerkt.
* Schoonmaakwerkschema: de schoonmaakwerkschema is verbeterd om potentiële fouten en einden te vermijden. Dit optimaliseert gegevensbestandgrootte en prestaties.
* Ingebedde beelden in transactieberichten: wij hebben de volledige steun van ingebedde beelden in transactieberichten toegevoegd, om mogelijke neerstortingen of ontbrekende beelden te vermijden.
* Databasegrootte - XtkJobLog: aan deze tabel is een zuiveringsmechanisme toegevoegd . Dit heeft een positief effect op de gegevensbestandgrootte.
* BCC-archivering: de standaardparameters voor BCC archivering zijn veranderd om archiveringssnelheid te verhogen. [Meer informatie](../../installation/using/email-archiving.md#parameters)
* Update databasestructuur: SQL de verzoeken die door de Tovenaar van de Update van de Structuur van het Gegevensbestand worden geproduceerd zijn verbeterd voor snellere uitvoering.
* Handleidingen voor acties van de exploitant: er zijn verscheidene richtsnoeren opgesteld om te voorkomen dat exploitanten acties uitvoeren die de integriteit van het platform kunnen aantasten . De ingebouwde schema&#39;s kunnen niet meer door de interface worden geschrapt. Ook, kan de werkschemabron XML niet meer door gebruikers worden uitgegeven niet-admin.
* Er zijn twee nieuwe opties beschikbaar gesteld: **XtkSecurity_Restrict_EditXML** (staat u toe om de uitgave van te onbruikbaar te maken de&#39; code van XML van leveringen&#39;) en **NmsOperation_OperationMgtDebug** (staat u toe om de technische werkschemauitvoering te controleren operationMgt). [Meer informatie](../../installation/using/configuring-campaign-options.md)

**Overige mutaties**

* Duw meldingen: wij steunen nu de optie van identiteitskaart van de Draad voor de duw van iOS.
* Verbeterde het beheer van lange - naamindexen die postverbeteringskwesties konden veroorzaken.
* Nu, tijdens de analyse van een decomail levering, als de publicatiewijze aan **[!UICONTROL None]** in de plaatsingstovenaar wordt geplaatst, wordt een fout geregistreerd en de analyse wordt tegengehouden: &quot;De publicatiemodus wordt ingesteld op &quot;none&quot;: Kan afbeelding niet insluiten. De beelden zullen niet op eigenschaptelefoon worden getoond.&quot; (NEO-12208)
* Het breedbandbeheer is verbeterd voor transactieoverseinen. Wanneer de uitzendingen van de uitvoeringsinstantie aan de controleinstantie worden gesynchroniseerd, wordt het @lastModified gebied bijgewerkt aan de huidige datum van het systeem. De optie MC_Update_BlLastModified is toegevoegd voor controleinstanties. Waar betekent dat de huidige datum op de controleinstantie (standaardgedrag) zal worden gebruikt. Vals betekent dat wij @lastModified datum gebruiken van de uitvoeringsinstantie het logboek @lastModified. (NEO-12579)
* De indexen werden toegevoegd in de tijdelijke lijsten van de coupon om levering te optimaliseren verzendend. (NEO-12437)
* In de integratie van de Analyse, wordt de herwinning van het segmentgegevens van AAM met % karakter nu toegestaan. (NEO-12025)
* Verwijderde de recordlimiet van 10.000 records in Werkstroom Heatmap om een ontbrekend gegevensprobleem op te lossen. (NEO-12329)
* Het open Bureau wordt niet gesteund en nu volledig verwijderd uit de toepassing. Als je het nog steeds gebruikt, verplaats je naar Libre Office, want het werkt niet meer vanaf 19.1.
* U kunt de toegang tot de gegevens van de Update in Werkschema nu beperken Write gebruikend systeemattributen. [Meer informatie](../../configuration/using/filtering-schemas.md)

**Patches**

* Vast een kwestie die het certificaat verhinderde om voor mobiele dupberichten van iOS te worden geupload.
* Vaste potentiële terugkerende servercrashes voor transactiepush-meldingen. Andere problemen met een crash zijn opgelost.
* Vaste een kwestie die rapporteringsdiscrepanties tussen gebruikersactiviteiten en het volgen rapporten voor de open leveringsindicator veroorzaakte. (NEO-11742)
* Vast een kwestie met login IMS.
* Vast een kwestie aan die tot ontbrekende beelden in een levering kon leiden wanneer het toevoegen van een beeld van de bibliotheek. (NEO-11900)
* Vaste een kwestie die kon voorkomen wanneer het halen van aanbiedingsdetails in een directe postlevering. (NEO-11700)
* Vaste een kwestie die de transactionele berichtprestaties van SMS kon beïnvloeden. (NEO-9812)
* Vast een consoleneerstorting die kon voorkomen wanneer het gebruiken van Defined in een externe dossieroptie voor het belangrijkste doel van een levering. (NEO-12349)
* Vaste een kwestie wanneer het analyseren van een bericht dat ontvangers voor Japanse (.JP) domeinen richtte. (NEO-12246)
* Vast een vertoningskwestie wanneer het gebruiken van een distributie van waarden met een verbinding 1:N. (NEO-12212, NEO-11820)
* Vaste een kwestie die fouten NmsMxDomain in de logboeken MTA na een postupgrade kon veroorzaken. (NEO-12752)
* Vast een kwestie wanneer het gebruiken van &quot;houd alle extra gegevens van de belangrijkste reeks&quot;optie in een activiteit van het verrijkingswerkschema. (NEO-13291)
* Vast een de botsingskwestie van de Tomcat wanneer het verzenden van duw- berichten gebruikend HTTP2. (NEO-12701)
* Vaste een kwestie met HTTPRequest API die niet op alle callbacks wachtte eindigen. (NEO-12628)
* Vast een kwestie met het gegevensverwerkingsproces om indicatoren voor transactieberichten te volgen. (NEO-12529)
* Vast een kwestie met het gebruik van thema&#39;s in aanbiedingsbeheer. (NEO-11804)
* Vast een prestatieskwestie wanneer het verzenden van duw- berichten. (NEO-11787)
* FIxed een kwestie wanneer het previewing van een uitgaand dossier van XML of CSV in aanbiedingsbeheer voor een directe postlevering. (NEO-11290)
* Vast een kwestie wanneer het installeren van het **Managing pakket van Sociale Netwerken** (Sociale Marketing). (NEO-12081)
* Vaste een kwestie die u verhinderde een Webtoepassing te schrappen zelfs als u de correcte toegangsrechten had. (NEO-12072)
* Vast een kwestie die kon veroorzaken dat sommige waarden worden beschreven wanneer het uitvoeren van en dan het invoeren van een voorwerp via XML. De optie XtkExport_IncludeDefaultValues is toegevoegd. Wanneer de reeks aan Waar (standaardgedrag), alle waarden wordt uitgevoerd. Wanneer de reeks aan Vals, de wijzigingen met de standaardwaarde wordt beschreven. (NEO-11979)
* Vaste een kwestie die de **[!UICONTROL Alert]** werkschemaactiviteit veroorzaakte om te ontbreken toen een verrijkingsactiviteit na een vraag werd toegevoegd. (NEO-12132)
* Vaste een kwestie op de opstellingen van Oracle waar de pijpleiding (trekkers) compensatie niet met succes van het gegevensbestand werd teruggewonnen veroorzakend duplicaten. (NEO-12121)
* Vast een kwestie die vertoningsfouten in spillijsten kon veroorzaken wanneer het gebruiken van de integratie van de Analyse (NEO-12103)
* Vaste een kwestie met het Beschrijvende rapport van de Analyse. (NEO-11414)
* Vaste een kwestie met de schakelaars van CRM wanneer de verre lijst een gebied met een onderstreepteken in zijn naam bevatte.
* Vast een kwestie die een vertoningskwestie voor muntsymbolen in de Hypotheseverslagen kon veroorzaken. (NEO-11634)
* Vaste een redirection en het volgen kwestie wanneer het gebruiken van bepaalde karakters in het volgen van verbindingen.
* Vaste een kwestie die aanbiedingsvoorproef verhinderde correct te werken.
* Vast een kwestie met zachte steunen die niet uit de adreslijst worden verwijderd.
* Vast een fout JAVA wanneer het gebruiken van streepjescodes.
* Vast een vertaalprobleem in webtoepassingen (NEO-12460)
* Vast een kwestie met de s3 het werkschemaactiviteit van de Overdracht van het Dossier. (NEO-12473)
* Vaste een kwestie met datumgebieden in Webtoepassingen. (NEO-12496)
* Vast een de uitputtingskwestie van identiteitskaart wanneer het gebruiken van zaadadressen in een levering aan. (NEO-11842)
* Vast een kwestie met fantoomjs en Debian 9 verenigbaarheid.
* Vast een fout wanneer het goedkeuren van de inhoud van een bewijs. (NEO-12725)
* Vast een kwestie met &quot;sluit deze ondergroep van de populatie&quot;werkschemaeigenschap uit. (NEO-12441)
* Vaste een kwestie met HTTPRequest-wacht API die niet op alle callbacks wachtte eindigen. (NEO-12628)
* Vaste een kwestie met de &quot;Update Gedeelde taak van het Publiek&quot;in een gespleten activiteit. (NEO-11562)
* Vast een de botsingskwestie van de Webserver. (NEO-12904)
* Vast een kwestie met de parameter van de Aard in transactionele malplaatjes aan. (NEO-12334)
* Vaste een kwestie van de consoleneerstorting wanneer het tonen van gevolgde URLs in de redacteur van de e-mailtekst. (NEO-13122)
* Vaste een kwestie met de Gespleten activiteit van het Dossier wanneer het invoeren van publiek van de Manager van het Publiek. (NEO-11550)
* Vaste een kwestie die fouten in het hete klikrapport veroorzaakte. (NEO-11459)
* Vast een kwestie met voorstel het teruggeven aan. (NEO-11565)
* Vaste een kwestie met de activiteit van de Update van de Lijst wanneer het invoeren van publiek van de Manager van het Publiek. (NEO-11226)
* Vast een kwestie met de de activiteit van het Programma en configuratie van de tijdzone. (NEO-11662)
* Vaste een kwestie die het volgende werkschema om in het geval van misvormde URLs veroorzaakte te ontbreken.
* Vaste een kwestie met externe rekeningen na het invoeren van het mobiele toepassingspakket.
* Vast een kwestie wanneer het toewijzen van een tijdzone aan een exploitant. (NEO-12464)
* Vast een kwestie die fouten in de kindlogboeken kon veroorzaken. (NEO-11539, NEO-8978)
* Vaste een kwestie wanneer het klikken van het pictogram van de Geschiedenis in een bewaard rapport. (NEO-11620)
* Vaste een kwestie wanneer het uitgeven van een spillijst in een rapport. (NEO-12068)
