---
product: campaign
title: Migreren naar de Adobe Analytics-connector
description: Campagne - Veelgestelde vragen over Analytics Connector
feature: Technote, Analytics Integration
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Is alleen van toepassing op v7 on-premise en hybride implementaties"
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
hide: true
hidefromtoc: true
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 1%

---

# Hoe te om bestaande Genesis integratie aan de Schakelaar van Adobe Analytics te migreren {#acc-aa-faq}

Vanaf de release van Campaign Classic v7 21.1.3 is de Adobe Analytics Data Connector afgekeurd. [Meer informatie](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html?lang=nl-NL)

Op 1 augustus 2021 is Adobe Campaign Classic verwijderd van de oude interface van Data Connectors, maar de bestaande integratie van de Campagne zal tot 17 augustus 2022 gegevens verzamelen en doorgeven aan Adobe Analytics. Na deze datum zal de integratie ophouden gegevens te verzamelen en door te geven aan Adobe Analytics.

U **moeten** de nieuwe integratie van de Adobe Analytics Connector op Adobe Exchange die de verouderde integratie van Data Connectors vervangt. Voor meer informatie over Adobe Analytics Connector raadpleegt u [deze pagina](../../integrations/using/gs-aa.md).

Voor alle vragen over deze wijzigingen leest u de [Veelgestelde vragen](#faq-aa). Neem voor meer informatie contact op met [Klantenservice Adoben](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

>[!NOTE]
>
>Als u migreert vanaf een bestaande Adobe Analytics Data Connector (voorheen bekend als Genesis integration) en u de Nieuwe classificatiearchitectuur in Adobe Analytics gebruikt, hebt u buildversies nodig die beginnen vanaf 7.3.1 of 8.4.1 om te kunnen migreren naar de nieuwe Adobe Analytics Connector.

## Wat is er veranderd?

Er is nu een nieuwe integratie tussen Campaign Classic v7 en Adobe Analytics beschikbaar. Belangrijke wijzigingen worden hieronder weergegeven.

* De **Contactdatum** De classificatie, die van type datum is, is verouderd door Adobe Analytics. Voor gemigreerde integratie zal het van hetzelfde type blijven. Voor alle **Contactdatum** gemaakt door Campagne, wordt het type **String**.

* **Verwerkingsregels** door Adobe Campaign worden gecreëerd als onderdeel van nieuwe integraties. Willekeurig **Verwerkingsregels** moet handmatig worden gemaakt vanuit Adobe Analytics of rechtstreeks gebruikmaken van de JavaScript-implementatie aan de clientzijde. **Verwerkingsregels** blijven behouden voor bestaande integraties.

* De ingebouwde technische workflows en hun gedrag blijven hetzelfde. Alleen de back-end-API&#39;s die door de workflows worden gebruikt om gegevens van en naar Adobe Analytics te verzenden of aan te trekken, zijn gewijzigd.

* Let erop dat de `nlserver` Het proces moet met de gebruiker van de technische IMS-account worden geconfigureerd om de nieuwe aansluiting te laten werken. Deze verandering moet gebeuren door Adobe. Neem contact op met [Klantenservice Adoben](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Als u Adobe Genesis API&#39;s was in aangepaste workflows voor het ophalen en doorsturen van gegevens vanuit Adobe Analytics, moet u nu de nieuwe Adobe Analytics 1.4/2.0 API&#39;s gebruiken. [Meer informatie](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Heb je invloed op?

Als u de bestaande Verbinding van Gegevens van Adobe Analytics gebruikt (die vroeger als Genesis integratie wordt bekend), en de integratie werd uitgevoerd op een lagere bouwstijl dan Campagne 21.1.3, wordt u beïnvloed.

Leer hoe u uw versie kunt controleren [in deze sectie](../../integrations/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Hoe kan ik bijwerken?

U moet een upgrade uitvoeren naar Campagne 21.1.3 (of meer) **vóór 17 augustus 2022**.

Als gehoste klant werkt de Adobe samen met u om uw exemplaar(s) te upgraden naar de nieuwere versie. U kunt dan [Adobe Analytics-connector](../../platform/using/gs-aa.md).

Als klant op locatie/hybride klant moet u een upgrade uitvoeren naar een van de nieuwere versies om van de nieuwe integratie te kunnen profiteren.
Zodra alle instanties worden bevorderd, zult u kunnen [de nieuwe integratie uitvoeren](../../integrations/using/adobe-analytics-provisioning.md) naar Adobe Analytics Connector en zorg voor een naadloze overgang.

## Veelgestelde vragen{#faq-aa}

**Hoe krijg ik logboeken?**

Configuratie en workflows van gebruikersinterfaces zijn uitgerust met **uitgebreid** registreren.

In de uitgebreide modus worden de verzoek- en antwoordheaders ook afgedrukt voor elke API-aanvraag naar Adobe Analytics.

Als gebruiker op locatie kunt u de breedtelodus als volgt implementeren:

* Om uitgebreide wijze voor het gebruikersinterface toe te laten: rerun `web` in de uitgebreide modus te verwerken.
* Om uitgebreide wijze voor toe te laten **webAnalytics** workflows: selecteer de **Uitvoeren in de motor** van de werkschemaeigenschappen, en re-run `wfserver` in uitgebreide modus.

**Wat betekent de fout &#39;Integratie-eigenaar niet-beheerder&#39;?**

Meer informatie over de Data Connectors `Integration Owner Not Admin` Fout in [deze pagina](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Wat gebeurt er met oude gegevens en rapportreeksen als de migratie naar de nieuwe connector is voltooid?**

Na migratie zal een nieuwe schakelaar (die van de oude schakelaar wordt gemigreerd) beginnen gegevens aan die zelfde rapportreeks te duwen en de bestaande gegevens zullen niet worden beïnvloed: het zal aan de bestaande gegevens toevoegen.

**Sommige bestaande gebeurtenissen/gebeurtenissen/rapportsuites in Analytics zijn niet zichtbaar in Campagne. Wat moet ik doen?**

Integratie is afhankelijk van gegevens over Technical Account Token voor dagelijkse werking. Als er geen toestemming aan een dimensie/metrisch/rapportreeks van het productprofiel verbonden aan de Gebruiker van de Technische Rekening is, zullen APIs die wij gebruiken eenvoudig voor die verzoeken vastlopen.

Als wij voor details van een component Analytics (zoals metriek/afmetingen/segmenten/rapportreeksen) lezen, zal API deze componenten in het resultaat niet terugkeren (die als iets kunnen kijken geschrapt op de zijde van Analytics of niet aanwezig is). De API voor Analytics zal deze aanvragen en foutmeldingen negeren.

De oplossing is het bijwerken van de **Productprofiel** in Analytics User Context of Technical User Token met de nieuw gemaakte/ontbrekende componenten door deze componenten toe te voegen in [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}. Voor meer hulp, contacteer [Klantenservice Adoben](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Nuttige koppelingen

* [Upgrade uw omgeving](../../production/using/build-upgrade.md)
* [Veelgestelde vragen over buildupgrades](../../platform/using/faq-build-upgrade.md)
* [Build Campaign Classic downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [De nieuwe clientconsole beschikbaar maken voor gebruikers](../../installation/using/client-console-availability-for-windows.md)
* [Campagne-clientconsole installeren](../../installation/using/installing-the-client-console.md)
