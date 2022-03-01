---
product: campaign
title: Nieuwste release
description: De nieuwste aanvullende informatie voor Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8278228a6610e99f9400343bc967e16f2759dfbe
workflow-type: tm+mt
source-wordcount: '1257'
ht-degree: 83%

---

# Nieuwste release{#latest-release}

![](../../assets/v7-only.svg)

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van Campaign Classic v7**. Elke nieuwe build heeft een status die wordt aangegeven door een kleur. Meer informatie over de build-statussen van Campaign Classic v7 vindt u op [deze pagina](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Release 7.2.2 - build 4349 {#release-7-2-2}

_1 maart 2022_

**Patches**

* Probleem verholpen tijdens het configureren van de **Webanalyse** externe account, die ervoor zorgde dat de integratiestatus altijd &#39;Integratie succesvol&#39; weergaf, zelfs als er fouten optraden. (NEO-36672)
* Oplossing voor verschillende postupgradefouten die te maken hadden met het mechanisme van de reeks-id bij een negatieve id. (NEO-43205, NEO-42846, NEO-42845)
* Probleem verholpen tijdens het gebruik van de **Webanalyse** externe account met terugkerende en doorlopende leveringen, waardoor gegevens van de externe rekening gedeeltelijk verloren zijn gegaan. (NEO-38548)
* Probleem verholpen waardoor de postupgrade vertraagde bij het bijwerken van de tabel NmsActiveContact. (NEO-43206)
* Probleem verholpen met een fout na de upgrade die optrad als mappen buiten het vak waren verplaatst van het dialoogvenster **Beheer** naar een andere locatie. (NEO-42875)
* Probleem verholpen bij het gebruik van een **Gegevens bijwerken** workflowactiviteit die kan voorkomen dat het ontvangende schema wordt bijgewerkt met de ontvangende gegevens uit een externe Google Cloud-database. (NEO-42343)
* Probleem verholpen tijdens naupgrade met betrekking tot de Adobe Analytics-aansluiting. (NEO-43318, NEO-38136)
* Probleem verholpen met een overschreven CUID door &#39;VALUE_TO_CHANGE&#39; tijdens postupgrade. (NEO-43267)
* Probleem verholpen dat tot fouten leidde bij het synchroniseren van de mid-sourcing en marketing instanties in een multi-mid configuratie. (NEO-10432)
* Probleem verholpen dat tot een fout leidde bij het vernieuwen van de leverbare werkstroom wanneer er meer dan 1000 uitzendingen tegelijk werden aangeboden. (NEO-40276)
* Probleem verholpen waardoor de open ratio niet kon worden bijgewerkt en op leveringsindicatoren voor de verhouding kon worden geklikt. (NEO-43253)

## ![](assets/do-not-localize/green_2.png) Release 7.2.1 - build 9346 {#release-7-2-1}

_10 januari 2022_

**Beveiligingsverbetering**

Er zijn verschillende beveiligingsverbeteringen aangebracht in FDA-accounts:

* Wanneer u uw externe FDA-account configureert, kunt u zich nu aanmelden bij uw Snowflake-account met behulp van sleutelpaarverificatie voor verbeterde verificatiebeveiliging. [Meer informatie](../../installation/using/configure-fda-snowflake.md)
* Wanneer u uw externe FDA-account configureert, kunt u zich nu aanmelden bij uw Azure Synapse Analytics-account met behulp van de door het systeem toegewezen beheerde identiteit. [Meer informatie](../../installation/using/configure-fda-synapse.md#azure-external)
* Alle verwijzingen naar de log4j-bibliotheek zijn uit Campaign verwijderd om een optimale beveiliging te garanderen.

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
