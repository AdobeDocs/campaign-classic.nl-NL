---
solution: Campaign Classic
product: campaign
title: Release 19.2
description: Release 19.2
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: b5b9e42eca25193cf4d69f654e74a02afd8adca9
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 14%

---


# Release 19.2{#release-19-2}

## ![](assets/do-not-localize/limited_2.png) Release 19.2.4 - build 9082 {#release-19-2-4-build-9082}

_23 december 2020_

>[!CAUTION]
>
> * Deze versie wordt geleverd met een nieuw verbindingsprotocol: als u verbinding maakt met Campaign via de Adobe Identity Service (IMS), is een upgrade verplicht voor zowel de Campaign-server als de clientconsole om na **31 maart 2021** verbinding te kunnen maken met Campaign.
   >
   > 
* Deze release wordt geleverd met een [oplossing voor een beveiligingsprobleem](https://helpx.adobe.com/nl/security/products/campaign/apsb21-04.html): een upgrade is verplicht om de beveiliging van uw IT-omgeving te versterken.



* Het verbindingsprotocol is bijgewerkt en aangepast aan het nieuwe IMS-verificatiemechanisme.
* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-27777)

## ![](assets/do-not-localize/red_2.png) Release 19.2.3 - build 9081 {#release-19-2-3-build-9081}

_7 februari 2020_

**Verbeteringen**

* Probleem met regressie verholpen als gevolg van de implementatie van SSL-certificering, waardoor de gebruikersverbinding op de Windows-server is mislukt. (NEO-20629)
* Probleem verholpen waarbij een onjuist versietnummer werd weergegeven in het menu **Info**.

## ![](assets/do-not-localize/red_2.png) Release 19.2 - build 9080 {#release-19-2-build-9080}

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
      <li>U kunt bijhouden of een consument heeft gekozen voor de verkoop van persoonlijke gegevens. Hiervoor moet u de tabel Profielen uitbreiden en een <strong>Uitschakelen voor het veld CCPA</strong> toevoegen. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Meer informatie</a></li></td> 
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
<td> <p>Met Adobe Campaign kunt u de nieuwe interactieve <a href="https://amp.dev/about/email/">AMP for Email</a>-indeling uitproberen. Hiermee kunnen marketers AMP-componenten in berichten opnemen om de e-mailbeleving te verbeteren met rijke, dynamische en interactieve inhoud, die rechtstreeks in het bericht zelf kan worden geactiveerd.</p>
   <p>Dit vermogen wordt vrijgegeven als openbare bèta.</p>
   <p>Raadpleeg de <a href="../../delivery/using/defining-interactive-content.md">gedetailleerde documentatie</a> en de <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">videotutorial</a>voor meer informatie.</p><br /></td> 
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
<td> <p>Beveiligd SMS wordt nu ondersteund via de uitgebreide algemene SMPP-connector. Hierdoor is een gecodeerde verbinding met de provider mogelijk.</p> <p><strong></strong> WaarschuwingDeze functie vereist een bijgewerkt certificaat op alle servers. Ongeldige, ingetrokken of verlopen certificaten genereren fouten die de algemene mogelijkheden voor het verzenden van SMS beïnvloeden.</p><p>Raadpleeg de <a href="https://helpx.adobe.com/nl/campaign/kb/sms-connector-protocol-and-settings.html">gedetailleerde documentatie</a> voor meer informatie. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* Oplossing voor kwetsbaarheden met betrekking tot scripts die verwijzen naar andere sites in de Campagne-interface: validatie van invoergegevens en codering van uitvoer. (NEO-16810)
* Oplossing voor een beveiligingsprobleem met profielautorisatie dat toegang tot onbevoegde gegevens mogelijk maakt door het beleid voor aanmeldingsbeperkingen te versterken. (NEO-14445)

**Verbeteringen**

* Geheugenverbruik optimaliseren voor pushmeldingen.
* Voor optimalisatie van prestaties en opslag is de verwerking van het bestand **logins.log** verbeterd. Het bestand wordt nu in meerdere bestanden gesplitst, elke dag met maximaal 365 bestanden. [Meer informatie](../../production/using/log-files.md)
* De externe rekening van CRM van de Dynamica van Microsoft kan nu worden gevormd gebruikend wachtwoordgeloofsbrieven (wachtwoord + gebruikersbenaming) of certificaat (privé sleutel). [Meer informatie](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Er zijn enkele verbeteringen toegevoegd aan de Hadoop FDA-aansluiting om de betrouwbaarheid te verbeteren
* Er is een specifieke hulplijn toegevoegd om schijfruimte te controleren voordat u openbare bronnen op de server kunt uploaden.
* Nieuwe [Campagneopties](../../installation/using/configuring-campaign-options.md) zijn toegevoegd:
   * Met de configuratieoptie **WdbcKillSessionPolicy** kunt u het gedrag **Onvoorwaardelijk Stoppen** op alle workflows en PostSQL-databasequery&#39;s beïnvloeden.
   * Met de optie **NmsOperation_DeliveryPreparationWindow** kunt u het aantal dagen definiëren waarboven leveringen met een inconsistente status worden uitgesloten van het aantal actieve leveringen.
   * Met de optie **WdbcOptions_TempDbName** kunt u een aparte database configureren voor het werken van tabellen op Microsoft SQL Server. Hierdoor worden back-ups en replicatie geoptimaliseerd. [Meer informatie](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * De optie **XtkCleanup_NoStats** is verbeterd voor PostgreSQL om het gedrag van de stap van de opslagoptimalisering van het gegevensbestand schoonmaakwerkschema beter te controleren. [Meer informatie](../../production/using/database-cleanup-workflow.md#statistics-update)
* Er is een afsluitmechanisme voor de account toegevoegd aan de **aanmeldingsnaam()**-API. Het verhindert verdere login pogingen na een bepaald aantal opeenvolgende ontbroken login pogingen binnen een gespecificeerd tijdsbestek.
* Met een nieuwe optie **Maximale verpersoonlijkingsruntime** in de leveringseigenschappen kunt u een time-outperiode voor de verpersoonlijkingsruntime definiëren om te voorkomen dat de verpersoonlijkingsfase te lang doorloopt. [Meer informatie](../../delivery/using/personalization-fields.md#timing-out-personalization)
* De optie **ftp protocol** is toegevoegd om u toe te staan om een volmachtsconfiguratie voor verbindingen te gebruiken SFTP. [Meer informatie](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Nieuwe ondersteuning van proxytoegang tot een externe SFTP-server voor on-premise omgevingen.
* Er is een specifieke hulplijn toegevoegd om te voorkomen dat pakketten worden geïnstalleerd die niet compatibel zijn met de instantie Campagne. [Meer informatie](../../installation/using/installing-campaign-standard-packages.md)

_Verouderde systemen_

De volgende systemen zijn nu [afgekeurd](https://helpx.adobe.com/nl/campaign/kb/deprecated-and-removed-features.html) voor Campaign Classic-implementaties:
* Apache 2.2
* Centos 6

Zorg ervoor dat u beschikt over ondersteunde versies van alle systemen die in de nieuwste matrix voor campagnecompatibiliteit worden vermeld. [Meer informatie](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html)

_Campagne Mobile SDK_

De build 1.0.26 van de iOS SDK is nu beschikbaar. In deze nieuwe build hebben we de ondersteuning van iOS 13 toegevoegd. Deze nieuwe versie ondersteunt nu meldingsprioriteit en het nieuwe beheerproces voor registratietoken voor iOS 13-pushberichten. Als u toepassingen uitvoert op een eerdere versie van de SDK, moet u de toepassingen opnieuw compileren met de nieuwe SDK. Neem contact op met [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om de SDK op te halen.

**Patches**

* Probleem verholpen waarbij het programma vastloopt als het veld **Gekoppelde tabel toevoegen** leeg was in de werkstroomactiviteit **Gegevens laden (RDBMS)**. (NEO-12213)
* Probleem verholpen dat ertoe kon leiden dat bepaalde berichten niet werden verwerkt door de server voor middeluitgaven. (NEO-12395)
* Probleem verholpen in de workflow voor het opschonen van databases bij gebruik van de optie voor het weergeven van query&#39;s met Teradata. (NEO-12399)
* Probleem opgelost dat invloed had op de leveringsanalyse met typologieregel, waaronder ne.jp domain. (NEO-12609)
* Probleem verholpen met betrekking tot SMS over TLS-updates die een restrictiever certificaatbeleid impliceerden. Deze updates kunnen leiden tot een verbindingsfout tussen marketing- en midsourcingservers in het geval van een verouderd certificaat. (NEO-17698)
* Probleem verholpen bij het gebruik van de knop **Verbinding testen** op een externe account in een omgeving voor midsourcing met Vault-verificatie. (NEO-12722)
* Probleem verholpen bij query&#39;s waarbij gebruik werd gemaakt van datumfuncties met een FDA Hadoop-verbinding. (NEO-12847)
* Probleem verholpen bij het vervangen van een afbeelding in de e-maileditor. (NEO-13098)
* Probleem verholpen waarbij na de upgrade fouten konden optreden in mappen die waren verwijderd of verplaatst naar een andere locatie. (NEO-13118)
* Probleem verholpen met de optie **Afbeelding per schermgrootte van apparaat definiëren** bij LIJNEN-berichten. (NEO-13228)
* Probleem met voorbereiding van levering verholpen wanneer de optie **Dubbel adres uitsluiten tijdens levering** niet is geselecteerd. (NEO-13240)
* Probleem verholpen in workflows wanneer de activiteit **Bestandsoverdracht** wordt gebruikt om bestanden te downloaden met de optie **Bronbestanden verwijderen na overdracht**, met naam die een spatieteken bevat. (NEO-13411)
* Probleem verholpen waarbij Tomcat-cache werd opgeschoond en dit tot geheugenproblemen kon leiden. (NEO-13456)
* Probleem verholpen bij het installeren van de **Besturing van de aanbiedingsmotor met uitvoeringsinstantie** ingebouwde pakket op een bestaande besturingsinstantie die in Microsoft SQL 2017 wordt uitgevoerd. (NEO-13539)
* Oplossing voor een probleem met een crash van de console dat zich zou kunnen voordoen wanneer bijgehouden URL&#39;s in een e-mail werden uitgeschakeld, op het tabblad **Tekstinhoud** vanwege een niet-geïnitialiseerde variabele. (NEO-13545)
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
* Probleem verholpen dat invloed had op willekeurige sampling in **Split**-workflowactiviteit met Hadoop FDA-database. (NEO-16636)
* Oplossing voor een regressie op Oracle waarbij sommige functies na de upgrade als ongeldig werden beschouwd. (NEO-12759)


