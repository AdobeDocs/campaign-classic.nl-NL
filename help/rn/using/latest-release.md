---
product: campaign
title: Nieuwste release
description: De nieuwste aanvullende informatie voor Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 458821770c6233ec1893d4efe60169516b311bdd
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 26%

---

# Nieuwste release {#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van Campaign Classic v7**. Elke nieuwe build heeft een status die wordt aangegeven door een kleur. Meer informatie over de build-statussen van Campaign Classic v7 vindt u op [deze pagina](rn-overview.md).

## Release 7.4.2 - build 9390 {#release-7-4-2}

[!BADGE Algemene beschikbaarheid]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Algemene beschikbaarheid"}

_2 april 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Beveiligingsverbeteringen {#security-7-4-2}

Deze release bevat verschillende beveiligingsoplossingen.

De verbinding met Adobe-oplossingen en -toepassingen via het **[!UICONTROL Adobe Experience Cloud]** externe account is bijgewerkt om de beveiliging te verbeteren.

### Belangrijkste correcties {#release-7-4-2-fixes}

Deze release bevat de volgende belangrijkste oplossingen:

* TLS-/SMPP-verbinding - Problemen opgelost met SMPP-stabiliteit

* Oplossingen voor Google BigQuery:

   * Problemen met regressies van BOOLEAN-gegevenstypen opgelost
   * Problemen met proxy-instellingen opgelost
   * Problemen met regressies van het gegevenstype DATETIME opgelost
   * Problemen met de stabiliteit van bulksgewijs laden opgelost
   * Verbeterde interne tests op ODBC-versies
   * Probleem verholpen met speciale tekens in verbindingstekenreeks
   * Standaardtime-out (5 minuten) voor Google BigQuery-query&#39;s verwijderd

* Mail Transfer Agent (MTA) - Probleem opgelost met een verweesde onderliggende MTA die vast bleef zitten op de status **[!UICONTROL Start pending]**.


### Andere oplossingen {#release-7-4-2-other-fixes}

De volgende problemen zijn ook opgelost in deze release:

* Oplossing voor een kwestie waar de **Gegevens die (dossier) laden** activiteit er niet in slaagde om dossiers aan de server <!--after an upgrade to version 8.3.8--> te uploaden. Gebruikers kunnen nu bestanden uploaden zonder vastgelopen voortgang of consolefouten. (NEO-47269)

* Fouten in segmentatiefouten in Apache opgelost <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349-->. Met deze oplossing wordt het genereren van kernbestanden voorkomen en wordt een stabiele serverbewerking gegarandeerd. (NEO-59059)

* Een connectiviteitsprobleem opgelost met de Google BigQuery-database <!--after upgrading to version 7.3.3 build 9359--> . Gebruikers kunnen nu verbindingen testen met succes via de externe GCP-account. (NEO-62455)

* Verbeterde compatibiliteit voor kolomupdates van Boolean en Datetime in Google BigQuery-tabellen met FDA (Federated Data Access). Deze correctie zorgt voor een correcte verwerking van gegevenstypen tijdens invoegen/bijwerken-bewerkingen. (NEO-65774)

* Oplossing voor een kwetsbaarheid bij de injectie van bronnen waardoor aanvallers HTML-elementen in e-maileindpunten konden injecteren. Deze beveiligingsverbetering voorkomt ongeoorloofde toegang en phishingpogingen. (NEO-66462)

* Oplossing voor periodiek optredende fouten bij het invoegen van gegevens in Google BigQuery-tabellen vanwege problemen met HTTP-inhoud of overdrachtcodering. Deze oplossing zorgt voor stabiele workflows voor het laden van gegevens. (NEO-66989)

* Oplossing voor een kwetsbaarheid met betrekking tot padtraversal in de methode `File.list()` in workflows. Deze beveiligingsverbetering voorkomt ongeoorloofde toegang tot mappen en beschermt vertrouwelijke bestanden. (NEO-77898)

* Probleem verholpen waarbij de SMS-leveringslogboeken niet correct werden bijgewerkt naar de status &#39;Ontvangen op mobiel&#39;. Deze verbetering zorgt voor nauwkeurige leveringsrapportage. (NEO-78843)

* Oplossing voor aanmeldingsfouten in Adobe Campaign Classic bij gebruik van Azure Federated Data Access (FDA). Gebruikers kunnen zich nu met succes aanmelden via de clientconsole. (NEO-79373)

* Probleem verholpen waarbij een crash optrad in workflows die door de methode `CCurlAzureBlobStorage::UploadStream()` werden veroorzaakt. Deze verbetering verzekert stabiele werkschemauitvoering. (NEO-79598)

* Activeerde twee kritieke compilatiemarkeringen (`ControlFlowGuard` en `StackProtection`) op Vensters om productveiligheid te verbeteren en exploitatierisico&#39;s te verlichten. (NEO-80145)

* Probleem verholpen waarbij gebeurtenisstatussen onjuist werden verzonden terwijl de broadlog in een mislukte status verkeerde. Deze verbetering zorgt voor nauwkeurige gebeurtenisrapportage. (NEO-80245)

* POP3 OAuth vernieuwt en toegangstoken wordt nu opgeslagen in de database en de fout `Authentication failure: unknown user name or bad password` wordt niet meer weergegeven nadat het token voor vernieuwen is verlopen. (NEO-80683)

* Een optie `XApiKey` wordt nu gebruikt als een waarde voor de client-id om verbinding te maken met Adobe Analytics in plaats van de client-id van de externe account van Marketing Cloud (MAC) te gebruiken. (NEO-80434)

* Oplossing voor een probleem waarbij inMail-gebruikers verificatiefouten ondervonden als gevolg van een verlopen token. Gebruikers kunnen nu de verbinding testen en de server opnieuw starten om vergelijkbare problemen op te lossen. (NEO-80683)

* Verbeterde functionaliteit van de analyse API door ervoor te zorgen dat alle analytische aanroepen een consistente API-sleutel (Campaign1) voor verificatie gebruiken, zelfs wanneer wordt overgeschakeld naar een willekeurige client-id. Dit zorgt voor naadloze analysetracering. (NEO-80434)

* Verbeterde de BigQuery Federated Data Access-connector (FDA) door gebruikers de time-outperiode voor query&#39;s te laten aanpassen. Deze verbetering verhindert onderbrekingsfouten tijdens langlopende vragen. (NEO-81222)

* Het upgradeproces van de release Campagne <!--7.4.1--> is bijgewerkt en bevat de vereiste afhankelijkheden. Deze verbetering vereenvoudigt het verbeteringsproces voor gebruikers. (NEO-81433)

* Probleem verholpen waarbij de console vastliep wanneer een subworkflow werd gebruikt in combinatie met een `enum` -veld. Deze verbetering verzekert stabiele werkschemauitvoering. (NEO-81864)

* Oplossing voor een probleem waarbij MTA-onderliggende processen vastzaten en leveringssleuven blokkeerden. Deze moeilijke situatie verzekert vlotte leveringsverrichtingen voor de mededelingen van de Push en WhatsApp. (NEO-82351)

* Probleem verholpen waarbij leveringen in afwachting van pauze in personalisatie vastzaten. Deze verbetering zorgt voor een geslaagde uitvoering van de levering. (NEO-82781)

* Verbeterde IMS login functionaliteit door het eindpunt CampaignIO voor authentificatie leveraging. Deze verbetering stroomlijnt het login proces. (NEO-82838)

* Aangepaste time-outfouten in FDA (Google BigQuery Federated Data Access) voor een stabiele implementatie van de query na hotfix. (NEO-82923)

* Oplossing voor een ruimteprobleem bij het laden van grote gegevensvolumes in Teradata-tabellen. Deze verbetering zorgt voor stabiele bewerkingen voor het laden van gegevens. (NEO-83252)

* Probleem verholpen waarbij GCP-query&#39;s mislukten vanwege onjuiste datum- en tijdstempelvergelijkingen <!--after upgrading to version 9383--> . Deze verbetering verzekert vraagverenigbaarheid. (NEO-83826)

* Oplossing voor mislukte aflevering die werd veroorzaakt door hervatting van onderbroken afleveringsactiviteiten. Deze oplossing zorgt voor een geslaagde uitvoering van de levering. (NEO-83809)

* Oplossing voor verificatiefouten met de FDA-connector (Snowflake Federated Data Access) bij gebruik van Private Key Authentication. Deze verbetering zorgt voor geslaagde databaseverbindingen. (NEO-84024)

* Geïmplementeerde waakhond verandert om MTA kindgroefblokkering aan te pakken die door vastgezette processen wordt veroorzaakt. Deze verbetering zorgt voor vloeiende leveringsbewerkingen. (NEO-84553)

* Uitgebreide JavaScript wacht controles om MTA kindgroefblokkering aan te pakken die door processen in een werkende staat wordt veroorzaakt. Deze moeilijke situatie verzekert stabiele leveringsverrichtingen. (NEO-85150)

