---
title: Laatste release
description: Opmerkingen bij de nieuwste release Campaign Classic
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '1820'
ht-degree: 3%

---


# Laatste release{#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste kandidaatversie** van Campaign Classic Release.

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
<td> <p>Wanneer u uw mobiele app integreert met Campagne, moet u uw communicatie beveiligen met APNs (Apple Push Notification service). U kunt verificatie op basis van een certificaat of een token gebruiken.
</p>
<p>Deze twee verificatiemodi zijn nu beschikbaar voor mobiele iOS-apps in Campaign Classic:
</p>
<ul> 
<li><p>Verificatie op basis van token (aanbevolen): deze verificatiemodus is gebaseerd op een .p8-bestand. Deze authentificatiemodus is sneller aangezien elke aanvraag aan APNs het teken bevat. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Meer informatie</a></p></li>
<li><p>Certificaatgebaseerde verificatie: deze verificatiemodus is gebaseerd op een .p12-bestand. Voor elke app is een afzonderlijk certificaat vereist. Dit certificaat wordt door Apple geleverd via uw ontwikkelaarsaccount. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Meer informatie</a></p></li> 
</ul>
<p>Leer hoe te om de authentificatiemodus in Campagne in de <a href="../../delivery/using/configuring-the-mobile-application.md">gedetailleerde documentatie</a>te selecteren.</p>
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
<td> <p>Android-pushmeldingen zijn verbeterd en bieden nu ondersteuning voor FCM HTTP v1 API voor Android-pushkanaalverificatie. </p>
<p>Met de nieuwe ondersteunde API-versie kunt u nu FCM-meldingsberichten verzenden die uitgebreide mogelijkheden voor pushberichten bieden. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Meer informatie</a></p> 
<p>In <a href="../../delivery/using/configuring-the-mobile-application-android.md">deze sectie</a> wordt uitgelegd hoe u de FCM HTTP v1-API voor Android in Adobe Campaign configureert.</p>
</td> 
</tr> 
</tbody> 
</table>

**Verbeterde beveiliging**

* Beveiligd laden van bibliotheken: Om tegen DLL te beschermen die aanvallen voorlaadt, laadt de Campagne nu Vensters DLLs slechts van het standaard systeemDLL weg terwijl het laden van de Cliënt van de Campagne (nlclient). [Meer](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) informatie (NEO-24147)
* Oplossing voor een beveiligingsprobleem ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Smeery). (NEO-25661)
* Probleem verholpen dat optrad tijdens het verwerken van GDPR-privacyverzoeken die ervoor zorgden dat records niet konden worden verwijderd uit aangepaste tabellen met een relatie op het tweede niveau met de tabel Ontvanger. (NEO-25967)
* Probleem verholpen met beveiliging door gebruik te maken van API-aanroepen van gebruikers die geen beheerder zijn en Adobe Experience Manager-sjablonen proberen te synchroniseren. (NEO-23487)

**Compatibiliteitsupdates**

De volgende systemen worden nu ondersteund met Campaign:
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**Verouderde functies**

De volgende functies zijn afgekeurd in 20.3:

* Het demdex-domein dat wordt gebruikt voor het importeren en exporteren van soorten publiek naar de Adobe Experience Cloud is afgekeurd. Als u het indexdomein voor uw invoer/uitvoer externe rekeningen gebruikt, moet u uw implementatie aanpassen dienovereenkomstig. [Meer informatie](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* De de integratieauthentificatie van trekkers oorspronkelijk die op de authentificatie van AUTH wordt gebaseerd om tot pijpleiding toegang te hebben is nu veranderd en verplaatst naar Adobe I/O. [Meer informatie](../../integrations/using/configuring-adobe-io.md)

Meer informatie vindt u op de pagina [](../../rn/using/deprecated-features.md)Afgekeurde en verwijderde functies.

**Verbeteringen**

* Er zijn verschillende verbeteringen aangebracht in de **clientconsole**:
   * Om incompatibiliteit met bepaalde beperkingen van GPO-regels voor internetbeveiliging te voorkomen, is het aanmeldingsscherm van de client-console van Campagne vervangen door een ingebouwd standaard Windows-formulier.
   * Probleem verholpen bij het kopiëren/plakken van activiteiten in een workflow met de 64-bits clientconsole. (NEO-27635)
   * In het menu **Info** is informatie toegevoegd om 64- en 32-bits consoles van elkaar te onderscheiden.
* De workflow-id wordt nu weergegeven in de logboeken wanneer u een workflow hervat. Op deze manier kunt u beter bepalen welke workflow is hervat.
* Er is een nieuw permanent cookie geïntroduceerd: nllastdelid. In dit cookie (anders dan UUID230) wordt de deliveryId opgeslagen. Wanneer de zittingskoekje niet aanwezig is, zou de uitzendingsinformatie worden genomen van deliveryId huidig in dit koekje.
Deze wijziging verhelpt een probleem dat optrad toen de browsersessie voorbij was: het sessiecookie met deliveryId en broadlogId is verwijderd. Zonder deliveryId, kon de breedbandinformatie niet worden gevonden en de het volgen lijstinformatie zou ontbreken in het geval van permanent het volgen (laatste levering).
Meer informatie over cookies vindt u in [deze sectie](../../platform/using/privacy-and-recommendations.md#cookies).
* Verbeterde hoge prestaties van de volumeproductie van de leveringsprestatie met de leverbaarheidsserver door het MTA proces opnieuw te beginnen alvorens levering te verzenden.

**Overige wijzigingen**

* Wanneer u relatief pad gebruikt voor SFTP, worden `~/` tekens niet meer automatisch toegevoegd. Indien nodig kunt u handmatig `~/` tekens aan het pad toevoegen, maar Adobe raadt u aan een **absoluut pad** te gebruiken.
* De authentificatie van NT van vensters is verwijderd uit de beschikbare authentificatiemethodes toen het vormen van een nieuw gegevensbestand met een Server van Microsoft SQL. [Meer informatie](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* De workflow voor het opschonen van databases is geoptimaliseerd voor Teradata om de prestaties te verbeteren. (NEO-19959)
* Het foutbericht dat werd weergegeven bij het invoegen van een afbeelding uit Adobe Target, is verbeterd en de naam van de huurder was leeg in de externe account.
* In leveringseigenschappen is de naam van de **[!UICONTROL Archive emails]** optie gewijzigd **[!UICONTROL Email BCC]**.
* Om robuustheid te verbeteren, worden selectAll vragen met ongeldige knopen nu verworpen. Als u de controle moet onbruikbaar maken en aan het vorige gedrag terugkeren, kunt u XtkSecurity_Disable_QueryCheck aan 0 plaatsen.

**Technische ontwikkelingen**

Tomcat is bijgewerkt van versie 7 (7.0.103) naar versie 8 (8.5.57).

De `tomcat-7` map wordt vervangen door een `tomcat-8` map.

In vensters _zijn iis_neolane_setup.vbs_ en _apache_neolane.conf_ nu geïnstalleerd in de `conf` directory (in plaats van `tomcat-7/conf` eerder).

Op Linux wordt _apache_neolane.conf_ nu geïnstalleerd in de `conf` directory.

**Patches**

* Probleem verholpen waardoor leveringsstatistieken niet opnieuw konden worden berekend.
* Probleem verholpen waarbij een foutbericht werd weergegeven tijdens het uploaden van een CSV-bestand bij het gebruik van een Campaign Classic 9080-build die was aangesloten op een server die gebruikmaakte van een oudere build. (NEO-23218)
* Probleem verholpen waarbij een foutbericht kon worden weergegeven tijdens het configureren van de wizard CRM voor Microsoft Dynamics voor een externe account. Dit is te wijten aan een compatibiliteitsprobleem met de nieuwste versie van MS Dynamics CRM API. (NEO-24528)
* Probleem verholpen waardoor u opzoektypeverslagen (gegevens die bestaan uit buitenlandse zeer belangrijke verslagen die met andere lijsten worden verbonden) van Campaign Classic naar de Dynamiek van Microsoft kon uitvoeren gebruikend de schakelaar van CRM. (NEO-23864)
* Probleem verholpen dat kon verhinderen dat de gegevens van de Dynamica van Microsoft worden gehaald als de **Automatische indexoptie** in de schakelaar van CRM werd toegelaten. (NEO-25981)
* Probleem met IMS-verificatie verholpen waarbij verbindingen geopend konden blijven, zelfs als ze werden beëindigd. De beëindigde verbindingen zullen nu automatisch worden gesloten zodra zij worden gebeëindigd om het accumuleren van verbindingen en het verbruiken van systeemmiddelen te vermijden. (NEO-25996)
* Probleem verholpen waarbij geen foutbericht werd weergegeven wanneer de synchronisatie van Adobe Experience Manager-inhoud voor een levering is mislukt als gevolg van een onjuiste configuratie van de externe account (onjuist account of wachtwoord). Er wordt nu een bericht weergegeven in het geval van een fout, zodat u het probleem gemakkelijker kunt identificeren. (NEO-25586)
* Probleem verholpen die optrad bij het selecteren van het bewerkingstype **Bijwerken** in de activiteit Gegevens **** bijwerken. Als de bij te werken gegevens onjuist waren, zou de workflow mislukken en mislukken. In het geval van onjuiste gegevens, zal het werkschema niet ontbreken, en de verslagen zullen in een **Afgewezen uitgaande overgang worden opgeslagen** . (NEO-23794)
* Probleem verholpen waardoor werkstromen die subworkflows bevatten, niet konden werken. (NEO-24036)
* Probleem verholpen tijdens het bewerken van een beschrijving van een campagnemalplaatje dat ervoor zorgde dat de knop **Opslaan** niet kon worden weergegeven tijdens het kopiëren-plakken van symbolen zoals bijvoorbeeld Japanse tekens. (NEO-27071)
* Probleem verholpen waardoor u de trackingserver niet kon wijzigen in de wizard Instantieconfiguratie.
* Probleem verholpen waardoor de beschrijving van een campagne- of campagnemalplaatje niet kon worden opgeslagen wanneer er buiten het venster werd geklikt voordat op de knop **Opslaan** werd geklikt. (NEO-27449)
* Probleem verholpen waarbij het technische werkschema **Aantal actieve factureringsprofielen** (billingActiveContactCount) niet kon werken. Dit zou kunnen gebeuren als een verbinding op een berekend gebied in een schemauitbreiding was uitgevoerd. Er is een grote hoeveelheid gegevens gemaakt, wat ertoe kan leiden dat de database over onvoldoende ruimte beschikt. (NEO-24062)
* Probleem verholpen met de activiteit **Gegevens laden (bestand)** , waardoor u Japanse tekens uit tekst- en CSV-bestanden niet kunt importeren als deze aan het einde van het bestand zijn geplaatst. (NEO-24957)
* Probleem verholpen met ononderbroken leveringen, waardoor de velden **Analyse gestart** en **Analyse voltooid** niet correct kunnen worden ingevuld. (NEO-20755)
* Probleem verholpen waarbij een foutbericht kon worden weergegeven wanneer werd geprobeerd SMS-berichten voor te vertonen na een query op een ander schema dan **Ontvanger** (nms:ontvanger). (NEO-27517)
* Probleem verholpen bij gebruik van de Snowflake FDA-aansluiting. Een gebruiker met de de toegangsnaamrechten van de Snowflake FDA kon geen vraag op een schema van de Snowflake uitvoeren. Er is een fout van het type &quot;Wachtwoord niet gevonden&quot; weergegeven in de logboeken. (NEO-23851)
* Probleem verholpen bij het gebruik van een FDA-connector die gebeurde toen de naam van het gekoppelde FDA-schema een subtekenreeks was van een elementnaam van het huidige schema. Dit gebeurde bijvoorbeeld wanneer het FDA-schema &quot;cust&quot; was en een van de elementen binnen het Ontvangerschema &quot;customer&quot; was. Bij het ophalen van de kolom in het element &quot;customer&quot; en het toevoegen van een kolom uit het schema &quot;cust&quot; FDA, ontbrak de waarde voor de lokale kolom. (NEO-20193)
* Probleem verholpen in workflows tijdens het ophalen van records uit een externe database en het invoegen van records in de Campagne-database. (NEO-26359)
* Probleem verholpen in de technische workflow voor de status **van een** update-gebeurtenis: om het rangschikken van de inkomende overeenkomstige gebieden in de activiteit van de **Statistieken** van de Levering aan te passen, werd het rangschikken van drie bestemmingsgebieden in de activiteit van de de leveringsstaten **van de** Update veranderd van 32 in 64 beetjes. (NEO-11557) Meer informatie over de workflow voor de status **van een** update-gebeurtenis vindt u in [deze sectie](../../workflow/using/message-center--execution-.md).
* Probleem verholpen in het **Message Center-rapport met gebeurtenisgeschiedenis** dat scriptfouten veroorzaakte bij het toepassen van filters en dat het filter op een datumbereik onmogelijk maakte. (NEO-23365)
* Oplossing voor een interferentieprobleem tussen de technische workflows van de **campagnebanen** (operationMgt) en **Preview** (predicasting). Dit gebeurde wanneer de geplande leveringen in &quot;Klaar Doel&quot;of &quot;Klaar om worden geleverd&quot;status bleven. (NEO-20819)
* Probleem met XML-parsering verholpen waarbij de XML-id niet aanwezig was in het gegevensveld in xtkOperator. Het veroorzaakte een postupgrade-fout. (NEO-26113)
* Probleem verholpen bij het gebruik van de **bestandsoverdrachtactiviteit** die gekoppeld was aan een Azure extern account gecodeerd in SSL, waar de verbinding tot stand was gebracht met HTTP in plaats van met HTTPS. (NEO-26720)
* Probleem verholpen met een MSSQL-database waarbij een fout kon optreden met de procedure up_updatestats tijdens de opschoningsworkflow.
* Oplossing voor een crash die optrad tijdens het afsluiten van het webproces als de interactieverzoeken nog steeds worden verwerkt. (NEO-26447)
* Probleem verholpen waarbij de functie **NoNull** in Oracle DB niet meer werkte na upgrade 9032. (NEO-26488)
* Probleem verholpen waarbij de traceringsworkflow mislukte na upgrade 9171 als het LINEV2-pakket was geïnstalleerd zonder het Message Center-pakket.
* Probleem met schaalbaarheid verholpen waarbij de verbindingspool niet kon worden verhoogd tot het gewenste aantal verbindingen omdat de verbindingstekenreeks voor het kenmerk &#39;APP&#39; uiteindelijk een ongeldige waarde kreeg. (NEO-25105)
* Probleem verholpen op het niveau van de proxyconfiguratie waardoor u zich niet kon aanmelden bij Adobe Campaign na de laatste Windows 10-update. (NEO-27813)
* Probleem verholpen waarbij ongewenste URL&#39;s zichtbaar werden in de geleverde e-mails nadat HTML-sjablonen met trackingkoppelingen waren geïmporteerd. (NEO-25909)
* Probleem verholpen waarbij de server vastliep bij het weergeven van de doelgegevens van de rest van een activiteit **Splitsen** in een workflow.
* Probleem verholpen waarbij de server vastliep door geheugenbeschadiging te voorkomen tijdens het opschonen van de expressieparser. (NEO-26856)
* Probleem verholpen in de verrijkingsactiviteit waarbij niet-beheerders instantievariabelen definieerden. (NEO-25653)