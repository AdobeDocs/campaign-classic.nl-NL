---
product: campaign
title: Toegang tot marketingcampagnes
description: Toegang tot marketingcampagnes
role: User
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 2%

---

# Toegang tot marketingcampagnes{#accessing-marketing-campaigns}

Met Adobe Campaign kunt u marketingcampagnes maken, configureren, uitvoeren en analyseren. Alle marketing campagnes kunnen van een verenigd controlecentrum worden beheerd.

## Beginselen van de werkruimte {#workspace-basics}

### Startpagina {#home-page}

Als u eenmaal verbinding hebt met Adobe Campaign, bladert u door de verschillende mogelijkheden via koppelingen in de navigatiebalk.


![](assets/campaign_global_view.png)


Campagne-elementen vindt u in het dialoogvenster **[!UICONTROL Campaigns]** tab: hier ziet u een overzicht van de marketingprogramma&#39;s, campagnes en hun subsets. Een marketingprogramma bestaat uit campagnes die bestaan uit leveringen, taken, gekoppelde middelen, enz. In het kader van het marketingcampagnebeheer met behulp van campagnes worden de gegevens over leveringen, begrotingen, revisoren en bijbehorende documenten in de campagnes gevonden.

De **[!UICONTROL Browsing]** van de **[!UICONTROL Campaigns]** biedt verschillende ingangen aan, afhankelijk van modules die op de instantie worden geïnstalleerd. U hebt bijvoorbeeld toegang tot:

* **Campagnekalender**: kalender van plannen, marketingprogramma&#39;s, leveringen en campagnes. Zie [Campagnekalender](#campaign-calendar).
* **Campagnes**: toegang tot de campagnes in alle marketingprogramma&#39;s.
* **Leveringen**: toegang tot de met de campagnes verband houdende leveringen.
* **Webtoepassingen**: toegang tot webtoepassingen (formulieren, bestemmingspagina&#39;s, enz.).

>[!NOTE]
>
>Raadpleeg voor meer informatie over de algemene ergonomie van Adobe Campaign, machtigingen en functies voor profielbeheer [deze sectie](../../platform/using/adobe-campaign-workspace.md).
>
>Alle functies met betrekking tot kanalen en leveringen worden nader beschreven in [deze sectie](../../delivery/using/steps-about-delivery-creation-steps.md).

### Campagnekalender {#campaign-calendar}

Elke campagne behoort tot een programma dat op zijn beurt deel uitmaakt van een plan. Abonnementen, programma&#39;s en campagnes zijn toegankelijk via de **[!UICONTROL Campaign calendar]** in het menu **Campagnes** tab.

Als u een abonnement, programma, campagne of levering wilt bewerken, klikt u op de naam van het abonnement in de kalender en klikt u vervolgens op **[!UICONTROL Open...]**. Het wordt dan getoond in een nieuw lusje, zoals hieronder getoond:

![](assets/d_ncs_user_interface_hierar.png)

U kunt de informatie filteren die in de campagnecalender wordt weergegeven: klik op de knop **[!UICONTROL Filter]** en selecteer de filtercriteria.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>Wanneer u filtert op een datum, worden alle campagnes met een begindatum die later is dan de opgegeven datum en/of met een einddatum die ouder is dan de opgegeven datum, weergegeven. Selecteer datums met de kalenders rechts van elk veld.

U kunt ook de opdracht **[!UICONTROL Search]** veld om de weergegeven items te filteren.

Met de pictogrammen die aan elk item zijn gekoppeld, kunt u de status van het item weergeven: voltooid, bezig, bewerkt, enzovoort.

### Bladeren in een marketingprogramma {#browsing-in-a-marketing-program}

Met campagnes kunt u een reeks programma&#39;s beheren die uit verschillende marketingcampagnes bestaan. Elke campagne bevat leveringen en de bijbehorende processen en middelen.

#### Door een programma bladeren {#browsing-a-program}

Wanneer u een programma bewerkt, gebruikt u de onderstaande tabbladen om door het programma te bladeren en het te configureren.

* De **Schema** wordt de agenda van de programma&#39;s weergegeven voor een maand, week of dag, afhankelijk van het tabblad waarop u in de kalenderkoptekst klikt.

  Indien nodig kunt u een campagne, programma of een taak maken via deze pagina.

  ![](assets/s_ncs_user_interface_campaign02.png)

* De **Bewerken** kunt u het programma aanpassen: naam, begin- en einddatum, budget, gekoppelde documenten, enz.

  ![](assets/s_ncs_user_interface_campaign05.png)

#### Browsercampagnes {#browsing-campaigns}

Campagnes zijn toegankelijk via de campagnemalender, de **[!UICONTROL Schedule]** van het programma of de lijst van campagnes.

1. Selecteer via de campagnemalender de campagne die u wilt weergeven en klik op de knop **[!UICONTROL Open]** koppeling.

   ![](assets/campaign_planning_edit_op.png)

   De campagne wordt bewerkt op een nieuw tabblad, zoals hieronder wordt weergegeven:

   ![](assets/campaign_op_edit.png)

1. Via de **[!UICONTROL Schedule]** van het programma is de bewerkingsmodus gelijk aan de campagnecalender.
1. Via de **[!UICONTROL Campaigns]** koppeling van de **[!UICONTROL Campaigns]** klikt u op de naam van de campagne die u wilt bewerken.

   ![](assets/campaign_edit_from_list.png)

### Een campagne besturen {#controlling-a-campaign}

#### Dashboard {#dashboard}

Voor elke campagne worden taken, bronnen en leveringen gecentraliseerd in één scherm, het dashboard, waarmee u marketingacties kunt beheren in samenwerking met anderen.

Het dashboard van een campagne wordt gebruikt als controleinterface. De belangrijkste fasen van het maken en het beheer van de campagne worden rechtstreeks door het programma geopend: leveringen, extractiebestanden, meldingen, budgetten, enz.

![](assets/s_ncs_user_op_board_start_del.png)

Met Adobe Campaign kunt u samenwerkingsprocessen opzetten voor het opzetten en goedkeuren van de verschillende stadia van marketing- en communicatiecampagnes: goedkeuring van de begroting, het doel, de inhoud, enz.

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>De configuratie van campagnemalplaatjes wordt voorgesteld in [Campagnersjablonen](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### Schema {#schedule}

Een campagne centraliseert een reeks leveringen. Voor elke campagne, biedt het programma een globale mening van alle componenten aan: u kunt de taken en de leveringen tonen, en tot hen gemakkelijk toegang hebben.

![](assets/campaign_planning_tab.png)

#### Forum {#forum}

Voor elke campagne kunnen exploitanten berichten uitwisselen via een speciaal forum.

Meer informatie in [Discussieforums](../../mrm/using/discussion-forums.md).

#### Rapporten {#reports}

De **[!UICONTROL Reports]** via de koppeling hebt u toegang tot de campagnerapporten .

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>De rapporten worden gedetailleerd in [deze sectie](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Configuratie {#configuration}

Campagnes worden gemaakt via campagnemalplaatjes. U kunt herbruikbare sjablonen configureren waarvoor sommige opties zijn geselecteerd en andere instellingen al zijn opgeslagen. Voor elke campagne wordt de volgende functionaliteit aangeboden:

* Verwijzing van [documenten en middelen](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents): u kunt documenten aan de campagne koppelen (korte beschrijving, rapport, afbeeldingen, enz.). Alle documentindelingen worden ondersteund.
* Kosten definiëren: voor elke campagne kunt u met Adobe Campaign definiëren [kostenposten en kostenberekeningsstructuren](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories) die kunnen worden gebruikt bij het maken van de marketingcampagne. Bijvoorbeeld: afdrukkosten, gebruik van een externe instantie, huur van ruimte.
* Vaststellen van doelstellingen: u kunt kwantificeerbare doelstellingen voor een campagne bepalen, bijvoorbeeld aantal abonnees, bedrijfsvolume, enz. Deze informatie wordt later gebruikt in campagnerapporten.
* Beheer [zaadadressen](../../delivery/using/about-seed-addresses.md) en [controlegroepen](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).
* Goedkeuringen beheren: u kunt de behandelingen selecteren die u wilt goedkeuren en, indien nodig, de revisieoperatoren of -groepen selecteren. [Meer informatie](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)

>[!NOTE]
>
>Om tot de campagneconfiguraties toegang te hebben en veranderingen in hen aan te brengen, klik **[!UICONTROL Advanced campaign parameters...]** in de **[!UICONTROL Edit]** tab.

## De webinterface gebruiken {#using-the-web-interface-}

U kunt de Adobe Campaign-consoleschermen openen via een internetbrowser om alle campagnes en leveringen, alsmede rapporten en informatie over de profielen in uw database weer te geven. Met deze toegang kunt u geen records maken. Afhankelijk van de rechten van de operator kunt u de gegevens in de database bekijken en/of bewerken. U kunt bijvoorbeeld de inhoud van de campagne goedkeuren, een levering opnieuw starten of stoppen, enzovoort.

1. Meld u op de gebruikelijke manier aan via https://`<your instance>:<port>/view/home`.
1. Via de menu&#39;s hebt u toegang tot de overzichten.

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

Naast het navigeren over campagnes en het bekijken van hen, kunt u deze soorten taken uitvoeren:

* De activiteit van de monitor op een geval
* Deelnemen aan validatieprocessen, bijvoorbeeld een leveringsinhoud goedkeuren of afwijzen
* Andere snelle handelingen uitvoeren, bijvoorbeeld een werkstroom pauzeren
* Alle rapportfuncties openen
* Deelnemen aan forumdiscussies

In deze tabel worden de acties samengevat die u kunt uitvoeren op campagnes vanuit een browser:

| Pagina  | Actie |
| --- | --- |
| Lijst met campagnes, leveringen, aanbiedingen, enz. | Een lijstitem verwijderen |
| Campaign | Een campagne annuleren |
| Levering | De inhoud en het doel van de levering goedkeuren<br/>De leveringsinhoud verzenden<br/>Levering bevestigen<br/>Een levering onderbreken en stoppen |
| Webtoepassing | Een webtoepassing maken<br/>De inhoud en eigenschappen van de toepassing bewerken<br/>De toepassingsinhoud opslaan als een sjabloon<br/>De toepassing publiceren |
| Voorstel | Inhoud en geschiktheid van aanbieding goedkeuren<br/>Een online aanbieding uitschakelen |
| Taak | Een taak voltooien<br/>Een taak annuleren |
| Marketingbronnen | Een resource goedkeuren<br/>Een bron vergrendelen en ontgrendelen |
| Campagne | Een pakket ter goedkeuring indienen<br/>Een pakket goedkeuren of afwijzen<br/>Een pakket annuleren |
| Campagnevolgorde | Een bestelling maken<br/>Een bestelling accepteren of afwijzen <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| Voorraad | Een voorraadlijn verwijderen |
| Aanbiedingssimulatie | Een simulatie starten en stoppen |
| Doelworkflow | Een workflow starten, pauzeren en stoppen |
| Rapporteren | De huidige gegevens opslaan in de rapportgeschiedenis |
| Forum | Een discussie toevoegen<br/>Reageren op een boodschap in een gesprek<br/>Een discussie volgen en het abonnement opzeggen |

### Goedkeuringen

Goedkeuringen (bijvoorbeeld van een doel of een leveringsinhoud) kunnen via webtoegang worden uitgevoerd.

![](assets/campaign_web_interface_validation.png)

U kunt ook de koppeling gebruiken die zich in de meldingen bevindt. Raadpleeg voor meer informatie hierover [Controle en goedkeuring van leveringen](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
