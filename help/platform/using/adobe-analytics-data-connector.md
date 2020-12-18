---
solution: Campaign Classic
product: campaign
title: Adobe Analytics-dataconnector
description: Adobe Analytics-dataconnector
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 1%

---


# Adobe Analytics-dataconnector{#adobe-analytics-data-connector}

## Info over integratie van gegevensconnector {#about-data-connector-integration}

>[!IMPORTANT]
>
>Adobe Analytics Data Connector is niet compatibel met Transaction messaging (Message Center).

Gegevensconnector (voorheen bekend als Adobe Genesis) maakt interactie tussen Adobe Campaign en Adobe Analytics mogelijk via het **Web Analytics-aansluitingen**-pakket. Het stuurt gegevens door naar Adobe Campaign in de vorm van segmenten met betrekking tot gebruikersgedrag na een e-mailcampagne. Omgekeerd verzendt het programma indicatoren en kenmerken van e-mailcampagnes die door Adobe Campaign worden geleverd aan Adobe Analytics - Gegevensconnector.

Met de gegevensconnector biedt Adobe Campaign een manier om het internetpubliek te meten (Web Analytics). Dankzij deze integratie kan Adobe Campaign na een marketingcampagne gegevens over het gedrag van bezoekers van een of meer sites herstellen en (na analyse) hermarketingcampagnes voeren om deze in kopers om te zetten. Omgekeerd, laten de analytische hulpmiddelen van het Web Adobe Campaign toe om indicatoren en campagneattributen aan hun platforms door te sturen.

Raadpleeg de volgende [documentatie](https://helpx.adobe.com/marketing-cloud/how-to/analytics-ac.html) voor meer informatie over de implementatie van de integratie van Adobe Analytics met Adobe Campaign.

De actievelden voor elk gereedschap zijn als volgt:

* De rol van de webanalyse:

   1. markeert de e-mailcampagnes die met Adobe Campaign zijn gestart;
   1. bespaart ontvankelijk gedrag, op de plaats zij na het klikken van campagne e-mail, in de vorm van segmenten doorbladeden. Segmenten hebben betrekking op verlaten producten (bekeken, maar niet aan de kar toegevoegd of aangekocht), op aankopen of het verlaten van de kar.

* Adobe Campaign-rol:

   1. verzendt de indicatoren en campagneattributen naar de schakelaar, die hen op zijn beurt aan het analytische hulpmiddel van het Web doorstuurt;
   1. segmenten terugwinnen en analyseren;
   1. leidt tot een hermarketing campagne.

## Integratie instellen {#setting-up-the-integration}

Als u de gegevensconnector wilt instellen, moet u verbinding maken met uw Adobe Campaign-instantie en de volgende bewerkingen uitvoeren:

* [Stap 1: Integratie in Analytics configureren](#step-1--configure-integration-in-analytics)
* [Stap 2: Externe account maken in campagne](#step-2--create-the-external-account-in-campaign)
* [Stap 3: Adobe Campaign en Adobe Analytics synchroniseren](#step-3--synchronize-adobe-campaign-and-adobe-analytics)

### Stap 1: Integratie in Analytics {#step-1--configure-integration-in-analytics} configureren

In de volgende stappen wordt de configuratie van de gegevensconnector beschreven met een wizard.

1. Meld u aan bij de Adobe Experience Cloud met een Adobe ID of Enterprise ID.

   ![](assets/adobe_genesis_install_001.png)

1. Selecteer **[!UICONTROL Analytics]** in de lijst met Experience Cloud-oplossingen.

   ![](assets/adobe_genesis_install_013.png)

1. Selecteer **[!UICONTROL Data Connectors]** op het tabblad **[!UICONTROL Admin]**.

   U moet de volgende de hulpmiddelentoestemmingen van Analytics hebben om tot **[!UICONTROL Data Connectors]** menu toegang te hebben. Raadpleeg [deze pagina](https://docs.adobe.com/content/help/en/analytics/admin/admin-console/permissions/analytics-tools.html) voor meer informatie
   * Integraties (maken)
   * Integraties (update)
   * Integraties (verwijderen)

   ![](assets/adobe_genesis_install_002.png)

1. Selecteer **[!UICONTROL Adobe Campaign Classic]** in de lijst met partners.

   ![](assets/adobe_genesis_install_014.png)

1. Klik in het dialoogvenster **[!UICONTROL Add integration]** op **[!UICONTROL Activate]**.
1. Controleer **[!UICONTROL I accept these terms and conditions]** en selecteer **[!UICONTROL Report suite]** verbonden aan deze integratie en ga het schakelaaretiket in.

   Klik **[!UICONTROL Create and configure this integration]** als u klaar bent.

   ![](assets/adobe_genesis_install_015.png)

1. Voer het e-mailadres in dat de meldingen namens de connector ontvangt en kopieer vervolgens het **[!UICONTROL Account ID]** zoals het wordt weergegeven in de externe Adobe Campaign-account (zie voor meer informatie [Stap 2: Maak het externe account in Campagne (a2/>).](#step-2--create-the-external-account-in-campaign)

   ![](assets/adobe_genesis_install_005.png)

1. Geef de id&#39;s op die nodig zijn om de impact van de e-mailcampagne te meten, d.w.z. de interne naam van de campagne (cid) en de tabel-id voor iNmsBroadlog (bid). Geef ook de indicatoren op voor gebeurtenissen die moeten worden verzameld.
Zorg ervoor dat uw **[!UICONTROL Events]** van Numeriek type zijn, anders zullen zij niet in het drop-down menu verschijnen.

   ![](assets/adobe_genesis_install_006.png)

1. Geef indien nodig de gepersonaliseerde segmenten op.

   ![](assets/adobe_genesis_install_007.png)

1. Selecteer in **[!UICONTROL Data collection]** een methode voor het herstellen van gegevens, in dit geval de **[!UICONTROL cid]**- en **[!UICONTROL bid]**-id&#39;s die in stap 6 zijn opgegeven.

   ![](assets/adobe_genesis_install_009.png)

1. Selecteer de informatie die u op het dashboard wilt weergeven.

   ![](assets/adobe_genesis_install_0112.png)

1. Controleer de configuratie in de pagina die de vorige stappen samenvat.

   ![](assets/adobe_genesis_install_011.png)

1. Klik **[!UICONTROL Activate Now]** om configuratie goed te keuren en de schakelaar te activeren.

   ![](assets/adobe_genesis_install_012.png)

   De gegevensconnector is nu geconfigureerd.

### Stap 2: Externe account maken in campagne {#step-2--create-the-external-account-in-campaign}

De integratie van Adobe Campaign in de analyseplatforms vindt plaats via een connector. U synchroniseert de toepassingen door het volgende proces toe te passen:

1. Installeer het **Web Analytics-pakket** in Adobe Campaign.
1. Ga naar de **[!UICONTROL Administration > Platform > External accounts]** omslag van de boom van Adobe Campaign.
1. Klik met de rechtermuisknop op de lijst met externe accounts en selecteer **[!UICONTROL New]** in de vervolgkeuzelijst (of klik op de knop **[!UICONTROL New]** boven de lijst met externe accounts).
1. Gebruik de vervolgkeuzelijst om het type **[!UICONTROL Web Analytics]** te selecteren.
1. Selecteer de provider voor de aansluiting, dat wil zeggen **[!UICONTROL Adobe Analytics - Data Connector]** in dit geval.

   ![](assets/webanalytics_ext_account_create_001.png)

1. Klik op de koppeling **[!UICONTROL Enrich the formula...]** om de URL-berekeningsformule te wijzigen en de integratie-informatie (campagne-id&#39;s) voor het gereedschap Webanalyse op te geven en de domeinen van de sites waarvan de activiteit moet worden bijgehouden.
1. Geef de domeinnaam of -namen van de sites op.

   ![](assets/webanalytics_tracking_001.png)

1. Klik **[!UICONTROL Next]** en zorg ervoor de domeinnamen zijn bewaard.

   ![](assets/webanalytics_tracking_002.png)

1. Indien nodig moet u de berekeningsformule te veel laden. U doet dit door het selectievakje in te schakelen en de formule rechtstreeks in het venster te bewerken.

   ![](assets/webanalytics_tracking_003.png)

   >[!IMPORTANT]
   >
   >Deze configuratiewijze is gereserveerd voor deskundige gebruikers: Als deze formule een fout bevat, kunnen e-mailleveringen worden gestopt.

1. Met het tabblad **[!UICONTROL Advanced]** kunt u meer technische instellingen configureren of wijzigen.

   * **[!UICONTROL Lifespan]**: Hiermee kunt u de vertraging opgeven (in dagen_ waarna de webgebeurtenissen in Adobe Campaign zijn hersteld door technische workflows. Standaard: 180 dagen.
   * **[!UICONTROL Persistence]**: Hiermee kunt u de periode opgeven gedurende welke alle webgebeurtenissen (bijvoorbeeld een aankoop) kunnen worden toegewezen aan een campagne voor het opnieuw op de markt brengen, Standaard: 7 dagen.

>[!NOTE]
>
>Als u verschillende publiekmeetgereedschappen gebruikt, kunt u **[!UICONTROL Other]** in de vervolgkeuzelijst **[!UICONTROL Partners]** selecteren wanneer u de externe account maakt. U mag slechts naar één externe account verwijzen in de leveringseigenschappen: u moet daarom de formule van bijgehouden URL&#39;s aanpassen door de parameters toe te voegen die door de Adobe en alle andere gebruikte meetinstrumenten worden verwacht.

### Stap 3: Adobe Campaign en Adobe Analytics {#step-3--synchronize-adobe-campaign-and-adobe-analytics} synchroniseren

Nadat u de externe account hebt gemaakt, moet u beide toepassingen synchroniseren.

1. Ga naar uw eerder gemaakte externe account.
1. Wijzig desgewenst het account **[!UICONTROL Label]**.
1. Wijzig de **[!UICONTROL Internal name]** zodanig dat deze overeenkomt met de **[!UICONTROL Name]** die is gekozen tijdens het configureren van de gegevensconnector.

   ![](assets/webanalytics_ext_account_setting_001.png)

1. Klik op de koppeling **[!UICONTROL Approve connection]**.

   ![](assets/webanalytics_ext_account_setting_002.png)

   Zorg ervoor **[!UICONTROL Internal name]** **[!UICONTROL Name]** in de de configuratietovenaar van de Verbinding van Gegevens wordt gespecificeerd.

1. Ga **[!UICONTROL Account ID]** in de configuratietovenaar van de Verbinding van Gegevens in.

   ![](assets/webanalytics_ext_account_setting_003.png)

1. Volg de stappen volgens de de tovenaar van de Verbinding van Gegevens gids, dan terugkeer aan de externe rekening in Adobe Campaign.
1. Klik op **[!UICONTROL Next]** om de gegevensuitwisseling tussen Adobe Campaign en Adobe Analytics - Gegevensconnector te laten plaatsvinden.

   De segmentlijst wordt weergegeven wanneer de synchronisatie is voltooid.

   ![](assets/webanalytics_ext_account_setting_004.png)

Wanneer de synchronisatie van gegevens tussen Adobe Campaign en Adobe Analytics - Gegevensconnector effectief is, worden de drie standaardsegmenten die zijn gedefinieerd in de wizard Gegevensconnector hersteld door Adobe Campaign en zijn deze toegankelijk op het tabblad **[!UICONTROL Segments]** van de externe Adobe Campaign-account.

![](assets/webanalytics_segments.png)

Als extra segmenten in de tovenaar van de Verbinding van Gegevens zijn gevormd, kunt u hen aan Adobe Campaign toevoegen. Klik hiertoe op de koppeling **[!UICONTROL Update segment list]** en volg de stappen die worden beschreven in de wizard Externe account. Nadat de bewerking is uitgevoerd, worden de nieuwe segmenten weergegeven in de lijst.

![](assets/webanalytics_segments_update.png)

### Technische workflows van webanalyseprocessen {#technical-workflows-of-web-analytics-processes}

Gegevensuitwisseling tussen Adobe Campaign en Adobe Analytics - Gegevensconnector wordt afgehandeld door vier technische workflows die als achtergrondtaak worden uitgevoerd.

Deze bestanden zijn beschikbaar in de Adobe Campaign-structuur, in de map **[!UICONTROL Administration > Production > Technical workflows > Web analytics process]**.

![](assets/webanalytics_workflows.png)

* **[!UICONTROL Recovering of web events]**: eenmaal per uur downloadt deze workflow segmenten over het gedrag van gebruikers op een bepaalde site, neemt deze op in de Adobe Campaign-database en start de workflow voor het opnieuw in de handel brengen.
* **[!UICONTROL Event purge]**: met deze workflow kunt u alle gebeurtenissen uit de database verwijderen, afhankelijk van de periode die in het  **[!UICONTROL Lifespan]** veld is geconfigureerd. Raadpleeg [Stap 2 voor meer informatie hierover: Maak het externe account in Campagne](#step-2--create-the-external-account-in-campaign).
* **[!UICONTROL Identification of converted contacts]**: directory van de bezoekers die een aankoop hebben gedaan na een hermarketingcampagne. De gegevens die door deze workflow worden verzameld, zijn toegankelijk in het **[!UICONTROL Re-marketing efficiency]**-rapport. Raadpleeg deze [pagina](#creating-a-re-marketing-campaign).
* **[!UICONTROL Sending of indicators and campaign attributes]**: Hiermee kunt u e-mailcampagnemarameters via Adobe Campaign naar de Adobe Experience Cloud verzenden via Adobe Analytics - Data-connector. Deze workflow wordt elke dag om 4 uur gestart en het kan 24 uur duren voordat de gegevens naar Analytics worden verzonden.

   Deze workflow moet niet opnieuw worden gestart, anders worden alle eerdere gegevens opnieuw verzonden, waardoor de resultaten van Analytics kunnen worden scheefgetrokken.

   Het gaat om indicatoren die:

   * **[!UICONTROL Messages to deliver]** (@toDeliver)
   * **[!UICONTROL Processed]** (@processing)
   * **[!UICONTROL Success]** (@geslaagd)
   * **[!UICONTROL Total count of opens]** (@totalRecipientOpen)
   * **[!UICONTROL Recipients who have opened]** (@ontvangerOpen)
   * **[!UICONTROL Total number of recipients who clicked]** (@totalRecipientClick)
   * **[!UICONTROL People who clicked]** (@personClick)
   * **[!UICONTROL Number of distinct clicks]** (@receivingClick)
   * **[!UICONTROL Opt-Out]** (@optOut)
   * **[!UICONTROL Errors]** (@fout)

   >[!NOTE]
   >
   >De verzonden gegevens zijn de delta die op de laatste momentopname wordt gebaseerd die tot negatieve waarde in de metrische gegevens kan leiden.

   De verzonden kenmerken zijn als volgt:

   * **[!UICONTROL Internal name]** (@internalName)
   * **[!UICONTROL Label]** (@label)
   * **[!UICONTROL Label]** (operation/@label): alleen als het  **** Campaignpackage is geïnstalleerd
   * **[!UICONTROL Nature]** (operation/@nature): alleen als het  **** Campaignpackage is geïnstalleerd
   * **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
   * **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
   * **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
   * **[!UICONTROL Contact date]** (planning/@contactDate)



## Leveringen bijhouden in Adobe Campaign {#tracking-deliveries-in-adobe-campaign}

Als u wilt dat de Adobe Experience Cloud de activiteit op de sites kan volgen wanneer de levering door Adobe Campaign wordt verzonden, moet u in de leveringseigenschappen verwijzen naar de bijbehorende connector. Hiervoor voert u de volgende stappen uit:

1. Open de levering van de campagne die u wilt bijhouden.

   ![](assets/webanalytics_delivery_properties_003.png)

1. Open de leveringseigenschappen.
1. Ga naar het tabblad **[!UICONTROL Web Analytics]** en selecteer de eerder gemaakte externe account. Zie [Stap 2: Maak het externe account in Campagne](#step-2--create-the-external-account-in-campaign).

   ![](assets/webanalytics_delivery_properties_002.png)

1. Je kunt nu je levering verzenden en je rapport bekijken in Adobe Analytics.

## Nieuwe marketingcampagne maken {#creating-a-re-marketing-campaign}

Om uw re-marketing campagne voor te bereiden, creeer eenvoudig leveringsmalplaatjes die voor re-marketing typecampagnes worden gebruikt. Dan vorm uw re-marketing campagne en verbind het met een segment. Elk segment moet een andere hermarketingcampagne voeren.

Nieuwe marketingcampagnes worden automatisch gestart zodra Adobe Campaign de segmenten heeft hersteld waarin het gedrag wordt geanalyseerd van de mensen die voor de eerste campagne zijn geselecteerd. In het geval van het verlaten van het winkelwagentje of het bekijken van een product zonder een aankoop, wordt een levering verzonden naar de betrokken ontvangers zodat hun site eindigt met een aankoop.

Adobe Campaign biedt persoonlijke leveringssjablonen die u kunt gebruiken of zelf kunt databaseren om campagnes voor te bereiden.

1. Ga in **[!UICONTROL Explorer]** naar de map **[!UICONTROL Resources > Templates > Delivery templates]** van de Adobe Campaign-structuur.
1. Dupliceer de **[!UICONTROL Email delivery (re-marketing)]** malplaatje of de re-marketing malplaatjevoorbeelden die door Adobe Campaign worden aangeboden.
1. Pas de sjabloon aan uw wensen aan en sla deze op.

   ![](assets/webanalytics_delivery_model.png)

1. Maak een nieuwe campagne en selecteer de sjabloon **[!UICONTROL Re-marketing campaign]** in de vervolgkeuzelijst.

   ![](assets/webanalytics_remarketing_campaign_002.png)

1. Klik op de koppeling **[!UICONTROL Configure...]** om het segment en de leveringssjabloon op te geven die aan de campagne zijn gekoppeld.
1. Selecteer de eerder geconfigureerde externe account.

   ![](assets/webanalytics_remarketing_campaign_003.png)

1. Selecteer het desbetreffende segment.

   ![](assets/webanalytics_remarketing_campaign_005.png)

1. Selecteer het leveringsmalplaatje voor deze re-marketing campagne moet worden gebruikt, dan klik **[!UICONTROL Finish]** om het venster te sluiten.

   ![](assets/webanalytics_remarketing_campaign_006.png)

1. Klik **[!UICONTROL OK]** om het campagnevenster te sluiten.

Het **[!UICONTROL Re-marketing efficiency]** rapport wordt betreden via de globale rapportpagina. Het laat u het aantal geconverteerde contacten (d.w.z. het hebben van iets gekocht) met betrekking tot het aantal kartverlaten na de Adobe Campaign hermarketing campagne bekijken. De conversiesnelheid wordt berekend per week, maand of sinds het begin van de synchronisatie tussen Adobe Campaign- en Web-analyseprogramma&#39;s.

![](assets/webanalytics_reporting.png)

