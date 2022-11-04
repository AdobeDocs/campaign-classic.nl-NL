---
product: campaign
title: Technische workflows
description: Meer informatie over de technische workflows die beschikbaar zijn bij Campaign Classic-pakketten.
feature: Workflows
exl-id: 9aed2665-cd4b-419c-b9f2-ea04fc1d8f01
source-git-commit: 1635366b9e1302acd3d8997312bf07d5c1a68982
workflow-type: tm+mt
source-wordcount: '1705'
ht-degree: 3%

---

# Technische workflows{#about-technical-workflows}

![](../../assets/v7-only.svg)

## Technische workflows {#overview}

De workflows die in deze sectie worden beschreven, worden geïnstalleerd met de verschillende ingebouwde Adobe Campaign-pakketten. Deze pakketten en de bijbehorende technische workflows zijn afhankelijk van uw licentieovereenkomst. De ingebouwde pakketten worden gedetailleerd in [deze sectie](../../installation/using/installing-campaign-standard-packages.md).

Standaard zijn technische workflows beschikbaar in een submap van het volgende knooppunt: **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

De technische werkschema&#39;s kunnen slechts door exploitanten met het recht van het Beleid worden begonnen en worden gewijzigd. Raadpleeg deze voor meer informatie over machtigingen [sectie](../../platform/using/access-management-groups.md#default-groups).

>[!NOTE]
>
>De technische werkschema&#39;s met betrekking tot de module van het Centrum van het Bericht zijn beschikbaar door gebrek in **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]** knooppunt.

Raadpleeg voor meer informatie over het controleren van technische workflows de [speciale sectie](monitoring-technical-workflows.md).

## Lijst met technische workflows {#list-technical-workflows}

| Technische workflow | Pakket | Beschrijving |
|------|--------|-----------|
| **Aliasreiniging** (aliasCleansing) | Levering | Deze werkstroom normaliseert opsommingswaarden. Deze wordt standaard elke dag om 3 uur geactiveerd. |
| **Facturering** (facturering) | Levering | Deze workflow stuurt het systeemactiviteitenrapport per e-mail naar de &#39;factureringsoperator&#39;. Het wordt teweeggebracht 25e van elke maand op de instantie van de Marketing. |
| **Berekening van Twitter-statistieken** (statsTwitter) | Sociale netwerken (sociale marketing) - Alleen campagne v7 | Deze workflow berekent statistieken over retweets en bezoeken aan Twitter. |
| **Campagnebanen** (operationMgt) | Marketingcampagnes (Campagne) | In deze workflow worden de taken voor marketingcampagnes beheerd (starttaken, bestanden uitpakken, enz.). Het leidt ook tot werkschema&#39;s met betrekking tot terugkomende en periodieke campagnes. |
| **Gegevens verzamelen voor de service HeatMap** (collectDataHeatMapService) | Standaard geïnstalleerd | Deze werkstroom wint gegevens terug die door de dienst HeatMap worden vereist. |
| **Verzoeken om privacy verzamelen** (collectPrivacyRequests) | Verordening inzake bescherming van privacydata | Met deze workflow worden de gegevens van de ontvanger gegenereerd die in Adobe Campaign zijn opgeslagen en kunnen deze worden gedownload op het scherm van de privacyaanvraag. |
| **Kostprijsberekening** (begrotingsbeheer) | Marketingcampagnes (Campagne) | Deze workflow start de berekening van kosten en kostenposten voor de begrotingen, plannen, programma&#39;s, campagnes, leveringen en taken. |
| **Database opschonen** (opruimen) | Levering | Deze workflow is de workflow voor databaseonderhoud: het maakt verschillende berekeningen van de statistieken en de processen, en schrapt verouderde gegevens van het gegevensbestand volgens de bepaalde configuratie in de plaatsingsmedewerker. Het wordt teweeggebracht elke dag om 4am door gebrek. Raadpleeg [deze sectie](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic) voor meer informatie. |
| **Geblokkeerde lijngebruikers verwijderen** (deleteBlockedLineUsersV2) | LINE-kanaal | Deze workflow zorgt ervoor dat de gegevens van de gebruikers van de LIJN V2 worden verwijderd nadat ze de officiële account van de LIJN gedurende 180 dagen hebben geblokkeerd. |
| **Gegevens over privacyverzoeken verwijderen** (deletePrivacyRequestsData) | Verordening inzake bescherming van privacydata | Deze workflow verwijdert de gegevens die de ontvanger in Adobe Campaign heeft opgeslagen. |
| **Leveringsindicatoren** (leveringsindicatoren) | Midsourcingplatform | Deze werkstroom werkt leveringsvolgindicatoren voor een levering bij. Deze workflow wordt standaard elke uur geactiveerd. |
| **Discussieformeprocessen** (newsgroupMgt) | Marketing resources (MRM) | Deze workflow beheert de levering van meldingen van discussieforums. Deze gebeurtenis wordt geactiveerd wanneer een goedkeuringssignaal wordt ontvangen |
| **Verspreide marketingprocessen** (centralLocalMgt) | Centrale/lokale Marketing (Distributed Marketing) | Deze workflow begint met het verwerken van de gedistribueerde marketingmodule. Het lanceert de verwezenlijking van lokale campagnes en beheert berichten met betrekking tot orden en campagnepakketbeschikbaarheid. |
| **Gebeurtenis leegmaken** (webAnalyticsPurgeWebEvents) | Webanalytische connectors | Met deze workflow kunt u elke gebeurtenis uit het databaseveld verwijderen op basis van de periode die is geconfigureerd in het veld Lifespan. |
| **Soorten publiek exporteren naar de Adobe Experience Cloud** (exportSharedAudience) | Integratie met Adobe Experience Cloud | Deze workflow exporteert soorten publiek als gedeeld publiek/segmenten. Deze doelgroepen kunnen worden gebruikt in de verschillende Adobe Experience Cloud-oplossingen die u gebruikt. |
| **Voorspelling** (prognoses) | Levering | Deze workflow analyseert leveringen die zijn opgeslagen in de voorlopige kalender (maakt voorlopige logbestanden). Het wordt teweeggebracht elke dag bij 1am door gebrek. |
| **Volledige geaggregeerde berekening (voorzettingskubus)** (agg_nmsproposition_rcp_full) | Aanbiedingsengine (interactie) | Deze workflow werkt het volledige aggregaat voor de keuzelijst met voorstellen van aanbiedingen bij. Het wordt teweeggebracht elke dag om 6 uur door gebrek. In dit aggregaat worden de volgende afmetingen vastgelegd: Kanaal, levering, marketingaanbieding en datum. De blokje van het voorstel van de Aanbieding wordt dan gebruikt om rapporten te produceren die op voorstellen worden gebaseerd. Meer informatie over kubussen vindt u in [deze sectie](../../reporting/using/ac-cubes.md). |
| **Identificatie van omgezette contactpersonen** (webAnalyticsFindConverted) | Webanalytische connectors | Deze workflow indexeert bezoekers van de site die hun aankoop hebben voltooid na een campagne voor het opnieuw op de markt brengen van producten. De gegevens die door deze workflow worden hersteld, zijn toegankelijk via het efficiëntierapport voor opnieuw in de handel brengen (zie deze pagina). |
| **Publiek importeren uit de Adobe Experience Cloud** (importSharedAudience) | Integratie met Adobe Experience Cloud | Met deze workflow kunt u soorten publiek/segmenten van verschillende Adobe Experience Cloud-oplossingen importeren in Adobe Campaign. |
| **Banen op leveringen in campagnes** (deliveryMgt) | Marketingcampagnes (Campagne) | Deze workflow activeert de goedgekeurde leveringen en start de naverwerking van de serviceprovider voor een externe levering. Het verzendt ook goedkeuringsberichten en herinneringen. |
| **Banen voor dienstverleners** (providerMgt) | Marketingcampagnes (Campagne) | Dit werkschema begint de leverancier (e-mail aan de router en post-verwerking) te verwerken zodra de leveringen zijn goedgekeurd. |
| **Update van toegangstoken LINE V2** (updateLineV2AccessToken) | LINE-kanaal - alleen campagne v7 | Deze werkstroom verfrist het toegangstoken aan LIJN V2. |
| **MID naar migratie naar LineUserID** (MIDToUserIDMigration) | LINE-kanaal | Deze workflow genereert de LINE V2-gebruikers-id voor migratie van LIJN V1 naar LIJN V2. |
| **Meldingen over marketingbronnen** (assetManagement) | Marketing resources (MRM) | Deze workflow beheert meldingen die verband houden met de goedkeuring en publicatie van marketingbronnen. |
| **Berichtencentrum &lt;external_account_name>** (mcSynch_&lt;external_account_name>) | Transactionaal berichtenbeheer (Berichtcentrum - Controle) | Deze workflow: <ul><li>Hiermee wordt de lijst met gebeurtenissen hersteld die door de bewerking(en) zijn verwerkt.</li><li>synchroniseert met de tabel NmsBroadLogMsg om de kwalificaties van de leveringsberichten te herstellen.</li><li>Hiermee worden de logbestanden voor gebeurtenislevering hersteld zodra de synchronisatie met de tabel NmsBroadLogMsg is voltooid.</li><li>synchroniseert met de tabel NmsTrackingUrl om de tracking voor bezorgings-URL&#39;s te herstellen.</li><li>Hiermee worden URL&#39;s voor het bijhouden van gebeurtenissen hersteld zodra de synchronisatie met de tabel NmsTrackingUrl is voltooid.</li><li>Hiermee kunt u alle e-mailadressen herstellen die elke drie uur nadat een levering is verzonden, in quarantaine zijn geplaatst.</li></ul> |
| **MessageCenter volledige geaggregeerde berekening** (agg_messageCenter_full) | Transactionaal berichtenbeheer (Berichtcentrum - Controle) | Deze werkstroom werkt het Volledige aggregaat voor de kubus van het Centrum van het Bericht bij. Deze wordt standaard elke dag om 3 uur geactiveerd. In dit aggregaat worden de volgende afmetingen vastgelegd: Het type Kanaal, Datum, Status en Gebeurtenis. De kubus van het centrum van het Bericht wordt dan gebruikt om rapporten te produceren die op gebeurtenissen worden gebaseerd. Meer informatie over kubussen vindt u in [deze sectie](../../reporting/using/ac-cubes.md) |
| **Midden-sourcing (leveringstellers)** (defaultMidSourcingDlv) | Overdracht naar midsourcing | Deze workflow verzamelt tellingsinformatie voor leveringen op de server voor midsourcing. De telgegevens omvatten algemene leveringsindicatoren zoals het aantal verzonden leveringen, enz. Trackinggegevens zoals die worden geopend, worden niet opgenomen. Deze wordt standaard om de tien minuten geactiveerd. |
| **Midden-sourcing (leveringslogboeken)** (defaultMidSourcingLog) | Overdracht naar midsourcing | Deze workflow verzamelt leveringslogboeken op de server voor midsourcing. Deze wordt standaard elke uur geactiveerd. |
| **NMAC-opt-out-beheer** (mobileAppOptOutMgt) | Kanaal voor mobiele apps | Met deze workflow worden afmeldingsopties op mobiele apparaten bijgewerkt. Het wordt teweeggebracht om de 6 uur tussen 1am en middernacht. Raadpleeg voor meer informatie [deze sectie](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines). |
| **Melding voorstel** (aanbiedingsbeheer) | Levering | Deze workflow implementeert goedgekeurde aanbiedingen in de onlineomgeving en in elke categorie in de aanbiedingencatalogus. |
| **Opschonen van gepauzeerde workflows** (CleupPausedWorkflows) | Levering | In deze workflow worden gepauzeerde workflows geanalyseerd waarvoor de ernst is ingesteld op Normaal en worden waarschuwingen en meldingen geactiveerd wanneer deze al te lang zijn gepauzeerd. Na een maand worden gepauzeerde technische workflows onvoorwaardelijk gestopt. Standaard wordt de activering elke maandag om 17.00 uur gestart. Raadpleeg voor meer informatie [Afhandeling van gepauzeerde workflows](monitoring-workflow-execution.md#handling-of-paused-workflows). |
| **Opmaak van privacyverzoek** (cleanPrivacyRequests) | Verordening inzake bescherming van privacydata | Deze workflow wist de bestanden met toegangsverzoeken die ouder zijn dan 90 dagen. |
| **Batchgebeurtenissen verwerken** (batchEventsProcessing) | Transactiebericht uitvoeren (Berichtcentrum - Uitvoering) | Met deze workflow kunt u batchgebeurtenissen in een wachtrij plaatsen voordat u ze aan een berichtsjabloon koppelt. |
| **Real-time gebeurtenissen verwerken** (rtEventsProcessing) | Transactiebericht uitvoeren (Berichtcentrum - Uitvoering) | Dit werkschema laat u gebeurtenissen in real time in een rij zetten alvorens hen met een berichtmalplaatje te associëren. |
| **Propositiesynchronisatie** (propositionSynch) | Besturing van de aanbiedingsengine met uitvoeringsinstantie | Deze workflow synchroniseert voorstellingen tussen de marketinginstantie en de uitvoeringsinstantie die voor interacties wordt gebruikt. |
| **Herstel van webgebeurtenissen** (webAnalyticsGetWebEvents) | Webanalytische connectors | Elk uur downloadt deze workflow segmenten op het gedrag van internetgebruikers op een bepaalde site, plaatst deze in de Adobe Campaign-database en start de workflow voor het opnieuw in de handel brengen. |
| **Rapportageaggregaten** (reportingAggregates) | Levering | Deze workflow werkt aggregaten bij die worden gebruikt in rapporten. Het wordt teweeggebracht elke dag om 2 uur door gebrek. |
| **Verzending van indicatoren en campagnerekenmerken** (webAnalyticsSendMetrics) | Webanalytische connectors | Met deze workflow kunt u e-mailcampagneindicatoren van Adobe Campaign naar Adobe Experience Cloud Suite verzenden via de Adobe® Analytics-connector. De betrokken indicatoren zijn als volgt: Verzonden (Verzonden), Totaal aantal van opent (iTotalRecipientOpen), Totaal aantal ontvangers die klikte (iTotalRecipientClick), Fouten (iError), Opt-Out (opt-out) (iOptOut). |
| **Voorraad: Orders en waarschuwingen** (stockMgt) | Marketingcampagnes (Campagne) | Deze workflow start voorraadberekening op de orderregels en beheert drempelwaarden voor waarschuwingen. |
| **Facebook-ventilatoren synchroniseren** (syncFacebookFans) | Sociale netwerken (sociale marketing) - Alleen campagne v7 | Deze workflow importeert elke dag om 7.00 uur Facebook-fans naar Adobe Campaign. |
| **Facebook-pagina&#39;s synchroniseren** (syncFacebook) | Sociale netwerken (sociale marketing) - Alleen campagne v7 | Deze workflow synchroniseert elke dag om 7.00 uur Facebook-pagina&#39;s met Adobe Campaign. |
| **Twitter-pagina&#39;s synchroniseren** (syncTwitter) | Sociale netwerken (sociale marketing) - Alleen campagne v7 | Deze workflow importeert elke dag om 7.00 uur Twitter-volgers naar Adobe Campaign. |
| **Taakmelding** (taskMgt) | Marketingbronnen (MRM) - alleen campagne v7 | Met deze workflow kunt u meldingen verzenden met betrekking tot taken in marketingcampagnes. |
| **Tekstspatiëring** (reeksspatiëring) | Levering | Deze workflow voert het herstel en de consolidatie van trackinggegevens uit. Het verzekert ook de herberekening van het volgen en leveringsstatistieken, vooral die gebruikt door het archiveren van het Centrum van het Bericht werkschema. Deze wordt standaard één keer per uur geactiveerd. |
| **Status van gebeurtenis bijwerken** (updateEventsStatus) | Transactiebericht uitvoeren (Berichtcentrum - Uitvoering) | Met deze workflow kunt u een status aan een gebeurtenis toewijzen. Gebeurtenisstatussen zijn als volgt:<ul><li>In behandeling: de gebeurtenis bevindt zich in een wachtrij. Er is nog geen berichtsjabloon aan gekoppeld.</li><li>In afwachting van levering: Als de gebeurtenis zich in een wachtrij bevindt, is er een berichtsjabloon aan gekoppeld en wordt deze momenteel verwerkt door de levering.</li><li>Verzonden: deze status wordt gekopieerd uit de leveringslogboeken. Dit betekent dat de levering is verzonden.</li><li>Genegeerd door de levering: deze status wordt gekopieerd uit de leveringslogboeken. Het betekent dat de levering is genegeerd.</li><li>Afleveringsfout: deze status wordt gekopieerd uit de leveringslogboeken. Het betekent dat de levering is mislukt.</li><li>Gebeurtenis niet gedekt: de gebeurtenis is niet gekoppeld aan een berichtsjabloon. De gebeurtenis wordt niet opnieuw verwerkt.</li></ul> |
| **Vernieuwen voor leverbaarheid** (DeliabilityUpdate) | Levering | Deze workflow wordt elke avond uitgevoerd en beheert de kwalificatieregels voor stuiterende e-mailadressen, evenals de lijst met domeinen en MX&#39;s. Hiervoor moet de HTTPS-poort open zijn op het platform. |