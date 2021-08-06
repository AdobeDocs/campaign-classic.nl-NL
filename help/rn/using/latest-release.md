---
product: campaign
title: Laatste release
description: Nieuwste opmerkingen bij de release van Campaign Classic
feature: Overzicht
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: c59529a0a4d72ecb795569591d62a68f030a0ac7
workflow-type: tm+mt
source-wordcount: '1951'
ht-degree: 99%

---

# Laatste release{#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd bij de **nieuwste Campaign Classic Release**.

>[!NOTE]
>
>Campaign **General Availability (GA)-builds** zijn: de [[!DNL Gold Standard] 11-release](../../rn/using/gold-standard.md#gs-11) en de [Campaign 21.1.3-release](../../rn/using/latest-release.md#release-21-1-3-build-9330).

## ![](assets/do-not-localize/green_2.png) Release 21.1.3 - Build 9330 {#release-21-1-3-build-9330}

_5 juni 2021_

**Nieuwe functies**

<table>
<thead>
<tr>
<th><strong>Integratie met Adobe Journey Orchestration</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>De integratie tussen Journey Orchestration en Adobe Campaign Classic is nu GA. Journey Orchestration kan e-mails, pushberichten en sms-berichten verzenden met behulp van de Adobe Campaign Classic Transactional Messaging-mogelijkheden.</p>
<p>De verbinding tussen de instanties van Journey Orchestration en Campaign Classic wordt door Adobe ingesteld tijdens de inrichting.</p>
<p>Raadpleeg de <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=nl">Journey Orchestration-documentatie</a> voor meer informatie. In deze <a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=nl">sectie</a> wordt een stapsgewijs gebruiksscenario gepresenteerd</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>Line-kanaalverbeteringen</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>De volgende verbeteringen werden toegevoegd aan het Line-kanaal:
</p>
<ul> 
<li><p>Ondersteuning voor Line-videoberichttype</p></li>
<li><p>Ondersteuning voor Line Partner Registration-API</p></li>
<li><p>Ondersteuning voor het opnieuw verzenden van berichten in geval van een Line-fout aan serverzijde of een time-out van het netwerk</p></li>
</ul>
<p>Raadpleeg de <a href="../../delivery/using/line-channel.md">gedetailleerde documentatie</a> voor meer informatie.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Vertica FDA-connector</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>U kunt nu uw Adobe Campaign Classic-instantie verbinden met uw externe Vertica-database. Deze verbinding wordt beheerd via een nieuw extern account.</p>
<p>Raadpleeg de <a href="../../installation/using/configure-fda-vertica.md">gedetailleerde documentatie</a> voor meer informatie.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Google Big Query FDA-connector</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>U kunt nu uw Adobe Campaign Classic-instantie verbinden met uw externe Google Big Query-database. Deze verbinding wordt beheerd via een nieuw extern account.
</p>
<p>Raadpleeg de <a href="../../installation/using/configure-fda-google-big-query.md">gedetailleerde documentatie</a> voor meer informatie.</p>
</td> 
</tr> 
</tbody> 
</table>

**Verbeterde beveiliging**

* De toegang tot de **xtk:session#GetCnxInfo** API-methode die de volledige details van de databaseverbinding retourneert, is nu beperkt tot alleen beheerders. (NEO-27779)
* De afgeschafte decryptString-functie is vervangen door decryptPassword in CRM-gerelateerde JavaScript-bestanden.
* De functie voor het volgen van handtekeningen is verbeterd om het risico op trackingfouten te verkleinen wanneer tools van derden (e-mailclients, internetbrowsers, veilige koppelingsbeveiligingstools) de gevolgde koppeling wijzigen.
* Er is een probleem opgelost waardoor bijgehouden URL&#39;s niet werkten als ze hoofdletters bevatten. Het ondertekeningsmechanisme van bijgehouden URL&#39;s is nu hoofdlettergevoelig. (NEO-28414)

**Compatibiliteitsupdates**

De volgende systemen worden nu ondersteund met Campaign:
* Google Big Query FDA-connector
* Vertica FDA-connector
* PostgreSQL 13

Ontdek meer in de [Campaign-compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

**Verouderde functies**

* Vanaf Campaign 21.1 is de Adobe Analytics-gegevensconnector afgeschaft. Als u deze connector gebruikt, moet u uw implementatie dienovereenkomstig aanpassen met de nieuwe connector Adobe Analytics Connector.
Raadpleeg de [gedetailleerde documentatie](../../technotes/aa-connector-migration.md) voor meer informatie.
* De ondersteuning voor Debian 8 is nu afgeschaft.
* Na het afschaffen van Oracle CRM in 20.3 is het verbonden externe account uit de interface verwijderd.

Meer informatie vindt u op de pagina [Afgeschafte en verwijderde functies](../../rn/using/deprecated-features.md).

**Verbeteringen**

* Er zijn extra controles toegevoegd bij het opslaan van een workflow om ervoor te zorgen dat de namen van activiteiten uniek zijn en dat overgangen altijd worden gevolgd door een activiteit.
* De technische workflow **Facturering (facturering)** bevat nu de taken die oorspronkelijk werden uitgevoerd door de workflow **Aantal actieve factureringsprofielen** (billingActiveContactCount), die is verwijderd. Het e-mailrapport dat elke maand door de workflow wordt verzonden, bevat nu informatie over het aantal actieve profielen voor de instantie. [Meer informatie](../../workflow/using/about-technical-workflows.md).
* Het nieuwe **_keyOnMData** attribuut is toegevoegd om een sleutel voor bewerkingen van memogegevens te kunnen gebruiken.

**Andere wijzigingen**

* De derde partij openssl voor Windows is bijgewerkt naar versie 1.1.1h.
* In de beschrijving van het Debian-pakket is nlServer gewijzigd in Adobe Campaign Classic-server.

**Patches**

* Er is een probleem opgelost bij het bewerken van de sessietime-out om gebruikers na een bepaalde tijd af te melden, waardoor gebruikers zelfs na de ingestelde tijd aangemeld bleven.
* Er is een probleem opgelost waarbij leveringen werden weergegeven als alleen-lezen, maar nog steeds konden worden bewerkt in de leveringseigenschappen.
* Er is een fout gecorrigeerd die ervoor zorgde dat de werkbalk voor bewerken verdween bij het ontwerpen van een webapplicatie.
* Er is een fout opgelost waarbij de tekstversie van een e-mailbericht met Adobe Campaign Classic-kopteksten werd weergegeven wanneer een koppeling naar een e-mailbericht werd toegevoegd. (NEO-29211
* Bij gebruik van FDA via HTTP-verbinding zat de **Mid-sourcing (leveringslogboeken)** (defaultMidSourcingLog)-workflow vast in het tijdsbestek dat is ingesteld door de optie **NmsMidSourcing_LogsPeriodHour**. Dit zou voorkomen dat records worden bijgewerkt met gegevens die na dit ingestelde tijdsbestek zijn opgetreden. (NEO-30833)
* Er is een probleem opgelost dat optrad na het uitvoeren van de synchronisatieworkflow van het berichtencentrum. Telkens wanneer een map met leveringsvoorwerpen naar een aangepaste map werd verplaatst, verplaatste de workflow de leveringen terug naar de generieke map **Transactional Message-history**. (NEO-27445)
* Er is een probleem opgelost waarbij een foutbericht werd weergegeven tijdens een poging om de rapporten **Broadcast-statistieken**, **Tracking-indicatoren** en **Statistieken van de delende activiteiten** weer te geven.
* De **Oracle On Demand**-workflowactiviteit is verwijderd uit de interface na het afkeuren van de Oracle CRM-connector.
* Er is een probleem opgelost waarbij de uitvoering van verwerkingsworkflows werd gestopt na het dagelijks opnieuw opstarten van de workflowservermodule (wfserver). (NEO-30047)
* Er is een probleem opgelost waardoor het MX-beheerdocument niet kon worden bijgewerkt, wat negatieve gevolgen zou kunnen hebben voor de IP-reputatie. (NEO-29897)
* Er is een probleem opgelost waardoor webprocessen vastliepen bij het ontvangen van een SOAP-call. (NEO-28796, NEO-29600)
* Er is een probleem opgelost waarbij het maken van de FDA-index van SAP HANA mislukte. (NEO-29664)
* Er is een probleem opgelost waarbij transactieberichten soms in de status **Wachten** bleven bij het uitvoeren van SOAP-calls met een header. (NEO-28737)
* Er is een probleem opgelost dat optrad bij gebruik van de Teradata FDA-connector: alle tijdelijke tabellen werden gemaakt op slechts één knooppunt van het cluster, waardoor soms de hele spoolruimte werd bezet en Teradata vastliep. De tijdelijke tabellen worden nu op veel knooppunten gegenereerd. (NEO-28230)
* Er is een probleem opgelost bij het gebruik van webapplicaties dat ervoor zorgde dat trackinglabels onjuiste primaire sleutels genereerden naar het schema **nms: trackingURL**. (NEO-27931)
* De compatibiliteit met ODBC 3.x is verbeterd om de nauwkeurigheid van foutberichten te verzekeren.
* Er is een probleem opgelost waarbij de console vastliep als aangepaste contentsjablonen werden gebruikt in e-mailleveringen. (NEO-31547)
* Er is een probleem opgelost waardoor Tomcat geen geldige antwoorden kon verzenden vanwege een trage verbinding of een grote respons.
* Er is een probleem opgelost dat kon optreden bij het lezen van UUID vanuit een PostgreSQL-database.
* Er is een probleem opgelost dat tot prestatieproblemen kon leiden bij het zoeken naar voorstelgegevens gekoppeld aan aanbiedingen. (NEO-27554)
* Er is een probleem opgelost waarbij het webproces niet reageerde wanneer de IMS-service was geactiveerd, maar niet reageerde.
* Er is een probleem opgelost waarbij u geen levering kon verzenden met een groep proeven vanwege een specifiek samenvoegingsmechanisme dat de personalisatie van de levering niet kon uitvoeren. (NEO-14391)
* Er is een probleem opgelost waarbij geen waarschuwing met de waarschuwingsactiviteit werd verzonden als een query en een verrijkingsactiviteit de leveringstabel als doel hadden. (NEO-25157)

## ![](assets/do-not-localize/red_2.png) Release 21.1.2 - Build 9282 {#release-21-1-2-build-9282}

_15 april 2021_

* Wachtwoordbeheer is verbeterd om de beveiliging te optimaliseren.
* Er is een probleem opgelost waarbij MTA soms vastliep.

## ![](assets/do-not-localize/red_2.png) Release 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

_22 februari 2021_

**Verbeterde beveiliging**

* Het mechanisme voor consoleverificatie is verbeterd om de beveiliging te optimaliseren. (NEO-26944)
* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-28532)

**Compatibiliteitsupdates**

De volgende systemen worden nu ondersteund met Campaign:

* Salesforce-API-versie 49 wordt nu ondersteund bij gebruik van het externe Salesforce CRM-account.

**Afgeschafte functies**

Het rapport **Technical Deliverability Monitoring** is nu afgeschaft.

Meer informatie vindt u op de pagina [Afgeschafte en verwijderde functies](../../rn/using/deprecated-features.md).

**Verbeteringen**

**Email Feedback Service (EFS)** is een schaalbare service die rechtstreeks feedback van de Enhanced MTA vastlegt, zodat de rapporteringsnauwkeurigheid wordt verbeterd. Deze functie wordt uitgebracht als een persoonlijke bètaversie en wordt in toekomstige versies geleidelijk beschikbaar gemaakt voor alle klanten.

* Alle categorieën feedback worden nu vastgelegd voor volledige en nauwkeurige rapportage.
* De berekening van de Geleverd-indicator is nu gebaseerd op realtimefeedback van de Enhanced MTA voor verbeterde nauwkeurigheid en reactiviteit.
* EFS lost het probleem van vertragingen bij het rapporteren van synchrone soft bounces op.

Raadpleeg de [gedetailleerde documentatie](../../delivery/using/sending-with-enhanced-mta.md#efs) voor meer informatie.
Als u geïnteresseerd bent in deelname aan deze gesloten bèta, vult u dit [formulier](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) in. We nemen dan contact met u op.

**Overige wijzigingen**

* De overdrachtsnelheid is verbeterd voor grote trackinglogboeken door compressie te gebruiken.
* De workflowheatmap is verbeterd om time-outs te voorkomen bij het uitvoeren van workflows met meerdere activiteiten. (NEO-27423).
* Er is een probleem opgelost waarbij een aanbieding nog kon worden ingediend als de einddatum was verstreken. Campaign Classic houdt nu rekening met de volledige tijdstempel van de einddatum in plaats van alleen met de datum. (NEO-27590)
* De Google+-koppeling is verwijderd uit het gedeelte waar u **koppelingen voor het delen op sociale media** kunt aanpassen.
* Er is een probleem opgelost na de implementatie van een foutoplossing in de vorige release. Er is een controle voor de hostnaam toegevoegd bij het verbinden via SSL/TLS. Sms-berichten konden hierdoor voorheen niet worden verzonden. De hostnaamverificatie is uitgeschakeld voor de meeste protocollen zoals POP3, sms en HTTP met proxy, en de certificaatcontrole voor het externe sms-account is verbeterd met drie waarden (NEO-29581). [Meer informatie](../../delivery/using/sms-protocol.md#skip-tls)

**Patches**

* Er is een probleem opgelost waarbij de sneltoetsen Tab, Enter en Escape niet werkten op het nieuwe aanmeldingsscherm.
* Er is een probleem met vernieuwen opgelost waarbij de naam van een nieuwe workflow na het opslaan werd vervangen door de standaardwaarde (NEO-26106).
* Er is een probleem opgelost dat optrad tijdens het uitvoeren van workflows waarbij een nieuw veld werd toegevoegd als onderdeel van een **verrijkingsactiviteit** voorafgaand aan een **verzendingsactiviteit** met behulp van de doeltoewijzing **External file**: er werden ongewenste velden toegevoegd aan de doeltoewijzing **External file**. (NEO-27687)
* Er is een probleem opgelost waarbij sommige tekens in de broncode werden gewijzigd wanneer een webapplicatie die eerder was gemaakt en opgeslagen, opnieuw werd geopend. (NEO-27597)
* Er is een probleem opgelost dat zich kon voordoen bij de upgrade naar een build met het nieuwe handtekeningmechanisme voor het bijhouden van koppelingen (vanaf build 19.1.4 en Campaign 20.2): wanneer verschillende sjablonen aan een gebeurtenis waren gekoppeld, kon de upgrade ertoe leiden dat de verkeerde sjabloon werd geselecteerd tijdens het verzenden van het transactionele bericht. (NEO-28326)
* Er is een probleem opgelost waarbij de MTA niet meer reageerde en geen verzendingen kon verwerken tenzij deze opnieuw werd gestart. (NEO-27455)
* Er is een probleem opgelost met het tijdstempelbeheer van een MSSQL-database tijdens het bulksgewijs laden van een kolom van het type Datum/tijd.
* Er is een probleem opgelost met een workflowquery bij het gebruik van Redshift-xtk-functies. SubDays, SubSeconds, SubMinutes en SubHours accepteren nu beide Redshift-tijdstempeltypen (NEO-24962).
* Er is een probleem opgelost waarbij een scriptfoutbericht werd weergegeven bij een voorvertoning van een rapport met anonieme toegang. (NEO-27081)
* Er is een probleem opgelost waarbij het geheugengebruik op de server werd verminderd tijdens het uitvoeren van de verzendingsanalyse.
* Er is een probleem opgelost waardoor de instantie mogelijk niet werkte wanneer specifieke complexe query&#39;s werden uitgevoerd.
* Er is een probleem opgelost waarbij de technische workflow **Synchronizing Twitter pages** mogelijk niet werd uitgevoerd. (NEO-28634)
* Er is een probleem opgelost waarbij soms een foutbericht werd weergegeven voor de functie decryptPassword tijdens een poging om op Twitter te publiceren met de verzendingssjabloon **Tweet (twitter)**. (NEO-28216)
* Er is een probleem opgelost dat optrad bij het gebruik van een **Javascript**-activiteit om een HTTP-aanvraag in een workflow uit te voeren. De aanroep mislukte met de volgende fout (NEO-29146) na het bepalen van het poortnummer in de hostnaam:

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Er is een probleem opgelost waardoor geen nieuwe verzendingen met personalisatie van doelgegevens konden worden verzonden (NEO-30323).
* Er is een probleem opgelost waarbij verschillende crashes optraden in de marketinginstantie waardoor dumpbestanden werden veroorzaakt.
* Er is een probleem opgelost waarbij de **Tracking**-workflow mislukte met de volgende fout (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Er is een probleem opgelost dat optrad bij het maken en opslaan van een verzending op het tabblad **Targeting &amp; Workflow** van een campagne: de voorvertoning mislukte met de volgende fout (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Er is een probleem opgelost dat optrad bij het instellen van een extern account tussen een marketinginstantie en een Adobe Campaign Standard-instantie of een Campaign Classic-mid-sourcinginstantie, en het gebruiken van de optie DisableFOH2=1. Bij het gebruik van de optie DisableFOH2=1 in het externe account werden de verbindingen niet correct gesloten, wat resulteerde in de volgende fout (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Er is een sms-probleem opgelost waarbij verbindingsproblemen optraden tussen de server en de provider. De verbinding werd vervolgens door de onderliggende MTA automatisch uitgeschakeld. Adobe Campaign Classic deed geen poging om verbinding te maken met deze falende verbinding zolang er geen nieuwe onderliggende MTA werd gestart.
