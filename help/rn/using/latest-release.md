---
product: campaign
title: Laatste release
description: Nieuwste opmerkingen bij de release van Campaign Classic
feature: Overzicht
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 28083eb0271c8c148955fa33978479dc3683eaed
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 52%

---

# Laatste release{#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van de Campaign Classic-releasekandidaat**.

>[!NOTE]
>
>Campaign **General Availability (GA)-builds** zijn: de [[!DNL Gold Standard] 11-release](../../rn/using/gold-standard.md#gs-11) en de [Campaign 20.2.5-release](../../rn/using/release--20-2.md).

## ![](assets/do-not-localize/blue_2.png) Release 21.1.3 - build 9330 {#release-21-1-3-build-9330}

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
<p>De integratie tussen Journey Orchestration en Adobe Campaign Classic is nu GA. Journey Orchestration kan e-mails, pushberichten en SMS verzenden met de Adobe Campaign Classic Transaction Messaging-mogelijkheden.</p>
<p>De verbinding tussen de instanties van de Journey Orchestration en van de Campaign Classic is opstelling door Adobe bij leveringstijd.</p>
<p>Raadpleeg de <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html">Journey Orchestration-documentatie</a> voor meer informatie. In deze <a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html">sectie</a> wordt een stapsgewijs gebruiksgeval weergegeven</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>Verbeteringen lijnkanaal</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>De volgende verbeteringen zijn toegevoegd aan het lijnkanaal:
</p>
<ul> 
<li><p>Ondersteuning voor LINE-videoberichttype</p></li>
<li><p>Ondersteuning voor LINE Partner Registration API</p></li>
<li><p>Ondersteuning voor het opnieuw verzenden van berichten in geval van een fout aan de serverzijde of time-out van het netwerk</p></li>
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

* De toegang tot de **xtk:session#GetCnxInfo** API-methode die de volledige gegevens van de databaseverbinding retourneert, is nu beperkt tot alleen beheerders. (NEO-27779)
* De vervangen decryptString-functie is vervangen door decryptPassword in CRM-gerelateerde JavaScript-bestanden.
* De functie Handtekening bijhouden is verbeterd en beperkt het risico dat omleidingsfouten worden bijgehouden wanneer hulpmiddelen van derden (e-mailclients, internetbrowsers, beveiligingsprogramma&#39;s voor koppelingen) de bijgehouden koppeling wijzigen.
* Probleem verholpen waardoor bijgehouden URL&#39;s niet meer werken als deze hoofdletters bevatten. Ondertekeningsmechanisme van bijgehouden URL&#39;s is nu hoofdlettergevoelig. (NEO-28414)

**Compatibiliteitsupdates**

De volgende systemen worden nu ondersteund met Campaign:
* Google Big Query FDA-connector
* Vertica FDA-connector
* PostgreSQL 13

Ontdek meer in de [Campaign-compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

**Verouderde functies**

* Vanaf de release van Campagne 21.1 is de Adobe Analytics Data Connector verouderd. Als u deze schakelaar gebruikt, moet u uw implementatie aanpassen dienovereenkomstig met de nieuwe schakelaar van Adobe Analytics.
Raadpleeg de [gedetailleerde documentatie](../../platform/using/adobe-analytics-connector.md) voor meer informatie.
* De ondersteuning voor Debian 8 is nu afgekeurd.
* Na de afschrijving van Oracle CRM in 20.3 is de gerelateerde externe rekening uit de interface verwijderd.

Meer informatie vindt u op de pagina [Afgeschafte en verwijderde functies](../../rn/using/deprecated-features.md).

**Verbeteringen**

* Er zijn extra controles toegevoegd bij het opslaan van een workflow om ervoor te zorgen dat de namen van activiteiten uniek zijn en dat overgangen altijd worden gevolgd door een activiteit.
* De technische workflow **Facturering (facturering)** bevat nu de taken die oorspronkelijk zijn uitgevoerd door de workflow **Aantal actieve factureringsprofielen** (billingActiveContactCount), die is verwijderd. Het e-mailrapport dat elke maand door de workflow wordt verzonden, bevat nu informatie over het aantal actieve profielen voor de instantie. [Meer informatie](../../workflow/using/about-technical-workflows.md).
* Het nieuwe **_keyOnMData** attribuut is toegevoegd om een sleutel voor verrichtingen op memogegevens te kunnen gebruiken.

**Overige wijzigingen**

* De openssl-derde voor Windows is bijgewerkt naar versie 1.1.1h.
* In de beschrijving van het Debian-pakket is NLServer gewijzigd in Adobe Campaign Classic-server.

**Patches**

* Probleem verholpen tijdens het bewerken van de sessietime-out voor het afmelden van gebruikers na een bepaalde tijd waarin gebruikers zich zelfs na de ingestelde tijd bleven aanmelden.
* Probleem verholpen waarbij leveringen als alleen-lezen werden weergegeven, maar nog wel konden worden bewerkt in de eigenschappen van de leveringen.
* Correctie van een fout die ervoor zorgde dat de werkbalk voor bewerken verdween bij het ontwerpen van een webtoepassing.
* Probleem verholpen waarbij de tekstversie van een e-mailbericht met Adobe Campaign Classic-kopteksten werd weergegeven wanneer een koppeling naar een e-mailbericht werd toegevoegd. (NEO-29211
* Bij gebruik van FDA via HTTP-verbinding, bleef de **Mid-sourcing (leveringslogboeken)** (defaultMidSourcingLog)-workflow vast in het tijdframe dat is ingesteld door de optie **NmsMidSourcing_LogsPeriodHour**. Hierdoor wordt voorkomen dat records worden bijgewerkt met gegevens die na dit ingestelde tijdpad zijn opgetreden. (NEO-30833)
* Probleem verholpen die optrad na het uitvoeren van de synchronisatieworkflow van het berichtcentrum. Telkens wanneer een omslag van leveringsvoorwerpen aan een douanemap werd bewogen, zou het werkschema de leveringen terug naar generische **Transactionele berichtgeschiedenis** omslag bewegen. (NEO-27445)
* Probleem verholpen waarbij een foutbericht werd weergegeven tijdens een poging om de **Cijfers voor uitzending**, **Tracking-indicatoren** en **Statistieken van de delende activiteiten**-rapporten weer te geven.
* De **Oracle On Demand** werkschemaactiviteit is verwijderd uit de interface na de afleiding van de Oracle CRM-connector.
* Probleem verholpen waarbij de uitvoering van verwerkingsworkflows werd gestopt na het dagelijks opnieuw opstarten van de wfserver-module (workflowserver). (NEO-30047)
* Probleem verholpen waardoor het MX-beheerdocument niet kon worden bijgewerkt, wat negatieve gevolgen zou kunnen hebben voor de IP-reputatie. (NEO-29897)
* Probleem verholpen waarbij het webproces vastliep bij het ontvangen van een SOAP-aanroep. (NEO-28796) (NEO-29600)
* Probleem opgelost waarbij het maken van de FDA-index van het SAP HANA mislukte. (NEO-29664)
* Probleem verholpen waarbij transactieberichten in de status **Wachten** konden worden bewaard wanneer SOAP-aanroepen met een header werden uitgevoerd. (NEO-28737)
* Probleem verholpen die optrad bij gebruik van de Teradata FDA-connector: alle tijdelijke tabellen werden gemaakt op slechts één knooppunt van het cluster, waardoor de hele spoolruimte zou kunnen worden ingenomen en Teradata vastliep. De tijdelijke tabellen worden nu op veel knooppunten gegenereerd. (NEO-28230)
* Probleem verholpen bij het gebruik van webtoepassingen die ervoor zorgden dat trackinglabels onjuiste primaire sleutels naar het schema **nms leidden:trackingURL**. (NEO-27931)
* De compatibiliteit met ODBC 3.x is verbeterd om foutberichten accuraat te maken.
* Probleem verholpen waarbij de console vastloopt als sjablonen voor aangepaste inhoud werden gebruikt in e-mailleveringen. (NEO-31547)
* Probleem verholpen waarbij Tomcat geen geldige reacties kon verzenden vanwege een langzame verbinding of een grote reactiegrootte.
* Probleem verholpen die kon optreden bij het lezen van UUID vanuit een PostgreSQL-database.
* Probleem verholpen dat tot prestatieproblemen kan leiden bij het zoeken naar propositiegegevens met betrekking tot aanbiedingen. (NEO-27554)
* Probleem opgelost waarbij het webproces niet reageerde wanneer de IMS-service was geactiveerd maar niet reageerde.
* Probleem verholpen waarbij u geen levering kon verzenden met een groep proefdrukken vanwege een specifiek samenvoegingsmechanisme dat de levering niet kon aanpassen. (NEO-14391)
* Probleem verholpen waarbij geen waarschuwing met de waarschuwingsactiviteit werd verzonden als een query en een verrijkingsactiviteit de leveringstabel als doel hadden. (NEO-25157)

## ![](assets/do-not-localize/red_2.png) Release 21.1.2 - build 9282 {#release-21-1-2-build-9282}

_15 april 2021_

* Wachtwoordbeheer is verbeterd om de beveiliging te optimaliseren.
* Er is een probleem opgelost waarbij MTA soms vastliep.

## ![](assets/do-not-localize/red_2.png) Release 21.1.1 - build 9277 {#release-21-1-1-build-9277}

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
