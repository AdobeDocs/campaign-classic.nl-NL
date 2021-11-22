---
product: campaign
title: De levering valideren
description: De levering valideren
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
exl-id: c2f4d8d0-f0fe-4d1a-92fd-91edaf9729f3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1663'
ht-degree: 5%

---

# De levering valideren {#validating-the-delivery}

![](../../assets/common.svg)

Wanneer een levering is gecreeerd en gevormd, moet u het bevestigen alvorens het naar het belangrijkste doel te verzenden.

Dit doet u als volgt:

1. **De levering analyseren**: met deze stap kunt u de te leveren berichten voorbereiden. [Meer info](#analyzing-the-delivery).

   De regels die tijdens de analyse worden toegepast, worden weergegeven in [deze sectie](#validation-process-with-typologies). De beschikbare validatiemodi worden gedetailleerd beschreven in de [De goedkeuringsmodus wijzigen](#changing-the-approval-mode) sectie.

1. **Proefdrukken verzenden**: Met deze stap kunt u inhoud, URL&#39;s, personalisatie enzovoort beheren. Meer informatie in [Een proefdruk verzenden](steps-validating-the-delivery.md#sending-a-proof) en [Een specifiek proefdrukdoel definiëren](steps-defining-the-target-population.md#defining-a-specific-proof-target).

>[!IMPORTANT]
>
>De twee stappen hierboven MOETEN na elke wijziging op de berichtinhoud worden uitgevoerd.

## De levering analyseren {#analyzing-the-delivery}

De analyse is het stadium waarin de doelpopulatie wordt berekend en de leveringsinhoud wordt voorbereid. Zodra het volledig is, is de levering klaar om worden verzonden.

### De analyse starten {#launching-the-analysis}

1. Klik op **[!UICONTROL Send]**.
1. Selecteer **[!UICONTROL Deliver as soon as possible]**.

   ![](assets/s_ncs_user_email_del_send.png)

1. Klikken **[!UICONTROL Analyze]** om de analyse handmatig te starten.

   Op de voortgangsbalk ziet u de voortgang van de analyse.

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >De validatieregels die tijdens de analyse worden gebruikt, worden beschreven in de [Validatieproces met typologieën](steps-validating-the-delivery.md#validation-process-with-typologies) sectie.

1. U kunt de analyse op elk gewenst moment stoppen door op **[!UICONTROL Stop]**.

   ![](assets/s_ncs_user_wizard_email01_16.png)

   Tijdens de voorbereidingsfase worden geen berichten verzonden. U kunt de analyse daarom zonder risico starten of annuleren.

   >[!IMPORTANT]
   >
   >Wanneer de analyse loopt, bevriest de levering (of het bewijs). Elke wijziging in de levering (of het bewijs) moet worden gevolgd door een andere analyse voordat zij van toepassing wordt.

1. Wacht tot de analyse is voltooid.

   Wanneer de analyse is voltooid, geeft de bovenste sectie van het venster aan of de voorbereiding van de levering is voltooid of dat er fouten zijn opgetreden. Alle validatiestappen, waarschuwingen en fouten worden weergegeven. De gekleurde pictogrammen tonen het berichttype:
   * Het blauwe pictogram geeft een informatief bericht aan.
   * Het gele pictogram geeft een niet-kritieke verwerkingsfout aan.
   * Het rode pictogram geeft een kritieke fout aan die het verzenden van de levering verhindert.

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. Klikken **[!UICONTROL Close]** om eventuele fouten te corrigeren.

1. Nadat u de wijzigingen hebt aangebracht, opent u de analyse opnieuw en klikt u op **[!UICONTROL Analyze]**.

Nadat u het resultaat van de analyse hebt gecontroleerd, kunt u klikken op **[!UICONTROL Confirm delivery]** om het bericht naar het opgegeven doel te verzenden. Met een bevestigingsbericht kunt u de levering starten.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>Klik op de knop **[!UICONTROL Change the main delivery target]** verbinding als het aantal te verzenden berichten niet uw configuratie aanpast. Zo kunt u de definitie van de doelpopulatie wijzigen en de analyse opnieuw starten.

### Analyse-instellingen {#analysis-parameters}

De **[!UICONTROL Analysis]** tabblad van de leveringseigenschappen kunt u een set gegevens definiëren voor de voorbereiding van berichten tijdens de analysefase.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

Op dit tabblad hebt u toegang tot de volgende opties:

* **[!UICONTROL Label and code of the delivery]** : de opties in deze sectie worden gebruikt om de waarden van deze velden tijdens de fase van de leveringsanalyse te berekenen. De **[!UICONTROL Compute the execution folder during the delivery analysis]** in het veld wordt de naam berekend van de map die deze leveringsactie tijdens de analysefase zal bevatten.
* **[!UICONTROL Approval mode]** : in dit veld kunt u handmatig of automatisch afleveren definiëren wanneer de analyse is voltooid. De validatiemodi worden weergegeven in de [De goedkeuringsmodus wijzigen](#changing-the-approval-mode) sectie.
* **[!UICONTROL Prepare the delivery parts in the database]** : met deze optie kunt u de prestaties van de leveringsanalyse verbeteren. Zie [deze sectie](#improving-delivery-analysis)voor meer informatie.
* **[!UICONTROL Prepare the personalization data with a workflow]** : met deze optie kunt u de aanpassingsgegevens in uw levering voorbereiden in een automatische workflow, waardoor u een aanzienlijke prestatieverhoging voor het uitvoeren van personalisatie kunt realiseren. Zie voor meer informatie [Aanpassing optimaliseren](personalization-fields.md#optimizing-personalization).
* **[!UICONTROL Start job in a detached process]** : met deze optie kunt u de leveringsanalyse in een afzonderlijk proces starten. De analysefunctie gebruikt standaard het Adobe Campaign-toepassingsserverproces (webserver). Als u deze optie selecteert, zorgt u ervoor dat de analyse ook wordt voltooid wanneer de toepassingsserver uitvalt.
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** : deze optie voegt de SQL vraaglogboeken aan het leveringsdagboek tijdens de analysefase toe.
* **[!UICONTROL Ignore personalization scripts during sending]** : Met deze optie kunt u de interpretatie van JavaScript-instructies in HTML-inhoud omzeilen. Ze worden op dezelfde manier weergegeven als in de geleverde inhoud. Deze richtlijnen worden in het kader van de **&lt;%=** -tag).

### De prestaties van de leveringsanalyse verbeteren {#improving-delivery-analysis}

Om de voorbereiding van de levering te versnellen, kunt u controleren **[!UICONTROL Prepare the delivery parts in the database]** voordat de analyse wordt gestart.

Wanneer deze optie wordt toegelaten, wordt de levering voorbereiding uitgevoerd direct binnen het gegevensbestand, dat de analyse kan beduidend versnellen.

Deze optie is momenteel alleen beschikbaar als aan de volgende voorwaarden is voldaan:
* De levering moet een e-mail zijn. De andere kanalen worden momenteel niet ondersteund.
* U moet niet midsourcing of extern verpletteren, slechts bulklevering gebruiken die type verplettert. U kunt het verpletteren controleren die in wordt gebruikt **[!UICONTROL General]** tabblad van het dialoogvenster **[!UICONTROL Delivery properties]**.
* U kunt geen populatie richten die uit een extern dossier komt. Voor één levering klikt u op de knop **[!UICONTROL To]** koppeling van de **[!UICONTROL Email parameters]** en controleert of de **[!UICONTROL Defined in the database]** is geselecteerd. Voor levering die in een werkschema wordt gebruikt, controleer dat de ontvangers zijn **[!UICONTROL Specified by the inbound event(s)]** in de **[!UICONTROL Delivery]** tab.
* U moet een PostSQL-database gebruiken.

### De prioriteit van de analyse configureren {#analysis-priority-}

Wanneer de levering deel uitmaakt van een campagne, **[!UICONTROL Advanced]** biedt een extra optie. Zo kunt u de verwerkingsvolgorde voor leveringen in dezelfde campagne ordenen.

Elke levering wordt geanalyseerd voordat deze wordt verzonden. De duur van de analyse is afhankelijk van het extractiebestand van de levering. Hoe groter de grootte van het bestand, des te langer de analyse duurt, waardoor de volgende leveringen wachten.

De opties voor de **[!UICONTROL Message preparation by the scheduler]** laat u de leveringsanalyse in een campagnewerkschema voorrang geven.

![](assets/delivery_analysis_priority.png)

Als een levering te groot is, is het beter om een lage prioriteit aan het toe te wijzen om de analyse van andere werkschemaleveringen te vermijden vertragen.

>[!NOTE]
>
>Om ervoor te zorgen dat de grotere leveringsanalyses de vooruitgang van uw werkschema&#39;s niet vertragen, kunt u hun uitvoering plannen door te tikken **[!UICONTROL Schedule execution for a time of low activity]**.

## Een proef verzenden {#sending-a-proof}

Adobe raadt u ten zeerste aan een cyclus voor leveringsvalidatie in te stellen om mogelijke fouten in de berichtconfiguratie op te sporen. Zorg ervoor dat de content zo vaak als nodig wordt goedgekeurd door proeven naar testontvangers te verzenden. Telkens wanneer een wijziging wordt aangebracht, moet voor de goedkeuring van de content een proef worden verzonden.

>[!NOTE]
>
>* Beschikbare validatiemodi worden nader beschreven in [De goedkeuringsmodus wijzigen](steps-validating-the-delivery.md#changing-the-approval-mode).
>* Configuratie van het proefdrukdoel wordt uitgelegd in [Een specifiek proefdrukdoel definiëren](steps-defining-the-target-population.md#defining-a-specific-proof-target).

>


Volg onderstaande stappen om een proefdruk te verzenden:

1. Controleer of het proefdrukdoel is geconfigureerd zoals wordt beschreven in [Een specifiek proefdrukdoel definiëren](steps-defining-the-target-population.md#defining-a-specific-proof-target).
1. Klikken **[!UICONTROL Send a proof]** op de bovenste balk van de wizard voor levering.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. Analyse van berichten starten. Zie [De levering analyseren](steps-validating-the-delivery.md#analyzing-the-delivery).
1. U kunt nu de levering verzenden (zie [De levering verzenden](steps-sending-the-delivery.md)).

   Nadat de levering is verzonden, wordt de proefdruk weergegeven in de leveringslijst en wordt deze automatisch gemaakt en genummerd. Deze kan worden bewerkt als u toegang wilt krijgen tot de inhoud en eigenschappen van de sjabloon. Raadpleeg [deze pagina](about-delivery-monitoring.md) voor meer informatie.

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >Als er verschillende indelingen zijn gemaakt voor de levering (HTML en Tekst), kunt u de indeling kiezen van de berichten die naar de ontvangers van de proefdrukken in de onderste sectie van het venster worden verzonden.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

Mogelijk wilt u de inhoud van de levering wijzigen als gevolg van opmerkingen van de validatiegroep die de proefafdruk ontvangt. Nadat u de wijzigingen hebt aangebracht, moet u de analyse opnieuw starten en een andere proefdruk verzenden. Elke nieuwe proef wordt genummerd en het programma geopend in het leveringsdagboek.

Nadat de levering is geanalyseerd, kunt u de verschillende proefdrukken bekijken die via de **[!UICONTROL Proofs]** tabblad van het logboek (**[!UICONTROL Audit]** ).

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

U moet zoveel proefdrukken verzenden als nodig zijn totdat de inhoud van de levering is voltooid. Daarna kunt u de levering naar het hoofddoel verzenden en de validatiecyclus sluiten.

De **[!UICONTROL Advanced]** tabblad met leveringseigenschappen kunt u de eigenschappen van de proefdruk definiëren. Indien nodig, kunt u de ontvankelijke uitsluitingsregels met voeten treden.

![](assets/s_ncs_user_wizard_email01_145.png)

De volgende opties zijn beschikbaar:

* Met de eerste optie kunt u de proefdrukverdubbelingen behouden.
* Beide volgende opties laten u ontvangers houden die op lijst van gewezen personen en adressen in quarantaine zijn. Zie de beschrijving van deze opties voor het hoofddoel in [Uitsluitingsinstellingen aanpassen](steps-defining-the-target-population.md#customizing-exclusion-settings). In tegenstelling tot het doel van een levering, waar deze adressen door gebrek worden uitgesloten, worden zij gehouden door gebrek voor het doel van een proef.
* De **[!UICONTROL Keep the delivery code for the proof]** Met deze optie geeft u de bewijzen dezelfde leveringscode als die welke is gedefinieerd voor de levering waarop ze betrekking hebben. Deze code wordt gespecificeerd in de eerste stap van de leveringstovenaar.
* Standaard wordt het onderwerp van de proefdruk voorafgegaan door &#39;Bewijs nr.&#39;, waarbij # het nummer van de proefdruk is. U kunt dit voorvoegsel wijzigen in het dialoogvenster **[!UICONTROL Label prefix]** veld.

## Validatieproces met typologieën {#validation-process-with-typologies}

Alvorens om het even welke berichten te verzenden, zou u de campagne moeten analyseren om zijn inhoud en configuratie goed te keuren. De controleregels die tijdens de analysefase worden toegepast, worden in een **typologie**. Voor e-mails worden standaard de volgende punten in de analyse behandeld:

* Het object goedkeuren
* URL&#39;s en afbeeldingen goedkeuren
* De URL-labels goedkeuren
* De koppeling voor annuleren goedkeuren
* De grootte van proefdrukken controleren
* De geldigheidsperiode controleren
* De planning van golven controleren

De typologie die voor elke levering moet worden toegepast, wordt geselecteerd in de **[!UICONTROL Typologies]** in de leveringsparameters.

U kunt de goedkeuringsregels, de inhoud ervan, de volgorde van uitvoering en de volledige beschrijving weergeven en bewerken via het dialoogvenster **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** knooppunt.

U kunt nieuwe regels tot stand brengen en nieuwe typologieën van deze knoop bepalen. Deze taken zijn echter voorbehouden aan ervaren gebruikers die JavaScript kennen.

Raadpleeg voor meer informatie over typologische regels [deze pagina](../../campaign-opt/using/about-campaign-typologies.md).

Als u de huidige typologie wilt bewerken, klikt u op de knop **[!UICONTROL Edit link]** pictogram rechts van **[!UICONTROL Typology]** veld.

![](assets/s_ncs_user_email_del_typo_tab.png)

De **[!UICONTROL Rule]** bevat een lijst met de typologische regels die moeten worden toegepast. Selecteer een regel en klik op de knop **[!UICONTROL Detail...]** pictogram om de configuratie te bekijken:

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** typologieën van het type worden gebruikt in het kader van het beheer van de verkoopdruk . Raadpleeg [deze sectie](../../mrm/using/about-marketing-resource-management.md) voor meer informatie.

## De goedkeuringsmodus wijzigen {#changing-the-approval-mode}

De **[!UICONTROL Analysis]** kunt u de validatiemodus selecteren. Als tijdens de analyse waarschuwingen worden gegenereerd (bijvoorbeeld als bepaalde tekens worden geaccentueerd in het onderwerp van de levering, enz.), kunt u de levering zodanig configureren dat wordt bepaald of deze nog moet worden uitgevoerd. Door gebrek, moet de gebruiker het verzenden van berichten aan het eind van de analysefase bevestigen: is **handmatig** validatie.

Selecteer een andere goedkeuringsmodus in de vervolgkeuzelijst in het desbetreffende veld.

![](assets/s_ncs_user_email_del_validation_mode.png)

De volgende goedkeuringsmodi zijn beschikbaar:

* **[!UICONTROL Manual]**: Aan het einde van de analysefase moet de gebruiker de levering bevestigen om te beginnen met het verzenden. Om dit te doen, klik **[!UICONTROL Start]** om de levering te starten.
* **[!UICONTROL Semi-automatic]**: Het verzenden begint automatisch als de analysefase geen waarschuwingsberichten produceert.
* **[!UICONTROL Automatic]**: De verzending begint automatisch aan het einde van de analysefase, ongeacht het resultaat ervan.
