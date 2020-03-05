---
title: Versie 19.2
seo-title: Versie 19.2
description: Versie 19.2
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


# Versie 19.2{#release-19-2}

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

## ![](assets/blue_2.png) Versie 19.2.3 - Bouwstijl 9081 {#release-19-2-3-build-9081}

_07 februari 2020_

**Verbeteringen**

* Vast een regressiekwestie toe te schrijven aan de implementatie van SSL certificatie die de gebruikersverbinding om op de server van Vensters veroorzaakte te ontbreken. (NEO-20629)
* Vaste een kwestie die een onjuist aantal van de versiemarkering in het **ongeveer** menu toonde.

## ![](assets/orange_2.png) Versie 19.2 - Bouwstijl 9080 {#release-19-2-build-9080}

_2 december 2019_

**Wat is nieuw?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA is de nieuwe privacywet van de Staat van Californië die de eisen van de gegevensbescherming harmoniseert en moderniseert die op 1 januari 2020 van kracht worden. CCPA is op de klanten van de Campagne van Adobe van toepassing die gegevens voor de Onderwerpen van Gegevens houden die in Californië verblijven.</p>
    <p>Naast de reeds beschikbare privacymogelijkheden (met inbegrip van toestemmingsbeheer, de montages van het gegevensbehoud, en gebruikersrollen), de hulp van de Campagne van Adobe vergemakkelijkt uw bereidheid voor CCPA:</p>
    <ul>
      <li>Recht op toegang en recht op verwijdering: we maken gebruik van de mogelijkheden die voor GDPR zijn toegevoegd. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Meer informatie</a></li>
      <li>U kunt volgen of een consument voor de verkoop van persoonlijke gegevens heeft gekozen. Voor dit, moet u de lijst van Profielen uitbreiden en een <strong>Opt-out voor gebied toevoegen CCPA</strong> . <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Meer informatie</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Werkstroom live-bewaking</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>U kunt de uitvoeringsstatus van alle werkschema's op uw instantie nu controleren gebruikend vooraf bepaalde meningen.</p>
   <p>Voor meer informatie, verwijs naar de <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">gedetailleerde documentatie</a>.</p></td> 
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
<td> <p>De Campagne van Adobe laat u toe om de nieuwe interactieve <a href="https://amp.dev/about/email/">AMP voor E-mail</a> formaat uit te proberen, dat marketeers toestaat om de componenten van AMP binnen berichten te omvatten om de e-mailervaring met rijke, dynamische en interactieve inhoud te verbeteren, direct actionable in het bericht zelf.</p>
   <p>Dit vermogen wordt vrijgegeven als openbare bèta.</p>
   <p>Voor meer informatie, verwijs naar de <a href="../../delivery/using/defining-interactive-content.md">gedetailleerde documentatie</a> en de <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">zelfstudie video</a>.</p><br /></td> 
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
<td> <p>Beveiligd SMS wordt nu gesteund door de Uitgebreide Algemene Schakelaar SMPP. Dit staat een gecodeerde verbinding aan de leverancier toe.</p> <p><strong>Waarschuwing</strong> Voor deze functie is een bijgewerkt certificaat vereist voor alle servers. De ongeldige, herroepen of verlopen certificaten zullen fouten produceren die het algemene SMS verzenden van mogelijkheden beïnvloeden.</p><p>Voor meer informatie, verwijs naar de <a href="https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html">gedetailleerde documentatie</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Beveiligingsverbeteringen**

* Vaste Opgeslagen de kwetsbaarheid van Scripting van de Kruisplaats in de interface van de Campagne - de bevestiging van inputgegevens en output het coderen. (NEO-16810)
* Vast een veiligheidskwestie op profielvergunning die toegang tot onbevoegde gegevens kon verlenen, door login beperkingsbeleid te versterken. (NEO-14445)

**Verbeteringen**

* Optimalisering van het geheugenverbruik voor afdrukberichten.
* Voor prestaties en opslagoptimalisering, is de behandeling van het **logins.log** - dossier verbeterd. Het dossier wordt nu verdeeld in veelvoudige dossiers, één elke dag met een maximum van 365 behouden dossiers. [Meer informatie](../../production/using/log-files.md)
* De externe rekening van CRM van de Dynamica van Microsoft kan nu worden gevormd gebruikend wachtwoordgeloofsbrieven (wachtwoord + gebruikersbenaming) of certificaat (privé sleutel). [Meer informatie](../../platform/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Sommige verbeteringen zijn toegevoegd aan de Hadoop FDA-connector om de betrouwbaarheid te verbeteren
* Een specifieke garantie is toegevoegd om schijfruimte te controleren alvorens toe te staan om openbare middelen op de server te uploaden.
* De nieuwe Opties van de [Campagne](../../installation/using/configuring-campaign-options.md) zijn toegevoegd:
   * De **WdbcKillSessionPolicy** configuratieoptie staat u toe om het **Onvoorwaardelijke gedrag van het Einde** op alle werkschema&#39;s en PostgreSQL- gegevensbestandvragen te beïnvloeden.
   * De optie **NmsOperation_DeliveryPreparationWindow** staat u toe om het aantal dagen te bepalen waarboven de leveringen met inconsistente status van de telling van lopende leveringen zullen worden uitgesloten.
   * De optie **WdbcOptions_TempDbName** staat u toe om een afzonderlijk gegevensbestand voor het werken van lijsten op de Server van Microsoft te vormen SQL. Dit optimaliseert steunen en replicatie. [Meer informatie](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * De optie **XtkCleanup_NoStats** is verbeterd voor PostgreSQL om het gedrag van de stap van de opslagoptimalisering van het werkschema van de gegevensbestandschoonmaakbeurt beter te controleren. [Meer informatie](../../production/using/database-cleanup-workflow.md#statistics-update)
* Er is een mechanisme voor het afsluiten van een account toegevoegd aan de **logon()** API. Het verhindert om het even welke verdere login pogingen na een bepaald aantal opeenvolgende ontbroken login pogingen binnen een gespecificeerd tijdsbestek.
* Een nieuwe optie van de de tijdstijd **van de** Maximum verpersoonlijking in de leveringseigenschappen staat u toe om een onderbreking voor de verpersoonlijkingsruntime te bepalen, om de verpersoonlijkingsfase te verhinderen te lang te lopen. [Meer informatie](../../delivery/using/personalization-fields.md#timing-out-personalization)
* De optie van het **ftp protocol** is toegevoegd om u toe te staan om een volmachtsconfiguratie voor de verbindingen van SFTP te gebruiken. [Meer informatie](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Nieuwe steun van volmachtstoegang tot een externe server van SFTP voor op-gebouwmilieu&#39;s.
* Er is een specifieke hulplijn toegevoegd om te voorkomen dat pakketten worden geïnstalleerd die niet compatibel zijn met de instantie Campaign. [Meer informatie](../../installation/using/installing-campaign-standard-packages.md)

_Afgekeurde systemen_

De volgende systemen zijn nu [afgekeurd](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html) voor de Klassieke implementaties van de Campagne:
* Apache 2.2
* Centos 6

Gelieve te verzekeren u op gesteunde versies van om het even welke systemen bent die in de recentste matrijs van de Verenigbaarheid van de Campagne worden vermeld. [Meer informatie](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

_Campagne Mobile SDK_

Bouwstijl 1.0.26 van iOS SDK is nu beschikbaar. In deze nieuwe bouwstijl, hebben wij de steun van iOS 13 toegevoegd. Deze nieuwe versie steunt nu berichtprioriteit en het nieuwe proces van het registratie symbolische beheer voor iOS 13 Duw berichten. Als u toepassingen op een vorige versie van SDK in werking stelt, moet u uw toepassingen met nieuwe SDK recompile. Om SDK te krijgen, gelieve de Zorg van de Klant van Adobe te contacteren.

**Patches**

* De vaste consoleneerstorting die kon voorkomen wanneer het toevoegen van een lege verbonden lijst in de het werkschemaactiviteit van de Lading van **Gegevens (RDBMS)** . (NEO-12213)
* Vast een kwestie die tot bepaalde berichten kon leiden die niet door de server worden verwerkt van de Midden-sourcing. (NEO-12395)
* Vast een kwestie in het werkschema van de gegevensbestandschoonmaakbeurt wanneer het gebruiken van de vraag het verbinden optie met Teradata. (NEO-12399)
* Vaste een kwestie die leveringsanalyse met typologieregel met inbegrip van ne.jp domein beïnvloedt. (NEO-12609)
* Vaste een kwestie met betrekking tot SMS over de updates van TLS die op een restrictiever certificaatbeleid impliceerden. Deze updates zouden tot een verbindingsmislukking tussen marketing en midsourcing servers kunnen leiden in het geval van een verouderd certificaat. (NEO-17698)
* Vast een probleem aan bij het gebruik van de knop **Test-verbinding** op een externe account in een omgeving met gemiddelde sourcing met Vault-verificatie. (NEO-12722)
* Vast een kwestie op vragen gebruikend datumfuncties met een verbinding FDA Hadoop. (NEO-12847)
* Vaste een kwestie wanneer het vervangen van een beeld in de e-mailredacteur. (NEO-13098)
* Vast een kwestie die tot post-verbeteringsfouten op omslagen kon leiden die waren geschrapt of naar een andere plaats verplaatst. (NEO-13118)
* Vaste een kwestie op beeldvertoning wanneer het gebruiken van het **Define beeld per de grootte** van het apparatenscherm optie op de berichten van de LIJN. (NEO-13228)
* Vast een kwestie van de leveringsvoorbereiding aan wanneer het **Exclude dubbele adres tijdens leveringsoptie** niet wordt geselecteerd. (NEO-13240)
* Vaste een kwestie in werkschema&#39;s wanneer het gebruiken van de de overdrachtactiviteit **van het** Dossier om dossiers te downloaden gebruikend de **Schrapping de brondossiers na overdrachtoptie** , met naam die een ruimtekarakter bevat. (NEO-13411)
* Vast een kwestie met de geheime voorgeheugenschoonmaakbeurt van Tomcat die tot geheugenkwesties zou kunnen leiden. (NEO-13456)
* Vaste een kwestie wanneer het installeren van de **Controle van aanbiedingsmotor met ingebouwde pakket van de uitvoeringsinstantie** op een bestaande controleinstantie die in Microsoft SQL 2017 loopt. (NEO-13539)
* De vaste consoleneerstorting die kon voorkomen wanneer het uncheck gevolgde URLs in een e-mail, van de inhoud **tabel van de** Tekst. (NEO-13545)
* Vast een het coderen kwestie op de Chinese afzendernaam. (NEO-13837)
* Vast een fout die kon opheffen wanneer het tonen van de gegevens van de enquêterespons van de Ontdekkingsreiziger. (NEO-14590)
* Vastgesteld een kwestie die tot discrepantie tussen de indeling van het leveringslogboek en de quarantainetabel zou kunnen leiden. (NEO-16547)
* Vast een probleem aan met DKIM-sleutels die niet in e-mails zijn ingebouwd. (NEO-16804)
* Vaste een kwestie die de verkeerde foutencode toonde toen een ongeldig zittingsteken in de context van API vraag werd gebruikt om gebeurtenissen teweeg te brengen. De foutcode was &#39;HTTP 200 OK&#39; in plaats van &#39;HTTP 403 Verboden&#39;. (NEO-16826)
* Vaste een kwestie wanneer het tonen van leveringsrapporten via Webtoegang. (NEO-17015)
* Vast een IMS authentificatiekwestie wanneer login aan de Campagne van Adobe. (NEO-17312)
* Vast een probleem aan waardoor quarantaine-e-mails tijdens het privacybeheerproces niet konden worden verwijderd. (NEO-17314)
* Vaste doorvoerproblemen na upgraden naar 9031 met SQL-database. (NEO-17558)
* Vaste een kwestie die de Schakelaar van CRM met Salesforce beïnvloedde. (NEO-17712)
* Vaste een onderbrekingskwestie wanneer het invoeren van gegevens van externe SFTP. (NEO-19723)
* Vast een kwestie wanneer het toegang tot van Predictive modellen. (NEO-19713)
* Vast een kwestie die willekeurige bemonstering in de **Gespleten** werkschemaactiviteit met de gegevensbestand van Hadoop FDA beïnvloedt. (NEO-16636)

