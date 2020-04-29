---
title: Laatste release
description: Laatste release
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


# Laatste release{#latest-release}

[Upgrade](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) maken| [Release](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) van het regelpaneel| [Documentatie-updates](../../rn/using/documentation-updates.md) | [Eerdere versies](../../rn/using/release--19-2.md) | [Verouderde kenmerken](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

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

## ![](assets/do-not-localize/blue_2.png) Release 20.1.2 - build 9123 {#release-20-1-2-build-9123}

_13 maart 2020_

* Probleem verholpen waarbij implementatie van versies op Red Hat 7-servers werd voorkomen. (NEO-2332)

## ![](assets/do-not-localize/orange_2.png) Release 20.1 - build 9122 {#release-20-1-build-9122}

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
   <td> <p>Sneeuwvlok is een volledig beheerd wolkendepot dat is gebouwd om op zowel opslag als compute niveau te schrapen. Met deze nieuwe aansluiting kan Adobe Campaign nu de kracht van Snowflake benutten om Big Data Segmentation uit te voeren. Deze connector is beschikbaar voor alle klanten, ook voor klanten die worden gehost door Adobe.</p>
    <p>Raadpleeg voor meer informatie de <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">gedetailleerde documentatie</a> en <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">zelfstudievideo</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Verbeteringen voor Hadoop FDA-aansluiting</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>De Hadoop FDA Connector is verbeterd om zowel Hadoop 3.0 als Cloudera te ondersteunen.</p>
    <p>Raadpleeg de <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">gedetailleerde documentatie</a>voor meer informatie.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* Verbeterde veiligheid in rapportconfiguratie om tegen klikjacking te beschermen. Dit geldt voor nieuwe verslagen. Voor oude rapporten moet u deze opnieuw publiceren om wijzigingen toe te passen. (NEO-13282)

* Los een klein geheugenprobleem in cryptString op. (NEO-20071)

* Verbeterde controle JSP om een interne IP bekendmaking te bevestigen. (NEO-16821)

* Probleem verholpen waarbij gegevens over stacktracering konden worden weergegeven aan gebruikers die geen beheerder zijn. (NEO-12388)

* Verbeterd beheer van gegevens uit vorige sessies in cache. (NEO-17039)

* Probleem verholpen waardoor het bestand logins.log geen succesvolle aanmeldingspogingen kon opnemen via IMS. (NEO-11004)

**Verbeteringen**

* iOS 13 wordt nu ondersteund door de HTTP2-connector.

* Verbeterd quarantainebeheer en opschoning van de tabellen die worden gebruikt door de functie voor pushmeldingen (nms:address en nms:appSubscriptionRcp). Voor iOS (alleen HTTP2-connector) worden uitgeschakelde tokens nu op dezelfde manier verwerkt als voor Android. De markering voor uitschakelen is nu ingesteld in de tabel NmsAppSubscriptionRcp. [Meer informatie](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Er is een nieuwe optie toegevoegd aan de **JavaScript-code** en de activiteiten in de workflow voor **geavanceerde JavaScript-code** om een time-outperiode te definiëren. Hierdoor wordt voorkomen dat de uitvoeringsfase van javascript te lang wordt uitgevoerd. Als de time-outperiode verstreken is, wordt de workflow gestopt. De standaardtime-out is 1 uur. [Meer informatie](../../workflow/using/sql-code-and-javascript-code.md)

* De leveringsanalyse wordt nu gestopt wanneer geen passende affiniteit op de midsourcingserver wordt gevonden, met het overeenkomstige foutenmelding die wordt getoond.

* Database-failover voor Postgres wordt nu ondersteund: Wanneer de databaseserver vastloopt en opnieuw wordt opgestart, maakt Campagne nu automatisch opnieuw verbinding met de server.

* De **weergave In afwachting** van starten is toegevoegd aan het knooppunt Beheer > Audit > Workflows Status. Dit staat u toe om alle werkschema&#39;s op uw instantie te controleren die om door het **operationMgt** proces wachten te zijn begonnen. Deze weergave wordt geleverd met het marketingpakket. [Meer informatie](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Overige wijzigingen**

* In Linux gebruikt het opstarten van de netwerkservice nu een systeemeenheid in plaats van het script /etc/init.d/nlserver6. De migratie naar het nieuwe opstartschema wordt automatisch uitgevoerd wanneer u het 20.1-pakket installeert. /etc/init.d/nlserver6 wordt nog verstrekt maar voor het in wisselwerking staan met de nlserver dienst (begin, nieuw begin, einde, enz.), adviseren wij dat u het systeembevel direct gebruikt.

* De meest verbruikende douanetabellen zijn bewogen van de **xtkNewId** opeenvolging aan specifieke opeenvolgingen. [Meer informatie](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Verbeterde queryprestaties die kunnen worden beïnvloed door onnodige databaseverbindingen.

* Verbeterde prestaties van de wizard Database bijwerken.

* Het beheer van de databaserecord is verbeterd.

* De robuustheid van de verbindingspool is verbeterd, die onverwachte verbindingsmislukkingen kan verhinderen te vaak te gebeuren.

* De regels voor de validatie van e-mailadressen voor het verzenden van een adres naar quarantaine in het geval van een elektronische fout zijn verbeterd. [Meer informatie](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Voor Debian gebruikt Campaign nu PCRE-bibliotheken van het systeem wanneer deze beschikbaar zijn.

* De campagne staat nu het gebruik van een recentere systeemODBC bibliotheek toe.

* Er is een time-out toegevoegd aan het LINE-servlet wanneer een verbinding wordt geopend om een rijke afbeelding te laden. Als het laden van de afbeelding te veel tijd in beslag neemt, stopt de servlet de verbinding om een knelpunt te voorkomen.

**Patches**

* Probleem verholpen met versleuteling van accountsleutels bij gebruik van de Hadoop-connector.

* Probleem met regressie verholpen als gevolg van de implementatie van SSL-certificering, waardoor de gebruikersverbinding op de Windows-server is mislukt. (NEO-20629)

* Probleem verholpen met incrementele queryactiviteit in het geval van negatieve workflow-id&#39;s. (NEO-1979)

* Probleem met codering verholpen bij het uitvoeren van query&#39;s via de Netezza FDA-connector. (NEO-19594)

* Probleem verholpen dat tot een fout leidde bij het gebruik van de POST-methode in de gebeurtenisactiviteit van de **webdownloadworkflow** .

* Probleem opgelost met het genereren van voorstellen. (NEO-18176)

* Probleem met weergave van voettekst verholpen bij gebruik van de sjabloon voor het verkrijgen van een webformulier.

* Probleem verholpen bij het parseren van de URL&#39;s in de inhoud van doorlopende leveringen die ertoe konden leiden dat ze vastliepen. (NEO-16910)

* Probleem verholpen waarbij de velden **Start** en **End** niet werden berekend tijdens het maken van een nieuwe campagne.

* Probleem verholpen met de workflowactiviteit **Bestanden downloaden** bij gebruik van een URL.

* Probleem verholpen bij het voorvertonen van een geïmporteerde lijst in een queryactiviteit van een rapport. (NEO-13119)

* Probleem verholpen waarbij een verouderde afbeelding werd weergegeven wanneer u in de e-maileditor het aanpassingsblok **Powered by Campaign** (Aangedreven door campagne) selecteerde.

* De netwerkcommunicatie tussen de client en de server is verbeterd.

* Probleem verholpen waarbij te veel workflows in dezelfde campagne werden gemaakt. U kunt nu niet meer dan 28 workflows maken. Er wordt een waarschuwing weergegeven.

* Probleem verholpen bij gebruik van de optie **A voor het afstemmen van kolommen** in een **Uniewerkstroomactiviteit** .

* Probleem verholpen waarbij de console vastloopt die kan optreden wanneer een beschadigde verrijkingslijst in een workflow wordt gebruikt. (NEO-18096)

* Oplossing voor diverse problemen met het vastlopen van de console die in workflows konden optreden (NEO-18010, NEO-18032)

* Probleem verholpen waarbij een workflowactiviteit voor een **extern signaal** ook kon worden uitgevoerd als deze was uitgeschakeld. (NEO-17524)

* Probleem verholpen bij het maken van een nieuw schema.

* Probleem met bijhouden bij het verzenden van SMS-berichten is opgelost. (NEO-19595)

* Probleem verholpen waarbij een onjuist doelaantal werd weergegeven in leveringsindicatoren.

* Probleem verholpen waarbij onjuiste percentages werden weergegeven bij het genereren van een beschrijvend rapport via een workflowactiviteit. (NEO-14314)

* Probleem verholpen waarbij verschillende nummers werden weergegeven in het rapport met de leveringstijd. (NEO-11783)

* Probleem verholpen waardoor de trackingindicatoren voor transactionele berichten niet konden worden bijgewerkt in de workflow voor bijhouden. (NEO-1770)

* Oplossing voor een regressieprobleem dat ertoe leidde dat het webproces vastliep en opnieuw opstartte bij het aanvragen van een aanbieding via SOAP. (NEO-19482)

* Probleem verholpen waarbij gegevens niet konden worden geüpload naar openbare bronnen als de uploadmap een externe gedeelde locatie was. (NEO-19361)

* Probleem opgelost waarbij het publiek voor **importeren uit de technische workflow van Adobe Experience Cloud** voortdurend faalde. (NEO-18463)

* Probleem verholpen waarbij leveringen niet konden worden verzonden wanneer sjablonen werden gebruikt die vanuit Experience Manager waren geïmporteerd. (NEO-17540)

* Probleem verholpen dat optrad na de upgrade naar versie 9032 en waardoor de instantie geen verbinding kon maken met de FTP-server via het SSL-protocol. (NEO-20498)

* Oplossing van een probleem dat optrad bij het verwijderen, invoegen of bijwerken van een grote hoeveelheid gegevens met de **activiteit Gegevens** bijwerken in een workflow met een FDA-schema als doeldimensie. (NEO-13280)

* Probleem verholpen waarbij e-mailberichten niet konden worden verzonden wanneer de instructie &#39;if&#39; buiten de `body` tag werd gebruikt.

* Probleem verholpen die optrad tijdens het weergeven van de spiegelpagina vanuit de leveringslogboeken van een verzonden bericht. (NEO-17976)

* Probleem verholpen waardoor de **koppeling naar het aanpassingsblok van de spiegel** niet kon worden weergegeven op het tabblad **Tekstinhoud** nadat op HTML **in een levering** importeren was geklikt. (NEO-17568)

* Het foutbericht dat wordt weergegeven wanneer u op een koppeling naar een verlopen spiegelpagina klikt, is verduidelijkt. (NEO-17340)

* Probleem verholpen waardoor sommige knoppen niet konden worden gebruikt in het scherm voor het maken van **gegevensdistributie** .

* Probleem verholpen dat optrad bij het plannen van een leveringsactiviteit in een instantie met Asia/Kolkata als tijdzone. (NEO-2001)

* Er wordt nu een fout weergegeven wanneer een levering een probleem met de affiniteitsconfiguratie heeft.

* Probleem verholpen waarbij een onjuist versietnummer in het menu **Info** werd weergegeven.

* Probleem verholpen die optrad tijdens het bijwerken van de verpletterende account vanuit de eigenschappen van een terugkerende levering in een workflow. (NEO-18684)

* Probleem verholpen dat optrad wanneer verbinding werd gemaakt met de instantie via de omleidingsmodule, waardoor de verbinding niet goed kon worden schoongemaakt zodra deze was gesloten.
