---
product: campaign
title: Processen opvolgen
description: Leer hoe u Campagne-processen kunt controleren
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1f5d8c7e-6f9b-46cd-a9b4-a3b48afb1794
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '3606'
ht-degree: 0%

---

# Processen opvolgen{#monitoring-processes}

![](../../assets/v7-only.svg)

De toepassingsserver en de omleidingsserver (**bijhouden**) kan handmatig of automatisch worden gecontroleerd.

## Handmatige controle {#manual-monitoring}

Ga naar **[!UICONTROL Monitoring]** en klik op de knop **[!UICONTROL Overview]** koppeling gebruiken om de pagina voor procesbewaking van Adobe Campaign weer te geven.

![](assets/d_ncs_monitoring.png)

Met de weergegeven pagina kunt u de status van de verbonden instantie weergeven, namelijk:

* informatie over de zaak : versie, naam, database-engine, geïnstalleerde pakketten, serversysteemindicatoren,
* de lijst van ontbrekende processen en uitvoeringsinformatie (begindatum, PID, enz.);
* een weergave van workflows en leveringen.

Aanvullende manieren om de verschillende campagneprocessen te bewaken worden weergegeven in [deze pagina](../../production/using/monitoring-guidelines.md).

### Logboekjournaal {#log-journal}

Het is mogelijk om het logboekdagboek met betrekking tot een proces te tonen. Klik hiertoe op het proces. **mta** klikt u bijvoorbeeld op **[!UICONTROL Open the log journal]** .

![](assets/d_ncs_monitoring2.png)

### Systeemindicatoren {#system-indicators}

Met de lijst met systeemindicatoren kunt u informatie over de computer weergeven, zoals het fysieke en virtuele geheugen, actieve processen en beschikbare schijfruimte. De indicatoren zijn verschillend voor Linux en Vensters werkende systemen. Ga naar de **[!UICONTROL Instance Monitoring]** en klik op de knop **[!UICONTROL Display]** link naar de lijst van indicatoren

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]** : specifieke indicator voor **Berichtencentrum**. Zie [deze sectie](../../message-center/using/additional-configurations.md#monitoring-thresholds) voor meer informatie .

* **[!UICONTROL Memory]** : informatie over het fysieke geheugen (RAM).

   **[!UICONTROL Current value]** : daadwerkelijk geheugenverbruik.

   **[!UICONTROL Max Value]** : totale hoeveelheid geïnstalleerd geheugen.

   **[!UICONTROL Available]** : hoeveelheid beschikbaar geheugen.

   **[!UICONTROL Warning]** : deze indicator wordt weergegeven wanneer het geheugenverbruik 80% van de totale hoeveelheid bereikt.

   **[!UICONTROL Alert]** : deze indicator wordt weergegeven wanneer het geheugenverbruik 90% van de totale hoeveelheid bereikt.

   Wanneer de **[!UICONTROL Warning]** en **[!UICONTROL Alert]** Er worden indicatoren weergegeven. U kunt dit probleem oplossen door RAM toe te voegen aan het systeem waarop de Adobe Campaign-server is geïnstalleerd. U kunt ook besluiten de Adobe Campaign-server op een daarvoor bestemde computer te installeren.

* **[!UICONTROL Swap Memory]** : informatie met betrekking tot het virtuele geheugen dat een pagineringsdossier aanpast: een gebied op de vaste schijf dat door Windows wordt gebruikt alsof het RAM-geheugen is.

   **[!UICONTROL Current value]** : daadwerkelijk geheugenverbruik.

   **[!UICONTROL Max Value]** : totale hoeveelheid geheugen.

   **[!UICONTROL Available]** : hoeveelheid beschikbaar geheugen.

   **[!UICONTROL Warning]** : deze indicator wordt weergegeven wanneer het geheugenverbruik 80% van de totale hoeveelheid bereikt.

   **[!UICONTROL Alert]** : deze indicator wordt weergegeven wanneer het geheugenverbruik 90% van de totale hoeveelheid bereikt.

   Wanneer de **[!UICONTROL Warning]** en **[!UICONTROL Alert]** de indicatoren worden getoond, kunt u de kwestie oplossen door de grootte van het uitwisselingsdossier in de geavanceerde montages van Vensters te verhogen.

* **[!UICONTROL Disk XXX]** : informatie over machinelezers.

   **[!UICONTROL Current value]** : werkelijk gebruikte schijfruimte.

   **[!UICONTROL Max Value]** : totale schijfcapaciteit.

   **[!UICONTROL Available]** : schijfruimte beschikbaar

   **[!UICONTROL Used]** : percentage gebruikte schijf.

   **[!UICONTROL Warning]** : deze indicator wordt weergegeven wanneer de beschikbare schijfruimte 80% van de totale capaciteit bereikt.

   **[!UICONTROL Alert]** : deze indicator wordt weergegeven wanneer de beschikbare schijfruimte 90% van de totale capaciteit bereikt.

* **[!UICONTROL Number of processes too old]** : informatie over Adobe Campaign-processen die al meer dan een dag actief zijn.

   **[!UICONTROL Current value]** : aantal processen dat momenteel actief is.

   **[!UICONTROL Max Value]** : maximumaantal toegestane processen (1).

   **[!UICONTROL Alert]** : deze indicator wordt weergegeven als het aantal processen gelijk is aan 1.

   Wanneer de **[!UICONTROL Alert]** -indicator wordt weergegeven, kan het zijn dat het desbetreffende proces is vergrendeld door de SQL-database-engine of dat het proces vastzit in een oneindige lus. De **waakhond** -proces dat door Adobe Campaign wordt geleverd, wordt elke dag opnieuw gestart en kunt u dit probleem oplossen. U kunt echter ook zelf een einde maken aan het desbetreffende proces om een nieuwe start te forceren.

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]** : specifieke indicator voor **Berichtencentrum**. Zie [deze sectie](../../message-center/using/additional-configurations.md#monitoring-thresholds) voor meer informatie .

* **[!UICONTROL Load average (1/5/15 minutes)]** : informatie over de belasting, d.w.z. de gebruikssnelheid van de processor door de processen die gedurende de laatste minuut, vijf minuten of vijftien minuten op de machine worden uitgevoerd

   **[!UICONTROL Current value]** : werkelijke lading van de machine.

   **[!UICONTROL Max value]** : maximale belasting van het proces of de processen op de machine

   **[!UICONTROL Warning]** : deze indicator wordt weergegeven wanneer de lading 80 % van de maximaal toegestane waarde over de laatste minuut , vijf minuten of vijftien minuten bereikt .

   **[!UICONTROL Alert]** : deze indicator wordt weergegeven wanneer de lading 90 % bereikt van de maximaal toegestane waarde van de laatste minuut , vijf minuten of vijftien minuten .

* **[!UICONTROL Memory]** : informatie over het fysieke geheugen (RAM).

   **[!UICONTROL Current value]** : daadwerkelijk geheugenverbruik.

   **[!UICONTROL Max Value]** : totale hoeveelheid geïnstalleerd geheugen.

   **[!UICONTROL Available]** : hoeveelheid beschikbaar geheugen.

   **[!UICONTROL Warning]** : deze indicator wordt weergegeven wanneer het geheugenverbruik 80% van de totale hoeveelheid bereikt.

   **[!UICONTROL Alert]** : deze indicator wordt weergegeven wanneer het geheugenverbruik 90% van de totale hoeveelheid bereikt.

   Wanneer de **[!UICONTROL Warning]** en **[!UICONTROL Alert]** Er worden indicatoren weergegeven. U kunt dit probleem oplossen door RAM toe te voegen aan het systeem waarop de Adobe Campaign-server is geïnstalleerd. U kunt ook besluiten de Adobe Campaign-server op een daarvoor bestemde computer te installeren.

* **[!UICONTROL Swap Memory]** : informatie met betrekking tot het virtuele geheugen dat een pagineringsdossier aanpast: een gebied op de vaste schijf dat door Windows wordt gebruikt alsof het RAM-geheugen is.

   **[!UICONTROL Current value]** : daadwerkelijk geheugenverbruik.

   **[!UICONTROL Max Value]** : totale hoeveelheid geheugen.

   **[!UICONTROL Available]** : hoeveelheid beschikbaar geheugen.

   **[!UICONTROL Warning]** : deze indicator wordt weergegeven wanneer het geheugenverbruik 80% van de totale hoeveelheid bereikt.

   **[!UICONTROL Alert]** : deze indicator wordt weergegeven wanneer het geheugenverbruik 90% van de totale hoeveelheid bereikt.

   Wanneer de **[!UICONTROL Warning]** en **[!UICONTROL Alert]** Er worden indicatoren weergegeven. U kunt dit probleem oplossen door het uitwisselingsbestand groter te maken.

* **[!UICONTROL Core Files]** : informatie over de bestanden die zijn gegenereerd na het vastlopen van een Adobe Campaign-proces. Met deze bestanden kunt u de oorzaken van het vastlopen vaststellen.

   **[!UICONTROL Current Value]** : aantal bestaande bestanden.

   **[!UICONTROL Max Value]** : maximumaantal geoorloofde bestanden (1).

   **[!UICONTROL Warning]** : deze indicator wordt weergegeven wanneer het aantal bestanden groter is dan 1.

   **[!UICONTROL Alert]** : deze indicator wordt weergegeven wanneer het aantal bestanden gelijk is aan 1.

   Wanneer een proces wegens een botsing ontbreekt, wordt het getoond in rood op de lijst van processen en automatisch opnieuw begonnen door **waakhond** door Adobe Campaign opgegeven proces.

* **[!UICONTROL Number of shared memory segments]** : informatie over de geheugensegmenten die door alle Adobe Campaign-processen worden gedeeld.

   **[!UICONTROL Current value]** : aantal geheugensegmenten dat momenteel in gebruik is.

   **[!UICONTROL Max Value]** : maximum aantal geoorloofde geheugensegmenten (2).

   **[!UICONTROL Warning]** : deze indicator wordt getoond wanneer het aantal geheugensegmenten 1 bereikt.

   **[!UICONTROL Alert]** : deze indicator wordt getoond wanneer het aantal geheugensegmenten 2 bereikt.

* **[!UICONTROL Number of processes too old]** : informatie over processen die langer dan één dag actief zijn geweest.

   **[!UICONTROL Current value]** : aantal processen dat momenteel actief is.

   **[!UICONTROL Max Value]** : maximumaantal toegestane processen.

   **[!UICONTROL Warning]** : deze indicator wordt weergegeven wanneer het aantal processen 80 % van de toegestane drempel bereikt .

   **[!UICONTROL Alert]** : deze indicator wordt weergegeven wanneer het aantal processen 90 % van de toegestane drempel bereikt .

* **[!UICONTROL File Handles]** : informatie over de bestandsdescriptoren, d.w.z. het aantal geopende bestanden per proces.

   **[!UICONTROL Current value]** : het huidige aantal bestandsdescriptors.

   **[!UICONTROL Max Value]** : maximumaantal bestandsdescriptors dat door het besturingssysteem is geautoriseerd.

   **[!UICONTROL Warning]** : deze indicator wordt weergegeven wanneer het aantal geautoriseerde bestandsdescriptors de drempel van 80% bereikt.

   **[!UICONTROL Alert]** : deze indicator wordt weergegeven wanneer het aantal geautoriseerde bestandsdescriptors de drempel van 90% bereikt.

* **[!UICONTROL Processes]** : informatie over de machineverwerking.

   **[!UICONTROL Current value]** : aantal processen dat momenteel actief is.

   **[!UICONTROL Max Value]** : maximumaantal toegestane processen.

   **[!UICONTROL Active Processes]** : aantal actieve processen.

   **[!UICONTROL Inactive Processes]** : aantal inactieve processen.

   **[!UICONTROL Warning]** : deze indicator wordt weergegeven wanneer het aantal toegestane processen de drempel van 80 % bereikt.

   **[!UICONTROL Alert]** : deze indicator wordt weergegeven wanneer het aantal toegestane processen de drempel van 90% bereikt.

* **[!UICONTROL Zombie Processes]** : informatie over de processen die zijn gestopt maar nog een proces-herkenningsteken (PID) hebben en in de proceslijst zichtbaar blijven.

   **[!UICONTROL Current value]** : aantal zombie-processen dat momenteel actief is.

   **[!UICONTROL Max Value]** : maximumaantal toegestane zombie-processen (2).

   **[!UICONTROL Warning]** : deze indicator wordt weergegeven wanneer het aantal zombie-processen dichtbij 2 ligt.

   **[!UICONTROL Alert]** deze indicator wordt weergegeven wanneer het aantal zombie-processen 2 bereikt.

#### Aangepaste indicatoren {#customized-indicators}

Met Adobe Campaign kunt u indicatoren aanpassen. Dit doet u als volgt:

1. Een **.sh** bestand en noem het bestand **[!UICONTROL cust_indicators.sh]** .
1. Voeg uw aangepaste indicatoren toe aan dit bestand. Bijvoorbeeld:

   ```
   #!/bin/bash 
   echo "<indicator name='Zombie Processes'>  
   <current label='Current Value' value='0' display=''/>  
   <warning value='2'/>  <alert value='2'/>  
   <max label='Max Value' value='2'/>
   </indicator>"
   ```

   of

   ```
   #!/bin/bash 
   echo "<indicator name='Availability'>  
   <current label='Last update of data' display='2012-09-03 10:00'/>  
   <current label='Availability last month' display='100.00%'/>  
   <current label='Availability this month' display='100.00%'/> 
   <current label='Recent downtime periods' display='2012-07-04 11:10:00 - 11:19:59'/>
   </indicator>"
   ```

1. Plaats het bestand in de **[!UICONTROL usr/local/neolane/nl6]** map.

Dit bestand wordt aangeroepen door Adobe Campaign.

## SMTP-rapporten {#smtp-reports}

SMTP-rapporten voor de bewaking van de levering zijn geïntegreerd in het Adobe Campaign-platform. Zij kunnen via de console of het gebruiken van de toegang van het Web worden betreden.

Deze rapporten tonen SMTP leveringsstatistieken en SMTP fouten door domein.

De exploitant moet beheerrechten hebben om toegang te krijgen tot deze rechten.

Ze zijn gegroepeerd onder **Toezicht** > &#39;SMTP-bewaking&#39;.

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* Informatie over SMTP-bewaking is alleen beschikbaar als het e-mailkanaal is geactiveerd.
>* De **[!UICONTROL SMTP sending statistics]** alleen worden aangeboden als de statistische server op de instantie is gestart.

>


### SMTP-verzendende statistieken {#smtp-sending-statistics}

De **[!UICONTROL SMTP sending statistics]** het rapport laat u serveractiviteit controleren. Er wordt een synthese van elk van de overeenkomende elementen weergegeven.

![](assets/smtp_stats_report.png)

De lijst van indicatoren voor dit verslag wordt onder de grafiek weergegeven.

1. Het totale aantal verzonden berichten.
1. 
   * Blauwe lijn: berichten die klaar zijn om te worden verzonden en die in de Shaper zijn binnengekomen, d.w.z. laatste fase voordat SMTP wordt verzonden (valt samen met de binnenkomende gegevens).

   * Groene lijn: met succes verzonden berichten (valt samen met de uitgaande gegevens).

   * Rode lijn: berichten die door Shaper worden verlaten, aan **mta** (valt samen met de gegevens die over deze terugvordering zijn afgewezen).

   Deze waarden worden uitgedrukt in aantal berichten per uur.

1. Vertegenwoordigt twee rijen van Shapier:

   * Blauwe curve: wachtrij met actieve berichten. Deze berichten worden zo snel mogelijk verzonden.

   * Kaki-curve: de &#39;uitgestelde&#39; wachtrij. Deze berichten kunnen op dit moment niet worden geretourneerd vanwege een vertraging of omdat er geen verbinding met het doel beschikbaar is. De pogingen worden elke 5s, 10s, 20s, 40s, 2 min, enz. uitgevoerd. voor de definitie **MaxAgeSec** tijd voordat deze worden verlaten.

1. Deze grafieken tonen een detail van verlaten berichten (rode kromme op de tweede grafiek): het toont het aandeel berichten die zonder herpoging (fout) worden verlaten vergeleken met berichten het waarvan verzenden ontbrak (rood). Dit laat u het aandeel berichten bekijken die niet binnen de toegekende periode wegens beperkingen door de statistiekserver (throttling) of wegens verre serveronbeschikbaarheid worden verwerkt.
1. SMTP-verbindingen geopend of geopend.
1. Schatting van het aantal **mtachild**.

>[!NOTE]
>
>Dit rapport heeft betrekking op de status van de component Email Traffic Shaper.

### SMTP-fouten per domein {#smtp-errors-per-domain}

Dit rapport laat u de leveringsfouten, over een vastgestelde periode bekijken, die door domein wordt verdeeld.

>[!NOTE]
>
>De **minConnectionsToLog**, **minErrorsToLog** en **minMessagesToLog** opties van de **serverConf.xml** het dossier bepaalt de drempels waarboven verbindingsstatistieken in aanmerking worden genomen.

![](assets/smtp_error_report.png)

De lijst van indicatoren voor dit verslag is hieronder weergegeven.

* De **Domein** de kolom bevat de naam van het domein waarnaar de berichten worden verzonden (of de echte domeinnaam yahoo.com bijvoorbeeld voor yahoo.fr),
* De **Cnx** de kolom toont het aantal verbindingen SMTP open voor dit domein,
* De **Verzonden** de kolom komt overeen met het aantal berichten dat naar dit domein wordt verzonden;
* De **Volume** in de kolom wordt het volume weergegeven van berichten die naar dit domein zijn verzonden (bij benadering waarde),
* De **Fouten** de kolom toont een volumeindicator van fouten op dit domein over de periode,
* De **Laatste reactie** de kolom toont het laatste SMTP antwoordbericht dat voor dit domein wordt ontvangen;
* De **Datum** de kolom toont de datum van de laatste reactie SMTP voor dit domein wordt ontvangen dat.

>[!NOTE]
>
>De waarden die worden weergegeven in het dialoogvenster **Cnx**, **Verzonden**, en **Volume** de kolommen worden berekend ten opzichte van de in de **[!UICONTROL Period]** veld.

Klik op een domeinnaam om de fouten te bekijken.

Ze zijn gecategoriseerd door PublicId: dit herkenningsteken beantwoordt aan een IP adres dat door verscheidene Adobe Campaign mtas achter een router wordt gedeeld. De statistiekserver gebruikt deze id om de verbinding- en leveringsstatistieken tussen dit beginpunt en de doelserver te onthouden.

![](assets/smtp_error_report_details.png)

De **[!UICONTROL Owner of domain]** kunt u verschillende domeinnamen onder hetzelfde label groeperen. In de aanvankelijke rapportmening, zullen alle MX domeinnamen aan deze eigenaar worden geassocieerd.

Klik op een PublicID om meer details te bekijken.

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>Het foutenpercentage wordt vertegenwoordigd door twee grafieken. Het eerste is een horizontale voortgangsbalk op een zwarte achtergrond. De tweede grafiek is chronologisch. De geselecteerde periode wordt verdeeld in twaalf tijdintervallen, elk die door een verticale vooruitgangsbar worden vertegenwoordigd. In beide weergaven is de balk zwart als er geen fout is gedetecteerd. De kleur van de balk is afhankelijk van het percentage fouten dat is aangetroffen (geel, vervolgens oranje en tenslotte rood). De kleur grijs betekent dat er geen significant gegevensvolume is gevonden. Het is mogelijk om het nauwkeurige percentage van fouten te tonen door de curseur op de grafiek te zetten.

>[!NOTE]
>
>Voor meer informatie over SMTP-fouten en het beheer ervan in Adobe Campaign raadpleegt u [deze sectie](../../installation/using/email-deliverability.md).

## Factureringsrapport {#billing-report}

De **[!UICONTROL Billing]** de technische werkstroom verzendt het rapport van de systeemactiviteit naar de &quot;facturerings&quot;exploitant per e-mail. Het wordt teweeggebracht door gebrek 25th van elke maand op de instantie van de Marketing.

De technische workflow vindt u in een submap van het volgende knooppunt: **Beheer** > **Productie** > **Technische workflows**.

![](assets/billing.png)

Nadat de workflow elke 25e van de maand is gestart, ontvangt uw factureringsoperator het volgende rapport in zijn postvak.

![](assets/billing_2.png)

De volgende cijfers zijn beschikbaar om uw leveringen te volgen:

* **[!UICONTROL Start date]** : Begindatum van de levering. Merk op dat het vroeger dan de &quot;van&quot;datum van het rapport kan zijn.
* **[!UICONTROL Label]** : Etiket van de levering. Leveringen met minder dan 100 berichten worden als te klein beschouwd en dus geaggregeerd op de begindatum. In dat geval geeft het label het aantal aggregaten weer, bijvoorbeeld [Samenvoeging van 3 kleine leveringen].
* **[!UICONTROL Total volume]** : Het totale volume van de bytes dat voor de levering wordt overgebracht.
* **[!UICONTROL Avg volume]** : Gemiddeld volume van overgedragen bytes. Dit is het resultaat van de volgende formule **(totaal volume / berichten)**, die de berekeningsgrondslag vormt voor de **[!UICONTROL Multiplier]** metrisch.
* **[!UICONTROL Messages]** : Aantal verzonden berichten. Dit omvat zowel berichten die met succes werden verzonden als pogingen (na de ontvangst van een stuitbericht van de gecontacteerde server).
* **[!UICONTROL Multiplier (x)]** : De waarde van de vermenigvuldiger wordt afgetrokken van het gemiddelde volume van de berichten.
* **[!UICONTROL Count]** : Resultaat van de vermenigvuldiging van de berichten en de vermenigvuldiger.

## Automatische controle {#automatic-monitoring}

Adobe Campaign biedt verschillende automatische controlemethoden, die hieronder worden weergegeven.

### Opdrachtregel {#command-line}

Opdracht

**nlserver-monitor**

Hier geeft u een aantal indicatoren weer voor de Adobe Campaign-modules en het systeem.

Er wordt uitvoer gegenereerd in een gemakkelijk verwerkte XML-indeling.

Deze opdracht kan ook worden uitgevoerd met de opdracht **-missing** parameter, die van de processen een lijst maakt die van deze instantie missen wanneer de configuratiedossiers zeggen dat zij zouden moeten uitvoeren.

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### Door de server gepubliceerde informatie {#information-published-by-the-server}

#### /r/test {#r-test}

De **http(s)://`<application>`/r/test** wordt gebruikt om de omleidingsserver te testen. Wij adviseren gebruikend deze zelfde methode om de frontale servers te testen die voor het volgen worden gebruikt. Deze pagina kan ook worden gebruikt om een verzender van de lading te testen.

Een regel als deze wordt weergegeven in XML-indeling:

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**Frequentie**: deze test maakt geen gebruik van belasting en kan dus zeer vaak worden uitgevoerd (bijvoorbeeld eenmaal per seconde).

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

Dit **http(s)://`<Application server url>`/nl/jsp/ping.jsp**  pagina werkt op dezelfde manier als zijn netwerktegenhanger: het test een volledige vraag die door apache/tomcat/Webmodule/gegevensbestand gaat en aan de cliënt uploadt. Als alles goed werkt, geeft het een &quot;OK&quot;. We raden u aan deze test uit te voeren op computers met toegang tot de databases (bijvoorbeeld mtas&#39;s en enquêtes).

**Gebruik**: een zittingsteken verbonden aan een exploitant login moet als argument worden overgegaan om ver login (zie de uiteinde in [Automatische controle via Adobe Campaign-scripts](#automatic-monitoring-via-adobe-campaign-scripts)).

Bijvoorbeeld:

![](assets/ncs_monitoring_ping.png)

De naam van de operator en de aanmelding moeten eerder in de Adobe Campaign-clientconsole zijn geconfigureerd met databaserechten.

![](assets/ncs_operators_rights_01.png)

**Frequentie**: dit is een test die zeer weinig bandbreedte gebruikt . Het kan dus vrij vaak, maar niet meer dan eenmaal per minuut, worden uitgevoerd.

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

Dit is een test om te controleren of een operator via een webpagina toegang heeft tot de Adobe Campaign-server. dezelfde webpagina als de pagina die via de menu&#39;s van de clientconsole wordt geopend. U kunt deze pagina vanuit uw bewakingstools bellen (Tivoli, Nagios, enz.).

![](assets/ncs_monitoring_web.png)

**Gebruik**: een zittingsteken verbonden aan een exploitant login die u met de instantie laat verbinden moet als argument worden gebruikt (zie de uiteinde in [Automatische controle via Adobe Campaign-scripts](#automatic-monitoring-via-adobe-campaign-scripts)).

De exploitant en hun login moeten eerder in de de cliëntconsole van Adobe Campaign met de aangewezen gegevensbestandrechten en beperkingen worden gevormd.

**Frequentie**: dit is een volledige servertest en hoeft niet vaak te worden uitgevoerd (het kan bijvoorbeeld elke tien minuten worden uitgevoerd).

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

Dit **jsp** staat voor het toegangspunt voor Adobe Campaign-toepassings-API&#39;s. Zij kan daarom een gedetailleerd toezicht op de aanvraag uitvoeren. Het kan ook worden gebruikt om de Webdiensten van Adobe Campaign te controleren. Het wordt gebruikt in onze toezichtmanuscripten, maar merk op dat het voor machtsgebruikers slechts is.

### Controle op basis van implementatietypen {#monitoring-based-on-deployment-types}

Adobe Campaign maakt verschillende implementatieconfiguraties mogelijk (voor meer informatie hierover raadpleegt u [deze sectie](../../installation/using/hosting-models.md)). In deze sectie worden de verschillende automatische bewakingstechnieken beschreven die moeten worden toegepast, afhankelijk van het type installatie.

<table> 
 <thead> 
  <tr> 
   <th> Type implementatie </th> 
   <th> Controleren </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Zelfstandig </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> en <span class="uicontrol">/nl/jsp/monitor.jsp</span> op de Adobe Campaign-server</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Standaard </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> en <span class="uicontrol">/nl/jsp/ping.jsp</span> op de frontservers</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> op de toepassingsserver</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Enterprise </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> en <span class="uicontrol">/nl/jsp/ping.jsp</span> op de frontservers</p> </li> 
     <li><p> <span class="uicontrol">/r/test</span> en <span class="uicontrol">/nl/jsp/monitor.jsp</span> op de toepassingsserver</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Midden-sourcing </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> op de toepassingsserver</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Automatische controle via Adobe Campaign-scripts {#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign kan een hulpmiddel van de instantiecontrole (netreport) verstrekken dat u een rapport door e-mail betreffende de ontdekte anomalieën laat verzenden.

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>Dit gereedschap kan worden gebruikt om uw instanties te controleren, maar wordt niet ondersteund door Adobe Campaign. Neem voor meer informatie contact op met de beheerder van de campagne.

### Vereiste elementen {#required-elements}

Voor automatische controle zijn de volgende voorzorgsmaatregelen voorafgaand aan de installatie vereist:

* U moet beschikken over de **netreport.tgz** (Linux-installatie) of **netreport.zip** (Windows-installatie),
* We raden u ten zeerste aan geen bewaking op de te controleren machine te installeren,
* het moet zijn geïnstalleerd op een machine met een JRE of JDK;
* in Linux moet de te controleren computer **bc** pakket. Raadpleeg [deze sectie](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages) voor meer informatie.

### Installatieprocedure {#installation-procedure}

De installatieprocedure is als volgt:

1. Maak indien nodig in de console een nieuwe operator (de gebruiker voor &#39;controle&#39; bestaat al), maar wijs geen rechten toe.
1. Ophalen van archief uitvoeren.
1. Lees de **readme** bestand.
1. Werk de **netconf.xml** configuratiebestand.
1. Werk de **netreport.bat** (Windows) of **netreport.sh** (Linux).

### Het bestand netconf.xml configureren {#configuring-the-netconf-xml-file}

Het XML-configuratiebestand bevat de volgende elementen:

* [Element &#39;Eigenschappen&#39;](#properties--element)
* [Instantie-element](#instance--element)
* [Element &#39;Host&#39;](#host--element)
* [Subelementen](#sub-elements)

Hier volgt een configuratievoorbeeld:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<netconf>
  <properties mailServer="mail.adobe.net" mailFrom="mail@adobe.com" recipientList="recipient@adobe.com">
    <nightMode start="00:00 am" end="07:00 am"/>
    <buildRange minimum="7829" maximum="8180"/>
    <buildRange minimum="8300" maximum="8400"/>
    <sla/>
  </properties>

  <instance name="dev" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devrd.domain.com" alias="devrd" sessiontoken="monitoring" criticalLevel="1" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="false" isSecure="false"/>
                                <redir url="/r/test"/>
                                <http url="/nl/jsp/ping.jsp"/>
                </host>
                <host name="devtrk.domain.com" alias="devtrk" sessiontoken="monitoring" criticalLevel="0" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="true" isSecure="false"/>
                </host>
  </instance>
  <host name="dev-test" alias="dev-test" sessiontoken="monitoring" criticalLevel="2">
                <ncs instance="dev" url="/nl/jsp/soaprouter.jsp" includeDead="false"/>
  </host>
</netconf>
```

>[!NOTE]
>
>U kunt verschillende configuraties opgeven door een achtervoegsel toe te voegen aan de **netconf.xml** bestand, bijvoorbeeld **netconf-dev.xml**, **netconf-prod.xml**, enz. Dan specificeer de configuratie voor het uitvoeren van netreport in **netreport.bat** of **netreport.sh** bestanden toevoegen **$JAVA_HOME/bin/java netreport dev** of **@%JAVA_HOME%binjava netreport-proxy** bijvoorbeeld.

>[!IMPORTANT]
>
>Voor de **toezicht** -operator om te werken, moet de machine waarop het netreport wordt uitgevoerd zich in een beveiligingszone bevinden die zich in **sessionTokenOnly** in. Als er geen vertrouwd IP-masker is opgegeven voor deze operator, moet de beveiligingszone zich ook binnen **allowEmptyPassword** en **allowUserPassword** in.

#### Element &#39;Eigenschappen&#39; {#properties--element}

Dit element wordt gebruikt om de configuratie van e-mailberichten te vullen, dat wil zeggen

* **mailServer**: SMTP-server gebruikt om e-mailberichten te verzenden (bijvoorbeeld: smtp.domain.net).
* **mailFrom**: e-mailadres van de afzender van het rapport (bv.: monitoring@domain.net).
* **receivingList**: de lijst met e-mailadressen van ontvangers die toezicht houden. Adressen moeten worden gescheiden door komma&#39;s (geen spaties).
* &#39;**nacht** De modus &#39; (optioneel) wordt gebruikt om te voorkomen dat e-mailberichten tussen de opgegeven tijdsperiode worden verzonden. In plaats daarvan worden de gegevens geconsolideerd en wordt een e-mail over de activiteit van de nacht verzonden na de eindtijd (standaard 7:00).
* De **buildRange** Met subelement (optioneel) kunt u een minimum- en maximumbuildnummer opgeven. Er wordt een fout gegenereerd voor alle computers waarvan het buildnummer niet binnen dit bereik valt

   ```
   <buildRange minimum="0000" maximum="9999"/>
   ```

* U kunt een **`<sla>`** (facultatief) subelement in **eigenschappen** element. Een logboekdossier zal worden geproduceerd telkens als netreport wordt uitgevoerd. De naam van het bestand bevat de configuratienaam en de datum en tijd, bijvoorbeeld **dev_06_12_13_16_47_05.tmp**. Het bestand bevat de volgende informatie: instantienaam, machinenaam, ernstniveau, (0 tot 3, van minst kritiek aan meest kritiek), datum (timestamp formaat), tijd die (in milliseconden) tussen de vraag en de reactie, de gebruikte dienst (http, ncs, ncsex, redir) wordt verstreken. Deze informatie wordt gescheiden door lusrekentekens en lijnonderbrekingen aan het eind van elke dienst.

>[!NOTE]
>
>De **persistHtmlFile** kenmerk met de waarde &quot;true&quot; op het tabblad **`<property>`** -element wordt gebruikt om de meest recente monitorstatus in het bestand op te nemen **netreport.md**. Dit bestand wordt opgeslagen in de installatiemap.

#### Instantie-element {#instance--element}

Met dit element kunt u verschillende computers (hosts) opnieuw groeperen in dezelfde instantie. De instantienamen worden weergegeven in het eerste deel van de e-mail met controle. U kunt op de naam van een instantie klikken om de details van elke computer te openen.

```
instance name="instanceName" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **name**: instantienaam die in het eerste deel van de e-mail zal verschijnen.
* **receivingList** (optioneel): Hiermee kunt u via e-mail een monitoringrapport over een bepaald exemplaar verzenden.

#### Element &#39;Host&#39; {#host--element}

Dit element vormt de controle van een bepaalde server op de gastheer, d.w.z.

* **name**: naam van de te controleren machine.
* **alias** (optioneel): naam van de bewaakte computer zoals deze in het rapport wordt weergegeven.
* **sessionToken**: biedt aanmeldingsverificatie via een geautoriseerd sessietoken.

   Om het zittingsteken te vormen, selecteer **toezicht** in de Adobe Campaign-console. In de **Toegangsrechten** op, geeft u de IP-adressen op van de computers die gemachtigd zijn om dit exemplaar te controleren. U kunt dan verbinding maken met de controlepagina vanaf deze computers met behulp van de **toezicht** id en zonder een wachtwoord op te geven.

   ![](assets/ncs_operators_rights_02.png)

* **kritiekLevel** (optioneel): Hiermee kunt u fouten sorteren en weergeven op ernst. Mogelijke waarden zijn &#39;0&#39; (alle weergegeven niveaus), &#39;1&#39; (alleen hoge en kritieke fouten weergegeven) en &#39;2&#39; (alleen kritieke fouten weergegeven). Als dit kenmerk niet wordt opgegeven, worden alle foutniveaus weergegeven.
* **filter** (optioneel): Hiermee kunt u bepaalde workflowfouten uitsluiten, bijvoorbeeld **filter=&quot;wkf;wkf1&quot;**. Workflowlabels moeten worden gescheiden door puntkomma&#39;s.

#### Subelementen {#sub-elements}

* **tcp**: controleert of de server omhoog of omlaag is. U moet een poortnummer invoeren.
* **http**: controleert of de server van het Web bestaat (toepassingsserver is operationeel).
* **ncs**: controleert de processen op de instantie ingegaan in het &quot;instantie&quot;attribuut (werkschemafouten, geheugengebruik, enz.). De **inbegrepen** (verplicht) geeft u de optie om dode processen weer te geven (&#39;true&#39; of &#39;false&#39; waarden).
* **redir**: controleert het volgen.

In de meeste gevallen is alleen de **ncs** en **redir** subelementen kunnen worden bewaard.

In elk geval kunnen bepaalde knooppunten worden overbelast in de subelementen (bijvoorbeeld het knooppunt **port=75** om de haven te overladen die voor de http, ncs of redir verbinding wordt gebruikt):

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

In de **ncs**, **redir** en **http** subelementen kunt u toevoegen **isSecure** (optioneel) om aan te geven of het HTTPS-protocol wel of niet moet worden gebruikt (&#39;true&#39; of &#39;false&#39; waarden). Als dit kenmerk niet wordt opgegeven, wordt het http-protocol gebruikt.

### Het vormen van het netreport.bat of netreport.sh- dossier {#configuring-the-netreport-bat-or-netreport-sh--file}

Om het te vormen, geef dit dossier uit en wijs op welke folder JRE of JDK geïnstalleerd is.

### Bewaking starten {#launching-monitoring}

Als u de controle wilt starten, voert u de **netreport.bat** of **netreport.sh** op regelmatige intervallen via een script. Een rapport wordt verzonden na de eerste uitvoering, en dan slechts in het geval van een verandering van status.

### Bewaking van tests {#testing-monitoring}

Als u de controle wilt testen, voert u de opdracht **netreport.bat** of **netreport.sh** bestand.

Er wordt een e-mail verzonden naar de ontvangers die zijn opgegeven in het dialoogvenster **receivingList** van de **netconf.xml** bestand.
