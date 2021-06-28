---
product: campaign
title: Migreren naar de Adobe Analytics-connector
description: Campagne - Veelgestelde vragen over Analytics Connector
hide: true
hidefromtoc: true
source-git-commit: 41478c656ffd4e113788149e6cca9ed00602789e
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 5%

---

# Migreren naar Adobe Analytics Connector {#acc-aa-faq}

Vanaf de release van Campaign Classic v7 21.1.3 is de Adobe Analytics Data Connector afgekeurd. [Meer informatie](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

Op 1 augustus 2021 wordt Adobe Campaign Classic verwijderd uit de interface voor oude gegevensconnectors, maar de bestaande integratie van de campagne zal tot 1 maart 2022 gegevens blijven verzamelen en doorgeven aan Adobe Analytics. Op 1 maart 2022 zal de integratie ophouden gegevens te verzamelen en door te geven aan Adobe Analytics.

U moet aan de nieuwe integratie van de Verbinding van Adobe Analytics op de Uitwisseling van Adobe migreren die de integratie van de Verbindingen van erfenisGegevens vervangt, zoals die in [deze pagina](../platform/using/adobe-analytics-connector.md) wordt beschreven.


>[!NOTE]
>
>Voor alle vragen over deze wijzigingen leest u de [Veelgestelde vragen](#faq-aa). Neem voor meer informatie contact op met de [klantenservice van Adobe](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Wat is er veranderd?

Er is nu een nieuwe integratie tussen Campaign Classic v7 en Adobe Analytics beschikbaar. Belangrijke wijzigingen worden hieronder weergegeven.

* De integratie tussen Adobe Campaign Classic en Adobe Analytics-verificatie is van gebruiker/wachtwoord naar Adobe Identity Management Service (IMS) verplaatst. Dientengevolge, moet u Adobe IMS uitvoeren, en met Campagne [via een Adobe ID ](../integrations/using/about-adobe-id.md) verbinden, alvorens de implementatie van de Verbinding van Analytics te beginnen.

* De **Contactdatum**-classificatie, die als datumnotatie wordt gebruikt, is vervangen door Adobe Analytics. Voor gemigreerde integratie zal het van hetzelfde type blijven. Voor elke **Contactdatum** die door Campagne wordt gemaakt, is het type **String**.

* **Verwerkingsregels** worden door Adobe Campaign gemaakt als onderdeel van nieuwe integraties. Of **Verwerkingsregels** zouden manueel van Adobe Analytics moeten worden gecreeerd of direct gebruik cliënt-zij implementatie Javascript. **De verwerkingsregels** blijven intact voor bestaande integratie.

* De ingebouwde technische workflows en hun gedrag blijven hetzelfde. Alleen de back-end-API&#39;s die door de workflows worden gebruikt om gegevens van en naar Adobe Analytics te verzenden of aan te trekken, zijn gewijzigd.

* Merk op dat het `nlserver` proces met de Gebruiker van de Technische Rekening IMS voor de nieuwe schakelaar zou moeten worden gevormd om te werken. Deze wijziging moet door Adobe worden doorgevoerd. Neem contact op met de [Adobe-klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om dit te implementeren.

* Als u Adobe Genesis API&#39;s was in aangepaste workflows voor het ophalen en verplaatsen van gegevens uit Adobe Analytics, moet u nu de nieuwe Adobe Analytics 1.4/2.0 API&#39;s gebruiken. [Meer informatie](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Heeft dit gevolgen voor u?

Als u de bestaande Verbinding van Gegevens van Adobe Analytics gebruikt (die vroeger als Genesis integratie wordt bekend), en de integratie werd uitgevoerd op een lagere bouwstijl dan Campagne 21.1.3, wordt u beïnvloed.

Leer hoe u uw versie [in deze sectie ](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) controleert.

## Hoe kan ik bijwerken?

U moet aan Campagne 21.1.3 (of meer) **vóór 1 Maart, 2022** bevorderen.

Als gehoste klant werkt Adobe samen met u om uw exemplaar(s) te upgraden naar de nieuwere versie.

Als klant op locatie/hybride klant moet u een upgrade uitvoeren naar een van de nieuwere versies om van de nieuwe integratie te kunnen profiteren.

Zodra alle instanties worden bevorderd, zult u de nieuwe integratie [aan de Schakelaar van Adobe Analytics kunnen uitvoeren, en een naadloze overgang verzekeren.](../platform/using/adobe-analytics-connector.md)


## Veelgestelde vragen{#faq-aa}

**Hoe krijg ik logboeken?**

De configuratie en de werkschema&#39;s van de gebruikersinterface zijn uitgerust met **verbose** registreren.

In de uitgebreide modus worden de verzoek- en antwoordheaders ook afgedrukt voor elke API-aanvraag naar Adobe Analytics.

Als gebruiker op locatie kunt u de breedtelodus als volgt implementeren:

* Om uitgebreide wijze voor het gebruikersinterface toe te laten: voert het `web` proces in uitgebreide wijze opnieuw in.
* Om uitgebreide wijze voor de **webAnalytics** werkschema&#39;s toe te laten: Selecteer de optie **Uitvoeren in de engine** uit de workfloweigenschappen en `wfserver` opnieuw uitvoeren in de uitgebreide modus.

**Wat betekent de fout &#39;Integratie-eigenaar niet-beheerder&#39;?**

Meer informatie over de fout `Integration Owner Not Admin` Gegevensconnectors in [deze pagina](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Wat gebeurt er met oude gegevens en rapportreeksen als de migratie naar de nieuwe connector is voltooid?**

Na migratie wordt een nieuwe aansluiting (gemigreerd van de oude connector) gebruikt om gegevens naar dezelfde rapportsuite te verplaatsen en worden bestaande gegevens niet beïnvloed: het zal aan de bestaande gegevens toevoegen.

**Sommige bestaande gebeurtenissen/gebeurtenissen/rapportsuites in Analytics zijn niet zichtbaar in Campagne. Wat moet ik doen?**

Integratie is afhankelijk van gegevens over Technical Account Token voor dagelijkse werking. Als er geen toestemming aan een dimensie/metrisch/rapportreeks van het productprofiel verbonden aan de Gebruiker van de Technische Rekening is, zullen APIs die wij gebruiken eenvoudig voor die verzoeken vastlopen.

Als wij voor details van een component Analytics (zoals metriek/afmetingen/segmenten/rapportreeksen) lezen, zal API deze componenten in het resultaat niet terugkeren (die als iets kunnen kijken geschrapt op de zijde van Analytics of niet aanwezig is). De API voor Analytics zal deze aanvragen en foutmeldingen negeren.

De oplossing is het **Productprofiel** in Analytics User Context of Technical User Token met de nieuw gecreëerde/ontbrekende componenten bij te werken door deze componenten in [Adobe Admin Console](https://adminconsole.adobe.com/) toe te voegen. Neem voor meer hulp contact op met [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Nuttige koppelingen

* [Upgrade uw omgeving](../production/using/build-upgrade.md)
* [Veelgestelde vragen over buildupgrades](../platform/using/faq-build-upgrade.md)
* [Campaign Classic-build downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [De nieuwe clientconsole beschikbaar maken voor gebruikers](../installation/using/client-console-availability-for-windows.md)
* [Campagne-clientconsole installeren](../installation/using/installing-the-client-console.md)
