---
product: campaign
title: Releases van Campaign Classic 2023
description: Meer informatie over releases van Campaign Classic 2023
feature: Release Notes
role: User
level: Beginner
exl-id: 8ed11e96-9f23-4e2e-bae2-25c51cfb549a
source-git-commit: f39dc6077a7ddc3fb9b53d4082c08e65e7683f10
workflow-type: ht
source-wordcount: '2337'
ht-degree: 100%

---

# Releases van 2023{#release-2023}

## Release 7.3.5 - build 9368 {#release-7-3-5}

[!BADGE Beperkte beschikbaarheid]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Beperkte beschikbaarheid"}

_Woensdag 5 december 2023_

### Beveiligingsverbeteringen {#release-7-3-5-security}


* Met Campaign Classic v7.3.5 is het verificatieproces verbeterd en beveiligd. Technische operatoren moeten nu Adobe Identity Management System (IMS) gebruiken om verbinding te maken met Campaign. Ontdek in [deze technische opmerking](../../technotes/using/ims-migration.md) hoe u uw bestaande technische account(s) kunt migreren.

* Daarnaast raadt Adobe Campaign bij het versterken van het beveiligings- en verificatieproces sterk aan om de modus voor verificatie van eindgebruikers te migreren van de native verificatie van aanmelding/wachtwoord naar Identity Management System (IMS) van Adobe. Ontdek in [deze technische opmerking](../../technotes/using/migrate-users-to-ims.md) hoe u uw operators kunt migreren.

* Als een webformulier de status **Publicatie in behandeling** heeft, wordt het niet automatisch live. Om beveiligingsproblemen te voorkomen, moet het worden gepubliceerd voordat het **Online** wordt en toegankelijk is via de webformulier-URL in een webbrowser. [Meer informatie](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Andere verbeteringen {#release-7-3-5-other}

Als u deze release start, werkt het bijhouden van koppelingen in e-mails die al zijn verzonden, nog tijdens de upgrade. [Meer informatie](../../platform/using/faq-build-upgrade.md)

### Patches {#release-7-3-5-patches}

* Probleem verholpen bij het gebruik van gegevens uit een Google Big Query-database en het bijwerken van gegevens in een Oracle-database: alle sleutels in de tijdelijke tabel met workflows zijn ingesteld op `0`. (NEO-65091)
* Probleem verholpen waarbij de uitvoering van een workflow mislukte wanneer twee query&#39;s in een Google Big Query-database werden gecombineerd in een **Samenvoeging**-workflowactiviteit. (NEO-63705)
* Probleem verholpen waarbij de gebruiker werd gevraagd opnieuw te verifiëren wanneer in een Campaign-rapport op de knop `Back` werd geklikt. (NEO-65087)
* Probleem verholpen in de workflow Database opschonen die optrad als een levering werd verwijderd vóór de leveringsbewijzen werden afgeleverd. (NEO-48114)
* Probleem verholpen tijdens verbinden met de clientconsole: recente updates van de TLS-verificatie leidden tot een verbindingsfout. (NEO-50488)
* Probleem verholpen met de HTTP-proxyverificatie na de upgrade van de Campaign naar 7.3.1., waarbij HTTP-verzoeken in Campaign-workflows mislukten met `error 407 – proxy auth required is returned`. (NEO-49624)
* Er is een intermitterende fout opgelost bij GPG-ontsleuteling in workflowactiviteiten van **Script**. Het bijbehorende foutbericht was: `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->




## Release 7.3.4 - build 9364 {#release-7-3-4}

[!BADGE Beperkte beschikbaarheid]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Beperkte beschikbaarheid"}


>[!CAUTION]
>
>De upgrade van Client Console is verplicht. Lees op deze [pagina](../../installation/using/installing-the-client-console.md) hoe u uw Client Console kunt upgraden.
>
>Als u [Campaign - Microsoft Dynamics CRM Connector](../../platform/using/crm-connectors.md) gebruikt, moet u zowel uw marketing als uw mid-sourcingservers upgraden met deze nieuwe build.

_7 september 2023_

### Beveiligingsverbeteringen {#release-7-3-4-security}

* De beveiliging in IMS API&#39;s is verbeterd. Clientgevoelige informatie (d.w.z. toegangstokens) is verwijderd uit URL-parameters. Deze gegevens worden nu verzonden in de header voor publicatiegegevens of autorisaties, zodat een veiliger communicatieproces mogelijk is. (NEO-63045)
* De beveiliging in webapps is verbeterd om DDOS-aanvallen te voorkomen. (NEO-50757)
* De beveiliging is verbeterd om te voorkomen dat PII-gegevens worden weergegeven in weblogfouten. (NEO-46827)
* De beveiliging is geoptimaliseerd om te voorkomen dat het beveiligingstoken wordt opgenomen in de URL van de Campaign-startpagina. (NEO-38519)

### Compatibiliteitsupdates  {#release-7-3-4-compat}

* Tomcat is bijgewerkt naar Versie 8.5.91
* De bibliotheek libexpat is bijgewerkt naar 2.5.0 om de beveiliging te verbeteren. (NEO-51023)

### Verbeteringen {#release-7-3-4-improvements}

* De parameter MaxWorkingSetMb in het bestand van de serverconfiguratie (serverConf.xml) is gewijzigd om geheugentoewijzing voor leveringen te optimaliseren. (NEO-49204)
* De externe BigQuery-account is uitgebreid met nieuwe opties die worden gebruikt voor het instellen van de GCloud SDK. (NEO-63879) [Meer informatie](../../installation/using/configure-fda-google-big-query.md#google-external)
* Er is een nieuwe sectie `cusHeader` toegevoegd aan het configuratiebestand van de server (serverConf.xml). Hiermee kunt u aangepaste headers toevoegen wanneer u een bestand van een externe server uploadt. (NEO-58339) [Meer informatie](../../installation/using/the-server-configuration-file.md#cusheaders).
* Het beheer van het trackinglog is verbeterd en voorkomt negatieve ID&#39;s voor lastMsgId. Het is veranderd van int32 in int64. (NEO-52290)
* De workflow voor het leveren van statistieken (mid-sourcing) is kant-en-klaar toegevoegd. Deze nieuwe workflow synchroniseert de gegevens van de leveringsstatistiek (nms:deliveryStat) van het midden aan de marketinginstantie. (NEO-36802)

### Patches {#release-7-3-4-patches}

* Er is een probleem verholpen waarbij soms een dienstverzoek voorafgaand aan IMS-login werd gemaakt als de oproepverificatie van de serviceaanvraag een servicetoken gebruikte. (NEO-64903)
* Er is een probleem met regressie verholpen dat bij gebruik van de Digital Content Editor tot scrolproblemen kon leiden. (NEO-64671, NEO-59256)
* Er is een probleem verholpen met regressie bij het plakken van content van Excel naar de Digital Content Editor. (NEO-63287)
* Er is een probleem verholpen waardoor webapps soms niet correct werden weergegeven in de v5-compatibiliteitsmodus. (NEO-63174)
* Er is een probleem verholpen waarbij niet-beheerders geen webAnalytics-leveringen konden verzenden. (NEO-62750)
* Er is een probleem verholpen waarbij browsers geen extra spaties konden toevoegen bij gebruik van voorwaardelijke content in een levering. (NEO-62132)
* Er is een regressieprobleem verholpen waardoor de berekening van de actieve contactpersoon niet correct werkte in de factureringsworkflow bij het gebruik van doelschema&#39;s gekoppeld aan meerdere logschema&#39;s. (NEO-61468)
* Er is een probleem verholpen dat soms een fout veroorzaakte en waardoor scrollen soms niet mogelijk was bij het bewerken van de content van een levering. (NEO-61364)
* Er is een probleem verholpen waarbij een pop-upvenster werd geopend wanneer werd geklikt op een afbeelding in de editor van de e-mailcontent. (NEO-60752)
* Er is een probleem verholpen waardoor speciale tekens in de HTML-content van een levering in verschillende browsers soms niet goed werden gecodeerd. (NEO-60081)
* Er is een synchronisatieprobleem opgelost dat soms optrad bij het gebruik van de inSMS-workflowactiviteit. (NEO-59544)
* Er is een probleem opgelost bij het gebruik van de Big Query-connector met tijdstempel- of datum/tijd-velden. (NEO-59502, NEO-49768)
* Er is een probleem opgelost waardoor u geen cumulatieve leveringsrapporten kon gebruiken. (NEO-59211)
* Er is een probleem opgelost dat tot fouten kon leiden bij het delen van doelgroepen met de People Core-service. (NEO-58637)
* Er is een probleem opgelost bij het weergeven van de spiegelpagina van een levering. (NEO-58325)
* Er is een probleem opgelost waardoor de xtk-expressie XtkLibrary.Right() niet werkte. (NEO-57870)
* Er is een probleem opgelost waarbij het stijlkenmerk van de body-tag werd gewijzigd bij het uploaden van een afbeelding in de Digital Content Editor. (NEO-57697)
* Er is een probleem opgelost met speciale tekens bij het uitvoeren van batchexports met de CRM-connectoractiviteit. (NEO-54300)
* Er is een probleem opgelost waardoor het laden van grote hoeveelheden niet werkte met het gegevenstype &#39;tekenreeks&#39; bij gebruik van een activiteit voor het laden van gegevens en de Big Query-connector. (NEO-53748)
* Er is een probleem met de cachesleutel opgelost dat tot renderingproblemen voor aanbiedingen kon leiden. (NEO-51516, NEO-49995)
* Er is een probleem opgelost dat tot een validatiefout kon leiden bij het verzenden van een direct mail-levering met behulp van targetMapping met goedkeuringen. (NEO-50758)
* Er is een probleem opgelost met het beheer van query&#39;s dat van invloed kon zijn op de leveringsprestaties. (NEO-49991)
* Er is een probleem opgelost bij het gebruik van externe accounts voor de leveringsactiviteiten van de campagneworkflow, wat kon leiden tot problemen met de configuratie van externe accounts. (NEO-49959)
* Er is een prestatieprobleem opgelost met het verzenden van pushmeldingen. (NEO-49953)
Er is een probleem opgelost waardoor Japanse tekens soms onjuist werden weergegeven bij het exporteren van rapporten (NEO-49308).
* Er is een probleem opgelost waarbij in het Tomcat-foutrapport te veel foutgegevens werden weergegeven. (NEO-49029)
* Er is een probleem opgelost dat tot een leveringsfout kon leiden bij het gebruik van een groot aantal aanbiedingen. (NEO-48807)
* Er is een probleem opgelost waardoor de workflowactiviteit **Gegevens bijwerken** niet correct werkte. (NEO-48140)
* Er is een probleem opgelost waardoor de kliktraceringsgegevens niet konden worden gesynchroniseerd voor leveringen met een ander extern account dan e-mail.(NEO-47277)
* Er is een probleem opgelost waardoor realtimeraceringslogboeken niet konden worden gesynchroniseerd in de marketinginstantie van het Berichtencentrum. (NEO-42540)
* Er is een probleem opgelost waardoor het voorvoegsel van de werkruimte niet kon worden weergegeven in het detectievenster van een schema, voor databasetabellen van Snowflake. (NEO-40297)
* Er is een probleem opgelost waardoor `<img-amp>`-tags niet werkten in e-mailcontent. (NEO-38685)
* Er is een probleem opgelost waardoor de archiveringsworkflow van het Berichtencentrum mislukte bij gebruik van een HTTP-relay. (NEO-33783)
* Er is een probleem opgelost dat fouten in de lettertypenaam en -grootte kon veroorzaken in de editor voor e-mailcontent. (NEO-61342)

## Release 7.3.3 - build 9359 {#release-7-3-3}

[!BADGE Beperkte beschikbaarheid]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Beperkte beschikbaarheid"}

>[!AVAILABILITY]
>
>Er is een specifieke upgrade beschikbaar voor de patch v7.3.3.IMS voor deze versie, als er geen andere patch op uw omgeving is toegepast. Deze biedt [beveiligingsupdates van Adobe Identity Management System (IMS) die worden geleverd bij v7.3.5](#release-7-3-5-security) aan bestaande v7.3.3-omgevingen.


_20 maart 2023_


### Beveiligingsverbetering {#release-7-3-3-security}

* Tomcat is bijgewerkt van versie 8.5.81 naar 8.5.85 om de beveiliging te optimaliseren. (NEO-56936)


### Verbeteringen {#release-7-3-3-improvements}

* De factureringsworkflow is verbeterd om de prestaties te optimaliseren. (NEO-47658)
* De trackingworkflow is verbeterd om de prestaties bij grote leveringen te optimaliseren. (NEO-45064)
* Trackingbeheer is verbeterd om mogelijke problemen met dynamische parameters in URL&#39;s op te lossen. Trackingbeheer v3 verwerkt nu URL&#39;s van het ajax-type (met parameters na een &#39;#&#39;) af en voorkomt dat tools van derden tracking-URL&#39;s kunnen wijzigen. Neem contact op met Adobe om deze wijziging toe te passen. (NEO-46535)
* Als u deze release start, werkt het bijhouden van koppelingen in e-mails die al zijn verzonden, nog tijdens de upgrade. [Meer informatie](../../platform/using/faq-build-upgrade.md)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

>[!CAUTION]
>
>De upgrade van Client Console is verplicht. Lees op deze [pagina](../../installation/using/installing-the-client-console.md) hoe u uw Client Console kunt upgraden.

### Patches {#release-7-3-3-patches}

* Probleem verholpen waardoor proef-pushberichten voor iOS niet konden worden verzonden van de controle-instantie (context transactionele berichten). (NEO-54713)
* Probleem verholpen waardoor scrollen soms niet mogelijk was in het tabblad **Bewerken** van de Digital Content Editor (DCE). (NEO-54474)
* Probleem verholpen waarbij twee verrijkingsactiviteiten dezelfde naam-ID gebruikten in hun koppeling, waardoor de tweede verrijkingsactiviteit de koppelingen van de eerste gebruikte. (NEO-48851)

## Release 7.3.2 - build 9356 {#release-7-3-2}

[!BADGE Beperkte beschikbaarheid]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Beperkte beschikbaarheid"}


>[!AVAILABILITY]
>
>Er is een specifieke Campaign v7.3.2.IMS-patchupgrade beschikbaar voor deze versie - als er geen andere patch op uw omgeving is toegepast. Deze biedt [beveiligingsupdates van Adobe Identity Management System (IMS) die worden geleverd bij v7.3.5](#release-7-3-5-security) aan bestaande v7.3.3-omgevingen.

_21 november 2022_

### Compatibiliteitsupdates {#release-7-3-2-compat}

* Adobe Campaign is nu compatibel met PostgreSQL 14. Raadpleeg deze [technische opmerking](../../technotes/using/tech-stack-upgrade.md) voor meer informatie.

* Na afloop van de levensduur van Microsoft Internet Explorer 11 gebruikt de HTML-renderingengine voor dashboards in de clientconsole nu Edge Chromium. (NEO-20741)

Ontdek meer in de [Campaign-compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md#RDBMSservers).

>[!CAUTION]
>
>De upgrade van Client Console is verplicht. Lees op deze [pagina](../../installation/using/installing-the-client-console.md) hoe u uw Client Console kunt upgraden.

### Verbeteringen {#release-7-3-2-improvements}

* De Google BigQuery-connector biedt nu volledige ondersteuning voor booleaanse velden. (NEO-49181)
* U kunt nu de geldigheidsduur van de IMS-cookies configureren in de `Configuration for the redirection service`-sectie van het bestand serverConf.xml. Dit geldt voor de volgende cookies: `uuid230`, `nllastdelid` en `AMCV_` (NEO-42541)
* Het IP-adres kan nu worden verborgen in het /r/test-verzoek door `showSourceIP` in te stellen op false in de omleidingsnode van het bestand serverConf.xml. [Meer informatie](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)
* Als u deze release start, werkt het bijhouden van koppelingen in e-mails die al zijn verzonden, nog tijdens de upgrade. [Meer informatie](../../platform/using/faq-build-upgrade.md)


### Afgeschafte functies  {#release-7-3-2-deprecated}

* Social marketing met Facebook is nu afgeschaft. U kunt integratie met X (voorheen Twitter) gebruiken om berichten te plaatsen op sociale media. U kunt ook met Adobe werken om een aangepast kanaal te maken.
* ACS Connector (primeaanbieding) is nu afgeschaft. U kunt de export-/importcapaciteiten van Campaign gebruiken voor het extraheren en injecteren van gegevens in beide producten.

Meer informatie vindt u op de pagina [Afgeschafte en verwijderde functies](deprecated-features.md).

### Andere wijzigingen  {#release-7-3-2-other}

<!--* Web logs have been improved: `logonEscalation` warnings are now only displayed for users with admin privileges. (NEO-47167)-->
* Om fouten te voorkomen wordt de workflow **Gegevens verzamelen voor Heatmap-service** (collectDataHeatMapService) nu standaard gestopt. (NEO-33959)
* Er zijn verschillende verbeteringen geïmplementeerd om het CPU-gebruik voor het campagnedashboard te optimaliseren. (NEO-46417)
* De loadLibraryDebug JS-methode is verwijderd om crashes te voorkomen. (NEO-46968)
* De resterende verwijzingen naar de bibliotheek log4j zijn verwijderd uit de installatie van Campaign in Windows. (NEO-44851)

### Patches {#release-7-3-2-patches}

* Er is een probleem verholpen waardoor u de workflowoptie **Geselecteerde regels samenvoegen** niet kon gebruiken. (NEO-48488)
* Er is een probleem verholpen waardoor de **Success**-bezorgingsindicatie niet correct werd bijgewerkt bij gebruik van Adobe Campaign Enhanced MTA. (NEO-50462)
* Er is een probleem verholpen bij het resetten van de goedkeuring van content in een e-mailbezorging, waardoor u niet opnieuw kon goedkeuren. (NEO-44259)
* Er is een probleem verholpen waardoor de knop **Bezorgingsgoedkeuring** niet werd weergegeven. (NEO-47547)
* Er is een probleem verholpen in het HTML-tabblad van een bezorging dat kon optreden voor grootschalige HTML-code. (NEO-47440)
* Er is een probleem verholpen dat van invloed was op de statusupdates van het leveringslogboek op de MID-instantie wanneer de optie `FeatureFlag_GZIP_Compression` was ingeschakeld. (NEO-49183)
* Er is een probleem verholpen waardoor u geen meldingen van mobiele iOS-apps kon verzenden vanaf een uitvoeringsinstantie bij gebruik van tokenverificatie. (NEO-45961)
* Er is een probleem verholpen met de workflow **Vernieuwen voor bezorgbaarheid** (deliverabilityUpdate) die vastliep als er te veel broadlogs waren om te synchroniseren. (NEO-48287)
* Er is een probleem verholpen met het gebeurtenistype dat de workflow **Synchronisatie van berichtencentrum** (mcSynch) blokkeerde.
* Er is een probleem verholpen dat tot een fout kon leiden bij het toevoegen van de indicator **Ontvangers die hebben geopend** (estimatedRecipientOpen) in de aanvullende gegevens van een **Query**-workflowactiviteit. (NEO-46665)
* Er is een probleem verholpen met de workflow **Facturering** die mislukte wanneer controle- en uitvoeringspakketten van het Berichtencentrum op dezelfde instantie waren geïnstalleerd. (NEO-47674)
* Er is een probleem verholpen met de workflow **Facturering** die mislukte wanneer tabellen met de primaire sleutel waren gedefinieerd als een tekenreeks in plaats van een geheel getal. (NEO-46254)
* Er is een probleem verholpen met heatmapfilters als de naam van de workflow te lang was. (NEO-46301)
* Er is een probleem verholpen dat werd geïntroduceerd in 7.3.1 op de Snowflake FDA-connector waardoor records werden verwijderd bij gebruik van &quot;0 of 1 cardinality simple join&quot; tijdens verrijking. (NEO-48737)
* Er is een probleem verholpen met Snowflake FFDA bij gebruik van de sorteerparameter in de workflowactiviteit **Splitsen**. (NEO-45899)
* Er is een probleem verholpen waardoor u de externe accountconfiguratie niet kon opslaan. Het externe account wordt nu automatisch opgeslagen na de verbindingstest voor connectoren met parsermogelijkheden (Snowflake en Google BigQuery). (NEO-47636)
* Er is een probleem verholpen waardoor u geen datatype Tijd kon invoegen in de workflowactiviteit **Gegevensupdate** op MSSQL. (NEO-47763)
* Er is een probleem verholpen waardoor het MTA-proces crashte wanneer de tijdzone van de engine niet was ingesteld (specifiek voor MSSQL). (NEO-46619)
* Er is een probleem verholpen met het importeren van HTML-bestanden wanneer afbeeldingsnodes (img) URL&#39;s met personalisatievelden bevatten. (NEO-48396)
* Er is een HTTP 500-fout verholpen bij pogingen om verbinding te maken met een instantie waarbij de `limit`-node niet werd geconfigureerd in het serverConf.xml-bestand.
* Er is een probleem verholpen dat kon leiden tot de foutmelding &#39;Tekenset komt niet overeen&#39; bij het gebruik van bepaalde functies, zoals `to_nclob` met een Oracle Unicode-database waar NChar niet was ingeschakeld. (NEO-49361)
* Er is een probleem verholpen dat tot een fout leidde wanneer een gebruiker met leestoegangsrechten voor de map nmsDeliveryMapping probeerde een campagne of workflow uit te voeren. (NEO-48230)
* Er is een probleem verholpen waardoor de functie `JSPContext.sqlExecWithOneParam` niet werkte. (NEO-50066)
* Verschillende omleidingsfouten zijn opgelost. (NEO-50030)
