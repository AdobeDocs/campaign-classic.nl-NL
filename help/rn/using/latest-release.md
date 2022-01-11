---
product: campaign
title: Nieuwste release
description: De nieuwste aanvullende informatie voor Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 630a62c5e5c9782c5c55fdebd651493a2d68fc54
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 17%

---

# Nieuwste release{#latest-release}

![](../../assets/v7-only.svg)

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van Campaign Classic v7**. Elke nieuwe build heeft een status die wordt aangegeven door een kleur. Meer informatie over de build-statussen van Campaign Classic v7 vindt u op [deze pagina](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Release 7.2.1 - build 9346 {#release-7-2-1}

_10 januari 2022_

**Verbeterde beveiliging**

Er zijn verschillende beveiligingsverbeteringen aangebracht in de FDA-rekeningen:

* ODBC-stuurprogramma&#39;s worden nu rechtstreeks geïnstalleerd met Adobe Campaign Third Parties. Handmatige stappen zijn niet meer vereist om deze stuurprogramma&#39;s te installeren.
* Wanneer u uw externe FDA-account configureert, kunt u zich nu aanmelden bij uw Snowflake-account met behulp van sleutelparverificatie voor uitgebreide verificatiebeveiliging. [Meer informatie](../../installation/using/configure-fda-snowflake.md)
* Wanneer het vormen van uw FDA externe rekening, kunt u nu login aan uw rekening van de Analytics van de Azure synapse gebruikend de systeem-toegewezen beheerde identiteit. [Meer informatie](../../installation/using/configure-fda-synapse.md#azure-external)
* Alle verwijzingen naar de bibliotheek log4j zijn verwijderd uit Campagne om optimale veiligheid te verzekeren.

**Verbeteringen**

* Microsoft Dynamics CRM 365 Connector

   Er zijn kritieke correcties toegepast voor de web-API van Microsoft Dynamics Connector:

   * Probleem verholpen dat optrad tijdens een importeractie die werd geactiveerd door een workflow. Hierdoor werden de lege waarden van tekenreeksvelden opgeslagen als nul in plaats van als lege waarden.
   * Probleem verholpen dat leidde tot de volgende fout voor het importeren of exporteren van gegevens met behulp van web-API-calls: Ongeldige URI: het URI-schema is te lang.
   * Verschillende problemen verholpen bij het importeren, vanuit Microsoft Dynamics 365, van gegevens die opzoekvelden bevatten.

* Google BigQuery FDA-connector

   * Google BigQuery FDA Connector is nu beschikbaar voor gehoste implementaties. [Meer informatie](../../installation/using/configure-fda-google-big-query.md)
   * Toegevoegde ondersteuning voor het inschakelen van verbindingen met een proxyserver voor Google BigQuery FDA-connector. De vereiste volmachtsopties kunnen door het gebied van Opties in de externe rekeningsconfiguratie worden geplaatst. [Meer informatie](../../installation/using/configure-fda-google-big-query.md#google-external)

**Andere wijzigingen**

* Na hun verval zijn de activiteiten van Microsoft CRM, Salesforce, CRM On Demand van het Oracle verwijderd uit de interface. Om de gegevenssynchronisatie tussen Adobe Campaign en een CRM-systeem te configureren, kunt u de activiteit CRM-connector gebruiken. [Meer informatie](../../workflow/using/crm-connector.md)
* De **[!UICONTROL Encrypted identifier]** veld is toegevoegd aan het bezoekersschema (nms:bezoeker). Dit veld wordt berekend en moet worden gebruikt voor webtoepassingen. Dit is van toepassing wanneer het kanaal van de Lijn op de mid-sourcing instantie wordt gevormd.
* De gegevensbronnen van CRM kunnen nu met worden gebruikt **Gegevensbron wijzigen** activiteit.
* Er is een nieuwe optie toegevoegd aan het dialoogvenster **Foutbeheer** eigenschappen van workflowactiviteiten: De **Afbreken bij fout** deze optie wordt automatisch beëindigd. U kunt het daarna niet opnieuw starten (NEO-29661). [Meer informatie](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Een specifieke opeenvolging wordt nu gebruikt om de primaire sleutels voor de lijst te produceren nmsGroup, die wordt gebruikt om statistische groepen van ontvangers tot stand te brengen. Eerder werd de xtknownId-reeks gebruikt. (NEO-30832)
* Toegevoegde ondersteuning voor batch-updatebewerkingen met behulp van de CRM-connectoractiviteit.
* Verbeterde prestaties voor transactionele overseinenverwerkingstijd. (NEO-40370)

**Patches**

* Probleem verholpen bij het maken van een levering die tot een fout in het dialoogvenster **Afbeeldingen** tabblad van het dialoogvenster **Bijhouden en afbeeldingen** venster. Dit gebeurde wanneer het gebruiken van een auto volmachtsconfiguratie. (NEO-33260)
* Probleem verholpen waarbij het uploaden van een bestand naar een HTTPS-server (Debian 10) in synchrone modus werd verhinderd.
* Probleem verholpen waarbij gegevens van de tabel met leveringsstatistieken niet konden worden geregistreerd (`nmsDeliveryLogStats`) worden verwijderd uit de instantie voor midsourcing tijdens het opschonen van de database nadat de gerelateerde leveringen zijn verwijderd. (NEO-31034)
* Probleem verholpen waardoor u geen meldingen voor mobiele apps op iOS kon verzenden tijdens het gebruik van tokenverificatie (NEO-38640).
* Probleem verholpen waarbij berichten met scriptfouten konden worden weergegeven tijdens het maken en configureren van rapporten (NEO-38393).
* Probleem verholpen waarbij de traceringsworkflow op het Oracle zou kunnen mislukken omdat grote hoeveelheden leveringsindicatoren gelijktijdig werden bijgewerkt (NEO-39653).
* Probleem verholpen waardoor een levering niet kon worden verzonden als gevolg van een fout die optrad bij het uitvoeren van een controletype (NEO-39833).
* Probleem verholpen op bestemmingspagina&#39;s waardoor speciale tekens niet correct konden worden weergegeven op de pagina&#39;s met HTML online enquêteantwoorden (NEO-39438).
* Probleem verholpen waardoor de Campaign Classic-console niet kon werken wanneer u met de rechtermuisknop op een van de mappen op het tabblad Explorer klikte (NEO-38884).
* Oplossing een fout wanneer het gebruiken van een eerder gecreeerd leveringsmalplaatje verbonden aan een rekening van de Analyse van het Web in een nieuwe levering waar de configuratie van de Analyse van het Web mist. (NEO-28666)
* Probleem verholpen waardoor u geen voorvertoning kunt weergeven van mobiele leveringen die aan een workflow waren gekoppeld.
* Correctie van een fout die ervoor zorgde dat gepersonaliseerde het volgen URLs niet werden opnieuw gericht wanneer het URL handtekeningsmechanisme voor het volgen van verbindingen werd toegelaten.
* Probleem verholpen waarbij problemen met het indexbeheer konden optreden na de upgrade.
* Oplossing voor een fout die optrad bij het gebruik van de gegevenstypen van het opzoekveld met Microsoft Dynamics CRM in **Importeren** of **Exporteren** workflowactiviteiten.
* Probleem verholpen waardoor u zich niet kon aanmelden bij de console vanwege een probleem met de proxyconfiguratie. (NEO-38388)
* Het probleem van de regressie dat de **Map wissen** werkt niet correct. (NEO-37459)
* Probleem verholpen die tot een fout met een ongeldige aanvraag leidde bij het gebruik van XML-gegevensvelden met de Microsoft Dynamics CRM-account als de xml waarnaar wordt verwezen dubbele aanhalingstekens bevatte.
* Probleem verholpen waarbij problemen met de netwerktime-out onjuist werden geregistreerd als problemen met scriptonderbreking in plaats van netwerkfouten. Dit probleem is opgetreden in het geval van HTTP-aanvragen die in JavaScript-activiteiten zijn opgenomen. (NEO-38079)
* Probleem verholpen waarbij onjuiste resultaten werden geretourneerd tijdens het uitvoeren van de functies Amazon Redshift HoursDiff en MinutesDiff tijdens het uitpakken van de tijdcomponent.(NEO-31673)
* Het probleem dat de **Hot klikken** rapport van ladingen voor leveringen sinds de bouw 9182. (NEO-28900)
* Correctie van een fout die het &amp;-symbool in een URL heeft vervangen door de verwijzing naar de tekeneenheid (`&amp;`) gebruikers geen toegang geven tot de URL die is gekoppeld aan een QR-code. (NEO-28621)
* Probleem verholpen waarbij een nieuwe externe account werd gemaakt telkens wanneer een gebruiker een nieuwe campagneworkflow en een leveringsactiviteit maakte die aan een Web Analytics-account was gekoppeld. Dit is veroorzaakt door een ontbrekende id in het object voor levering van webAnalyticsAccount. (NEO-39691)
* Het probleem dat de **Leeslijst** workflowactiviteit vanaf het moment dat de lijst in de database werd geïdentificeerd met een negatieve id. (NEO-39607)
* Probleem verholpen waarbij **Midden-sourcing (leveringslogboeken)** workflow mislukt. (NEO-39662)
* Probleem verholpen waardoor u geen voorvertoning kon weergeven van e-mailleveringen die aan een workflow waren gekoppeld. (NEO-37840)
* Probleem verholpen waarbij geldige tabellen met lijstwaarden konden worden verwijderd door de workflow voor het opschonen van databases. (NEO-34911)
* Probleem verholpen waarbij de factureringsworkflow vastliep bij marketinginstanties.
