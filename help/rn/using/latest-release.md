---
product: campaign
title: Nieuwste release
description: De nieuwste aanvullende informatie voor Campaign Classic v7
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 155fbcd2846cfc5a8db25194bd8d7007356db24e
workflow-type: tm+mt
source-wordcount: '1869'
ht-degree: 57%

---

# Nieuwste release{#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van Campaign Classic v7**. Elke nieuwe build heeft een status die wordt aangegeven door een kleur. Meer informatie over de build-statussen van Campaign Classic v7 vindt u op [deze pagina](rn-overview.md).

## Release 7.3.4 - build 9364 {#release-7-3-4}

[!BADGE Algemene beschikbaarheid]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Algemene beschikbaarheid"}

>[!CAUTION]
>
>De upgrade van Client Console is verplicht. Lees op deze [pagina](../../installation/using/installing-the-client-console.md) hoe u uw Client Console kunt upgraden.
>
> Als u [Campagne - Microsoft Dynamics CRM Connector](../../platform/using/crm-connectors.md), moet u zowel uw marketing als uw midsourcingservers met deze nieuwe build upgraden.

_7 september 2023_

**Beveiligingsverbetering**

* De beveiliging in IMS API&#39;s is verbeterd. Client-sensitive informatie (d.w.z. toegangstokens) is verwijderd uit URL parameters. Deze gegevens worden nu verzonden in de koptekst voor postgegevens of autorisaties, zodat een veiliger communicatieproces mogelijk is. (NEO-63045)
* De beveiliging in webapps is verbeterd om DDOS-aanvallen te voorkomen. (NEO-50757)
* De beveiliging is verbeterd om te voorkomen dat PII-gegevens worden weergegeven in weblogfouten. (NEO-46827)
* De beveiliging is geoptimaliseerd om te voorkomen dat het beveiligingstoken wordt opgenomen in de URL van de startpagina van de campagne. (NEO-38519)

**Compatibiliteitsupdates**

* Tomcat is bijgewerkt naar versie 8.5.91
* De bibliotheek libexpat is bijgewerkt naar 2.5.0 om de beveiliging te verbeteren. (NEO-51023)

**Verbeteringen**

* De parameter MaxWorkingSetMb in het dossier van de serverconfiguratie (serverConf.xml) is gewijzigd om geheugentoewijzing voor leveringen te optimaliseren. (NEO-49204)
* De externe BigQuery-account is uitgebreid met nieuwe opties die worden gebruikt voor het instellen van de GCloud SDK. (NEO-63879) [Meer informatie](../../installation/using/configure-fda-google-big-query.md#google-external)
* Een nieuwe `cusHeader` is toegevoegd aan het configuratiebestand van de server (serverConf.xml). Hiermee kunt u aangepaste koppen toevoegen wanneer u een bestand van een externe server uploadt. (NEO-58339) [Meer informatie](../../installation/using/the-server-configuration-file.md#cusheaders).
* Het beheer van het trackinglogbestand is verbeterd en voorkomt negatieve id&#39;s voor lastMsgId. Het is veranderd van int32 in int64. (NEO-52290)
* De workflow voor het leveren van statistieken (mid-sourcing) is toegevoegd. Deze nieuwe werkstroom synchroniseert de gegevens van de leveringsstatistiek (nms:deliveryStatus) van het midden aan de marketing instantie. (NEO-36802)

**Patches**

* Probleem verholpen die kon voorkomen wanneer een de dienstverzoek voorafgaand aan login IMS werd gemaakt, als de de vraagauthentificatie van het de dienstverzoek een de dienstteken gebruikte. (NEO-64903)
* Oplossing voor een probleem met regressie dat bij gebruik van de Digital Content Editor tot schuifproblemen kan leiden. (NEO-64671, NEO-59256)
* Probleem met regressie verholpen bij het plakken van inhoud van Excel naar de Digital Content Editor. (NEO-63287)
* Probleem verholpen waardoor webapps niet correct konden worden weergegeven in de v5-compatibiliteitsmodus. (NEO-63174)
* Probleem verholpen waarbij niet-beheerders webAnalytics-leveringen niet konden verzenden. (NEO-62750)
* Probleem verholpen waarbij browsers geen extra spaties konden toevoegen wanneer voorwaardelijke inhoud in een levering werd gebruikt. (NEO-62132)
* Oplossing voor een regressieprobleem dat ervoor zorgde dat de berekening van de actieve contactpersoon niet correct werkte in de factureringsworkflow bij het gebruik van doelschema&#39;s gekoppeld aan meerdere logschema&#39;s. (NEO-61468)
* Probleem verholpen dat tot een fout kon leiden en ertoe kon leiden dat u niet kon schuiven wanneer u de inhoud van een levering bewerkt. (NEO-61364)
* Probleem verholpen waarbij een pop-upvenster werd geopend wanneer werd geklikt op een afbeelding in de e-mailinhoudeditor. (NEO-60752)
* Probleem verholpen waarbij speciale tekens in de HTML-inhoud van een levering onjuist werden gecodeerd in verschillende browsers. (NEO-60081)
* Oplossing voor een synchronisatieprobleem dat kon optreden bij gebruik van de inSMS-workflowactiviteit. (NEO-59544)
* Probleem verholpen bij gebruik van de Big Query-connector met tijdstempel- of datetime-velden. (NEO-59502, NEO-49768)
* Probleem verholpen waarbij cumulatieve leveringsrapporten niet konden worden gebruikt. (NEO-59211)
* Probleem verholpen dat tot fouten kon leiden bij het delen van publiek met de People Core Service. (NEO-58637)
* Probleem verholpen bij het weergeven van de spiegelpagina van een levering. (NEO-58325)
* Probleem opgelost waarbij de xtk-expressie XtkLibrary.Right() niet werkte. (NEO-57870)
* Probleem opgelost waarbij het stijlkenmerk van de body-tag werd gewijzigd tijdens het uploaden van een afbeelding in de Digital Content Editor. (NEO-57697)
* Probleem verholpen met speciale tekens tijdens het uitvoeren van batchexport met de CRM-connectoractiviteit. (NEO-54300)
* Probleem verholpen waarbij het laden van grote hoeveelheden niet kon werken met gegevenstypen &quot;tekenreeks&quot; bij het gebruik van een activiteit voor het laden van gegevens en de Big Query-connector. (NEO-53748)
* Probleem met cachesleutel verholpen waarbij renderingproblemen konden optreden. (NEO-51516, NEO-49995)
* Probleem verholpen dat tot een validatiefout kon leiden bij het verzenden van een directe-maillevering met targetMapping met goedkeuringen. (NEO-50758)
* Probleem met querybeheer opgelost, wat van invloed zou kunnen zijn op de prestaties van de levering. (NEO-49991)
* Probleem verholpen waarbij bij het gebruik van externe accounts in workflowleveringsactiviteiten voor campagnes problemen met de configuratie van externe accounts konden ontstaan. (NEO-49959)
* Probleem met prestaties verholpen bij het verzenden van pushberichten. (NEO-49953) Het volgende probleem is opgelost: Japanse tekens kunnen bij het exporteren van rapporten onjuist worden weergegeven (NEO-49308).
* Probleem opgelost waarbij in het Tomcat-foutrapport te veel foutgegevens werden weergegeven. (NEO-49029)
* Probleem verholpen dat tot een leveringsfout kan leiden bij het gebruik van een groot aantal voorstellen. (NEO-48807)
* Probleem verholpen waardoor de **Gegevens bijwerken** de workflowactiviteit werkt niet correct. (NEO-48140)
* Probleem verholpen waarbij klik op het bijhouden van gegevens niet kon worden gesynchroniseerd voor leveringen met een andere externe account dan e-mail.(NEO-47277)
* Probleem verholpen waardoor traceringslogboeken in real time niet konden worden gesynchroniseerd op de marketinginstantie van Message Center. (NEO-42540)
* Probleem verholpen waardoor het voorvoegsel van de werkruimte niet kon worden weergegeven in het detectievenster van een schema, voor databasetabellen van de Snowflake. (NEO-40297)
* Probleem verholpen dat was voorkomen `<img-amp>` -tags van werken in e-mailinhoud. (NEO-38685)
* Probleem verholpen waarbij de archiveringsworkflow van het Message Center zou kunnen mislukken bij gebruik van een HTTP-relais. (NEO-33783)
* Probleem verholpen waarbij lettertypenaam en -grootte zouden kunnen resulteren in fouten in de e-mailinhoudseditor. (NEO-61342)

## Release 7.3.3 - build 9359 {#release-7-3-3}

[!BADGE Beperkte beschikbaarheid]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Beperkte beschikbaarheid"}

>[!CAUTION]
>
>De upgrade van Client Console is verplicht. Lees op deze [pagina](../../installation/using/installing-the-client-console.md) hoe u uw Client Console kunt upgraden.

_20 maart 2023_

**Beveiligingsverbetering**

* Tomcat is bijgewerkt van versie 8.5.81 naar 8.5.85 om de beveiliging te optimaliseren. (NEO-56936)

**Verbeteringen**

* De factureringsworkflow is verbeterd om de prestaties te optimaliseren. (NEO-47658)
* De trackingworkflow is verbeterd om de prestaties bij grote leveringen te optimaliseren. (NEO-45064)
* Trackingbeheer is verbeterd om mogelijke problemen met dynamische parameters in URL&#39;s op te lossen. Trackingbeheer v3 verwerkt nu URL&#39;s van het ajax-type (met parameters na een &#39;#&#39;) af en voorkomt dat tools van derden tracking-URL&#39;s kunnen wijzigen. Neem contact op met Adobe om deze wijziging toe te passen. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**Patches**

* Probleem verholpen waardoor proef-pushberichten voor iOS niet konden worden verzonden van de controle-instantie (context transactionele berichten). (NEO-54713)
* Probleem verholpen waardoor scrollen soms niet mogelijk was in het tabblad **Bewerken** van de Digital Content Editor (DCE). (NEO-54474)
* Probleem verholpen waarbij twee verrijkingsactiviteiten dezelfde naam-ID gebruikten in hun koppeling, waardoor de tweede verrijkingsactiviteit de koppelingen van de eerste gebruikte. (NEO-48851)

## Release 7.3.2 - build 9356 {#release-7-3-2}

[!BADGE Beperkte beschikbaarheid]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Beperkte beschikbaarheid"}

_21 november 2022_

>[!CAUTION]
>
>De upgrade van Client Console is verplicht. Lees op deze [pagina](../../installation/using/installing-the-client-console.md) hoe u uw Client Console kunt upgraden.

**Compatibiliteitsupdates**

* Adobe Campaign is nu compatibel met PostgreSQL 14. Raadpleeg deze [technische opmerking](../../technotes/using/tech-stack-upgrade.md) voor meer informatie.

* Na afloop van de levensduur van Microsoft Internet Explorer 11 gebruikt de HTML-renderingengine voor dashboards in de clientconsole nu Edge Chromium. (NEO-20741)

Ontdek meer in de [Campaign-compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md#RDBMSservers).

**Verbeteringen**

* De Google BigQuery-connector biedt nu volledige ondersteuning voor booleaanse velden. (NEO-49181)
* U kunt nu de geldigheidsduur van de IMS-cookies configureren in de `Configuration for the redirection service`-sectie van het bestand serverConf.xml. Dit geldt voor de volgende cookies: `uuid230`, `nllastdelid` en `AMCV_` (NEO-42541)
* Het IP-adres kan nu worden verborgen in het /r/test-verzoek door `showSourceIP` in te stellen op false in de omleidingsnode van het bestand serverConf.xml. [Meer informatie](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

**Afgeschafte functies**

* Social marketing met Facebook is nu afgeschaft. U kunt Twitter-integratie gebruiken om te posten op sociale media. U kunt ook met Adobe werken om een aangepast kanaal te maken.
* ACS Connector (primeaanbieding) is nu afgeschaft. U kunt de export-/importcapaciteiten van Campaign gebruiken voor het extraheren en injecteren van gegevens in beide producten.

Meer informatie vindt u op de pagina [Afgeschafte en verwijderde functies](deprecated-features.md).

**Andere wijzigingen**

* Weblogboeken zijn verbeterd: `logonEscalation`-waarschuwingen worden nu alleen weergegeven voor gebruikers met beheerdersrechten. (NEO-47167)
* Om fouten te voorkomen wordt de workflow **Gegevens verzamelen voor Heatmap-service** (collectDataHeatMapService) nu standaard gestopt. (NEO-33959)
* Er zijn verschillende verbeteringen geïmplementeerd om het CPU-gebruik voor het campagnedashboard te optimaliseren. (NEO-46417)
* De loadLibraryDebug JS-methode is verwijderd om crashes te voorkomen. (NEO-46968)
* De resterende verwijzingen naar de bibliotheek log4j zijn verwijderd uit de installatie van Campaign in Windows. (NEO-44851)

**Patches**

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
