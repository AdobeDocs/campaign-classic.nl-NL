---
product: campaign
title: Nieuwste release
description: De nieuwste aanvullende informatie voor Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: cdbcfc5aa0614e41ce76cb777fec58fbd01797d2
workflow-type: ht
source-wordcount: '903'
ht-degree: 100%

---

# Nieuwste release {#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van Campaign Classic v7**. Elke nieuwe build heeft een status die wordt aangegeven door een kleur. Meer informatie over de build-statussen van Campaign Classic v7 vindt u op [deze pagina](rn-overview.md).

## Release 7.4.2  {#release-7-4-2}

### Versie 9391 {#build-9391}

[!BADGE Beperkte beschikbaarheid]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Beperkte beschikbaarheid"}

_12 mei 2025_

Deze versie bevat de volgende oplossingen:

* Probleem verholpen dat zich na de upgrade voordeed bij niet-Oracle-instellingen. (NEO-87012)
* Er is een TLS/HTTPS-backendprobleem opgelost dat zowel de clientconsole als de server trof. (NEO-87432)

### Versie 9390 {#build-9390}

[!BADGE Algemene beschikbaarheid]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Algemene beschikbaarheid"}

_2 april 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

**Beveiligingsverbeteringen**

Deze release bevat verschillende beveiligingsoplossingen.

De verbinding met Adobe-oplossingen en -toepassingen via het **[!UICONTROL Adobe Experience Cloud]** externe account is bijgewerkt om de beveiliging te verbeteren.

**Belangrijke oplossingen**

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


**Andere oplossingen**

De volgende problemen zijn ook opgelost in deze release:

* Probleem verholpen waarbij de activiteit **Gegevens laden (bestand)** er niet in slaagde bestanden naar de server te uploaden<!--after an upgrade to version 8.3.8-->. Gebruikers kunnen nu bestanden uploaden zonder vastgelopen voortgang of consolefouten. (NEO-47269)

* Fouten met segmentatie in Apache opgelost <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349-->. Deze oplossing voorkomt het genereren van kernbestanden en zorgt voor een stabiele werking van de server. (NEO-59059)

* Een connectiviteitsprobleem opgelost met de Google BigQuery-database <!--after upgrading to version 7.3.3 build 9359-->. Gebruikers kunnen nu verbindingen testen via het externe GCP-account. (NEO-62455)

* Verbeterde compatibiliteit voor kolomupdates van Boolean en Datetime in Google BigQuery-tabellen met FDA (Federated Data Access). Deze oplossing zorgt voor een correcte verwerking van gegevenstypen tijdens het invoegen/bijwerken. (NEO-65774)

* Een kwetsbaarheid voor resource-injectie verholpen, waardoor aanvallers HTML-elementen in e-maileindpunten konden injecteren. Deze beveiligingsverbetering voorkomt ongeoorloofde toegang en phishing-pogingen. (NEO-66462)

* Oplossing voor periodiek optredende fouten bij het invoegen van gegevens in Google BigQuery-tabellen als gevolg van problemen met HTTP-content of overdrachtscodering. Deze oplossing zorgt voor stabiele workflows voor het laden van gegevens. (NEO-66989)

* Kwetsbaarheid voor path traversal in de `File.list()`-methode binnen workflows verholpen. Deze beveiligingsverbetering voorkomt ongeoorloofde toegang tot mappen en beschermt vertrouwelijke bestanden. (NEO-77898)

* Probleem verholpen waarbij SMS-leveringslogboeken niet correct werden bijgewerkt naar de status &#39;Ontvangen op mobiel&#39;. Deze verbetering zorgt voor een nauwkeurige leveringsrapportage. (NEO-78843)

* Aanmeldingsfouten opgelost in Adobe Campaign Classic bij gebruik van Azure Federated Data Access (FDA). Gebruikers kunnen nu inloggen via de clientconsole. (NEO-79373)

* Een crash verholpen in workflows die werd veroorzaakt door de `CCurlAzureBlobStorage::UploadStream()`-methode. Deze verbetering zorgt voor een stabiele uitvoering van de workflow. (NEO-79598)

* Twee kritieke compilatievlaggen (`ControlFlowGuard` en `StackProtection`) in Windows geactiveerd om de beveiliging van het product te verbeteren en exploitatierisico&#39;s te beperken. (NEO-80145)

* Probleem verholpen waarbij gebeurtenisstatussen onjuist werden verzonden terwijl de broadlog zich in een mislukte status bevond. Deze verbetering zorgt voor nauwkeurige gebeurtenisrapportage. (NEO-80245)

* POP3 OAuth vernieuwen en toegangstoken worden nu opgeslagen in de database en de fout `Authentication failure: unknown user name or bad password` wordt niet meer weergegeven nadat de vernieuwingstoken is verlopen. (NEO-80683)

* Een optie `XApiKey` wordt nu gebruikt als waarde voor de client-id om verbinding te maken met Adobe Analytics in plaats van de client-id van de externe account van Marketing Cloud (MAC). (NEO-80434)

* Probleem opgelost waarbij authenticatiefouten optraden bij inMail-gebruikers als gevolg van het verlopen van een token. Gebruikers kunnen nu de verbinding testen en de server opnieuw opstarten om vergelijkbare problemen op te lossen. (NEO-80683)

* Verbeterde analytische API-functionaliteit door ervoor te zorgen dat alle analytische oproepen een consistente API-sleutel (Campaign1) voor verificatie gebruiken, zelfs wanneer wordt overgeschakeld naar een willekeurige client-id. Dit zorgt voor naadloze analysetracering. (NEO-80434)

* BigQuery Federated Data Access-connector (FDA) verbeterd door gebruikers de time-outperiode voor query&#39;s te laten aanpassen. Deze verbetering verhindert time-outfouten tijdens langlopende query&#39;s. (NEO-81222)

* Het upgradeproces voor de release van Campaign <!--7.4.1--> is bijgewerkt en bevat de vereiste afhankelijkheden. Deze verbetering vereenvoudigt het upgradeproces voor gebruikers. (NEO-81433)

* Probleem verholpen waarbij de console vastliep wanneer een subworkflow werd gebruikt in combinatie met een `enum`-veld. Deze verbetering zorgt voor een stabiele uitvoering van de workflow. (NEO-81864)

* Oplossing voor een probleem waarbij onderliggende MTA-processen vastliepen, waardoor leveringsslots werden geblokkeerd. Deze oplossing zorgt voor een soepele levering van Push- en WhatsApp-communicatie. (NEO-82351)

* Probleem verholpen waarbij leveringen bleven hangen in personalisatie in behandeling door onderbroken leveringsactiviteiten. Deze verbetering zorgt voor een succesvolle uitvoering van de levering. (NEO-82781)

* Verbeterde aanmeldingsfunctionaliteit voor IMS door gebruik te maken van het CampaignIO-eindpunt voor authenticatie. Deze verbetering stroomlijnt het inlogproces. (NEO-82838)

* Time-outfouten in Google BigQuery Federated Data Access (FDA) verholpen om een stabiele query-uitvoering te garanderen na de implementatie van een hotfix. (NEO-82923)

* Oplossing voor een ruimteprobleem bij het laden van grote gegevensvolumes in Teradata-tabellen. Deze verbetering zorgt voor het stabiel laden van gegevens. (NEO-83252)

* Probleem verholpen waarbij GCP-query&#39;s mislukten vanwege onjuiste datum- en tijdstempelvergelijkingen <!--after upgrading to version 9383-->. Deze verbetering zorgt voor compatibiliteit met query&#39;s. (NEO-83826)

* Oplossing voor mislukte leveringen die werden veroorzaakt door het hervatten van onderbroken leveringsactiviteiten. Deze oplossing zorgt voor een succesvolle uitvoering van de levering. (NEO-83809)

* Oplossing voor authenticatiefouten met de FDA-connector (Snowflake Federated Data Access) bij gebruik van Private Key Authentication. Deze verbetering zorgt voor succesvolle databaseverbindingen. (NEO-84024)

* Watchdog-wijzigingen geïmplementeerd om onderliggende MTA-sleufblokkade door vastzittende processen aan te pakken. Deze verbetering zorgt voor een soepele levering. (NEO-84553)

* Verbeterde JavaScript-wachtcontroles om onderliggende MTA-sleufblokkade aan te pakken die door processen in een werkende staat wordt veroorzaakt. Deze oplossing zorgt voor een stabiele levering. (NEO-85150)

