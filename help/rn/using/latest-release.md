---
title: Laatste versie
description: Laatste versie
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


# Laatste versie{#latest-release}

[Upgrade](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) maken| [Door het bedieningspaneel afgegeven](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) gegevens| [Bijwerken](../../rn/using/documentation-updates.md) documentatie| [Eerdere introducties](../../rn/using/release--19-2.md) | [Afgekeurde kenmerken](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

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

## ![](assets/blue_2.png) Versie 20.1 - Bouwstijl 9122 {#release-20-1-build-9122}

_17 februari 2020_

**Wat is nieuw?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Snowflake FDA-connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake is een volledig beheerd cloud-gegevenspakhuis dat is gebouwd om geschaald uit te breiden op zowel opslagniveau als computerniveau. Met deze nieuwe schakelaar, kan de Campagne van Adobe hefboomwerking de macht van Snowflake nu om de Grote Segmentatie van Gegevens uit te voeren. Deze schakelaar is beschikbaar aan alle klanten, met inbegrip van die door Adobe worden ontvangen.</p>
    <p>Voor meer informatie, verwijs naar de <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">gedetailleerde documentatie</a> en de <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">zelfstudie video</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Verbeteringen van de Hadoop FDA-connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>De Hadoop FDA-connector is verbeterd om zowel Hadoop 3.0 als Cloudera te ondersteunen.</p>
    <p>Voor meer informatie, verwijs naar de <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">gedetailleerde documentatie</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Beveiligingsverbeteringen**

* Verbeterde veiligheid in rapportconfiguratie om tegen klikjacking te beschermen. Dit geldt voor nieuwe verslagen. Voor oude rapporten, moet u hen opnieuw publiceren om veranderingen toe te passen. (NEO-13282)

* Bevestig een kleine geheugenkwestie in cryptString. (NEO-20071)

* Verbeterde monitorJSP om een interne IP openbaarmaking te bevestigen. (NEO-16821)

* Vast een kwestie waar de informatie van het stapelspoor aan niet admingebruikers kon worden getoond. (NEO-12388)

* Verbeterde het beheer van caching gegevens van vorige zittingen. (NEO-17039)

* Vaste een kwestie die logins.log dossier verhinderde succesvolle login pogingen door IMS te registreren. (NEO-11004)

**Verbeteringen**

* iOS 13 wordt nu gesteund met de schakelaar van HTTP2.

* Verbeterd quarantainebeheer en opruiming van de lijsten die door de functie van het push-bericht worden gebruikt (nms:adres en nms:appSubscriptionRcp). Voor iOS (de schakelaar van HTTP2 slechts), worden de gehandicapte tekenen nu behandeld op de zelfde manier zoals voor Android. Maak vlag onbruikbaar is nu geplaatst in de lijst NmsAppSubscriptionRcp. [Meer informatie](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Een nieuwe optie is toegevoegd in de code **** JavaScript en de activiteiten van het de codewerkschema van **Geavanceerde JavaScript** om een onderbrekingsperiode te bepalen. Dit verhindert de uitvoeringsfase javascript te lang te lopen. Als de time-out periode verstrijkt, wordt de workflow gestopt. De standaardonderbreking is 1 uur. [Meer informatie](../../workflow/using/sql-code-and-javascript-code.md)

* De leveringsanalyse wordt nu tegengehouden wanneer geen passende affiniteit op de midsourcing server wordt gevonden, met de overeenkomstige foutenmelding die wordt getoond.

* Database-failover voor Postgres wordt nu ondersteund: wanneer de gegevensbestandserver neerstortt en opnieuw begint, verbindt de Campagne nu automatisch opnieuw met het.

* De **Begin Hangende** mening is toegevoegd aan de knoop van de Status van het Beleid > van de Controle > van de Werkschema&#39;s. Dit staat u toe om alle werkschema&#39;s op uw instantie te controleren die wachten om door het **operationMgt** proces worden begonnen. Deze mening komt met het pakket van de campagnes van de Marketing. [Meer informatie](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Overige mutaties**

* Voor Linux, gebruikt het opstarten van de nlserver dienst nu een systeemeenheid in plaats van het /etc/init.d/nlserver6 manuscript. De migratie naar de nieuwe startregeling wordt automatisch uitgevoerd wanneer u het 20.1 pakket installeert. /etc/init.d/nlserver6 wordt nog verstrekt maar voor het in wisselwerking staan met de nlserver dienst (begin, nieuw begin, einde, enz.), adviseren wij dat u het systeembevel direct gebruikt.

* De meest verbruikende douanetabellen zijn bewogen van de opeenvolging **xtkNewId** aan specifieke opeenvolgingen. [Meer informatie](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Verbeterde vraagprestaties die door onnodige gegevensbestandverbindingen zouden kunnen worden beïnvloed.

* Verbeterde de prestaties van de tovenaar van de gegevensbestandupdate.

* Het beheer van het gegevensbestandverslag werd verbeterd.

* De robuustheid van de verbindingspool is verbeterd, die onverwachte verbindingsmislukkingen kan verhinderen te vaak te gebeuren.

* De regels van de e-mailadrestatie om een adres naar quarantaine te verzenden in het geval van een zachte fout zijn verbeterd. [Meer informatie](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Voor Debian, gebruikt de Campagne nu systeemPCRE bibliotheken wanneer zij beschikbaar zijn.

* De campagne staat nu het gebruik van een recentere bibliotheek van systeemODBC toe.

* Een onderbreking is toegevoegd aan de server van de LIJN wanneer het openen van een verbinding om een rijk beeld te laden. Als het beeld te veel tijd vergt te laden, houdt servlet de verbinding tegen om een knelpunt te vermijden.

**Patches**

* Vast een kwestie van de rekeningssleutel van de rekening wanneer het gebruiken van de schakelaar van Hadoop.

* Vast een regressiekwestie toe te schrijven aan de implementatie van SSL certificatie die de gebruikersverbinding om op de server van Vensters veroorzaakte te ontbreken. (NEO-20629)

* Vaste een kwestie met de stijgende vraagactiviteit in het geval van negatieve werkschema IDs. (NEO-19779)

* Vast een het coderen kwestie wanneer het runnen van vragen via de schakelaar van Netezza FDA. (NEO-19594)

* Vaste een kwestie die tot een fout leidde toen het gebruiken van de POST methode in de het werkschemagebeurtenisactiviteit van de Download van het **Web** .

* Vaste een kwestie met de generatie van het voorstel. (NEO-18176)

* Vast een kwestie van de footer vertoning wanneer het gebruiken van het malplaatje van de de vormvorm van het verwervingsWeb.

* Vaste een kwestie wanneer het ontleden van URLs in de inhoud van ononderbroken leveringen die hen konden veroorzaken om te botsen. (NEO-16910)

* Vast een kwestie met de gebieden van het **Begin** en van het **Eind** die niet worden gegevens verwerkt wanneer het creëren van een nieuwe campagne.

* Vaste een kwestie met het werkschemaactiviteit van de Download van het **Dossier** wanneer het gebruiken van een URL.

* Vast een kwestie wanneer het previewing van een ingevoerde lijst in een vraagactiviteit van een rapport. (NEO-13119)

* Vaste een kwestie die een verouderd beeld toen het selecteren van het **Powered by Campaign** verpersoonlijkingsblok in de e-mailredacteur toonde.

* De netwerkcommunicatie tussen de cliënt en de server is verbeterd.

* Vast een kwestie wanneer teveel werkschema&#39;s in de zelfde campagne worden gecreeerd. Nu, kunt u niet meer dan 28 werkschema&#39;s tot stand brengen. Er wordt een waarschuwing weergegeven.

* Vaste een kwestie wanneer het gebruiken van de **A selectie van kolommen** verzoeningsoptie in een **Uniewerkschemaactiviteit** .

* Vaste een kwestie van de consoleneerstorting die kon voorkomen wanneer het gebruiken van een bedorven verrijkingslijst in een werkschema. (NEO-18096)

* Vaste diverse kwesties van de consoleneerstorting die in werkschema&#39;s konden voorkomen (NEO-18010, NEO-18032)

* Vaste een kwestie die de uitvoering van een **Externe activiteit van het signaalwerkschema** toeliet zelfs toen het onbruikbaar werd gemaakt. (NEO-17524)

* Vaste een kwestie wanneer het creëren van een nieuw schema.

* Vast een volgende kwestie wanneer het verzenden van de berichten van SMS. (NEO-19595)

* Vaste een kwestie die onjuist gericht publieksaantal in leveringsindicatoren toonde.

* Vaste een kwestie die onjuiste percentages toen het produceren van een beschrijvend rapport via een werkschemaactiviteit toonde. (NEO-14314)

* Vast een kwestie die het rapport van de leveringsproductie maakte toont verschillende aantallen wanneer de parameter van de tijdmening. (NEO-11783)

* Vaste een kwestie die de transactionele berichten het volgen indicatoren verhinderde door het Volgende werkschema worden bijgewerkt. (NEO-17770)

* Vaste een regressiekwestie die het Webproces om veroorzaakte te botsen en opnieuw te beginnen wanneer het verzoeken van om een aanbieding door ZEEP. (NEO-19482)

* Vaste een kwestie die verhinderde gegevens aan openbare middelen te uploaden als uploadde folder een verre gedeelde plaats was. (NEO-19361)

* Vaste een kwestie die het **publiek van de Invoer van de Technische werkschema tp van de Wolk** van de Ervaring van Adobe constant veroorzaakte ontbreken. (NEO-18463)

* Vaste een kwestie die leveringen verhinderde worden verzonden wanneer het gebruiken van malplaatjes die van de Manager van de Ervaring worden ingevoerd. (NEO-17540)

* Vaste een kwestie die na bevordering voorkwam om 9032 te bouwen en de instantie te verhinderen met de server van FTP over SSL protocol te verbinden. (NEO-20498)

* Vaste een kwestie die voorkwam toen het schrappen van, het opnemen van of het bijwerken van een grote hoeveelheid gegevens met de de gegevensactiviteit van de **Update** in een werkschema gebruikend een schema FDA als het richten dimensie. (NEO-13280)

* Vast een kwestie aan die e-mails verhinderde worden verzonden wanneer het gebruiken van de &quot;als&quot;verklaring buiten de `body` markering.

* Vaste een kwestie die voorkwam toen het proberen om de spiegelpagina van de leveringslogboeken van een verzonden bericht te tonen. (NEO-17976)

* Vaste een kwestie die de **Verbinding aan het verpersoonlijkingsblok van de spiegelpagina** verhinderde in het de inhoudslusje van de **Tekst** na het klikken van HTML **van de** Invoer in een levering wordt getoond. (NEO-17568)

* De foutenmelding die wanneer het klikken van een verbinding aan een spiegelpagina wordt getoond die is verlopen duidelijk. (NEO-17340)

* Vaste een kwestie die sommige knopen in het de verwezenlijkingsscherm van de distributie **van** Gegevens verhinderde worden gebruikt.

* Vaste een kwestie die toen het plannen van een leveringsactiviteit in een geval met Azië/Kolkata als tijdzone voorkwam. (NEO-2001)

* Een fout wordt nu getoond wanneer een levering een kwestie van de affiniteitsconfiguratie heeft.

* Vaste een kwestie die een onjuist aantal van de versiemarkering in het **ongeveer** menu toonde.

* Vaste een kwestie die voorkwam toen het proberen om de verpletterende rekening van de eigenschappen van een terugkomende levering in een werkschema bij te werken. (NEO-18684)

* Vaste een kwestie die toen het verbinden met de instantie door de omleidingsmodule voorkwam, die de verbinding verhinderde behoorlijk te worden schoongemaakt zodra gesloten.
