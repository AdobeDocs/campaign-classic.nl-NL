---
product: campaign
title: Nieuwste release
description: De nieuwste aanvullende informatie voor Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 95c4a83037bcd2e22a03ac80d1ec4a7896a94ce3
workflow-type: tm+mt
source-wordcount: '2709'
ht-degree: 75%

---

# Nieuwste release{#latest-release}

![](../../assets/v7-only.svg)

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van Campaign Classic v7**. Elke nieuwe build heeft een status die wordt aangegeven door een kleur. Meer informatie over de build-statussen van Campaign Classic v7 vindt u op [deze pagina](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Release 7.3.2 - build 9356 {#release-7-3-2}

_21 november 2022_

**Compatibiliteitsupdates**

* Na het einde van de levensduur van Microsoft Internet Explorer 11 gebruikt de HTML-renderingengine voor dashboards in de clientconsole nu Edge Chromium. (NEO-20741)

**Verbeteringen**

* De Google BigQuery-aansluiting biedt nu volledige ondersteuning voor Booleaanse velden. (NEO-49181)
* U kunt nu de geldigheidsperiode van de IMS-cookies configureren in de `Configuration for the redirection service` van het bestand serverConf.xml. Dit geldt voor de volgende cookies: `uuid230`, `nllastdelid` en `AMCV_` (NEO-42541)
* IP kan nu in het &quot;/r/test&quot;verzoek worden verborgen door te plaatsen `showSourceIP` naar false in het knooppunt redirection van het bestand serverConf.xml. [Meer informatie](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

**Afgeschafte functies**

* Sociale marketing met Facebook is nu afgekeurd. U kunt Twitter-integratie gebruiken om sociale media te plaatsen of met Adobe te werken om een aangepast kanaal te maken.

* ACS Connector (prime-aanbieding) is nu afgekeurd. U kunt de uitvoer/de invoermogelijkheden van de Campagne gebruiken om gegevens in beide producten te halen en te injecteren.

Meer informatie vindt u op de pagina [Afgeschafte en verwijderde functies](deprecated-features.md).

**Andere wijzigingen**

* Weblogboeken zijn verbeterd: `logonEscalation` waarschuwingen worden nu alleen weergegeven voor gebruikers met beheerdersrechten. (NEO-47167)
* Om fouten te voorkomen, **Gegevens verzamelen voor Heatmap-service** (collectDataHeatMapService) workflow wordt nu standaard gestopt. (NEO-33959)
* Er zijn verschillende verbeteringen doorgevoerd om het CPU-gebruik voor het campagnesdashboard te optimaliseren. (NEO-46417)
* Om vastlopen te voorkomen, is de loadLibraryDebug JS-methode verwijderd. (NEO-46968)
* De resterende verwijzingen naar de bibliotheek log4j zijn verwijderd uit de installatie van de Campagne in Vensters. (NEO-44851)

**Patches**

* Probleem verholpen waarbij het gebruik van de **Geselecteerde lijnen samenvoegen** workflowoptie. (NEO-48488)
* Het probleem dat de **Succes** De leveringsindicator wordt correct bijgewerkt bij gebruik van Adobe Campaign Enhanced MTA. (NEO-50462)
* Probleem verholpen waarbij goedkeuring van inhoud opnieuw werd ingesteld in een e-maillevering. Hierdoor kon u het probleem niet opnieuw goedkeuren. (NEO-44259)
* Het probleem dat de **Afleveringsgoedkeuring** weergegeven. (NEO-47547)
* Oplossing voor een prestatieprobleem op het tabblad HTML van een levering dat zich zou kunnen voordoen voor code met een grote HTML. (NEO-47440)
* Oplossing voor een probleem dat invloed had op de statusupdates van het leveringslogboek voor de MID-instantie, wanneer de `FeatureFlag_GZIP_Compression` is ingeschakeld. (NEO-49183)
* Probleem verholpen waardoor u geen berichten voor mobiele apps van iOS kunt verzenden van een uitvoeringsinstantie tijdens het gebruik van tokenverificatie. (NEO-45961)
* Probleem verholpen met de **Vernieuwen voor leverbaarheid** werkstroom (DeliabilityUpdate) die vastliep toen het hebben van teveel uitzendingen aan synchronisatie. (NEO-48287)
* Probleem verholpen met het gebeurtenistype dat de **Synchronisatie van Message Center** (mcSynch) workflow.
* Probleem verholpen dat tot een fout kon leiden bij het toevoegen van de **Ontvangers die zijn geopend**  (estimatedRecipientOpen)-indicator in de aanvullende gegevens van een **Query** workflowactiviteit. (NEO-46665)
* Probleem verholpen met de **Facturering** werkstroom die mislukte toen het hebben van de pakketten van de Controle en van de Uitvoering van het Centrum van het Bericht op de zelfde instantie werd geïnstalleerd. (NEO-47674)
* Probleem verholpen met de **Facturering** workflow die mislukte wanneer tabellen met de primaire sleutel als een tekenreeks in plaats van als een geheel getal werden gedefinieerd. (NEO-46254)
* Probleem verholpen met heatmap-filters als de naam van de workflow te lang was. (NEO-46301)
* Probleem opgelost dat in 7.3.1 op de Snowflake FDA-aansluiting werd geïntroduceerd en dat ertoe leidde dat records werden weggelaten wanneer tijdens het verrijken &quot;0 of 1 cardinaliteit simple join&quot; werd gebruikt. (NEO-48737)
* Probleem verholpen met Snowflake FFDA bij gebruik van de sorteerparameter in een **Splitsen** workflowactiviteit. (NEO-45899)
* Probleem verholpen waardoor u de configuratie van externe accounts niet kunt opslaan. Het externe account wordt nu automatisch opgeslagen na de verbindingstest voor connectors met parseringsmogelijkheden (Snowflake en Google BigQuery). (NEO-47636)
* Probleem verholpen waardoor u geen datatype Tijd kon invoegen in een **Gegevensupdate** workflowactiviteit op MSSQL. (NEO-47763)
* Probleem verholpen die ertoe leidde dat het MTA-proces vastliep wanneer de tijdzone van de engine niet was ingesteld (specifiek voor MSSQL). (NEO-46619)
* Probleem verholpen met het importeren van HTML-bestanden wanneer afbeeldingsknooppunten (img) URL&#39;s bevatten met aanpassingsvelden. (NEO-48396)
* Probleem verholpen waarbij een HTTP 500-fout werd verholpen bij een poging verbinding te maken met een instantie waarbij de `limit` knooppunt niet geconfigureerd in het bestand serverConf.xml.
* Probleem verholpen waarbij een fout met een tekenset kon optreden bij het gebruik van bepaalde functies, zoals `to_nclob` met een Oracle unicode-database waarbij NChar niet is ingeschakeld. (NEO-49361)
* Probleem verholpen dat tot een fout leidde wanneer een gebruiker met leestoegangsrechten in de map nmsDeliveryMapping een campagne of workflow probeerde uit te voeren. (NEO-48230)
* Het probleem dat de `JSPContext.sqlExecWithOneParam` van het werken. (NEO-50066)
* Correctie van verschillende omleidingsfouten. (NEO-50030)

## ![](assets/do-not-localize/orange_2.png) Release 7.3.1 - build 9352 {#release-7-3-1}

_1 juli 2022_

**Nieuwe functies**

<table> 
<thead>
<tr> 
<th> <strong>Tijdgevoelige meldingen</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Met iOS 15 heeft Apple een concept van gevoelige meldingen toegevoegd dat de ontwikkelaar van de app de mogelijkheid geeft om de modus Focus te omzeilen wanneer een melding als gevoelig wordt beschouwd en de gebruiker in real time moet bereiken.</p>
<p>Leer in de <a href="../../delivery/using/create-notifications-ios.md">gedetailleerde documentatie</a> hoe u een gevoelige melding maakt.</p>
</td> 
</tr> 
</tbody> 
</table>

**Compatibiliteitsupdates**

* Adobe Campaign SDK ondersteunt nu Android 12 en iOS 15 voor pushberichten.
* Adobe Campaign is nu compatibel met MySQL 8.
* Adobe Campaign is nu compatibel met Windows 11.
* Adobe Campaign is nu compatibel met Debian 11.

Raadpleeg de [Campaign-compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Verbeteringen**

* Na afloop van de levensduur van Microsoft Internet Explorer 11 gebruikt de HTML-renderingengine voor Adobe Services (aanmeldpagina) in de console nu Edge Chromium. Merk op dat Microsoft Internet Explorer 11 nog steeds de HTML-renderingengine voor dashboards in de clientconsole is.  Bovendien is de installatie van de Microsoft Edge Webview 2-runtime nu vereist voor elke installatie van de clientconsole (van Campaign Classic 7.3 build-versie). [Meer informatie](../../installation/using/installing-the-client-console.md)
* Het beheer van de databaseverbinding in Adobe Campaign is verbeterd om de stabiliteit te optimaliseren.
* Microsoft Exchange Online OAuth 2.0-verificatie voor POP3 wordt nu ondersteund in Campaign. [Meer informatie](../../installation/using/external-accounts.md#bounce-mails-external-account)
* Er zijn verschillende problemen verholpen bij het gebruik van een verrijkingsworkflowactiviteit met externe gegevens. (NEO-38069)
* De SAP Hana FDA-connector is bijgewerkt en werkt nu met de nieuwste SAP Hana-databaseversie (2.x).
* De Teradata FDA-connector is bijgewerkt en werkt nu met de nieuwste Teradata-versie (17).
* In 20.2 werd de ondersteuning van tokengebaseerde authenticatie voor iOS-leveringen geïntroduceerd voor nieuwe leveringen en leveringssjablonen. In 7.2 is een patch toegevoegd aan de postugrade om de op token gebaseerde authenticatieondersteuning toe te passen op maximaal 10.000 eerder gemaakte leveringen en leveringssjablonen. In 7.3 is de patch verbeterd en is de limiet verwijderd.

**Patches**

* Er is een fout uit de vorige build opgelost waardoor gebruikers de IMS-aanmeldingspagina niet konden vergroten of verkleinen. (NEO-30085)
* Er is een fout opgelost die optrad bij het installeren van het contentmanagerpakket op een bestaande instantie. (NEO-32349)
* Er is een probleem opgelost in het menu **Campagnes** waarbij continu het bericht voor bewerking in uitvoering werd weergegeven. (NEO-44904)
* Er is een probleem opgelost waarbij, met Adobe Analytics ingeschakeld, BID (Broadlog-ID) en CID (Campaign ID) uit de URL werden verwijderd bij het verzenden van een e-mail met een URL zonder de levering op te slaan. (NEO-38678)
* Er is een probleem opgelost bij het uploaden van een afbeelding in de map Openbare bronnen in een instantie met een specifieke Berichtencentrum-configuratie. De volgende foutmelding verschijnt: Kan de afbeeldingen niet uploaden naar de trackingservers. (NEO-38546, NEO-45572)
* Er is een probleem opgelost waardoor het systeem crashte bij het opnieuw genereren de configuratie bij beschadigde configuratiebestanden. (NEO-38752)
* Er is een probleem opgelost waardoor leveringsindicatoren niet correct werden bijgewerkt. (NEO-44827)
* Er is een probleem opgelost dat tot een postupgradefout kon leiden bij het gebruik van complexe query&#39;s. (NEO-43648)
* Er is een probleem opgelost waardoor de voorvertoning van webApps niet werkte. (NEO-43242)
* Er is een probleem opgelost waardoor de lead van de levering mislukte bij het gebruik van een extern targettoewijzingsbestand in een workflow met een activiteit voor het laden van gegevens (bestand). (NEO-43691)
* Er is een probleem opgelost dat tot crashes kon leiden en een volledige herstart van de instantie vereiste. (NEO-44645)
* Er is een probleem opgelost waardoor Workflow Heatmap geen resultaat kon laden. (NEO-43360)
* Er is een probleem opgelost dat tot verbindingsproblemen kon leiden bij het gebruik van de externe FDA-connector. (NEO-42722)
* Er is een probleem opgelost met bewijzen bij het gebruik van adresvervanging en uitsluiting van controlegroepen. (NEO-39695)
* Er is een probleem opgelost dat kon leiden tot workflowfouten als gevolg van een probleem met de Snowflake-connector. (NEO-46299)
* Er is een probleem opgelost waarbij de clientconsole soms vastliep vanwege een ongeldig teken in een personalisatieblok. (NEO-45761)
* Een probleem opgelost dat tot verbindingsproblemen kon leiden bij het maken van een extern account voor Snowflake als externe database. (NEO-45744)
* Er is een probleem opgelost waardoor tabelinformatie soms beschermd werd weergegeven door een visibleIf-kenmerk. (NEO-37865)
* Er is een probleem opgelost waarbij de foutmelding &#39;$ is niet gedefinieerd&#39; soms werd weergegeven tijdens de leveringsanalysefase. (NEO-32940)
* Er is een probleem opgelost waarbij leveringen werden gekoppeld aan een verkeerd eventType. (NEO-45743)
* Een probleem opgelost dat kon leiden tot crashes als gevolg van intermitterende core dumps (NEO-30549)
* Er is een probleem opgelost dat tot crashes kon leiden bij het gebruik van foutieve HTML-code in een levering. (NEO-40385)
* Er is een probleem opgelost waardoor gebruikers die geen beheerder waren, geen toegang hadden tot het tabblad **Analyse** in de leveringseigenschappen. (NEO-34025)
* Er is een probleem opgelost waardoor een afbeelding tijdens het voorbereiden van berichten niet kon worden geüpload in segmentmodus van een externe server. (NEO-40307)

## ![](assets/do-not-localize/green_2.png) Release 7.2.2 - build 9349 {#release-7-2-2}

_1 maart 2022_

>[!NOTE]
>
> Deze build is compatibel met Client Console v7.2.1.

**Patches**

* Er is een probleem opgelost bij het configureren van het externe account **Webanalytics** die altijd de integratiestatus &#39;Integratie succesvol&#39; weergaf, zelfs als er fouten optraden. (NEO-36672)
* Verschillende postupgradefouten opgelost met het mechanisme voor de sequentie-ID bij negatieve ID&#39;s. (NEO-43205, NEO-42846, NEO-42845)
* Er is een probleem opgelost bij het gebruik van het externe account **Webanalytics** met terugkerende en continue leveringen, waardoor gegevens van het externe account gedeeltelijk verloren gingen. (NEO-38548)
* Er is een probleem opgelost dat de postupgrade vertraagde bij het bijwerken van de tabel NmsActiveContact. (NEO-43206)
* Er is een probleem opgelost met een postupgradefout die optrad als kant-en-klare mappen waren verplaatst van de **Beheer**-node naar een andere locatie. (NEO-42875)
* Er is een probleem opgelost met het gebruik van een workflowactiviteit **Gegevens bijwerken** waardoor het schema van de ontvanger niet kon worden bijgewerkt met gegevens van de ontvanger uit een externe Google Cloud-database. (NEO-42343)
* Er is een probleem opgelost tijdens de postupgrade met betrekking tot de Adobe Analytics-connector. (NEO-43318, NEO-38136)
* Er is een probleem opgelost met een overschreven CUID door VALUE_TO_CHANGE tijdens de postupgrade. (NEO-43267)
* Er is een probleem opgelost dat leidde tot fouten bij het synchroniseren van de mid-sourcing- en marketinginstanties op een multi-mid-configuratie. (NEO-10432)
* Er is een probleem opgelost dat leidde tot een fout bij het vernieuwen van de afleveringsworkflow bij meer dan 1000 brede logboeken tegelijk. (NEO-40276)
* Er is een probleem opgelost waardoor de leveringsindicatoren voor de open-ratio en de click-ratio niet automatisch werden bijgewerkt. (NEO-43253)

## ![](assets/do-not-localize/limited_2.png) Release 7.2.1 - build 9346 {#release-7-2-1}

_10 januari 2022_

**Beveiligingsverbetering**

Er zijn verschillende beveiligingsverbeteringen aangebracht in FDA-accounts:

* Wanneer u uw externe FDA-account configureert, kunt u zich nu aanmelden bij uw Snowflake-account met behulp van sleutelpaarverificatie voor verbeterde verificatiebeveiliging. [Meer informatie](../../installation/using/configure-fda-snowflake.md)
* Wanneer u uw externe FDA-account configureert, kunt u zich nu aanmelden bij uw Azure Synapse Analytics-account met behulp van de door het systeem toegewezen beheerde identiteit. [Meer informatie](../../installation/using/configure-fda-synapse.md#azure-external)
* Alle verwijzingen naar de log4j-bibliotheek zijn uit Campaign verwijderd om een optimale beveiliging te garanderen.

**Compatibiliteitsupdates**

Adobe Campaign is nu compatibel met Windows Server 2019. Raadpleeg de [Campaign-compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Verbeteringen**

* Microsoft Dynamics CRM 365-connector

   Er zijn kritieke oplossingen aangebracht voor de web-API van Microsoft Dynamics Connector:

   * Probleem verholpen dat optrad tijdens een importeractie die werd geactiveerd door een workflow. Hierdoor werden de lege waarden van tekenreeksvelden opgeslagen als nul in plaats van als lege waarden.
   * Probleem verholpen dat leidde tot de volgende fout voor het importeren of exporteren van gegevens met behulp van web-API-calls: Ongeldige URI: het URI-schema is te lang.
   * Er zijn verschillende problemen opgelost bij het importeren, vanuit Microsoft Dynamics 365, van gegevens die opzoekvelden bevatten.

* Google BigQuery FDA-connector

   * Google BigQuery FDA Connector is nu beschikbaar voor gehoste implementaties. [Meer informatie](../../installation/using/configure-fda-google-big-query.md)
   * Ondersteuning toegevoegd om verbindingen met een proxyserver mogelijk te maken voor Google BigQuery FDA-connector. Vereiste proxy-opties kunnen worden ingesteld via het veld Opties in de externe accountconfiguratie. [Meer informatie](../../installation/using/configure-fda-google-big-query.md#google-external)

**Andere wijzigingen**

* Na hun afschaffing zijn de actieactiviteiten van Microsoft CRM, Salesforce en Oracle CRM On Demand uit de interface verwijderd. Voor het configureren van de gegevenssynchronisatie tussen Adobe Campaign en een CRM-systeem kunt u de activiteit CRM-connector gebruiken. [Meer informatie](../../workflow/using/crm-connector.md)
* Het veld **[!UICONTROL Encrypted identifier]** is toegevoegd aan het bezoekersschema (nms:bezoeker). Dit veld wordt berekend en moet worden gebruikt voor webtoepassingen. Dit is van toepassing wanneer het Line-kanaal is geconfigureerd in de mid-sourcing-instantie.
* CRM-databronnen kunnen nu worden gebruikt met de activiteit **Databron wijzigen**.
* Er is een nieuwe optie toegevoegd in de **Foutbeheer**-eigenschappen van workflowactiviteiten: de optie **Afbreken bij fout** stopt automatisch de workflow. U kunt deze daarna niet opnieuw starten (NEO-29661). [Meer informatie](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Er wordt nu een speciale reeks gebruikt om de primaire sleutels voor de nmsGroup-tabel te genereren, die wordt gebruikt om statistische groepen ontvangers te maken. Vroeger werd de xtknewId-reeks gebruikt. (NEO-30832)
* Ondersteuning toegevoegd voor batchupdatebewerkingen met behulp van de CRM-connectoractiviteit.
* Verbeterde prestaties voor de verwerkingstijd van transactionele berichten. (NEO-40370)

**Patches**

* Er is een probleem opgelost bij het maken van een levering die leidde tot een fout in het tabblad **Afbeeldingen** van het venster **Tracking en afbeeldingen**. Dit gebeurde bij gebruik van een automatische proxyconfiguratie. (NEO-33260)
* Er is een probleem opgelost waardoor u een bestand niet kon uploaden op een Debian 10-server (HTTPS) in synchrone modus.
* Er is een probleem opgelost waardoor records van de tabel met leveringsstatistieken (`nmsDeliveryLogStats`) niet konden worden verwijderd uit de mid-sourcing-instantie tijdens het opschonen van de database nadat de gerelateerde leveringen waren verwijderd. (NEO-31034)
* Er is een probleem opgelost waardoor u geen meldingen voor mobiele apps op iOS kon verzenden terwijl u verificatie op basis van tokens gebruikte (NEO-38640).
* Er is een probleem opgelost waarbij soms scriptfoutberichten werden weergegeven bij het maken en configureren van rapporten (NEO-38393).
* Er is een probleem opgelost waardoor de trackingworkflow op Oracle kon mislukken doordat grote hoeveelheden leveringsindicatoren tegelijkertijd werden bijgewerkt (NEO-39653).
* Er is een probleem opgelost waardoor een levering niet kon worden verzonden vanwege een fout die optrad tijdens het uitvoeren van een besturingstypologie (NEO-39833).
* Er is een probleem opgelost in landingspagina&#39;s waardoor speciale tekens niet correct werden weergegeven in de HTML-pagina&#39;s van online-enquêtes (NEO-39438).
* Er is een probleem opgelost waardoor de Campaign Classic-console niet werkte wanneer u met de rechtermuisknop op een van de mappen op het tabblad Verkenner (NEO-38884) klikte.
* Er is een fout opgelost bij het gebruik van een eerder gemaakte leveringssjabloon die is gekoppeld aan een Web Analytics-account in een nieuwe levering waarbij de Web Analytics-configuratie ontbrak. (NEO-28666)
* Er is een probleem opgelost waardoor u geen voorbeeld van mobiele leveringen kon bekijken die aan een workflow waren gekoppeld.
* Er is een fout opgelost die verhinderde dat gepersonaliseerde tracking-URL&#39;s werden omgeleid wanneer het URL-handtekeningmechanisme voor trackinglinks was ingeschakeld.
* Er is een probleem opgelost dat na de upgrade mislukte storingen gaf vanwege een probleem met indexbeheer.
* Er is een fout opgelost die optrad bij het gebruik van opzoekveldgegevenstypen met Microsoft Dynamics CRM in **Import**- of **Export**-workflowactiviteiten.
* Er is een probleem opgelost waardoor u niet op de console kon inloggen vanwege een probleem met de proxyconfiguratie. (NEO-38388)
* Er is een regressieprobleem opgelost waardoor de functie **Map opschonen** niet correct werkte. (NEO-37459)
* Er is een probleem opgelost dat leidde tot een onjuiste aanvraagfout bij het gebruik van xml-gegevensvelden met de Microsoft Dynamics CRM-account als de xml waarnaar werd verwezen, dubbele aanhalingstekens bevatte.
* Er is een probleem opgelost waarbij netwerktime-outproblemen ten onrechte werden vastgelegd als scriptonderbrekingsproblemen in plaats van netwerkfouten. Dit probleem deed zich voor in het geval van HTTP-verzoeken die waren opgenomen in JavaScript-activiteiten. (NEO-38079)
* Er is een probleem opgelost dat onjuiste resultaten opleverde bij het uitvoeren van de Amazon Redshift HoursDiff- en MinutesDiff-functies tijdens het extraheren van de tijdcomponent.(NEO-31673)
* Er is een probleem opgelost waardoor het rapport **Hot Clicks** niet kon worden geladen voor leveringen sinds build 9182. (NEO-28900)
* Er is een fout opgelost die het symbool &amp; in een URL met de karakterentiteitsreferentie (`&amp;`), waardoor gebruikers geen toegang hadden tot de URL die aan een QR-code was gekoppeld. (NEO-28621)
* Er is een probleem opgelost waarbij een nieuw extern account werd gemaakt telkens wanneer een gebruiker een nieuwe campagneworkflow en een leveringsactiviteit aan een Web Analytics-account maakte. Dit werd veroorzaakt door een ontbrekende ID in het webAnalyticsAccount-publicatieobject. (NEO-39691)
* Er is een probleem opgelost waardoor de werkstroomactiviteit **Leeslijst** niet werkte wanneer de lijst in de database werd geïdentificeerd met een negatieve ID. (NEO-39607)
* Er is een probleem opgelost waarbij de workflow **Mid-sourcing (leveringslogboeken)** kon mislukken. (NEO-39662)
* Er is een probleem opgelost waardoor u geen voorbeeld van e-mailleveringen kon bekijken die aan een workflow waren gekoppeld. (NEO-37840)
* Er is een probleem opgelost dat ertoe kon leiden dat geldige tabellen met lijstwaarden werden verwijderd door de workflow voor het opschonen van de database. (NEO-34911)
* Er is een probleem opgelost waardoor de factureringsworkflow kon crashen op marketinginstanties.
