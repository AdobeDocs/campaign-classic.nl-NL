---
product: campaign
title: Releases van 2020
description: Meer informatie over Campaign Classic 2020-releases
feature: Overview
role: User
level: Beginner
exl-id: e2eb7e04-faaa-4df0-913d-471c291eeb03
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '6601'
ht-degree: 73%

---

# Releases van 2020{#release-2020}

![](../../assets/v7-only.svg)


## Release 20.3{#release-20-3}

### ![](assets/do-not-localize/red_2.png) Release 20.3.3 - build 9234 {#release-20-3-3-build-9234}

_11 januari 2021_

* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-27777)
* Oplossing van een regressieprobleem bij het genereren van de broadlog waarbij het MTA-proces kon crashen.

### ![](assets/do-not-localize/red_2.png) Release 20.3.1 - build 9228 {#release-20-3-1-build-9228}

_27 oktober 2020_

>[!CAUTION]
>
> * Deze release wordt geleverd met een nieuw verbindingsprotocol: als u verbinding maakt met Campaign via de Adobe Identity Service (IMS), is een upgrade verplicht voor zowel de Campaign-server als de clientconsole om na **30 juni 2021** verbinding te kunnen maken met Campaign. [Meer informatie](../../technotes/using/ims-updates.md)
> * Deze release wordt geleverd met een [oplossing voor een beveiligingsprobleem](https://helpx.adobe.com/nl/security/products/campaign/apsb21-04.html): een upgrade is verplicht om de beveiliging van uw IT-omgeving te versterken.
> * Als u via oAuth-verificatie de Experience Cloug Triggers-integratie gebruikt, moet u overstappen op Adobe I/O zoals [op deze pagina](../../integrations/using/configuring-adobe-io.md) wordt beschreven. De verouderde oAuth-authentificatiemodus met Campaign [is beëindigd](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) in **september 2021**. Gehoste omgevingen profiteren van een verlenging tot **23 februari 2022**. Als klant op locatie of hybride klant neemt u contact op met de klantenservice van Adobe om de ondersteuning uit te breiden tot februari 2022. U moet de [AppID van de OAuth-applicatie](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) aan Adobe verstrekken.


**Nieuwe functies**

<table> 
<thead>
<tr> 
<th> <strong>Verbeteringen voor iOS-pushmeldingen</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Wanneer u uw mobiele app integreert met Campaign, moet u uw communicatie met de APNs (Apple Push Notification-service) beveiligen. U kunt verificatie op basis van een certificaat of op basis van een token gebruiken.
</p>
<p>Deze twee verificatiemodi zijn nu beschikbaar voor mobiele iOS-apps in Campaign Classic:
</p>
<ul> 
<li><p>Verificatie op basis van token (aanbevolen): deze verificatiemodus is gebaseerd op een .p8-bestand. Deze verificatiemodus gaat sneller, aangezien elk verzoek aan APN’s het token bevat. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Meer informatie</a></p></li>
<li><p>Verificatie op basis van certificaat: deze verificatiemodus is gebaseerd op een .p12-bestand. Voor elke app is een afzonderlijk certificaat vereist. Dit certificaat wordt door Apple geleverd via uw ontwikkelaarsaccount. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Meer informatie</a></p></li> 
</ul>
<p>Leer in de <a href="../../delivery/using/configuring-the-mobile-application.md">gedetailleerde documentatie</a> hoe u een verificatiemodus selecteert in Campaign.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Verbeteringen voor Android-pushmeldingen</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p><a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">Android-pushmeldingen zijn verbeterd en bieden nu ondersteuning voor de FCM HTTP v1-API voor Android-pushkanaalverificatie.</a> </p>
<p>Met de nieuwe ondersteunde API-versie kunt u nu FCM-meldingsberichten verzenden die uitgebreide mogelijkheden voor pushmeldingen bieden. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Meer informatie</a></p> 
<p>Ontdek in <a href="../../delivery/using/configuring-the-mobile-application-android.md">deze sectie</a> hoe u FCM HTTP v1 API voor Android in Adobe Campaign configureert.</p>
</td> 
</tr> 
</tbody> 
</table>

**Verbeterde beveiliging**

* Beveiligd laden van bibliotheken: ter bescherming tegen dll-voorafladingsaanvallen laadt Campaign Windows-dll’s nu alleen vanaf het Windows-standaardsysteempad naar dll’s tijdens het laden van de Campaign Client (nlclient). [Meer informatie](https://support.microsoft.com/nl-nl/topic/bibliotheken-veilig-laden-om-te-voorkomen-dat-dll-aanvallen-vooraf-worden-geladen-d41303ec-0748-9211-f317-2edc819682e1) (NEO-24147)
* Er is een beveiligingsprobleem verholpen ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-25661)
* Er is een probleem verholpen dat optrad tijdens het verwerken van GDPR-verzoeken om toegang tot persoonsgegevens waardoor records niet konden worden verwijderd uit aangepaste tabellen met een relatie op het tweede niveau tot de tabel met ontvangers. (NEO-25967)
* Er is een beveiligingsprobleem verholpen waarbij API-aanroepen werden gebruikt van gebruikers die geen beheerder zijn tijdens een poging om Adobe Experience Manager-sjablonen te synchroniseren. (NEO-23487)

**Compatibiliteitsupdates**

De volgende systemen worden nu ondersteund met Campaign:
* iOS 14
* PostgreSQL 12
* CentOS/RedHat 8
* MSSQL2019

Ontdek meer in de [Campaign-compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

**Verouderde functies**

De volgende functies zijn afgeschaft in 20.3:

* Het demdex-domein dat werd gebruikt voor het importeren en exporteren van doelgroepen naar de Adobe Experience Cloud is afgeschaft. Als u het demdex-domein voor uw externe import/export-accounts gebruikt, moet u uw implementatie dienovereenkomstig aanpassen. [Meer informatie](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* De Triggers-integratieverificatie die oorspronkelijk was gebaseerd op de oAUTH-verificatieset-up voor toegang tot de pipeline is nu gewijzigd en verplaatst naar Adobe I/O. [Meer informatie](../../integrations/using/configuring-adobe-io.md)

Meer informatie vindt u op de pagina [Afgeschafte en verwijderde functies](../../rn/using/deprecated-features.md).

**Verbeteringen**

* Er zijn verschillende verbeteringen aangebracht in de **clientconsole**:
   * Het verbindingsprotocol is bijgewerkt en aangepast aan het nieuwe IMS-verificatiemechanisme. De upgrade van de server- en clientconsole is verplicht om na 30 juni 2021 verbinding te kunnen maken.
   * Om incompatibiliteit met bepaalde GPO-regelbeperkingen voor internetbeveiliging te voorkomen is het aanmeldingsscherm van de Campaign-clientconsole vervangen door een ingebouwd standaard Windows-formulier.
   * Er is een probleem verholpen met het kopiëren/plakken van activiteiten in een workflow op een 64-bits clientconsole. (NEO-27635)
   * In het menu **Info** is informatie toegevoegd om 64- en 32-bitsconsoles van elkaar te onderscheiden.
* De workflow-id wordt nu weergegeven in de logboeken wanneer u een workflow hervat. Zo kunt u beter bepalen welke workflow is hervat.
* Er is een nieuw permanent cookie geïntroduceerd: nllastdelid. In dit cookie (anders dan UUID230) wordt deliveryId opgeslagen. Wanneer er geen sessiecookie aanwezig is, wordt de broadloginformatie uit de deliveryId in dit cookie gehaald.
Deze wijziging verhelpt een probleem dat optrad als de browsersessie was afgelopen: het sessiecookie met deliveryId en broadlogId werd verwijderd. Zonder deliveryId kon de broadloginformatie niet worden gevonden en ontbrak de informatie van de trackingtabel bij permanente tracking (laatste levering).
Meer informatie over cookies vindt u in [deze sectie](../../platform/using/privacy-and-recommendations.md#cookies).
* Verbeterde doorvoerprestaties van grote leveringen met leverbaarheidsserver door het MTA-proces opnieuw te starten vóór verzending van de levering.

**Overige wijzigingen**

* Wanneer u een relatief pad gebruikt voor SFTP, worden `~/`-tekens niet meer automatisch toegevoegd. Zo nodig kunt u handmatig `~/`-tekens aan het pad toevoegen, maar het wordt aangeraden een **absoluut pad** te gebruiken.
* De Windows NT-verificatie is verwijderd uit de beschikbare verificatiemethodes bij het configureren van een nieuwe database met een Microsoft SQL Server. [Meer informatie](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* De workflow voor het opschonen van databases is geoptimaliseerd voor Teradata om de prestaties te verbeteren. (NEO-19959)
* Het foutbericht dat werd weergegeven bij het invoegen van een afbeelding uit Adobe Target, waarbij de naam van de tenant leeg was in het externe account, is verbeterd.
* In leveringseigenschappen is de naam van de optie **[!UICONTROL Archive emails]** gewijzigd in **[!UICONTROL Email BCC]**.
* Om de robuustheid te verbeteren worden selectAll-query’s met ongeldige knooppunten nu afgewezen. Als u de controle moet uitschakelen en moet teruggaan naar de vorige functionaliteit, kunt u XtkSecurity_Disable_QueryCheck op 0 zetten.
* De negatieve ondersteuning voor het ID-bereik is toegevoegd voor de reeks nmsBroadlogId. Deze build past de min_value van de nmsBroadlogId-reeks aan om het negatieve bereik op te nemen. Als u een strikt gebruik-case hebt die geen negatieve id&#39;s toestaat, moet u de min_value van de reeks terugzetten op 1.

**Technische ontwikkelingen**

Tomcat is bijgewerkt van versie 7 (7.0.103) naar versie 8 (8.5.57).

De map `tomcat-7` is vervangen door een map `tomcat-8`.

In Windows _zijn iis_neolane_setup.vbs_ en _apache_neolane.conf_ nu geïnstalleerd in de map `conf` (in plaats van `tomcat-7/conf` zoals eerder).

In Linux is _apache_neolane.conf_ nu geïnstalleerd in de map `conf`.

**Patches**

* Er is een probleem verholpen waardoor leveringsstatistieken niet opnieuw konden worden berekend.
* Er is een probleem verholpen waarbij een foutbericht werd weergegeven tijdens het uploaden van een CSV-bestand bij het gebruik van een Campaign Classic 9080-build die was verbonden met een server die gebruikmaakte van een oudere build. (NEO-23218)
* Er is een probleem verholpen waarbij soms een foutbericht werd weergegeven tijdens het configureren van de CRM Microsoft Dynamics-wizard voor een extern account. Dit kwam door een compatibiliteitsprobleem met de nieuwste versie van de MS Dynamics CRM-API. (NEO-24528)
* Er is een probleem verholpen waardoor u opzoekrecords (data die bestaan uit records met vreemde sleutels die zijn verbonden met andere tabellen) niet kon exporteren van Campaign Classic naar Microsoft Dynamics met de CRM-connector. (NEO-23864)
* Er is een probleem verholpen waardoor Microsoft Dynamics-data niet konden worden opgehaald als de optie **Automatische index** was ingeschakeld in de CRM-connector. (NEO-25981)
* Er is een probleem verholpen met IMS-verificatie waardoor verbindingen soms geopend bleven, zelfs als ze waren beëindigd. Beëindigde verbindingen worden nu automatisch afgesloten om een opeenstapeling van verbindingen en het verbruik van systeembronnen te vermijden. (NEO-25996)
* Er is een probleem verholpen waarbij geen foutbericht werd weergegeven wanneer de synchronisatie van Adobe Experience Manager-content voor een levering mislukte als gevolg van een onjuiste configuratie van het externe account (onjuist account of wachtwoord). Er wordt nu een bericht weergegeven bij een fout, zodat u het probleem gemakkelijker kunt identificeren. (NEO-25586)
* Er is een probleem verholpen dat optrad bij het selecteren van het bewerkingstype **Bijwerken** in de activiteit **Data bijwerken**. Als de bij te werken data onjuist waren, meldde de workflow een fout en mislukte. Bij onjuiste data zal de workflow niet mislukken en worden de records opgeslagen in een uitgaande overgang **Afwijzingen**. (NEO-23794)
* Er is een probleem verholpen waardoor workflows met subworkflows niet konden functioneren. (NEO-24036)
* Er is een probleem verholpen met de bewerking van een campagnesjabloonbeschrijving waardoor de knop **Opslaan** niet werd weergegeven bij het kopiëren en plakken van symbolen zoals bijvoorbeeld Japanse tekens. (NEO-27071)
* Er is een probleem verholpen waardoor u de trackingserver niet kon wijzigen in de wizard Instantieconfiguratie.
* Er is een probleem verholpen waardoor de beschrijving van een campagne of campagnesjabloon niet kon worden opgeslagen wanneer er buiten het venster werd geklikt voordat op de knop **Opslaan** was geklikt. (NEO-27449)
* Er is een probleem verholpen waardoor de technische workflow **Aantal actieve factureringsprofielen** (billingActiveContactCount) niet werkte. Dit kon gebeuren wanneer een koppeling was uitgevoerd op een berekend veld in een schema-extensie. Er werd een grote hoeveelheid data gemaakt waardoor de database geen tijdelijke ruimte meer had. (NEO-24062)
* Er is een probleem verholpen met de activiteit **Data laden (bestand)**, waardoor Japanse tekens niet konden worden geïmporteerd uit TXT- en CSV-bestanden als deze aan het einde van het bestand waren geplaatst. (NEO-24957)
* Er is een probleem verholpen met doorlopende leveringen waardoor de velden **Analyse gestart** en **Analyse voltooid** niet correct konden worden ingevuld. (NEO-20755)
* Er is een probleem verholpen waarbij soms een foutbericht werd weergegeven wanneer werd geprobeerd sms-berichten weer te geven na een query op een ander schema dan **Ontvanger** (nms:recipient). (NEO-27517)
* Er is een probleem verholpen met het gebruik van de Snowflake FDA-connector. Een gebruiker met Snowflake FDA-toegangsnaamrechten kon geen query uitvoeren op een Snowflake-schema. Er werd een fout van het type ‘Wachtwoord niet gevonden’ in de logboeken weergegeven. (NEO-23851)
* Er is een probleem verholpen met het gebruik van een FDA-connector dat optrad wanneer de gekoppelde FDA-schemanaam een subtekenreeks was van een elementnaam van het huidige schema. Dit gebeurde bijvoorbeeld wanneer het FDA-schema ‘cust’ was en een van de elementen binnen het ontvangerschema ‘customer’ was. Bij het ophalen van de kolom in het element ‘customer’ en het toevoegen van een kolom uit het FDA-schema ‘cust’ ontbrak de waarde voor de lokale kolom. (NEO-20193)
* Er is een probleem verholpen in workflows tijdens het ophalen van records uit een externe database en het invoegen van records in de Campaign-database. (NEO-26359)
* Er is een probleem verholpen in de technische workflow **Evenementstatus bijwerken**: voor het matchen van het formaat van binnenkomende corresponderende velden in de activiteit **Leveringsstatistieken** werd het formaat van drie bestemmingsvelden in de activiteit **Leveringsstatistieken bijwerken** gewijzigd van 32 in 64 bits. (NEO-11557) Meer informatie over de workflow **Evenementstatus bijwerken** vindt u in [deze sectie](../../workflow/using/about-technical-workflows.md).
* Er is een probleem verholpen in het rapport **Geschiedenis van gebeurtenissen in het Berichtencentrum** dat scriptfouten veroorzaakte bij het toepassen van filters, waardoor filteren op datumbereik onmogelijk was. (NEO-23365)
* Er is een interferentieprobleem verholpen tussen de technische workflows **Campaign-taken** (operationMgt) en **Voorvertoning** (forecasting). Dit gebeurde wanneer geplande leveringen in de status ‘Target gereed’ of ‘Gereed voor levering’ bleven staan. (NEO-20819)
* Er is een probleem met XML-parsering verholpen waarbij de XML-id niet aanwezig was in het veld mdata in xtkOperator. Dit veroorzaakte een postupgradefout. (NEO-26113)
* Er is een probleem verholpen met het gebruik van de activiteit **Bestandsoverdracht** die gekoppeld was aan een extern Azure-account, versleuteld in SSL, waar de verbinding werd gemaakt met HTTP in plaats van met HTTPS. (NEO-26720)
* Er is een probleem verholpen met een MSSQL-database waarbij een fout kon optreden met de procedure up_updatestats tijdens de opschoningsworkflow.
* Er is een probleem verholpen met een crash die optrad tijdens het afsluiten van het webproces als er nog Interaction-aanvragen werden verwerkt. (NEO-26447)
* Er is een probleem verholpen waarbij de functie **NoNull** in Oracle DB niet meer werkte na upgrade 9032. (NEO-26488)
* Er is een probleem verholpen waarbij de trackingworkflow mislukte na upgrade 9171 als het LINEV2-pakket was geïnstalleerd zonder het Berichtencentrum-pakket.
* Er is een probleem verholpen met schaalbaarheid waarbij de verbindingspool niet kon worden verhoogd tot het gewenste aantal verbindingen omdat de tekenreeks voor databaseverbindingen voor het kenmerk ‘APP’ uiteindelijk een ongeldige waarde kreeg. (NEO-25105)
* Er is een probleem verholpen op het niveau van proxyconfiguratie waardoor u zich na de laatste Windows 10-update niet kon aanmelden bij Adobe Campaign. (NEO-27813)
* Er is een probleem verholpen waarbij ongewenste URL’s zichtbaar werden in de geleverde e-mails na het importeren van HTML-sjablonen met trackingkoppelingen. (NEO-25909)
* Er is een probleem verholpen waarbij de server vastliep bij het weergeven van de doeldata van de rest van een **Splitsen**-activiteit in een workflow.
* Er is een probleem verholpen waarbij de server vastliep door geheugenbeschadiging te voorkomen tijdens het opschonen van de expressieparser. (NEO-26856)
* Er is een probleem verholpen in de verrijkingsactiviteit waarbij niet-beheerders instantievariabelen definieerden. (NEO-25653)
* Oplossing voor een regressie die de export van workflowgegevens naar een FDA-database kon blokkeren (Teradata, Snowflake).

## Release 20.2{#release-20-2}

### ![](assets/do-not-localize/limited_2.png) Release 20.2.5 - build 9188 {#release-20-2-5-build-9188}

_15 april 2021_

* Er is een probleem met een regressie van de clientconsole opgelost die tot permanente foutberichten op het IMS-verbindingsscherm leidde. (NEO-34821)

**Alleen de console-upgrade is verplicht. Er is geen serverupgrade vereist.**

>[!NOTE]
>
> Maak verbinding met [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) om de nieuwe versie te downloaden. [Op deze pagina ](../../installation/using/client-console-availability-for-windows.md) leert u hoe u de console-update aan alle eindgebruikers kunt voorstellen.

_31 maart 2021_

**Verbeteringen**

* Er is een verbetering aangebracht om te voorkomen dat er bij ongeldige zeepoproepen crasht. Hierdoor werkt de instantie mogelijk niet meer wanneer wordt geprobeerd specifieke complexe query&#39;s uit te voeren. (NEO-28796, NEO-30553)
* Oplossing voor een regressie die ervoor zorgde dat SMS-leveringen met TLS niet werden verzonden vanwege de verificatie van de hostnaam. (NEO-29581)
* Probleem verholpen waardoor ondertekende koppelingen voor bijhouden van handtekeningen niet konden werken op bepaalde e-mailclients. (NEO-28414, NEO-29615)
* Probleem verholpen met een id-reeks voor bijhouden bij het gebruik van tags voor webApp die conflicten kunnen veroorzaken met dubbele id&#39;s. (NEO-27931)
* Probleem verholpen waarbij actieve workflows werden gestopt door het dagelijkse opnieuw opstarten van de wfserver. (NEO-30047)
* Er is een beveiligingsprobleem verholpen waarbij API-aanroepen werden gebruikt van gebruikers die geen beheerder zijn tijdens een poging om Adobe Experience Manager-sjablonen te synchroniseren. (NEO-32389, NEO-23487)
* Probleem verholpen waarbij de console vastliep als een leveringsdialoogvenster wordt gesloten voor een levering die met een sjabloon is gemaakt. (NEO-31547)
* Probleem verholpen dat optrad tijdens het maken en opslaan van een levering in het dialoogvenster **Doelstelling en workflow** tabblad van een campagne: de voorvertoning zou mislukken met de volgende fout. (NEO-29440)
* Probleem verholpen waarbij Tomcat 8.5 ongeldige antwoorden verzendt die fouten in Transactieberichten logboeken veroorzaakten. (NEO-30858)
* Oplossing voor een regressieprobleem dat geheugenbeschadiging in extern draadbeheer veroorzaakt en de prestaties beïnvloedt.
* Probleem opgelost waarbij de factureringsworkflow mogelijk mislukte bij het gebruik van een aangepaste doeltoewijzing. De primaire sleutel van het aangepaste schema wordt opgeslagen in de kolom &quot;sourceId&quot;, die alleen gehele getallen toestaat. Het staat nu geheel zowel als koordwaarden toe. (NEO-25914, NEO-28146)
* Er is een regressie opgelost die verhinderde dat bepaalde onderdelen van de console konden worden gebruikt, zoals de datumkiezer en afbeeldingsbeheer in verzendingen. (NEO-31453)

### ![](assets/do-not-localize/red_2.png) Release 20.2.4 - build 9187 {#release-20-2-4-build-9187}

_15 april 2021_

* Er is een probleem met een regressie van de clientconsole opgelost die tot permanente foutberichten op het IMS-verbindingsscherm leidde. (NEO-34821)
* Er is een regressie opgelost die verhinderde dat bepaalde onderdelen van de console konden worden gebruikt, zoals de datumkiezer en afbeeldingsbeheer in verzendingen. (NEO-31453, NEO-31454)

**Alleen de console-upgrade is verplicht. Er is geen serverupgrade vereist.**

>[!NOTE]
>
> Maak verbinding met [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) om de nieuwe versie te downloaden. [Op deze pagina ](../../installation/using/client-console-availability-for-windows.md) leert u hoe u de console-update aan alle eindgebruikers kunt voorstellen.

_22 december 2020_

>[!CAUTION]
>
> * Deze release wordt geleverd met een nieuw verbindingsprotocol: als u verbinding maakt met Campaign via de Adobe Identity Service (IMS), is een upgrade verplicht voor zowel de Campaign-server als de clientconsole om na **30 juni 2021** verbinding te kunnen maken met Campaign.  [Meer informatie](../../technotes/using/ims-updates.md)
> * Deze release wordt geleverd met een [oplossing voor een beveiligingsprobleem](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): een upgrade is verplicht om de beveiliging van uw IT-omgeving te versterken.
> * Als u via oAuth-verificatie de Experience Cloug Triggers-integratie gebruikt, moet u overstappen op Adobe I/O zoals [op deze pagina](../../integrations/using/configuring-adobe-io.md) wordt beschreven. De verouderde oAuth-authentificatiemodus met Campaign [is beëindigd](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) in **september 2021**. Gehoste omgevingen profiteren van een verlenging tot **23 februari 2022**. Als klant op locatie of hybride klant neemt u contact op met de klantenservice van Adobe om de ondersteuning uit te breiden tot februari 2022. U moet de [AppID van de OAuth-applicatie](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) aan Adobe verstrekken.


**Verbeteringen**

* Het verbindingsprotocol is bijgewerkt en aangepast aan het nieuwe IMS-verificatiemechanisme.
* De de integratieauthentificatie van trekkers oorspronkelijk gebaseerd op de authentificatie van de AUTH aan toegangspijplijn is veranderd en aan Adobe I/O verplaatst. [Meer informatie](../../integrations/using/configuring-adobe-io.md)
* Nu het [verouderde binaire protocol voor iOS APN’s niet meer wordt ondersteund](https://developer.apple.com/news/?id=c88acm2b), zijn alle instanties die dit protocol gebruiken, bijgewerkt naar het HTTP/2-protocol tijdens de postupgrade.
* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-27777)
* Probleem verholpen waarbij de SMPP-connector werd gedeactiveerd na een verbindingsfout, waardoor andere SMS-leveringen niet werden verzonden en prestatieproblemen optraden. (NEO-28609)
* Er is een probleem verholpen waarbij de server vastliep door geheugenbeschadiging te voorkomen tijdens het opschonen van de expressieparser. (NEO-26856)
* Er is een probleem verholpen waarbij de server vastliep bij het weergeven van de doeldata van de rest van een **Splitsen**-activiteit in een workflow.
* Er is een probleem verholpen waarbij soms een foutbericht werd weergegeven wanneer werd geprobeerd sms-berichten weer te geven na een query op een ander schema dan **Ontvanger** (nms:recipient). (NEO-27517)
* Probleem verholpen bij het indienen van een HTTPS-verbindingsaanvraag met het poortnummer dat expliciet in de hostnaam is gedefinieerd, het aanroepen is mislukt vanwege een certificaatfout. (NEO-29146)
* Probleem opgelost in POSIX-draadbeheer dat grote core dump-bestanden heeft gegenereerd voor de marketinginstantie. (NEO-28117, NEO-29281)
* Correctie van problemen die ertoe kunnen leiden dat het webproces vastloopt bij het voorbereiden van leveringen of bij terugkerende voorvertoning van levering. (NEO-27790, NEO-27517)
* Probleem verholpen waarbij leveringen of het verzenden van bewijzen mislukten wanneer deze door een niet-beheerder werden geactiveerd. (NEO-28597)

![](assets/do-not-localize/cp-icon.png) **Release van nieuw Configuratiescherm in oktober** met domeinconfiguratie met CNAME-records en nieuwe mogelijkheden voor databasecontrole. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=nl).

### ![](assets/do-not-localize/red_2.png) Release 20.2.3 - build 9182 {#release-20-2-3-build-9182}

_11 september 2020_

* Oplossing voor een regressie die ertoe leidde dat een leveringsvoorbereiding werd geblokkeerd als gevolg van één foutieve functie in het leveringsonderdeel, wat tot geheugenoverbelasting leidde. (NEO-27346)
* Probleem verholpen met een post-upgrade waarbij Apache en de webserver werden uitgeschakeld voordat de webapplicatie opnieuw werd gepubliceerd. (NEO-27155)
* Oplossing voor een regressie op het sjabloonbeheer van HTML die ertoe leidde dat URL&#39;s werden bijgehouden omdat tabs onjuist werden geïnterpreteerd. (NEO-25909)
* Probleem verholpen met de opschoningsworkflow voor databases die zou kunnen mislukken als gevolg van een niet-beheerde gegevensbron. (NEO-23160, NEO-23364)
* Tijdens de opschoningsworkflow worden nu verlopen lijsten in batches van 100 verwijderd in plaats van één voor één.
* Oplossing voor een regressie waardoor u niet de interne naam van een extern account kon wijzigen. (NEO-27323)
* Oplossing voor een regressie tijdens een post-upgrade die een onjuiste start van nlserver (foutenlogboeken) veroorzaakte.
* Het updatebeheer voor gedeeld geheugen is verbeterd. De extra stappen die zijn vereist in 20.2, zijn niet meer nodig.

### ![](assets/do-not-localize/red_2.png) Release 20.2.2 - build 9180 {#release-20-2-2-build-9180}

_woensdag 22 juli 2020_

* Er is een probleem verholpen waarbij tracking niet werkte als de handtekeningfunctie was uitgeschakeld. (NEO-26411)
* Probleem verholpen waarbij niet-ondertekende koppelingen van gepersonaliseerde domeinen werden geblokkeerd terwijl ze moesten worden toegestaan. (NEO-25210)
* Er is een probleem verholpen waardoor u tracking-URL’s niet kon openen of er niet op kon klikken bij gebruik van bepaalde oudere versies van Outlook. (NEO-25688)
* Probleem verholpen waarbij URL&#39;s van spiegelpagina&#39;s onjuist werden gedefinieerd in e-mailleveringen (vanwege onjuiste ASCII-tekenbesturing). (NEO-26084)
* Probleem verholpen met de codering van URL-beheer in de service voor antiphishing. (NEO-25283)
* Er is een probleem verholpen waarbij de tracking van URL’s met fragmenten in personalisatieparameters (ankerlabels met pondteken) niet werkte. (NEO-25774)
* Er is een probleem verholpen met tracking bij gebruik van specifieke aangepaste trackingformules. (NEO-25277)
* Er is een probleem verholpen waardoor tracking van ‘berichtklikken’ niet kon worden uitgevoerd (iOS- en Android-pushmeldingen). (NEO-25965)
* Oplossing voor een regressie die invloed had op berekende velden in een workflow waardoor de workflow mislukte. (NEO-25194)
* Oplossing voor een regressie waardoor het direct kunnen maken van webtracking-URL’s niet werkte. (NEO-20999)
* Oplossing voor een regressieprobleem met standaard leveringsrapporten die afgekapt leken te zijn bij het exporteren naar PDF. (NEO-25757)
* Probleem verholpen waarbij de implementatiewizard vastliep.
* Probleem verholpen waarbij de workflow voor het melden van aanbiedingen niet goed kon werken nadat een post-upgrade was uitgevoerd.
* De iOS HTTP2-connector is verbeterd (updates van derden en foutbeheer). (NEO-25904, NEO-25903)
* De lijst jarsToSkip in catalina.properties is bijgewerkt om de verwijzing naar een jar-bestand dat niet meer werd gebruikt, te verwijderen (iOS-meldingen).
* Probleem verholpen waarbij de leveringsvoorbereiding na het uitvoeren van de post-upgrade werd geblokkeerd.
* Na de overstap naar het nieuwe ID-mechanisme voor reeksen worden alle webapplicaties waarmee de tabel met ontvangers worden bijgewerkt, opnieuw gepubliceerd tijdens de post-upgrade.
* Een mogelijke XSS-kwetsbaarheid in de leveringscontent is verholpen. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **Release van nieuw configuratiescherm in juni** met controle van actieve profielen, controle van de leverbaarheid van subdomeinen en beheer van GPG-sleutels. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html).

### ![](assets/do-not-localize/red_2.png) Release 20.2.1 - build 9178 {#release-20-2-1-build-9178}

_8 juni 2020_

**Nieuwe functies**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Ondersteuning voor emoticons</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Bij het ontwerpen van een bericht in Campaign kunt nu gemakkelijk emoticons invoegen in de hoofdtekst van het bericht met behulp van een speciale knop. U kunt ze ook toevoegen aan de onderwerpregel van de e-mail. U kunt de lijst met beschikbare emoticons in de interface aanpassen.</p>
    <p>Raadpleeg de <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">gedetailleerde documentatie</a> voor meer informatie over het toevoegen van emoticons. Leer <a href="../../delivery/using/customizing-emoticon-list.md">in deze sectie</a> hoe u de lijst met emoticons kunt aanpassen.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>U kunt uw instantie van Campaign nu verbinden met uw externe database van Azure Synapse. Deze verbinding wordt beheerd via een nieuw extern account.</p>
    <p>Azure Synapse is alleen beschikbaar voor hybride en on-premise omgevingen. Raadpleeg de <a href="../../installation/using/configure-fda-synapse.md">gedetailleerde documentatie</a> voor meer informatie.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Thaise en Braziliaanse privacywetten</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>De Thaise wet inzake de bescherming van persoonsgegevens (PDPA) is de nieuwe privacywet die de vereisten inzake databescherming voor Thailand harmoniseert en moderniseert. </p>
   <p>De Braziliaanse wet inzake gegevensbescherming (Lei Geral de Proteção de Dados, LGPD) wordt begin 2021 van kracht voor alle bedrijven die in Brazilië persoonsgegevens verzamelen of verwerken.</p>
   <p>Deze voorschriften zijn van toepassing op Adobe Campaign-klanten die data bewaren voor in deze landen wonende betrokken personen. Naast de privacymogelijkheden die reeds beschikbaar zijn in Campaign (met inbegrip van toestemmingsbeheer, instellingen voor dataretentie en gebruikersrollen), grijpen wij deze kans om extra mogelijkheden op te nemen om u te helpen uw gereedheid voor PDPA en LGPD te vergemakkelijken:</p>
   <ul> 
     <li><p>Recht op toegang en recht op verwijdering: wij gebruiken de mogelijkheden die voor AVG en CCPA zijn toegevoegd. <a href="https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html">Meer informatie</a></p></li> 
     <li> <p>Wanneer u een aanvraag om toegang tot persoonsgegevens maakt met de Campaign-interface of -API, selecteert u nu het type <strong>Regulation</strong>: PDPA, LGPD, AVG, CCPA. <a href="https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Meer informatie</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* Alle klanten hebben standaard een betere beveiliging voor het bijhouden van koppelingen in e-mails. Er is een extra, verbeterde beveiligingsfunctie beschikbaar die kan worden ingeschakeld door contact op te nemen met de klantenservice. Meer informatie over de functie en de stappen die niet-gehoste klanten moeten uitvoeren, vindt u in de [Controlelijst voor beveiliging en privacy](https://helpx.adobe.com/nl/campaign/kb/acc-security.html). (NEO-24232)

* Om de beveiliging te optimaliseren is het MD5-hashalgoritme waarmee bestandsnamen worden gegenereerd, versterkt met sha256 voor het uploaden van openbare bestanden. (NEO-17044)

* Om de beveiliging tegen XSS-aanvallen te versterken worden scripts aan de clientzijde onbruikbaar gemaakt bij het uitvoeren van een spiegelpagina. (NEO-17987)

* Probleem verholpen waarbij de technische workflow voor **het opschonen van privacyaanvragen** niet kon worden gebruikt om afstemmingsdata te verwijderen. (NEO-25168, NEO-21004)

* Probleem verholpen met de activiteit **Bestand overdragen** waardoor verificatie op basis van SFTP-sleutels niet kon werken op Debian 9. (NEO-23183)

**Verbeteringen op gebied van compatibiliteit**

De volgende systemen worden nu ondersteund met Campaign:
* Besturingssystemen: Debian 10
* RDBMS: Oracle 18c en Oracle 19c
* FDA: Azure Synapse Analytics

Kom meer te weten in de [Campaign-compatibiliteitsmatrix](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html).

**Verbeteringen**

* Transactionele berichten zijn verbeterd voor een betere gebruikerservaring. U kunt nu de publicatie van een transactionele berichtsjabloon ongedaan maken, waardoor deze uit de uitvoeringsinstanties wordt verwijderd. [Meer informatie](../../message-center/using/publishing-message-templates.md#template-unpublication).

* Er zijn nieuwe opties beschikbaar om beperkingen in te stellen bij het verzenden van e-mails die afbeeldingen of bijlagen bevatten. Deze beveiligingen kunnen prestatieproblemen vermijden, wat in het bijzonder nuttig is bij transactionele berichten. [Meer informatie](../../installation/using/configuring-campaign-options.md#delivery)

* Met de nieuwe optie **Prepare the delivery parts in the database** kunt u de levering direct in de database voorbereiden. Hierdoor kan de analyse aanzienlijk worden versneld. Deze optie is alleen beschikbaar voor specifieke configuraties. [Meer informatie](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* De prestaties van de activiteit [CRM Connector](../../workflow/using/crm-connector.md) voor Microsoft Dynamics zijn verbeterd. (NEO-13303, NEO-12710)

* De versie van het gedeelde geheugen is verhoogd.

   >[!WARNING]
   >
   >Deze verbetering vereist een extra stap na het uitvoeren van de upgrade. Raadpleeg de onderstaande sectie over **Technische ontwikkelingen**.

* De opschoningsworkflow is verbeterd. Zwevende werktabellen van alle verwijderde workflows worden nu ook automatisch verwijderd door de opschoningsworkflow. [Meer informatie](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Certificaten voor mobiele iOS-applicaties met de iOS HTTP2-connector worden nu gevalideerd voordat pushmeldingen worden verzonden, zodat leveringen niet mislukken vanwege verlopen certificaten.

* Het beheer van HTTP-proxyverbindingen is verbeterd. [Meer informatie](../../installation/using/file-res-management.md).

* Nieuwe optie in workflowactiviteiten **[!UICONTROL Javascript Code]** en **[!UICONTROL Advanced Javascript Code]** om uitvoering na een bepaalde limiet te stoppen. Standaardwaarde is 1 uur. [Meer informatie](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

**Overige wijzigingen**

* Verouderde sms-connectoren zijn nu afgeschaft. Raadpleeg de [pagina met verouderde functies](../../rn/using/deprecated-features.md).

* U kunt uw eigen Litmus-account niet meer gebruiken voor provisioning en gebruik van inboxrendering in Adobe Campaign. [Meer informatie](../../delivery/using/inbox-rendering.md).

* Voor een beter onderscheid tussen weergaven en mappen is de kleur van weergavenamen gewijzigd van donkerblauw in donkercyaan. [Meer informatie](../../platform/using/access-management-folders.md)

* Campaign Classic kan nu worden verbonden met Microsoft Dynamics CRM-accounts die worden gehost in de regio’s Verenigd Koninkrijk, India en Canada. Dit is van toepassing op Office 365 en op on-premise implementatietypen (Dynamics 2015).

* Campaign voert nu een TLS-verificatie uit om te controleren of de hostnaam van de server overeenkomt met de hostnaam in het opgegeven certificaat.

* De tabel met leverings- en trackingstatistieken geeft nu één vermelding per levering op voor het sms-kanaal in plaats van één vermelding per leveringsontvanger.

* Er is een foutbericht toegevoegd in het logboekbestand om gebruikers te waarschuwen wanneer het gedownloade bestand groter is dan de schijfruimte.

* De volgende functies zijn nu beschikbaar voor de Snowflake-connector: MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Technische ontwikkelingen**

Deze nieuwe build werkt het gedeelde geheugen bij en vereist extra stappen om de upgrade uit te voeren. Als Campaign-beheerder dient u geheugensegmenten te verwijderen. Deze stappen zijn verplicht, omdat oude segmenten het starten van nlserver/nlsrvmod verhinderen.

In Windows moet het systeem opnieuw worden opgestart.

In Debian/CentOs moet het gedeelde geheugen worden verwijderd. Dit zijn de stappen die u moet uitvoeren:

Voor de upgrade moet u de volgende stappen uitvoeren:

1. Stop de service apache2 (http2 op CentOS) als deze actief is.
1. Stop de service nlserver (nlserver6 voor oudere builds) als deze actief is.

Na de upgrade:

1. Verwijder het gedeelde geheugen met de opdracht **ipcrm** als de versie ouder is dan de huidige versie.
1. Start de service nlserver als deze actief was.
1. Start de service apache2 als deze actief was.

Hier zijn de opdrachtregels voor Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Een voorbeeld voor Linux is beschikbaar op deze [pagina](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Patches**

* Oplossing voor een kleine regressie in de logboeken van de opschoningsworkflow.
* Probleem verholpen met de activiteit **Laden (SOAP)** tijdens het parseren van WSDL-bestanden in de workflow.
* Probleem verholpen dat een fout veroorzaakte bij het upgraden van een groot aantal workflows met behulp van een activiteit **Enquête** om een groot aantal workflows efficiënt te verwerken.
* Oplossing voor een probleem met onregelmatige verbinding tijdens de verwerking van inMail-berichten van de Enhanced MTA. (NEO-20380)
* Probleem verholpen waarbij de percentages voor hot clicks niet correct werden weergegeven wanneer afbeeldingen met een breedte van 100% werden weergegeven in de HTML. (NEO-23203)
* Probleem verholpen waardoor de voorwaardelijke content van de levering niet volledig kon worden weergegeven in het rapport met hot clicks. (NEO-18729)
* Probleem verholpen waarbij de stap voor doelgoedkeuring werd overgeslagen wanneer een workflow werd hervat om een terugkerende levering te verzenden. (NEO-18166)
* Probleem verholpen waardoor de knop **Restart message preparation** niet kon worden hervat nadat een fout in de workflow was verholpen. (NEO-13488)
* Probleem verholpen waarbij leveringen in de midsourcingmodus tijdens de opbouwfase konden mislukken, waarbij ontvangers in de Japanse e-mailindeling werden opgenomen. (NEO-23846)
* Probleem met tijdzoneconversie verholpen met de Snowflake-connector (NEO-20105)
* Probleem met externe accounts met FTP via SSL opgelost. (NEO-20498)
* Probleem verholpen waarbij afbeeldingen niet konden worden weergegeven in Line-leveringen. (NEO-23207)
* Probleem verholpen dat een fout veroorzaakte bij het publiceren van een aanbieding. (NEO-23312)
* Probleem verholpen met pushmeldingen die het mogelijk maakten testverbindingen te gebruiken in mobiele applicaties, zelfs als het certificaat verlopen was. (NEO-22991)
* Probleem verholpen dat invloed zou kunnen hebben op pushmeldingen wanneer deze op een hoge frequentie worden verzonden. (NEO-20516)
* Probleem verholpen waarbij bij de volgende trackingdata duplicaten werden opgenomen, ook al werden deze niet bijgehouden in de trackinglogboeken. (NEO-20040)
* Probleem verholpen waarbij dubbele transactionele e-mails werden verzonden nadat een fout met de communicatie van de trackingserver was verholpen. (NEO-23640)
* Probleem verholpen waarbij de parameterwaarde voor codering tijdens het omleiden van een tracking-URL werd verwijderd (van invloed op Japanse tekens). (NEO-25637)
* Probleem verholpen waarbij een query niet werkte bij het vergelijken van getallen met drijvende komma’s. (NEO-23243)
* Probleem verholpen waarbij de weergave van de content van de kolom **Modified by** kon worden verhinderd nadat een workflow opnieuw was gestart. (NEO-23035)
* Probleem opgelost waarbij het downloaden van logboekbestanden uit een tweede container tot mislukken van de technische workflow voor tracking leidde. (NEO-23159)
* Probleem verholpen waarbij workflows konden mislukken wanneer een activiteit **Verrijking** werd uitgevoerd. (NEO-17338)
* Er is een controle toegevoegd aan het veld **Doubles to keep** in de workflowactiviteit **Deduplicatie** om te voorkomen dat er ongeldige of negatieve waarden worden ingevoerd.
* De **planningswizard** is verwijderd uit de terugkerende campagnes om te voorkomen dat uren en minuten worden vermeld. Alleen datums worden in aanmerking genomen.
* Probleem verholpen met extra opslagvelden tijdens het maken van leveringen via de optie **Computed by a script** in de workflowactiviteit **Script**. (NEO-20609)
* Probleem verholpen waarbij dubbele workflows niet werden verwijderd binnen de opschoningstaken voor de database.
* Probleem verholpen waarbij de technische workflow voor **facturering (actieve profielen)** mislukte. (NEO-19777)
* Oplossing voor een regressieprobleem tijdens het gebruik van de ACS-connectorfunctie waardoor er geen verbinding kon worden gemaakt met een Campaign Standard-instantie (onjuist beheer van de FOH/FOH2-verbinding). (NEO-23433)
* Probleem verholpen waardoor u geen schema-extensie voor een primaire sleutel met meerdere kolommen met een Hadoop-tabel kon maken. (NEO-17390)
* Probleem verholpen in de activiteit **Laden (SOAP)** waardoor WSDL-bestanden soms niet niet vanaf een URL konden worden geladen. (NEO-16924)
* Probleem verholpen waardoor u geen **onvoorwaardelijke stop** kon uitvoeren via de console wanneer meerdere actieve workflowservers een gelijke taakverdeling hadden. (NEO-19556)
* Oplossing voor een regressie die ertoe leidde dat de opschoningsworkflow vastliep.
* Probleem verholpen dat kon optreden wanneer een sjabloon op een uitvoeringsinstantie werd gepubliceerd.
* Probleem verholpen waardoor de technische workflow van collectPrivacyRequests niet kon worden uitgevoerd. (NEO-20513, NEO-25169)
* Problemen verholpen die zich konden voordoen wanneer werd geprobeerd verbinding te maken met Audience Manager na de upgrade naar 9080. (NEO-20511, NEO-25167)
* Problemen verholpen die konden optreden bij het exporteren van rapporten in PDF- of XLS-indeling. (NEO-20982, NEO-23493, NEO-23348)
* Probleem verholpen waarbij een levering twee keer in de leveringslijst kon worden weergegeven nadat deze was verzonden.
* Probleem met de leveringsvoorbereiding verholpen dat kon optreden wanneer de routeringsconfiguratie was ingesteld om de levering via midsourcing te verzenden.
* Probleem verholpen waarbij een foutbericht kon worden weergegeven wanneer op een koppeling voor een webapplicatie in een Line-bericht werd geklikt.
* Probleem verholpen waarbij de geschiedenis van de activiteit **Incrementele query** werd verwijderd na het uitvoeren van de opschoningsworkflow.
* Probleem verholpen bij het maken van een extern account voor midsourcing waarbij de optie NmsMidSourcing_LastBroadLog_&lt;InternalName> ontbrak..
* Oplossing voor een regressieprobleem met een databaseverbinding waarbij de webserver voortdurend opnieuw werd opgestart vanwege een probleem met de databasecodering. Dit kan leiden tot overmatig verbruik. (NEO-23264)


## Release 20.1{#release-20-1}

### ![](assets/do-not-localize/limited_2.png) Release 20.1.4 - build 9126 {#release-20-1-4-build-9126}

_15 april 2021_

* Er is een probleem met een regressie van de clientconsole opgelost die tot permanente foutberichten op het IMS-verbindingsscherm leidde. (NEO-34821)

**Alleen de console-upgrade is verplicht. Er is geen serverupgrade vereist.**

>[!NOTE]
>
> Maak verbinding met [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) om de nieuwe versie te downloaden. [Op deze pagina ](../../installation/using/client-console-availability-for-windows.md) leert u hoe u de console-update aan alle eindgebruikers kunt voorstellen.

_22 maart 2021_

* Er is een regressie opgelost die verhinderde dat bepaalde onderdelen van de console konden worden gebruikt, zoals de datumkiezer en afbeeldingsbeheer in verzendingen. (NEO-31453, NEO-31454)

**Alleen de console-upgrade is verplicht. Er is geen serverupgrade vereist.**

>[!NOTE]
>
> Maak verbinding met [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) om de nieuwe versie te downloaden. [Op deze pagina ](../../installation/using/client-console-availability-for-windows.md) leert u hoe u de console-update aan alle eindgebruikers kunt voorstellen.

_23 december 2020_

>[!CAUTION]
>
> * Deze release wordt geleverd met een nieuw verbindingsprotocol: als u verbinding maakt met Campaign via de Adobe Identity Service (IMS), is een upgrade verplicht voor zowel de Campaign-server als de clientconsole om na **30 juni 2021** verbinding te kunnen maken met Campaign. [Meer informatie](../../technotes/using/ims-updates.md)
>
> * Deze release wordt geleverd met een [oplossing voor een beveiligingsprobleem](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): een upgrade is verplicht om de beveiliging van uw IT-omgeving te versterken.


* Het verbindingsprotocol is bijgewerkt en aangepast aan het nieuwe IMS-verificatiemechanisme.
* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-27777)

### ![](assets/do-not-localize/red_2.png) Release 20.1.3 - build 9124{#release-20-1-3-build-9124}

_6 mei 2020_

* Probleem verholpen met de activiteit **Bestand overdragen** waardoor verificatie op basis van SFTP-sleutels niet kon werken op Debian 9. (NEO-23183)

### ![](assets/do-not-localize/red_2.png) Release 20.1.2 - build 9123{#release-20-1-2-build-9123}

_13 maart 2020_

* Probleem verholpen waarbij implementatie van versies op Red Hat 7-servers werd voorkomen. (NEO-23332)

### ![](assets/do-not-localize/red_2.png) Release 20.1 - build 9122{#release-20-1-build-9122}

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
    <p>Raadpleeg voor meer informatie de <a href="../../installation/using/configure-fda-snowflake.md">gedetailleerde documentatie</a> en <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">zelfstudievideo</a>.</p>
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

* Verbeterd quarantainebeheer en opschoning van de tabellen die worden gebruikt door de functie voor pushmeldingen (nms:address en nms:appSubscriptionRcp). Voor iOS (alleen HTTP2-connector) worden uitgeschakelde tokens nu op dezelfde manier afgehandeld als voor Android. De markering voor uitschakelen is nu ingesteld in de tabel NmsAppSubscriptionRcp. [Meer informatie](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Er is een nieuwe optie toegevoegd aan het dialoogvenster **JavaScript-code** en **Geavanceerde JavaScript-code** workflowactiviteiten om een time-outperiode te definiëren. Hierdoor wordt voorkomen dat de uitvoeringsfase van JavaScript te lang wordt uitgevoerd. Als de time-outperiode verstreken is, wordt de workflow gestopt. De standaardtime-out is 1 uur. [Meer informatie](../../workflow/using/sql-code-and-javascript-code.md)

* De leveringsanalyse wordt nu gestopt wanneer geen passende affiniteit op de midsourcingserver wordt gevonden, met het overeenkomstige foutenmelding die wordt getoond.

* Database-failover voor Postgres wordt nu ondersteund: Wanneer de databaseserver vastloopt en opnieuw wordt opgestart, maakt Campagne nu automatisch opnieuw verbinding met de server.

* De **Begin in behandeling** De weergave is toegevoegd aan het knooppunt Beheer > Audit > Workflows Status. Hierdoor kunt u alle workflows op uw instantie controleren die wachten om te worden gestart door de **operationMgt** proces. Deze weergave wordt geleverd met het marketingpakket. [Meer informatie](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Andere wijzigingen**

* In Linux gebruikt het opstarten van de netwerkservice nu een systeemeenheid in plaats van het script /etc/init.d/nlserver6. De migratie naar het nieuwe opstartschema wordt automatisch uitgevoerd wanneer u het 20.1-pakket installeert. /etc/init.d/nlserver6 wordt nog verstrekt maar voor het in wisselwerking staan met de nlserver dienst (begin, nieuw begin, einde, enz.), adviseren wij dat u het systeembevel direct gebruikt.

* De meest verbruikende aangepaste tabellen zijn verplaatst van de **xtkNewId** reeks naar toegewezen reeksen.

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

* Probleem verholpen dat tot een fout leidde bij het gebruik van de methode POST in het dialoogvenster **Webdownload** workflowgebeurtenisactiviteit.

* Probleem opgelost met het genereren van voorstellen. (NEO-18176)

* Probleem met weergave van voettekst verholpen bij gebruik van de sjabloon voor het verkrijgen van een webformulier.

* Probleem verholpen bij het parseren van de URL&#39;s in de inhoud van doorlopende leveringen die ertoe konden leiden dat ze vastliepen. (NEO-16910)

* Probleem verholpen met de **Start** en **Einde** velden die niet worden berekend tijdens het maken van een nieuwe campagne.

* Probleem verholpen met de **Bestand downloaden** workflowactiviteit bij gebruik van een URL.

* Probleem verholpen bij het voorvertonen van een geïmporteerde lijst in een queryactiviteit van een rapport. (NEO-13119)

* Probleem verholpen waarbij een verouderde afbeelding werd weergegeven wanneer u het dialoogvenster **Aangedreven door campagne** personaliseringsblok in de e-mailredacteur.

* De netwerkcommunicatie tussen de client en de server is verbeterd.

* Probleem verholpen waarbij te veel workflows in dezelfde campagne werden gemaakt. U kunt nu niet meer dan 28 workflows maken. Er wordt een waarschuwing weergegeven.

* Probleem verholpen tijdens het gebruik van de **Een selectie van kolommen** afstemmingsoptie in een **Unie** workflowactiviteit.

* Probleem verholpen waarbij de console vastloopt die kan optreden wanneer een beschadigde verrijkingslijst in een workflow wordt gebruikt. (NEO-18096)

* Oplossing voor diverse problemen met het vastlopen van de console die in workflows konden optreden (NEO-18010, NEO-18032)

* Probleem verholpen waarbij de uitvoering van een **Extern signaal** workflowactiviteit, zelfs wanneer deze was uitgeschakeld. (NEO-17524)

* Probleem verholpen bij het maken van een nieuw schema.

* Probleem met bijhouden bij het verzenden van SMS-berichten is opgelost. (NEO-19595)

* Probleem verholpen waarbij een onjuist doelaantal werd weergegeven in leveringsindicatoren.

* Probleem verholpen waarbij onjuiste percentages werden weergegeven bij het genereren van een beschrijvend rapport via een workflowactiviteit. (NEO-14314)

* Probleem verholpen waarbij verschillende nummers werden weergegeven in het rapport met de leveringstijd. (NEO-11783)

* Probleem verholpen waardoor de traceringsindicatoren voor transactionele berichten niet konden worden bijgewerkt door de workflow voor bijhouden. (NEO-17770)

* Oplossing voor een regressieprobleem dat ertoe leidde dat het webproces vastliep en opnieuw opstartte bij het aanvragen van een aanbieding via SOAP. (NEO-19482)

* Probleem verholpen waarbij gegevens niet konden worden geüpload naar openbare bronnen als de uploadmap een externe gedeelde locatie was. (NEO-19361)

* Het probleem dat de oorzaak was van de **Publiek importeren uit de Adobe Experience Cloud** technische werkstroom tp blijft mislukken. (NEO-18463)

* Probleem verholpen waardoor leveringen niet konden worden verzonden bij gebruik van sjablonen die uit Experience Manager zijn geïmporteerd. (NEO-17540)

* Probleem verholpen dat optrad na de upgrade naar versie 9032 en waardoor de instantie geen verbinding kon maken met de FTP-server via het SSL-protocol. (NEO-20498)

* Oplossing voor een probleem dat optrad bij het verwijderen, invoegen of bijwerken van een grote hoeveelheid gegevens met de **Gegevens bijwerken** activiteit in een werkschema gebruikend een schema FDA als het richten dimensie. (NEO-13280)

* Probleem verholpen waarbij e-mailberichten niet konden worden verzonden als er JavaScript-code buiten de HTML-inhoudstag stond. (NEO-18628)

* Probleem verholpen die optrad tijdens het weergeven van de spiegelpagina vanuit de leveringslogboeken van een verzonden bericht. (NEO-17976)

* Het probleem dat ervoor zorgde dat de **Koppelen aan spiegelpagina** het verpersoonlijkingsblok wordt getoond in **Tekstinhoud** tabblad nadat u hebt geklikt **HTML importeren** in een levering. (NEO-17568)

* Het foutbericht dat wordt weergegeven wanneer u op een koppeling naar een verlopen spiegelpagina klikt, is verduidelijkt. (NEO-17340)

* Probleem verholpen waardoor sommige knoppen niet konden worden gebruikt in het dialoogvenster **Gegevensverspreiding** aanmaakscherm.

* Probleem verholpen dat optrad bij het plannen van een leveringsactiviteit in een instantie met Asia/Kolkata als tijdzone. (NEO-20001)

* Er wordt nu een fout weergegeven wanneer een levering een probleem met de affiniteitsconfiguratie heeft.

* Probleem verholpen waarbij een onjuist versietnummer werd weergegeven in het dialoogvenster **Info** -menu.

* Probleem verholpen die optrad tijdens het bijwerken van de verpletterende account vanuit de eigenschappen van een terugkerende levering in een workflow. (NEO-18684)

* Probleem verholpen dat optrad wanneer verbinding werd gemaakt met de instantie via de omleidingsmodule, waardoor de verbinding niet goed kon worden schoongemaakt zodra deze was gesloten.
