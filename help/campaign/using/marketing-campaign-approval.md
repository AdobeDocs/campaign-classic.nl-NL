---
title: Marketing-campagnes goedkeuren
seo-title: Verkoopcampagnes goedkeuren
description: Verkoopcampagnes goedkeuren
seo-description: null
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---

# Marketing-campagnes goedkeuren {#approving-marketing-campaigns}

## Goedkeuringsproces {#approval-process}

Elke leveringsstap kan worden goedgekeurd om volledige controle en controle op de verschillende processen van de campagne te waarborgen: het richten, inhoud, begroting, extractie, en het verzenden van een bewijs.

>[!NOTE]
>
>U moet controleren of de revisoren de juiste rechten hebben om te worden goedgekeurd. Controleer ook of hun beveiligingszone correct is gedefinieerd.

E-mailberichten worden verzonden naar de Adobe Campagneontwikkelaars die controleurs zijn aangewezen om hen op de hoogte te brengen van een goedkeuringsverzoek.

De goedkeuringsprocedure wordt voorgesteld bij de [controle en de goedkeuring van de leveringen](#checking-and-approving-deliveries).

>[!NOTE]
>
>Alleen de eigenaar van de levering kan een levering starten. Als een andere operator (of een operatorgroep) een levering wil starten, moet u deze als controleurs toevoegen in het **[!UICONTROL Delivery start:]** veld.\
>Zie ook [Revisoren](#selecting-reviewers)selecteren.

### Exploitatiebeginsel {#operating-principle-}

De standaard e-mail voor goedkeuring van de begroting is bijvoorbeeld als volgt:

![](assets/s_user_validation_link_in_mail.png)

De revisoroperatoren kunnen vervolgens kiezen of ze de desbetreffende stap al dan niet goedkeuren.

![](assets/s_user_validation_page_confirm.png)

Zodra de exploitant zijn keuze, goedkeuring of afwijzing van de baan goedkeurt wordt doorgestuurd naar het leveringsdashboard.

![](assets/s_user_validation_link_in_op_board.png)

De informatie is ook beschikbaar in de goedkeuringslogboeken van de campagne (die via het **[!UICONTROL Edit > Tracking > Approvals]** lusje worden betreden):

![](assets/s_user_validation_log_in_op_edit_tab.png)

Deze meldingen worden verzonden naar de betrokken marktdeelnemers voor elk proces waarvoor goedkeuring is ingeschakeld.

De goedkeuringen kunnen voor het campagnemalplaatje, voor elke campagne individueel, of voor een levering worden toegelaten.

Alle taken waarvoor goedkeuring is vereist, worden geselecteerd in het campagnemalplaatje ( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** tabblad), evenals de operatoren die verantwoordelijk zijn voor de goedkeuring (ze ontvangen meldingen, tenzij deze optie niet is ingeschakeld). Raadpleeg voor meer informatie de [goedkeuringsprocessen](#approving-processes).

Deze montages kunnen voor elke campagne met dit malplaatje worden gecreeerd, en individueel voor elke campagnelevering worden met voeten getreden: Klik op de **[!UICONTROL Properties]** knop en vervolgens op de **[!UICONTROL Approvals]** tab.

In het volgende voorbeeld is voor de leveringsinhoud geen goedkeuring vereist:

![](assets/s_user_validation_select_process_from_del.png)

### Revisoren selecteren {#selecting-reviewers}

Voor elk type goedkeuring worden de voor de goedkeuring verantwoordelijke exploitanten of groepen van marktdeelnemers geselecteerd uit de vervolgkeuzelijst in de levering. Met de **[!UICONTROL Edit...]** koppeling kunt u extra operatoren toevoegen. In dit venster kunt u ook de deadline van de goedkeuring bewerken.

![](assets/s_user_validation_add_operator.png)

Als er geen controleur is opgegeven, is de campagnemanager verantwoordelijk voor de goedkeuring en ontvangt deze de meldingen. De campagnemanager wordt opgegeven op het **[!UICONTROL Edit > Properties]** tabblad van de campagne:

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>Alle andere Adobe Campagneontwikkelaars met **[!UICONTROL Administrator]** rechten kunnen ook taken goedkeuren, maar ze ontvangen geen meldingen.\
>Standaard kan de campagnemanager de goedkeuring niet uitvoeren of de leveringen starten als er goedkeuringsoperatoren zijn gedefinieerd. U kunt dit gedrag wijzigen en de campagnemanager machtigen om leveringen goed te keuren/te beginnen door de optie **NmsCampaign_Activate_OwnerConfirmation** met **1** als waarde te creëren.

### Goedkeuringsmodi {#approval-modes}

#### Goedkeuring via het dashboard {#approval-via-the-dashboard}

Als u een taak wilt goedkeuren via de console of de webinterface, klikt u op de desbetreffende koppeling op het campagnemdashboard. Taken kunnen ook worden goedgekeurd via het volgen van de levering of via het leveringsdashboard.

![](assets/s_user_validation_from_console.png)

Controleer de informatie die u wilt goedkeuren, kies of u de goedkeuring wilt accepteren of afwijzen en voer zo nodig een opmerking in. Klik **[!UICONTROL Ok]** om op te slaan.

>[!NOTE]
>
>Als een proces reeds door een andere exploitant is goedgekeurd, is de goedkeuringsverbinding niet beschikbaar.

#### Goedkeuring via kennisgevingsberichten {#approval-via-notification-messages}

Klik op de koppeling in het bericht (zie [Meldingen](#notifications)). U wordt gevraagd uzelf te identificeren, zoals hieronder wordt getoond:

![](assets/s_user_validation__log_in.png)

Selecteer **[!UICONTROL Accept]** of **[!UICONTROL Reject]** en voer zo nodig een opmerking in.

![](assets/s_user_validation_save_target_validation.png)

Klik **[!UICONTROL Validate]**.

>[!NOTE]
>
>Als tijdens het proces waarschuwingen zijn weergegeven, wordt een waarschuwing weergegeven in het bericht.

#### Goedkeuring bijhouden {#approval-tracking}

De informatie is op verschillende plaatsen beschikbaar:

* In het logboek van de campagnegoedkeuring, **[!UICONTROL Approvals]** subtab van het **[!UICONTROL Edit > Tracking]** lusje:

   ![](assets/s_user_validation_log_from_op.png)

* In het logboek van de campagnelevering, **[!UICONTROL Deliveries]** sub-lusje van het **[!UICONTROL Edit > Tracking]** lusje:

   ![](assets/s_user_validation_log_from_delivery_list.png)

* U kunt de goedkeuringsstatus voor elke levering weergeven door op de **[!UICONTROL Hide/show log]** optie op het **[!UICONTROL Summary]** tabblad te klikken.

   ![](assets/s_user_validation_log_delivery.png)

* Deze informatie is ook toegankelijk via het **[!UICONTROL Tracking > Approvals]** tabblad van elke levering:

   ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>Wanneer een exploitant een taak heeft goedgekeurd of geweigerd, kunnen de andere beoordelende exploitanten niet langer op de goedkeuring reageren.

#### Automatische en handmatige goedkeuring {#automatic-and-manual-approval}

Als u een doelworkflow maakt en goedkeuring automatisch is (de standaardmodus), wordt de goedkeuringskoppeling weergegeven of wordt een melding verzonden zodra goedkeuring is vereist.

Als u de goedkeuringsmodus wilt kiezen (handmatig of automatisch), klikt u op het **[!UICONTROL Edit > Properties]** tabblad van de campagne- of campagnemalplaatje, klikt u **[!UICONTROL Advanced campaign settings...]** en tot slot op het **[!UICONTROL Approvals]** tabblad.

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>De geselecteerde goedkeuringsmodus is van toepassing op alle leveringen van de campagne.

Wanneer een doelworkflow wordt gemaakt, kunt u met handmatige goedkeuring voorkomen dat er goedkeuringskoppelingen worden gemaakt of dat meldingen automatisch worden verzonden. Het campagnemdashboard bevat vervolgens een **[!UICONTROL Submit targeting for approval]** koppeling waarmee het goedkeuringsproces handmatig kan worden gestart.

Met een bevestigingsbericht kunt u goedkeuringen autoriseren voor de taken die voor deze levering zijn geselecteerd.

De goedkeuringsknoppen worden vervolgens weergegeven op het campagnemdashboard (voor deze levering), op het leveringsdashboard en in het bijhouden van de levering. Als meldingen zijn ingeschakeld, worden ze parallel verzonden.

Met deze methode voor het inschakelen van goedkeuringen kunt u doelgericht werken zonder dat u onjuiste meldingen naar revisoren verzendt.

### Meldingen {#notifications}

Meldingen zijn specifieke e-mailberichten die naar revisoren worden verzonden om hen te laten weten dat een proces in afwachting is van goedkeuring. Wanneer de exploitant de verbinding in het bericht klikt, verschijnt een authentificatiepagina en, na het programma openen, kan de exploitant de informatie bekijken en de baan goedkeuren of verwerpen. U kunt ook een opmerking invoeren in het goedkeuringsvenster.

De inhoud van e-mailberichten voor meldingen kan worden aangepast. Zie [Inhoud](#notification-content)voor meldingen.

#### Melding inschakelen/uitschakelen {#enabling-disabling-notification}

Door gebrek, worden de berichtberichten verzonden als de goedkeuring van de verwante baan in het campagnemalplaatje, de campagne, of de levering wordt toegelaten. Meldingen kunnen echter alleen via de console worden uitgeschakeld.

Hiervoor bewerkt u het goedkeuringsvenster van de sjabloon voor de campagne of de campagne ( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** tabblad) en selecteert u **[!UICONTROL Do not enable notification sending]**.

![](assets/s_user_validation_notif_desactivate.png)

#### Inhoud voor meldingen {#notification-content}

De inhoud van het bericht wordt bepaald in een specifiek malplaatje: **[!UICONTROL Notification of validations for the marketing campaign]**. Deze sjabloon wordt opgeslagen in de **[!UICONTROL Administration > Campaign management > Technical delivery templates]** map van de Adobe Campaign-structuur.

## Controle en goedkeuring van leveringen {#checking-and-approving-deliveries}

Met Adobe Campaign kunt u goedkeuringsprocessen instellen voor de belangrijkste fasen van de marketingcampagne in de modus Samenwerken.

Voor directe postleveringen, kunnen de exploitanten van de Campagne van Adobe het extractiedossier bekijken alvorens het naar de router wordt verzonden, en indien nodig kunnen zij het formaat veranderen en extractie opnieuw lanceren. Zie Een extractiebestand [](#approving-an-extraction-file)goedkeuren.

Voor elke campagne kunt u het leveringsdoel, de inhoud (zie [Inhoud](#approving-content)goedkeuren) en de kosten goedkeuren. De Adobe Campagnebeheerders die voor goedkeuring verantwoordelijk zijn kunnen per e-mail op de hoogte worden gesteld en kunnen goedkeuring van de console of via een verbinding van het Web goedkeuren of verwerpen. Zie [Processen](#approving-processes)goedkeuren.

Wanneer deze validatiefasen zijn voltooid, kan de levering worden gestart. Zie [Een levering](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)starten.

>[!NOTE]
>
>Voor meer informatie over goedkeuringswijzen en het volgen, zie het proces [van de](#approval-process)Goedkeuring.

### Goedkeuring van processen {#approving-processes}

De stadia die goedkeuring vereisen verschijnen op het campagnesdashboard (via de console van de Webinterface). Zij verschijnen ook in de levering volgende lijst en op het leveringsdashboard.

Op dit moment is de stand van zaken van de campagne **[!UICONTROL To validate]**.

>[!NOTE]
>
>* Als u de processen wilt selecteren die moeten worden goedgekeurd, wijzigt u de sjabloon van de campagne. Raadpleeg de sjablonen [voor](../../campaign/using/marketing-campaign-templates.md#campaign-templates)campagnes voor meer informatie.
   >
   >
* Raadpleeg ook de sectie over het [goedkeuringsproces](#approval-process).



![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>In een het richten werkschema, als een fout verbonden aan een configuratiekwestie tijdens berichtvoorbereiding voorkomt, wordt de **[!UICONTROL Restart message preparation]** verbinding getoond op het dashboard. Corrigeer de fout en klik op deze koppeling om de berichtvoorbereiding opnieuw te starten terwijl het doelwerkgebied wordt overgeslagen.

![](assets/s_user_validation_relaunch_message_preparation.png)

Voor elke levering in de campagne, kunt u de volgende processen goedkeuren:

* **Doelstelling, inhoud en begroting**

   Wanneer de **[!UICONTROL Enable target approval]**, **[!UICONTROL Enable content approval]** of de **[!UICONTROL Enable budget approval]** opties in het venster van de montages van de baangoedkeuring worden geselecteerd, worden de relevante verbindingen getoond in het campagnesdashboard voor de betrokken leveringen.

   >[!NOTE]
   >
   >De goedkeuring van de begroting is slechts beschikbaar als gericht goedkeuring in het venster van goedkeuringsmontages wordt toegelaten. De koppeling voor goedkeuring van de begroting wordt pas weergegeven nadat het doel is geanalyseerd. Deze koppeling wordt ook samen met de koppeling voor doelgoedkeuring weergegeven.

   Als de **[!UICONTROL Assign content editing]** of de **[!UICONTROL External content approval]** opties in het venster van goedkeuringsmontages worden geselecteerd, zal het dashboard de **[!UICONTROL Available content]** en **[!UICONTROL External content approval]** verbindingen tonen.

   Met Goedkeuring van inhoud hebt u toegang tot de verzonden proefdrukken.

* **Goedkeuring van uittreksels (direct-mailbezorging)**

   Wanneer **[!UICONTROL Enable extraction approval]** wordt geselecteerd in het venster van goedkeuringsmontages, moet het gehaalde dossier worden goedgekeurd alvorens de router kan worden meegedeeld.

   Er is een **[!UICONTROL Approve content]** koppeling beschikbaar op het campagnemdashboard, zoals hieronder wordt weergegeven:

   ![](assets/s_ncs_user_edit_file_valid.png)

   U kunt een voorvertoning weergeven van de extractiebestanden via het goedkeuringsvak. U kunt de bestanden vervolgens accepteren of afwijzen.

   ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

   >[!NOTE]
   >
   >De voorvertoning van het extractiebestand heeft alleen betrekking op een gegevensvoorbeeld. Het volledige uitvoerbestand wordt niet geladen.

* **Bijbehorende leveringen goedkeuren**

   De **[!UICONTROL Enable individual approval of each associated delivery]** optie wordt gebruikt voor één hoofdlevering verbonden aan secundaire leveringen. Deze optie is standaard niet geselecteerd, zodat een algemene goedkeuring van de hoofdlevering kan worden uitgevoerd. Als deze optie is geselecteerd, moet elke levering afzonderlijk worden goedgekeurd.

   ![](assets/s_ncs_user_task_valid_associate.png)

#### Goedgekeurde processen selecteren {#choosing-the-processes-to-be-approved}

De goedkeuringsfasen worden bepaald met het malplaatje verbonden aan de campagne. U moet de elementen selecteren die u wilt goedkeuren in de sjabloon en de Adobe Campagneontwikkelaars opgeven die verantwoordelijk zijn voor deze goedkeuringen. Raadpleeg de sjablonen [voor](../../campaign/using/marketing-campaign-templates.md#campaign-templates)campagnes voor meer informatie.

>[!NOTE]
>
>De goedkeuringsconfiguratie voor de campagne of het campagnemalplaatje zal worden toegepast op alle toekomstige leveringen met betrekking tot deze campagne. Wijzigingen in de configuratie worden niet toegepast op vorige leveringen.

Deze informatie kan voor elke campagne en elke levering worden overschreven.

Voor een campagne, klik het **[!UICONTROL Edit > Properties]** lusje, dan de **[!UICONTROL Advanced campaign settings...]** verbinding, en tenslotte het **[!UICONTROL Approvals]** sub-lusje om tot de pagina van de goedkeuringsconfiguratie toegang te hebben.

U kunt de processen selecteren en deselecteren om Adobe Campagneontwikkelaars die voor goedkeuring verantwoordelijk zijn, goed te keuren en aan te wijzen. Dit kunnen individuele operatoren, een groep operatoren of een lijst met operatoren zijn.

Als u een lijst met operatoren wilt selecteren, klikt u op de **[!UICONTROL Edit...]** koppeling rechts van het veld waarin de eerste controleur wordt aangewezen en voegt u zoveel operatoren toe als nodig is, zoals hieronder wordt getoond:

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* Als een lijst met revisoren is gedefinieerd, wordt een taak goedgekeurd zodra een controleur deze heeft geaccepteerd. De desbetreffende goedkeuringsverbinding wordt dan niet meer aangeboden in het dashboard. Wanneer het verzenden van meldingen is ingeschakeld en een andere controleur op de goedkeuringskoppeling in het meldingsbericht klikt, wordt hem meegedeeld dat een andere operator de taak al heeft goedgekeurd.
>* U kunt een goedkeuringsschema voor de campagne definiëren in de onderste sectie van het revisiebewerkingsvenster. Standaard hebben revisoren drie dagen vanaf de verzenddatum om een proces goed te keuren. Het is mogelijk om een herinnering te vormen die automatisch naar de betrokken exploitanten vóór de goedkeuringstermijn wordt verzonden.
>* U kunt vanuit deze sectie herinneringen toevoegen.
>



![](assets/s_ncs_user_edit_op_valid_calendar.png)

Klik voor elke levering op de **[!UICONTROL Audit]** knop en het **[!UICONTROL Approvals]** tabblad om goedkeuringsdatums en automatische herinneringen weer te geven en te bewerken.

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>Dit tabblad is beschikbaar nadat het goedkeuringsproces voor inhoud is gestart.

### Inhoud goedkeuren {#approving-content}

>[!CAUTION]
>
>Voor het goedkeuren van een inhoud is een proefcyclus verplicht. Met proefdrukken kunt u de weergave van gegevens, aanpassingsgegevens en de werking van koppelingen goedkeuren. Raadpleeg de sectie [Berichten](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) verzenden voor meer informatie over het maken van een proefdruk en de bijbehorende levenscyclus.
>
>De hieronder beschreven functies voor inhoudsgoedkeuring kunnen worden toegevoegd aan de levering van het bewijs.

Het is mogelijk om een cyclus van de inhoudsgoedkeuring te vormen. Selecteer hiertoe de **[!UICONTROL Enable content approval]** optie in het venster met goedkeuringsinstellingen. De belangrijkste stappen van de cyclus voor inhoudsgoedkeuring zijn:

1. Na het creëren van een nieuwe levering, klikt de campagnemanager de **[!UICONTROL Submit content]** verbinding op het campagnedashboard om de cyclus van de inhoudgoedkeuring te beginnen.

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >Als de **[!UICONTROL Enable the sending of proofs]** optie (voor e-mailleveringen) of **[!UICONTROL Enable the sending and approval of proofs]** (voor direct e-mailleveringen) is geselecteerd in het venster met goedkeuringsinstellingen, worden de proefdrukken automatisch verzonden.

1. Er wordt een meldingsbericht verzonden naar de persoon die verantwoordelijk is voor de inhoud, die kan kiezen of u de inhoud al dan niet wilt goedkeuren:

   * via het e-mailbericht:

      ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

      >[!NOTE]
      >
      >Het e-mailbericht bevat een koppeling naar de reeds verzonden proefdrukken en mogelijk naar een weergave van het bericht voor de verschillende webmails als de optie **Aflevering** is ingeschakeld voor deze instantie.

   * via de console of webinterface, het bijhouden van de levering, het bezorgdashboard of het campagnemdashboard:

      ![](assets/s_ncs_user_validation_content_bat_op.png)

      >[!NOTE]
      >
      >Met dit campagnemdashboard kunt u de lijst met proefdrukken weergeven die zijn verzonden door op de **[!UICONTROL Inbox rendering...]** koppeling te klikken. Als u de inhoud wilt weergeven, klikt u op het **[!UICONTROL Detail]** pictogram rechts van de lijst.

      ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. Aan de voor de campagne verantwoordelijke persoon wordt een meldingsbericht gezonden waarin deze wordt geïnformeerd of de inhoud al dan niet is goedgekeurd.

   >[!NOTE]
   >
   >De persoon die verantwoordelijk is voor de campagne kan de cyclus voor het goedkeuren van inhoud op elk gewenst moment opnieuw starten. Om dit te doen, klik de verbinding op de **[!UICONTROL Content status]** lijn van het campagnesdashboard (op leveringsniveau), dan klik **[!UICONTROL Reset content approval to submit it again]**.

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### Inhoud bewerken toewijzen {#assign-content-editing}

Met deze optie kunt u iemand definiëren die verantwoordelijk is voor het bewerken van inhoud, zoals een webstramien. Als de **[!UICONTROL Assign content editing]** optie is geselecteerd in het venster met goedkeuringsinstellingen, worden verschillende goedkeuringsstappen toegevoegd tussen het maken van de levering en het verzenden van het e-mailbericht aan de persoon die de inhoud beheert:

1. Na het creëren van een nieuwe levering, klikt de persoon verantwoordelijk voor de campagne de **[!UICONTROL Submit content editing]** verbinding in het campagnedashboard om de tevreden het uitgeven cyclus te beginnen.

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. De persoon die verantwoordelijk is voor het bewerken van inhoud ontvangt een e-mail met de mededeling dat de inhoud beschikbaar is.

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. Vervolgens kunnen ze zich aanmelden bij de console, de levering openen en deze bewerken met een vereenvoudigde wizard om het onderwerp, HTML en tekstinhoud te wijzigen en proefdrukken te verzenden.

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >Als de **[!UICONTROL Enable the sending of proofs]** optie (voor e-mailleveringen) of **[!UICONTROL Enable the sending and approval of proofs]** (voor direct e-mailleveringen) is geselecteerd in het venster met goedkeuringsinstellingen, worden de proefdrukken automatisch verzonden.

1. Nadat de persoon die verantwoordelijk is voor het bewerken van inhoud alle wijzigingen in de inhoud van de levering heeft aangebracht, kan hij of zij de inhoud beschikbaar stellen.

   Om dit te doen, kunnen zij:

   * Klik op de **[!UICONTROL Available content]** koppeling via de Adobe Campaign-console.

      ![](assets/s_ncs_user_validation_submit_content_available.png)

   * Klik op de koppeling in het meldingsbericht en geef vervolgens de beschikbaarheid van de inhoud goed.

      ![](assets/s_ncs_user_validation_submit_content_available2.png)

      De exploitant kan een commentaar toevoegen alvorens de inhoud aan de persoon voor te leggen die de campagne leidt.

      ![](assets/s_ncs_user_validation_submit_content_available3.png)

      Met het meldingsbericht kan de revisor de inhoud goedkeuren of afwijzen.

      ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### Goedkeuring van externe inhoud {#external-content-approval}

Met deze optie kunt u een externe operator definiëren die verantwoordelijk is voor het goedkeuren van rendering van leveringen, zoals consistentie in de communicatie van het merk, snelheden, enzovoort. Wanneer de **[!UICONTROL External content approval]** optie is geselecteerd in het venster met goedkeuringsinstellingen, worden verschillende goedkeuringsstappen toegevoegd tussen de goedkeuring van inhoud en de verzending van het bericht aan de persoon die verantwoordelijk is voor de campagne:

1. De externe contentmanager ontvangt een bericht via e-mail waarin wordt gemeld dat de inhoud is goedgekeurd en waarmee externe goedkeuring wordt aangevraagd.
1. Het e-mailbericht bevat koppelingen naar de verzonden proefdrukken, waarmee u rendering van de levering kunt weergeven en een knop voor het goedkeuren of afwijzen van de leveringsinhoud.

   >[!NOTE]
   >
   >Deze koppelingen zijn alleen beschikbaar als een of meer proefdrukken zijn verzonden. Anders is rendering van levering alleen beschikbaar via de console of de webinterface.

   ![](assets/s_user_validation_external_content.png)

### Een extractiebestand goedkeuren {#approving-an-extraction-file}

Voor off-line leveringen, produceert de Campagne van Adobe een extractiedossier dat, afhankelijk van hoe het opstelling is, naar de router wordt verzonden. De inhoud ervan is afhankelijk van de gebruikte exportsjabloon.

Wanneer de inhoud, de bestemming en het budget zijn goedgekeurd, verandert de levering in **[!UICONTROL Extraction pending]** totdat de extractieworkflow voor de campagnes wordt gestart.

![](assets/s_ncs_user_waiting_file_extraction.png)

Op de datum van het extractieverzoek wordt het extractiebestand gemaakt en verandert de leveringsstatus in **[!UICONTROL File to approve]**.

![](assets/s_ncs_user_file_extract_to_valid.png)

U kunt de inhoud van het geëxtraheerde bestand weergeven (door op de naam ervan te klikken), goedkeuren of, indien nodig, de indeling wijzigen en de extractie opnieuw starten met de koppelingen op het dashboard.

Zodra het dossier is goedgekeurd, kunt u het bericht e-mail naar de router verzenden. Raadpleeg voor meer informatie [Een offline levering](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery)starten.
