---
solution: Campaign Classic
product: campaign
title: Release 20.1
description: Release 20.1
audience: rns
content-type: reference
topic-tags: campaign-release-notes, latest-release-notes
translation-type: tm+mt
source-git-commit: b5b9e42eca25193cf4d69f654e74a02afd8adca9
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 12%

---


# Release 20.1{#release-20-1}

## ![](assets/do-not-localize/limited_2.png) Release 20.1.4 - build 9126 {#release-20-1-4-build-9126}

_23 december 2020_

>[!CAUTION]
>
> * Deze versie wordt geleverd met een nieuw verbindingsprotocol: als u verbinding maakt met Campaign via de Adobe Identity Service (IMS), is een upgrade verplicht voor zowel de Campaign-server als de clientconsole om na **31 maart 2021** verbinding te kunnen maken met Campaign.
   >
   > 
* Deze release wordt geleverd met een [oplossing voor een beveiligingsprobleem](https://helpx.adobe.com/nl/security/products/campaign/apsb21-04.html): een upgrade is verplicht om de beveiliging van uw IT-omgeving te versterken.


* Het verbindingsprotocol is bijgewerkt en aangepast aan het nieuwe IMS-verificatiemechanisme.
* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-27777)

## ![](assets/do-not-localize/red_2.png) Release 20.1.3 - build 9124{#release-20-1-3-build-9124}

_6 mei 2020_

* Probleem verholpen met de activiteit **Bestand overdragen** waardoor verificatie op basis van SFTP-sleutels niet kon werken op Debian 9. (NEO-23183)

## ![](assets/do-not-localize/red_2.png) Release 20.1.2 - build 9123{#release-20-1-2-build-9123}

_13 maart 2020_

* Probleem verholpen waarbij implementatie van versies op Red Hat 7-servers werd voorkomen. (NEO-23332)

## ![](assets/do-not-localize/red_2.png) Release 20.1 - build 9122{#release-20-1-build-9122}

_17 februari 2020_

**Nieuwe functies**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Snowflake FDA-connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake is een volledig beheerde opslagplaats voor cloudgegevens die op zowel opslagniveau als computerniveau is gebouwd. Met deze nieuwe aansluiting kan Adobe Campaign nu gebruikmaken van de kracht van Snowflake om Big Data Segmentation uit te voeren. Deze schakelaar is beschikbaar aan alle klanten, met inbegrip van die door Adobe worden ontvangen.</p>
    <p>Raadpleeg voor meer informatie de <a href="../../installation/using/configure-fda-snowflake.md">gedetailleerde documentatie</a> en <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">zelfstudievideo</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Verbeteringen voor hadoop FDA-aansluiting</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>De Hadoop FDA Connector is verbeterd om zowel Hadoop 3.0 als Cloudera te ondersteunen.</p>
    <p>Raadpleeg de <a href="../../installation/using/configure-fda-hadoop.md">gedetailleerde documentatie</a> voor meer informatie.</p>
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

* Er is een nieuwe optie toegevoegd aan de workflowactiviteiten **JavaScript code** en **Geavanceerde JavaScript-code** om een time-outperiode te definiëren. Hierdoor wordt voorkomen dat de uitvoeringsfase van javascript te lang wordt uitgevoerd. Als de time-outperiode verstreken is, wordt de workflow gestopt. De standaardtime-out is 1 uur. [Meer informatie](../../workflow/using/sql-code-and-javascript-code.md)

* De leveringsanalyse wordt nu gestopt wanneer geen passende affiniteit op de midsourcingserver wordt gevonden, met het overeenkomstige foutenmelding die wordt getoond.

* Database-failover voor Postgres wordt nu ondersteund: Wanneer de databaseserver vastloopt en opnieuw wordt opgestart, maakt Campagne nu automatisch opnieuw verbinding met de server.

* De weergave **In behandeling starten** is toegevoegd aan het knooppunt Beheer > Audit > Workflows Status. Dit staat u toe om alle werkschema&#39;s op uw instantie te controleren die om door het **operationMgt** proces wachten te zijn begonnen. Deze weergave wordt geleverd met het marketingpakket. [Meer informatie](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Overige wijzigingen**

* In Linux gebruikt het opstarten van de netwerkservice nu een systeemeenheid in plaats van het script /etc/init.d/nlserver6. De migratie naar het nieuwe opstartschema wordt automatisch uitgevoerd wanneer u het 20.1-pakket installeert. /etc/init.d/nlserver6 wordt nog verstrekt maar voor het in wisselwerking staan met de nlserver dienst (begin, nieuw begin, einde, enz.), adviseren wij dat u het systeembevel direct gebruikt.

* De meest verbruikende douanetabellen zijn bewogen van **xtkNewId** opeenvolging aan specifieke opeenvolgingen. [Meer informatie](https://helpx.adobe.com/nl/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Verbeterde queryprestaties die kunnen worden beïnvloed door onnodige databaseverbindingen.

* Verbeterde prestaties van de wizard Database bijwerken om minder SQL-instructies te maken en zo de responstijd te optimaliseren.

* Het beheer van de databaserecord is verbeterd.

* De robuustheid van de verbindingspool is verbeterd, die onverwachte verbindingsmislukkingen kan verhinderen te vaak te gebeuren.

* De regels voor de validatie van e-mailadressen voor het verzenden van een adres naar quarantaine in het geval van een elektronische fout zijn verbeterd. [Meer informatie](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Voor Debian gebruikt Campaign nu PCRE-bibliotheken van het systeem wanneer deze beschikbaar zijn.

* De campagne staat nu het gebruik van een recentere systeemODBC bibliotheek toe.

* Er is een time-out toegevoegd aan het LINE-servlet wanneer een verbinding wordt geopend om een rijke afbeelding te laden. Als het laden van de afbeelding te veel tijd in beslag neemt, stopt de servlet de verbinding om een knelpunt te voorkomen.

**Patches**

* Probleem verholpen met versleuteling van accountsleutels bij gebruik van de Hadoop-connector.

* Probleem met regressie verholpen als gevolg van de implementatie van SSL-certificering, waardoor de gebruikersverbinding op de Windows-server is mislukt. (NEO-20629)

* Probleem verholpen met incrementele queryactiviteit in het geval van negatieve workflow-id&#39;s. (NEO-19779)

* Probleem met codering verholpen bij het uitvoeren van query&#39;s via de Netezza FDA-connector. (NEO-19594)

* Probleem verholpen dat tot een fout leidde wanneer het gebruiken van de methode van de POST in **Web Download** de activiteit van de werkschemagebeurtenis.

* Probleem opgelost met het genereren van voorstellen. (NEO-18176)

* Probleem met weergave van voettekst verholpen bij gebruik van de sjabloon voor het verkrijgen van een webformulier.

* Probleem verholpen bij het parseren van de URL&#39;s in de inhoud van doorlopende leveringen die ertoe konden leiden dat ze vastliepen. (NEO-16910)

* Probleem verholpen waarbij de velden **Start** en **End** niet werden berekend tijdens het maken van een nieuwe campagne.

* Probleem verholpen met de **activiteit van het downloaden van bestanden** bij het gebruik van een URL.

* Probleem verholpen bij het voorvertonen van een geïmporteerde lijst in een queryactiviteit van een rapport. (NEO-13119)

* Probleem verholpen waarbij een verouderde afbeelding werd weergegeven wanneer het personaliseringsblok **Powered by Campaign** in de e-maileditor werd geselecteerd.

* De netwerkcommunicatie tussen de client en de server is verbeterd.

* Probleem verholpen waarbij te veel workflows in dezelfde campagne werden gemaakt. U kunt nu niet meer dan 28 workflows maken. Er wordt een waarschuwing weergegeven.

* Probleem verholpen bij het gebruik van de **Selectie van kolommen**-afstemmingsoptie in een **Union**-werkstroomactiviteit.

* Probleem verholpen waarbij de console vastloopt die kan optreden wanneer een beschadigde verrijkingslijst in een workflow wordt gebruikt. (NEO-18096)

* Oplossing voor diverse problemen met het vastlopen van de console die in workflows konden optreden (NEO-18010, NEO-18032)

* Probleem verholpen waarbij een **Externe signaalactiviteit** kon worden uitgevoerd, zelfs als deze was uitgeschakeld. (NEO-17524)

* Probleem verholpen bij het maken van een nieuw schema.

* Probleem met bijhouden bij het verzenden van SMS-berichten is opgelost. (NEO-19595)

* Probleem verholpen waarbij een onjuist doelaantal werd weergegeven in leveringsindicatoren.

* Probleem verholpen waarbij onjuiste percentages werden weergegeven bij het genereren van een beschrijvend rapport via een workflowactiviteit. (NEO-14314)

* Probleem verholpen waarbij verschillende nummers werden weergegeven in het rapport met de leveringstijd. (NEO-11783)

* Probleem verholpen waardoor de trackingindicatoren voor transactionele berichten niet konden worden bijgewerkt in de workflow voor bijhouden. (NEO-17770)

* Oplossing voor een regressieprobleem dat ertoe leidde dat het webproces vastliep en opnieuw opstartte bij het aanvragen van een aanbieding via SOAP. (NEO-19482)

* Probleem verholpen waarbij gegevens niet konden worden geüpload naar openbare bronnen als de uploadmap een externe gedeelde locatie was. (NEO-19361)

* Probleem verholpen waarbij het **Importeerpubliek uit de technische workflow van Adobe Experience Cloud** voortdurend faalde. (NEO-18463)

* Probleem verholpen waardoor leveringen niet konden worden verzonden bij gebruik van sjablonen die uit Experience Manager zijn geïmporteerd. (NEO-17540)

* Probleem verholpen dat optrad na de upgrade naar versie 9032 en waardoor de instantie geen verbinding kon maken met de FTP-server via het SSL-protocol. (NEO-20498)

* Oplossing van een probleem dat optrad bij het verwijderen, invoegen of bijwerken van een grote hoeveelheid gegevens met de **activiteit Gegevens bijwerken** in een workflow met een FDA-schema als doeldimensie. (NEO-13280)

* Probleem verholpen waarbij e-mailberichten niet konden worden verzonden als er JavaScript-code buiten de HTML-inhoudstag stond. (NEO-18628)

* Probleem verholpen die optrad tijdens het weergeven van de spiegelpagina vanuit de leveringslogboeken van een verzonden bericht. (NEO-17976)

* Probleem verholpen waardoor het **Koppelen naar spiegel**-aanpassingsblok niet kon worden weergegeven op het tabblad **Tekstinhoud** nadat was geklikt op **HTML importeren** in een levering. (NEO-17568)

* Het foutbericht dat wordt weergegeven wanneer u op een koppeling naar een verlopen spiegelpagina klikt, is verduidelijkt. (NEO-17340)

* Probleem verholpen waardoor sommige knoppen niet konden worden gebruikt in het aanmaakscherm **Gegevensdistributie**.

* Probleem verholpen dat optrad bij het plannen van een leveringsactiviteit in een instantie met Asia/Kolkata als tijdzone. (NEO-20001)

* Er wordt nu een fout weergegeven wanneer een levering een probleem met de affiniteitsconfiguratie heeft.

* Probleem verholpen waarbij een onjuist versietnummer werd weergegeven in het menu **Info**.

* Probleem verholpen die optrad tijdens het bijwerken van de verpletterende account vanuit de eigenschappen van een terugkerende levering in een workflow. (NEO-18684)

* Probleem verholpen dat optrad wanneer verbinding werd gemaakt met de instantie via de omleidingsmodule, waardoor de verbinding niet goed kon worden schoongemaakt zodra deze was gesloten.
