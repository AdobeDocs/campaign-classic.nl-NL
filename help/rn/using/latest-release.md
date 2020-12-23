---
solution: Campaign Classic
product: campaign
title: Laatste release
description: Nieuwste opmerkingen bij de release van Campaign Classic
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 57093a687534ed1e7f77738ca233d4cc86cf40cf
workflow-type: tm+mt
source-wordcount: '1875'
ht-degree: 97%

---


# Laatste release{#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van de Campaign Classic-releasekandidaat**.

Voor de Campaign Classic Gold Standard-versie (nieuwste GA-build) [raadpleegt u deze pagina](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Release 20.3.1 - build 9228 {#release-20-3-1-build-9228}

_27 oktober 2020_

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

>[!CAUTION]
>
>Deze versie wordt geleverd met een nieuw verbindingsprotocol: De upgrade is verplicht voor zowel de campagneserver als de clientconsole om verbinding te kunnen maken met Campagne na 21 maart 2021.

**Verbeterde beveiliging**

* Beveiligd laden van bibliotheken: ter bescherming tegen dll-voorafladingsaanvallen laadt Campaign Windows-dll’s nu alleen vanaf het Windows-standaardsysteempad naar dll’s tijdens het laden van de Campaign Client (nlclient). [Meer informatie](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
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
   * Het verbindingsprotocol is bijgewerkt om het nieuwe IMS authentificatiemechanisme te volgen. De upgrade van de server- en clientconsole is verplicht om verbinding te kunnen maken na 21 maart 2021.
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

**Technische ontwikkelingen**

Tomcat is bijgewerkt van versie 7 (7.0.103) naar versie 8 (8.5.57).

De map `tomcat-7` is vervangen door een map `tomcat-8`.

In Windows _zijn iis_neolane_setup.vbs_ en _apache_neolane.conf_ nu geïnstalleerd in de map `conf` (in plaats van `tomcat-7/conf` zoals eerder).

In Linux is _apache_neolane.conf_ nu geïnstalleerd in de map `conf`.

**Patches**

* Er is een probleem verholpen waardoor leveringsstatistieken niet opnieuw konden worden berekend.
* Er is een probleem verholpen waarbij een foutbericht werd weergegeven tijdens het uploaden van een CSV-bestand bij het gebruik van een Campaign Classic 9080-build die was verbonden met een server die gebruikmaakte van een oudere build. (NEO-23218)
* Er is een probleem verholpen waarbij soms een foutbericht werd weergegeven tijdens het configureren van de CRM Microsoft Dynamics-wizard voor een extern account. Dit kwam door een compatibiliteitsprobleem met de nieuwste versie van de MS Dynamics CRM-API. (NEO-24528)
* Er is een probleem verholpen waardoor u opzoekrecords (data die bestaan uit records met vreemde sleutels die zijn verbonden met met andere tabellen) niet kon exporteren van Campaign Classic naar Microsoft Dynamics met de CRM-connector. (NEO-23864)
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