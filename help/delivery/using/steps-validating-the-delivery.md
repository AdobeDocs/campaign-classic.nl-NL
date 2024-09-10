---
product: campaign
title: De levering valideren
description: Leer hoe u een levering kunt valideren
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability, Email Rendering, Proofs
role: User
exl-id: c2f4d8d0-f0fe-4d1a-92fd-91edaf9729f3
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1662'
ht-degree: 4%

---

# De levering valideren {#validating-the-delivery}

Wanneer een levering is gecreeerd en gevormd, moet u het bevestigen alvorens het naar het belangrijkste doel te verzenden.

Dit doet u als volgt:

1. **analyseert de levering**: deze stap laat u de berichten voorbereiden om te leveren. [Meer informatie](#analyzing-the-delivery).

   De regels die tijdens analyse worden toegepast worden voorgesteld in [ deze sectie ](#validation-process-with-typologies). De beschikbare bevestigingswijzen zijn gedetailleerd in de [ Verandering de goedkeuringswijze ](#changing-the-approval-mode) sectie.

1. **verzendt proef**: deze stap laat u inhoud, URLs, verpersoonlijking, enz. controleren. Leer meer in [ een proef ](steps-validating-the-delivery.md#sending-a-proof) verzenden en [ bepalen een specifiek proefdrukdoel ](steps-defining-the-target-population.md#defining-a-specific-proof-target).

>[!IMPORTANT]
>
>De twee stappen hierboven MOETEN na elke wijziging op de berichtinhoud worden uitgevoerd.

## De levering analyseren {#analyzing-the-delivery}

De analyse is het stadium waarin de doelpopulatie wordt berekend en de leveringsinhoud wordt voorbereid. Zodra het volledig is, is de levering klaar om worden verzonden.

### De analyse starten {#launching-the-analysis}

1. Klik op **[!UICONTROL Send]** om de leveringanalyse te starten.
1. Selecteer **[!UICONTROL Deliver as soon as possible]**.

   ![](assets/s_ncs_user_email_del_send.png)

1. Klik op **[!UICONTROL Analyze]** om de analyse handmatig te starten.

   Op de voortgangsbalk ziet u de voortgang van de analyse.

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >De bevestigingsregels die tijdens analyse worden gebruikt worden beschreven in het [ proces van de Bevestiging met typologieën ](steps-validating-the-delivery.md#validation-process-with-typologies) sectie.

1. U kunt de analyse op elk gewenst moment stoppen door op **[!UICONTROL Stop]** te klikken.

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

1. Klik op **[!UICONTROL Close]** om de eventuele fouten te corrigeren.

1. Nadat u de wijzigingen hebt aangebracht, klikt u opnieuw op de analyse **[!UICONTROL Analyze]** .

Nadat u het resultaat van de analyse hebt gecontroleerd, kunt u op **[!UICONTROL Confirm delivery]** klikken om het bericht naar het opgegeven doel te verzenden. Met een bevestigingsbericht kunt u de levering starten.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>Klik op de koppeling **[!UICONTROL Change the main delivery target]** als het aantal berichten dat u wilt verzenden niet overeenkomt met uw configuratie. Zo kunt u de definitie van de doelpopulatie wijzigen en de analyse opnieuw starten.

### Analyse-instellingen {#analysis-parameters}

Op het tabblad **[!UICONTROL Analysis]** van de leveringseigenschappen kunt u een set gegevens definiëren voor de voorbereiding van berichten tijdens de analysefase.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

Op dit tabblad hebt u toegang tot de volgende opties:

* **[!UICONTROL Label and code of the delivery]** : de opties in deze sectie worden gebruikt om de waarden van deze gebieden tijdens de fase van de leveringsanalyse te berekenen. In het veld **[!UICONTROL Compute the execution folder during the delivery analysis]** wordt de naam berekend van de map die deze leveringsactie tijdens de analysefase zal bevatten.
* **[!UICONTROL Approval mode]** : in dit veld kunt u handmatig of automatisch afleveren definiëren wanneer de analyse is voltooid. De bevestigingswijzen worden voorgesteld in de [ Verandering de goedkeuringswijze ](#changing-the-approval-mode) sectie.
* **[!UICONTROL Prepare the delivery parts in the database]** : met deze optie kunt u de prestaties van de leveringsanalyse verbeteren. Zie [deze sectie](#improving-delivery-analysis)voor meer informatie.
* **[!UICONTROL Prepare the personalization data with a workflow]** : met deze optie kunt u de aanpassingsgegevens in uw levering voorbereiden in een automatische workflow. Hierdoor kunt u de prestaties aanzienlijk verbeteren en de personalisatie uitvoeren. Voor meer op dit, zie [ verpersoonlijking ](personalization-fields.md#optimizing-personalization) optimaliseren.
* **[!UICONTROL Start job in a detached process]** : met deze optie kunt u de afleveringsanalyse in een afzonderlijk proces starten. De analysefunctie gebruikt standaard het Adobe Campaign-toepassingsserverproces (webserver). Als u deze optie selecteert, zorgt u ervoor dat de analyse ook wordt voltooid wanneer de toepassingsserver uitvalt.
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** : deze optie voegt de SQL vraaglogboeken aan het leveringsdagboek tijdens de analysefase toe.
* **[!UICONTROL Ignore personalization scripts during sending]** : met deze optie kunt u de interpretatie van JavaScript-instructies in HTML-inhoud omzeilen. Ze worden op dezelfde manier weergegeven als in de geleverde inhoud. Deze instructies worden geïntroduceerd met de tag **&lt;%=** .)

### De prestaties van de leveringsanalyse verbeteren {#improving-delivery-analysis}

Als u de voorbereiding van de levering wilt versnellen, controleert u de optie **[!UICONTROL Prepare the delivery parts in the database]** voordat u de analyse start.

Wanneer deze optie wordt toegelaten, wordt de levering voorbereiding uitgevoerd direct binnen het gegevensbestand, dat de analyse kan beduidend versnellen.

Deze optie is momenteel alleen beschikbaar als aan de volgende voorwaarden is voldaan:

* De levering moet een e-mail zijn. De andere kanalen worden momenteel niet ondersteund.
* U moet niet midsourcing of extern verpletteren, slechts bulklevering gebruiken die type verplettert. U kunt de routering controleren die wordt gebruikt op het tabblad **[!UICONTROL General]** van **[!UICONTROL Delivery properties]** .
* U kunt geen populatie richten die uit een extern dossier komt. Voor één levering klikt u op de koppeling **[!UICONTROL To]** in de **[!UICONTROL Email parameters]** en controleert u of de optie **[!UICONTROL Defined in the database]** is geselecteerd. Voor een levering die in een workflow wordt gebruikt, controleert u of de ontvangers **[!UICONTROL Specified by the inbound event(s)]** op het tabblad **[!UICONTROL Delivery]** zijn.
* U moet een PostSQL-database gebruiken.

### De prioriteit van de analyse configureren {#analysis-priority-}

Wanneer de levering onderdeel is van een campagne, biedt het tabblad **[!UICONTROL Advanced]** een extra optie. Zo kunt u de verwerkingsvolgorde voor leveringen in dezelfde campagne ordenen.

Elke levering wordt geanalyseerd voordat deze wordt verzonden. De duur van de analyse is afhankelijk van het extractiebestand van de levering. Hoe groter de grootte van het bestand, des te langer de analyse duurt, waardoor de volgende leveringen wachten.

Met de opties voor de **[!UICONTROL Message preparation by the scheduler]** kunt u prioriteit geven aan de leveringsanalyse in een campagneworkflow.

![](assets/delivery_analysis_priority.png)

Als een levering te groot is, is het beter om een lage prioriteit aan het toe te wijzen om de analyse van andere werkschemaleveringen te vermijden vertragen.

>[!NOTE]
>
>Om ervoor te zorgen dat de grotere leveringsanalyses de vooruitgang van uw werkschema&#39;s niet vertragen, kunt u hun uitvoeringen plannen door **[!UICONTROL Schedule execution for a time of low activity]** te tikken.

## Een proef verzenden {#sending-a-proof}

Adobe raadt u ten zeerste aan een cyclus voor leveringsvalidatie in te stellen om mogelijke fouten in de berichtconfiguratie op te sporen. Zorg ervoor dat de content zo vaak als nodig wordt goedgekeurd door proeven naar testontvangers te verzenden. Telkens wanneer een wijziging wordt aangebracht, moet voor de goedkeuring van de content een proef worden verzonden.

>[!NOTE]
>
>De beschikbare bevestigingswijzen zijn gedetailleerd in [ Verandering de goedkeuringswijze ](steps-validating-the-delivery.md#changing-the-approval-mode).

Volg onderstaande stappen om een proefdruk te verzenden:

1. Zorg ervoor het proefdrukdoel is gevormd zoals die in [ wordt beschreven een specifiek proefdrukdoel ](steps-defining-the-target-population.md#defining-a-specific-proof-target) bepaalt.

1. Klik **[!UICONTROL Send a proof]** op de hoogste bar van de leveringsmedewerker.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. Analyse van berichten starten. Zie [ de levering ](steps-validating-the-delivery.md#analyzing-the-delivery) analyseren.
1. U kunt de levering nu verzenden (zie [ verzenden de levering ](steps-sending-the-delivery.md)).

   Nadat de levering is verzonden, wordt de proefdruk weergegeven in de leveringslijst en wordt deze automatisch gemaakt en genummerd. Deze kan worden bewerkt als u toegang wilt krijgen tot de inhoud en eigenschappen van de sjabloon. Raadpleeg [deze pagina](about-delivery-monitoring.md) voor meer informatie.

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >Als er verschillende indelingen zijn gemaakt voor de levering (HTML en Tekst), kunt u de indeling kiezen van de berichten die naar de ontvangers van de proefdrukken in de onderste sectie van het venster worden verzonden.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

Mogelijk wilt u de inhoud van de levering wijzigen als gevolg van opmerkingen van de validatiegroep die de proefafdruk ontvangt. Nadat u de wijzigingen hebt aangebracht, moet u de analyse opnieuw starten en een andere proefdruk verzenden. Elke nieuwe proef wordt genummerd en het programma geopend in het leveringsdagboek.

Nadat de levering is geanalyseerd, kunt u de verschillende proefdrukken weergeven die via het subtabblad **[!UICONTROL Proofs]** van het logbestand (**[!UICONTROL Audit]** tab) zijn verzonden.

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

U moet zoveel proefdrukken verzenden als nodig zijn totdat de inhoud van de levering is voltooid. Daarna kunt u de levering naar het hoofddoel verzenden en de validatiecyclus sluiten.

Op het tabblad **[!UICONTROL Advanced]** met leveringseigenschappen kunt u de eigenschappen van de proefdruk definiëren. Indien nodig, kunt u de ontvankelijke uitsluitingsregels met voeten treden.

![](assets/s_ncs_user_wizard_email01_145.png)

De volgende opties zijn beschikbaar:

* Met de eerste optie kunt u de proefdrukverdubbelingen behouden.
* Beide volgende opties laten u ontvangers houden die op lijst van gewezen personen en adressen in quarantaine zijn. Zie de beschrijving van deze opties voor het belangrijkste doel in [ uitsluitingsmontages ](steps-defining-the-target-population.md#customizing-exclusion-settings) aanpassen. In tegenstelling tot het doel van een levering, waar deze adressen door gebrek worden uitgesloten, worden zij gehouden door gebrek voor het doel van een proef.
* Met de optie **[!UICONTROL Keep the delivery code for the proof]** geeft u de proefdruk dezelfde leveringscode als die welke is gedefinieerd voor de levering waarop de optie betrekking heeft. Deze code wordt gespecificeerd in de eerste stap van de leveringsmedewerker.
* Standaard wordt het onderwerp van de proefdruk voorafgegaan door &#39;Bewijs nr.&#39;, waarbij # het nummer van de proefdruk is. U kunt dit voorvoegsel wijzigen in het veld **[!UICONTROL Label prefix]** .

## Validatieproces met typologieën {#validation-process-with-typologies}

Alvorens om het even welke berichten te verzenden, zou u de campagne moeten analyseren om zijn inhoud en configuratie goed te keuren. De controleregels die tijdens de analysefase worden toegepast worden bepaald in a **typologie**. Voor e-mails worden standaard de volgende punten in de analyse behandeld:

* Het object goedkeuren
* URL&#39;s en afbeeldingen goedkeuren
* De URL-labels goedkeuren
* De koppeling voor annuleren goedkeuren
* De grootte van proefdrukken controleren
* De geldigheidsperiode controleren
* De planning van golven controleren

De typologie die voor elke levering moet worden toegepast, wordt in de leveringsparameters op het tabblad **[!UICONTROL Typologies]** geselecteerd.

U kunt de goedkeuringsregels, de inhoud, de volgorde van uitvoering en de volledige beschrijving via het knooppunt **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** weergeven en bewerken.

U kunt nieuwe regels tot stand brengen en nieuwe typologieën van deze knoop bepalen. Deze taken zijn echter voorbehouden aan deskundige gebruikers die JavaScript kennen.

Voor meer op typologische regels, verwijs naar [ deze pagina ](../../campaign-opt/using/about-campaign-typologies.md).

Als u de huidige typologie wilt bewerken, klikt u op het pictogram **[!UICONTROL Edit link]** rechts van het veld **[!UICONTROL Typology]** .

![](assets/s_ncs_user_email_del_typo_tab.png)

Het tabblad **[!UICONTROL Rule]** bevat een lijst met de typologische regels die moeten worden toegepast. Selecteer een regel en klik op het pictogram **[!UICONTROL Detail...]** om de configuratie ervan weer te geven:

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** typetypetypes worden gebruikt in het kader van het beheer van de verkoopdruk. Raadpleeg [deze sectie](../../mrm/using/about-marketing-resource-management.md) voor meer informatie.

## De goedkeuringsmodus wijzigen {#changing-the-approval-mode}

Met het tabblad **[!UICONTROL Analysis]** voor leveringseigenschappen kunt u de validatiemodus selecteren. Als tijdens de analyse waarschuwingen worden gegenereerd (bijvoorbeeld als bepaalde tekens worden geaccentueerd in het onderwerp van de levering, enz.), kunt u de levering zodanig configureren dat wordt bepaald of deze nog moet worden uitgevoerd. Door gebrek, moet de gebruiker het verzenden van berichten aan het eind van de analysefase bevestigen: dit is **handmatige** bevestiging.

Selecteer een andere goedkeuringsmodus in de vervolgkeuzelijst in het desbetreffende veld.

![](assets/s_ncs_user_email_del_validation_mode.png)

De volgende goedkeuringsmodi zijn beschikbaar:

* **[!UICONTROL Manual]**: Aan het einde van de analysefase moet de gebruiker de levering bevestigen om te beginnen met verzenden. Klik hiertoe op de knop **[!UICONTROL Start]** om de levering te starten.
* **[!UICONTROL Semi-automatic]**: het verzenden begint automatisch als de analysefase geen waarschuwingsberichten genereert.
* **[!UICONTROL Automatic]**: het verzenden begint automatisch aan het einde van de analysefase, ongeacht het resultaat.
